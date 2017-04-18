---
title: "ServiceToEndpointAssociation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# ServiceToEndpointAssociation
將服務對應至端點。  
  
## 語法  
  
```  
class ServiceToEndpointAssociation  
{  
  Service ref;  
  Endpoint ref;  
};  
```  
  
## 方法  
 ServiceToEndpointAssociation 類別並未定義任何方法。  
  
## 屬性  
 ServiceToEndpointAssociation 類別有下列屬性：  
  
### ref  
 資料型別：服務  
  
 存取類型：唯讀  
限定詞：索引鍵  
  
 與端點關聯的服務。  
  
### ref  
 資料型別：端點  
  
 存取類型：唯讀  
限定詞：索引鍵  
  
 與服務關聯的端點。  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|命名空間|於 root\\ServiceModel 中定義|