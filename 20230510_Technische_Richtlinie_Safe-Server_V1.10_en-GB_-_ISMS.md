---
country: Germany
document_name: Safe Server Technical Guideline
source_file: 20230510_Technische Richtlinie Safe-Server V1.10 en-GB - ISMS.pdf
extracted_date: 2026-04-30
jurisdiction: Germany
---

# Safe Server Technical Guideline

**Multi-state Gaming Supervision System (LUGAS)**

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
- Adjustment of the wording of the description for networkHost and networkGameId in Start Community Player Match Player.

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
  - Changed "isFreeOfCharge" to "charge" with different values. Note on the handling of bonus money added.
  - Note on the submission of a permit inserted.
- Adjustments to Start Community Player Match Players
  - Changed "isFreeOfCharge" to "charge" with different values. Note on the handling of bonus money added.
  - Note on the submission of a permit inserted.
- Adaptations to Permit Single Player Play
  - Note on the submission of a permit inserted.
  - Introductory text: "more than 5 seconds" changed to "at least 5 seconds".
- Adaptations to Approval Community Player Game
  - Note on the submission of a permit inserted.
- Adjustments to end community player match players.
  - New fields "bonusStake" and "bonusRevenue" added. Added a note on how to handle bonus money.
  - Note on handling transactions Player Account added.
  - Examples of bonus money and real and bonus money introduced.
- Adjustments to end single player match.
  - New fields "bonusStake" and "bonusRevenue" added. Added a note on how to handle bonus money.
  - Note on handling transactions Player Account added.
  - Examples of bonus money and real and bonus money introduced.
- Adjustments to deposit (player).
  - Added note on the interaction of central file reconciliation, player account transaction and deposits.
  - Note that deposits from a bonus money account do not have to be reconciled with the central files.
- Adjustments to deposit (central files).
  - Added note on the interaction of central file reconciliation, player account transaction and deposits.
  - Note that deposits from a bonus money account do not need to be reconciled with the central files.
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

As of 1 July 2021, the State Treaty on the New Regulation of Gambling in Germany of 29 October 2020 (State Treaty on Gaming 2021 - GlüStV 2021).

In the future, the supervision of gambling on the Internet will be carried out by the Joint Gambling Authority of the Federal States with headquarters in Halle (Saale). During a transitional period until 31 December 2022, individual federal states will perform gambling law tasks with nationwide responsibility pursuant to Section 27p GlüStV 2021. Against this background, the competent gambling supervisory authority of the State of Saxony-Anhalt, the State Administration Office, will in particular be responsible for the management of the information technology systems provided for the monitoring of the gambling market on the Internet pursuant to the State Gambling Treaty from 1 July 2021.

The connection to these systems is obligatory for permitted providers of games of chance on the internet according to the State Treaty on Games of Chance 2021.

The interstate gambling supervision system (LUGAS) created for this purpose consists of the central files, consisting of

- the deposit limit setting file (limit file),
- the parallel play prevention file (activity file)

and the evaluation system together.

The competent authority shall use the evaluation system regulated in Section 6i (2) GlüStV 2021 as a tool for the supervision of gambling on the Internet. It ensures that the data collected by the gambling providers (hereinafter referred to as providers) themselves are evaluated and reviewed with regard to compliance with the GlüStV.

Providers are required to accurately record all required data.

The collection and provision of data is carried out independently by the providers on so-called safe servers, which are to be set up and operated by the providers at their own expense. The data must be stored on the safe server in a digitally unchangeable form. This means that the provider is responsible for ensuring that no access to the automatically created files is possible without the express request of the authority and that no data is lost or damaged due to technical defects. The provider must enable control at any time, including direct access by the competent supervisory authority. The evaluation system continuously accesses the safe servers and retrieves the provided data for processing.

This document defines the data required to interact with the systems and describes how these are to be stored by the providers on the safe servers.

## 3 Scope

This guideline must be implemented by all providers who offer online games of chance on the internet in accordance with the permit pursuant to § 4 GlüStV 2021. By applying for a licence, the provider agrees to the current scope of this directive.

Version 1.1 of this guideline dated 24.06.2021 is effective as of 01.07.2021. It is subject to constant revision and will be updated on a regular basis after it becomes effective. Further information on the specific mode of updating will be announced by the competent gaming supervisory authority.

## 4 Definitions of terms

### 4.1 Domain terms

**Provider** A provider is an organiser of sports betting, online casino games, online poker or virtual slot machine games on the internet who has obtained a permit pursuant to Section 4 GlüStV 2021.

**Authority** This term is a short form for the "Joint Gambling Authority of the Länder", which is established pursuant to Section 27a GlüStV 2021 for the purpose of performing the duties of gambling supervision.

**Match** A match is a game of a game, e.g. a round on a virtual slot machine.

**Game** A game is the expression of a type of game, e.g. a specific slot machine.

**Type of game** In the current state of the guideline, two types of game are depicted: Single player game and community player game.

**Player** A player is a natural person who uses the services of a provider.

**Payment service** Defines the method of a payment and the manner, with which a recipient or sender of a payment is identified.

**Payment method** All information necessary to identify the recipient or sender of a payment within the framework of a payment service.

### 4.2 Technical terms

**Byte** A sequence of eight yes and no information to represent 256 different values.

**URI** The Uniform Resource Identifier is an identifier for resources on the Internet.

**HTTPS** The Hypertext Transfer Protocol Secure is an encrypted communication protocol for the Internet.

**API** An application programming interface is an interface of computer programs.

## 5 Specification of the Safe Server

Each provider has a server that can be accessed from the Internet and from which the data is fetched in the form of chunks. The server must provide the interface described in the chapter Event Interface. Only requests from LUGAS may be accepted. LUGAS uses a client certificate for authentication. The required information is provided to the provider in advance by the authority.

The storage and protection of the data described in the Events chapter is the responsibility of the provider. The provider must comply with the requirements described in the chapter on information security.

For the integration of the safe server, the provider must transmit the URI and two certificates to LUGAS.

Certificate for communication: The first certificate is used for secure communication based on mTLS between the safe server and LUGAS (resilience).

Certificate for signing: The second certificate is used in combination with a so-called qualified electronic time stamp to ensure the authenticity and integrity of the transmitted data. The certificate ensures the origin of the data (authenticity & non-repudiation of the data). The qualified electronic time stamp ensures that the data has not been changed since the time of the time stamp (integrity of the data).

### 5.1 Information security issues

#### 5.1.1 Certificate requirements

The certificates provided by the provider for the communication and signing of the data must be issued by an official CA. The identity of the provider must be ensured by the CA by means of "organisation validation" (2.23.140.1.2.2). The required parameters of the cryptographic procedure for signing and transmitting the data are based on the TR-02102 of the BSI1. DSA ECDSA (NIST 256 or prime256v1) + SHA-256 is explicitly required. The maximum term of a key is 3 years. Should the algorithm or the key length be prematurely classified as insecure by the BSI, new keys must be created and exchanged. The authority reserves the right to adapt the requirements should changes become necessary.

1 https://www.bsi.bund.de/SharedDocs/Downloads/DE/BSI/Publikationen/TechnischeRichtlinien/TR02102/BSI-TR-02102.pdf

#### 5.1.2 Data integrity

A so-called qualified electronic time stamp is used to ensure that the data within a chunk cannot be changed by an independent body. The provider is obliged to sign the chunks with a qualified electronic time stamp from a recognised certification body. Recognised certification bodies can be found in the EU Trust List2. The exact regulation for the formation of the time stamp is described in the section Signature of the chunks.

2 https://esignature.ec.europa.eu/efda/tl-browser/#/screen/home

#### 5.1.3 Authenticity & non-repudiation of data

To ensure that the data originates from the provider, another signature is added to the data of a chunk. For this purpose, the certificate is used for signing. The private key is used to sign the chunk. The exact rule for forming the signature is described in the section Signature of the chunks.

#### 5.1.4 Resilience

Communication between LUGAS and the providers is based on mTLS (Mutual TLS). For this purpose, the authority publishes a corresponding client certificate. The operator of the safe saver is instructed to only accept connections where the other party can identify itself with such a valid client certificate of the authority. To enable a smooth transition with new client certificates, the authority publishes successor certificates in good time. New client certificates are always immediately valid, but do not replace the predecessor. This applies insofar as the authority does not communicate otherwise.

The safe server must be uniquely identifiable by LUGAS. For this purpose, the safe server must use the certificate transmitted to the authority for communication.

### 5.2 Event interface

#### 5.2.1 Structure

The events are returned to LUGAS in so-called chunks. The events must always be arranged in the logical order, e.g. the status of a player may only be transmitted after registration for this player. It is permitted to file retroactively effective events, see Correction events. UTC must be used as the time zone for the eventTime.

```json
{
  "id": "3608e046-c713-4864-b559-867018fadb5c",
  "data": [
    {
      "eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
      "eventName": "PlayerRegistration",
      "eventTime": "2022-06-08T01:12:59.000000Z",
      "playerId": "1"
    },
    {
      "eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
      "eventName": "PlayerRegistration",
      "eventTime": "2022-06-08T01:14:55.000000Z",
      "playerId": "77"
    }
  ]
}
```

```
e1e9da8e1c1d9ca643c371354d6d58ffde4036589ca294981e9a14a46fdfaa2f1a3a2173ebba9ec73781fe95a0da25a3
```

#### 5.2.2 Chunks

To limit the size of the responses, the events of a day are divided into chunks. A chunk contains a maximum of 200,000 events. As soon as a chunk is closed because it is no longer being processed, it can be retrieved as a successor.

#### 5.2.3 Chunk signature

Each chunk must be signed to ensure the authenticity of the data. The JSON Web Signature (JWS), specified by RFC 75153, is used for this.

1. Qualified electronic time stamp

   The formation of the qualified electronic time stamp is done according to RFC 31614.

   1. The data of the chunk is used for the hash to be signed. The JSON string must be UTF-8 encoded for this.
   2. Calculation of the hash value e.g. with the algorithm SHA-384 as hex.

   Line breaks inserted for readability

   ```
   MIIERQYJKoZIhvcNAQcCoIIENjCCBDICAQMxCzAJBgUrDgMCGgUAMI...
   ```

   3. Transmission of the hash value and the algorithm used to the certification body for qualified electronic time stamps.
   4. Timestamp token of the certification authority Base64 encoded (shortened in the example).

2. Signature

   The signature is made according to RFC 75155, using the signature with detached content according to Appendix F6 and unencoded content according to RFC 77977. The qualified time stamp must be stored as a protected header8 under the key x-qtimestamp.

   1. The payload is the data of the chunk (see above). The JSON string must be UTF-8 encoded for this.
   2. The qualified timestamp is stored in the Protected Header with the key x-qtimestamp deposited.

      Example of the header  
      Timestamp token displayed abbreviated

      ```json
      {
        "x-qtimestamp": "MIIERQYJKoZIhvcNAQcCoIIENjCCBDICAQMxCzAJBgUrDgMCGgUAMI..."
      }
      ```

   3. The protected header is signed together with the payload using the certificate for signing.

      Signature Input (cf. RFC 77979):

      ```
      ASCII(BASE64URL(UTF8(JWS Protected Header)) || '.') || JWS Payload
      ```

   4. The payload is then removed in the signature token (detached content10).

3 https://www.rfc-editor.org/rfc/rfc7515  
4 https://www.rfc-editor.org/rfc/rfc3161  
5 https://www.rfc-editor.org/rfc/rfc7515  
6 https://www.rfc-editor.org/rfc/rfc7515#appendix-F  
7 https://www.rfc-editor.org/rfc/rfc7797  
8 https://www.rfc-editor.org/rfc/rfc7515#section-4  
9 https://www.rfc-editor.org/rfc/rfc7797  
10 https://www.rfc-editor.org/rfc/rfc7515#appendix-F

The signature is stored accordingly in the signature block of the response.

Common mistakes

- In order to validate the signature, the indentation of the JSON must be the same for the signature and in the HTTP body for the content of the payload. The usual indentation of JSON can therefore not be used.

Indentation for the signature

```json
{
"id": "3608e046-c713-4864-b559-867018fadb5c",
"data": [
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "PlayerRegistration",
"eventTime": "2022-06-08T01:12:59.000000Z",
"playerId": "1"
}
]
}
```

Different indentation in the HTTP body (additional spaces represented by 'X')

```json
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
"playerId": "1"
}
]
...
}
```

x-qtimestamp is shown shortened, line breaks inserted for readability

```
eyJhbGciOiJFUzI1NiIsIngtcXRpbWVzdGFtcCI6Ik1JSUlFUlFZSktvWklo
dmNOQVFjQ29JSUVOakNDQkRJQ0FRTXhDekFKQmdVckRnTUNHZ1VBTUkuLi4i
fQ..i199fkkjpDfPW6PeR3vDPT8VNpWA_3aiHgYnNHALmeR6PYF_qGZRrSjy
uMXHvvlRtIMt0wS9wJgSzdtH95H15Q
```

Correct indentation in the HTTP body

```json
{
"payload": {
"id": "3608e046-c713-4864-b559-867018fadb5c",
"data": [
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "PlayerRegistration",
"eventTime": "2022-06-08T01:12:59.000000Z",
"playerId": "1"
}
]
},
...
}
```

