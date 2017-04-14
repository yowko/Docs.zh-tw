---
title: "&lt;namedPipeTransport&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# &lt;namedPipeTransport&gt;
定義傳輸，這個傳輸會使通道在包含於自訂繫結時使用具名管道來傳輸訊息。  
  
## 語法  
  
```  
  
<namedPipeTransport>  
      <connectionPoolSettings  
         groupName=”String”  
          idleTimeout"TimeSpan"  
        maxOutboundConnectionsPerEndpopint=”Integer” />  
</namedPipeTransport>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<namedPipeTransport\> 的 \<connectionPoolSettings\>](../../../../../docs/framework/configure-apps/file-schema/wcf/connectionpoolsettings.md)|為具名管道繫結指定其他連線集區設定。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<繫結\>](../../../../../docs/framework/misc/binding.md)|定義自訂繫結的所有繫結功能。|  
  
## 備註  
 這個傳輸會使用以下格式的 URI "net.pipe:\/\/hostname\/path"。  其他 URI 元件是選擇性的。  
  
 `namedPipeTransport` 項目建立自訂繫結時的起點，此繫結會實作具名管道傳輸通訊協定。  這個傳輸是用於電腦的 Windows Communication Foundation \(WCF\) 至 WCF 通訊。  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>   
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>   
 <xref:System.ServiceModel.Channels.TransportBindingElement>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 [傳輸](../../../../../docs/framework/wcf/feature-details/transports.md)   
 [選擇傳輸](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)   
 [繫結](../../../../../docs/framework/wcf/bindings.md)   
 [擴充繫結](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [自訂繫結](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)