---
title: User Data Agreement
description: How OpenDLP handles your personal data
---






## **OpenDLP Software Data Processing Policy**

The purpose of this data processing policy (hereinafter: policy) is to present the data processing processes related to the OpenDLP software developed and operated by Sortition Europe Nonprofit Kft. (registered office: 1092 Budapest, Ráday utca 31. C. lház. 1. emel 11. avt.; company registration number: 01-09-419871; tax number: 32356465-2-43; Hennig Brett Stephen, managing director) as data controller.

The technological background of the software is provided by the Sortition Foundation (registered office: Lytchett House, 13 Freeland Park Wareham Road, Poole, Dorset, BH16 6FA, United Kingdom).  Given that the parent company determines the technical framework of the software and provides the server infrastructure, the software operates in a flexible data management model. Depending on the contractual agreement with the Client (Partner), Sortition Europe Nonprofit Kft. and the Sortition Foundation may act either as Joint Data Controllers pursuant to Article 26 of the GDPR, or as Data Processors acting strictly on behalf of the Client, who remains the sole Data Controller. For the long-term database management described in Section 3, Sortition Europe Nonprofit Kft. acts as an Independent Data Controller 

The joint data controllers have set out in a separate agreement the procedure for handling data subject requests, the responsibilities for incident management, the sharing of technical and organizational measures, and the rules for communicating with data subjects. Data subjects may exercise their rights against any joint data controller.

The Data Controllers hereby inform you of the rights of the users of the software (hereinafter: Data Subject) regarding the processing of their personal data, pursuant to Article 13 of Regulation (EU) 2016/679 of the European Parliament and of the Council of 27 April 2016 on the protection of natural persons with regard to the processing of personal data and on the free movement of such data, and repealing Directive 95/46/EC (hereinafter: GDPR), as well as the measures taken to protect their personal data.

The personal scope of the Notice covers all data subjects who use the OpenDLP software and whose personal data are thus processed by the Data Controllers.

OpenDLP is a professional, open-source system designed to automate the representative, diverse, and fair selection of participants in citizen’s assemblies using scientifically based sortition algorithms (such as the _sortition-algorithms_ Python library). . The system pays special attention to the Privacy by Design principle: during the lottery process, a significant part of the data exists only in the working memory (RAM), reducing the risk of data leakage. Data security is guaranteed by a separate Docker environment, 2FA authentication, while drawing clear lines of responsibility between the platform operator and the user organization.

The software flexibly handles external integrations (e.g. Google Sheets, OAuth 2.0), while drawing clear lines of responsibility between the platform operator and the user organization.

## **Special Note on the Categories of Data Subjects**

To ensure clarity and compliance, this Notice distinguishes between two distinct categories of individuals whose data is processed within the OpenDLP system:

- Lottery Applicants (Data Subjects): Citizens who apply to participate in democratic lotteries. Their data is processed for registration, selection, and contact purposes, as detailed in Sections 2, 3, 4, and 5.
- System Users (Organizers): Representatives and staff members of our Partners or Clients who hold administrator accounts to operate the software.

1. **Data management for Organizers**

_Purpose of processing:_ To manage user accounts, provide access to the platform, ensure system accountability, and provide technical support.

_Legal basis_: The performance of the contract with the Client [Article 6(1)(b) of the GDPR] and the legitimate interest of the Data Controller to ensure IT security and accountability [Article 6(1)(f) of the GDPR].

_Types of data processed:_ Name, institutional/work email address, username, password (hashed), system logs of user actions, and IP addresses.

_Data storage and security:_ Authentication is protected by OAuth 2.0 or secure local credentials combined with mandatory Two-Factor Authentication (2FA).

_Duration of data processing:_ 

- User account data is retained for the duration of the contractual relationship with the Client. 
- If no active project/contract is in place, the account is maintained in an inactive status for a maximum of 2 years from the last login, based on the Data Controller's legitimate interest to ensure seamless access for returning clients. 
- After this period, or upon the Client's explicit request, the account will be permanently deleted. Technical access logs are kept for 3 months. 

