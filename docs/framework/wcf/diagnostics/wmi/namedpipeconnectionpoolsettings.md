---
title: "NamedPipeConnectionPoolSettings | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 079bccb8-54b5-4436-a43d-5567763f72ce
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# NamedPipeConnectionPoolSettings
NamedPipeConnectionPoolSettings  
  
## 語法  
  
```  
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## 方法  
 NamedPipeConnectionPoolSettings 類別並未定義任何方法。  
  
## 屬性  
 NamedPipeConnectionPoolSettings 類別具有下列屬性：  
  
### GroupName  
 資料型別：字串  
  
 存取類型：唯讀  
  
 繫結項目所使用之連線集區的群組名稱。  
  
### IdleTimeout  
 資料型別：日期時間  
  
 存取類型：唯讀  
  
 連線中斷之前可閒置的最長時間。  
  
### MaxOutboundConnectionsPerEndpoint  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 用戶端上每個端點的傳出連線數目上限。  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|命名空間|於 root\\ServiceModel 中定義|  
  
## 請參閱  
 <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>