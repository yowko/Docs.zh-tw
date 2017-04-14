---
title: "&lt;persistableType&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &lt;persistableType&gt;
指定所有永久性型別。  
  
## 語法  
  
```  
  
<comContracts>  
  <comContract>  
      <persistableTypes>  
         <persistableType id="string"  
            name="string">  
         </persistableType>  
      </persistableTypes>  
  </comContract>  
</comContracts>  
```  
  
## 類型  
 `Type`  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|id|必要屬性，其中包含的字串可指定永久性類別的唯一識別碼。|  
|name|選擇性屬性，其中包含的字串可指定永久性類別的名稱。|  
  
### 子項目  
 無  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<persistableTypes\>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)|`persistableType` 項目的集合。|  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>   
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>   
 [\<comContracts\>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)   
 [整合 COM\+ 應用程式](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)   
 [HOW TO：設定 COM\+ 服務設定](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)