## **Specific Data Processing Activities for Lottery Applicants** 

2. **Registration and participation in the democratic lottery process**

_Purpose of data processing:_ To collect data on applicants for the citizen’s assemblies, to run the selection algorithm based on scientific standards, and to ensure a representative, diverse, and fair selection of participants, achieving the best possible statistical approximation of the target population. 

_Legal basis for data processing:_ voluntary consent of the data subjects pursuant to Article 6(1)(a) of the GDPR, and with regard to sensitive personal data pursuant to Article 9(2)(a) of the GDPR. If one of the joint data controllers is a public authority, the legal basis for data processing is Article 6(1)(e) of the GDPR.

_Type of personal data processed:_ The type of personal data processed is project-dependent and is strictly limited to the data categories necessary to ensure demographic representativeness, diversity, and social inclusiveness, as well as the data necessary to maintain contact with the applicants. . Such data may include, in particular, the following: name, address, date of birth, email, telephone number, ethnicity, educational level, income status, language, disability, gender, occupation, previous voting data, digital literacy, housing type, attitudinal data (e.g. views on climate protection).

_Method of data processing and storage:_ The system uses a multi-layered protection architecture:

_Log masking (Privacy by Design):_ Personal identifiers (e.g. email addresses) included in system logs are automatically masked, so that even in the event of an error, unencrypted personal data is not stored in the log files*.*

_Physical and Logical Protection:_ The data is stored on servers within the European Union (Netherlands) managed by Mythic Beasts Ltd. Backups are stored in data centers located in the United Kingdom. The data moves unencrypted on the internal network between Docker containers, but is isolated from the outside world. The system strives to minimize personal data in log files. Although virtual disks are not encrypted in software, physical access is prevented by strict protocols, and discarded media is destroyed by physical crushing.

_Backup encryption:_ Backups are stored on servers protected by block-level encryption, ensuring data integrity and protection.

_External integrations (Google Sheets):_ The software allows the use of Google Sheets. If the Partner (Client) chooses this path, he is responsible for the geographical storage location of the data and for ensuring the legal basis for data transfer outside the EU (USA). The system assists the user with an active warning when starting functions involving data movement. The software can send the result of the draw back to the Google spreadsheet provided by the Partner. In this process, the software only records the selection status (yes/no), and does not generate any further personal data.

Data is stored on servers within the European Union (Netherlands) managed by Mythic Beasts Ltd. Backups are stored in data centers located in the United Kingdom. Data travels unencrypted over the internal network between Docker containers, but is kept private from the outside world. The system strives to minimize the amount of personal data in log files.

_Duration of data processing:_ 

- For log files: 3 months.
- For lottery data: until the project is closed or consent is withdrawn. In case of deletion, the system permanently empties the personal fields, but an anonymous technical identifier (ID) is retained in the lottery log for auditability.

_Data processors:_

| **Name** | **Location** | **Data processor’s tasks** |
| Microsoft Ireland Operations Ltd. | One Microsoft Place, South County Business Park, Leopardstown, Dublin 18, Ireland | Cloud based infrastructure, server hosting (Azure/VM) and OAuth 2.0 authentication. |
| Google Ireland Limited | Gordon House, Barrow Street, Dublin 4, Ireland | Data source integration (Google Sheets), cloud based storage and OAuth 2.0 authentication. |
| Sortition Foundation | HQ: 27 Old Gloucester Street, London, WC1N 3AX, United Kingdom | Software maintenance, technical support, supervision of the algorithm and technical execution of data handling processes. |
| Mythic Beasts Ltd. | Cambridge, UK | Server hosting and backups. |

Possible consequence of failure to process data: The Data Subject cannot participate in the lottery process, so the opportunity to participate in the citizens assembly cannot be ensured.

3. **Contact and information**

_Purpose of data processing:_ Technical support of the registration process, official notification of the lottery results, confirmation of participation and coordination of logistical details.

_Legal basis for data processing:_ voluntary consent of the data subjects pursuant to Article 6(1)(a) of the GDPR. Consent is given simultaneously with registration, by providing contact details.