To avoid this problem, it is recommended to serialise JSON without indentation.

#### 5.2.4 Compression of the chunks

The chunks can be compressed using GZIP11 or Brotli12. For this purpose, the Content-Encoding header is specified in the response.

11 https://www.gnu.org/software/gzip/  
12 https://github.com/google/brotli

#### 5.2.5 Pick up the events

To fetch the events, LUGAS sends a request to the interface with the last chunk fetched.

The successor of the chunk specified via the path is then returned. Only chunks that have already been completed and are no longer being modified are returned. By means of the Accept-Encoding header, LUGAS specifies the supported compression algorithms. The authenticity of the payload object is ensured by the JSON Web signature (RFC 751513) in the signature field. The signature with detached content according to Appendix F14 and unencoded content according to RFC 779715 is used.

Path:

13 https://www.rfc-editor.org/rfc/rfc7515  
14 https://www.rfc-editor.org/rfc/rfc7515#appendix-F  
15 https://www.rfc-editor.org/rfc/rfc7797

**Name**: chunk  
**Type**: string  
**Description**: The ID of the requested chunk.  
**Example**: "20220512-2"

- For the first chunk, the value initial must be specified for chunk.

Request header:

**Name**: Accept-Encoding  
**Type**: array[string]  
**Description**: List of the LUGAS-supported Compression algorithms (compression of the chunks)  
**Example**: List["gzip", "br"]

Answers

- 404 (NOT FOUND) - No successor to the requested chunk exists yet.
- 200 (OK) - The requested chunk was found.

Response header:

**Content encoding**  
Data type: string  
Description: Defines the encoding used (such as compression) according to the official specification16  
Mandatory: Yes

Response Body:

**payload**  
Data type: json  
Description: Contains the requested chunk and further information. Information (See payload)  
Mandatory: Yes

16 https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Encoding

`GET /events/{chunk}/next`

**signature**  
Data type: string  
Description: Signature of the payload with detached content and Unencoded Content  
Mandatory: Yes

**personalPlayerData**  
Data type: array[json]  
Description: Data of the players for the requested chunk  
Mandatory: Yes

Payload:

**id**  
Data type: string  
Description: Unique identifier of the chunk  
Mandatory: Yes

**predecessor**  
Data type: json  
Description: Contains the id and signature of the previous chunk.  
Mandatory: Conditional mandatory field

**data**  
Data type: array[json]  
Description: Contains list of events in chronological and logical order.  
Mandatory: Yes

PersonalPlayerData:

**eventId**  
Data type: string  
Description: The Id of the event for which personal data are to be provided.  
Mandatory: Yes

**givenName**  
Data type: string  
Description: The first name of the player  
Mandatory: Yes

**lastName**  
Data type: string  
Description: The name of the player  
Mandatory: Yes

**street**  
Data type: string  
Description: The street of the player's current address  
Mandatory: Yes

**number**  
Data type: string  
Description: The house number(s) of the player's current address  
Mandatory: Yes

**postcode**  
Data type: string  
Description: The postcode of the player's current place of residence  
Mandatory: Yes

**place**  
Data type: string  
Description: The place of residence of the player's current address  
Mandatory: Yes

**area**  
Data type: string  
Description: The state of the player's current residence  
Mandatory: Yes

**countryAlpha2Code**  
Data type: string  
Description: The alpha2Code of the country from the current place of residence of the player.  
Mandatory: Yes

**birthDate**  
Data type: string  
Description: The date of birth of the player  
Mandatory: Yes

**birthPlace**  
Data type: string  
Description: The birthplace of the player  
Mandatory: Yes

**birthName**  
Data type: string  
Description: The birth name of the player  
Mandatory: Yes

Predecessor:

**id**  
Data type: string  
Description: Unique identifier of the previous chunk  
Mandatory: Yes

**signature**  
Data type: string  
Description: Signature of the previous chunk  
Mandatory: Yes

Notes

- The predecessor object always contains the identifier and signature of the previous chunk. Here, a reference to the chunk from the example first chunk is shown.
- The very first chunk is a special case. Since there is no predecessor here, the predecessor object is null and is not specified.
- If the player's primary residence is outside Germany, the provider may use a secondary residence in Germany instead of the primary residence. This can be a registered secondary residence or a place of habitual residence. The usual place of residence is a place where the player does not only stay temporarily, but with a certain duration and regularity.

Example First Chunk:

`GET /events/initial/next`

```json
{
"payload": {
"id": "3608e046-c713-4864-b559-867018fadb5c",
"data": [
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "PlayerRegistration",
"eventTime": "2022-06-08T01:12:59.000000Z",
"playerId": "1
},
{
"eventId": "2c674ff4-ec1e-4821-b206-ab851cb7ec83",
"eventName": "ProviderAreaRegistration",
"eventTime": "2022-06-08T01:13:00.000000Z"
},
"areaId": "214",
"\"name\"": "\"Slot Machine Paradise\""
}
]
},
"signature": "eyJhbGciOiJFUzI1NiIsImI2NCI6ZmFsc2UsImNyaXQiOlsiYjY0Il0sInR5cCI6IkpXVCJ9..7smqrCvRv_-K6toM2K6ze6CxVEFiACWiD5vWDrx8HoetBdzdT3gSI0J9o-aEML-e0nfXBYTQPDg1HTC5OpYyOA",
"personalPlayerData": [
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"givenName": "MAX",
"lastName": "MUSTERMANN",
"street": "GRONINGERWEG"
},
"number": "15",
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
```

Example Normal Chunk:

`GET /events/3608e046-c713-4864-b559-867018fadb5c/next`

```json
{
"payload": {
"id": "ccc03e9c-2cec-44d2-a165-836813baf87c",
"predecessor": {
"id": "3608e046-c713-4864-b559-867018fadb5c",
"signature": "eyJhbGciOiJFUzI1NiIsImI2NCI6ZmFsc2UsImNyaXQiOlsiYjY0Il0sInR5cCI6IkpXVCJ9..7smqrCvRv_-.K6toM2K6ze6CxVEFiACWiD5vWDrx8HoetBdzdT3gSI0J9o-aEML-e0nfXBYTQPDg1HTC5OpYyOA"
},
"data": [
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "PlayerRegistration",
"eventTime": "2022-06-08T01:18:02.000000Z",
"playerId": "22
}
]
},
"signature": "eyJhbGciOiJFUzI1NiIsImI2NCI6ZmFsc2UsImNyaXQiOlsiYjY0Il0sInR5cCI6IkpXVCJ9..sR8VoO-SigEwW3Vyn_rjnyafE-vVky6kPdl4OuoTDeuQR-H9SxDEo6loZGZuKOizoOmixgj0CXr5lDIfyoSmA",
"personalPlayerData": [
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"givenName": "KARIN",
"lastName": "MUSTERFRAU",
"street": "HAUPTWEG",
"number": "36",
"postCode": "39104",
"place": "MAGDEBURG",
"area": "DE-ST",
"countryAlpha2Code": "DE",
"birthDate": "1996-10-13",
"birthPlace": "MUNICH",
"birthName": "FISCHER"
}
]
}
```

#### 5.2.6 Assignment of player data

For each event in data that must be linked to personal data (see personal data player), exactly one corresponding entry must be made in personalPlayerData. The assignment is made via the eventId.

#### 5.2.7 Feedback

Feedback from LUGAS on the processing of the events.

After processing each chunk, LUGAS sends feedback to the safe server. In principle, three different results can be reported:

- Success: The chunk was processed completely. No validation errors occurred.
- SuccessWithInvalidEvents: The chunk was processed completely. One or more events are invalid and have been ignored.
- Canceled: The chunk could not be processed.

Example of successful processing without a validation error (Success):

`POST /feedback`

```json
{
"result": "success",
"chunkId": "chunk1",
"processedEvents": 1500
}
```

In the event that the chunk can be processed successfully, but errors occur with individual events (SuccessWithInvalidEvents), a description of the error is stored in the invalidEvents list for each event.

```json
{
"result": "Canceled",
"chunkId": "chunk1",
"processedEvents": 0,
"errorMessage": "The server certificate used is unknown"
}
```

```json
{
"result": "SuccessWithInvalidEvents",
"chunkId": "chunk1",
"processedEvents": 1500,
"invalidEvents": [
{
"eventNumber": 1004,
"errors": {
"birthDate": [
"The player is not of age."
]
}
},
{
"eventNumber": 1005,
"errors": {
"playerId": [
"No player with this PlayerId is registered."
]
}
}
]
}
```

Note: Invalid events are ignored by LUGAS, so that consequential errors can occur as in the example above. Here, during registration (event number: 1004), it is determined that the player is not of age at the time of registration. Therefore, the registration event is ignored. In the following PlayerStatus event (event number: 1005), the PlayerId for this player is therefore not known to LUGAS.

Possible reasons for rejecting a chunk (Canceled) include:

- Error with the server certificate used
- Errors in the structure of the response so that, for example, the JSON cannot be parsed.
- Invalid signature or timestamp
- No match of the predecessor data with the predecessor

A description of the error is given in the errorMessage field.

Request-Body:

**result**  
Data type: string  
Description: Feedback status. Possible values "Success", "SuccessWithInvalidEvents" or "Canceled".  
Mandatory: Yes

**chunkId**  
Data type: string  
Description: Unique identifier of the processing chunk  
Mandatory: Yes

**processedEvents**  
Data type: int  
Description: Number of processing events within the chunk  
Mandatory: Yes

**errorMessage**  
Data type: string  
Description: Description of the error if the chunk could not be processed  
Mandatory: No

**invalidEvents**  
Data type: array[object]  
Description: List of invalid events with error description  
Mandatory: No

Invalid Events:

**eventNumber**  
Data type: int  
Description: Position of the faulty event within the chunk (0-based)  
Mandatory: Yes

**errors**  
Data type: object  
Description: List of error descriptions (string) for affected fields of the event  
Mandatory: Yes

Answers

- 204 (OK) - The feedback was successfully received.

## 6 Character set and data types

Events are transmitted as JSON and are accordingly based on the JSON standard17. For further explanation of individual fields and their restrictions, the following identifiers are used in this document:

**string** A JSON string. Control characters and leading, trailing or consecutive spaces are not allowed. The length is limited to 4096 characters.  
Example: `"Hello world!"`

**smallString** A string with the restriction that the length is limited to 256 characters.  
Example: `"Hello World!"`

**identifier** A string with the restriction that the length is limited to 36 characters. When comparing two pieces of data of this type, it is case sensitive. It is suitable to hold any 64-bit number. It is unique to its intended purpose, such as player, payment method, single player game, single player match, etc., and is assigned by the provider unless otherwise defined in this policy (e.g. for eventName, which is predefined for each event).  
Example: `"5emh/t5chEyN8S68yG1Rug=="`

**date** A JSON string containing a date and formatted according to ISO standard 860118.  
Example: `"2021‑01‑26"`

**datetime** A JSON string containing a date, time and the corresponding time zone, formatted according to ISO standard 8601.  
Example: `"2021‑01‑26T09:37:37Z"`

**decimal** A JSON number for which no exponential notation and for which a maximum of two decimal places are permitted. The value range corresponds to the definition of the data type decimal in C# with the restriction of two decimal places.  
Example: `19.47`

**money** A decimal that expresses an amount of money. This is always expressed in euros.  
Example: `19.47`

**bool** Specifies a JSON true value.  
Example: `true`

**int** A decimal with the restriction that decimal places are not permitted.  
Example: `123`

17 https://www.json.org/  
18 https://www.iso.org/iso-8601-date-and-time-format.html

## 7 Events

The events are transmitted in the form of JSON within chunks. A chunk is limited to 200,000 events. All events for the previous day should be available by 2 a.m. (UTC) on the following day at the latest.

Example

Data within a chunk:

```json
[
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "PlayerDataApproved",
"eventTime": "2020-01-01T09:42:29.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug=="
},
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "PlayerStatus",
"eventTime": "2020-01-01T09:43:29.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug==",
"status": "VerificationPending",
"intent": "RegularCycle"
}
]
```

The following conditions and restrictions apply:

- Chunks must be completely written as soon as a new chunk is created.
- Once a chunk has been transferred, it may not be renamed, moved, deleted or changed without the authority's instruction.

Note on non-mandatory fields:

Non-mandatory fields in the events, which are not filled in, may not be included in the filed files. It should be noted that each submitted, non-mandatory field is associated with a concrete meaning and in part significantly influences the entire interpretive purpose of the event.

Conversely, this means that these fields are mandatory under certain conditions if the interpretation is necessary. In general, the rule applies that non-mandatory fields must be filled in if the data to be entered exist for the purpose of the specific event. For example, when registering a player, it is not permissible not to transmit the field automaticProfitTransaction if the player has specified an amount from which winnings are to be automatically transferred to his bank account. All further information on this can be found in the notes under each event.

Note on event validation:

When processing the files, the formal correctness is checked. If, for example, the signature of a chunk is invalid, the import of all events is paused until the problem has been corrected. The provider is informed about the feedback.

For the purpose of validation, the provider shall communicate in special events the authorisations in relation to permitted games and payment services that it has received from the authority.

