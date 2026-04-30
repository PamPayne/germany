---
country: Germany
document_name: Technical Guideline Central Files
source_file: 20230510_LUGAS_Technische Richtlinie_Zentraldateien V1.11.3 en-GB - ISMS.pdf
extracted_date: 2026-04-30
jurisdiction: Germany
---

# Technical Guideline Central Files

Multi-state Gaming Supervision System (LUGAS)

Publisher: Dataport AöR  
on behalf of the  
Ministry of the Interior and Sport of the State  
of Saxony-Anhalt

Version: 1.11.3  
08.05.2023

## Table of contents

1 List of amendments 3  
2 Introduction 6  
3 Definitions 7  
4 System overview 7  
5 Authentication and issuance of a client certificate 8  
5.1 Issuing a client certificate for the first time 8  
5.2 Further client certificate management 10  
6 Interface description 11  
6.1 Character set and data types 11  
6.2 Error messages 12  
6.2.1 Basic error class 12  
6.2.2 Validation error class 12  
6.3 Central files of the players 13  
6.3.1 General error codes 13  
6.3.2 Create player 13  
6.3.3 Change player data 17  
6.3.4 Delete player 19  
6.3.5 Change limit 20  
6.3.6 Make a deposit 23  
6.3.7 Set players ACTIVE/INACTIVE 25  
6.3.8 Change PlayerId 26  
6.3.9 Find PlayerId 27  
6.4 Client certificate management 29  
6.4.1 Sign CSR 29  
6.4.2 Reissue Client Certificate 31  
6.4.3 Revocation of a client certificate 32  
7 Data deletion 33

## 1 List of changes

### Version 1.1 from 10.06.2021

- Removing error code F0002 from the Create Player operation
- Set correction of the path for players ACTIVE/INACTIVE

### Version 1.2 from 17.06.2021

- Further note on using the script for issuing a client certificate for the first time

### Version 1.3 from 25.06.2021

- Correction of the basic error class
- Correction of the HTTP status code when a player is successfully created

### Version 1.4 from 11.08.2021

- Correction of the data type for errorCode
- Add error code F1032 to the operation Sign CSR
- Add error code F0005 to the Make Deposit operation.

### Version 1.5 from 30.08.2021

- Adding a hint for encoding special characters in the operation Find PlayerId

### Version 1.6 from 29.09.2021

- Correction of the wording for error codes for the operation Sign CSR
- Correction of the wording for error codes and notes on the operation Reissue client certificate
- Add error code F1035 to the Reissue Client Certificate operation.
- Removing Error Code F1033 for Operation Revocation of a Client Certificate
- Add the response 403 (Forbidden) to the Revoke a Client Certificate operation.
- Removing the "since" parameter of the Revoke a Client Certificate operation
- Adding a note for transitional arrangements when making deposits for organisers of sports betting and horserace betting on the internet
- Correction of the validation error class example
- Revision of the error codes and addition of the new error code F1023 to the operation Set player ACTIVE/INACTIVE

### Version 1.7 from 14.10.2021

- Remove error code F1031 for Operation CSR signin
- Correction of the wording for error code F1034 for the operation Sign CSR
- Add error code F1041 to the operation Sign CSR
- Add error code F1050 to the operation Sign CSR
- Add error code F1041 to the Reissue Client Certificate operation.
- Add error code F1050 to the Reissue Client Certificate operation.
- Add error code F1036 to the Revoke a Client Certificate operation.
- Correction of the wording for the response 403 (Forbidden) for the operation Revocation of a client certificate
- Removing Error Code F1032 for Operation Revocation of a Client Certificate

### Version 1.8 from 23.11.2021

- Add error code F1037 to the Reissue Client Certificate operation.
- Add the possible response for status code 202 (Accepted) to the operation Set player ACTIVE/INACTIVE.
- Adding the section for General Error Codes and the error code F0006
- Removal of the error codes from the operations already described by the General Error Codes

### Version 1.9 from 14.02.2022

- Definition PlayerId sharpened Definition of terms
- Supplement Note on handling personal data Create player, change player data
- Supplement Note on the response time of the activity file Set player ACTIVE/INACTIVE
- Revision of the description for the operation Reissue Client Certificate
- Correction of error code F1037 for the operation Reissue Client Certificate

