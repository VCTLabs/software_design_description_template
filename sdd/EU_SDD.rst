.. create pdf with "rst2pdf EU_SDD.rst -s styles/sdd.yaml,styles/cui.yaml --use-floating-images -o EU_SDD.pdf"

.. class:: title-logobox

.. list-table::
   :widths: 72

   * - |
       |
       |
       | |ACME_logo|

.. |ACME_logo| image:: images/acme.png
   :width: 245
   :height: 84
   :scale: 250

|
|
|
|

.. class:: title-deepbox

.. list-table::
   :widths: 72

   * - .. class:: title-name

       Software Design Description
   * - .. class:: title-name

       ACME Engineering Evaluation Unit

|
|
|

.. class:: title-info

Doc #00001043

.. class:: title-info

Version 0.1

.. class:: title-info

01/24/24

|
|
|

.. role:: redtext

.. class:: title-deepbox

.. list-table::
   :widths: 72

   * - .. class:: title-notice

        :redtext:`Example Template Text Only`

        Distribution Statement A: Approved for public release. Distribution is unlimited.

        Controlled by: Department of Good Works, Security and Inspection Division, 800-NOT-REAL.

.. raw:: pdf

   PageBreak mainPage

.. contents:: Table of Contents

.. raw:: pdf

   PageBreak

Revisions
=========

Document revision history.

.. list-table::
   :widths: 9 19 11 33
   :header-rows: 1

   * - Revision
     - Author
     - Date
     - Description
   * - 0.1
     - SLA
     - 2024-01-24
     - Initial draft shell
   * - 0.2
     - SLA
     - 2024-06-15
     - Add example CUI marks and distribution statement


.. raw:: pdf

   PageBreak


1.0 - Scope
===========


1.1 - Identification
####################

This document is the Draft Software Design Description (see revision table)
for the End-user Management Component of the Advanced ACME Web Services Appliance,
Engineering Evaluation Unit.


1.2 - System Overview
#####################

The Advanced ACME Web Services Appliance is an on-premise virtual Web Services
cluster with an advanced management interface.  This document provides both the
Version Description and Installation steps for the Management Console only. The
ACME Web Service high-level system components are shown in Figure 1 below:

.. figure:: images/advanced_acme_web_service.png
   :width: 90%

   Figure 1. Advanced ACME Web Service Components

The management console consumes monitoring data and summarizes/displays the
analytics from Spark.


1.3 - Document Overview
#######################


2.0 Referenced documents
========================


3.0 Capabilities-based design decisions
=======================================

This section shall be divided into paragraphs as needed to present
CSCI-wide design decisions, that is, decisions about the CSCI’s
behavioral design (how it will behave, from a user’s point of view, in
meeting its requirements, ignoring internal implementation) and other
decisions affecting the selection and design of the software units that
make up the CSCI.

If all such decisions are explicit in the CSCI requirements or are
deferred to the design of the CSCI’s software units, this section shall
so state.

Design decisions that respond to requirements designated critical, such
as those for safety, security, or privacy, shall be placed in separate
subparagraphs. If a design decision depends upon system states or
modes, this dependency shall be indicated.

Design conventions needed to understand the design shall be presented
or referenced. Examples of CSCI-wide design decisions are the
following:

a. Design decisions regarding inputs the CSCI will accept and outputs
   it will produce, including interfaces with other systems, HWCIs, CSCIs,
   and users (4.3.x of this DID identifies topics to be considered in this
   description). If part or all of this information is given in Interface
   Design Descriptions (IDDs), they may be referenced.

b. Design decisions on CSCI behavior in response to each input or
   condition, including actions the CSCI will perform, response times and
   other performance characteristics, description of physical systems
   modeled, selected equations/algorithms/rules, and handling of unallowed
   inputs or conditions.

c. Design decisions on how databases/data files will appear to the user
   (4.3.x of this DID identifies topics to be considered in this
   description). If part or all of this information is given in Database
   Design Descriptions (DBDDs), they may be referenced.

d. Selected approach to meeting safety, security, and privacy
   requirements.

e. Other CSCI-wide design decisions made in response to requirements,
   such as selected approach to providing required flexibility,
   availability, and maintainability.

4.0 CSCI architectural design
=============================

This section shall be divided into the following paragraphs to describe
the CSCI architectural design. If part or all of the design depends
upon system states or modes, this dependency shall be indicated. If
design information falls into more than one paragraph, it may be
presented once and referenced from the other paragraphs. Design
conventions needed to understand the design shall be presented or
referenced.