The following is an overview of all events that must be provided by the providers.

### 7.1 Personal data player

All events related to player data are listed here. In this context, registration and data modification are to be linked with personal data (see Assignment of player data).

#### 7.1.1 Register

A player registers with his data with the provider.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "PlayerRegistration".

**eventTime**  
Data type: datetime  
Description: Time of registration of the player  
Mandatory: yes  
Restriction: -

**playerId**  
Data type: identifier  
Description: Identification of the player with the provider  
Mandatory: yes  
Restriction: -

**automaticProfitTransaction**  
Data type: money  
Description: Amount limit above which winnings are automatically paid to the player.  
Mandatory: no  
Restriction: Must be positive.

**balance**  
Data type: money  
Description: Current account balance of the player (if registration of existing player)  
Mandatory: no

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "PlayerRegistration",
"eventTime": "2020-11-20T09:42:29.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug=="
}
```

Notes

- In order to participate in games of chance, players are required to set up a gaming account pursuant to Section 6a (2) GlüStV 2021. Participation in games without a gaming account is not permitted.
- Pursuant to Section 4 (3) GlüStV 2021, players must be at least 18 years old to register.
- After registration, the player receives the status "VerificationPending" with the intent "Registration", which must also be deposited as an event (see status), as his data must be verified by a suitable and reliable procedure (see § 6a para. 2 GlüStV 2021).
- A registered player is entitled to participate provisionally in games of chance. For this purpose, he/she confirms that he/she has taken note of the instructions (see Confirmation of Provisional Gambling).
- Pursuant to Section 6b (3) GlüStV 2021, providers are obliged to provide a function with which it can be determined that winnings above a certain amount are automatically paid out. This amount must be stored in automaticProfitTransaction if the player uses this function.
- If the player registered before the initial setup of the safe server or is a player who was not previously required to register, the player's account balance must be entered in the balance field. If a successful data check has already been carried out for the player in accordance with Section 6a (5) GlüStV 2021, a corresponding event (see status) must be entered. If the current status of the player differs from this or if no data check has been completed yet, the current status must be transmitted.
- The eventTime may be before the time of the chunk for a stock player message for all associated events. Among others, the following events are to be transmitted subsequently: Add payment method, Activate lock, Cross-provider deposit limit, Transmission of player data, Provider-related player limits.
- The events Add payment method, Activate lock and Set provider-related player limit are not to be transmitted if they have already been removed by a corresponding event Remove payment method, Delete provider-related player limit or Remove lock before the initial connection to the safe servers.

#### 7.1.2 Data change

The player updates his data with the provider.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "PlayerUpdate".

**eventTime**  
Data type: datetime  
Description: Time of the data change of the player  
Mandatory: yes  
Restriction: -

**playerId**  
Data type: identifier  
Description: Identification of the player with the provider  
Mandatory: yes  
Restriction: Reference to an existing player

**automaticProfitTransaction**  
Data type: money  
Description: Amount limit above which winnings are automatically transferred to the player's bank account.  
Mandatory: no  
Restriction: Must be positive.

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "PlayerUpdate",
"eventTime": "2020-12-20T09:42:29.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug=="
}
```

Notes

- If a player's data changes, it must be verified again according to § 6a par. 5 p. 3 and 4 GlüStV 2021.
- The player receives the status "VerificationPending" with intent "DataChanged", which must also be stored as an event (see status). This status must also be set,
- if the player changes his data in the course of the annual data check.
- In case of a data change, the player data in the central files must also be changed.

#### 7.1.3 Data confirmation

The player confirms the accuracy of his data. This happens in the course of a regular check of his data by the provider, which is regulated according to § 6a para. 5 GlüStV 2021.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "PlayerDataApproved".

**eventTime**  
Data type: datetime  
Description: Time of confirmation of the player  
Mandatory: yes  
Restriction: -

**playerId**  
Data type: identifier  
Description: Identification of the player with the provider  
Mandatory: yes  
Restriction: Reference to an existing player

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "PlayerDataApproved",
"eventTime": "2020-11-20T09:42:29.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug=="
}
```

Notes

- Pursuant to Section 6a (5) sentence 5 GlüStV 2021, the provider is obliged to carry out this verification at the latest one year after the last confirmation before the player can participate in a new match.
- The player receives the status "VerificationPending" with intent "RegularCycle", which must also be stored as an event (see status).
- As soon as the player has confirmed his data in this process, he receives the status "Verified", which also has to be deposited as an event (see status).

#### 7.1.4 Confirmation preliminary match

The player wishes to participate in games of chance on a provisional basis pursuant to Section 6a (4) GlüStV 2021 and confirms that he/she has taken note of the information on the restrictions on provisional play.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "PlayerTemporarily".

**eventTime**  
Data type: datetime  
Description: Time at which the player confirms the clues  
Mandatory: yes  
Restriction: -

**playerId**  
Data type: identifier  
Description: Identification of the player with the provider  
Mandatory: yes  
Restriction: Reference to an existing player

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "PlayerTemporarily",
"eventTime": "2020-11-20T09:42:29.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug=="
}
```

Notes

- The player receives the status "VerificationPending" with intent "TemporarilyAccepted", which must also be stored as an event (see status).

#### 7.1.5 Status

A player goes through several states while holding a player account with the provider.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "PlayerStatus".

**eventTime**  
Data type: datetime  
Description: Time of the status change of the player  
Mandatory: yes  
Restriction: -

**playerId**  
Data type: identifier  
Description: Identification of the player with the provider  
Mandatory: yes  
Restriction: Reference to an existing player

**status**  
Data type: identifier  
Description: The current status of the player  
Mandatory: yes  
Restriction: See table below for valid values

**intent**  
Data type: identifier  
Description: A possible further explanatory cause  
Mandatory: conditional mandatory field  
Restriction: See table below for valid values

The following statuses are possible:

**VerificationPending** The player's data is verified. With the exception of the preliminary game, the player may not participate in games of chance in this status.

**VerificationFailed** The player data could not be verified. The player is not allowed to play.

**Verified** The player's details have been verified and the player is allowed to play in full.

**AccountClosed** The player has closed his gaming account with the provider.

For the states "VerificationPending" and "VerificationFailed" one of the following causes shall be obligatory. Each of these causes is valid in both states. If a verification fails in the "VerificationPending" state, the state shall be set to "VerificationFailed" and the cause shall be accepted.

**Registration** The player has registered with the provider.

**TemporarilyAccepted** The player has agreed that, until the initial verification of his data, only provisional, restricted gambling is possible pursuant to Section 6a (4) GlüStV 2021.

**DataChanged** The player has updated his data in accordance with Section 6a (5) GlüStV 2021.

**ChangedPayment** The player has changed his payment information in accordance with § 6a para. 6 GlüStV 2021 amended.

**RegularCycle** The player has confirmed his data in the course of the regular data check pursuant to Section 6a (5) GlüStV 2021.

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "PlayerStatus",
"eventTime": "2020-11-20T09:42:29.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug==",
"status": "VerificationPending",
"intent": "RegularCycle"
}
```

Notes

- If status contains the value "VerificationPending" or "VerificationFailed", intent must be set.
- If the provider initiates the annual verification of the player data pursuant to Section 6a (5) GlüStV 2021, the player receives the status "VerificationPending" with intent "RegularCycle".
- If the player changes his data due to the annual review, the intent changes from "RegularCycle" to "DataChanged".
- If the player confirms his data, he receives the status "Verified", which must also be deposited as an event (see data confirmation).

### 7.2 Player suspension

#### 7.2.1 Activate lock

A player has been suspended in the provider's system.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "PlayerSuspension".

**eventTime**  
Data type: datetime  
Description: Time of activation of the lock  
Mandatory: yes  
Restriction: -

**playerId**  
Data type: identifier  
Description: Identification of the player with the provider  
Mandatory: yes  
Restriction: Reference to an existing player

**suspensionReason**  
Data type: identifier  
Description: The reason for the lock  
Mandatory: yes  
Restriction: See table below for valid values

**suspensionEndsAt**  
Data type: dateTime  
Description: Indicates when the temporary lock, if any, ends.  
Mandatory: no  
Restriction: -

The following reasons are possible:

**Addiction** A player is banned by the provider due to a recognised addiction problem in accordance with Section 6i (1) GlüStV 2021.

**Bot** A player is informed by the provider due to the use of a Bot software in online poker, which constitutes an offence under Section 22b (3) GlüStV 2021, is blocked.

**Legal** A player is blocked by the provider on one of the grounds listed in Section 6a (8) GlüStV 2021. These are suspicion of unlawfully acquired winnings, as well as violations of legal provisions, in particular in the area of money laundering, of the present State Treaty or of conditions for the gaming account.

**Voluntary** A player independently triggers an immediate short term ban after § Section 6i (3) GlüStV 2021.

If the player is banned by the provider for any other reason, this event is not to be deducted.

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "PlayerSuspension",
"eventTime": "2020-11-20T09:42:29.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug==",
"suspensionReason": "Legal"
}
```

Notes

- If it is a temporary suspension that expires automatically, enter suspensionEndsAt. Explicit reporting of the lifting of this suspension (see Lifting a suspension) is then not mandatory.
- Locks with suspensionReason "Voluntary" are always to be indicated as temporary locks of 24 hours.
- If a player is banned for more than one reason, this event must be indicated once per reason on the safe server.
- If a lock with a specific reason has already been specified that has not yet expired, a new event with the same suspensionReason is regarded as an update of the known lock. There is no differentiation of the suspensions within a suspension reason.
- The most concrete possible reason for suspension must always be given. If a player has been found to be using bot software, suspensionReason must be indicated as "Bot", although "Legal" would also be correct in terms of content.

#### 7.2.2 Unlock

A block triggered at the provider during the match is lifted.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "PlayerResumption".

**eventTime**  
Data type: datetime  
Description: Time when the suspension is lifted if suspensionEndsAt is not transmitted.  
Mandatory: yes  
Restriction: -

**playerId**  
Data type: identifier  
Description: Identification of the player with the provider  
Mandatory: yes  
Restriction: Reference to an existing player

**suspensionReason**  
Data type: identifier  
Description: The reason for the lock  
Mandatory: yes  
Restriction: See table above for valid values

**suspensionEndsAt**  
Data type: dateTime  
Description: Indicates when the temporary lock, if any, ends.  
Mandatory: no  
Restriction: -

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "PlayerResumption",
"eventTime": "2020-11-20T09:42:29.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug==",
"suspensionReason": "Legal"
}
```

Notes

- This event can be transmitted to extend, shorten and lift a temporary lock (multiple times if necessary).
- Notwithstanding the above, it is not permitted to extend suspensions with suspensionReason "Voluntary".
- If suspensionEndsAt is not transmitted, the lock is considered lifted from the point of view of the evaluation system at the time of eventTime.

### 7.3 Provider-related player limits

#### 7.3.1 Set limit

The player sets a limit pursuant to Section 6c (2) sentence 1 GlüStV 2021, which only applies to the provider.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "LocalLimitSet".

**eventTime**  
Data type: datetime  
Description: Time of the setting of the local limit at the provider by the player  
Mandatory: yes  
Restriction: -

**playerId**  
Data type: identifier  
Description: Identification of the player with the provider  
Mandatory: yes  
Restriction: Reference to an existing player

**limitScope**  
Data type: identifier  
Description: Limit type  
Mandatory: yes  
Restriction: See table below for valid values

**timeUnit**  
Data type: identifier  
Description: Limit interval  
Mandatory: yes  
Restriction: See table below for valid values

**amount**  
Data type: money  
Description: The set limit  
Mandatory: yes  
Restriction: Must be positive.

The following limits are possible:

**Deposit** The limit refers to the sum of the amount of deposits that may be made in the interval.

**Stake** The limit refers to the sum of the stakes that may be placed in the interval.

**Loss** The limit refers to the sum of the loss that may be made in the interval.

The following intervals are possible:

**Day** A daily limit

**Week** A weekly limit

**Month** A monthly limit

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "LocalLimitSet",
"eventTime": "2020-11-20T09:42:29.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug==",
"limitScope": "Stake",
"timeUnit": "Month",
"amount": 499.47
}
```

Notes

- All limits set by the player shall be carried forward.
- Only one limit can be set per limitScope and timeUnit.
- The setting of a provider-related monthly deposit limit has no influence on the existing cross-provider monthly deposit limit pursuant to Section 6c (1) GlüStV 2021.

#### 7.3.2 Delete limit

The player removes a registered provider-related limit.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "LocalLimitUnset".

**eventTime**  
Data type: datetime  
Description: Time of removal of the local limit at the provider by the player  
Mandatory: yes  
Restriction: -

**playerId**  
Data type: identifier  
Description: Identification of the player with the provider  
Mandatory: yes  
Restriction: Reference to an existing player

**limitScope**  
Data type: identifier  
Description: Limit type  
Mandatory: yes  
Restriction: See table above for valid values

