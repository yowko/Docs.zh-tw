---
title: <parameter>
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: c3f2179835ad1232e115cad0decdd3d41bbdc160
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932839"
---
# <a name="parameter"></a>\<parameter>
指定當宣告型別為泛型型別時的泛型參數。  
  
 \<system.runtime.serialization>  
\<dataContractSerializer>  
\<declaredTypes > 元素  
\<新增 declaredTypes > 的\<> 元素  
\<knownType > 元素  
\<參數 > 元素  
  
## <a name="syntax"></a>語法  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|索引|當宣告型別為泛型型別時，會指定將傳回已知型別的泛型參數。|  
|型別|字串，說明用來序列化和還原序列化的已知型別。|  
  
## <a name="index-attribute"></a>index 屬性  
  
|值|描述|  
|-----------|-----------------|  
|"0"|泛型型別中的第一個參數。 例如，<xref:System.Collections.Generic.List%601> 只有一個參數。 如果將它當做宣告型別，則 index 會設定為 "0"。|  
|"1"|泛型型別中的第二個參數。 例如，<xref:System.Collections.Generic.Dictionary%602> 有兩個參數。 如果已知型別是由第二個參數傳回的，請將 index 屬性設定為 "1"。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<knownType>](knowntype.md)|指定可由宣告型別的欄位或屬性傳回的已知型別。|  
  
## <a name="remarks"></a>備註  
 如需已知類型的詳細資訊, 請參閱[資料合約已知類型](../../../wcf/feature-details/data-contract-known-types.md)和<xref:System.Runtime.Serialization.DataContractSerializer>。  
  
 如需使用此元素的範例, 請參閱[ dataContractSerializer>。\< ](datacontractserializer-element.md)  
  
 此組態項目不可以同時具有這兩個屬性。 如果同時設定了這兩個屬性，就會發生 <xref:System.Configuration.ConfigurationErrorsException>。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [資料合約已知類型](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [\<add>](add-of-declaredtypes-element.md)
