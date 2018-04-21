# Script generated with Bloom
pkgdesc="ROS - Navigation related tutorials."
url='http://www.ros.org/wiki/navigation_tutorials'

pkgname='ros-kinetic-navigation-tutorials'
pkgver='0.2.3_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('ros-kinetic-catkin'
)

depends=('ros-kinetic-laser-scan-publisher-tutorial'
'ros-kinetic-navigation-stage'
'ros-kinetic-odometry-publisher-tutorial'
'ros-kinetic-point-cloud-publisher-tutorial'
'ros-kinetic-robot-setup-tf-tutorial'
'ros-kinetic-roomba-stage'
'ros-kinetic-simple-navigation-goals-tutorial'
)

conflicts=()
replaces=()

_dir=navigation_tutorials
source=()
md5sums=()

prepare() {
    cp -R $startdir/navigation_tutorials $srcdir/navigation_tutorials
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/kinetic/setup.bash ] && source /opt/ros/kinetic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/kinetic \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DPYTHON_BASENAME=-python2.7 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