**timeUnit**  
Data type: identifier  
Description: Limit interval  
Mandatory: yes  
Restriction: See table above for valid values

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "LocalLimitUnset",
"eventTime": "2020-11-20T09:42:29.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug==",
"limitScope": "Stake",
"timeUnit": "Month
}
```

Notes

- With regard to becoming effective, the deletion of a limit behaves like an increase to the highest possible value according to § 6c para. 3 sentence 2 GlüStV 2021. Thus, it continues to be valid within the legal protection period and any violations that may occur are detected by the evaluation system.

### 7.4 Matches

#### 7.4.1 Start Single Player Match

Information on the start of a match that a player is conducting alone.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "SinglePlayerMatch".

**eventTime**  
Data type: datetime  
Description: Time at which the player started the match  
Mandatory: yes  
Restriction: -

**playerId**  
Data type: identifier  
Description: Identification of the player with the provider  
Mandatory: yes  
Restriction: Reference to an existing player

**gameId**  
Data type: identifier  
Description: Unique identifier of the game  
Mandatory: yes  
Restriction: Reference to an existing single player game

**matchId**  
Data type: identifier  
Description: Unique identifier of the current match  
Mandatory: yes  
Restriction: -

**profitRatio**  
Data type: decimal  
Description: Specifies the average payout ratio per one euro wagered pursuant to Section 22a (3) sentence 2 GlüStV 2021 resulting from the verification by a certification body. If such a certificate does not exist, the average payout ratio that should mathematically result after an infinite number of games shall be indicated.  
Mandatory: yes  
Restriction: Must be greater than 0.

**charge**  
Data type: identifier  
Description: Indicates what type of game it is  
Mandatory: yes  
Restriction: See table below for valid values.

The following types are possible:

**Real** It is a paid game

**Free** This is a free entertainment offer

**Bonus** This is a game with bonus money

**RealAndBonus** This is a game with real and bonus money

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "SinglePlayerMatch",
"eventTime": "2020-11-20T09:51:29.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug==",
"gameId": "123456",
"matchId": "HD5Ojhp9b0qD4LBJw7vL1A==",
"profitRatio": 12.47,
"charge": "real"
}
```

Notes

- gameId is a reference to the single player games submitted by the provider (see Add single player game).
- Before starting a game, it is necessary that a permit has been created for that game (see Permit Single Player Game).
- In the case of round-based single-player games, each round is to be treated as a separate match pursuant to Section 22a (4) sentence 2 GlüStV 2021, which must fully comply with the legal requirements such as maximum stake and explicit player declaration.
- This event is to be deposited for promotions as well as free offers according to § 6j GlüStV 2021.
- If charge contains the value "bonus", "bonusStake" and "bonusRevenue" must be specified in the end single player match.
- If charge contains the value "RealAndBonus", both "bonusStake" and "bonusRevenue" as well as "stake" and "revenue" must be specified in the end single player match.

#### 7.4.2 End Single Player Match

Information about the end of a match that a player has played alone.

Fields

**eventId** identifier Unique Id of the event  
**eventName** identifier Unique identifier of the event  
**eventTime** datetime Time at which the match ended  
**playerId** identifier Identification of the player with the provider  
**matchId** identifier Unique identifier of the finished match  
**stake** money Total real money wagered by the player during the match  
**revenue** money Total real money profit or loss of the player through the match.  
yes -  
yes Must contain the value "SinglePlayerMatchResult".  
yes -  
yes Reference to an existing player  
yes Reference to the player's existing match  
yes Must not be negative.  
yes -

**bonusStake** money Total bonus money wagered by the player during the match  
**bonusRevenue** money Total bonus money Winning or losing the player through the match  
conditional mandatory field  
conditional mandatory field  
Must not be negative. See note.  
See note.

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "SinglePlayerMatchResult",
"eventTime": "2020-11-20T09:51:29.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug==",
"matchId": "HD5Ojhp9b0qD4LBJw7vL1A==",
"stake": 19.47,
"revenue": -15
}
```

Example bonus money

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "SinglePlayerMatchResult",
"eventTime": "2020-11-20T09:51:29.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug==",
"matchId": "HD5Ojhp9b0qD4LBJw7vL1A==",
"stake": 0,
"revenue": 0,
"bonusStake": 15,
"bonusRevenue": -3
}
```

Example real and bonus money

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "SinglePlayerMatchResult",
"eventTime": "2020-11-20T09:51:29.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug==",
"matchId": "HD5Ojhp9b0qD4LBJw7vL1A==",
"stake": 19.47,
"revenue": -15,
"bonusStake": 2.47,
"bonusRevenue": 2
}
```

Example abandonment of a match

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "SinglePlayerMatchResult",
"eventTime": "2020-11-20T09:51:29.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug==",
"matchId": "HD5Ojhp9b0qD4LBJw7vL1A==",
"stake": 0,
"revenue": 0,
"bonusStake": 0,
"bonusRevenue": 0
}
```

Notes

- matchId is a reference to an ongoing single player match (see Start Single Player Match).
- This event is to be deposited for both gratuitous and monetary matches.
- In the case of a free offer, stake and revenue are to be set to 0.
- bonusStake and bonusRevenue are to be set if it is a single player match with bonus money or real and bonus money (see Start Single Player Match).
- If a match is cancelled due to technical problems, stake, revenue, bonusStake and bonusRevenue is set to 0.

#### 7.4.3 Start Community Player Match Players

Information on how to enter a match that a player is conducting with other players.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "MultiPlayerMatch".

**eventTime**  
Data type: datetime  
Description: The date on which the player joined the community player match.  
Mandatory: yes  
Restriction: -

**playerId**  
Data type: identifier  
Description: Identification of the player with the provider  
Mandatory: yes  
Restriction: Reference to an existing player

**gameId**  
Data type: identifier  
Description: Unique identifier of the game  
Mandatory: yes  
Restriction: Reference to an existing community player game

**matchId**  
Data type: identifier  
Description: Unique identifier of the match  
Mandatory: yes  
Restriction: -

**charge**  
Data type: identifier  
Description: Indicates what type of game it is  
Mandatory: yes  
Restriction: See table below for valid values.

**tableNumber**  
Data type: identifier  
Description: The table at which the player is playing.  
Mandatory: yes  
Restriction: -

**networkHost**  
Data type: smallString  
Description: Name of the provider in a network match  
Mandatory: no  
Restriction: -

**networkGameId**  
Data type: identifier  
Description: ID of the network game at a Netwerk-Match  
Mandatory: no  
Restriction: -

The following types are possible:

**Real** It is a paid game

**Free** This is a free entertainment offer

**Bonus** This is a game with bonus money

**RealAndBonus** This is a game with real and bonus money

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "MultiPlayerMatch",
"eventTime": "2020-11-20T09:51:29.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug==",
"gameId": "789",
"matchId": "HD5Ojhp9b0qD4LBJw7vL1A==",
"charge": "real",
"tableNumber": "T4411x1",
"networkHost": "ZPOKER",
"networkGameId": "MyweoQRQe0KPxR9enkjWbA=="
}
```

Notes

- gameId is a reference to the community player games submitted by the provider (see Add community player game).
- Before starting a game, it is necessary that a permit has been created for this game (see Permit Community Player Game).
- A community player match is started with the participation of the first player. An explicit declaration of the start of the match is not provided. eventTime defines the time when the player begins to participate in the match and does not allow any conclusions to be drawn about when the match as a whole was started.
- If it is a network match, networkHost and networkGameId are mandatory.
- This event is to be deposited for promotions as well as free offers according to § 6j GlüStV 2021.
- If charge contains the value "bonus", "bonusStake" and "bonusRevenue" must be specified in End Community Player Match Player.
- If charge contains the value "RealAndBonus", both "bonusStake" and "bonusRevenue" as well as "stake" and "revenue" must be specified in End Community Player Match Player.

#### 7.4.4 End Community Player Match Players

Information about leaving a match that a player is doing with other players.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "Multi-PlayerMatchResult".

**eventTime**  
Data type: datetime  
Description: Time at which the player left the match  
Mandatory: yes  
Restriction: -

**playerId**  
Data type: identifier  
Description: Identification of the player with the provider  
Mandatory: yes  
Restriction: Reference to an existing player

**matchId**  
Data type: identifier  
Description: Unique identifier of the currently running match  
Mandatory: yes  
Restriction: Reference to the ongoing community player match

**stake**  
Data type: money  
Description: Total real money wagered by the player during the match  
Mandatory: yes  
Restriction: Must not be negative.

**rake**  
Data type: money  
Description: The fee that the player effectively had to pay to participate in the community player match.  
Mandatory: yes  
Restriction: Must not be negative.

**totalRake**  
Data type: money  
Description: Total fee for participation in the Community Player Match  
Mandatory: yes  
Restriction: Must not be negative.

**revenue**  
Data type: money  
Description: Player's total real money profit or loss from the match  
Mandatory: yes  
Restriction: -

**bonusStake**  
Data type: money  
Description: Total bonus money wagered by the player during the match  
Mandatory: conditional mandatory field  
Restriction: Must not be negative. See note.

**bonusRevenue**  
Data type: money  
Description: Total bonus money won or lost by the player through the match  
Mandatory: conditional mandatory field  
Restriction: See note.

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "MultiPlayerMatchResult",
"eventTime": "2020-11-20T09:51:29.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug==",
"matchId": "HD5Ojhp9b0qD4LBJw7vL1A==",
"stake": 19.47,
"rake": 0.47,
"totalRake": 1,
"revenue": -15
}
```

Example bonus money

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "MultiPlayerMatchResult",
"eventTime": "2020-11-20T09:51:29.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug==",
"matchId": "HD5Ojhp9b0qD4LBJw7vL1A==",
"stake": 0,
"rake": 0.47,
"totalRake": 1,
"revenue": 0,
"bonusStake": 15.3,
"bonusRevenue": -6
}
```

Example real and bonus money

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "MultiPlayerMatchResult",
"eventTime": "2020-11-20T09:51:29.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug==",
"matchId": "HD5Ojhp9b0qD4LBJw7vL1A==",
"stake": 4,
"rake": 0.47,
"totalRake": 1,
"revenue": -3,
"bonusStake": 15.3,
"bonusRevenue": -6
}
```

Notes

- matchId is a reference to the community player match submitted by the provider (see Start Community Player Match Player).
- eventTime defines the time when the player leaves the match and does not allow any conclusions to be drawn about when the match ends. An ongoing community player match is closed exclusively via the event End community player match. It is therefore also possible for a player to leave a match and later, by chance, participate again in the same match that is still in progress. Separate start and end events must be transmitted for each participation.
- For totalRake, the entire amount collected must be recorded, even if the provider only keeps a part or nothing of the collected fees.
- This event is to be deposited for both gratuitous and monetary matches.
- In the case of a free offer, stake, rake, totalRake and revenue must be set to 0.
- bonusStake and bonusRevenue are to be set if it is a community player match with bonus money or real and bonus money (see Start Community Player Match).

#### 7.4.5 End Community Player Game

The provider informs that, from his point of view, a community player game has ended and that it is no longer possible for players to participate.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "Multi-PlayerMatchClosure".

**eventTime**  
Data type: datetime  
Description: Time at which the provider declares the match closed  
Mandatory: yes  
Restriction: -

**matchId**  
Data type: identifier  
Description: Unique identifier of the currently running match  
Mandatory: yes  
Restriction: Reference to the ongoing community player match

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "MultiPlayerMatchClosure",
"eventTime": "2020-11-20T09:51:29.725Z",
"matchId": "HD5Ojhp9b0qD4LBJw7vL1A=="
}
```

Notes

- This event is only allowed after all players have left the ongoing community player game.

### 7.5 Payments

#### 7.5.1 Add payment method

The player registers a payment method pursuant to Section 6b (4) GlüStV 2021, via which deposits and/or withdrawals can be made. A payment method is based on a payment service, which is defined in the Payment Services Annex, LUGAS.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "PaymentModalityRegistration".

**eventTime**  
Data type: datetime  
Description: Time at which the player enters his payment method  
Mandatory: yes  
Restriction: -

**paymentModalityId**  
Data type: identifier  
Description: Unique ID of the player's payment method with the provider  
Mandatory: yes  
Restriction: -

**playerId**  
Data type: identifier  
Description: Identification of the player with the provider  
Mandatory: yes  
Restriction: Reference to an existing player

**methodName**  
Data type: string  
Description: Name of the payment method used  
Mandatory: yes  
Restriction: The values follow the Payment Services Annex, as well as the LUGAS Translations Annex.

**idData**  
Data type: string  
Description: Number of the same Payment methods per Players  
Mandatory: yes  
Restriction: Contains for each Payment method per Player a Letters. Alphabetical ascending by Number of the individual payment method. The Values follow the attachment Transliteration regulation LUGAS

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "PaymentModalityRegistration",
"eventTime": "2020-11-20T09:42:29.725Z",
"paymentModalityId": "MyweoQRQe0KPxR9enkjWbA==",
"playerId": "5emh/t5chEyN8S68yG1Rug==",
"methodName" : "KLARNA",
"idData" : "A
}
{
"eventId": "4c234ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "PaymentModalityRegistration",
"eventTime": "2020-11-21T17:33:30.725Z",
"paymentModalityId" : "ByxciQrtndaZTkaOPR8nsa==",
"playerId": "5emh/t5chEyN8S68yG1Rug==",
"methodName" : "KLARNA",
"idData" : "B
}
```

Notes

