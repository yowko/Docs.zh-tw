---
title: <routing>
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: fcf2d4eec93fd7127c6f800e1c739ad1fac49203
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399966"
---
# \<routing>

表示定義一組路由篩選的設定區段，其會決定在評估傳入訊息時所使用的 Windows Communication Foundation （WCF）類型 <xref:System.ServiceModel.Dispatcher.MessageFilter> ，以及定義當篩選準則符合時，要傳送訊息的目標端點的路由表。

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<routing>**
  
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

|     | 描述 |
| --- | ----------- |
| [**\<filters>**](filters-of-routing.md) | 包含一組路由篩選準則，決定在評估傳入訊息時，會使用 Windows Communication Foundation （WCF） MessageFilter 的類型。 |
| [**\<filterTables>**](filtertables.md) | 包含路由篩選條件與目標端點之間的對應，可指定當篩選條件符合時所使用的端點。 |

### <a name="parent-elements"></a>父元素

|     | 描述 |
| --- | ----------- |
| **\<system.ServiceModel>** | 所有 WCF 組態項目的根項目。 |

## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
