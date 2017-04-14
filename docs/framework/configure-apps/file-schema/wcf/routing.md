---
title: "&lt;傳送&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# &lt;傳送&gt;
代表定義一組路由篩選條件的組態區段，這些篩選條件會判斷傳入訊息時所用之 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> 的型別及路由表 \(定義當篩選條件相符時的訊息傳送目標端點\)。  
  
## 語法  
  
```vb  
  
<routing>  
      <filters>  
        <filter customType=”String”  
                filterData=”String”  
                filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"   
                name="String" />  
      </filters>  
      <routingTables>  
        <table name="String">  
          <entries>  
            <add endpoint="String"   
                 filterName="String"   
                 priority="Integer" />  
          </entries>  
        </table>  
      </routingTables>  
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
|[\<篩選條件\>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|包含一組路由篩選條件，這些篩選條件會判斷傳入訊息時所使用之 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] MessageFilter 的類型。|  
|[\<filterTables\>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md)|包含路由篩選條件與目標端點之間的對應，可指定當篩選條件符合時所使用的端點。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|system.ServiceModel|所有 WCF 組態項目的根項目。|  
  
## 請參閱  
 [System.ServiceModel.Routing.Configuration.RoutingSection](assetId:///System.ServiceModel.Routing.Configuration.RoutingSection?qualifyHint=False&amp;autoUpgrade=True)