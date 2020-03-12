
# Maintainer: 
pkgname="ros-melodic-franka-ros"
pkgver="0.6.0"
pkgrel=1
pkgdesc="franka_ros is a metapackage for all Franka Emika ROS packages"
arch=('x86_64')
url="http://wiki.ros.org/franka_ros"
license=('Apache 2.0')

makedepends=(
'cmake'
)

depends=(
'ros-melodic-franka-control'
'ros-melodic-franka-description'
'ros-melodic-franka-example-controllers'
'ros-melodic-franka-gripper'
'ros-melodic-franka-hw'
'ros-melodic-franka-msgs'
'ros-melodic-franka-visualization'
'ros-melodic-panda-moveit-config'
)

provides=($pkgname)
conflicts=($pkgname)
_dir="franka_ros-release-release-melodic-franka_ros-0.6.0-1"
source=("$pkgname-$pkgver.tar.gz::https://github.com/frankaemika/franka_ros-release/archive/release/melodic/franka_ros/0.6.0-1.tar.gz")
md5sums=('b1fc2b4a9e6e0fb076f0b95e5b5857e3')

build() {
	# Use ROS environment variables
  	source /usr/share/ros-build-tools/clear-ros-env.sh
  	[ -f /opt/ros/melodic/setup.bash ] && source /opt/ros/melodic/setup.bash

	# Create build directory
  	[ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  	cd ${srcdir}/build

	# Build project
	cmake ${srcdir}/${_dir} \
	      -DCMAKE_BUILD_TYPE=Release \
	      -DCATKIN_BUILD_BINARY_PACKAGE=ON \
	      -DCMAKE_INSTALL_PREFIX=/opt/ros/melodic \
	      -DPYTHON_EXECUTABLE=/usr/bin/python3 \
	      -DSETUPTOOLS_DEB_LAYOUT=OFF
	make
}

package() {
	cd "${srcdir}/build"
	make DESTDIR="${pkgdir}/" install
}
