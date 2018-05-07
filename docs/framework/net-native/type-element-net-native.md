---
title: '&lt;Type&gt; 項目 (.NET Native)'
ms.date: 03/30/2017
ms.assetid: 1e88d368-a886-4f1e-8eb6-6127979a9fce
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad20cf4528f5ca7d23f80570cc34712d33b74d93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="lttypegt-element-net-native"></a>&lt;Type&gt; 項目 (.NET Native)
將執行階段原則套用到特定的類型，例如類別或結構。  
  
## <a name="syntax"></a>語法  
  
```xml  
<Type Name="type_name"  
      Activate="policy_type"  
      Browse="policy_type"  
      Dynamic="policy_type"  
      Serialize="policy_type"   
      DataContractSerializer="policy_setting"  
      DataContractJsonSerializer="policy_setting"  
      XmlSerializer="policy_setting"  
      MarshalObject="policy_setting"  
      MarshalDelegate="policy_setting"  
      MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|屬性類型|描述|  
|---------------|--------------------|-----------------|  
|`Name`|一般|必要屬性。 指定類型名稱。|  
|`Activate`|反射|選擇性屬性。 控制建構函式的執行階段存取，以便啟動執行個體。|  
|`Browse`|反射|選擇性屬性。 控制程式項目相關資訊的查詢，但不會啟用任何執行階段存取。|  
|`Dynamic`|反射|選擇性屬性。 控制對所有類型成員 (包括建構函式、方法、欄位、屬性和事件) 的執行階段存取，以啟用動態程式設計。|  
|`Serialize`|序列化|選擇性屬性。 控制建構函式、欄位和屬性的執行階段存取，以便 Newtonsoft JSON 序列化程式等程式庫可對類型執行個體進行序列化和還原序列化。|  
|`DataContractSerializer`|序列化|選擇性屬性。 控制使用 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> 類別的序列化原則。|  
|`DataContractJsonSerializer`|序列化|選擇性屬性。 控制使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> 類別的 JSON 序列化原則。|  
|`XmlSerializer`|序列化|選擇性屬性。 控制使用 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> 類別的 XML 序列化原則。|  
|`MarshalObject`|Interop|選擇性屬性。 控制 Windows 執行階段和 COM 之參考類型的封送處理原則。|  
|`MarshalDelegate`|Interop|選擇性屬性。 控制將委派類型當作函式指標封送處理至機器碼的原則。|  
|`MarshalStructure`|Interop|選擇性屬性。 控制將值類型封送處理為原生程式碼的原則。|  
  
## <a name="name-attribute"></a>Name 屬性  
  
|值|描述|  
|-----------|-----------------|  
|*type_name*|類型名稱。 如果這個 `<Type>` 元素是 [\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md) 元素或另一個 `<Type>` 元素的子系，則 *type_name* 可以包含類型的名稱，而不含命名空間。 否則，*type_name* 必須包含完整的類型名稱。|  
  
## <a name="all-other-attributes"></a>所有其他屬性  
  
|值|描述|  
|-----------|-----------------|  
|*policy_setting*|要套用到此原則類型的設定。 可能的值為 `All`、`Auto`、`Excluded`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal` 和 `Required All`。 如需詳細資訊，請參閱[執行階段指示詞原則設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)。|  
  
### <a name="child-elements"></a>子項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<AttributeImplies>](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|如果包含之類型是屬性，則定義屬性套用到的程式碼項目的執行階段原則。|  
|[\<Event>](../../../docs/framework/net-native/event-element-net-native.md)|將反映原則套用至屬於此類型的事件。|  
|[\<Field>](../../../docs/framework/net-native/field-element-net-native.md)|將反映原則套用至屬於此類型的欄位。|  
|[\<GenericParameter>](../../../docs/framework/net-native/genericparameter-element-net-native.md)|將原則套用至泛型類型的參數類型。|  
|[\<ImpliesType>](../../../docs/framework/net-native/impliestype-element-net-native.md)|如果原則已套用至包含 `<Type>` 元素所表示的類型，則會將該原則套用至類型。|  
|[\<Method>](../../../docs/framework/net-native/method-element-net-native.md)|將反映原則套用至屬於此類型的方法。|  
|[\<MethodInstantiation>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|將反映原則套用至屬於此類型的建構泛型方法。|  
|[\<Property>](../../../docs/framework/net-native/property-element-net-native.md)|將反映原則套用至屬於此類型的屬性。|  
|[\<Subtypes>](../../../docs/framework/net-native/subtypes-element-net-native.md)|將執行階段原則套用至從包含類型繼承的所有類別。|  
|`<Type>`|將反映原則套用至巢狀類型。|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|將反映原則套用至建構的泛型類型。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<Application>](../../../docs/framework/net-native/application-element-net-native.md)|做為容器，以包含整個應用程式的類型，以及中繼資料可在執行階段用於反映的類型成員。|  
|[\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md)|將反映原則套用至指定組件中的所有類型。|  
|[\<程式庫>](../../../docs/framework/net-native/library-element-net-native.md)|定義包含類型和類型成員的組件，該類型和類型成員的中繼資料會在執行階段用於反映。|  
|[\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)|將反映原則套用至命名空間中的所有類型。|  
|`<Type>`|將反映原則套用至類型及其所有成員。|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|將反映原則套用至已建構的泛型類型及其所有成員。|  
  
