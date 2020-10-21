# littleBeasts - Software Requirements Specification

## Table of Contents

-   [Flashcard Community - Software Requirements Specification](#flashcard-community---software-requirements-specification)

    -   [Table of Contents](#table-of-contents)

    -   [1. Introduction](#1-introduction)

        -   [1.1 Purpose](#11-purpose)
        -   [1.2 Scope](#12-scope)
        -   [1.3 Definitions, Acronyms and Abbreviations](#13-definitions-acronyms-and-abbreviations)
        -   [1.4 References](#14-references)
        -   [1.5 Overview](#15-overview)

    -   [2. Overall Description](#2-overall-description)

        -   [2.1 Vision](#21-vision)

    -   [2.2 Product perspective](#22-product-perspective)

        -   [2.3 User characteristics](#23-user-characteristics)
        -   [2.4 Dependencies](#24-dependencies)

    -   [3. Specific Requirements](#3-specific-requirements)

        -   [3.1 Functionality – Data Backend](#31-functionality--data-backend)

            -   [3.1.1 Usage of live pictures](#311-usage-of-live-pictures)
            -   [3.1.2 Provide status history](#312-provide-status-history)
            -   [3.1.3 User Management](#313-user-management)

        -   [3.2 Functionality – User Interface](#32-functionality--user-interface)

            -   [3.2.1 User system](#321-user-system)
            -   [3.2.1 Frontend](#321-frontend)
            -   [3.2.3 Flashcard boxes](#323-flashcard-boxes)
            -   [3.2.4 Flashcards](#324-flashcards)
            -   [3.2.5 Statistics](#325-statistics)

        -   [3.3 Usability](#33-usability)

        -   [3.4 Reliability](#34-reliability)

            -   [3.4.1 Availability](#341-availability)
            -   [3.4.2 MTBF, MTTR](#342-mtbf-mttr)
            -   [3.4.3 Accuracy](#343-accuracy)
            -   [3.4.4 Bug classes](#344-bug-classes)

        -   [3.5 Performance](#35-performance)

            -   [3.5.1 Response time](#351-response-time)
            -   [3.5.2 Throughput](#352-throughput)
            -   [3.5.3 Capacity](#353-capacity)
            -   [3.5.4 Resource utilization](#354-resource-utilization)

        -   [3.6 Supportability](#36-supportability)

        -   [3.7 Design Constraints](#37-design-constraints)

            -   [3.7.1 Development tools](#371-development-tools)
            -   [3.7.2 Spring Boot](#372-spring-boot)
            -   [3.7.3 ReactJS](#373-reactjs)
            -   [3.7.4 Supported Platforms](#374-supported-platforms)

        -   [3.8 Online User Documentation and Help System Requirements](#38-online-user-documentation-and-help-system-requirements)

        -   [3.9 Purchased Components](#39-purchased-components)

        -   [3.10 Interfaces](#310-interfaces)

            -   [3.10.1 User Interfaces](#3101-user-interfaces)
            -   [3.10.2 Hardware Interfaces](#3102-hardware-interfaces)
            -   [3.10.3 Software Interfaces](#3103-software-interfaces)
            -   [3.10.4 Communications Interfaces](#3104-communications-interfaces)

        -   [3.11 Licensing Requirements](#311-licensing-requirements)

        -   [3.12 Legal, Copyright and other Notices](#312-legal-copyright-and-other-notices)

        -   [3.13 Applicable Standards](#313-applicable-standards)

    -   [4. Supporting Information](#4-supporting-information)

## 1. Introduction

### 1.1 Purpose
The purpose of this document is to provide a good overview regarding the functionality and additional other aspects in the Camera Observation Tool Project.
It is used to give outsiders an idea of the different features in our App and the technical aspects for realising them. Furthermore it shall be taken as guideline throughout the development and the final tests and comparisions.

### 1.2 Scope
This SRS applies to the whole project. It is aimed to provide information for both internal and external purposes.

### 1.3 Definitions, Acronyms and Abbreviations

| Term     |                                     |
| -------- | ----------------------------------- |
| **SRS**  | Software Requirements Specification |
| **JSON** | JavaScript Object Notation          |
| **API**  | Application Programming Interface   |
| **MTBF** | Mean Time Between Failures          |
| **MTTR** | Mean Time To Repair                 |
| **DTO**  | Data Transfer Object                |
| **HTTP** | Hypertext Transfer Protocol         |
| **FAQ**  | Frequently Asked Questions          |
| **REST** | Representational State Transfer     |
| **COT**  | Camera Observation Tool             |
| **SE**   | Software Engineering                |
| **RPi**  | Raspberry Pi Computer               |

### 1.4 References

| Title                                                                                                     | Date       |
| -----------------------------------------------------------------------------------------------------     | ---------- |
| [Blog](https://cameraobservationtool.wordpress.com/)                                                      | 17/10/2018 |
| [GitHub](https://github.com/mymanu/Camera-Observation-Tool/)                                              | 17/10/2018 |
| [YouTrack](https://dhbw-karlsruhe.myjetbrains.com/youtrack/projects/45cb46d4-e2e1-4ad9-bd02-e6ddee90b3f5) | 17/10/2018 |


### 1.5 Overview
The following chapters aim to give an overview regarding the general project idea and concepts, while defining the needed specifications later on. To be able to evaluate the functionality, all the planed use cases are declared too. Furthermore we will give a detailed description of our used interfaces and additional technical imformation.

## 2. Overall Description

### 2.1 Vision
During our second year of studying we want to develop a Camera Observation Tool (COT) for our course Souftware Engineering.
This will be a tool for smart homes. The user can be notified when an unknown person enters their backyard. An AI for categorzing visitors and a live analysis of an (outdoor) camera picture make that possible. We also want to provide access to the live video for the user. As a backup solution in case our video recognition doesn't worok, we thought about adding a voice recognition or a quiz/password.

## 2.2 Product perspective

### 2.3 User characteristics

### 2.4 Dependencies
For full functionality of the app special hardware is needed.To be precise at least one installed camera with connectivity to the internet. Indirect access by using a micro computer (e.g. RPi) is possible too. Furthermore a big enough internet bandwidth is recommended to garuantee a certain video quality when checking the status while in holidays.

## 3. Specific Requirements

### 3.1 Functionality – Data Backend

#### 3.1.1 Usage of live pictures
A camera should send pictures to the server side of the application. To decrease the needed storage space, we decided to use some kind of motion sensor. Pictures taken before and after a certain amount of time has passed without anyone passing by should be deleted. Pictures of visitors should be passed to the recognition function. Depending on the result a notification can be sent to the user of the app. The user input will be taken for further algorithm improvement using an AI. 

#### 3.1.2 Provide status history
A history of the last x people should be safed on the server. This will help the user backtracking certain visitors and their behaviour.

#### 3.1.3 User Management
We plan to implement a user management system. While the admin of the installed app shall have all possible user rights, we want to give the them the possibility to add certain roles and profiles. Installation and configuration of additional cameras would be one such feature. Furthermore the deletion of pictures from the history and creating new profiles. Lastly the accepting and declining of visitors.

### 3.2 Functionality – User Interface

#### 3.2.1 User system

#### 3.1.2 Frontend
The user will be notified via an mobile app or web app. Here he has the possibility to accept or decline the visitors presence on his property. Additionaly he has the option to view a history of the last visitors and edit the so far saved visitors. He can categorize them into a group of welcomed and unwelcomed people.

#### 3.2.3 Flashcard boxes

#### 3.2.4 Flashcards

#### 3.2.5 Statistics

### 3.3 Usability
We plan to design the user interface as intuitive as possible.

### 3.4 Reliability

#### 3.4.1 Availability

#### 3.4.2 MTBF, MTTR

#### 3.4.3 Accuracy

#### 3.4.4 Bug classes

### 3.5 Performance

#### 3.5.1 Response time
As low as possible but without interfering too much with the overall network traffic.

#### 3.5.2 Throughput

#### 3.5.3 Capacity

#### 3.5.4 Resource utilization

### 3.6 Supportability

### 3.7 Design Constraints

#### 3.7.1 Development tools

#### 3.7.2 Spring Boot

#### 3.7.3 ReactJS

#### 3.7.4 Supported Platforms

### 3.8 Online User Documentation and Help System Requirements

### 3.9 Purchased Components

### 3.10 Interfaces

#### 3.10.1 User Interfaces

#### 3.10.2 Hardware Interfaces
The camera needs direct or indirect access to the internet.

#### 3.10.3 Software Interfaces

#### 3.10.4 Communications Interfaces
Communication between not only the backend server and the camera, but also the server and the client application has to specified. Secure data transfer has to be provided.

### 3.11 Licensing Requirements

### 3.12 Legal, Copyright and other Notices

### 3.13 Applicable Standards
Encryption standards have to be taken into account. Additionly we want to develop using the Clean Code concept.

## 4. Supporting Information
