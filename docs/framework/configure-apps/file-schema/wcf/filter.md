---
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: 6e78275aaeb202405e327302455d56fa431d7f27
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855254"
---
# \<filter>

定義路由篩選，這會決定在評估傳入訊息時所使用的 Windows Communication Foundation （WCF）類型 <xref:System.ServiceModel.Dispatcher.MessageFilter> ，以及篩選準則所需的任何支援資料或參數。

[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<filters>**](filters-of-routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**  
  
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
| customType | 字串，其中包含要做為篩選之自訂類型的完整類型名稱。 如果 `filterType` 設定為 `custom` ，這個屬性就會包含要建立之類別的完整型別名稱。  `filterData`也可以包含評估自訂型別篩選準則期間要使用的值。 |
| filterData | 包含篩選資料的字串。 如需如何指定這個屬性的詳細資訊，請參閱 <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>。 |
| filterType | 包含篩選條件類型的字串。 此屬性的型別為 <xref:System.ServiceModel.Routing.Configuration.FilterType>。  如需此屬性與 `filterData` 屬性如何搭配運作的詳細資訊，請參閱 <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>。 |
| NAME       | 字串，其中包含這個篩選項目的唯一名稱。 |

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

| 元素 | 描述 |
| ------- | ----------- |
| [\<routing>](routing.md) | 定義一組路由篩選的設定區段，可決定在 <xref:System.ServiceModel.Dispatcher.MessageFilter> 評估傳入訊息時所使用的 Windows Communication Foundation （WCF）類型。 |

## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>