### Version 1.10 from 10.05.2022

- Response time specifies players' central files
- Request repetitions added for error codes F0004, F0006 and F0005 Create player, change F0005 limit, make F0005 deposit

### Version 1.10.1 from 05.07.2022

- Correction of status code (404 to 409) in error code F0005 Make Deposit

### Version 1.11 from 10.08.2022

- Separate from the attribute "name" in "givenName" and "lastName" in
  - Create player
  - Find PlayerID
  - Change player data
- Renaming attribute "birthLocation" to "birthPlace" in
  - Create player
  - Find PlayerID
  - Change player data
- Adapt the examples to new transliteration rules.

### Version 1.11.1 from 06.10.2022

- Response body for limit is retained in
  - Create player
  - Change limit
- Merging of the examples for the response for limit reduction and limit is maintained in
  - Create player
  - Change limit

### Version 1.11.2 from 21.11.2022

- Clarification that field names are case-insensitive in central file responses. Record set and data types

### Version 1.11.3 from 08.05.2023

- Updating the Sample Request for Reissue Client Certificate

## 2 Introduction

As of 1 July 2021, the State Treaty on the New Regulation of Gambling in Germany of 29 October 2020 (State Treaty on Gaming 2021 - GlüStV 2021).

In the future, the supervision of gambling on the Internet will be carried out by the Joint Gambling Authority of the Federal States with headquarters in Halle (Saale). During a transitional period until 31 December 2022, individual federal states will perform gambling law tasks with nationwide responsibility pursuant to Section 27p GlüStV 2021. Against this background, the competent gambling supervisory authority of the State of Saxony-Anhalt, the State Administration Office, will in particular be responsible for the management of the information technology systems provided for the monitoring of the gambling market on the Internet pursuant to the State Gambling Treaty from 1 July 2021.

The connection to these systems is obligatory for permitted providers of games of chance on the internet according to the State Treaty on Games of Chance 2021.

The Inter-Länder Gaming Supervision System (LUGAS) created for this purpose consists of the central files, consisting of

- the deposit limit setting file (limit file),
- the parallel play prevention file (activity file)

and the evaluation system (see Technical Guideline Safe-Server).

The competent authority shall use the evaluation system regulated in Section 6i (2) GlüStV 2021 as a tool for the supervision of gambling on the Internet. It ensures that the data collected by the gambling providers themselves are evaluated and reviewed with regard to compliance with the GlüStV.

Gambling operators are obliged to record all required data accurately.

The collection and provision of data is carried out independently by the gaming operators on so-called safe servers, which are to be set up and operated by the gaming operators at their own expense. The data must be stored on the safe server in a digitally unchangeable form and must allow for control at any time, including direct access by the competent supervisory authority. The evaluation system shall continuously access the safe server and retrieve the data provided for processing.

## 3 Definitions of terms

**Provider** A provider is an organiser of sports betting, online casino games, online poker or virtual slot machine games on the internet who has obtained a permit pursuant to Section 4 GlüStV 2021.

**Limit** Cross-provider deposit limit to limit a player's monthly deposits.

**PlayerId** Unique identifier of a player at a provider. Is assigned by the provider and must be entered during registration. Not a cross-provider identifier.

## 4 System overview

Figure 1: Technical context

LUGAS provides three interfaces with different functions:

- Public API  
  URI template: https://public.api.{domain}  
  The public API can be used without client certificates. It allows a client certificate to be issued for the first time.

- Protected API  
  URI template: https://api.{domain}  
  The protected API can only be used with a valid client certificate and a valid permission to gamble online. It allows access to the central files and the management of own client certificates.

- Sandbox API  
  URI template: https://sandbox.api.{domain}  
  The sandbox API can, comparable to the protected API, only be used with a valid client certificate. The sandbox API enables testing of the central files in a separate environment from the protected API. Managing your own client certificates is only possible via the protected API and not via the sandbox API.

No real personal player data may be used for the Sandbox API!

## 5 Authentication and issuance of a client certificate

Authentication against the protected API and the sandbox API is done via client certificates. The client certificates are valid for either the protected API or the sandbox API. This means that with a valid client certificate for the sandbox API, the protected API cannot be called. The issuing of a valid client certificate is described in the following section .

