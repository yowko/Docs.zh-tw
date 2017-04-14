---
title: "端點 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fe63370d-81a1-40f3-97c2-59cb357c78d2
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# 端點
端點  
  
## 語法  
  
```  
class Endpoint  
{  
  string Address;  
  string AddressHeaders[];  
  string AddressIdentity;  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  Binding Binding;  
  string ContractName;  
  string CounterInstanceName;  
  string ListenUri;  
  string Name;  
  sint32 ProcessId;  
  Contract ref;  
};  
```  
  
## 方法  
 Endpoint 類別定義下列方法。  
  
|方法|描述|  
|--------|--------|  
|[GetOperationCounterInstanceName](../../../../../docs/framework/wcf/diagnostics/wmi/getoperationcounterinstancename.md)|擷取作業效能計數器執行個體名稱|  
  
## 屬性  
 Endpoint 類別具有下列屬性：  
  
### 地址  
 資料型別：字串  
  
 存取類型：唯讀  
  
 包含端點位址的 URI。  
  
### AddressHeaders  
 資料型別：字串陣列  
  
 存取類型：唯讀  
  
 附加到此端點之位址標頭的集合。  
  
### AddressIdentity  
 資料型別：字串  
  
 存取類型：唯讀  
  
 端點的身分識別。  
  
### AppDomainId  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 裝載端點之 appdomain 的 appdomain 識別碼。  
  
### 行為  
 資料型別：行為陣列  
  
 存取類型：唯讀  
  
 此端點實作之行為的集合。  
  
### 繫結  
 資料型別：繫結  
  
 存取類型：唯讀  
  
 此端點所使用的繫結。  
  
### ContractName  
 資料型別：字串  
  
 存取類型：唯讀  
  
 指定公開此端點之合約的字串。  
  
### CounterInstanceName  
 資料型別：字串  
  
 存取類型：唯讀  
  
 端點之效能計數器執行個體的名稱。  
  
### ListenUri  
 資料型別：字串  
  
 存取類型：唯讀  
  
 端點接聽的 Uri。  
  
### 名稱  
 資料型別：字串  
  
 存取類型：唯讀  
  
 此端點的唯一名稱。  
  
### ProcessId  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 裝載端點之處理序的處理序識別碼。  
  
### ref  
 資料型別：合約  
  
 存取類型：唯讀  
  
 此端點公開的合約。  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|命名空間|於 root\\ServiceModel 中定義|