4.1 CSCI components
###################

This paragraph shall:

a. Identify the software units that make up the CSCI. Each software
   unit shall be assigned a project-unique identifier.

Note: A software unit is an element in the design of a CSCI; for
example, a major subdivision of a CSCI, a component of that
subdivision, a class, object, module, function, routine, or database.
Software units may occur at different levels of a hierarchy and may
consist of other software units. Software units in the design may or
may not have a one- to-one relationship with the code and data entities
(routines, procedures, databases, data files, etc.) that implement them
or with the computer files containing those entities. A database may be
treated as a CSCI or as a software unit. The SDD may refer to software
units by any name(s) consistent with the design methodology being used.

b. Show the static (such as "consists of") relationship(s) of the
   software units. Multiple relationships may be presented, depending on
   the selected software design methodology (for example, in an
   object-oriented design, this paragraph may present the class and object
   structures as well as the module and process architectures of the
   CSCI).

c. State the purpose of each software unit and identify the CSCI
   requirements and CSCI- wide design decisions allocated to it.
   (Alternatively, the allocation of requirements may be provided in 6.a.)

d. Identify each software unit’s development status/type (such as new
   development, existing design or software to be reused as is, existing
   design or software to be reengineered, software to be developed for
   reuse, software planned for Build N, etc.) For existing design or
   software, the description shall provide identifying information, such
   as name, version, documentation references, library, etc.

e. Describe the CSCI’s (and as applicable, each software unit’s)
   planned utilization of computer hardware resources (such as processor
   capacity, memory capacity, input/output device capacity, auxiliary
   storage capacity, and communications/network equipment capacity). The
   description shall cover all computer hardware resources included in
   resource utilization requirements for the CSCI, in system-level
   resource allocations affecting the CSCI, and in resource utilization
   measurement planning in the Software Development Plan (SDP). If all
   utilization data for a given computer hardware resource are presented
   in a single location, such as in one SDD, this paragraph may reference
   that source. Included for each computer hardware resource shall be:

  1) The CSCI requirements or system-level resource allocations being satisfied
  2) The assumptions and conditions on which the utilization data are
     based (for example, typical usage, worst-case usage, assumption of
     certain events)
  3) Any special considerations affecting the utilization (such as use of
     virtual memory, overlays, or multiprocessors or the impacts of
     operating system overhead, library software, or other implementation
     overhead)
  4) The units of measure used (such as percentage of processor capacity,
     cycles per second, bytes of memory, kilobytes per second)
  5) The level(s) at which the estimates or measures will be made (such
     as software unit, CSCI, or executable program)

f. Identify the program library in which the software that implements
   each software unit is to be placed.

4.2 Concept of execution
########################

This paragraph shall describe the concept of execution among the
software units. It shall include diagrams and descriptions showing the
dynamic relationship of the software units, that is, how they will
interact during CSCI operation, including, as applicable, flow of
execution control, data flow, dynamically controlled sequencing, state
transition diagrams, timing diagrams, priorities among units, handling
of interrupts, timing/sequencing relationships, exception handling,
concurrent execution, dynamic allocation/deallocation, dynamic
creation/deletion of objects, processes, tasks, and other aspects of
dynamic behavior.

4.3 Interface design
####################

This paragraph shall be divided into the following subparagraphs to
describe the interface characteristics of the software units. It shall
include both interfaces among the software units and their interfaces
with external entities such as systems, configuration items, and users.
If part or all of this information is contained in Interface Design
Descriptions (IDDs), in section 5 of the SDD, or elsewhere, these
sources may be referenced.


4.3.1 Interface identification and diagrams
-------------------------------------------

This paragraph shall state the project-unique identifier assigned to
each interface and shall identify the interfacing entities (software
units, systems, configuration items, users, etc.) by name, number,
version, and documentation references, as applicable. The
identification shall state which entities have fixed interface
characteristics (and therefore impose interface requirements on
interfacing entities) and which are being developed or modified (thus
having interface requirements imposed on them). One or more interface
diagrams shall be provided, as appropriate, to depict the interfaces.


4.3.x (Project-unique identifier of interface)
----------------------------------------------

