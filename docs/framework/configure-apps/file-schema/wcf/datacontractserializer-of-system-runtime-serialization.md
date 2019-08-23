---
title: <dataContractSerializer>< 的 >。
ms.date: 03/30/2017
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
ms.openlocfilehash: 380d9ba5b8407d78b5045fd34fcdf37c0818d6f9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919342"
---
# <a name="datacontractserializer-of-systemruntimeserialization"></a>\<dataContractSerializer > > \<的序列化
包含 <xref:System.Runtime.Serialization.DataContractSerializer> 的組態資料。  
  
 \<system.runtime.serialization>  
\<dataContractSerializer>  
  
## <a name="syntax"></a>語法  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer ignoreExtensionDataObject="Boolean"
                            maxItemsInObjectGraph="Integer">
      <declaredTypes>
        <add type="String">
          <knownType type="String">
            <parameter index="Integer"
                       type="String" />
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|項目|描述|  
|-------------|-----------------|  
|ignoreExtensionDataObject|布林值，該值會指定當端點序列化或還原序列化時，是否略過端點所提供的資料。 此屬性只能在 `<dataContractSerializer>` 項目下的 `<behavior>` 設定。|  
|maxItemsInObjectGraph|整數，指定要序列化或還原序列化的項目數上限。 此屬性為 65536。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<declaredTypes>](declaredtypes.md)|包含還原序列化時，<xref:System.Runtime.Serialization.DataContractSerializer> 使用的已知型別。<br /><br /> 如需資料合約和已知類型的詳細資訊, 請參閱[資料合約已知類型](../../../wcf/feature-details/data-contract-known-types.md)。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<system.runtime.serialization>](system-runtime-serialization.md)|代表 <xref:System.Runtime.Serialization> 命名空間區段的根項目，而且包含用來設定 <xref:System.Runtime.Serialization.DataContractSerializer> 選項的項目。|  
  
## <a name="remarks"></a>備註  
 如需已知類型的詳細資訊, <xref:System.Runtime.Serialization.DataContractSerializer>請參閱和[資料合約已知類型](../../../wcf/feature-details/data-contract-known-types.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- [資料合約已知類型](../../../wcf/feature-details/data-contract-known-types.md)
