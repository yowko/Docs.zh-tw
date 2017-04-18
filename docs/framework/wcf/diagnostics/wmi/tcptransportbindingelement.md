---
title: "TcpTransportBindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# TcpTransportBindingElement
TcpTransportBindingElement  
  
## 語法  
  
```  
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## 方法  
 TcpTransportBindingElement 類別並未定義任何方法。  
  
## 屬性  
 TcpTransportBindingElement 類別具有下列屬性：  
  
### ConnectionPoolSettings  
 資料型別：TcpConnectionPoolSettings  
  
 存取類型：唯讀  
  
 連線集區設定。  
  
### ListenBacklog  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 可以擱置之佇列連線要求的最大數目。  
  
### PortSharingEnabled  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 布林值，這個值指定是否為此連線啟用 TCP 連接埠共用。  
  
### TeredoEnabled  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 布林值，指定是否啟用 Teredo \(對防火牆後的用戶端進行定址的技術\)。  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|命名空間|於 root\\ServiceModel 中定義|  
  
## 請參閱  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>