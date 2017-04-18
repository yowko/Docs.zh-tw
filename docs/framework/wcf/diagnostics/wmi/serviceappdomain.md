---
title: "ServiceAppDomain | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f28e5186-a66d-46c1-abe9-b50e07f8cb4f
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# ServiceAppDomain
將服務對應至應用程式定義域。  
  
## 語法  
  
```  
class ServiceAppDomain  
{  
  Service ref;  
  AppDomainInfo ref;  
};  
```  
  
## 方法  
 ServiceAppDomain 類別不會定義任何方法。  
  
## 屬性  
 ServiceAppDomain 類別具有下列屬性：  
  
### ref  
 資料型別：服務               
 限定詞：索引鍵  
  
 存取類型：唯讀  
  
 這個應用程式定義域的服務。  
  
### ref  
 資料型別：AppDomainInfo               
 限定詞：索引鍵  
  
 存取類型：唯讀  
  
 包含應用程式定義域的屬性。  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|命名空間|於 root\\ServiceModel 中定義|