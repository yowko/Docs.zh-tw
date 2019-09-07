---
title: <routing>
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: fcf2d4eec93fd7127c6f800e1c739ad1fac49203
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399966"
---
# <a name="routing"></a>\<路由 >

表示定義一組路由篩選的設定區段，其決定在評估傳入訊息時所使用的 Windows Communication Foundation <xref:System.ServiceModel.Dispatcher.MessageFilter> （WCF）類型，以及將目標端點定義為的路由表。當篩選準則相符時，將訊息傳送至。

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<路由 >**
  
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
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>屬性和元素

下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

無

### <a name="child-elements"></a>子元素

|     | 說明 |
| --- | ----------- |
| [ **\<filters>** ](filters-of-routing.md) | 包含一組路由篩選準則，決定在評估傳入訊息時，會使用 Windows Communication Foundation （WCF） MessageFilter 的類型。 |
| [ **\<filterTables>** ](filtertables.md) | 包含路由篩選條件與目標端點之間的對應，可指定當篩選條件符合時所使用的端點。 |

### <a name="parent-elements"></a>父元素

|     | 描述 |
| --- | ----------- |
| **\<system.ServiceModel>** | 所有 WCF 組態項目的根項目。 |

## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
