---
title: "&lt;knownType&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# &lt;knownType&gt;
指定還原序列化期間要由 <xref:System.Runtime.Serialization.DataContractSerializer> 使用的型別。  項目會指定由「宣告型別」的欄位或屬性所傳回的「已知型別」。如需詳細資訊，請參閱[資料合約已知型別](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)。  
  
## 語法  
  
```  
  
<knownType type="String">  
     <parameter index="Integer"  
                type="String" />  
</knownType>  
```  
  
## 類型  
 `string`  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|類型|指定型別 \(包括命名空間\)、組件名稱、版本、文化特性和公開金鑰權杖。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<參數\>](../../../../../docs/framework/configure-apps/file-schema/wcf/parameter.md)|指定當宣告型別為泛型型別時的參數索引。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|將宣告型別新增至宣告型別集合中。|  
  
## 備註  
 如需已知型別的詳細資訊，請參閱[資料合約已知型別](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)與 <xref:System.Runtime.Serialization.DataContractSerializer>。  
  
 如需使用這個項目的範例，請參閱 [\<dataContractSerializer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)。  
  
## 範例  
  
```  
<add type="MyCompany.Library.Shape,   
           MyAssembly, Version=2.0.0.0, Culture=neutral,  
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">  
           <knownType type="MyCompany.Library.Circle,   
                      MyAssembly, Version=2.0.0.0, Culture=neutral,  
                      PublicKeyToken=XXXXXX,  
                      processorArchitecture=MSIL"/>  
</add>  
```  
  
## 請參閱  
 <xref:System.Runtime.Serialization.DataContractSerializer>   
 [資料合約已知型別](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)   
 [\<dataContractSerializer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)   
 [\<add\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)