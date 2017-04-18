---
title: "&lt;backupList&gt; 的 &lt;add&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# &lt;backupList&gt; 的 &lt;add&gt;
表示定義備份端點項目的組態項目。  
  
## 語法  
  
```vb  
  
<routing>  
  <backupLists>  
    <backupList name="String">  
      <add endpointName="String" />  
    </backupList>    
  </backupLists>  
</routing>  
  
```  
  
```csharp  
  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|name|指定備份端點名稱的字串。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<傳送\>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|包含端點清單，這些端點是您希望路由服務在無法連上主要端點時使用的端點。|  
  
## 請參閱  
 [System.ServiceModel.Routing.Configuration.BackupEndpointElement](assetId:///System.ServiceModel.Routing.Configuration.BackupEndpointElement?qualifyHint=False&amp;autoUpgrade=True)