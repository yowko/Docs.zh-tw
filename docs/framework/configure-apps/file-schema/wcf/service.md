---
title: "&lt;服務&gt; | Microsoft Docs"
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
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
caps.latest.revision: 27
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 27
---
# &lt;服務&gt;
`service` 項目包含 Windows Communication Foundation \(WCF\) 服務的設定。  它也包含公開服務的端點。  
  
## 語法  
  
```  
  
<service behaviorConfiguration=String"  
        name="String"  
</service>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|behaviorConfiguration|字串，其中包含要用於產生服務實體之行為的行為名稱。  行為名稱必須在定義服務之處的範圍內。  預設值為空字串。|  
|name|必要的字串屬性，其中指定要具現化的服務型別。  這個設定必須等同於有效的型別。  格式應該為 `Namespace.Class.`。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<endpoint\>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)|公開此服務之 `endpoint` 項目的集合。|  
|[\<Host \- 主應用程式\>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|指定這個服務執行個體的主機。  此項目的型別為 <xref:System.ServiceModel.Configuration.HostElement>。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<服務\>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|所有 WCF 組態項目的根項目。|  
  
## 備註  
 服務定義於組態檔的 `services` 區段中。  組件可包含任何數目的服務。  各服務都有自己的 `service` 組態區段。  這個區段及其內容會定義特定服務的服務合約、行為和端點。  
  
 `behaviorConfiguration` 項目也是選擇性。  它會定義服務使用的行為。  在這個屬性中指定的行為必須連結至相同組態檔案範圍內的行為。  
  
 每一個服務會公開一或多個端點，每個端點擁有自己的位址和繫結。  在組態檔中使用的所有繫結都必須定義在檔案的範圍內。  繫結會透過 `name` 和 `bindingConfiguration` 屬性的組合，來連結至端點。  `name` 屬性描述繫結定義所在的區段。  `bindingConfiguration` 屬性定義要使用繫結區段中的哪一個組態。  繫結區段可定義數個組態。  
  
## 範例  
 這是服務組態的範例。  
  
```  
<service behaviorConfiguration="testChannelBehavior"   
     name="HelloWorld">  
     <endpoint   
        address="/HelloWorld2/"  
        name="test"  
        bindingNamespace="http://www.cohowinery.com/"  
        binding="basicHttpBinding"  
        contract="IHelloWorld" />  
</service>  
```  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.ServiceElement>   
 [設定服務](../../../../../docs/framework/wcf/configuring-services.md)