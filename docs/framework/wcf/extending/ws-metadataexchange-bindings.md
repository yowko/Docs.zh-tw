---
title: "WS-MetadataExchange 繫結 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# WS-MetadataExchange 繫結
本主題會說明如何為各種傳輸建構預設中繼資料交換繫結。  
  
## 預設繫結  
  
|預設繫結名稱|繫結的建構方式|  
|------------|-------------|  
|MexHttpBinding|已停用傳輸層級安全性的 <xref:System.ServiceModel.WSHttpBinding>。|  
|MexHttpsBinding|支援傳輸層級安全性的 <xref:System.ServiceModel.WSHttpBinding>。|  
|MexNamedPipeBinding|具有使用預設值之 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> 的 <xref:System.ServiceModel.Channels.CustomBinding>。|  
|MexTcpBinding|具有使用預設值之 <xref:System.ServiceModel.Channels.TcpTransportBindingElement> 的 <xref:System.ServiceModel.Channels.CustomBinding>。|