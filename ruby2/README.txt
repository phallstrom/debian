  aptitude update

	aptitude -y install \
	         build-essential curl libc6-dev openssl ca-certificates \
	         libreadline6-dev zlib1g-dev libssl-dev libyaml-dev \
	         libsqlite3-dev  libgdbm-dev libncurses5-dev libffi-dev \
	         checkinstall
	
	cd /usr/local/src
	
	wget http://cache.ruby-lang.org/pub/ruby/2.0/ruby-2.0.0-p451.tar.gz
  
  tar zxvf ruby-2.0.0-p451.tar.gz
  	
	cd ruby-2.0.0-p451
	
	./configure --prefix=/usr/local --disable-install-doc
	
	make
	
	echo "Ruby 2.0.0-p451, no docs, installed into /usr/local" > description-pak
	
	checkinstall -D --fstrans=no --nodoc --pkgname='ruby2' \
	    --pkgversion='2.0.0-p451' --provides='ruby' \
	    --pkglicense='BSDL' --pkggroup='ruby' \
	    --maintainer='philip@pjkh.com' \
	    --requires='libc6, libreadline6, zlib1g, libssl1.0.0, libyaml-0-2, \
	                libsqlite3-0, libgdbm3, libncurses5, libffi5'


  ###############
	
  aptitude purge ruby2

	dpkg -i ruby2_2.0.0-p451-1_amd64.deb
	
	aptitude show ruby2
