---
title: "&lt;protocolMapping&gt; 的 &lt;add&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# &lt;protocolMapping&gt; 的 &lt;add&gt;
代表傳輸通訊協定配置 \(例如 http、net.tcp、net.pipe 等\) 與 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 繫結之間的預設通訊協定對應。  在執行階段建立預設的端點時，[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 會查看所設定的對應，並且決定要用於特定基礎位址的繫結。  
  
## 語法  
  
```vb  
  
<protocolMapping>  
    <add binding="String”  
         bindingConfiguration="String”  
         scheme="http/net.msmq/net.pipe/net.tcp"/>  
</protocolMapping>  
  
```  
  
```csharp  
  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|項目|描述|  
|--------|--------|  
|繫結|指定在建立預設端點期間用於端點之繫結類型的字串。|  
|bindingConfiguration|指定要參考之繫結組態區段名稱的字串。|  
|scheme|要用於預設端點的傳輸通訊協定配置。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<protocolMapping\>](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|代表組態區段，該區段用於定義傳輸通訊協定配置 \(例如 http、net.tcp、net.pipe 等\) 和 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 繫結之間的預設通訊協定對應。|  
  
## 範例  
 下列組態範例示範 machine.config 檔案中的預設通訊協定對應。  您可以透過修改 machine.config 檔案，在電腦層級覆寫這個預設對應。  或者，如果您只想在應用程式範圍內覆寫該預設對應，也可以覆寫應用程式組態檔中的這個區段，並且變更個別通訊協定配置的對應。  
  
```  
  
<protocolMapping>  
        <add scheme="http" binding="basicHttpBinding"/>  
        <add scheme="net.tcp" binding="netTcpBinding"/>  
        <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
        <add scheme="net.msmq" binding="netMsmqBinding"/>  
</protocolMapping>  
  
```  
  
## 請參閱  
 [System.ServiceModel.Configuration.ProtocolMappingSection](assetId:///System.ServiceModel.Configuration.ProtocolMappingSection?qualifyHint=False&amp;autoUpgrade=True)   
 [System.ServiceModel.Configuration.ProtocolMappingElement](assetId:///System.ServiceModel.Configuration.ProtocolMappingElement?qualifyHint=False&amp;autoUpgrade=True)