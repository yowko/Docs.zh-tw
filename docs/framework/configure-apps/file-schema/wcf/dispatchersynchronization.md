---
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: b95f25217c2a3558846cc7a0ef43e21aacd2ee2a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398007"
---
# <a name="dispatchersynchronization"></a>\<dispatcherSynchronization>
  
指定可讓服務以非同步方式傳送回覆的端點行為。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<dispatcherSynchronization >**  
  
## <a name="syntax"></a>語法  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a>類型  
  
`Type`  
  
## <a name="attributes-and-elements"></a>屬性和元素  
  
下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性

| 屬性               | 說明       |
| ----------------------- | ----------------- |
| asynchronousSendEnabled | 布林值，指定是否啟用非同步傳送行為。 |
| `maxPendingReceives`    | 整數，指定可在通道發行之並行接收的數目。<br /><br /> 唯有在您正確設定服務節流閥行為後，才可設定這個值。 |

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

| 元素 | 描述 |  
| ------- | ----------- |  
| [\<behavior>](behavior-of-endpointbehaviors.md)|指定端點行為。 |

## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