### 5.1 Issuing a client certificate for the first time

In order to facilitate the process of issuing a client certificate, a Linux bash script can be used, which is provided by the responsible gambling supervisory authority. The script automates all further steps so that a signed client certificate is available after its execution. In addition, a function test is carried out using an example query.

Notes:

- The script is used to create a single certificate. Once a script has successfully issued a signed certificate, the contained token is no longer valid.
- If a certificate is already recognised in the current folder, the overwriting must be explicitly confirmed. Alternatively, the script only repeats the function test.
- If the function test was not successful, the authority must be contacted.

`openssl genrsa -out client.key 4096`

`openssl req -new -key client.key -out client.csr -subj "/"`

The (manual) issuing of a client certificate is done in the following steps:

#### 1. Generate private key

A private key can be generated with OpenSSL. Notes:

- The key strength of the RSA algorithm is defined by the BSI1 to be 3072 or 4096 bits for longer operation.

Command:

#### 2. Generate CSR

For reasons of IT security, the process is designed in such a way that the actual secret (private key) lies exclusively with the provider. Therefore, a Certificate Signing Request2 (CSR) must be created to generate a client certificate.

Notes:

- A subject is not required as it is determined for the client certificate by the authority.

Command:

#### 3. Signing the client certificate

The CSR must be sent via HTTP to the public API server. A token issued by the authority must also be specified. The token is only valid for one request and is limited to 30 days. In case of success, the client certificate is delivered as a response.

The specific interface is described in the section Signing CSR.

1 https://www.bsi.bund.de/DE/Themen/Unternehmen-und-Organisationen/Standards-und-Zertifizierung/Technische-Guidelines/TR-sorted-by-topic/tr02102/tr02102_node.html  
2 https://www.globalsign.com/de-de/blog/was-ist-ein-certificate-signing-request

### 5.2 Further client certificate management

Existing client certificates can be renewed independently by the provider before their validity expires. The specific interface is described in the section Issuing a new client certificate.

In addition, the provider has the option to revoke its own client certificates before their validity expires. The specific interface is described in the section Revoking a Client Certificate.

## 6 Interface description

### 6.1 Character set and data types

The API is addressed by means of JSON and is accordingly based on the JSON standard3. Any character encoding with byte order marking can be used for the JSON messages, e.g. UTF-8, UTF-16 BE or LE.

For further explanation of individual fields and their restrictions, the following identifiers are used in this document:

| Identifier | Explanation | Example |
|---|---|---|
| string | Any string of the data set. Control characters are not allowed. | "Hello World!" |
| date | A string containing a date and formatted according to ISO standard 86014. | “2021‑01‑26” |
| datetime | A string containing a date, time and the corresponding time zone, formatted according to ISO standard 86015. | “2021‑01‑26T09:37:37Z” |
| currency | A sequence of digits, with a maximum of two Decimal places which express a monetary amount. This is always given in euros. The value range corresponds to the definition of the data type decimal in C# with the restriction of two decimal places. | 19.99 |
| bool | Gives a truth value. | true |
| int | An integer without decimal places. | 123 |
| object | A complex object that is only used to output additional information. |  |

For all responses of the central files, the names of the fields are case-insensitive.

3 https://www.json.org/  
4 https://www.iso.org/iso-8601-date-and-time-format.html  
5 https://www.iso.org/iso-8601-date-and-time-format.html

### 6.2 Error messages

#### 6.2.1 Basic error class

For error messages, a uniform base class is used with the following fields:

| Name | Data type | Description | Mandatory |
|---|---|---|---|
| errorCode | string | The error code to determine the cause of the error. | yes |

Example:

```json
{
  "errorCode": "F0002"
}
```

Note: This base class can in principle be extended

#### 6.2.2 Validation error class

Error message for validation error

| Name | Data type | Description | Mandatory |
|---|---|---|---|
| errorCode | string | The error code to determine the cause of the error. | yes |
| validationErrors | object | Directory with entries of the validation errors. | yes |

Example:

```json
{
  "validationErrors": {
    "place": [
      "Please enter a valid location."
    ]
  },
  "errorCode": "F0001"
}
```

