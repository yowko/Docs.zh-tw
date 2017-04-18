---
title: "&lt;backupLists&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# &lt;backupLists&gt;
代表組態區段，用於定義錯誤處理中使用的一組備份服務。  每個子項目都是一個備份清單，該清單會列舉一組您要路由服務在無法找到主要端點時使用的端點。如果清單中的第一個端點故障，路由服務會自動容錯移轉至清單中的下一個端點。這樣您就可以快速地為應用程式加入可靠性，不需指導用戶端應用程式如何處理複雜的模式或所有服務部署的位置。  
  
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
 無。  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<篩選\>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)|包含端點清單，這些端點是您希望路由服務在無法找到主要端點時使用的端點。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<傳送\>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|代表定義一組路由篩選條件的組態區段，這些篩選條件會判斷傳入訊息時所用之 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> 的型別及路由表 \(定義當篩選條件相符時的訊息傳送目標端點\)。|  
  
## 請參閱  
 [System.ServiceModel.Routing.Configuration.BackupListCollection](assetId:///System.ServiceModel.Routing.Configuration.BackupListCollection?qualifyHint=False&amp;autoUpgrade=True)