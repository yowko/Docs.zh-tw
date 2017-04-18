---
title: "ChannelPoolSettings | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# ChannelPoolSettings
ChannelPoolSettings  
  
## 語法  
  
```  
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## 方法  
 ChannelPoolSettings 類別不會定義任何方法。  
  
## 屬性  
 ChannelPoolSettings 類別具有下列屬性：  
  
### IdleTimeout  
 資料型別：日期時間  
  
 存取類型：唯讀  
  
 連線中斷之前可閒置的最長時間。  
  
### LeaseTimeout  
 資料型別：日期時間  
  
 存取類型：唯讀  
  
 逾時前可完成租用作業的最長時間。  
  
### MaxOutboundChannelsPerEndpoint  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 每個端點的傳出通道數目上限。  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|命名空間|於 root\\ServiceModel 中定義|  
  
## 請參閱  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>