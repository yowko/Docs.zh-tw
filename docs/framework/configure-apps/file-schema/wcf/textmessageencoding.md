---
title: "&lt;textMessageEncoding&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# &lt;textMessageEncoding&gt;
指定字元編碼和訊息版本處理，用於文字 XML 訊息。  
  
## 語法  
  
```  
  
<textMessageEncoding maxReadPoolSize="Integer"  
   maxWritePoolSize="Integer"  
   messageVersion="Soap11Addressing10/Soap12Addressing10"  
      writeEncoding=”UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|maxReadPoolSize|整數，指定可以同時讀取而不需配置新讀取器的訊息數。  較大的集區大小可讓系統容許更多活動失效的情況，但是會產生較大的工作集。  預設值為 64。|  
|maxWritePoolSize|整數，指定可以同時傳送而不需配置新寫入器的訊息數。  較大的集區大小可讓系統容許更多活動失效的情況，但是會產生較大的工作集。  預設值為 16。|  
|messageVersion|指定使用這個繫結所傳送訊息的 SOAP 版本。  有效值為<br /><br /> -   Soap11Addressing10<br />-   Soap12Addressing10<br /><br /> 預設為 Soap12Addressing10。  此屬性的型別為 <xref:System.ServiceModel.Channels.MessageVersion>。|  
|writeEncoding|指定要在繫結上發出訊息時使用的字元集編碼方式。  有效值為<br /><br /> -   UnicodeFffeTextEncoding：Unicode BigEndian 編碼方式<br />-   Utf16TextEncoding：Unicode 編碼方式<br />-   Utf8TextEncoding：8 位元編碼方式<br /><br /> 預設為 Utf8TextEncoding。  此屬性的型別為 <xref:System.Text.Encoding>。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<readerQuotas\>](../Topic/%3CreaderQuotas%3E.md)|定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。  此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<繫結\>](../../../../../docs/framework/misc/binding.md)|定義自訂繫結的所有繫結功能。|  
  
## 備註  
 編碼是將訊息轉換成位元組序列的處理序，  解碼則是相反的處理序。  Windows Communication Foundation \(WCF\) 包含 SOAP 訊息的三種編碼類型：文字、二進位和訊息傳輸最佳化機制 \(MTOM\)。  
  
 `textMessageEncoding` 項目所代表的文字編碼為最具互通性，但針對 XML 訊息編碼器的效率最為不彰。  文字編碼器會在網路上建立文字訊息。  此編碼器產生的訊息適合 WS\-\* 型的互通性。  Web 服務或 Web 服務用戶端通常可以了解文字 XML。  不過，若要針對 XML 訊息進行編碼，將大型二進位資料區塊當做文字傳輸是效率最差的方法。  
  
## 範例  
  
```  
<textMessageEncoding maxReadPoolSize="211"  
    maxWritePoolSize="2132"  
    messageVersion="Soap12Addressing10"  
    textEncoding=”utf-8” />  
```  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>   
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>   
 [選擇訊息編碼器](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)   
 [訊息編碼](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)   
 [繫結](../../../../../docs/framework/wcf/bindings.md)   
 [擴充繫結](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [自訂繫結](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)