---
title: '&lt;篩選器&gt;'
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: f7224eab9f3c21bce9839298b50c52e9da08b6f7
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146403"
---
# <a name="ltfiltergt"></a>&lt;篩選器&gt;

定義路由篩選條件，判斷類型的 Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter>傳入訊息，也可以在任何支援的資料或篩選條件所需的參數為時使用。

\<system.serviceModel >\<路由 >\<篩選條件 >\<篩選條件 >
  
## <a name="syntax"></a>語法  
  
```xml  
<routing>
  <filters>
    <filter customType="String"
            filterData="String"
            filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"
            name="String" />
  </filters>
</routing>
```  
  
## <a name="attributes-and-elements"></a>屬性和元素

下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

| 屬性  | 描述 |
| ---------- | ----------- |
| customType | 字串，其中包含要做為篩選之自訂類型的完整類型名稱。 如果`filterType`設為`custom`，這個屬性包含要建立之類別的完整型別名稱。  `filterData` 也可包含評估自訂型別篩選條件期間要使用的值。 |
| filterData | 包含篩選資料的字串。 如需如何指定這個屬性的詳細資訊，請參閱 <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>。 |
| filterType | 包含篩選條件類型的字串。 此屬性的型別為 <xref:System.ServiceModel.Routing.Configuration.FilterType>。  如需此屬性與 `filterData` 屬性如何搭配運作的詳細資訊，請參閱 <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>。 |
| name       | 字串，其中包含這個篩選項目的唯一名稱。 |

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

| 元素 | 描述 |
| ------- | ----------- |
| [\<路由 >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | 定義一組路由篩選條件，判斷類型的 Windows Communication Foundation (WCF) 的組態區段<xref:System.ServiceModel.Dispatcher.MessageFilter>傳入訊息時使用。 |

## <a name="see-also"></a>另請參閱

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>    
<xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>   
<xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>   
