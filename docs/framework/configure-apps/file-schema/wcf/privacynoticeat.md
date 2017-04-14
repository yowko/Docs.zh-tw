---
title: "&lt;privacyNoticeAt&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &lt;privacyNoticeAt&gt;
表示組態項目，指定用於 `wsFederationHttp` 繫結中的隱私權注意事項。  
  
## 語法  
  
```  
  
<privacyNotice url="String"  
        version="Integer" />  
```  
  
## 類型  
 `Type`  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`url`|指定隱私權注意事項所在之 URI 的字串。|  
|`version`|指定這個隱私權注意事項版本的整數。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<繫結\>](../../../../../docs/framework/misc/binding.md)|定義自訂繫結的所有繫結功能。|  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>   
 <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 [繫結](../../../../../docs/framework/wcf/bindings.md)   
 [擴充繫結](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [自訂繫結](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)