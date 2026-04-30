---
source_url: https://dbnsa.sharepoint.com/sites/ComplianceOfficers93/Regulatory Repository/Rest of World/Germany/2. Analysis/20230510_Technische Richtlinie Safe-Server V1.10 en-GB - ISMS.pdf
country: Germany
document_name: Safe Server Technical Guideline
source_file: 20230510_Technische Richtlinie Safe-Server V1.10 en-GB - ISMS.pdf
source_url: https://dbnsa.sharepoint.com/sites/ComplianceOfficers93/Regulatory%20Repository/Rest%20of%20World/Germany/2.%20Analysis/20230510_Technische%20Richtlinie%20Safe-Server%20V1.10%20en-GB%20-%20ISMS.pdf
extracted_date: 2026-04-30
jurisdiction: Germany
description: Technical guideline for providers on the operation of safe servers and event transmission within the Multi-state Gaming Supervision System (LUGAS).
regulatory_body: Ministry of the Interior and Sport of the State of Saxony-Anhalt
---

# Safe Server Technical Guideline

Multi-state Gaming Supervision System (LUGAS)

Publisher: Dataport AöR  
on behalf of the  
Ministry of the Interior and Sport of the State  
of Saxony-Anhalt

Version: 1.10  
10.05.2023

## Table of contents

1 List of amendments 5  
2 Introduction 12  
3 Scope 13  
4 Definitions of terms 13  
4.1 Domain terms 13  
4.2 Technical terms 14  
5 Specification of the safe server 15  
5.1 Information security concerns 15  
5.1.1 Certificate requirements 15  
5.1.2 Data integrity 16  
5.1.3 Authenticity & non-repudiation of data 16  
5.1.4 Resilience 16  
5.2 Event interface 16  
5.2.1 Structure 16  
5.2.2 Chunks 17  
5.2.3 Chunk signature 17  
5.2.4 Compression of the chunks 20  
5.2.5 Pick up the events 20  
5.2.6 Assignment of player data 26  
5.2.7 Feedback 26  
6 Character set and data types 29  
7 Events 31  
7.1 Personal data players 33  
7.1.1 Register 33  
7.1.2 Data change 35  
7.1.3 Data confirmation 36  
7.1.4 Confirmation of provisional match 38  
7.1.5 Status 39  
7.2 Player suspension 41  
7.2.1 Activate lock 41  
7.2.2 Unlock 43  
7.3 Provider-related player limits 45  
7.3.1 Set limit 45  
7.3.2 Delete limit 48  
7.4 Matches 49  
7.4.1 Start Single Player Match 49  
7.4.2 End Single Player Match 52  
7.4.3 Start Community Player Match Players 55  
7.4.4 End Community Player Match Players 58  
7.4.5 End Community Player Game 61  
7.5 Payments 62  
7.5.1 Add payment method 62  
7.5.2 Remove payment method 64  
7.5.3 Deposit 66  
7.5.4 Disbursement 68  
7.5.5 Transaction game account 71  
7.6 Interaction between player and provider 74  
7.6.1 Log-in 74  
7.6.2 Player Declaration Virtual Slot Game 75  
7.6.3 Player timeout 76  
7.6.4 Reality check 77  
7.6.5 Reality Check Confirmation 78  
7.6.6 Reminder change of area 79  
7.6.7 Request for correction Limit fixing 80  
7.6.8 Information statistical data 81  
7.6.9 Inducement inactivation 82  
7.7 Use of the central files 84  
7.7.1 Transmission of player data 84  
7.7.2 Cross-provider deposit limit 86  
7.7.3 Deposit 88  
7.7.4 Active status 90  
7.7.5 Lock check 92  
7.8 Provider data 93  
7.8.1 Add area 93  
7.8.2 Add single player game 94  
7.8.3 Approval single player game 95  
7.8.4 Add Community Player Game 98  
7.8.5 Approval Community Player Game 99  
7.8.6 Authorisation to set a deviating limit 102  
7.8.7 Add payment service 103  
7.8.8 Remove payment service 104  
7.9 Correction events 106  
7.9.1 Change event 106  
7.9.2 Delete event 108  
7.10 Sports betting 110  
7.10.1 Create betting offer 110  
7.10.2 Change the start time of the betting offer 112  
7.10.3 Place bet 113  
7.10.4 Changes to a placed bet 116  
7.10.5 Weather result 119  
7.10.6 Change in weather result 121  
8 Examples 122  
8.1 Initial connection safe server 122  
8.2 Player creates an account 123  
8.3 Average play cycle 123  
8.4 Procedure for annual player data verification by the provider 124  
9 Annexes 124

