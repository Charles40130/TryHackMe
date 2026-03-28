- NIST introduce the process of digital forensics in 4 phases :

4 phases :

1. Collection : Data collection, identifying all the devices which can stored data. (personal computers,laptops,digital cameras, USBs, etc....)
2. Examination : collected data may overwhelm investigators due to its size. Needs to be filtered and need to extract the interested data.
3. Analysis : Critical phase, investigators have to analyze the data by  correlating it with multiple pieces of evidence to draw conclusions.
4. Reporting : Prepared a detailed report which contains the investigation's methodology and detailed findings from the collected evidence, recommendations.

There are different types of digital forensics, all with their own collection and analysis methodologies, common types are listed below:
- **Computer forensics:** The most common type of digital forensics is computer forensics, which concerns investigating computers, the devices most commonly used in crimes.
- **Mobile forensics:** Mobile forensics involves investigating mobile devices and extracting evidence such as call records, text messages, GPS locations, and more.
- **Network forensics:** This area of forensics covers investigation beyond individual devices. It includes the whole network. The majority of the evidence found in networks is the network traffic logs.
- **Database forensics:** Many critical data is stored in dedicated databases. Database forensics investigates any intrusion into these databases that results in data modification or exfiltration.
- **Cloud forensics:** Cloud forensics is the type of forensics that involves investigating data stored on cloud infrastructure. This type of forensics sometimes gets tricky for the investigators as there is little evidence on cloud infrastructures.
- **Email forensics:** Email, the most common communication method between professionals, has become an important part of digital forensics. Emails are investigated to determine whether they are part of phishing or fraudulent campaigns.

---

### Evidence Acquisition
- Evidence collected without prior approval may be deemed indadmissible in court
- Forensics team should obtain authorization from the relevant authorities before collecting any data

Chain of custody : formal document containing all the details of the evidence:
- Description of the evidence (name, type).
- Name of individuals who collected the evidence.
- Date and time of evidence collection.
- Storage location of each piece of evidence.
- Access times and the individual record who accessed the evidence.

Write Blockers : essential part of the digital foresnincs's toolbox

---



**Autopsy:** [Autopsy](https://www.autopsy.com/) is a popular open-source digital forensics platform. An investigator can import an acquired disk image into this tool, and the tool will conduct an extensive analysis of the image. It offers various features during image analysis, including keyword search, deleted file recovery, file metadata, extension mismatch detection, and many more.
**DumpIt:** [DumpIt](https://www.toolwar.com/2014/01/dumpit-memory-dump-tools.html) offers the utility of taking a memory image from a Windows operating system. This tool creates memory images using a command-line interface and a few commands. The memory image can also be taken in different formats.

**Volatility:** [Volatility](https://volatilityfoundation.org/) is a powerful open-source tool for analyzing memory images. It offers some extremely useful plugins. Each artifact can be analyzed using a specific plugin. This tool supports various operating systems, including Windows, Linux, macOS, and Android.