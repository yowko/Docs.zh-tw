---
title: <knownType>
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: 6bb6a419d863172951d82a67de044cb8cfc30f49
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183789"
---
# \<knownType>

指定還原序列化期間要由 <xref:System.Runtime.Serialization.DataContractSerializer> 使用的型別。 項目會指定由「宣告型別」的欄位或屬性所傳回的「已知型別」。 如需詳細資訊，請參閱 [資料合約已知類型](../../../wcf/feature-details/data-contract-known-types.md)。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-of-declaredtypes-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<knownType>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a>類型  

 `string`  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|type|指定型別 (包括命名空間)、組件名稱、版本、文化特性和公開金鑰權杖。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<parameter>](parameter.md)|指定當宣告型別為泛型型別時的參數索引。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<add>](add-of-declaredtypes-element.md)|將宣告型別新增至宣告型別集合中。|  
  
## <a name="remarks"></a>備註  

 如需已知類型的詳細資訊，請參閱 [資料合約已知](../../../wcf/feature-details/data-contract-known-types.md) 型別和 <xref:System.Runtime.Serialization.DataContractSerializer> 。  
  
 如需 [\<dataContractSerializer>](datacontractserializer-element.md) 使用這個元素的範例，請參閱。  
  
## <a name="example"></a>範例  
  
```xml  
<add type="MyCompany.Library.Shape,
           MyAssembly, Version=2.0.0.0, Culture=neutral,
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">
  <knownType type="MyCompany.Library.Circle,
                   MyAssembly, Version=2.0.0.0, Culture=neutral,
                   PublicKeyToken=XXXXXX,
                   processorArchitecture=MSIL"/>
</add>
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [資料合約已知型別](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [\<add>](add-of-declaredtypes-element.md)
