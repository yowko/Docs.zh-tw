---
title: "&lt;bindingElementExtensions&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bb597fc0-c947-451c-afda-bf23d42f4f4d
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# &lt;bindingElementExtensions&gt;
這個區段會啟用電腦或應用程式組態檔中自訂繫結項目的使用。  您可以透過使用 `add` 關鍵字，將項目的 `type` 屬性設定為繫結項目延伸，以及將 `name` 屬性設定為自訂繫結項目，來將自訂繫結項目加入至這個集合。  
  
 繫結延伸可讓使用者建立使用者定義的繫結項目，做為自訂繫結的一部分。  就程式設計角度而言，繫結延伸是實作抽象類別 \(Abstract Class\) <xref:System.ServiceModel.Channels.BindingElement> 的型別。  在組態檔中，`bindingElementExtensions` 區段是用於定義延伸項目。  
  
 下列範例使用 `add` 項目，以及 `name` 屬性，將繫結延伸加入至組態檔的 `bindingElementExtensions` 區段中。  
  
```  
<system.serviceModel>  
    <extensions>  
        <bindingElementExtensions>  
           <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportSection, UdpTransport,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </bindingElementExtensions>  
    </extensions>  
</system.serviceModel>  
```  
  
 若要將組態功能加入至項目，使用者必須寫入並註冊 `bindingElementExtensionSection` 項目。  如需這方面的詳細資訊，請參閱 <xref:System.Configuration>。  
  
 在定義項目及其組態型別後，延伸即可做為自訂繫結的一部分，如下列範例所示。  
  
```  
<customBinding>  
     <binding name="test2">  
         <udpTransport />  
         <binaryMessageEncoding maxReadPoolSize="211" maxWritePoolSize="2132"  
             maxSessionSize="3141" />  
         </binding>  
</customBinding>  
```  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>   
 [擴充繫結](../../../../../docs/framework/wcf/extending/extending-bindings.md)