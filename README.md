# maProc-lib :dragon:


This lib is intended to map processes in *unix, this way you can get stack and heap addresses of a given process, without ptrace implementation at the moment, the lib has a [maProc](https://github.com/mentebinaria/maProc) project, which has qt creator as a front end , with all lib utilities maProc-lib

# About - Infos :copyright:
> [Documentation](https://0xc0ffeec0de.github.io/maProc-lib/index.html)

> All lib rights reserved to CoffeeCode organization

> The maProc project is separate from maproc-lib are separate projects

# Compile Library :printer:

> Commands

    cd maProc-lib
    mkdir build
    cd build
    cmake ..
    make


> Dependency

    build-essential

# Example 📖

A basic example of how to use the lib, and some features it brings

```C++
#include "maProclib/pmap.hpp"


int main(void)
{
	Pmap map; // object for mapper

	pid_t pid = 1; // pid target
	map.map_pid(pid); // method to check and map the pid

	if(map.map_mem("heap")) // map heap process if true get infos
	{
		std::cout << "Name Process" << map.get_utilsPid(NAME); // get utils name process
		std::cout << "Pid :" << pid << std::endl; // pid target
		// offset where the heap address begins
		std::cout << "Address start: 0x"<< std::hex << map.get_addrOn() << std::endl; 
		// offset end the heap address
		std::cout << "Address stop: 0x" << std::hex << map.get_addrOff() << std::endl; 
		std::cout << "Size Mem: " << map.get_sizeAddress() << std::endl; // size heap
		std::cout << "Flags: " << map.get_Flags() << std::endl; // flags, permissions
	}

	return 0;
}

```
