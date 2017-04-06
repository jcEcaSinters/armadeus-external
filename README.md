
<h1 align="center">
  <a href="http://www.armadeus.org"><img src="http://www.armadeus.org/wiki/images/logo.png" alt="Armadeus Project" width="200"></a>
  <a href="http://www.buildroot.org"><img src="https://buildroot.org/images/logo.png" alt="Buildroot" width="200"></a>  
  <br>
  Buildroot external repository for Armadeus board
  <br>
  <br>
</h1>

## Armadeus Board support

For now this external repository only support:
- APF27 SOM + APF27_Dev_Full baseboard.
The goal is to finalize tunning before buildroot mainline submission.

## Software version

This external repository have been tested with:
- buildroot-2017.02.1
- uboot-2017.03

## Install
```
git clone git://git.buildroot.net/buildroot
git clone https://github.com/jcEcaSinters/armadeus-external.git
mkdir buildroot-armadeus
cd buildroot-armadeus
make 0=${PWD} -C ../buildroot BR2_EXTERNAL=../armadeus-external armadeus_apf27_dev_full_defconfig
make
```
## Known issues / ToDoList
- Uboot patches have to be mainlined

## License

[GPLv2](LICENSE). Copyright (c) [ECA SINTERS](http://www.ecagroup.com).

