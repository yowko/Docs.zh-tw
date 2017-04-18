---
title: "設定用戶端行為 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: df5b32fa-e73b-4e8e-b66f-357c748e0173
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# 設定用戶端行為
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 會以兩種方式設定行為：一種是參考行為組態 \(定義於用戶端應用程式組態檔的 `<behavior>` 區段中\)，另一種是透過呼叫應用程式，以程式設計的方式設定。  這個主題將描述這兩種方法。  
  
 使用組態檔時，行為組態都是具名的組態設定集合。  每個行為組態的名稱必須是獨一無二的。  會在端點組態的 `behaviorConfiguration` 屬性中使用這個字串，以便將端點連結至行為。  
  
## 範例  
 下列組態程式碼會定義名稱為 `myBehavior` 的行為。  用戶端端點會參考 `behaviorConfiguration` 屬性中的這個行為。  
  
```  
<configuration>  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="myBehavior">  
                    <clientVia />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
        <bindings>  
            <basicHttpBinding>  
                <binding name="myBinding" maxReceivedMessageSize="10000" />  
            </basicHttpBinding>  
        </bindings>  
        <client>  
            <endpoint address="myAddress" binding="basicHttpBinding" bindingConfiguration="myBinding" behaviorConfiguration="myBehavior" contract="myContract" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
## 以程式設計方式使用行為  
 您也可以用程式設計的方式來設定或插入行為，方法是在開啟用戶端之前，在 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 用戶端物件上或用戶端通道物件處理站上尋找適當的 `Behaviors` 屬性。  
  
## 範例  
 下列程式碼範例會示範如何以程式設計的方式插入行為，其方法是先存取傳回自 <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> 屬性之 <xref:System.ServiceModel.Description.ServiceEndpoint> 上的 <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> 屬性，再建立通道物件。  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## 請參閱  
 [\<行為\>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)