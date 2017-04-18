---
title: "dataContractSerializer | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# dataContractSerializer
包含 <xref:System.Runtime.Serialization.DataContractSerializer> 的組態資料。  
  
## 語法  
  
```  
  
<dataContractSerializer ignoreExtensionDataObject="Boolean"  
      maxItemsInObjectGraph="Integer" />  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|項目|描述|  
|--------|--------|  
|ignoreExtensionDataObject|布林值，指定當端點序列化或還原序列化時，是否略過端點所提供的資料。|  
|maxItemsInObjectGraph|整數，指定要序列化或還原序列化的項目數上限。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<行為\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|指定端點行為。|  
  
## 備註  
 如需已知型別的詳細資訊，請參閱 <xref:System.Runtime.Serialization.DataContractSerializer> 文件。  
  
> [!CAUTION]
>  `<dataContractSerializer>` 行為項目 \(如果有的話\) 必須永遠出現在組態檔中 `<enableWebScript>` 行為項目之前。  否則，產生的行為未定義。  
  
## 請參閱  
 <xref:System.Runtime.Serialization.DataContractSerializer>   
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>   
 <xref:System.ServiceModel.Configuration.DataContractSerializerElement>   
 [資料合約已知型別](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)   
 [資料傳輸與序列化](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)