### 6.3 Central files of the players

Access to the players' central files is only possible via the protected API and the sandbox API. A response can be expected within 5 seconds. After 5 seconds the request should be repeated.

#### 6.3.1 General error codes

The following errors can occur with all requests to the players' central file.

Possible error codes

- F0001 The request does not comply with the transliteration rule or other vali- dation errors have occurred.  
  HTTP status code: 400  
  Data model: Validation error class

- F0004 An internal communication error has occurred (server error). Up to two retries are to be made.  
  HTTP status code: 502  
  Data model: Basic error class

- F0006 An unspecified error has occurred. Up to two retries are to be made.  
  HTTP status code: 500  
  Data model: Basic error class

#### 6.3.2 Create player

The provider registers a player in the central files.

Use cases

- The player has never been registered in the central files by a provider.
  - limitAmount is a mandatory field when creating
  - The limit applies immediately.
- The player has already been registered in the central files by a provider.
  - If the player wants to keep his existing limit, limitAmount remains empty.
  - If limitAmount has been set, the validity behaves analogously to Change Limit.

`POST /players`

Notes

- A pseudonym is formed from the transmitted personal data. In the following, only the pseudonym and the PlayerID are used within the central files.
- Providers may only grant limits for which they have a valid permission to increase the deposit limit. A deposit limit higher than 1,000 euros may only be set by a provider on the basis of a special permit pursuant to Section 6c (1) sentence 3 GlüStV 2021.
- The provider must register a player with a unique PlayerId. Multiple IDs cannot be stored for a player for one provider.
- The personal data must be transferred according to the rules of the transliteration rule (see annex transliteration rule).

Request

Request-Body:

| Name | Data type | Description | Mandatory |
|---|---|---|---|
| givenName | string | The first name of the player. | yes |
| lastName | string | The last name of the player. | yes |
| postcode | string | The postcode of the player's place of residence. | yes |
| place | string | The place of residence of the player's address. | yes |
| street | string | The street of the player's address. | yes |
| number | string | The house number(s) of the player's address. | yes |
| countryAlpha2Code | string | The country of the player's address as ISO 3166-1 ALPHA-2 coded. | yes |
| area | string | The state of the player's residence. | ja |
| birthDate | date | The date of birth of the player. | yes |
| birthPlace | string | The birthplace of the player. | yes |
| birthName | string | The birth name of the player. | yes |
| limitAmount | currency | The amount of the new limit (>=0.01). If a current limit is maintained, this value is not set. | no |
| playerId | string | The PlayerId of the player. Maximum number of characters: 127. characters allowed: a-z A-Z 0-9 - _ \ . | yes |

Example:

```json
{
  "givenName": "Max
  "lastName": "Mustermann",
  "postcode": "06128",
  "place": "Halle (Saale)",
  "street": "eggway",
  "number": "375",
  "countryAlpha2Code": "DE",
  "area": "DE-ST",
  "birthDate": "1990-11-20",
  "birthPlace": "Münster",
  "birthName": "-",
  "limitAmount": 200.00,
  "playerId": "9836d550-dce5-44e8-8ffd-37313215007d"
}
```

Answers

- 201 (Created)  
  The player was successfully created.

Response body (optional):

| Name | Data type | Description | Mandatory |
|---|---|---|---|
| currentLimit | currency | Indicates which limit is currently valid for the player. Is only set if limitAmount is set during creation. was set. | no |
| newLimit | currency | The requested limit of the player. Will only is set if the limitAmount passed is not immediately valid (cf. rules for changing the limit). | no |
| newLimitValidAt | datetime | Indicates when newLimit becomes valid. | no |

- Example (limit increase):

```json
{
  "currentLimit": 150.00,
  "newLimit": 199.47,
  "newLimitValidAt": "2020-11-20T09:42:29.737Z"
}
```

- Example (limit reduction or limit is maintained):

```json
{
  "currentLimit": 199.47
}
```

Possible error codes

- F0003 The specified limit exceeds the limit of 1000 euros and there is no valid authorisation to increase the deposit limit for the specified amount.  
  HTTP status code: 409  
  Data model: Basic error class

