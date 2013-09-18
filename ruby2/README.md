	aptitude install \
	         build-essential curl libc6-dev openssl ca-certificates \
	         libreadline6-dev zlib1g-dev libssl-dev libyaml-dev \
	         libsqlite3-dev  libgdbm-dev libncurses5-dev libffi-dev \
	         checkinstall
	
	cd /usr/local/src
	
	wget http://cache.ruby-lang.org/pub/ruby/2.0/ruby-2.0.0-p247.tar.gz
	
	cd ruby-2.0.0.p247
	
	./configure --prefix=/usr/local --disable-install-doc
	
	make
	
	echo "Ruby 2.0.0-p247, no docs, installed into /usr/local" > description-pak
	
	checkinstall -D --fstrans=no --nodoc --pkgname='ruby2' \
	    --pkgversion='2.0.0-p247' --provides='ruby' \
	    --pkglicense='BSDL' --pkggroup='ruby' \
	    --maintainer='philip@pjkh.com' \
	    --requires='libc6, libreadline6, zlib1g, libssl1.0.0, libyaml-0-2, \
	                libsqlite3-0, libgdbm3, libncurses5, libffi5'

	
	ruby2_2.0.0-p247-1_amd64.deb
	
    # aptitude purge ruby2
	The following packages will be REMOVED:
	  ruby2{ap}
	0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
	Need to get 0 B of archives. After unpacking 58.5 MB will be freed.
	Do you want to continue? [Y/n/?] Y
	(Reading database ... 28772 files and directories currently installed.)
	Removing ruby2 ...
	dpkg: warning: while removing ruby2, directory '/usr/local/share' not empty so not removed
	dpkg: warning: while removing ruby2, directory '/usr/local/lib/ruby/2.0.0/racc' not empty so not removed
	dpkg: warning: while removing ruby2, directory '/usr/local/lib/ruby/gems/2.0.0' not empty so not removed
	Processing triggers for man-db ...
	Current status: 8 new [-1].
	
	
	# dpkg -i ruby2_2.0.0-p247-1_amd64.deb
	Selecting previously unselected package ruby2.
	(Reading database ... 27773 files and directories currently installed.)
	Unpacking ruby2 (from ruby2_2.0.0-p247-1_amd64.deb) ...
	Setting up ruby2 (2.0.0-p247-1) ...
	Processing triggers for man-db ...
	
	
	# aptitude show ruby2
	Package: ruby2
	New: yes
	State: installed
	Automatically installed: no
	Version: 2.0.0-p247-1
	Priority: extra
	Section: ruby
	Maintainer: philip@pjkh.com
	Architecture: amd64
	Uncompressed Size: 58.5 M
	Depends: libc6, libreadline6, zlib1g, libssl1.0.0, libyaml-0-2, libsqlite3-0, libgdbm3, libncurses5, libffi5
	Provides: ruby
	Description: Ruby 2.0.0-p247, no docs, installed into /usr/local