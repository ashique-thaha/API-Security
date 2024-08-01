`SOAP (Simple Object Access Protocol)`

- SOAP is like XML, but it does more than XML-RPC. It has two parts: a header and a payload. The header says what to do with the message, and the payload carries the actual information. You can also use WSDL, which explains how to use SOAP services. Different protocols, like HTTP, can carry SOAP messages.

##### Anatomy of a SOAP Message
- `soap:Envelope`: (Required block) Tag to differentiate SOAP from normal XML. This tag requires a `namespace` attribute.
- `soap:Header`: (Optional block) Enables SOAP’s extensibility through SOAP modules.
- `soap:Body`: (Required block) Contains the procedure, parameters, and data.
- `soap:Fault`: (Optional block) Used within `soap:Body` for error messages upon a failed API call.


```xml
--> POST /Quotation HTTP/1.0
  Host: www.xyz.org
  Content-Type: text/xml; charset = utf-8
  Content-Length: nnn

  <?xml version = "1.0"?>
  <SOAP-ENV:Envelope
    xmlns:SOAP-ENV = "http://www.w3.org/2001/12/soap-envelope"
     SOAP-ENV:encodingStyle = "http://www.w3.org/2001/12/soap-encoding">

    <SOAP-ENV:Body xmlns:m = "http://www.xyz.org/quotations">
       <m:GetQuotation>
         <m:QuotationsName>MiscroSoft</m:QuotationsName>
      </m:GetQuotation>
    </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>

  <-- HTTP/1.0 200 OK
  Content-Type: text/xml; charset = utf-8
  Content-Length: nnn

  <?xml version = "1.0"?>
  <SOAP-ENV:Envelope
   xmlns:SOAP-ENV = "http://www.w3.org/2001/12/soap-envelope"
    SOAP-ENV:encodingStyle = "http://www.w3.org/2001/12/soap-encoding">

  <SOAP-ENV:Body xmlns:m = "http://www.xyz.org/quotation">
  	  <m:GetQuotationResponse>
  	     <m:Quotation>Here is the quotation</m:Quotation>
     </m:GetQuotationResponse>
   </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
```


**Note**: You may come across slightly different SOAP envelopes. Their anatomy will be the same, though.

