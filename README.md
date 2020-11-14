NEXT 1201AC Driver (for Raspberry pi 4)

RTL8812BU 칩셋을 사용하지만, RTL8822BU 드라이버와 호환이 된다.


민코딩(mincoding) 에서 삼성전자 / SSAFY 임베디드반 강의용으로 사용

http://www.ez-net.co.kr/new_2012/upload/goods/1201.665.jpg


=======================

#Install Build Tool

sudo apt install git gcc make vim

sudo apt install build-essential bc git wget libssl-dev bison flex


#Get kernel source code

cd /usr/src

sudo git clone --depth 1 https://github.com/raspberrypi/linux.git

sudo ln -s linux $(uname -r)

sudo ln -s /usr/src/linux /lib/modules/$(uname -r)/build


#prepare linux build headers

cd linux

sudo wget https://github.com/mincoding1/rtl8822bu/blob/master/Module7l.symvers

KERNEL=kernel7l

sudo make bcm2711_defconfig -j8

sudo make prepare -j8

sudo make modules_prepare -j8


#make driver

sudo make -j8

sudo make install

sudo reboot

