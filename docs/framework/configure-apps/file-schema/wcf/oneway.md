---
title: "&lt;oneWay&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# &lt;oneWay&gt;
針對自訂繫結啟用封包路由和使用單向方法。  
  
## 語法  
  
```  
  
<oneWay packetRoutable="Boolean">  
        <channelPoolSettings  
           idleTimeout"TimeSpan"  
          leaseTimeout"TimeSpan"  
          maxOutboundConnectionsPerEndpopint=”Integer” />  
```  
  
```  
  
</oneWay>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`packetRoutable`|布林值，指定是否啟用封包路由。  預設為 `false`。|  
|`MaxAcceptedChannels`|整數，指定可接受的通道數目上限。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<channelPoolSettings\>](../../../../../docs/framework/configure-apps/file-schema/wcf/channelpoolsettings.md)|<xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> 物件，包含目前通道的通道集區的屬性。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<繫結\>](../../../../../docs/framework/misc/binding.md)|定義自訂繫結的所有繫結功能。|  
  
## 備註  
 如果要啟用封包路由，便需要這個項目提供的單向轉換層。  使用者可以建立自訂繫結，將這個繫結置於工作階段感知或要求\-回覆傳輸層上，讓它啟用路由傳送封包功能。  當您要以較原始的方式來公開單向方法時，也可以使用這個項目。  還有其他轉換可套用至這一層，例如複合雙工和可信賴傳訊。  
  
## 請參閱  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>   
 <xref:System.ServiceModel.Configuration.OneWayElement>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 [繫結](../../../../../docs/framework/wcf/bindings.md)   
 [擴充繫結](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [自訂繫結](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)