## 1 List of changes

### Version 1.10 from 10.05.2023

- Adaptation for all events and examples
  - Field eventId added
- Adjustment for Deposit, Payout, End Single Player Match, Remove Payment Method
  - Field playerId added
- Adjustments to event interface
  - Removing the requirement to sort events by time within a chunk
  - Remove the requirement that all events within a chunk must have the same date.
- Adjustments to events
  - Remove the requirement that all events within a chunk must have the same date.
  - Changes to notes Plausibility check text adapted
  - Adding correction events
    - Change event
    - Delete event
- Adjustments to the allocation of player data
  - Linking player data and event via eventId
  - Adaptation examples
- Adding events for sports betting
  - Adding an event to create betting offers
  - Adding an event to change the start time of a betting offer
  - Adding an event to place a bet
  - Adding an event to modify a placed bet
  - Adding an event for the weather result
  - Adding an event to change a weather result
- Remove the request of a following transaction Game account in:
  - Start Single Player Match
  - End Single Player Match
  - Start Community Player Match Players
  - End Community Player Match Players
- Adjustment to transaction game account
  - Replace oldBalance and newBalance with amount
  - Removing the transactionType "SinglePlayerMatchResult" and "MultiPlayerMatchResult
  - Adding the transactionType "Bonus
  - Adaptation of the notes
- Adjustment to information statistical data
  - Adding the balance field
- Adjustment of the notes on bonus money at:
  - Deposit
  - Reporting the deposit to the central files
- Adaptation of the example Average play cycle
- Adding a note to stock players when registering

### Version 1.9 from 26.04.2023

- Adjustments to transaction game account
  - New field note inserted
  - New transaction types inserted
  - Notes on the use of the new fields and transaction types added

### Version 1.8 from 11.04.2023

- Removing chapters
  - Operating phases
  - Special Events Setup Phase
- Removing allowed phases from all events
- Adjustment of the Register Event
  - New field balance with notes inserted.
- Adjustments to End Single Player Match
  - Adding an example of an abandoned match
  - Adding hints for an abandoned match
- Adaptation of the example of rejected chunk in feedback
- Adjustment of the notes at:
  - Register
  - Confirmation preliminary match
  - Status
  - Activate lock
  - Set limit
  - Add payment method
- Adaptation of the examples
- Adjustments to deposit.
  - New field depositId inserted.
  - Notes on the use of the new field added.
- Adjustments to reporting of the deposit to the central files.
  - New field depositId inserted.
- Adjustments to disbursement.
  - New field payoutId inserted.
  - Notes on the use of the new field added.
- Adjustments to transaction game account.
  - Change of the field transactionReference to transactionReferenceId
  - Change the transactionReferenceId for deposit and payout.

### Version 1.7.1 from 01.12.2022

- Remove userName from the examples in signature of the chunks
- Replacing the userName example in the notes on non-mandatory fields in events
- Adjustment of the wording of the description for networkHost and networkGameId in Start
  Community Player Match Player.

### Version 1.7 from 22.11.2022

- Adjustments to the collection of events
  - Add PersonalPlayerData in the response body
  - Explanation of the matching between data of a chunk and PersonalPlayerData
- Adjustments to personal data for players
  - Removing some fields when registering and changing data
  - Events Register and Data Change must now be linked to personal data
- Correction Explanation for result Unspecified in lock check
- Revision of the specification for feedback after a chunk has been picked up.

### Version 1.6 from 26.09.2022

- Adjustments in Safe-Server specification.
  - Explanation of the certificate for communication and signing.
  - Add chapter Requirements for certificates.
  - Remove chapter Procedure for signing and transmitting the data.
  - Certificate to sign in authenticity & non-repudiation of data.
  - Certificate in Resilience Communication.
- Additions in signature of the chunks.
  - Instructions with examples for qualified electronic time stamps.
  - Instructions with examples for signature.
  - Naming and solution for indentation errors.

### Version 1.5.1 from 21.06.2022

- Additions and clarifications in safe server specification.
  - Summary of certificates.
  - Note on the EventId
- Additions in events
  - Closing time of the last chunk of a day.

### Version 1.5 from 25.03.2022

- Realignment Chapter Safe Server Specification.

