---
title: '&lt;namespaceTable&gt;'
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: 55b5565ffe9d3e9e7ea41d2a2e2f380490be1781
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151419"
---
# <a name="ltnamespacetablegt"></a>&lt;namespaceTable&gt;

代表定義一組項目的組態區段，其中包含前置詞對應的命名空間，這些對應稍後可在 XPath 篩選條件中用於路由。

**\<system.serviceModel >**   
&nbsp;&nbsp;**\<路由 >**   
&nbsp;&nbsp;&nbsp;&nbsp;**\<a d d >**
  
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

無

### <a name="child-elements"></a>子元素

|     | 描述 |
| --- | ----------- |
| [**\<篩選條件 >**](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | 定義用於 XPath 運算式的命名空間前置詞對應。 |

### <a name="parent-elements"></a>父元素

|     | 描述 |
| --- | ----------- |
| [**\<路由 >**](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | 代表定義一組路由篩選條件，判斷類型的 Windows Communication Foundation (WCF) 的組態區段<xref:System.ServiceModel.Dispatcher.MessageFilter>評估內送訊息，以及路由資料表定義目標端點時要使用將訊息傳送至篩選條件的比對。 |

## <a name="see-also"></a>另請參閱

<xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
