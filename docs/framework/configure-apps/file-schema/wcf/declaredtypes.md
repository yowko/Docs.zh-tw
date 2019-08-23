---
title: <declaredTypes>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- declaredTypes element
- DataContractSerializer
- KnownTypes
- <declaredTypes> element
ms.assetid: f35184e4-9d9e-4d37-8fb4-d5b58220eb3e
ms.openlocfilehash: cef34a8836c7b17fe9a85cac190090f42653df14
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919241"
---
# <a name="declaredtypes"></a>\<declaredTypes>
包含還原序列化時，<xref:System.Runtime.Serialization.DataContractSerializer> 使用的已知型別。  
  
 如需資料合約和已知類型的詳細資訊, 請參閱[資料合約已知類型](../../../wcf/feature-details/data-contract-known-types.md)。  
  
 system.runtime.serialization  
\<dataContractSerializer>  
\<declaredTypes>  
  
## <a name="syntax"></a>語法  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer>
      <declaredTypes>
        <add type="String ">
          <knownType type="String">
            <parameter index="Integer"/>
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
 無。  
  
### <a name="child-elements"></a>子元素  
  
|項目|說明|  
|-------------|-----------------|  
|[\<add>](add-of-declaredtypes-element.md)|新增需要已知型別的型別。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-of-system-runtime-serialization.md)|包含 <xref:System.Runtime.Serialization.DataContractSerializer> 的組態資料。|  
  
## <a name="remarks"></a>備註  
 如需已知類型的詳細資訊, 請參閱[資料合約已知類型](../../../wcf/feature-details/data-contract-known-types.md)和<xref:System.Runtime.Serialization.DataContractSerializer>。  
  
## <a name="example"></a>範例  
 下列 XML 程式碼顯示新增至`DataContractSerializer`專案的宣告型別和已知型別。 此範例顯示新增了三個型別。 第一個是名為 "Orders" 的自訂型別，它將使用名為 "Item" 的已知型別。 第二個宣告型別是使用 <xref:System.Collections.Generic.List%601> 做為已知型別的 `Item`。 最後，第三個宣告型別是 <xref:System.Collections.Generic.Dictionary%602>。 <xref:System.Collections.Generic.Dictionary%602> 類別型別是有兩個型別參數的泛型型別。 第一個參數表示索引鍵，第二個參數表示值。 下列範例會將第二個型別 (值) 的 <xref:System.Collections.Generic.List%601> 新增至已知型別的清單中。 您必須使用 `index` 屬性來指定要在已知型別中使用的型別參數。 在此案例中，值型別是由索引屬性設定為 "1" 者指定 (因為集合的索引是以零起始)。  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer>
      <declaredTypes>
        <add type="Examples.Types.Orders, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />
        </add>
        <add type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />
        </add>
        <add type="System.Collections.Generic.Dictionary`2, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
          <knownType type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
            <parameter index="1"/>
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [資料合約已知類型](../../../wcf/feature-details/data-contract-known-types.md)
- [\<add>](add-of-declaredtypes-element.md)
