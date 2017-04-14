---
title: "OneWayBindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# OneWayBindingElement
OneWayBindingElement  
  
## 語法  
  
```  
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## 方法  
 OneWayBindingElement 類別不會定義任何方法。  
  
## 屬性  
 OneWayBindingElement 類別具有下列屬性：  
  
### ChannelPoolSettings  
 資料型別：ChannelPoolSettings  
  
 存取類型：唯讀  
  
 通道集區設定。  
  
### MaxAcceptedChannels  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 已接受之通道的數目上限。  
  
### PacketRoutable  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 代表封包是否為可路由傳送的值。  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|命名空間|於 root\\ServiceModel 中定義|  
  
## 請參閱  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>