### Version 1.4 from 14.01.2022

- Adjustments to character set and data types
  - Exclusive use of UTF-8 as encoding of the JSON files.
- Adjustments to events
  - Change the directory structure to YYYY/MM/DD.
  - Adjustment of the file storage restrictions.
  - Adjustment of the sorting key.
- Adjustments to Register
  - Note on dealing with late registration of players.
  - Note on dealing with player status in the set-up phase.
- Adjustments to data change
  - Added note on additional data change in the central files.
- Adjustments to data confirmation
  - Note on player status after data confirmation.
- Adjustments to status
  - Added references to dealing with annual data review.
  - "intent" is now a conditional mandatory field.
- Adjustments to Start Single Player Match
  - Changed "isFreeOfCharge" to "charge" with different values. Note on the handling of
    bonus money added.
  - Note on the submission of a permit inserted.
- Adjustments to Start Community Player Match Players
  - Changed "isFreeOfCharge" to "charge" with different values. Note on the handling of
    bonus money added.
  - Note on the submission of a permit inserted.
- Adaptations to Permit Single Player Play
  - Note on the submission of a permit inserted.
  - Introductory text: "more than 5 seconds" changed to "at least 5 seconds".
- Adaptations to Approval Community Player Game
  - Note on the submission of a permit inserted.
- Adjustments to end community player match players.
  - New fields "bonusStake" and "bonusRevenue" added. Added a note on how to
    handle bonus money.
  - Note on handling transactions Player Account added.
  - Examples of bonus money and real and bonus money introduced.
- Adjustments to end single player match.
  - New fields "bonusStake" and "bonusRevenue" added. Added a note on how to
    handle bonus money.
  - Note on handling transactions Player Account added.
  - Examples of bonus money and real and bonus money introduced.
- Adjustments to deposit (player).
  - Added note on the interaction of central file reconciliation, player account transaction
    and deposits.
  - Note that deposits from a bonus money account do not have to be reconciled with
    the central files.
- Adjustments to deposit (central files).
  - Added note on the interaction of central file reconciliation, player account transaction
    and deposits.
  - Note that deposits from a bonus money account do not need to be reconciled with
    the central files.
- Adjustments to disbursement.
  - Note on handling transaction player account added
- Add adjustments to payment method
  - Field methodName added, otherData removed, idData converted.
  - Examples adapted accordingly.
- Additions in examples
  - Added example for annual data review.

### Version 1.3 from 30.09.2021

- Adjustments to Start Single Player Match
- Adjustments to lock check
- Adjustments to Average Play Cycle
- Adaptation of heading and reference to transmission of player data

### Version 1.2 from 03.08.2021

- Adaptation by examples

### Version 1.1 from 24.06.2021

- Adjustments to the introduction
- Adaptations to the specification of the safe server
- Adjustments to conditions and restrictions of the file format of events
- Supplementary information Operating phases
- Adaptations and specifications in events
  - Payment
  - Deposit
  - Approval Community Player Game
  - Start Single Player Match
  - Start Community Player Match Players
  - Status
  - Unlock
  - Add payment service
  - Add payment method

## 2 Introduction

As of 1 July 2021, the State Treaty on the New Regulation of Gambling in Germany of
29 October 2020 (State Treaty on Gaming 2021 - GlüStV 2021).

In the future, the supervision of gambling on the Internet will be carried out by the Joint
Gambling Authority of the Federal States with headquarters in Halle (Saale). During a
transitional period until 31 December 2022, individual federal states will perform gambling law tasks
with nationwide responsibility pursuant to Section 27p GlüStV 2021. Against this background, the
competent gambling supervisory authority of the State of Saxony-Anhalt, the State
Administration Office, will in particular be responsible for the management of the information
technology systems provided for the monitoring of the gambling market on the Internet pursuant
to the State Gambling Treaty from 1 July 2021.

The connection to these systems is obligatory for permitted providers of games of chance on the
internet according to the State Treaty on Games of Chance 2021.

The interstate gambling supervision system (LUGAS) created for this purpose consists of the
central files, consisting of

- the deposit limit setting file (limit file),
- the parallel play prevention file (activity file)

and the evaluation system together.

The competent authority shall use the evaluation system regulated in Section 6i (2) GlüStV 2021
as a tool for the supervision of gambling on the Internet. It ensures that the data collected by
the gambling providers (hereinafter referred to as providers) themselves are evaluated and
reviewed with regard to compliance with the GlüStV.

