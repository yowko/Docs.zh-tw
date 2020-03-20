---
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: c93a1f482882cc8cd9d229d82597efa64ba209bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152966"
---
# <a name="systemruntimeserialization"></a>\<系統.運行時.序列化>
代表 <xref:System.Runtime.Serialization> 命名空間區段的根項目，而且包含用來設定 <xref:System.Runtime.Serialization.DataContractSerializer> 選項的項目。  

[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;**\<系統.運行時.序列化>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer ignoreExtensionDataObject="Boolean"
                            maxItemsInObjectGraph="Integer">
      <declaredTypes>
        <add type="String">
          <knownType type="String">
            <parameter index="Integer" />
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<資料合同序列化器>](datacontractserializer-of-system-runtime-serialization.md)|能夠在還原序列化時，加入要使用的已知型別。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<配置>元素](../configuration-element.md)|組態的最上層項目。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.Serialization>
- [使用資料合約](../../../wcf/feature-details/using-data-contracts.md)
- [資料合約已知型別](../../../wcf/feature-details/data-contract-known-types.md)
