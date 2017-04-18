---
title: "&lt;篩選&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# &lt;篩選&gt;
定義路由篩選條件，可判斷傳入訊息時要使用之 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> 的型別，以及篩選條件所需的任何支援資料或參數。  
  
## 語法  
  
```vb  
  
<routing>  
      <filters>  
        <filter customType=”String”  
                filterData=”String”  
                filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"   
                name="String" />  
      </filters>  
</routing>  
  
```  
  
```csharp  
  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|customType|字串，其中包含要做為篩選條件之自訂型別的完整型別名稱。如果 `filterType` 設為 `custom`，這個屬性則會包含要建立之類別的完整型別名稱。`filterData` 也可包含評估自訂型別篩選條件期間要使用的值。|  
|filterData|包含篩選資料的字串。  如需如何指定這個屬性的詳細資訊，請參閱 <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>。|  
|filterType|包含篩選條件類型的字串。  此屬性的型別為 <xref:System.ServiceModel.Routing.Configuration.FilterType>。  如需此屬性與 `filterData` 屬性如何搭配運作的詳細資訊，請參閱 <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>。|  
|name|字串，其中包含這個篩選項目的唯一名稱。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<傳送\>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|組態區段，用於定義一組路由篩選條件，這些篩選條件可判斷傳入訊息時要使用之 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> 的型別。|  
  
## 請參閱  
 [System.ServiceModel.Routing.Configuration.FilterElement](assetId:///System.ServiceModel.Routing.Configuration.FilterElement?qualifyHint=False&amp;autoUpgrade=True)   
 <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>   
 <xref:System.ServiceModel.Routing.Configuration.FilterType>