---
title: <filters> 的 <routing>
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: c9bc3a2c379e14d8cf687676a3ec40702d150e1e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855244"
---
# <a name="filters-of-routing"></a>\<filters> 的 \<routing>

表示定義一組路由篩選的設定區段，其決定在 <xref:System.ServiceModel.Dispatcher.MessageFilter> 評估傳入訊息時所使用的 Windows Communication Foundation （WCF）類型。

[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.serviceModel>
  <routing>
    <filters>
      <filter customType="String"
              filterData="String"
              filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"
              name="String" />
    </filters>
  </routing>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>屬性和元素

下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

無

### <a name="child-elements"></a>子元素

|     | 描述 |
| --- | ----------- |
| [**\<filter>**](filter.md) | 包含路由篩選準則，決定在 <xref:System.ServiceModel.Dispatcher.MessageFilter> 評估傳入訊息時，將使用的 Windows Communication Foundation 類型（WCF）。 |

### <a name="parent-elements"></a>父元素

|     | 描述 |
| --- | ----------- |
| [**\<routing>**](routing.md) | 表示定義一組路由篩選的設定區段，其會決定在評估傳入訊息時所使用的 Windows Communication Foundation （WCF）類型 <xref:System.ServiceModel.Dispatcher.MessageFilter> ，以及定義當篩選準則符合時，要傳送訊息的目標端點的路由表。 |

## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