## <a name="remarks"></a>備註  
 反映、序列化和 interop 屬性都是選用性。 如果都不存在，`<Type>` 項目會做為容器，其子類型會定義個別成員的原則。  
  
 如果 `<Type>` 元素是 [\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md)、[\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)、`<Type>` 或 [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 元素的子系，它會覆寫父元素所定義的原則設定。  
  
 泛型類型的 `<Type>` 項目會將其原則套用至沒有自己的原則的所有例項。 建構的泛型型別原則是由 [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 元素所定義。  
  
 如果類型是泛型類型，其名稱會標示抑音符號符號 (\`) 後面接著其泛型參數的數目。 例如，`Name` 類別之 `<Type>` 元素的 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> 屬性，會顯示為 `Name="System.Collections.Generic.List`1"`。  
  
## <a name="example"></a>範例  
 下列範例使用反映來顯示 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> 類別之欄位、屬性和方法的相關資訊。 變數 `b` 在範例中是 [TextBlock](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) 控制項。 因為範例只會擷取類型資訊，所以中繼資料的可用性是由 `Browse` 原則設定所控制。  
  
 [!code-csharp[ProjectN_Reflection#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/browsegenerictype1.cs#3)]  
  
 因為 <xref:System.Collections.Generic.List%601> 類別中繼資料不會自動併入 [!INCLUDE[net_native](../../../includes/net-native-md.md)] 工具鏈結，所以範例無法在執行階段顯示要求的成員資訊。 若要提供必要的中繼資料，將下列 `<Type>` 項目加入到執行階段指示詞檔案。 請注意，因為我們提供了父代 [<Namespace\>](../../../docs/framework/net-native/namespace-element-net-native.md) 元素，所以不必在 `<Type>` 元素中提供完整的類型名稱。  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="*Application*" Dynamic="Required All" />  
      <Namespace Name ="System.Collections.Generic" >  
        <Type Name="List`1" Browse="Required All" />   
     </Namespace>  
   </Application>  
</Directives>  
```  
  
## <a name="example"></a>範例  
 下列範例使用反映來擷取 <xref:System.Reflection.PropertyInfo> 物件，代表 <xref:System.String.Chars%2A?displayProperty=nameWithType> 屬性。 然後，它使用 <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> 方法擷取字串中的第七個字元的值，並顯示字串中的所有字元。 變數 `b` 在範例中是 [TextBlock](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) 控制項。  
  
 [!code-csharp[ProjectN_Reflection#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/propertyinfo1.cs#1)]  
  
 由於無法使用 <xref:System.String> 物件的中繼資料，因此在使用 <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> 工具鏈結編譯時，呼叫 <xref:System.NullReferenceException> 方法會在執行階段擲回 [!INCLUDE[net_native](../../../includes/net-native-md.md)] 例外狀況。 若要消除例外狀況，並提供必要的中繼資料，將下列 `<Type>` 項目加入至執行階段指示詞檔案：  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
    <Assembly Name="*Application*" Dynamic="Required All" />  
    <Type Name="System.String" Dynamic="Required Public"/> -->  
  </Application>  
</Directives>  
```  
  
## <a name="see-also"></a>另請參閱  
 [執行階段指示詞 (rd.xml) 組態檔參考](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [執行階段指示詞項目](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [執行階段指示詞原則設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
