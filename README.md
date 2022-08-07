# SPARC Metadata Editor (sparc-me)
A python tool to explore, enhance, and expand SPARC datasets and their descriptions

[![Contributors][contributors-shield]][contributors-url]
[![GitHub commits](https://badgen.net/github/commits/SPARC-FAIR-Codeathon/sparc-me)](https://github.com/SPARC-FAIR-Codeathon/sparc-me/commit/) 
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]
[![Contributor Covenant](https://img.shields.io/badge/Contributor%20Covenant-2.1-4baaaa.svg)](code_of_conduct.md)
[![made-with-Markdown](https://img.shields.io/badge/Made%20with-Markdown-1f425f.svg)](http://commonmark.org)
<!-- [![PyPI download month](https://img.shields.io/pypi/dm/ansicolortags.svg)](https://pypi.python.org/pypi/ansicolortags/) -->

## Table of contents
* [About](#about)
* [Introduction](#introduction)
* [The problem](#the-problem)
* [Our solution - sparc-me](#our-solution---sparc-me)
* [Use-cases of sparc-me](#use-cases-of-sparc-me)
* [Impact](#impact)
* [Setting up sparc-me](#setting-up-sparc-me)
* [Using sparc-me](#using-sparc-me)
* [Reporting issues](#reporting-issues)
* [Contributing](#contributing)
* [Cite us](#cite-us)
* [FAIR practices](#fair-practices)
* [License](#license)
* [Team](#team)
* [Acknowledgements](#acknowledgements)

## About
This is the repository of Team sparc-me (Team #7) of the 2022 SPARC Codeathon. Click [here](https://sparc.science/help/2022-sparc-fair-codeathon) to find out more about the SPARC Codeathon 2022. Check out the [Team Section](#team) of this page to find out more about our team members.

With the exception of high-level planning by the team lead as advised by the Codeathon organisers, no work was done on this project prior to the Codeathon. Contributions from existing projects are described in the [Acknowledgements Section](#acknowledgements).

## Introduction
The NIH Common Fund program on **[Stimulating Peripheral Activity to Relieve Conditions (SPARC)](https://commonfund.nih.gov/sparc) focuses on understanding peripheral nerves** (nerves that connect the brain and spinal cord to the rest of the body), **how their electrical signals control internal organ function**, and **how therapeutic devices could be developed to modulate electrical activity in nerves to improve organ function**. This may provide a potentially powerful way to treat a diverse set of common conditions and diseases such hypertension, heart failure, gastrointestinal disorders, and more. 60 research groups spanning 90 institutions and companies contribute to SPARC and work across over 15 organs and systems in 8 species.

**The [SPARC Portal](http://sparc.science/) provides a single user-facing online interface to all resources generated by the SPARC community** that can be shared, cited, visualized, computed, and used for virtual experimentation. A key offering of the portal is the collection of well-curated, high-impact data that is being generated by SPARC-funded researchers. These datasets, along with other SPARC projects and computational simulations, can be found under the "[Find Data](https://sparc.science/data?type=dataset)" section of the SPARC Portal. 

**A SPARC dataset comprises** the following data and structure:
- **An experimental protocol** that has been submitted to Protocols.io, shared with the SPARC working group, curated, and published with a valid DOI.
- **Data files are organized into folders** by the investigators and curated according to the [SPARC Dataset Structure (SDS)](https://docs.sparc.science/docs/overview-of-sparc-dataset-format) and stored on the [Pennsieve data management system](https://sparc.science/resources/2j9lC0YFl5P34wGlkJOb49). The SDS was adapted from the [Brain Imaging Data Structure (BIDS)](https://bids.neuroimaging.io/index.html) specification. Data organization and submission that is in compliance with the SDS is greatly simplified using a cross-platform opensource [Software to Organize Data Automatically (SODA)](https://docs.sodaforsparc.io/) through a step-by-step interactive graphical user interface (GUI).

## The problem
There is **currently no approach available**:
- for users to **programmatically access and interrogate all metadata fields in SDS datasets** from a scientific programming language such as python.
- for contributors to **programmatically create new SDS datasets** (schemas for the SDS dataset validation are not yet publicly available).

This requires attention, as it limits the ability of members of the SPARC and the wider scientific community to apply FAIR principles for:
- interacting with SDS datasets for conducting their research (**limits accessibilty**).
- reusing the SDS specification for storing and curating results from their instrumentation and computational physiology workflows (especially from automated workflows that can generate large quantities of data and multiple datasets that may be impractical to store in SDS format through a step-by-step interactive tools like SODA) (**limits reusability**).
- quickly prototyping novel infrastructure/tools to elevate the impact of the SPARC program.  (**limits application**)
- propose and support extensions to the SDS ([similar to BIDS extensions](https://bids.neuroimaging.io/get_involved.html#extending-the-bids-specification)) to further expand the SPARC community e.g. by storing clinical data (**limits interoperabilty**)

## Our solution - sparc-me
To address this problem, we have **developed a python module called the SPARC Metadata Editor (sparc-me)** that can be used to enhance the FAIRness of SPARC data by enabling:

- *Discovery*
  - Accessing curated SDS datasets and their metadata (using the Pennsieve API)
  - Accessing protocols used by existing SDS datasets (using the protocols.io API)
  - Exploring data and metadata within SDS datasets
  - Defining a schema for SDS datasets
- *Interaction*
  - Creating, editing, and validating SDS datasets
- *Reusability and extensibilty*
  - Version controlling SDS schemas
- *Interoperabilty*
  - Conversion between BIDS datasets and SDS datasets

Examples and guided tutorials have been created to demonstrate each of the features above. 

## Use-cases of sparc-me
Potential application scenarios for sparc-me are illustrated in the figure below.

## Impact
sparc-me will elevate the impact of the SPARC program by providing the fundamental tools needed by users to programmatically interact with SDS datasets and efficiently build novel resources and tools from SPARC data. This includes:
- **supporting [SPARC Data and Resource Centre (DRC)](https://docs.sparc.science/docs/getting-started) and communnity developments** including:
  - assisting with efforts for automating SPARC data curation e.g. via realtime/on-the-fly dataset validation by users prior submission for curation.
  - improving efficiency of software developments (e.g. future codeathons and [SPARC portal roadmap developments](https://docs.sparc.science/docs/sparc-portal-roadmap)) by reducing the need to reimplement common functions. 
- **supporting and promoting reuse/harmonisation/compatibility with other research initiatives**. For example, sparc-me could be used to programatically map SDS descriptions to [Gen3 data dictionaries](https://gen3.org/resources/user/dictionary/) used in other NIH-funded initiatives such as the Common Fund’s [NIH Data Commons program](https://commonfund.nih.gov/commons).
 - **enabling version-controlled extensions of the SDS specification** to be proposed/explored (similar to BIDS extensions). This will enable other initiatives to build upon the extensive and ground-breaking developments of the SPARC community e.g. for storing results from [computational physiology workflows and digital twins that are being developed for precision medicine](https://doi.org/10.52843/cassyni.m56qzg).

## Setting up sparc-me

### From source code
#### Pre-requisites 
- [Git](https://git-scm.com/)

#### Downloading source code
```
git clone https://github.com/SPARC-FAIR-Codeathon/sparc-me.git
```

#### Installing dependencies
```
pip install -r requirements.txt
```

## Using sparc-me

### Running examples

A base example is located in ./examples/base_example.py for loading/saving/editing dataset/metadata 

### Running tutorials

Guided tutorials have been developed describing how to use sparc-me in different scenarios:

<table>
<thead>
  <tr>
    <th> Tutorial</th>
    <th> Description</th>
    <th> Status</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td> 1</td>
    <td> Download an existing curated SDS dataset (<a href="10.26275/fvsg-hzg1">human whole-body computational scaffold with embedded organs</a>), and use existing tools to query ontology terms that have been used to annotate SDS datasets using the SciCrunch knowledgebase.</td>
    <td>&#10060</td>
  </tr>
  <tr>
    <td> 2</td>
    <td> Create an SDS dataset from input data from a jet-injection experiment.</td>
    <td>&#10060</td>
  </tr>
  <tr>
    <td> 3 </td>
    <td> Create a version-controlled extension of the SDS to include additional metadata fields, and apply it to the dataset considered in Tutorial 1 to include data use descriptions from the <a href="https://github.com/EBISPOT/DUO">GA4GH-approved Data Use Ontology (DUO)</a>. This tutorial is a first step toward demonstrating how the SDS could be extended to describe clinical data.</td>
    <td>&#10060</td>
  </tr>
  <tr>
    <td> 4 </td>
    <td> Interacting with SDS datasets on O2SPARC with sparc-me.</td>
    <td>&#10060</td>
  </tr> 
  <tr>
    <td> 5 </td>
    <td> Converting a BIDS dataset to a SDS dataset.</td>
    <td>&#10060</td>
  </tr>
</tbody>
</table>
<p align="center">
<i> &#9989 = available, &#10060 = not fully ready </i>
</p>
<br/>

## Reporting issues 
To report an issue or suggest a new feature, use the [issues page](https://github.com/SPARC-FAIR-Codeathon/sparc-me/issues). Check existing issues before submitting a new one.

## Contributing
Fork this repository and submit a pull request to contribute. Before doing so, please read our [Code of Conduct](https://github.com/SPARC-FAIR-Codeathon/sparc-me/blob/main/CODE_OF_CONDUCT.md) and [Contributing Guidelines](https://github.com/SPARC-FAIR-Codeathon/sparc-me/blob/main/CONTRIBUTING.md). Please add a GitHub Star to support developments!

### Project structure
* `/sparc-me/` - Parent directory of sparc-me python module
* `/sparc-me/core/` - Core classes of sparc-me
* `/sparc-me/resources/templates/` - Location of SPARC dataset Structure templates
* `/examples/` - Parent directory of sparc-me examples
* `/tutorials/` - Parent directory of sparc-me tutorials

## Cite us
If you use sparc-me to make new discoveries or use the source code, please cite us as follows:
```
Savindi Wijenayaka, Michael Hoffman, Linkun Gao, Haribalan Kumar, Chinchien Lin, Thiranja Prasad Babarenda Gamage (2022). sparc-me: v1.0.0 - A python tool to explore, enhance, and expand SPARC datasets and their descriptions. 
Zenodo. https://doi.org/TODO.
```

## FAIR practices

## License
sparc-me is fully open source and distributed under the very permissive Apache License 2.0. See [LICENSE](https://github.com/SPARC-FAIR-Codeathon/sparc-me/blob/main/LICENSE) for more information.

## Team
* [Savindi Wijenayaka](https://github.com/savindi-wijenayaka) (Developer, Writer - Documentation)
* [Michael Hoffman](https://github.com/Moffhan) (Writer - Documentation)
* [Linkun Gao](https://github.com/LinkunGao) (Developer, Writer - Documentation)
* [Haribalan Kumar](https://github.com/haribalankumar) (Developer, Writer - Documentation)
* [Chinchien Lin](https://github.com/LIN810116) (SysAdmin, Writer - Documentation)
* [Thiranja Prasad Babarenda Gamage](https://github.com/PrasadBabarendaGamage) (Lead, Writer - Manuscript)

## Acknowledgements
We would like to thank the organizers of the 2022 SPARC Codeathon for their guidance and support during this Codeathon.

[contributors-shield]: https://img.shields.io/github/contributors/SPARC-FAIR-Codeathon/sparc-me.svg?style=flat-square
[contributors-url]: https://github.com/SPARC-FAIR-Codeathon/sparc-me/graphs/contributors
[stars-shield]: https://img.shields.io/github/stars/SPARC-FAIR-Codeathon/sparc-me.svg?style=flat-square
[stars-url]: https://github.com/SPARC-FAIR-Codeathon/sparc-me/stargazers
[issues-shield]: https://img.shields.io/github/issues/SPARC-FAIR-Codeathon/sparc-me.svg?style=flat-square
[issues-url]: https://github.com/SPARC-FAIR-Codeathon/sparc-me/issues
[license-shield]: https://img.shields.io/github/license/SPARC-FAIR-Codeathon/sparc-me.svg?style=flat-square
[license-url]: https://github.com/SPARC-FAIR-Codeathon/sparc-me/blob/master/LICENSE
[lines-of-code-shield]: https://img.shields.io/tokei/lines/github/SPARC-FAIR-Codeathon/sparc-me
[lines-of-code-url]: #
