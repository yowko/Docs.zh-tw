---
title: "&lt;filterTable&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# &lt;filterTable&gt;
代表路由表，其中包含篩選條件的清單，當篩選條件評估為 true 時，可用於評估訊息及訊息的路由目標用戶端端點。  
  
## 語法  
  
```vb  
  
<routing>  
      <filterTables>  
        <filterTable name="String">  
          <entries>  
            <add backupList=”String”  
                 endpointName="String"   
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
  
|項目|描述|  
|--------|--------|  
|name|字串，包含這個組態項目的唯一名稱。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<篩選條件\>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|當篩選條件相符時，路由篩選器與訊息傳送目標端點之間的對應。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<傳送\>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|包含路由表的組態區段。|  
  
## 請參閱  
 [System.ServiceModel.Routing.Configuration.RoutingSection](assetId:///System.ServiceModel.Routing.Configuration.RoutingSection?qualifyHint=False&amp;autoUpgrade=True)