- The Payment Services Annex is regularly updated by the Authority through the reported data of the providers in the context of the licensing process.
- The mandatory information in the idData field is analogously based on the number of payment services selected per player and provider.
- The addition of a payment method has the consequence that the player's data according to § 6a para. 6 S. 1 GlüStV 2021 must be re-verified. The status of the player changes to "VerificationPending with intent "ChangedPayment". Until the verification is complete, the player may not participate in games according to § 6a para. 6 p. 2 and 3 GlüStV 2021 and no deposits and withdrawals are permitted with this payment service. This status must also be set if the status is already set to "VerificationPending".
- Payment methods which have not yet been described by the Payment Services Annex, LUGAS at the time of registration must be subsequently reported by the provider as soon as this is possible.

#### 7.5.2 Remove payment method

The player removes a payment method through which deposits and/or withdrawals can be made.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "PaymentModality-Cancelation".

**eventTime**  
Data type: datetime  
Description: Time at which the provider declares the payment method as no longer usable.  
Mandatory: yes  
Restriction: -

**playerId**  
Data type: identifier  
Description: Identification of the player with the provider  
Mandatory: yes  
Restriction: Reference to an existing player

**paymentModalityId**  
Data type: identifier  
Description: Clear payment method of the provider  
Mandatory: yes  
Restriction: Reference to a previously created payment method

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "PaymentModalityCancelation",
"eventTime": "2020-11-20T09:42:29.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug==",
"paymentModalityId": "MyweoQRQe0KPxR9enkjWbA=="
}
```

Notes

- paymentModalityId refers to an already registered payment method, see Add payment method.
- Each change to an existing payment method is interpreted by the evaluation system as a new payment method and therefore requires its own paymentModalityId, which is to be sent with a new Add Payment Method event and the existing payment method is to be deleted via this event.
- A deposit or withdrawal with this payment method is no longer permitted after removal. It should be noted that a payment method to be deleted may have to be kept longer due to Section 6a (6) sentence 3 GlüStV 2021.

#### 7.5.3 Deposit

The player wants to deposit money.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "Deposit".

**eventTime**  
Data type: datetime  
Description: Time at which the player requests the deposit  
Mandatory: yes  
Restriction: -

**playerId**  
Data type: identifier  
Description: Identification of the player with the provider  
Mandatory: yes  
Restriction: Reference to an existing player

**paymentModalityId**  
Data type: identifier  
Description: Unique identifier of the payment method  
Mandatory: yes  
Restriction: Reference to an existing payment method

**amount**  
Data type: money  
Description: The amount the player wants to deposit.  
Mandatory: yes  
Restriction: The amount must be positive.

**depositId**  
Data type: identifier  
Description: Unique identifier of the deposit  
Mandatory: yes  
Restriction: -

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "Deposit",
"eventTime": "2020-11-20T09:42:29.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug==",
"paymentModalityId": "MyweoQRQe0KPxR9enkjWbA==",
"amount": 199.47,
"depositId": "84508dba-355d-4c0c-b53f-bdd0a5cd7ba0"
}
```

Notes

- Deposits may only be made via a pre-registered payment method, which is via paymentModalityId is referenced (see Adding a Payment Method).
- Pursuant to Section 6c (6) sentence 1 GlüStV 2021, each deposit must be reconciled with the central files (see Deposit). Between the deposit and the comparison with the central files, no further deposit events may occur for the player. Payments that were rejected by the central files must also be recorded as events.
- Each accepted deposit must have a gaming account transaction associated with it (see Gaming Account Transaction).
- Deposits which are rejected by the central files through the event Message of deposit to the central files (depositResult = Failed) are cancelled.
- The depositId is to be entered in the transaction account as transactionReferenceId and in the depositId field when reporting the deposit to the central files.

#### 7.5.4 Payment

The player wants money paid out.

Fields

**eventId** identifier Unique Id of the event  
**eventName** identifier Unique identifier of the event  
**eventTime** datetime Time at which the payout was requested.  
**playerId** identifier Identification of the player with the provider  
**paymentModalityId** identifier Unique identifier of the payment method  
yes -  
yes Must contain the value "Payout".  
yes -  
yes Reference to an existing player  
yes Reference to an existing payment channel

**amount** money The amount paid out  
yes The amount must be positive be.

**automatic** bool Indicates whether the payout was initiated due to an amount limit above which winnings are automatically paid out to the player.

**payoutId** identifier Unique identifier of the payout  
yes -  
yes -

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "Payout",
"eventTime": "2020-11-20T09:42:29.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug==",
"paymentModalityId": "MyweoQRQe0KPxR9enkjWbA==",
"amount": 199.47,
"automatic": false,
"payoutId": "961cd39b-1f51-4b3c-812a-63fd66f2ab6f"
}
```

Notes

- Withdrawals may only be made via a previously registered payment method (see Add payment method).
- Each payout must have a gaming account transaction associated with it (see Gaming Account Transaction).
- The payoutId is to be entered as transactionReferenceId in the game account transaction.

#### 7.5.5 Transaction game account

The player's account balance has been changed by a transaction.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "Transaction".

**eventTime**  
Data type: datetime  
Description: Time of effectiveness of the change in the account balance  
Mandatory: yes  
Restriction: -

**playerId**  
Data type: identifier  
Description: Identification of the player with the provider  
Mandatory: yes  
Restriction: Reference to an existing player

**transactionType**  
Data type: identifier  
Description: Unique type of transaction  
Mandatory: yes  
Restriction: See table below for valid values

**transactionReferenceId**  
Data type: identifier  
Description: Transaction reference  
Mandatory: conditional mandatory field  
Restriction: See table below for valid reference

**amount**  
Data type: money  
Description: The amount of change in the player's account balance  
Mandatory: yes  
Restriction: -

**note**  
Data type: string  
Description: Reason for the transaction  
Mandatory: no  
Restriction: The length is limited to 80 characters. Only to be specified for OtherDeposit and OtherPayout.

The following types are possible as the source of the transaction:

**Deposit** A deposit has been made  
Content of the field (transactionReferenceId): ID of deposit (depositId)

**Payout** A payout was made  
Content of the field (transactionReferenceId): ID of payout (payoutId)

**Bonus** Money has been transferred from a bonus money account to the gaming account  
Content of the field (transactionReferenceId): None

**Chargeback** A deposit has been revoked  
Content of the field (transactionReferenceId): Deposit ID (depositId)

**DepositFailed** A deposit was cancelled or has not taken place  
Content of the field (transactionReferenceId): ID of deposit (depositId)

**PayoutFailed** A payout was cancelled  
Content of the field (transactionReferenceId): ID of payout (payoutId)

**GoodwillCredit** A goodwill credit was issued made  
Content of the field (transactionReferenceId): No transactionReferenceId

**ProfitTransfer** A transfer of profit into or out of safe-server relevant areas.  
Content of the field (transactionReferenceId): No transactionReferenceId

**Tax** Tax incurred on a match  
Content of the field (transactionReferenceId): ID of the single player or community player match (matchId)

**OtherDeposit** Other increase of the game account (no matching transaction type)  
Content of the field (transactionReferenceId): No transactionReferenceId

**OtherPayout** Other reduction of the game account (no matching transaction type)  
Content of the field (transactionReferenceId): No transactionReferenceId

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "Transaction",
"eventTime": "2020-11-20T09:42:29.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug==",
"transactionType": "Payout",
"transactionReferenceId": "961cd39b-1f51-4b3c-812a-63fd66f2ab6f",
"amount": -5.78
}
```

Notes

- The change in the account balance in the amount field may be positive or negative.
- For a transaction of transactionType "Deposit", "Bonus", "PayoutFailed", "GoodwillCredit" or "OtherDeposit", the account balance may only increase.
- For a transaction of transactionType "Payout", "Chargeback" or "OtherPayout", the account balance may only decrease.
- For a transaction of transactionType "Chargeback", the account balance must be reduced by the amount of the original deposit.
- For a transaction of transactionType "DepositFailed", the account balance must not change. For the change of the player's account balance, the amount shall be 0. A transaction of transactionType "DepositFailed" is to be used if a deposit is aborted after successful reporting to the central files (reporting of the deposit to the central files), so that no further cash flow is to be expected.
- For a transaction of transactionType "PayoutFailed", the account balance must be increased by the amount of the original payout.
- For a transaction of transactionType "Tax", the account balance may decrease (report taxes due) and increase (reduce or cancel taxes reported). In each case, the Id of the single player or community player match must be entered in the transactionReferenceId field.
- With a transaction of transactionType "ProfitTransfer", the account balance may increase (profit transfer from non-relevant areas) or decrease (profit transfer to non-relevant areas). Only transfers to or from other areas within the meaning of Section 4 (5) No. 5 GlüStV 2021 are possible via this function, which do not have to be made available on the safe server for the evaluation system of LUGAS.
- The account balance kept here refers exclusively to monetary amounts. If applicable, ex- isting bonus money accounts for free entertainment offers do not require account management in the sense of the evaluation system and, in contrast to monetary matches, do not result in events of this type.

### 7.6 Interaction between player and provider

The provider is obliged to interact with players at regular intervals and to record their behaviour.

#### 7.6.1 Log-in

The player logs in to the provider.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "PlayerLogin".

**eventTime**  
Data type: datetime  
Description: Time at which the player logged in to the provider  
Mandatory: yes  
Restriction: -

**playerId**  
Data type: identifier  
Description: Identification of the player with the provider  
Mandatory: yes  
Restriction: Reference to an existing player

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "PlayerLogin",
"eventTime": "2020-11-20T09:42:29.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug=="
}
```

#### 7.6.2 Player Declaration Virtual Slot Game

The player makes a declaration pursuant to Section 22a (4) GlüStV 2021 that he/she wishes to play a virtual slot machine game.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "SinglePlayerMatchDeclaration".

**eventTime**  
Data type: datetime  
Description: Time of the declaration of the player  
Mandatory: yes  
Restriction: -

**playerId**  
Data type: identifier  
Description: Identification of the player with the provider  
Mandatory: yes  
Restriction: Reference to an existing player

**gameId**  
Data type: identifier  
Description: Unique identifier of the game with the provider  
Mandatory: yes  
Restriction: Reference to an existing game

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "SinglePlayerMatchDeclaration",
"eventTime": "2020-11-20T09:43:02.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug==",
"gameId": "123456"
}
```

Notes

- A match pursuant to Section 22a (6) GlüStV 2021 consists of a single round of play in a virtual slot machine game, e.g. the single operation of a slot machine. Each new operation of the machine is a new match and requires a new player declaration.

#### 7.6.3 Player timeout

Message that a player has been inactive for 30 minutes.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "PlayerTimeout".

**eventTime**  
Data type: datetime  
Description: Time when the timeout was detected  
Mandatory: yes  
Restriction: -

**playerId**  
Data type: identifier  
Description: Unique Unique identifier of the player with the provider  
Mandatory: yes  
Restriction: Reference to an existing player

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "PlayerTimeout",
"eventTime": "2020-11-20T09:42:29.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug=="
}
```

Notes

- A timeout has the consequence that the player is to be set to inactive in the activity file pursuant to Section 6h (4) sentence 5 GlüStV 2021 if he is active for the provider.

#### 7.6.4 Reality check

Pursuant to Section 6h (7) GlüStV 2021, a player must be notified of the elapsed time at least after every hour of activity (according to the Zen- tral files).

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "RealityCheckProvider".

**eventTime**  
Data type: datetime  
Description: The moment when the provider first displayed or would have displayed the message to the player  
Mandatory: yes  
Restriction: -

**playerId**  
Data type: identifier  
Description: Identification of the player with the provider  
Mandatory: yes  
Restriction: Reference to an existing player

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "RealityCheckProvider",
"eventTime": "2020-11-20T09:42:40.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug=="
}
```

Notes

- The event only has to be created once, even if the provider had to display the notice to the player several times (e.g. by the player reloading the website).

#### 7.6.5 Reality check confirmation

A player confirms the provider's tip.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "RealityCheckPlayer".

**eventTime**  
Data type: datetime  
Description: The moment when the player has confirmed the message or the activity (according to the Central files) was terminated  
Mandatory: yes  
Restriction: -

**playerId**  
Data type: identifier  
Description: Identification of the player with the provider  
Mandatory: yes  
Restriction: Reference to an existing player