Providers are required to accurately record all required data.

The collection and provision of data is carried out independently by the providers on so-called safe
servers, which are to be set up and operated by the providers at their own expense. The data must be
stored on the safe server in a digitally unchangeable form. This means that the provider is responsible
for ensuring that no access to the automatically created files is possible without the express request
of the authority and that no data is lost or damaged due to technical defects. The provider must
enable control at any time, including direct access by the competent supervisory authority. The
evaluation system continuously accesses the safe servers and retrieves the provided data for
processing.

This document defines the data required to interact with the systems and describes how these are
to be stored by the providers on the safe servers.

## 3 Scope

This guideline must be implemented by all providers who offer online games of chance on the
internet in accordance with the permit pursuant to § 4 GlüStV 2021. By applying for a licence, the
provider agrees to the current scope of this directive.

Version 1.1 of this guideline dated 24.06.2021 is effective as of 01.07.2021. It is subject to constant
revision and will be updated on a regular basis after it becomes effective. Further information on
the specific mode of updating will be announced by the competent gaming supervisory authority.

## 4 Definitions of terms

### 4.1 Domain terms

| Term | Definition |
|---|---|
| **Provider** | A provider is an organiser of sports betting, online casino games, online poker or virtual slot machine games on the internet who has obtained a permit pursuant to Section 4 GlüStV 2021. |
| **Authority** | This term is a short form for the "Joint Gambling Authority of the Länder", which is established pursuant to Section 27a GlüStV 2021 for the purpose of performing the duties of gambling supervision. |
| **Match** | A match is a game of a game, e.g. a round on a virtual slot machine. |
| **Game** | A game is the expression of a type of game, e.g. a specific slot machine. |
| **Type of game** | In the current state of the guideline, two types of game are depicted: Single player game and community player game. |
| **Player** | A player is a natural person who uses the services of a provider. |
| **Payment service** | Defines the method of a payment and the manner, with which a recipient or sender of a payment is identified. |
| **Payment method** | All information necessary to identify the recipient or sender of a payment within the framework of a payment service. |

### 4.2 Technical terms

| Term | Definition |
|---|---|
| **Byte** | A sequence of eight yes and no information to represent 256 different values. |
| **URI** | The Uniform Resource Identifier is an identifier for resources on the Internet. |
| **HTTPS** | The Hypertext Transfer Protocol Secure is an encrypted communication protocol for the Internet. |
| **API** | An application programming interface is an interface of computer programs. |

## 5 Specification of the Safe Server

Each provider has a server that can be accessed from the Internet and from which the data is fetched in
the form of chunks. The server must provide the interface described in the chapter Event Interface. Only
requests from LUGAS may be accepted. LUGAS uses a client certificate for authentication. The
required information is provided to the provider in advance by the authority.

The storage and protection of the data described in the Events chapter is the responsibility of the
provider. The provider must comply with the requirements described in the chapter on information
security.

For the integration of the safe server, the provider must transmit the URI and two certificates to
LUGAS.

Certificate for communication: The first certificate is used for secure communication based on
mTLS between the safe server and LUGAS (resilience).

Certificate for signing: The second certificate is used in combination with a so-called qualified
electronic time stamp to ensure the authenticity and integrity of the transmitted data. The
certificate ensures the origin of the data (authenticity & non-repudiation of the data). The
qualified electronic time stamp ensures that the data has not been changed since the time
of the time stamp (integrity of the data).

### 5.1 Information security issues

#### 5.1.1 Certificate requirements

The certificates provided by the provider for the communication and signing of the data must be
issued by an official CA. The identity of the provider must be ensured by the CA by means of
"organisation validation" (2.23.140.1.2.2). The required parameters of the cryptographic procedure for
signing and transmitting the data are based on the TR-02102 of the
BSI1
. DSA ECDSA (NIST 256 or
prime256v1) + SHA-256 is explicitly required. The maximum term of a key is 3 years. Should the
algorithm or the key length be prematurely classified as insecure by the BSI, new keys must be
created and exchanged. The authority reserves the right to adapt the requirements should changes
become necessary.

1
https://www.bsi.bund.de/SharedDocs/Downloads/DE/BSI/Publikationen/TechnischeRichtlinien/TR02102/BSI-TR-
02102.pdf

#### 5.1.2 Data integrity

