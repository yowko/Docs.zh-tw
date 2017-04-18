---
title: "服務 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# 服務
服務  
  
## 語法  
  
```  
class Service  
{  
  string BaseAddresses[];  
  Behavior Behaviors[];  
  string ConfigurationName;  
  string CounterInstanceName;  
  string DistinguishedName;  
  string Extensions[];  
  string Metadata[];  
  string Name;  
  string Namespace;  
  datetime Opened;  
  Channel OutgoingChannels[];  
  sint32 ProcessId;  
};  
```  
  
## 方法  
 此服務類別不會定義任何方法。  
  
## 屬性  
 此服務類別具有下列屬性：  
  
### BaseAddresses  
 資料型別：字串陣列  
  
 存取類型：唯讀  
  
 由服務使用的基底位址。  
  
### Behaviors  
 資料型別：行為陣列  
  
 存取類型：唯讀  
  
 與此服務關聯的行為。  
  
### ConfigurationName  
 資料型別：字串  
  
 存取類型：唯讀  
  
 ServiceElement\_BehaviorConfiguration  
  
### CounterInstanceName  
 資料型別：字串  
  
 存取類型：唯讀  
  
 服務效能計數器之執行個體的名稱。  
  
### DistinguishedName  
 資料型別：字串  
  
 存取類型：唯讀  
  
 位址的服務名稱。  
  
### Extensions  
 資料型別：字串陣列  
  
 存取類型：唯讀  
  
 服務執行個體擴充的執行個體內容。  
  
### Metadata  
 資料型別：字串陣列  
  
 存取類型：唯讀  
  
 服務中繼資料設定。  
  
### Name  
 資料型別：字串  
  
 存取類型：唯讀  
  
 這個服務的唯一名稱。  
  
### 命名空間  
 資料型別：字串  
  
 存取類型：唯讀  
  
 服務的命名空間。  
  
### Opened  
 資料型別：日期時間  
  
 存取類型：唯讀  
  
 服務開啟的時間。  
  
### OutgoingChannels  
 資料類型：通道陣列  
  
 存取類型：唯讀  
  
 從服務執行個體傳出的通道。  
  
### ProcessId  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 裝載服務之處理序的處理序識別碼。  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|命名空間|於 root\\ServiceModel 中定義|