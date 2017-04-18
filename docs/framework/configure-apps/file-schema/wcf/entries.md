---
title: "&lt;entries&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &lt;entries&gt;
這個路由項目會包含當篩選條件符合時，路由篩選條件與訊息傳送目標端點之間的對應。  
  
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
 無。  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<篩選條件\>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|將篩選條件對應至先前定義的用戶端端點。  將符合此篩選條件的訊息傳送至這個目的地。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<傳送\>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|包含路由表的組態區段。|  
  
## 請參閱  
 [System.ServiceModel.Routing.Configuration.RoutingSection](assetId:///System.ServiceModel.Routing.Configuration.RoutingSection?qualifyHint=False&amp;autoUpgrade=True)   
 [System.ServiceModel.Routing.Configuration.FilterTableEntryElement](assetId:///System.ServiceModel.Routing.Configuration.FilterTableEntryElement?qualifyHint=False&amp;autoUpgrade=True)