- F0005 A memory error has occurred. Please repeat the request. Up to two repetitions are to be made.  
  HTTP status code: 409  
  Data model: Basic error class

- F1001 The player has already been registered.  
  HTTP status code: 409  
  Data model: Basic error class

- F1002 A (different) player has already been registered for the specified PlayerId.  
  HTTP status code: 409  
  Data model: Basic error class

- F1003 A limit must be specified when registering a player for the first time.  
  HTTP status code: 409  
  Data model: Basic error class

#### 6.3.3 Change player data

The provider changes the personal data of a player.

Notes

- The personal data must be transferred according to the rules of the transliteration rule (see annex transliteration rule).
- If a player already exists with the new personal data, both player profiles are merged. When merging, only the most recent PlayerId of a provider is kept.

Request

`PUT /players/{playerId}`

Path parameters:

- playerId: The playerId of the player

Request-Body:

| Name | Data type | Description | Mandatory |
|---|---|---|---|
| givenName | string | The first name of the player. | yes |
| lastName | string | The last name of the player. | yes |
| postcode | string | The postcode of the player's place of residence. | yes |
| place | string | The place of residence of the player's address. | yes |
| street | string | The street of the player's address. | yes |
| number | string | The house number(s) of the player's address. | yes |
| countryAlpha2Code | string | The country of the player's address as ISO 3166-1 ALPHA-2 coded. | yes |
| area | string | The state of residence of the player. | ja |
| birthDate | date | The date of birth of the player. | yes |
| birthPlace | string | The birthplace of the player. | yes |
| birthName | string | The birth name of the player. | yes |

Example:

```json
{
  "givenName": "Max
  "lastName": "sampleWife",
  "postcode": "06128",
  "place": "Halle (Saale)",
  "street": "Kaiserslautererstrasse",
  "number": "75",
  "countryAlpha2Code": "DE",
  { "area": "DE-ST",
  "birthDate": "1990-11-20",
  "birthPlace": "Münster",
  "birthName": "Mustermann
}
```

Answers

- 204 (No Content) - The personal data has been successfully updated.  
  No response body

Possible error codes

- F0002 The player has not yet been registered. Please register the player first.  
  HTTP status code: 404  
  Data model: Basic error class

#### 6.3.4 Delete player

The provider deletes a player from the central files.

Notes

- A pseudonym is formed from the transmitted personal data. In the following, only the pseudonym and the PlayerID are used within the central files.
- Players are to be deleted when the player's gaming account with the provider is deleted.
- The PlayerId is blocked for one year after deletion and cannot be used for new players.
  - Exception: If the deleted player is re-registered, the deleted PlayerId is immediately available again to the provider for this player.
- Deleted players are treated by the central files as non-existent players. The player must be created again before his limit can be set, deposits made or his status (ACTIVE/INACTIVE) changed.

`DELETE /players/{playerId}`

Request

Path parameters:

- playerId: The PlayerId of the player.

Answers

- 202 (Accepted) - The player has been deleted and is no longer usable.  
  No response body

Possible error codes

- F0002 The player has not yet been registered. Please register the player first.  
  HTTP status code: 404  
  Data model: Basic error class

#### 6.3.5 Change limit

The provider changes the maximum limit of a player.

Notes

- Providers can only set limits above €1000 if they have a valid deposit limit increase authorisation to do so.
- The player must already be registered by the provider.
- The player's set limit applies to all providers with which the player is registered. This also applies to a limit over €1000 set by a provider with a deposit limit increase authorisation.
- If the new limit is smaller than the currently valid limit, the new limit applies immediately.
- If the new limit is identical to the currently valid limit, the latter is kept unchanged.
- If the new limit is greater than the currently valid limit, the new limit only becomes valid with a time delay. There are further cases to be distinguished:
  - No increase has yet been notified for the future.
    - The new limit will be valid in 8 days, starting from midnight Central European Time.
    - Example: If the new limit is registered on 12.01.2021 at 11:30 a.m., it will be valid from 20.01.2021 from 0:00 a.m. onwards.
  - Increases have already been notified for the future.
    - The new limit is included in the increases notified. Previously registered increases above the new limit are no longer applicable.
    - Example: Given the following limits, which become valid one after the other:
      - 200 € currently applies
      - 300 € apply in 3 days
      - 500 € apply in 5 days
      - 600 € apply in 7 days
    - The new limit is €300
      - The limit becomes valid in 3 days.
      - Increases to €500 and €600 are omitted.
    - The new limit is € 450
      - The limit becomes valid in 5 days.
      - Increases to €500 and €600 are omitted.
    - The new limit is €500
      - The limit becomes valid in 5 days.
      - Increases to €600 are omitted.
    - The new limit is €1000
      - The limit becomes valid in 8 days.
      - All previous increases remain in place.

