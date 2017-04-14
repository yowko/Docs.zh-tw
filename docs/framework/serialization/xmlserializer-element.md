---
title: "&lt;xmlSerializer&gt; 項目 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<xmlSerializer> 項目"
  - "XML 序列化, 組態"
  - "xmlSerializer 項目"
ms.assetid: d129d10c-3eb7-45d9-8098-5fa853825e47
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# &lt;xmlSerializer&gt; 項目
指定是否已完成 <xref:System.Xml.Serialization.XmlSerializer> 進度的其他檢查。  
  
## 語法  
  
```  
  
<xmlSerializer checkDeserializerAdvance = "true"|"false" />  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|**checkDeserializeAdvances**|指定是否已檢查 <xref:System.Xml.Serialization.XmlSerializer>的進度。  設定屬性為 "true" 或 "false"。  預設為 "true"。|  
|**useLegacySerializationGeneration**|指定 <xref:System.Xml.Serialization.XmlSerializer> 是否使用舊版序列化產生作業，此作業會將 C\# 程式碼寫入至檔案並編譯成組件，藉此產成組件。  預設為 **false**。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<system.xml.serialization\> 項目](../../../docs/framework/serialization/system-xml-serialization-element.md)|包含 <xref:System.Xml.Serialization.XmlSerializer> 及 <xref:System.Xml.Serialization.XmlSchemaImporter> 類別的組態設定。|  
  
## 備註  
 根據預設， <xref:System.Xml.Serialization.XmlSerializer> 提供額外層級的安全性，在還原序列化未受信任的資料時，避免潛在的拒絕服務攻擊。  做法是嘗試在還原序列化期間，偵測無限迴圈。  若偵測到這樣的狀況，將擲回例外狀況並且顯示下列訊息：「內部錯誤: 還原序列化無法處理基礎資料流」。  
  
 接收到此訊息並不表示正在進行阻絕服務攻擊。  在某些罕見的狀況下，無限迴圈偵測機制產生誤判，使得合法的傳入訊息導致擲回例外狀況。  如果您發現自己特定的應用程式合法訊息，遭到此額外的保護層級拒絕，請將 **checkDeserializeAdvances** 屬性設定為 "false"。  
  
## 範例  
 下列程式碼範例將 **checkDeserializeAdvances** 屬性設為 "false"。  
  
```  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
  </system.xml.serialization>  
</configuration>  
```  
  
## 請參閱  
 <xref:System.Xml.Serialization.XmlSerializer>   
 [\<system.xml.serialization\> 項目](../../../docs/framework/serialization/system-xml-serialization-element.md)   
 [XML 和 SOAP 序列化](../../../docs/framework/serialization/xml-and-soap-serialization.md)