**hasActivityExpired**  
Data type: bool  
Description: Indicates whether the end of the event has occurred by expiration of the activity.  
Mandatory: yes  
Restriction: -

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "RealityCheckPlayer",
"eventTime": "2020-11-20T09:42:40.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug==",
"hasActivityExpired": false
}
```

Notes

- This event refers to a reminder from the provider about the previous season (see reality check).
- Between the notice of the provider and the confirmation, the player may not continue playing.
- In the case of virtual slot machines, it must be taken into account that a waiting period of five minutes must be observed after confirmation.
- If the player does not confirm the provider's notice, e.g. by permanently leaving the site or other inactivity, the player timeout takes effect. In this case, the provider must set the player to inactive in the activity file pursuant to Section 6h (4) sentence 5 GlüStV 2021. This means that this event is triggered. hasActivityExpired must be set to "true" accordingly.

#### 7.6.6 Reminder range change

If a player changes the gaming area of the provider, he/she must confirm the information on the dangers and prevention of gambling addiction as well as counselling offers in accordance with Section 4 (5) no. 5 sentence 4 GlüStV 2021. By entering this event, the provider reports that the player has confirmed the information.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "PlayerChangedArea".

**eventTime**  
Data type: datetime  
Description: Time at which the player confirmed the clues.  
Mandatory: yes  
Restriction: -

**playerId**  
Data type: identifier  
Description: Identification of the player with the provider  
Mandatory: yes  
Restriction: Reference to an existing player

**oldAreaId**  
Data type: identifier  
Description: Area the player is leaving  
Mandatory: yes  
Restriction: Reference to an existing area

**newAreaId**  
Data type: identifier  
Description: Area the player enters  
Mandatory: yes  
Restriction: Reference to an existing area

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "PlayerChangedArea",
"eventTime": "2020-11-20T09:43:01.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug==",
"oldAreaId": "15",
"newAreaId": "7"
}
```

Notes

- oldAreaId and newAreaId are references to the provider's established areas (see Add Area) and must be different from each other.

#### 7.6.7 Correction request Limit setting

Depicts that a correction request is displayed to the player pursuant to Section 6c (1) sentence 9 GlüStV 2021 if he has attempted to set a limit that is too high across all providers.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "PlayerLimitCorrection-Request".

**eventTime**  
Data type: datetime  
Description: Time at which the request was sent  
Mandatory: yes  
Restriction: -

**playerId**  
Data type: identifier  
Description: Identification of the player with the provider  
Mandatory: yes  
Restriction: Reference to an existing player

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "PlayerLimitCorrectionRequest",
"eventTime": "2020-11-20T09:43:01.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug=="
}
```

#### 7.6.8 Information statistical data

Shows that a provider has displayed all cumulative stakes, winnings and losses of the previous 30 days to a player in accordance with Section 6d (2) GlüStV 2021.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "PlayerStatistics".

**eventTime**  
Data type: datetime  
Description: Time at which the provider displayed the message to the player.  
Mandatory: yes  
Restriction: -

**playerId**  
Data type: identifier  
Description: Identification of the player with the provider  
Mandatory: yes  
Restriction: Reference to an existing player

**stake**  
Data type: money  
Description: The sum of all bets in the last 30 days  
Mandatory: yes  
Restriction: Must not be negative.

**profit**  
Data type: money  
Description: The sum of all winnings in the last 30 days  
Mandatory: yes  
Restriction: Must not be negative.

**loss**  
Data type: money  
Description: The sum of all losses in the last 30 days  
Mandatory: yes  
Restriction: Must not be negative.

**balance**  
Data type: money  
Description: The current Account balance of the Player  
Mandatory: yes  
Restriction: -

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "PlayerStatistics",
"eventTime": "2020-11-20T09:43:01.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug==",
"stake": 99.47,
"profit": 12.47,
"loss": 86.47,
"balance": 75.79
}
```

Notes

- The player's current account balance in the balance field is an auxiliary information and not a mandatory information within the meaning of Section 6d (2) GlüStV 2021.

#### 7.6.9 Inducement inactivation

A player requests the provider under Section 6h (4) sentence 2 GlüStV 2021 to make him inactive on the activity file.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "PlayerLogout".

**eventTime**  
Data type: datetime  
Description: Time of the player's call  
Mandatory: yes  
Restriction: -

**playerId**  
Data type: identifier  
Description: Identification of the player with the provider  
Mandatory: yes  
Restriction: Reference to an existing player

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "PlayerLogout",
"eventTime": "2020-11-20T09:43:01.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug=="
}
```

### 7.7 Use of the central files

The provider shall log the use of the central files.

#### 7.7.1 Transmission of player data

Represents the attempt to create a player in the central files (cf. § 6c par. 5 p. 4 to 6 GlüStV 2021). The central files regulate in their specification how the response is to be interpreted.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "ApiRequestRegisterPlayer".

**eventTime**  
Data type: datetime  
Description: Time at which the request was sent to the central files  
Mandatory: yes  
Restriction: -

**playerId**  
Data type: identifier  
Description: Identification of the player with the provider  
Mandatory: yes  
Restriction: Reference to an existing player

**depositLimit**  
Data type: money  
Description: The player's cross-provider deposit limit set during registration.  
Mandatory: no  
Restriction: Must be positive.

**registrationResult**  
Data type: identifier  
Description: The result of the enquiry  
Mandatory: yes  
Restriction: See table below for valid values

The following results of the API call are possible:

**Successful** The player was successfully created.

**Failed** The player could not be created successfully.

**Unspecified** The response of the central files does not clearly fit into one of the specified results.

**NotAvailable** The request could not be sent to the API. The Network connection is not available or the web service reports a 5xx status code.

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "ApiRequestRegisterPlayer",
"eventTime": "2020-11-20T09:43:01.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug==",
"depositLimit": 200,
"registrationResult": "Successful"
}
```

Notes

- When setting the deposit limit, it should be noted that according to Section 6c (3) sentence 2 GlüStV 2021, this may only become valid later if there is already an existing cross-provider deposit limit that is smaller than the limit set here. For the concrete mechanics of the effectiveness of cross-provider deposit limits, the specification of the central files must be consulted.
- The deposit limit is not transferred if the player retains an existing cross-provider deposit limit pursuant to Section 6c (5) sentence 4 GlüStV 2021.

#### 7.7.2 Cross-provider deposit limit

Represents the attempt to set a new cross-provider limit in the central files for a player already registered in the central files in accordance with section 6c (3) sentence 1 GlüStV 2021. The central files regulate in their specification how the answer is to be interpreted.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "ApiRequestSetDepositLimit".

**eventTime**  
Data type: datetime  
Description: Time at which the request was sent to the central files  
Mandatory: yes  
Restriction: -

**playerId**  
Data type: identifier  
Description: Identification of the player with the provider  
Mandatory: yes  
Restriction: Reference to an existing player

**depositLimit**  
Data type: money  
Description: The player's new cross-provider deposit limit  
Mandatory: yes  
Restriction: Must be positive.

**depositLimitResult**  
Data type: identifier  
Description: The result of the enquiry  
Mandatory: yes  
Restriction: See table below for valid values

The following results of the API call are possible:

**Successful** The limit was set successfully.

**Failed** The limit could not be set.

**Unspecified** The response of the central files does not fit unambiguously into one of the specified results.

**NotAvailable** The request could not be sent to the API. The Network connection is not available or the web service reports a 5xx status code.

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "ApiRequestSetDepositLimit",
"eventTime": "2020-11-20T09:43:01.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug==",
"depositLimit": 200,
"depositLimitResult": "Successful"
}
```

Notes

- It should be noted that the limit set in accordance with Section 6c (3) sentence 2 GlüStV 2021 may only become valid later if there is already an existing cross-provider deposit limit that is smaller than the limit set here. For the concrete mechanics of the effectiveness of cross-provider deposit limits, the specification of the central files must be consulted.

#### 7.7.3 Deposit

Represents the attempt to make a deposit in accordance with Section 6c (6) sentence 1 GlüStV 2021 in the central files. The central files regulate in their specification how the response is to be interpreted.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "ApiRequestMakeDeposit".

**eventTime**  
Data type: datetime  
Description: Time at which the request was sent to the central files  
Mandatory: yes  
Restriction: -

**playerId**  
Data type: identifier  
Description: Identification of the player with the provider  
Mandatory: yes  
Restriction: Reference to an existing player

**amount**  
Data type: money  
Description: The amount of the deposit  
Mandatory: yes  
Restriction: Must be positive.

**depositResult**  
Data type: identifier  
Description: The result of the enquiry  
Mandatory: yes  
Restriction: See table below for valid values

**depositId**  
Data type: identifier  
Description: Unique identifier of the deposit  
Mandatory: yes  
Restriction: Reference to depositId of the deposit event

The following results of the API call are possible:

**Successful** The deposit was made successfully.

**Failed** The deposit was not made successfully.

**Unspecified** The response of the central files does not fit unambiguously into one of the specified results.

**NotAvailable** The request could not be sent to the API. The Network connection is not available or the web service reports a 5xx status code.

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "ApiRequestMakeDeposit",
"eventTime": "2020-11-20T09:43:01.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug==",
"amount": 199.47,
"depositResult": "Successful",
"depositId": "84508dba-355d-4c0c-b53f-bdd0a5cd7ba0"
}
```

Notes

- Deposits that are rejected by the central files may not be credited to the player account. In this case, no transaction event is filed.
- Pursuant to Section 6c (6) sentence 1 GlüStV 2021, each deposit must be reconciled with the central files (see Deposit). Between the deposit and the comparison with the central files, no further deposit events may occur for the player. Payments that were rejected by the central files must also be recorded as events.
- Each accepted deposit must be associated with a player account transaction (see Player Account Transaction). No other events may occur between the accepted deposit and the transaction to the player.

#### 7.7.4 Active status

Depicts the attempt to set a player to active or inactive in the central files according to § 6h para. 3 GlüStV 2021. The central files regulate in their specification how the answer is to be interpreted.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "ApiRequestSetActiveState".

**eventTime**  
Data type: datetime  
Description: Time at which the request was sent to the central files  
Mandatory: yes  
Restriction: -

**playerId**  
Data type: identifier  
Description: Identification of the player with the provider  
Mandatory: yes  
Restriction: Reference to an existing player

**active**  
Data type: bool  
Description: Indicates the provider's wish whether the player should be listed in the file as active (true) or inactive (false)  
Mandatory: yes  
Restriction: -

**activeStateResult**  
Data type: identifier  
Description: The result of the enquiry  
Mandatory: yes  
Restriction: See table below for valid values

The following results of the API call are possible:

**Successful** The activity status was successfully changed.

**Failed** The activity status was not successfully changed.

**Unspecified** The response of the central files does not clearly fit into one of the specified results.

**NotAvailable** The request could not be sent to the API. The Network connection is not available or the web service reports a 5xx status code.

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "ApiRequestSetActiveState",
"eventTime": "2020-11-20T09:43:01.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug==",
"active": true,
"activeStateResult": "Successful
}
```

#### 7.7.5 Lock check

Depicts a request to the barring file pursuant to Section 8 (3) sentence 4 GlüStV 2021, which checks whether the player is barred. The blocking file regulates in its specification how the answer is to be interpreted.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "ApiRequestGetSuspendedState".

**eventTime**  
Data type: datetime  
Description: Time at which the request was sent to the lock file  
Mandatory: yes  
Restriction: -

**playerId**  
Data type: identifier  
Description: Identification of the player with the provider  
Mandatory: yes  
Restriction: Reference to an existing player

**suspensionResult**  
Data type: identifier  
Description: The result of the enquiry  
Mandatory: yes  
Restriction: See table below for valid values

The following results of the API call are possible:

**Permitted** The player is permitted to participate in games of chance.

**Suspended** The player is not allowed to participate in games of chance due to a suspension.

**Unspecified** The lock file response does not fit uniquely into one of the specified outcomes.

**NotAvailable** The request could not be sent to the API. The Network connection is not available or the web service reports a 5xx status code.

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "ApiRequestGetSuspendedState",
"eventTime": "2020-11-20T09:43:01.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug==",
"suspensionResult": "Suspended"
}
```

### 7.8 Provider data

#### 7.8.1 Add area

The provider shall provide information on a gaming area pursuant to Section 4 (5) No. 5 GlüStV 2021 that it has established.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "ProviderAreaRegistration".

**eventTime**  
Data type: datetime  
Description: Time when the provider created the area  
Mandatory: yes  
Restriction: -

**areaId**  
Data type: identifier  
Description: Unique identification of the area  
Mandatory: yes  
Restriction: -

**name**  
Data type: smallString  
Description: Area name  
Mandatory: yes  
Restriction: -

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "ProviderAreaRegistration",
"eventTime": "2020-11-20T09:42:29.725Z",
"areaId": "213",
"\"name\"": "\"Slot Machine Paradise\""
}
```

Notes

- During the initial set-up of the safe server, all existing play areas must be communicated.

#### 7.8.2 Add single player game

A provider informs about a new single player game he has added.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "SinglePlayerGameRegistration".

**eventTime**  
Data type: datetime  
Description: Time when the provider created the match  
Mandatory: yes  
Restriction: -

**gameId**  
Data type: identifier  
Description: Unique identifier of the game  
Mandatory: yes  
Restriction: -

**name**  
Data type: smallString  
Description: Name of the game  
Mandatory: yes  
Restriction: -

**singlePlayerGameCategory**  
Data type: identifier  
Description: Category of the game  
Mandatory: yes  
Restriction: See table below for valid values

The following categories are possible:

- SlotGame
- Scratchcard
- Video poker
- Other

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "SinglePlayerGameRegistration",
"eventTime": "2020-11-20T09:42:29.725Z",
"gameId": "123456",
"\"name": "Red Mamba",
"\"singlePlayerGameCategory": "SlotGame"
}
```

Notes

- During the initial set-up of the safe server, all existing active games must be communicated.

#### 7.8.3 Approval single player game

A provider informs about the official permission to offer a single player game.

