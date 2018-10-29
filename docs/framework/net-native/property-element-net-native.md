---
title: '&lt;Property&gt; 項目 (.NET Native)'
ms.date: 03/30/2017
ms.assetid: ad4ba56d-3bcb-4c10-ba90-1cc66e2175a1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b4541bc5a878739c17179576739fbe33384445d
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2018
ms.locfileid: "50205202"
---
# <a name="ltpropertygt-element-net-native"></a>&lt;Property&gt; 項目 (.NET Native)
將執行階段反映原則套用至屬性。  
  
## <a name="syntax"></a>語法  
  
```xml  
<Property Name="property_name"  
          Browse="policy_type"  
          Dynamic="policy_type"  
          Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|屬性類型|描述|  
|---------------|--------------------|-----------------|  
|`Name`|一般|必要屬性。 指定屬性名稱。|  
|`Browse`|反射|選擇性屬性。 控制對屬性相關資訊的查詢，或控制屬性的列舉，但不會在執行階段啟用任何動態存取。|  
|`Dynamic`|反射|選擇性屬性。 控制對屬性的執行階段存取權，以啟用動態程式設計。 此原則可確保能夠在執行階段動態設定或擷取屬性。|  
|`Serialize`|序列化|選擇性屬性。 控制對屬性的執行階段存取權，使類型執行個體能夠由 Newtonsoft JSON 序列化程式之類的程式庫來序列化，或是用於資料繫結。|  
  
## <a name="name-attribute"></a>Name 屬性  
  
|值|描述|  
|-----------|-----------------|  
|*method_name*|屬性名稱。 屬性的類型是由父 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 或 [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 項目所定義。|  
  
## <a name="all-other-attributes"></a>所有其他屬性  
  
|值|描述|  
|-----------|-----------------|  
|*policy_setting*|要為屬性套用此原則類型的設定。 可能的值為 `Auto`、`Excluded`、`Included` 和 `Required`。 如需詳細資訊，請參閱[執行階段指示詞原則設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|將反映原則套用至類型及其所有成員。|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|將反映原則套用至已建構的泛型類型及其所有成員。|  
  
## <a name="remarks"></a>備註  
 如果未明確定義屬性的原則，則會繼承其父元素的執行階段原則。  
  
## <a name="example"></a>範例  
 下列範例會使用反映來具現化 `Book` 物件，並顯示其屬性值。 專案的原始 default.rd.xml 檔案會像下面這樣：  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Namespace Name="LibraryApplications"  Browse="Required Public" >  
         <Type Name="Book"   Activate="All" />  
      </Namespace>  
   </Application>  
</Directives>  
```  
  
 檔案會針對 `All` 類別，將 `Activate` 值套用至 `Book` 原則，如此可允許透過反映來存取類別建構函式。 `Browse` 類別的 `Book` 原則繼承自其父命名空間。 其設定為 `Required Public`，讓中繼資料在執行階段可供使用。  
  
 以下是範例的原始程式碼。 `outputBlock`變數代表<xref:Windows.UI.Xaml.Controls.TextBlock>控制項。  
  
 [!code-csharp[ProjectN_Reflection#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/property1.cs#6)]  
  
 不過，編譯和執行此範例會擲回 [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) 例外狀況。 雖然我們已經讓 `Book` 類型的中繼資料可供使用，但我們無法讓屬性 getter 的實作供動態使用。 我們可以用下列兩種方法之一來更正這個錯誤：  
  
-   在 `Book` 類型的 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 項目中定義其 `Dynamic` 原則。  
  
-   針對我們要叫用其 getter 的每個屬性，新增巢狀 [\<Property>](../../../docs/framework/net-native/property-element-net-native.md) 項目，如下列 default.rd.xml 檔案所示。  
  
    ```xml  
    <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
       <Application>  
          <Namespace Name="LibraryApplications"  Browse="Required Public" >  
             <Type Name="Book"   Activate="All" >  
                <Property Name="Title" Dynamic="Required" />  
                <Property Name="Author" Dynamic="Required" />  
                  <Property Name="ISBN" Dynamic="Required" />  
             </Type>  
          </Namespace>  
       </Application>  
    </Directives>  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [執行階段指示詞 (rd.xml) 組態檔參考](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [執行階段指示詞項目](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [執行階段指示詞原則設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
