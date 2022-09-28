---
layout: post
title:  "Linux学习的点点滴滴"
date:   2019-03-30 17:08:30 +0800
categories: Linux 
tags:  终端 Linux
author: Xu ShiJie
mathjax: false
---




* content
{:toc}
### linux 的 apt update && apt upgrade -y

- linux 的升级命令

	```
	update
		update is used to resynchronize the package index files from their
		sources. The indexes of available packages are fetched from the
		location(s) specified in /etc/apt/sources.list. For example, when
		using a Debian archive, this command retrieves and scans the
		Packages.gz files, so that information about new and updated
		packages is available. An update should always be performed before
		an upgrade or dist-upgrade. Please be aware that the overall
		progress meter will be incorrect as the size of the package files
		cannot be known in advance.
	```

	```
	upgrade
		upgrade is used to install the newest versions of all packages
		currently installed on the system from the sources enumerated in
		/etc/apt/sources.list. Packages currently installed with new
		versions available are retrieved and upgraded; under no
		circumstances are currently installed packages removed, or packages
		not already installed retrieved and installed. New versions of
		currently installed packages that cannot be upgraded without
		changing the install status of another package will be left at
		their current version. An update must be performed first so that
		apt-get knows that new versions of packages are available.
	```

	```
	dist-upgrade
		dist-upgrade in addition to performing the function of upgrade,
		also intelligently handles changing dependencies with new versions
		of packages; apt-get has a "smart" conflict resolution system, and
		it will attempt to upgrade the most important packages at the
		expense of less important ones if necessary. The dist-upgrade
		command may therefore remove some packages. The
		/etc/apt/sources.list file contains a list of locations from which
		to retrieve desired package files. See also apt_preferences(5) for
		a mechanism for overriding the general settings for individual
		packages.
	```
	
> 上面的内容是从apt-get的man文档中摘录出来的。上面表达的意思就是，update的作用是从/etc/apt/source.list文件中定义的源中去同步包的索引文件，即运行这个命令其实并没有更新软件，而是相当于windows下面的检查更新，获取的是软件的状态。

> 而upgrade则是更据update命令同步好了的包的索引文件，去真正地更新软件。

> 而dist-upgrade则是更聪明的upgrade，man文档中说它以更聪明的方式来解决更新过程中出现的软件依赖问题，它也是从/etc/apt/source.list文件中获得地址，然后从这些地址中检索需要更新的包。


> 最后，需要注意的一点是，每回更新之前，我们需要先运行update，然后才能运行upgrade和dist-upgrade，因为相当于update命令获取了包的一些信息，比如大小和版本号，然后再来运行upgrade去下载包，如果没有获取包的信息，那么upgrade就是无效的啦！


> -y 的意思是 即当安装包的时候会询问y/n,这个参数是所有询问默认y，下边不再提醒，在终端输入以上命令时，直接下载安装，不再要求确认