Request

Path parameters:

- playerId: The playerId of the player.

Request-Body:

| Name | Data type | Description | Mandatory |
|---|---|---|---|
| limitAmount | currency | The amount of the new limit. | yes |

Example:

```json
{
  "limitAmount": 199.26
}
```

`PUT /players/{playerId}/Limit`

Answers

- 200 (OK) The request was successfully processed  
  Response body:

| Name | Data type | Description | Mandatory |
|---|---|---|---|
| currentLimit | money | Indicates the current limit for the player. | no |
| newLimit | money | Specifies the limit passed to the API. Is filled, if the limit is not immediately valid. | no |
| newLimitValidAt | datetime | Indicates when the limit passed to the API has been becomes valid. Refers to newLimit, is filled accordingly. | no |

- Example (limit increase):

```json
{
  "currentLimit": 150.00,
  "newLimit": 199.47,
  "newLimitValidAt": "2020-11-20T09:42:29.737Z"
}
```

- Example (limit reduction or limit is maintained):

```json
{
  "newLimit": 199.47
}
```

Possible error codes

- F0002 The player has not yet been registered. Please register the player first.  
  HTTP status code: 404  
  Data model: Basic error class

- F0003 The specified limit exceeds the limit of 1000 euros and there is no valid authorisation to increase the deposit limit for the specified amount.  
  HTTP status code: 409  
  Data model: Basic error class

- F0005 A memory error has occurred. Please repeat the request. Up to two repetitions are to be made.  
  HTTP status code: 409  
  Data model: Basic error class

#### 6.3.6 Make a deposit

`POST /players/{playerId}/deposits`

The provider registers a deposit of the player in the central files.

Notes

- The player must already be registered.
- The sum of the player's monthly deposits is limited by the limit. The deposits are totalled across all providers.
- At the beginning of a calendar month (first of the month 00:00 CET), the deposits of the previous month are deleted and the player can again make deposits up to the set deposit limit.
- Once released, deposits cannot be reversed (e.g. if the transaction fails).
- Until 31.12.2022, a special rule applies to organisers of sports betting and horse betting on the internet if the competent authority grants exemptions in individual cases from the legal consequence of the § 6c paragraph 1 sentence 8. In this case, in the event of an error code "F1010", a new deposit in the amount of the current remaining limit must be immediately registered in the central files.

Request

Path parameters:

- playerId: The playerId of the player.

Request-Body:

| Name | Data type | Description | Mandatory |
|---|---|---|---|
| depositAmount | currency | The deposit amount (>=0.01). | yes |

Example:

```json
{
  "depositAmount": 449.73
}
```

Answers

- 204 (No Content) The deposit has been released.  
  No response body

Possible error codes

- F0002 The player has not yet been registered. Please register the player first.  
  HTTP status code: 404  
  Data model: Basic error class

- F0005 A memory error has occurred. Please repeat the request. Up to two repetitions are to be made.  
  HTTP status code: 409  
  Data model: Basic error class

- F1010 The deposit exceeds the remaining budget.  
  HTTP status code: 409  
  Data model: Error message with extension

| Name | Data type | Description | Mandatory |
|---|---|---|---|
| availableBudget | currency | The current remaining budget. | yes |

Example:

```json
{
  "errorCode": "F1010",
  "availableBudget": 200.00
}
```

#### 6.3.7 Set players ACTIVE/INACTIVE

`PUT /players/{playerId}/state`

The provider places a player in the central files ACTIVE or INACTIVE.

Notes

