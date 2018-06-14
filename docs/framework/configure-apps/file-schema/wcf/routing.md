---
title: '&lt;路由&gt;'
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: 1771d8a2603a8f61af6ba6e2acf6243d2fd073f7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747718"
---
# <a name="ltroutinggt"></a>&lt;路由&gt;

代表定義一組路由篩選條件，判斷類型的 Windows Communication Foundation (WCF) 的組態區段<xref:System.ServiceModel.Dispatcher.MessageFilter>傳入訊息及路由表定義目標端點時所要使用當篩選條件相符時傳送訊息。

[**\<system.serviceModel >**](system-servicemodel.md)   
&nbsp;&nbsp;**\<路由 >**

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
| [**\<篩選條件 >**](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md) | 包含一組路由篩選條件，以決定評估內送訊息時，就會使用 Windows Communication Foundation (WCF) MessageFilter 的型別。 |
| [**\<filterTables >**](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) | 包含路由篩選條件與目標端點之間的對應，可指定當篩選條件符合時所使用的端點。 |

### <a name="parent-elements"></a>父元素

|     | 描述 |
| --- | ----------- |
| **\<系統。ServiceModel >** | 所有 WCF 組態項目的根項目。 |

## <a name="see-also"></a>另請參閱

<xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
