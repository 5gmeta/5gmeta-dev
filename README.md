
This repository contains the documentation, examples and tutorials related to the 5GMETA platform

# Requirements
This documentation in build using [MkDocs](https://www.mkdocs.org/). It requires the following sofwtare:
* python3

MkDocs can installed using pip:
```
pip install mkdocs
```

# How to build the documentation
Tu build and run the documentation website, simply type the following lines in a command window:
```
mkdocs serve
```
Then, the document can be access in a web browser, typing the following address:
* http://127.0.0.1:8000

# List of directories

The code in this folder is structured as follows:
```
├── datasets (contains sample data)
├── docs (contains all documentation files in markdown)
   ├── datasets-description
   └── images
├── examples (contains python scripts with the examples)
   ├── edge-deployement
   ├── message-data-broker
      ├── cits_sender_python
      ├── events_receiver_python
      └── image_sender_python
   ├── stream-data-gateway
      ├── consumer
      └── producer
   ├── tutorial
   └── video-stream-broker
├── tools
   └── cits-example.json
├── utils
   └── platform-client (contains client example to consume data)
├── LICENSE.txt
├── mkdocs.yml
└── README.md
```

# Authors
* Pierre Merdrignac ([pierre.merdrignac@vedecom.fr](mailto:pierre.merdrignac@vedecom.fr))
* Khaled Chikh ([khaledchikh@unimore.it](mailto:khaledchikh@unimore.it))
* Felipe Mogollon ([fmogollon@vicomtech.org](mailto:fmogollon@vicomtech.org))

# Licence

Copyright : Copyright 2022 VEDECOM and UNIMORE

License : EUPL 1.2 ([https://eupl.eu/1.2/en/](https://eupl.eu/1.2/en/))

The European Union Public Licence (EUPL) is a copyleft free/open source software license created on the initiative of and approved by the European Commission in 23 official languages of the European Union.

Licensed under the EUPL License, Version 1.2 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at [https://eupl.eu/1.2/en/](https://eupl.eu/1.2/en/)

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.