A so-called qualified electronic time stamp is used to ensure that the data within a chunk cannot
be changed by an independent body. The provider is obliged to sign the chunks with a qualified
electronic time stamp from a recognised certification body. Recognised certification bodies can be
found in the EU Trust
List2
. The exact regulation for the formation of the time stamp is described in
the section Signature of the chunks.

2
https://esignature.ec.europa.eu/efda/tl-browser/#/screen/home

#### 5.1.3 Authenticity & non-repudiation of data

To ensure that the data originates from the provider, another signature is added to the data of a
chunk. For this purpose, the certificate is used for signing. The private key is used to sign the
chunk. The exact rule for forming the signature is described in the section Signature of the
chunks.

#### 5.1.4 Resilience

Communication between LUGAS and the providers is based on mTLS (Mutual TLS). For this
purpose, the authority publishes a corresponding client certificate. The operator of the safe saver is
instructed to only accept connections where the other party can identify itself with such a valid client
certificate of the authority. To enable a smooth transition with new client certificates, the authority
publishes successor certificates in good time. New client certificates are always immediately
valid, but do not replace the predecessor. This applies insofar as the authority does not
communicate otherwise.

The safe server must be uniquely identifiable by LUGAS. For this purpose, the safe server must use
the certificate transmitted to the authority for communication.

### 5.2 Event interface

#### 5.2.1 Structure

The events are returned to LUGAS in so-called chunks. The events must always be arranged in
the logical order, e.g. the status of a player may only be transmitted after registration for this player. It
is permitted to file retroactively effective events, see Correction events. UTC must be used as the
time zone for the eventTime.

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  
17

{
"id": "3608e046-c713-4864-b559-867018fadb5c",
"data": [
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "PlayerRegistration",
"eventTime": "2022-06-08T01:12:59.000000Z",
"playerId": "1",
},
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "PlayerRegistration",
"eventTime": "2022-06-08T01:14:55.000000Z",
"playerId": "77",
}
]
}

1 e1e9da8e1c1d9ca643c371354d6d58ffde4036589ca294981e9a14a46fd  
2 faa2f1a3a2173ebba9ec73781fe95a0da25a3

#### 5.2.2 Chunks

To limit the size of the responses, the events of a day are divided into chunks. A chunk contains a
maximum of 200,000 events. As soon as a chunk is closed because it is no longer being
processed, it can be retrieved as a successor.

#### 5.2.3 Chunk signature

Each chunk must be signed to ensure the authenticity of the data. The JSON Web Signature (JWS),
specified by RFC
75153
, is used for this.

1. Qualified electronic time stamp

The formation of the qualified electronic time stamp is done according to RFC
31614.

1. The data of the chunk is used for the hash to be signed. The JSON string must be UTF-8
   encoded for this.
2. Calculation of the hash value e.g. with the algorithm SHA-384 as hex.

Line breaks inserted for readability

3
https://www.rfc-editor.org/rfc/rfc7515 4https://www.rfc-
editor.org/rfc/rfc3161

1 MIIERQYJKoZIhvcNAQcCoIIENjCCBDICAQMxCzAJBgUrDgMCGgUAMI...

1 {  
2 "x-qtimestamp": "  
MIIERQYJKoZIhvcNAQcCoIIENjCCBDICAQMxCzAJBgUrDgMCGgUAMI...  
"  
3 }

1 ASCII(BASE64URL(UTF8(JWS Protected Header)) \|\| '.') \|\| JWS  
Payload

3. Transmission of the hash value and the algorithm used to the certification body for
   qualified electronic time stamps.
4. Timestamp token of the certification authority Base64 encoded (shortened in the example).

2. Signature

The signature is made according to RFC
75155
, using the signature with detached content
according to Appendix
F6
and unencoded content according to RFC
77977
. The qualified time
stamp must be stored as a
protected
header8 under the key x-qtimestamp.

1. The payload is the data of the chunk (see above). The JSON string must be UTF-8
   encoded for this .
2. The qualified timestamp is stored in the Protected Header with the key x-qtimestamp
   deposited.

Example of the header

Timestamp token displayed abbreviated

5
https://www.rfc-editor.org/rfc/rfc7515  
6
https://www.rfc-
editor.org/rfc/rfc7515#appendix-F  
7
https://www.rfc-
editor.org/rfc/rfc7797  
8
https://www.rfc-editor.org/rfc/rfc7515#section-
4  
9
https://www.rfc-editor.org/rfc/rfc7797 10https://www.rfc-
editor.org/rfc/rfc7515#appendix-F