This paragraph (beginning with 4.3.2) shall identify an interface by
project-unique identifier, shall briefly identify the interfacing
entities, and shall be divided into subparagraphs as needed to describe
the interface characteristics of one or both of the interfacing
entities. If a given interfacing entity is not covered by this SDD (for
example, an external system) but its interface characteristics need to
be mentioned to describe interfacing entities that are, these
characteristics shall be stated as assumptions or as "When [the entity
not covered] does this, [the entity that is covered] will ...." This
paragraph may reference other documents (such as data dictionaries,
standards for protocols, and standards for user interfaces) in place of
stating the information here. The design description shall include the
following, as applicable, presented in any order suited to the
information to be provided, and shall note any differences in these
characteristics from the point of view of the interfacing entities
(such as different expectations about the size, frequency, or other
characteristics of data elements):

a. Priority assigned to the interface by the interfacing entity(ies)
b. Type of interface (such as real-time data transfer,
   storage-and-retrieval of data, etc.) to be implemented
c. Characteristics of individual data elements that the interfacing
   entity(ies) will provide, store, send, access, receive, etc., such as:

  1) Names/identifiers

    a) Project-unique identifier
    b) Non-technical (natural-language) name
    c) DoD standard data element name
    d) Technical name (e.g., variable or field name in code or database)
    e) Abbreviation or synonymous names

  2) Data type (alphanumeric, integer, etc.)
  3) Size and format (such as length and punctuation of a character string)
  4) Units of measurement (such as meters, dollars, nanoseconds)
  5) Range or enumeration of possible values (such as 0-99)
  6) Accuracy (how correct) and precision (number of significant digits)
  7) Priority, timing, frequency, volume, sequencing, and other
     constraints, such as whether the data element may be updated and
     whether business rules apply
  8) Security and privacy constraints
  9) Sources (setting/sending entities) and recipients (using/receiving
     entities)

d. Characteristics of data element assemblies (records, messages,
   files, arrays, displays, reports, etc.) that the interfacing
   entity(ies) will provide, store, send, access, receive, etc.,
   such as:

  1) Names/identifiers

    a) Project-unique identifier
    b) Non-technical (natural language) name
    c) Technical name (e.g., record or data structure name in code or database)
    d) Abbreviations or synonymous names

  2) Data elements in the assembly and their structure (number, order,
     grouping)
  3) Medium (such as disk) and structure of data elements/assemblies on
     the medium
  4) Visual and auditory characteristics of displays and other outputs
     (such as colors, layouts, fonts, icons and other display elements,
     beeps, lights)
  5) Relationships among assemblies, such as sorting/access characteristics
  6) Priority, timing, frequency, volume, sequencing, and other
     constraints, such as whether the assembly may be updated and whether
     business rules apply
  7) Security and privacy constraints
  8) Sources (setting/sending entities) and recipients (using/receiving
     entities)

e. Characteristics of communication methods that the interfacing
   entity(ies) will use for the interface, such as:

  1) Project-unique identifier(s)
  2) Communication links/bands/frequencies/media and their characteristics
  3) Message formatting
  4) Flow control (such as sequence numbering and buffer allocation)
  5) Data transfer rate, whether periodic/aperiodic, and interval between
     transfers
  6) Routing, addressing, and naming conventions
  7) Transmission services, including priority and grade
  8) Safety/security/privacy considerations, such as encryption, user authentication,
     compartmentalization, and auditing

f. Characteristics of protocols the interfacing entity(ies) will use
for the interface, such as:

  1) Project-unique identifier(s)
  2) Priority/layer of the protocol
  3) Packeting, including fragmentation and reassembly, routing,
     and addressing
  4) Legality checks, error control, and recovery procedures
  5) Synchronization, including connection establishment,
     maintenance, termination
  6) Status, identification, and any other reporting features

g. Other characteristics, such as physical compatibility of the
   interfacing entity(ies) (dimensions, tolerances, loads, voltages, plug
   compatibility, etc.)


5. CSCI detailed design
=======================

This section shall be divided into the following paragraphs to describe
each software unit of the CSCI. If part of all of the design depends
upon system states or modes, this dependency shall be indicated. If
design information falls into more than one paragraph, it may be
presented once and referenced from the other paragraphs. Design
conventions needed to understand the design shall be presented or
referenced. Interface characteristics of software units may be
described here, in Section 4, or in Interface Design Descriptions
(IDDs). Software units that are databases, or that are used to access
or manipulate databases, may be described here or in Database Design
Descriptions (DBDDs).

5.x (Project-unique identifier of a software unit)
##################################################

(or designator of a group of software units)

