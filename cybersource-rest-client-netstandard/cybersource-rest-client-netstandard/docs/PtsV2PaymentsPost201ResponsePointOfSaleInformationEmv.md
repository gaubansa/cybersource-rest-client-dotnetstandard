# CyberSource.Model.PtsV2PaymentsPost201ResponsePointOfSaleInformationEmv
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Tags** | **string** | EMV data that is transmitted from the chip card to the issuer, and from the issuer to the chip card. The EMV data is in the tag-length-value format and includes chip card tags, terminal tags, and transaction detail tags.  For information about the individual tags, see the “Application Specification” section in the EMV 4.3 Specifications: http://emvco.com  **Note** Card present information about EMV applies only to credit card processing and PIN debit processing. All other card present information applies only to credit card processing. PIN debit processing is available only on FDC Nashville Global.  **Important** The following tags contain sensitive information and **must not** be included in this field:   - &#x60;56&#x60;: Track 1 equivalent data  - &#x60;57&#x60;: Track 2 equivalent data  - &#x60;5A&#x60;: Application PAN  - &#x60;5F20&#x60;: Cardholder name  - &#x60;5F24&#x60;: Application expiration date (This sensitivity has been relaxed for Credit Mutuel-CIC, American Express Direct, FDC Nashville Global, First Data Merchant Solutions, and SIX)  - &#x60;99&#x60;: Transaction PIN  - &#x60;9F0B&#x60;: Cardholder name (extended)  - &#x60;9F1F&#x60;: Track 1 discretionary data  - &#x60;9F20&#x60;: Track 2 discretionary data  For captures, this field is required for contact EMV transactions. Otherwise, it is optional.  For credits, this field is required for contact EMV stand-alone credits and contactless EMV stand-alone credits. Otherwise, it is optional.  **Important** For contact EMV captures, contact EMV stand-alone credits, and contactless EMV stand-alone credits, you must include the following tags in this field. For all other types of EMV transactions, the following tags are optional.   - &#x60;95&#x60;: Terminal verification results  - &#x60;9F10&#x60;: Issuer application data  - &#x60;9F26&#x60;: Application cryptogram   #### CyberSource through VisaNet - In Japan: 199 bytes - In other countries: String (252)  #### GPX This field only supports transactions from the following card types: - Visa - Mastercard - AMEX - Discover - Diners - JCB - Union Pay International  #### JCN Gateway The following tags must be included: - &#x60;4F&#x60;: Application identifier - &#x60;84&#x60;: Dedicated file name  Data length: 199 bytes  #### All other processors: String (999)  #### Used by Authorization: Optional Authorization Reversal: Optional Credit: Optional PIN Debit processing (purchase, credit and reversal): Optional  | [optional] 
**ChipValidationType** | **string** | Entity or service that provided the validation results returned in &#x60;chipValidationResult&#x60;.  Possible values:  - &#x60;02&#x60;: MasterCard on-behalf pre-validation service (The MasterCard authorization platform validated the M/Chip cryptogram before the authorization request reached the issuer.)  - &#x60;03&#x60;: MasterCard on-behalf stand-in service (The MasterCard authorization platform validated the M/Chip cryptogram because the issuer was not available.)  - &#x60;50&#x60;: Issuer  - &#x60;90&#x60;: Chip fall-back transaction downgrade process (The chip could not be read.)  This field is returned only for NFC payment network tokenization transactions with MasterCard.  **Note** No CyberSource through VisaNet acquirers support EMV at this time.  | [optional] 
**ChipValidationResult** | **string** | Cryptogram validation results returned by the entity or service specified in &#x60;chipValidationType&#x60;.  Possible values: - &#x60;A&#x60;: Application cryptogram is valid, but the application transaction counter (ATC) is outside allowed range. (A large jump in ATC values may indicate data copying or other fraud.) - &#x60;C&#x60;: Chip validation was completed successfully. - &#x60;E&#x60;: Application cryptogram is valid but the ATC indicates possible replay fraud. - &#x60;F&#x60;: Format error in the chip data. - &#x60;G&#x60;: Application cryptogram is valid but is not a valid authorization request cryptogram (ARQC). - &#x60;I&#x60;: Application cryptogram is invalid. - &#x60;T&#x60;: Application cryptogram is valid but terminal verification results (TVR) or card verification results (CVR) are invalid. - &#x60;U&#x60;: Application cryptogram could not be validated because of a technical error.  This field is returned only for NFC payment network tokenization transactions with MasterCard.  **Note** No CyberSource through VisaNet acquirers support EMV at this time.  | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
