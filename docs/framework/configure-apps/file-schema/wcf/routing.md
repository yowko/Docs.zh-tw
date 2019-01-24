---
title: '&lt;routing&gt;'
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: 855faedfd2e9523e939174441b0cfa50e052b375
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54565874"
---
# <a name="ltroutinggt"></a>&lt;routing&gt;

代表定義一組路由篩選條件，判斷類型的 Windows Communication Foundation (WCF) 的組態區段<xref:System.ServiceModel.Dispatcher.MessageFilter>評估內送訊息，以及路由資料表定義目標端點時要使用將訊息傳送至篩選條件的比對。

[**\<system.serviceModel>**](system-servicemodel.md)   
&nbsp;&nbsp;**\<routing>**
  
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
| [**\<filters>**](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md) | 包含一組路由篩選，以決定評估內送訊息時，就會使用 Windows Communication Foundation (WCF) MessageFilter 的型別。 |
| [**\<filterTables>**](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) | 包含路由篩選條件與目標端點之間的對應，可指定當篩選條件符合時所使用的端點。 |

### <a name="parent-elements"></a>父元素

|     | 描述 |
| --- | ----------- |
| **\<system.ServiceModel>** | 所有 WCF 組態項目的根項目。 |

## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