This paragraph shall identify a software unit by project-unique
identifier and shall describe the unit. The description shall include
the following information, as applicable. Alternatively, this paragraph
may designate a group of software units and identify and describe the
software units in subparagraphs. Software units that contain other
software units may reference the descriptions of those units rather
than repeating information.

a. Unit design decisions, if any, such as algorithms to be used, if not
   previously selected

b. Any constraints, limitations, or unusual features in the design of
   the software unit

c. The programming language to be used and rationale for its use if
   other than the specified CSCI language

d. If the software unit consists of or contains procedural commands
   (such as menu selections in a database management system (DBMS) for
   defining forms and reports, on- line DBMS queries for database access
   and manipulation, input to a graphical user interface (GUI) builder for
   automated code generation, commands to the operating system, or shell
   scripts), a list of the procedural commands and reference to user
   manuals or other documents that explain them

e. If the software unit contains, receives, or outputs data, a
   description of its inputs, outputs, and other data elements and data
   element assemblies, as applicable. Paragraph 4.3.x of this DID provides
   a list of topics to be covered, as applicable. Data local to the
   software unit shall be described separately from data input to or
   output from the software unit. If the software unit is a database, a
   corresponding Database Design Description (DBDD) shall be referenced;
   interface characteristics may be provided here or by referencing
   section 4 or the corresponding Interface Design Descriptions (IDDs).

f. If the software unit contains logic, the logic to be used by the
   software unit, including, as applicable:

  1) Conditions in effect within the software unit when its execution
     is initiated
  2) Conditions under which control is passed to other software units
  3) Response and response time to each input, including data
     conversion, renaming, and data transfer operations
  4) Sequence of operations and dynamically controlled sequencing
     during the software unit’s operation, including:

    a) The method for sequence control
    b) The logic and input conditions of that method, such as
       timing variations, priority assignments
    c) Data transfer in and out of memory
    d) The sensing of discrete input signals, and timing
       relationships between interrupt operations within the software
       unit

  5) Exception and error handling


6.0 Requirements traceability
=============================

This section shall contain:

a. Traceability from each software unit identified in this SDD to the
   CSCI requirements allocated to it. (Alternatively, this traceability
   may be provided in 4.1.)

b. Traceability from each CSCI requirement to the software units to
   which it is allocated.


7.0 Notes
=========

This section shall contain any general information that aids in
understanding this document (e.g., background information, glossary,
rationale). This section shall include an alphabetical listing of all
acronyms, abbreviations, and their meanings as used in this document
and a list of any terms and definitions needed to understand this
document.

Appendix A. Acronyms and abbreviations
======================================

The following may be used in this document to describe specific technologies
or engineering processes.

:AES: Advanced Encryption Standard - algorithm for symmetric key encryption/decryption
:BIF: Boot Image Format
:CI/CD: Continuous Integration/Continuous Deployment
:CONOPS: Concept of Operations
:COTS: Commercial-Off-The-Shelf
:CSCI: Computer Software Configuration Item
:DT&E: Developmental Test and Evaluation
:FPGA: Field-programmable gate array
:FSBL: First-stage boot loader
:FW: Firmware
:HMAC: Hashed Message Authentication Code - algorithm for private key authentication
:HW: Hardware
:ID: Project-unique identifier
:IRS: Interface Requirements Specification
:ICD: Interface Control Document (should reference IRS docs)
:JTAG: Joint Test Action Group debugging interface
:KPP: Key Performance Parameter
:KSA: Key System Attribute
:LRU: Line-Replaceable Unit
:MOE: Measure of Effectiveness
:MOP: Measure of Performance
:MS: Milestone
:NVM: Nonvolatile Memory
:O&M: Operations and Maintenance
:OCM: On-chip memory
:OT&E: Operational Test and Evaluation
:PL: Programmable Logic - FPGA plus FW
:POR: Power On / Reset
:PS: Processing System - ARMv7 Linux runtime
:PR: Pull Request (agile code review/quality check workflow step)
:R&R: Remove and Replace
:RAM: Reliability, Availability, and Maintainability (aka RMA)
:RC: Release Candidate (SW and FW)
:SS/SRS: System/Subsystem/Software Requirements Specifications
:SS/SDD: System/Subsystem/Software Design Descriptions
:SDP: Software Development Plan
:STP: Software Test Plan
:STD: Software Test Description
:STR: Software Test Report
:SUT: System Under Test
:SW: Software
:T&E: Test and Evaluation
:TDP: Technical Data Package
:VMP: Vulnerability Management Process