- The player must already be registered.
- ACTIVE in this case means that the player participates in gambling at a provider within the meaning of § 6h GlüStV 2021 (activity file). Setting a player INACTIVE is not the same as deleting the player.
- A player can only be ACTIVELY bet for one provider at a time.
- After the INACTIVE seeding, the player cannot be ACTIVELY seated by any bidder for a waiting period of five minutes.
- Only the provider who has set the player to ACTIVE is entitled to set the player back to ACTIVE.
- Only the provider may allow a player to participate in games who has successfully ACTIVELY wagered the player.
- The activity file usually responds after 5 seconds at the latest. After this period of time, there is no immediate transmission back.

Request

Path parameters:

- playerId: The PlayerId of the player.

Request-Body:

| Name | Data type | Description | Mandatory |
|---|---|---|---|
| isActive | bool | The status of the player. true sets the player to ACTIVE. false sets the player to INACTIVE. | yes |

Example:

```json
{
  "isActive": true
}
```

Answers

- 202 (Accepted) The player's status has been successfully set to INACTIVE.  
  No response body

- 204 (No Content) The player's status has been successfully set to ACTIVE.  
  No response body

Possible error codes

- F0002 The player has not yet been registered. Please register the player first.  
  HTTP status code: 404  
  Data model: Basic error class

- F1020 The player is ACTIVE with another provider.  
  HTTP status code: 409  
  Data model: Basic error class

- F1021 The player is INACTIVE.  
  HTTP status code: 409  
  Data model: Basic error class

- F1022 The player is in the waiting period and cannot yet be set ACTIVE.  
  HTTP status code: 409  
  Data model: Basic error class

- F1023 The player is already ACTIVE with the current provider.  
  HTTP status code: 409  
  Data model: Basic error class

#### 6.3.8 Change PlayerId

The provider changes the PlayerId of the player.

If the previous PlayerId of a player has to be changed for technical reasons, a new one can be assigned.

Notes:

- Each provider may only register a player with a provider-specific player ID.

Request

Path parameters:

- playerId: The playerId of the player.

Request-Body:

| Name | Data type | Description | Mandatory |
|---|---|---|---|
| newPlayerId | string | The new PlayerId of the player. Maximum yes Number of characters: 127. Allowed characters: a-z A-Z 0-9 - _ \ . |  |

Example:

```json
{
  "newPlayerId": "8453e850-bde8-22e7-6fda-14627965865c"
}
```

`PUT /players/{playerId}/id`

Answers

- 204 (No Content) - The PlayerId was successfully changed.  
  No response body

Possible error codes

- F0002 The player has not yet been registered. Please register the player first.  
  HTTP status code: 404  
  Data model: Basic error class

- F1002 A (different) player has already been registered for the specified PlayerId.  
  HTTP status code: 409  
  Data model: Basic error class

#### 6.3.9 Find PlayerId

If, for technical reasons, the previous PlayerId of a player is no longer known to the provider, it can be found with this request by providing the personal data.

`GET /players/findByPersonalData`

Notes:

- The personal data must be transferred according to the rules of the transliteration rule (see annex transliteration rule).

Request

Request header:

- x-personalPlayerData:

| Name | Data type | Description | Mandatory |
|---|---|---|---|
| givenName | string | The first name of the player. | yes |
| lastName | string | The last name of the player. | yes |
| postcode | string | The postcode of the player's place of residence. | yes |
| place | string | The place of residence of the player's address. | yes |
| street | string | The street of the player's address. | yes |
| number | string | The house number(s) of the player's address. | yes |
| countryAlpha2Code | string | The country of the player's address as ISO 3166-1 ALPHA-2 coded. | yes |
| area | string | The state of residence of the player. | ja |
| birthDate | date | The date of birth of the player. | yes |
| birthPlace | string | The birthplace of the player. | yes |
| birthName | string | The birth name of the player. | yes |

With this request, the personal data must be transmitted in the header! Special characters must be HTML-encoded (e.g. Ü -> %C3%9C).

Example:

```text
"x-personalPlayerData: givenName,Max,lastName,Mustermann,postcode06128,place,Halle (Saale),street,Kaiserslautererstrasse,number,75,countryAlpha2Code,DE,area,DE-ST,birthDate,1990-11-20,birthPlace,Münster,birthName,-"
```

Answers

- 200 (OK) - The player has been found.

