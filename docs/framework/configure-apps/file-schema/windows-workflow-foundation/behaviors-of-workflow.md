---
title: 工作流程的 <behaviors>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: 05a15cdf5c043eb5d94b36028324310d2b7a8413
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398882"
---
# <a name="behaviors-of-workflow"></a>\<工作流程 > 的行為
此元素包含**serviceBehaviors**集合。  集合中的每個項目都會定義工作流程服務使用的行為項目。 每個行為元素都是由其唯一的**名稱**屬性來識別。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<筆記本電腦.System.servicemodel >** ](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<行為 >**  
  
## <a name="syntax"></a>語法  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 None  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors-of-workflow.md)|這個組態區段表示為特定工作流程服務定義的所有行為。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<system.serviceModel>](../wcf/system-servicemodel.md)|所有工作流程組態項目的根項目。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [使用行為來設定與擴充執行階段](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
