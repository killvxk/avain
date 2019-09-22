# AVAIN - Automated Vulnerability Analysis (in) IP-based Networks
A framework for the automated vulnerability analysis in IP-based networks that enables its modules to work collaboratively by sharing results.

## About
AVAIN is a modular vulnerability analysis / penetration testing framework for computer networks and individual machines in which its modules can work collaboratively to achieve more sophisticated results. AVAIN can automatically assess the security level of an IP-based network or host. Its final output is a score between 0 and 10, where the higher the score, the more vulnerable / insecure the assessed object. In addition, AVAIN saves all the detailed results from its modules for the user to look at after the assessment. During the assessment, the most relevant parts of every module's output are shown right away.


Primarly AVAIN is an extensible framework that uses modules to do vulnerability assessment. As such it offers several features that make it easier to develop new modules and make use of existing ones. For more information, look at the [separate wiki page](https://github.com/DustinBorn/avain/wiki/Framework-Features). To see how to develop new modules with Python, look at [this](https://github.com/DustinBorn/avain/wiki/Creating-a-New-Module) wiki page.


## Current Features of Modules
In short, the currently available modules can:
- [x] Faciliate an Nmap scan &amp; somewhat postprocess it
- [x] Do an analysis based on the scan results to discover CVE / NVD entries that affect the discovered software
- [x] Brute force credentials for SSH &amp; Telnet services via Hydra and a configurable wordlist
- [x] Brute force directories and files on a webserver via a configurable wordlist
- [x] Completely scrape a webserver, i.e. crawl paths, find GET / POST parameters and cookies, find source code comments and find new network locations. Moreover, use Selenium to discover content that only becomes visible when opening websites via a browser, so dynamic content.

A more detailed overview of the current modules, what they can do and how they work is available in the [wiki](https://github.com/DustinBorn/avain/wiki/Module-Overview). All of AVAIN's modules are highly configurable. As a small example, you can configure authentication cookies to be used while scraping a website. For a full list of configuration parameters and how to use them properly, have look at the separate [wiki page](https://github.com/DustinBorn/avain/wiki/Configuration). In addition, while being fairly verbose during the scan, all of result files that contain even more information are stored in AVAIN's output directory. While the file structure should be simple to understand, it is further explained in the [wiki](https://github.com/DustinBorn/avain/wiki/Output-Structure).


## Installation
AVAIN was made to work on Unix based systems. It was tested to work on macOS, Ubuntu Linux and Kali Linux. You can either install it directly on your system or use the available Dockerfile. To install it directly &amp; automatically, run the ``install.sh`` script. As the script attempts to install the required software, you may have to run it as *root* or you will get asked for a password. In case the script does not work, you may be good by changing the package manager at the top of the script, if not feel free to open an issue. On macOS you need Homebrew. For more info on the installation process, see the [wiki page](https://github.com/DustinBorn/avain/wiki/Getting-Started).


## Usage
To use AVAIN, simply call it by typing ``avain`` without any arguments in a terminal and you will get presented with the following usage information.
```
usage: avain [-h] [-n NETWORKS [NETWORKS ...]] [-nL NETWORK_LIST] [-uM]
             [-c CONFIG] [-o OUTPUT] [-p PORTS] [-sN] [-v]
             [-sR SCAN_RESULTS [SCAN_RESULTS ...]]
             [-vS VULNERABILITY_SCORES [VULNERABILITY_SCORES ...]]
avain: error: at least one of the following arguments is required: -n/--network,-nL/--network-list, -uD/--update-modules or any one of [-sR/--scan-results, -vS/--vulnerability-scores]
```
To simply run AVAIN on some target ``192.168.42.1``, call it like so:
```
avain -n 192.168.42.1
```
Again, the contents of the created output folder should mostly be simple to understand, but a [separate wiki page](https://github.com/DustinBorn/avain/wiki/Output-Structure) goes into more detail. Further explanation on AVAIN's usage information is available at [this](https://github.com/DustinBorn/avain/wiki/Usage) wiki page.

Three more examples of how you can call AVAIN:
* ``avain -n 192.168.0.* -uM -p T:80,U:53 -o http_dns_sec``
* ``avain -n 192.168.0.1 192.168.0.100-150 -sN -c config/someconfig.cfg -v``
* ``avain -sR path_to_sr_1 path_to_sr_2 -o network_analysis``


## Wiki
In case you have more question about AVAIN, the [wiki](https://github.com/DustinBorn/avain/wiki/) is very detailed and explains AVAIN in great detail.


## Contribution & Bugs
If you want to contribute, or have any questions or suggestions, use GitHub or directly contact me via Email <a href="mailto:dustin.born@stud.tu-darmstadt.de">here</a>. If you found a bug or have other troubles, feel free to open an issue.


## License
AVAIN is licensed under the MIT license, see [here](https://github.com/DustinBorn/avain/blob/master/LICENSE).


## Miscellaneous
I created AVAIN as part of my Bachelor Thesis at TU Darmstadt (located in Germany) under the guidance of my advisor Rolf Egert. We have presented a paper about AVAIN at NetSys&nbsp;'19. In addition, another paper based on AVAIN has been accepted at the IEEE GLOBECOM 2019 Workshop on Security and Privacy in Smart, Cooperative IoT and CPS. For more info see the [Publications](https://github.com/DustinBorn/avain/wiki/Publications) wiki page.