_Type of personal data processed:_ name, e-mail, phone number.

_Method of data processing and storage:_ The system sends automatic notifications (e.g. registration confirmation) with the involvement of an external service provider (Brevo). The content of the e-mails is limited to the name and e-mail address, the messages sent do not contain other sensitive data. Telephone inquiries may also occur, when in the case of selected participants, during confirmation calls, operators only access the necessary identification data through the software interface. During messaging, the data is transmitted to the service provider via an encrypted channel.

_Duration of data processing:_

- For log files: 3 months.
- For contact details (email, telephone) until the end of the project, unless the data subject has specifically consented to subsequent inquiries.

_Data processor:_

| **Name** | **Location** | **Data processor’s tasks** |
| Sendinblue SAS (Brevo) | 122 rue du Faubourg Saint-Honoré, 75008 Párizs, France | Technical sending of transactional emails (confirmations, notifications). |

4. **Handling future inquiries**

_Purpose of data processing:_ Long-term storage and processing of data of applicants who have expressly consented to receive notifications of similar democratic events, citizens assemblies or democratic lotteries in the future during registration. With regard to this data processing, Sortition Europe Nonprofit Kft. acts as an independent data controller.

_Legal basis for data processing:_ Explicit, voluntary and specific consent of the data subjects given by means of a checkbox pursuant to Article 6(1)(a) of the GDPR, and with regard to sensitive data (ethnicity, political opinion, etc.) pursuant to Article 9(2)(a) of the GDPR.

_Type of personal data processed:_ Name, address, date of birth, e-mail, telephone number, ethnicity, educational background, income status, language, disability, gender, occupation, previous voting data, digital literacy, type of housing, attitudinal data (e.g. views on climate protection).

_Data processing and storage:_ The data is stored in a separate database of OpenDLP, protected by a password and two-factor authentication (2FA). The technical protection is the same as described in point 2.

_Duration of data processing:_

- Until consent is withdrawn (unsubscribe). The Data Controller undertakes to review the database at regular intervals (every 2 years) and requests confirmation from the Data Subjects by e-mail regarding further storage. If the Data Subject does not confirm his/her intention, his/her data will be permanently deleted.
- The retention period of technical log entries in this case is also 3 months.

5. **Scientific research and service development**

_The purpose of data processing:_  anonymization of data for scientific research, analysing the mathematical efficiency of the lottery processes and service developement. During this process direct identifiers (name, exact address, e-mail, telephone) are deleted or completely anonymized. Once the datasets are fully anonymised, they are no longer  constitute personal data under the GDPR, and may be stored and analysed for statistical and scientific  purposes without time limit. Prior to the completion of the anonymization process,  Sortition Europe Nonprofit Kft. is an independent data controller. For the specific and limited purpose of performing the anonymization and conducting subsequent scientific and statistical research, Sortition Europe Nonprofit Kft. acts as an independent data controller. 

_Legal basis for data processing:_ The legitimate interest of the Data Controller in the development of democratic processes and the improvement of the software service based on Article 6(1)(f) of the GDPR). In the case of the use of special data for statistical purposes, the legal basis is Article 9(2) of the GDPR.

_The type of personal data processed:_ Year of birth, ethnicity, educational level, income status, language, disability, gender, occupation, previous voting data, digital literacy, housing type, attitude data (e.g. views on climate protection), which are parameters necessary exclusively for statistical weighting and representativeness research..

_Method of data processing and storage:_ the data is stored in separate database tables, stripped of identifiers (name, e-mail). The datasets used for statistical analyses do not leave the system and are only accessible to the Data Controller's research staff.

_Duration of data processing:_

- The data will be anonymized as soon as possible after collection. Anonymized data (no longer personally identifiable) may be stored for statistical and scientific purposes without time limit, it is not subject to retention limits under the GDPR.
- Technical logs will also be retained for 3 months in this phase to ensure system security.

6. **System security and logging**

_The purpose of data processing:_ to guarantee the IT security of the software, to prevent unauthorized access, to detect system errors, and to ensure the auditability of the lottery process. Logging guarantees that it can be checked subsequently which administrator made which modification to the system, when and what.

