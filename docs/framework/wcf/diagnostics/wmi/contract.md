---
title: "合約 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# 合約
合約  
  
## 語法  
  
```  
class Contract  
{  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  string Name;  
  string Namespace;  
  Operation Operations[];  
  sint32 ProcessId;  
  Contract ref;  
  string SessionMode;  
  string Type;  
};  
```  
  
## 方法  
 Contract 類別不會定義任何方法。  
  
## 屬性  
 Contract 類別有下列屬性：  
  
### AppDomainId  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 裝載合約之的 appdomain 的識別碼。  
  
### Behaviors  
 資料型別：行為陣列  
  
 存取類型：唯讀  
  
 與此合約有關聯的行為。  
  
### Name  
 資料型別：字串  
  
 存取類型：唯讀  
  
 WSDL 中合約的名稱。  
  
### 命名空間  
 資料型別：字串  
  
 存取類型：唯讀  
  
 WSDL 中 `portType` 項目的命名空間。  
  
### Operations  
 資料型別：作業陣列  
  
 存取類型：唯讀  
  
 此合約的作業。  
  
### ProcessId  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 裝載合約之處理序的處理序識別碼。  
  
### ref  
 資料型別：合約  
  
 存取類型：唯讀  
  
 當合約是雙工合約時的回呼類型。  
  
### SessionMode  
 資料型別：字串  
  
 存取類型：唯讀  
  
 代表合約是否需要與此合約關聯的繫結才能使用通道工作階段。  
  
### Type  
 資料型別：字串  
  
 存取類型：唯讀  
  
 合約的類型。  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|Namespace|於 root\\ServiceModel 中定義|  
  
## 請參閱  
 <xref:System.ServiceModel.Description.ContractDescription>