Pursuant to Section 22a (6) GlüStV 2021, the average playing time of a single-player game must be at least 5 seconds. The authority may specify further details on the calculation of the average in the permit.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "SinglePlayerGamePermission".

**eventTime**  
Data type: datetime  
Description: Time of activation of the permit if permittedFrom is not transmitted.  
Mandatory: yes  
Restriction: -

**gameId**  
Data type: identifier  
Description: Unique identifier of the game  
Mandatory: yes  
Restriction: Reference to an existing single player game

**permittedFrom**  
Data type: datetime  
Description: Time from which the permit is active  
Mandatory: no  
Restriction: Must not be less than eventTime if specified.

**permittedTo**  
Data type: datetime  
Description: Time at which the permit becomes inactive  
Mandatory: no  
Restriction: -

**permittedStake**  
Data type: money  
Description: Indicates the maximum bet level that the authority has approved for a game of this type  
Mandatory: yes  
Restriction: Must be positive.

**calculationRule**  
Data type: identifier  
Description: Calculation rule of the average playing time  
Mandatory: no  
Restriction: See table below for valid values.

**areaId**  
Data type: identifier  
Description: Area of the provider in which this game is offered  
Mandatory: yes  
Restriction: Reference to an existing area of the provider

The following calculation rules are possible:

- Arithmetical
- Median

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "SinglePlayerGamePermission",
"eventTime": "2020-11-20T09:42:29.725Z",
"gameId": "123456",
"permittedTo": "2021-11-20T09:42:29.725Z",
"allowedStake": 2,
"calculationRule": "Arithmetical",
"areaId": "14"
}
```

Notes

- gameId is a reference to a registered single player game of the provider (see Add single player game).
- areaId is a reference to the established area of the provider (see Add area).
- PermittedTo is not required to be submitted for open-ended permits.
- If permittedFrom is not transmitted, the permit is interpreted as immediately active.
- As soon as eventTime of any event (possibly also of the approval event itself) falls on or after permittedFrom, the approval is interpreted as active.
- A permit interpreted as active is interpreted as terminated earlier or immediately by the transmission of a further permit, if applicable.
- A permit that has not yet been interpreted as active becomes invalid by the transmission of another permit.
- A permit is only effective for its active period.
- Before starting a game, it is necessary that a permit has been created for that game.

#### 7.8.4 Add a Community Player Game

A provider informs about a new community player game he has added.

Fields

**eventId** identifier Unique Id of the event  
**eventName** identifier Unique identifier of the event  
**eventTime** datetime Time when the provider created the match  
**gameId** identifier Unique identifier of the game  
yes -  
yes Must contain the value "MultiPlayerGameRegistration".  
yes -  
yes -

**name** smallString Name of the game  
yes -

**variant** smallString The variant of the game  
no -

**multiPlayerGameCategory** identifier Category of the game  
yes See table below for valid values

The following categories are possible:

- Poker
- Other

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "MultiPlayerGameRegistration",
"eventTime": "2020-11-20T09:42:29.725Z",
"gameId": "789",
"name": "Poker",
"variant": "Texas hold 'em",
"multiPlayerGameCategory": "Poker
}
```

Notes

- During the initial set-up of the safe server, all existing active games must be transmitted.
- variant is mandatory for games of the multiPlayerGameCategory "Poker".

#### 7.8.5 Approval Community Player Game

A provider informs about the official permission to offer a community player game.

Fields

**eventId** identifier Unique Id of the event  
**eventName** identifier Unique identifier of the event  
**eventTime** datetime Time of activation of the permit if permittedFrom is not transmitted.  
**gameId** identifier Unique identifier of the game  
yes -  
yes Must contain the value "MultiPlayerGamePermission".  
yes -  
yes Reference to an existing community player game

**permittedFrom**  
Data type: datetime  
Description: Time from which the permit is active  
Mandatory: no  
Restriction: Must not be less than eventTime if specified.

**permittedTo**  
Data type: datetime  
Description: Time at which the permit becomes inactive  
Mandatory: no  
Restriction: -

**permittedConcurrentMatches**  
Data type: int  
Description: Maximum number of simultaneous matches  
Mandatory: no  
Restriction: Must be at least 1

**isConcurrencyRestrictedToVariant**  
Data type: bool  
Description: Indicates whether the restriction on simultaneous play is exclusive to this variant of the game.  
Mandatory: no  
Restriction: -

**limitMinStake**  
Data type: money  
Description: Maximum limits for the minimum stakes per game round (e.g. Blinds in poker)  
Mandatory: no  
Restriction: Must be positive.

**limitTotalAmount**  
Data type: money  
Description: Maximum amount a player may have at his disposal  
Mandatory: no  
Restriction: Must be positive.

**limitTournamentBuyIn**  
Data type: money  
Description: Maximum amount for participation in a tournament  
Mandatory: no  
Restriction: Must be positive.

**areaId**  
Data type: identifier  
Description: Area of the provider in which this game is offered  
Mandatory: yes  
Restriction: Reference to an existing area of the provider

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "MultiPlayerGamePermission",
"eventTime": "2020-11-20T09:42:29.725Z",
"gameId": "789",
"permittedTo": "2020-11-21T09:42:29.725Z",
"permittedConcurrentMatches": 4,
"isConcurrencyRestrictedToVariant": true,
"limitMinStake": 48.47,
"limitTotalAmount": 2000,
"limitTournamentBuyIn": 19.47,
"areaId": "5
}
```

Notes

- gameId is a reference to a registered community player game of the provider (see Add community player game).
- areaId is a reference to the established area of the provider (see Add area).
- PermittedTo is not required to be submitted for open-ended permits.
- If permittedFrom is not transmitted, the permit is interpreted as immediately active.
- As soon as eventTime of any event (possibly also of the approval event itself) falls on or after permittedFrom, the approval is interpreted as active.
- A permit interpreted as active is interpreted as terminated earlier or immediately by the transmission of a further permit, if applicable.
- A permit that has not yet been interpreted as active becomes invalid by the transmission of another permit.
- A permit is only effective for its active period.
- permittedConcurrentMatches, isConcurrencyRestrictedToVariant, limitMinStake, limitTotalAmount and limitTournamentBuyIn are mandatory for poker games.
- Before starting a game, it is necessary that a permit has been created for that game.

#### 7.8.6 Authorisation to set a deviating limit

One provider informs about the authorisation to increase the limit according to § 6c par. 1 p. 3-5 GlüStV 2021.

Fields

**eventId** identifier Unique Id of the event  
**eventName** identifier Unique identifier of the event  
**eventTime** datetime Time of activation of the permit if permittedFrom is not transmitted.  
**permittedFrom** datetime Time from which the Approval is active  
**permittedTo** datetime Time at which the permit becomes inactive  
**limitAmount** money Maximum limit amount that the provider is allowed to allow to its players  
yes -  
yes Must contain the value "SpecialLimitRegistration".  
yes -  
no -  
no -  
yes Must be greater than 1000.00 Be €

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "SpecialLimitRegistration",
"eventTime": "2020-11-20T09:42:29.725Z",
"permittedTo": "2021-11-20T09:42:29.725Z",
"limitAmount": 1999.47
}
```

Notes

- PermittedTo is not required to be submitted for open-ended permits.
- If permittedFrom is not transmitted, the permit is immediately interpreted as active.
- As soon as eventTime of any event (possibly also of the permit event itself) falls on or after permittedFrom, the permit is considered active.
- A permit interpreted as active is interpreted as terminated earlier or immediately by the transmission of a further permit, if applicable.
- A permit that has not yet been interpreted as active becomes invalid by the transmission of another permit.
- A permit is only effective for its active period.

#### 7.8.7 Add payment service

A provider shall provide an officially approved payment service in accordance with the Payment Services Annex, LUGAS, with which all players can make deposits and/or withdrawals at the provider.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "PaymentServiceRegistration".

**eventTime**  
Data type: datetime  
Description: Time when the provider added the payment service  
Mandatory: yes  
Restriction: -

**paymentServiceNumber**  
Data type: identifier  
Description: The payment service number using the Payment Services Annex, LUGAS  
Mandatory: yes  
Restriction: -

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "PaymentServiceRegistration",
"eventTime": "2020-11-20T09:42:29.725Z",
"paymentServiceNumber": "2
}
```

Notes

- The Payment Services Annex, LUGAS is regularly updated by the authority through the reported data of the providers in the context of the granting of permission. Payment services that are not yet described in this annex at the time of registration must be reported by the provider as soon as this is possible.

#### 7.8.8 Remove payment service

A provider deletes a deposited payment service.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "PaymentServiceCancelation".

**eventTime**  
Data type: datetime  
Description: Time when the provider deleted the payment service  
Mandatory: yes  
Restriction: -

**paymentServiceNumber**  
Data type: identifier  
Description: The payment service number using the Payment Services Annex, LUGAS  
Mandatory: yes  
Restriction: -

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "PaymentServiceCancelation",
"eventTime": "2020-11-20T09:42:29.725Z",
"paymentServiceNumber": "2
}
```

Notes

- When this event is transmitted, no payment path to a player based on the payment service to be deleted may exist any longer.

### 7.9 Correction events

For the correction of events, it is possible to add, change or delete events subsequently. When changing and deleting events, the change event and delete event must be filed. To add events subsequently, only the event itself must be stored. Correction events themselves cannot be changed or deleted.

#### 7.9.1 Change event

Data of an event are subsequently changed.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the correction event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "RetroUpdate".

**eventTime**  
Data type: datetime  
Description: Time when the correction event was filed  
Mandatory: yes  
Restriction: -

**chunkId**  
Data type: identifier  
Description: Id of the chunk in which the event to be changed was transmitted  
Mandatory: yes  
Restriction: -

**event**  
Data type: event  
Description: The data of the event to be changed after the change  
Mandatory: yes  
Restriction: -

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "RetroUpdate",
"eventTime": "2020-11-20T09:42:29.725Z",
"chunkId": "3608e046-c713-4864-b559-867018fadb5c",
"event": {
"eventId": "f03f64d3-f5bd-438e-9498-bdee408d1ac1",
"eventName": "PlayerStatus",
"eventTime": "2020-11-20T09:42:29.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug==",
"status": "Verified
}
}
```

Notes

- The complete event to be changed, including unchanged fields, must be entered under event. The following fields may not be changed within event compared to the original event: eventId, eventName, eventTime and playerId if available.
- If an event with personal data is changed, the personal data must also be specified for the eventId of the event to be changed.
- If an event is changed more than once, the last change filed shall apply.
- After an event has been deleted, no more changes may be made to it. Instead, a new event with a new eventId can be filed.
- Correction events themselves cannot be changed or deleted.

#### 7.9.2 Delete Event

An event is deleted.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the correction event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "RetroDelete".

**eventTime**  
Data type: datetime  
Description: Time when the correction event was filed  
Mandatory: yes  
Restriction: -

**chunkId**  
Data type: identifier  
Description: Id of the chunk in which the event to be deleted was transmitted.  
Mandatory: yes  
Restriction: -

**event**  
Data type: event  
Description: The data of the event to be deleted  
Mandatory: yes  
Restriction: -

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "RetroDelete",
"eventTime": "2020-11-20T09:42:29.725Z",
"chunkId": "3608e046-c713-4864-b559-867018fadb5c",
"event": {
"eventId": "f03f64d3-f5bd-438e-9498-bdee408d1ac1",
"eventName": "PlayerStatus",
"eventTime": "2020-11-20T09:42:29.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug==",
"status": "Verified
}
}
```

Notes

- Under event, the complete original event to be deleted is to be entered unchanged.
- Previously changed events can be deleted by deleting the original event.
- To undo the deletion of an event, the desired event can be subsequently filed again with a new eventId.
- Correction events themselves cannot be changed or deleted.

### 7.10 Sports betting

#### 7.10.1 Create betting offer

A provider informs about a new sporting event on which bets may be placed.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "BetOffer

**eventTime**  
Data type: datetime  
Description: Time when the betting offer was created  
Mandatory: yes  
Restriction: -

**betOfferId**  
Data type: identifier  
Description: Unique identification of the betting offer  
Mandatory: yes  
Restriction: -

**sportEventId**  
Data type: identifier  
Description: Unique Id of the sporting event, which is announced by the authority.  
Mandatory: yes  
Restriction: -

**sportEvent**  
Data type: smallString  
Description: Free designation of the exact sporting event  
Mandatory: yes  
Restriction: -

**startTime**  
Data type: datetime  
Description: Start time of the exact sporting event  
Mandatory: yes  
Restriction: -

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "BetOffer",
"eventTime": "2020-11-20T09:42:29.725Z",
"betOfferId": "123",
"sportEventId": "bdef8e21-4870-49d0-a9d0-84b8e1d99bf8",
"sportEvent": "1.FC Magdeburg - Hamburger SV",
"startTime": "2020-12-20T13:00:00.000Z"
}
```

Notes

- The sportEventId corresponds to the Id of the sporting event published by the authority, which refers to a specific form of a competition. The sportEvent is the exact sporting event that is part of this competition.
- A betting offer must be created before bets can be placed on this sporting event.

#### 7.10.2 Change the start time of the betting offer

The start time of a sporting event on which bets may be placed changes.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "BetOfferUpdate

**eventTime**  
Data type: datetime  
Description: Time when the start time of the betting offer was changed  
Mandatory: yes  
Restriction: -

**betOfferId**  
Data type: identifier  
Description: Unique identification of the betting offer  
Mandatory: yes  
Restriction: Reference to an existing betting offer

**startTime**  
Data type: datetime  
Description: New start time of the exact sporting event  
Mandatory: yes  
Restriction: -

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "BetOfferUpdate",
"eventTime": "2020-11-20T09:42:29.725Z",
"betOfferId": "123",
"startTime": "2020-12-20T13:30:00.00Z"
}
```