_Legal basis for data processing:_ The legitimate interest of the Data Controller is the interest in maintaining IT security and process integrity based on Article 6(1)(f) of the GDPR.

_Type of personal data processed:_ User IDs, access times, logging of operations, and, occasionally, during troubleshooting processes – e-mail addresses appearing in technical error messages.

_Data management and storage method:_ Email addresses and personal identifiers are automatically masked from system logs (e.g. u\*\*\*r@example.com) before the logging phase, preventing data leakage in the event of error messages. Access to technical logs and infrastructure (server, database) is only possible with two-factor authentication (2FA) for designated system administrators. Data traffic is enclosed in Docker containers and is only open to the outside world through authorized endpoints.

_Duration of data processing:_

- The retention period for technical logs is 3 months. After that, the log files are automatically overwritten or deleted.
- The Data Controller will retain logs of substantive changes (deletion or modification of data) in the system until the project is completed for the purpose of accountability.

7. **Rights of the data subject, legal remedies**

We inform the Data Subjects that there is no self-service interface (user account) in the system, so requests to modify or delete data can be initiated by sending a message to the contact email address of the Data Controller (hereinafter: Data Controller) designated in the joint data management agreement. The data subject has the right to receive information related to the processing of personal data concerning him or her, and may request the correction of data concerning him or her.

The data subject may request the deletion of his or her processed personal data, the restriction of data processing, and may exercise his or her right to data portability and objection with the Data Controller.

The data subject has the right to receive feedback from the Data Controller as to whether his or her personal data is being processed, and if such data processing is in progress, he or she has the right to access the personal data and information regarding data processing. The data subject may only receive a copy of a document on which no other person appears, or only in an unrecognizable manner.

The data subject has the right to obtain from the Controller, at his request, the erasure of personal data concerning him or her without undue delay or the restriction of processing.

The data subject may object to the processing of his or her personal data. The OpenDLP system uses an algorithmic weighting and randomization mechanism when selecting participants, which operates under human supervision. The data subject has the right not to be subject to a decision based solely on automated processing, including profiling, which produces legal effects concerning him or her or similarly significantly affects him or her.

The Data Controller shall inform the data subject of the measures taken as a result of the request within one month of receipt of the request.

8. **Handling a data security incident**

A data breach is a breach of security that results in the accidental or unlawful destruction, loss, alteration, unauthorized disclosure of, or access to, processed personal data.

Upon detection of an incident, the Data Controller shall immediately take the necessary technical and organizational measures to mitigate the damage and protect the data. If the incident is likely to result in a high risk to the rights and freedoms of the Data Subjects, the Data Controller shall inform the Data Subject without undue delay of the nature of the incident, its likely consequences, and the remedial measures taken. The Data Controller shall report the incident to the National Data Protection and Freedom of Information Authority (1055 Budapest, Falk Miksa utca 9-11.) in accordance with the legal requirements (no later than 72 hours).

If you have a problem or question regarding data processing related to the OpenDLP software, you should first contact the Data Controllers. You can also assert your rights before the competent court of the place of residence of the data subject or the seat of the Data Controller, or you can contact the Hungarian National Authority for Data Protection and Freedom of Information (1055 Budapest, Falk Miksa utca 9-11; [www.naih.hu](http://www.naih.hu)) or, in relation to data processing involving the UK jurisdiction, the Information Commissioner’s Office (ICO, Wycliffe House, Water Lane, Wilmslow, Cheshire, SK9 5AF, www.ico.org.uk). . You can find more information about the court procedure on the website www.birosag.hu, and about the Authority on the website www.naih.hu.”

9. **Final provisions**

During the processing of personal data detailed in this Notice, personal data may be transferred to a third country or to an international organization under appropriate guarantees.

The Data Controller reserves the right to unilaterally amend this Notice with effect for the future. It will inform the Data Subjects about the amendments via its website.



If you have any questions about how we handle your data, please contact us at [privacy@sortitionfoundation.org](mailto:privacy@sortitionfoundation.org).

_Last updated: September 2026_