Response body:

| Name | Data type | Description | Mandatory |
|---|---|---|---|
| playerId | string | The PlayerId of the player. | no |

Example:

```json
{
  "playerId": "8453e850-bde8-22e7-6fda-14627965865c"
}
```

Possible error codes

- F0002 The player has not yet been registered. Please register the player first.  
  HTTP status code: 404  
  Data model: Basic error class

### 6.4 Client certificate management

Access to the client certificate management is only possible via the protected API. An exception is the endpoint Sign CSR for issuing a client certificate for the first time. This is only possible via the public API at .

#### 6.4.1 Sign CSR

The initial issuance of a client certificate is done with the to- ken issued by the authority.

The call is made via the public API

Notes:

- The token is valid only once and for 30 days. If an error occurs during the request, the token expires.

`POST /certificates?token={token}`

Request

Query parameters:

- Token: The one-time valid token issued by the authority to create a certificate.

Request body:

The CSR as a raw string with the content type application/pkcs10.

Example

```bash
curl
--location https://public.api.{domain}/certificates?token={token}
-H "Content-Type: application/pkcs10"
-H "Accept: application/x-x509-user-cert"
--data-binary @client.csr
--output client.pem
```

Answers

- 201 (Created) - The CSR was successfully signed.  
  Response body: Client certificate in PEM format as raw string

Possible error codes

- F0001 Validation errors have occurred.  
  HTTP status code: 400

- F1030 Invalid master data, the client certificate cannot be issued. Please contact the authority.  
  HTTP status code: 409

- F1034 The token does not exist or has already been used. Please contact the authorities.  
  HTTP status code: 404

- F1041 The provider identifier could not be found.  
  HTTP status code: 409

- F1050 The certificate could not be issued. Please contact the authority.  
  HTTP status code: 4XX or 5XX

#### 6.4.2 Reissue Client Certificate

Providers can independently have a new certificate issued for an existing valid client certificate. The newly created certificate is valid again for 365 days.

The call is made via the protected API

Notes:

- Re-issuance is possible at the earliest from the halfway point (from the 182nd day) of the certificate's validity period.

Request

`POST /certificates`

Request-Body:

The CSR as a raw string with the content type application/pkcs10.

Example:

```bash
curl
--location https://api.{domain}/certificates
-H "Content-Type: application/pkcs10"
-H "Accept: application/x-x509-user-cert"
--key old_client.key
--cert old_client.pem
--data-binary @new_client.csr
--output new_client.pem
```

Answers

- 201 (Created) - The CSR was successfully signed.  
  Response body: Client certificate in PEM format as raw string

Possible error codes

- F0001 Validation errors have occurred.  
  HTTP status code: 400

- F1030 Invalid master data, the client certificate cannot be issued. Please contact the authority.  
  HTTP status code: 409

- F1035 The certificate has already been renewed. Please contact the authority.  
  HTTP status code: 403

- F1037 The certificate cannot be renewed. Please contact the authority.  
  HTTP status code: 403

- F1041 The provider identifier could not be found.  
  HTTP status code: 409

- F1050 The certificate could not be issued. Please contact the authority.  
  HTTP status code: 4XX or 5XX

#### 6.4.3 Revocation of a client certificate

Providers can revoke their own client certificates.

The call is made via the protected API

Request

`PUT /certificates/{serial}/revocation`

Path parameters:

serial: The serial number of the client certificate to be revoked.

Request-Body:

| Name | Data type | Description | Mandatory |
|---|---|---|---|
| comment | string | A description for the revocation (optional). | no |

Example:

```json
{
  "comment": "private key stolen"
}
```

Answers

- 200 (No Content) - The revocation has been set.  
  No response body

- 403 (Forbidden) - Access to the certificate has been denied.  
  No response body

Possible error codes

- F0001 Validation errors have occurred.  
  HTTP status code: 400

- F1036 The revocation of the certificate cannot be changed.  
  HTTP status code: 403

## 7 Data deletion

- A player will be deleted from the central files after one year without any action by a gaming operator for this player (limit setting, deposit and ACTIVE setting). If the player becomes active again after this period, the player must be re-registered in the central files.
- A player's deposits are deleted from the central files at the end of the month.