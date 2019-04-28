---
title: <Library> 項目 (.NET Native)
ms.date: 03/30/2017
ms.assetid: f642276b-33fb-4a81-b882-8808c31ba69e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eda4f8d3819af05b022e0633d6883cca940f67e5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61866849"
---
# <a name="library-element-net-native"></a>\<文件庫 > 項目 (.NET Native)
定義包含類型和類型成員的組件，這些類型和類型成員的中繼資料可在執行階段用於反映。  
  
 \<Directives> 項目  
\<Library> 項目  
  
## <a name="syntax"></a>語法  
  
```xml  
<Library Name="assembly_name" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`Name`|必要屬性。 指定組件的名稱。 這個 `<Library>` 項目的子項目可針對這個組件中找到的類型和類型成員，定義其執行階段反映原則。|  
  
## <a name="name-attribute"></a>Name 屬性  
  
|值|描述|  
|-----------|-----------------|  
|*assembly_name*|組件的簡單名稱，不包含其副檔名。 這個屬性 (Attribute) 會對應至 <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> 屬性 (Property)。 例如，名為 Extensions.dll 之組件的名稱是 "Extensions"。 如需支援從組件條件式包含中繼資料之 *assembly_name* 的特殊格式，請參閱＜備註＞一節。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md)|將原則套用至特定組件中的所有類型。|  
|[\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)|將原則套用至特定命名空間中的所有類型。|  
|[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|將原則套用至特定類型，例如類別或結構。|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|將原則套用至建構的泛型類型。 例如，[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 項目可用來定義 `List<String>` 類型的原則。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<Directives>](../../../docs/framework/net-native/directives-element-net-native.md)|執行階段指示詞檔案的根項目。|  
  
## <a name="remarks"></a>備註  
 [\<Directives>](../../../docs/framework/net-native/directives-element-net-native.md) 項目可包含零、一或多個 `<Library>` 元素。  
  
 `<Library>` 項目可當做容器來使用，以定義在執行階段需要中繼資料的程式項目；這個項目不會表示原則。 在編譯時期，編譯器工具只會在 `<Library>` 項目所指定的程式庫中，搜尋其子項目所識別的程式項目。 在其他情況下，編譯器工具會在所有程式庫 (包含 .NET Framework 核心程式庫) 中，搜尋 [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) 項目的子項目所識別的程式項目。  
  
 您可以有條件地利用 `<Library>` 指示詞。 如果名稱`<Library>`項目開頭和結尾為星號 (\*)，則`<Library>`指示詞在應用程式參考星號之間指定的組件時，才有作用。 例如，只有在應用程式參考 Utillities.dll 組件時，下列執行階段指示詞才適用。  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Library Name="*Utilities*">  
   ...  
  </Library>  
</Directives>  
```  
  
## <a name="see-also"></a>另請參閱

- [\<應用程式 > 項目](../../../docs/framework/net-native/application-element-net-native.md)
- [\<指示詞 > 項目](../../../docs/framework/net-native/directives-element-net-native.md)
- [執行階段指示詞 (rd.xml) 組態檔參考](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [執行階段指示詞項目](../../../docs/framework/net-native/runtime-directive-elements.md)