#### 7.10.3 Place bet

Information about a bet placed by a player.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "BetPlacement

**eventTime**  
Data type: datetime  
Description: Time when the player placed the bet  
Mandatory: yes  
Restriction: -

**playerId**  
Data type: identifier  
Description: Identification of the player with the provider  
Mandatory: yes  
Restriction: Reference to an existing player

**betId**  
Data type: identifier  
Description: Unique identifier of the bet placed  
Mandatory: yes  
Restriction: -

**areaId**  
Data type: identifier  
Description: Area of the provider in which this bet is offered  
Mandatory: yes  
Restriction: Reference to an existing area of the provider

**stake**  
Data type: money  
Description: Total bet  
Mandatory: yes  
Restriction: -

**betKind**  
Data type: identifier  
Description: Clear method of betting  
Mandatory: yes  
Restriction: See table below for valid values

**bets**  
Data type: array[bet]  
Description: Details of the individual bets  
Mandatory: yes  
Restriction: -

The following information applies to a single bet:

**subBetId**  
Data type: identifier  
Description: Unique identifier of the individual partial bet  
Mandatory: yes  
Restriction: -

**betTypeId**  
Data type: identifier  
Description: Id of the type of bet (betting markets) announced by the authority  
Mandatory: yes  
Restriction: -

**betOfferId**  
Data type: identifier  
Description: Unique identification of the betting offer  
Mandatory: yes  
Restriction: Reference to an existing betting offer

**quote**  
Data type: decimal  
Description: Indication of the betting odds of a partial bet  
Mandatory: yes  
Restriction: Must be greater than 1

As a betKind, the following options are possible:

**Single** This is a single bet.

**Combination** This is a combination bet.

**Specific** This is a specific system.

Example of a single bet

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "BetPlacement",
"eventTime": "2020-11-20T09:42:29.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug==",
"betId": "555-666",
"areaId": "14",
"stake": 5.00,
"betKind": "Single",
"bets": [
{
"subBetId": "s111-222-333",
"betTypeId": "c72a5a59-74cc-4917-8e2a-6d75acf392b3",
"betOfferId": "123",
"quote": 1.50
}
]
}
```

Example of a combination bet or system bet

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "BetPlacement",
"eventTime": "2020-11-20T09:42:29.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug==",
"betId": "555-666",
"areaId": "14",
"stake": 5.00,
"betKind": "Combination",
"bets": [
{
"subBetId": "s111-222-333",
"betTypeId": "c72a5a59-74cc-4917-8e2a-6d75acf392b3",
"betOfferId": "123",
"quote": 1.50
},
{
},
"subBetId": "s444-555-666",
"betTypeId": "d34a5a59-74cc-4917-8e2a-6d75acf395c6",
"betOfferId": "123",
"quote": 4.50
}
]
}
```

Notes

- Before placing a bet, the corresponding betting offer must be made known.
- The player must report active status in the central files before placing a bet.
- If a single bet is placed, the bets field must contain exactly one entry. For combination bets or specific systems, at least two entries must be included.

#### 7.10.4 Changes to a placed bet

Modification of a bet placed by a player.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "BetPlacementUpdate

**eventTime**  
Data type: datetime  
Description: Time when the player changed the placed bet  
Mandatory: yes  
Restriction: -

**playerId**  
Data type: identifier  
Description: Identification of the player with the provider  
Mandatory: yes  
Restriction: Reference to an existing player

**betId**  
Data type: identifier  
Description: Unique identifier of the placed bet  
Mandatory: yes  
Restriction: Reference to existing bet of the player

**areaId**  
Data type: identifier  
Description: Area of the provider in which this bet is offered  
Mandatory: yes  
Restriction: Reference to an existing area of the provider

**stake**  
Data type: money  
Description: Total bet  
Mandatory: yes  
Restriction: -

**betKind**  
Data type: identifier  
Description: Clear method of betting  
Mandatory: yes  
Restriction: See table below for valid values

**bets**  
Data type: array[bet]  
Description: Details of the individual bets  
Mandatory: yes  
Restriction: -

The following information applies to a single bet:

**subBetId**  
Data type: identifier  
Description: Unique identifier of the individual partial bet  
Mandatory: yes  
Restriction: -

**betTypeId**  
Data type: identifier  
Description: Id of the type of bet (betting markets) announced by the authority  
Mandatory: yes  
Restriction: -

**betOfferId**  
Data type: identifier  
Description: Unique identification of the betting offer  
Mandatory: yes  
Restriction: Reference to an existing betting offer

**quote**  
Data type: decimal  
Description: Indication of the betting odds of a partial bet  
Mandatory: yes  
Restriction: Must be greater than 1

As a betKind, the following options are possible:

**Single** This is a single bet.

**Combination** This is a combination bet.

**Specific** This is a specific system.

Example of a single bet

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "BetPlacementUpdate",
"eventTime": "2020-11-20T09:42:29.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug==",
"betId": "555-666",
"areaId": "14",
"stake": 10.00,
"betKind": "Single",
"bets": [
{
"subBetId": "s111-222-333",
"betTypeId": "c72a5a59-74cc-4917-8e2a-6d75acf392b3",
"betOfferId": "123",
"quote": 1.75
}
]
}
```

Example of a combination bet or system bet

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "BetPlacementUpdate",
"eventTime": "2020-11-20T09:42:29.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug==",
"betId": "555-666",
"areaId": "14",
"stake": 10.00,
"betKind": "Combination",
"bets": [
{
"subBetId": "s111-222-333",
"betTypeId": "c72a5a59-74cc-4917-8e2a-6d75acf392b3",
"betOfferId": "123",
"quote": 1.50
},
{
},
"subBetId": "s444-555-666",
"betTypeId": "d34a5a59-74cc-4917-8e2a-6d75acf395c6",
"betOfferId": "123",
"quote": 4.75
}
]
}
```

Notes

- The event to change a placed bet is a new event with its own eventId. Except for playerId and betID, all details can be changed.
- It is possible to change the method of betting. In this case, the individual bets may have to be adjusted. For a single bet, the bets field must contain exactly one entry. For combined bets or specific systems, at least two entries must be included.

#### 7.10.5 Weather result

Information on the outcome of a player's bet.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "BetResult

**eventTime**  
Data type: datetime  
Description: Time when the bet was finished  
Mandatory: yes  
Restriction: -

**playerId**  
Data type: identifier  
Description: Identification of the player with the provider  
Mandatory: yes  
Restriction: Reference to an existing player

**betId**  
Data type: identifier  
Description: Unique identifier of the placed bet  
Mandatory: yes  
Restriction: Reference to existing bet of the player

**profit**  
Data type: money  
Description: Betting profit  
Mandatory: yes  
Restriction: 0 for reason "Lost", otherwise greater than 0

**reason**  
Data type: identifier  
Description: Reason why the bet was terminated  
Mandatory: yes  
Restriction: See table below for valid values

The following options are possible as reasons for ending a bet:

**Won** The bet was won.  
**Lost** The bet has been lost.  
**Canceled** The bet has been cancelled.  
**CashOut** The bet was sold early.

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "BetResult",
"eventTime": "2020-11-20T09:42:29.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug==",
"betId": "123",
"profit": 15.00,
"reason": "won"
}
```

Notes

- If a bet is cancelled with reason "Canceled", profit must be equal to the current stake of the bet.

#### 7.10.6 Change of the weather result

Changed information on the outcome of a player's bet, e.g. when the official final result of a sporting event is changed.

Fields

**eventId**  
Data type: identifier  
Description: Unique Id of the event  
Mandatory: yes  
Restriction: -

**eventName**  
Data type: identifier  
Description: Unique identifier of the event  
Mandatory: yes  
Restriction: Must contain the value "BetResultUpdate

**eventTime**  
Data type: datetime  
Description: Time when the weather result was changed  
Mandatory: yes  
Restriction: -

**playerId**  
Data type: identifier  
Description: Identification of the player with the provider  
Mandatory: yes  
Restriction: Reference to an existing player

**betId**  
Data type: identifier  
Description: Unique identifier of the placed bet  
Mandatory: yes  
Restriction: Reference to existing bet of the player

**profit**  
Data type: money  
Description: Betting profit  
Mandatory: yes  
Restriction: 0 for reason "Lost", otherwise greater than 0

**reason**  
Data type: identifier  
Description: Reason why the bet was terminated  
Mandatory: yes  
Restriction: See table below for valid values

The following options are possible as types of bet:

**Won** The bet was won.  
**Lost** The bet has been lost.  
**Canceled** The bet has been cancelled.  
**CashOut** The bet was sold early.

Example

```json
{
"eventId": "1c674ff4-ec1e-4821-b206-ab851cb7ec82",
"eventName": "BetResultUpdate",
"eventTime": "2020-11-20T09:42:29.725Z",
"playerId": "5emh/t5chEyN8S68yG1Rug==",
"betId": "123",
"profit": 15.00,
"reason": "won"
}
```

Notes

- If a bet is cancelled with reason "Canceled", profit must be equal to the current stake of the bet.
- The event to change a weather result is a new event with its own eventId. Except for playerId and betID, all details can be changed.

## 8 Examples

This chapter outlines some typical scenarios. Based on these examples, the respective sequence of events triggered by them is clarified.

### 8.1 Initial connection safe server

A provider initially binds its safe server.

1. The provider creates areas. Event: Add Area
2. The provider creates single player games. Event: Add single player game
3. The provider deposits the corresponding authorisation for each single-player game. Event: Approval Single Player Game
4. The provider creates community player games. event: Add community player game
5. The provider deposits the corresponding approval for each community player game. Event: Approval for Community Player Game
6. The provider defines which payment services it supports. Event: Add Payment Service
7. The provider transmits which players he has in the system. Event: Register

### 8.2 Player creates an account

A player who has not yet registered with the provider registers with the provider.

1. The provider stores the player's personal data. Event: Register
2. If applicable, the provider obliges the player to specify a payment method already with the registration. Event: Add payment method
3. The player must be made known to the central files and in the course of this select an inter-provider limit or confirm an already existing inter-provider limit. Event: Transmission of Player Data
4. The status of the player after registration is in the status "VerificationPending" with intent "Registration Event: Status
5. The player confirms that he/she has taken note of the instructions for the provisional match. Event: Confirmation of provisional match
6. The status of the player changes to "VerificationPending" with intent "TemporarilyAccepted". Event: Status
7. The player makes a deposit of €100. Event: Deposit
8. This is first checked at the central files. Event: Deposit
9. If successful, the deposit is credited to the gaming account. Event: Transaction in the gaming account
10. The games subsequently performed by the player after registration are analogous to, for example Average play cycle from step 3.
11. After the provider has checked the data, the player's status changes to "Verified". Event: Status

### 8.3 Average play cycle

A fully unlocked, non-blocked player logs in, plays a few games and logs out. This example illustrates the ideal game cycle without special cases such as bans or cross effects from competing providers.

1. The player logs in. Event: Log-in
2. The provider may not have sent him his statistical turnover data for more than 24 hours and must now do so. Event: Information on statistical data
3. The provider has to check that the player is not globally blocked. Event: Blocking check
4. The provider must set the player to active in the central files before the player participates in a match. Event: Active status
5. The player selects a virtual slot game and confirms that he/she wishes to play it (chargeable or not does not matter here). Event: Player Declaration Virtual Au- tomato Game
6. The match begins. Event: Start Single Player Match
7. The match ends. Event: End of single player match
8. The player continues to play for a few more rounds. The steps from player declaration to the end of the match are to be repeated accordingly with the exception of the active status (as the player is already active for the provider) and the request to the ban file.
9. The player is so engrossed in the game that he loses track of time. An hour has already passed. The supplier must now inform the player of the time that has passed. Event : Reality check
10. The player confirms the provider's hint. Event: Reality Check Confirmation
11. Shocked at how quickly time has passed, the player logs out of the provider. Event: Inducement Inactivation
12. Due to the player's instigation, the provider is obliged to set the player to inactive in the activity file. Event: Active status

### 8.4 Procedure for the annual player data verification by the provider

1. The provider initiates the verification of the player data before one year has elapsed since the last data confirmation in accordance with Section 6a (5) GlüStV 2021. The status of the player changes to "Verifica- tionPending with intent "RegularCycle". Event: Status
2. The player checks his data for accuracy and confirms or corrects it: 2a. The player confirms his data. Event: Data confirmation or 2b. If the player changes his or her data (event: data change), he or she still receives the status "VerificationPending" but with the intent "DataChanged". Event: Status.
3. The provider verifies the player. The status of the player changes to "Verified". Event: Sta- tus.

## 9 Attachments

- Annex transliteration rule, LUGAS
- Payment Services Annex, LUGAS