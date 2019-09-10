---
title: <filters> 的 <routing>
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: c9bc3a2c379e14d8cf687676a3ec40702d150e1e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855244"
---
# <a name="filters-of-routing"></a>\<> 路由 > \<的篩選準則

表示定義一組路由篩選的設定區段，其決定在評估傳入訊息時所使用的 Windows Communication Foundation <xref:System.ServiceModel.Dispatcher.MessageFilter> （WCF）類型。

[ **\<system.serviceModel>** ](system-servicemodel.md)\
&nbsp;&nbsp;[ **\<routing>** ](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<filters>**  
  
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
| [ **\<filter>** ](filter.md) | 包含路由篩選準則，決定在評估傳入訊息時，將<xref:System.ServiceModel.Dispatcher.MessageFilter>使用的 Windows Communication Foundation 類型（WCF）。 |

### <a name="parent-elements"></a>父元素

|     | 說明 |
| --- | ----------- |
| [ **\<routing>** ](routing.md) | 表示定義一組路由篩選的設定區段，其決定在評估傳入訊息時所使用的 Windows Communication Foundation<xref:System.ServiceModel.Dispatcher.MessageFilter> （WCF）類型，以及將目標端點定義為的路由表。當篩選準則相符時，將訊息傳送至。 |

## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
