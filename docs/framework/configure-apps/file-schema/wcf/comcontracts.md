---
title: "&lt;comContracts&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# &lt;comContracts&gt;
`comContracts` 組態區段包含的項目可讓您指定 COM\+ 整合服務合約的各種屬性。  
  
## 指定命名空間和合約  
 COM\+ 整合服務合約目前限制在 “http:\/\/tempuri.org” 命名空間，而合約名稱是衍生自支援的 COM 介面。  然而，您可以使用組態檔中的 `comContracts` 區段來指定替代項目。  
  
 例如，您可以使用下列組態來指定服務合約的命名空間和合約名稱，以及指定選項來強制工作階段繫結上的使用。  
  
```  
<comContracts>  
  <comContract  
      contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"  
      namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"  
      name="_Broker"  
      requireSession="true">  
  </comContract>  
</comContracts>  
```  
  
 當服務初始化時，指定的命名空間和合約名稱就會套用至所產生的服務描述。  
  
 當這個區段是空白時，服務初始化會套用取自支援的 COM 介面 ID 的預設命名空間和合約名稱。  
  
 此外，您可以使用 [\<exposedMethod\>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) 項目來指定 COM\+ 方法，這些方法會在 COM\+ 元件上的介面公開為 Web 服務時公開。  您也可以使用 [\<persistableTypes\>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)，指定整合中使用的永久性型別。  最後，您可以使用 [\<userDefinedType\>](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md) 項目來包含要納入服務合約中的使用者定義型別 \(UDT\)。  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>   
 <xref:System.ServiceModel.Configuration.ComContractElement>   
 [\<exposedMethod\>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md)   
 [\<persistableTypes\>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)   
 [\<userDefinedType\>](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md)   
 [\<comContract\>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontract.md)   
 [整合 COM\+ 應用程式](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)   
 [HOW TO：設定 COM\+ 服務設定](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)