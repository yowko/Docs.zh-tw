---
title: "Channel 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Channel 類別
通道  
  
## 語法  
  
```  
class Channel  
{  
  string LocalAddress;  
  Endpoint ref;  
  string RemoteAddress;  
  string SessionId;  
  string Type;  
};  
```  
  
## 方法  
 Channel 類別並未定義任何方法。  
  
## 屬性  
 Channel 類別具有下列屬性。  
  
### LocalAddress  
 資料型別：字串  
  
 存取類型：唯讀  
  
 通道的本機端點。  
  
### ref  
 資料型別：端點  
  
 存取類型：唯讀  
  
 通道所連接之端點的參考。  
  
### RemoteAddress  
 資料型別：字串  
  
 存取類型：唯讀  
  
 與通道相關聯的遠端位址。  
  
### SessionId  
 資料型別：字串  
  
 存取類型：唯讀  
  
 目前工作階段識別碼 \(如果有\)。  
  
### 類型  
 資料型別：字串  
  
 存取類型：唯讀  
  
 通道的類型。  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|命名空間|於 root\\ServiceModel 中定義|  
  
## 請參閱  
 <xref:System.ServiceModel.Channels.ChannelBase>