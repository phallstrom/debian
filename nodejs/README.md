    cd /usr/local/src
    
    wget -N http://nodejs.org/dist/node-latest.tar.gz
    
    tar xzvf node-latest.tar.gz && cd node-v*
    
    ./configure --prefix=/usr/local
    
    make

    version=`pwd | sed 's/.*node-v//'`

    echo "Node.js $version, installed into /usr/local" > description-pak

    checkinstall -D --fstrans=no --nodoc --pkgname='nodejs' \
        --pkgversion="$version" --provides='nodejs' \
        --maintainer='philip@pjkh.com' --pkglicense='GPL' \
        --pkggroup='nodejs'


