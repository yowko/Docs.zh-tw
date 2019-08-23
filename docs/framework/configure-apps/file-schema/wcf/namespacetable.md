---
title: <namespaceTable>
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: 0316e983446644671ead2f8f843dc91b493b29c9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933162"
---
# <a name="namespacetable"></a>\<namespaceTable>

代表定義一組項目的組態區段，其中包含前置詞對應的命名空間，這些對應稍後可在 XPath 篩選條件中用於路由。

**\<system.serviceModel>**    
&nbsp;&nbsp; **\<routing>**    
&nbsp;&nbsp;&nbsp;&nbsp; **\<namespaceTable>**
  
## <a name="syntax"></a>語法  
  
```xml  
<system.serviceModel>
  <routing>
    <namespaceTable>
      <add namespace="String"
           prefix="String" />
    </namespaceTable>
  </routing>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>屬性和元素

下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

None

### <a name="child-elements"></a>子元素

|     | 描述 |
| --- | ----------- |
| [ **\<filter>** ](filter.md) | 定義用於 XPath 運算式的命名空間前置詞對應。 |

### <a name="parent-elements"></a>父元素

|     | 描述 |
| --- | ----------- |
| [ **\<routing>** ](routing.md) | 表示定義一組路由篩選的設定區段, 其決定在評估傳入訊息時所使用的 Windows Communication Foundation<xref:System.ServiceModel.Dispatcher.MessageFilter> (WCF) 類型, 以及將目標端點定義為的路由表。當篩選準則相符時, 將訊息傳送至。 |

## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
