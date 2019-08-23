---
title: <add> 項目的 <declaredTypes>
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
ms.openlocfilehash: 1ea008dcc72d555b00e9648ace95bb9522ffc2c8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920179"
---
# <a name="add-of-declaredtypes-element"></a>\<新增 declaredTypes > \<元素的 >
在還原序列化期間，新增 <xref:System.Runtime.Serialization.DataContractSerializer> 所使用的型別。 每個宣告的型別都包含已知型別，這些已知型別將傳回做為宣告型別的欄位或屬性。  
  
 system.runtime.serialization  
\<dataContractSerializer>  
\<declaredTypes>  
\<新增 declaredTypes > \<的 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<add type="String">
  <knownType type="String">
    <parameter index="Integer"
               type="String" />
  </knownType>
</add>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|型別|必要的字串屬性。<br /><br /> 指定型別名稱 (包括命名空間)、組件名稱、版本號碼、文化特性和公開金鑰權杖。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<knownType>](knowntype.md)|為要加入的宣告型別指定已知型別。 如果宣告的型別是泛型型別，您也必須將參數項目加入至 `<knownType>` 項目，以指定要用於傳回已知型別的泛型參數。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<declaredTypes>](declaredtypes.md)|包含還原序列化期間 <xref:System.Runtime.Serialization.DataContractSerializer> 所需已知型別的型別。|  
  
## <a name="remarks"></a>備註  
 如需已知類型的詳細資訊, 請參閱[資料合約已知類型](../../../wcf/feature-details/data-contract-known-types.md)和<xref:System.Runtime.Serialization.DataContractSerializer>。  
  
 如需使用此元素的範例, 請參閱[ dataContractSerializer>。\< ](datacontractserializer-element.md)  
  
> [!NOTE]
> 如果您將 <xref:System.Object> 型別加入做為 `<declaredType>`，則會擲回 <xref:System.Configuration.ConfigurationErrorsException>。 這是因為 <xref:System.Object> 型別無法用來做為組態中的宣告型別。  
  
## <a name="example"></a>範例  
  
```xml  
<add type="MyCompany.Library.Shape,
           MyAssembly, Version=2.0.0.0, Culture=neutral,
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">
  <knownType type="MyCompany.Library.Circle,
                   MyAssembly, Version=2.0.0.0, Culture=neutral,
                   PublicKeyToken=XXXXXX,
                   processorArchitecture=MSIL" />
</add>
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [資料合約已知類型](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [\<新增 declaredTypes > \<的 >](add-of-declaredtypes-element.md)