3. The protected header is signed together with the payload using the certificate for
   signing.

Signature Input (cf. RFC
77979
):

4. The payload is then removed in the signature token (detached
   content10
   ).

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11

{
"id": "3608e046-c713-4864-b559-867018fadb5c",
"data": [
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "PlayerRegistration",
"eventTime": "2022-06-08T01:12:59.000000Z",
"playerId": "1",
}
]
}

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14

{
"payload": {
XX
XX
XX
XX
XX
XX
XX
XX},
"id": "3608e046-c713-4864-b559-867018fadb5c",
"data": [
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "PlayerRegistration",
"eventTime": "2022-06-08T01:12:59.000000Z",
"playerId": "1",
}
]
...
}

x-qtimestamp is shown shortened, line breaks inserted for readability

The signature is stored accordingly in the signature block of the response.

Common mistakes

- In order to validate the signature, the indentation of the JSON must be the same for the signature
  and in the HTTP body for the content of the payload. The usual indentation of JSON can
  therefore not be used.

Indentation for the signature

Different indentation in the HTTP body (additional spaces represented by 'X')

1 eyJhbGciOiJFUzI1NiIsIngtcXRpbWVzdGFtcCI6Ik1JSUlFUlFZSktvWklo  
2 dmNOQVFjQ29JSUVOakNDQkRJQ0FRTXhDekFKQmdVckRnTUNHZ1VBTUkuLi4i  
3 fQ..i199fkkjpDfPW6PeR3vDPT8VNpWA_3aiHgYnNHALmeR6PYF_qGZRrSjy  
4 uMXHvvlRtIMt0wS9wJgSzdtH95H15Q

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14

{
"payload": {
"id": "3608e046-c713-4864-b559-867018fadb5c",
"data": [
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "PlayerRegistration",
"eventTime": "2022-06-08T01:12:59.000000Z",
"playerId": "1",
}
]
},
...
}

Correct indentation in the HTTP body

To avoid this problem, it is recommended to serialise JSON without indentation.

#### 5.2.4 Compression of the chunks

The chunks can be compressed using
GZIP11
or
Brotli12
. For this purpose, the Content- Encoding
header is specified in the response.

#### 5.2.5 Pick up the events

To fetch the events, LUGAS sends a request to the interface with the last chunk fetched.
The successor of the chunk specified via the path is then returned. Only chunks that have already
been completed and are no longer being modified are returned. By means of the Accept-Encoding
header, LUGAS specifies the supported compression algorithms. The authenticity of the payload
object is ensured by the JSON Web signature (RFC
751513
) in the signature field. The signature with
detached content according to Appendix
F14
and unencoded content according to RFC
779715
is
used.

Path:

11
https://www.gnu.org/software/gzip/  
12
https://github.com/google/brotli  
13
https://www.rfc-
editor.org/rfc/rfc7515  
14
https://www.rfc-
editor.org/rfc/rfc7515#appendix-F 15https://www.rfc-
editor.org/rfc/rfc7797

| Name | Type | Description | Example |
|---|---|---|---|
| chunk | string | The ID of the requested chunk. | "20220512-2" |

- For the first chunk, the value initial must be specified for chunk.

Request
header:

| Name | Type | Description | Example |
|---|---|---|---|
| Accept- Encoding | array[string] | List of the LUGAS-supported Compression algorithms (compression of the chunks) | List["gzip", "br"] |

Answers

- 404 (NOT FOUND) - No successor to the requested chunk exists yet.
- 200 (OK) - The requested chunk was found.

Response header:

| Name | Data type | Description | Mandatory |
|---|---|---|---|
| Content encoding | string | Defines the encoding used (such as compression) according to the official specification16 | Yes |

Response Body:

| Name | Data type | Description | Mandatory |
|---|---|---|---|
| payload | json | Contains the requested chunk and further information. Information (See payload) | Yes |

16https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Encoding

1 GET /events/{chunk}/next

| Name | Data type | Description | Mandatory |
|---|---|---|---|
| signature | string | Signature of the payload with detached content and Unencoded Content | Yes |
| personalPlayerData | array[json] | Data of the players for the requested chunk | Yes |

Payload:

| Name | Data type | Description | Mandatory |
|---|---|---|---|
| id | string | Unique identifier of the chunk | Yes |
| predecessor | json | Contains the id and signature of the previous chunk. | Conditional mandatory field |
| data | array[json] | Contains list of events in chronological and logical order. | Yes |

