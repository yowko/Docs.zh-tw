---
title: "&lt;namespaceTable&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# &lt;namespaceTable&gt;
代表定義一組項目的組態區段，其中包含前置詞對應的命名空間，這些對應稍後可在 XPath 篩選條件中用於路由。  
  
## 語法  
  
```vb  
  
<routing>  
   <namespaceTable>  
     <add namespace="String" prefix="String" />   
   </namespaceTable>  
</routing>  
  
```  
  
```csharp  
  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<篩選\>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)|定義用於 XPath 運算式的命名空間前置詞對應。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<傳送\>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|代表定義一組路由篩選條件的組態區段，這些篩選條件會判斷傳入訊息時所用之 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> 的型別及路由表 \(定義當篩選條件相符時的訊息傳送目標端點\)。|  
  
## 請參閱  
 [System.ServiceModel.Routing.Configuration.NamespaceElementCollection](assetId:///System.ServiceModel.Routing.Configuration.NamespaceElementCollection?qualifyHint=False&amp;autoUpgrade=True)