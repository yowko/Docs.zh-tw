---
title: "&lt;參數&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# &lt;參數&gt;
指定當宣告型別為泛型型別時的泛型參數。  
  
## 語法  
  
```  
  
<parameter index="integer"  
                      type=String" />  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|索引|當宣告型別為泛型型別時，會指定將傳回已知型別的泛型參數。|  
|類型|字串，說明用來序列化和還原序列化的已知型別。|  
  
## index 屬性  
  
|值|描述|  
|-------|--------|  
|"0"|泛型型別中的第一個參數。  例如，<xref:System.Collections.Generic.List%601> 只有一個參數。  如果將它當做宣告型別，則 index 會設定為 "0"。|  
|"1"|泛型型別中的第二個參數。  例如，<xref:System.Collections.Generic.Dictionary%602> 有兩個參數。  如果已知型別是由第二個參數傳回的，請將 index 屬性設定為 "1"。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<knownType\>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|指定可由宣告型別的欄位或屬性傳回的已知型別。|  
  
## 備註  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]已知型別的詳細資訊，請參閱[資料合約已知型別](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)和 <xref:System.Runtime.Serialization.DataContractSerializer>。  
  
 如需使用這個項目的範例，請參閱 [\<dataContractSerializer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)。  
  
 此組態項目不可以同時具有這兩個屬性。  如果同時設定了這兩個屬性，就會發生 <xref:System.Configuration.ConfigurationErrorsException>。  
  
## 請參閱  
 <xref:System.Runtime.Serialization.DataContractSerializer>   
 [資料合約已知型別](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)   
 [\<dataContractSerializer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)   
 [\<add\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)