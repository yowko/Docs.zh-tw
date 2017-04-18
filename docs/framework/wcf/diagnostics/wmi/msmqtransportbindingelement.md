---
title: "MsmqTransportBindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# MsmqTransportBindingElement
MsmqTransportBindingElement  
  
## 語法  
  
```  
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## 方法  
 MsmqTransportBindingElement 類別並未定義任何方法。  
  
## 屬性  
 MsmqTransportBindingElement 類別具有下列屬性：  
  
### MaxPoolSize  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 包含內部 MSMQ 訊息物件之集區的大小上限。  
  
### QueueTransferProtocol  
 資料型別：字串  
  
 存取類型：唯讀  
  
 代表此繫結使用之已佇列通訊通道傳輸的列舉值。  
  
### UseActiveDirectory  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 傳回布林值，這個值表示是否應該使用 Active Directory 轉換佇列位址。  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|命名空間|於 root\\ServiceModel 中定義|  
  
## 請參閱  
 <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>