PersonalPlayerData:

| Name | Data type | Description | Mandatory |
|---|---|---|---|
| eventId | string | The Id of the event for which personal data are to be provided. | Yes |
| givenName | string | The first name of the player | Yes |
| lastName | string | The name of the player | Yes |
| street | string | The street of the player's current address | Yes |
| number | string | The house number(s) of the player's current address | Yes |
| postcode | string | The postcode of the player's current place of residence | Yes |
| place | string | The place of residence of the player's current address | Yes |
| area | string | The state of the player's current residence | Yes |

| Name | Data type | Description | Mandatory |
|---|---|---|---|
| countryAlpha2Codestring | The alpha2Code of the country from the current | Yes |
|  | place of residence of the player. |  |
| birthDate | string | The date of birth of the player | Yes |
| birthPlace | string | The birthplace of the player | Yes |
| birthName | string | The birth name of the player | Yes |

Predecessor:

| Name | Data type | Description | Mandatory |
|---|---|---|---|
| id | string | Unique identifier of the previous chunk | Yes |
| signature | string | Signature of the previous chunk | Yes |

Notes

- The predecessor object always contains the identifier and signature of the previous
  chunk. Here, a reference to the chunk from the example first chunk is shown.
- The very first chunk is a special case. Since there is no predecessor here, the predecessor
  object is null and is not specified.
- If the player's primary residence is outside Germany, the provider may use a secondary
  residence in Germany instead of the primary residence. This can be a registered secondary
  residence or a place of habitual residence. The usual place of residence is a place where
  the player does not only stay temporarily, but with a certain duration and regularity.

1 GET /events/initial/next

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  
17  
18  
19  
20  
21  
22  
23  
24  
25  
26  
27  
28  
29  
30  
31  
32  
33  
34  
35  
36  
37  
38  
39

{
"payload": {
"id": "3608e046-c713-4864-b559-867018fadb5c",
"data": [
{
"eventId": "1c674ff4-ec1e-4821-b206-
ab851cb7ec82", "eventName": "PlayerRegistration",
"eventTime": "2022-06-08T01:12:59.000000Z",
"playerId": "1
},
{
"eventId": "2c674ff4-ec1e-4821-b206-
ab851cb7ec83", "eventName":
"ProviderAreaRegistration", "eventTime": "2022-
06-08T01:13:00.000000Z",
}, "areaId": "214",
""name"": ""Slot Machine Paradise""
}
]
},
"signature": "eyJhbGciOiJFUzI1NiIsImI2NCI6ZmFsc2UsImNyaXQiOlsiYjY0Il0
sInR5cCI6IkpXVCJ9..7smqrCvRv_-K6toM2K6ze6CxVEFiACWiD5vWDrx8HoetBd
zdT3gSI0J9o-aEML-e0nfXBYTQPDg1HTC5OpYyOA",
"personalPlayerData": [
{
"eventId": "1c674ff4-ec1e-4821-b206-
ab851cb7ec82", "givenName": "MAX",
"lastName": "MUSTERMANN",
"street": "GRONINGERWEG",
}, "number": "15",
"postCode": "06128",
"place": "HALLE SAALE",
"area": "DE-ST",
"countryAlpha2Code": "DE",
"birthDate": "1990-11-20",
"birthPlace": "MÜNSTER",
"birthName": "TEICHLER".
}
]
}

Example First Chunk:

1 GET /events/3608e046-c713-4864-b559-867018fadb5c/next

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  
17  
18  
19  
20  
21  
22  
23  
24  
25  
26  
27  
28  
29  
30  
31  
32  
33  
34  
35  
36  
37  
38

{
"payload": {
"id": "ccc03e9c-2cec-44d2-a165-
836813baf87c", "predecessor": {
"id": "3608e046-c713-4864-b559-867018fadb5c",
"signature": "
eyJhbGciOiJFUzI1NiIsImI2NCI6ZmFsc2UsImNyaXQiOlsiYjY0Il0
sInR5cCI6IkpXVCJ9..7smqrCvRv_-.
K6toM2K6ze6CxVEFiACWiD5vWDrx8HoetBd
zdT3gSI0J9o-aEML-e0nfXBYTQPDg1HTC5OpYyOA"
},
"data": [
{
"eventId": "1c674ff4-ec1e-4821-b206-