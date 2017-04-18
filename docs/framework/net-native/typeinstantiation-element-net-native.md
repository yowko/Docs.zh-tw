---
title: "&lt;TypeInstantiation&gt; 項目 (.NET Native) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a5eada64-075b-4162-9655-ded84e4681f2
caps.latest.revision: 21
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 21
---
# &lt;TypeInstantiation&gt; 項目 (.NET Native)
將執行階段反映原則套用至建構的泛型類型。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<TypeInstantiation Name="type_name"  
                   Arguments="type_arguments"  
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
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|屬性類型|說明|  
|---------------|--------------------|-----------------|  
|`Name`|一般|必要屬性。 指定類型名稱。|  
|`Arguments`|一般|必要屬性。 指定泛型類型引數。 如果有多個引數存在，會以逗號分隔。|  
|`Activate`|反射|選擇性屬性。 控制建構函式的執行階段存取，以便啟動執行個體。|  
|`Browse`|反射|選擇性屬性。 控制程式項目相關資訊的查詢，但不會啟用任何執行階段存取。|  
|`Dynamic`|反射|選擇性屬性。 控制對所有類型成員 (包括建構函式、方法、欄位、屬性和事件) 的執行階段存取，以啟用動態程式設計。|  
|`Serialize`|序列化|選擇性屬性。 控制建構函式、欄位和屬性的執行階段存取，以便 Newtonsoft JSON 序列化程式等程式庫可對類型執行個體進行序列化和還原序列化。|  
|`DataContractSerializer`|序列化|選擇性屬性。 控制使用的序列化原則<xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName>類別。|  
|`DataContractJsonSerializer`|序列化|選擇性屬性。 控制使用的 JSON 序列化原則<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=fullName>類別。|  
|`XmlSerializer`|序列化|選擇性屬性。 使用 XML 序列化原則會控制<xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName>類別。|  
|`MarshalObject`|Interop|選擇性屬性。 控制 Windows 執行階段和 COM 之參考類型的封送處理原則。|  
|`MarshalDelegate`|Interop|選擇性屬性。 控制將委派類型當作函式指標封送處理至機器碼的原則。|  
|`MarshalStructure`|Interop|選擇性屬性。 控制將結構封送處理至機器碼的原則。|  
  
## <a name="name-attribute"></a>Name 屬性  
  
|值|說明|  
|-----------|-----------------|  
|*type_name*|類型名稱。 如果這個`<TypeInstantiation>`元素是子系[ <> \> ](../../../docs/framework/net-native/namespace-element-net-native.md)項目， [ <> \> ](../../../docs/framework/net-native/type-element-net-native.md)項目，或另一個`<TypeInstantiation>`項目， *type_name*可以指定其命名空間類型的名稱。 否則， *type_name*必須包含完整型別名稱。 不裝飾類型名稱。 例如，對於<xref:System.Collections.Generic.List%601?displayProperty=fullName>物件，`<TypeInstantiation>`項目可能會出現，如下所示︰<br /><br /> `\<TypeInstantiation Name=System.Collections.Generic.List Dynamic="Required Public" />`|  
  
## <a name="arguments-attribute"></a>引數屬性  
  
|值|描述|  
|-----------|-----------------|  
|*type_argument*|指定泛型型別引數。 如果有多個引數存在，會以逗號分隔。 每個引數都必須包含完整的類型名稱。|  
  
## <a name="all-other-attributes"></a>所有其他屬性  
  
|值|描述|  
|-----------|-----------------|  
|*policy_setting*|要為建構的泛型類型套用至此原則類型的設定。 可能的值為 `All`、`Auto`、`Excluded`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal` 和 `Required All`。 如需詳細資訊，請參閱[執行階段指示詞原則設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)。|  
  
### <a name="child-elements"></a>子項目  
  
|項目|說明|  
|-------------|-----------------|  
|[<>\>](../../../docs/framework/net-native/event-element-net-native.md)|將反映原則套用至屬於此類型的事件。|  
|[<>\>](../../../docs/framework/net-native/field-element-net-native.md)|將反映原則套用至屬於此類型的欄位。|  
|[<>\>](../../../docs/framework/net-native/impliestype-element-net-native.md)|如果原則已套用至包含 `<TypeInstantiation>` 元素所表示的類型，則會將該原則套用至類型。|  
|[<>\>](../../../docs/framework/net-native/method-element-net-native.md)|將反映原則套用至屬於此類型的方法。|  
|[<>\>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|將反映原則套用至屬於此類型的建構泛型方法。|  
|[<>\>](../../../docs/framework/net-native/property-element-net-native.md)|將反映原則套用至屬於此類型的屬性。|  
|[<>\>](../../../docs/framework/net-native/type-element-net-native.md)|將反映原則套用至巢狀類型。|  
|`<TypeInstantiation>`|將反映原則套用至巢狀建構的泛型類型。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[<>\>](../../../docs/framework/net-native/application-element-net-native.md)|做為整個應用程式的類型和類型成員的容器，這些類型和類型成員的中繼資料可在執行階段用於反映。|  
|[<>\>](../../../docs/framework/net-native/assembly-element-net-native.md)|將反映原則套用至指定組件中的所有類型。|  
|[<>\>](../../../docs/framework/net-native/library-element-net-native.md)|定義包含類型和類型成員的組件，該類型和類型成員的中繼資料會在執行階段用於反映。|  
|[<>\>](../../../docs/framework/net-native/namespace-element-net-native.md)|將反映原則套用至命名空間中的所有類型。|  
|[<>\>](../../../docs/framework/net-native/type-element-net-native.md)|將反映原則套用至類型及其所有成員。|  
|`<TypeInstantiation>`|將反映原則套用至建構的泛型類型及其所有成員。|  
  
## <a name="remarks"></a>備註  
 反映、序列化和 interop 屬性都是選用性。 不過，必須至少有一個屬性存在。  
  
 如果`<TypeInstantiation>`元素是子系[ <> \</> \> ](../../../docs/framework/net-native/assembly-element-net-native.md)， [ <> \</> \> ](../../../docs/framework/net-native/namespace-element-net-native.md)，或[ <> \</> \> ](../../../docs/framework/net-native/type-element-net-native.md)，項目，它會覆寫父元素所定義的原則設定。 如果[ <> \> ](../../../docs/framework/net-native/type-element-net-native.md)元素定義相對應的泛型型別定義，`<TypeInstantiation>`元素會覆寫執行階段反映原則，只會針對指定建構泛型類型的具現化。  
  
## <a name="example"></a>範例  
 下列範例會使用反映來擷取從建構的泛型型別定義<xref:System.Collections.Generic.Dictionary%602>物件。</TKey, TValue> 它也會使用反映來顯示資訊有關<xref:System.Type>代表建構泛型型別和泛型型別定義的物件。 變數`b`在範例中是[TextBlock](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx)控制項。  
  
 [!code-csharp[ProjectN_Reflection#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/makegenerictype1.cs#2)]  
  
 進行編譯之後[!INCLUDE[net_native](../../../includes/net-native-md.md)]工具鏈結，則會擲回[MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)例外狀況的呼叫<xref:System.Type.GetGenericTypeDefinition%2A?displayProperty=fullName>方法。 若要消除此例外狀況，並提供必要的中繼資料，您可以將下列 `<TypeInstantiation>` 元素加入至執行階段指示詞檔案：  
  
```xml  
  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
    <Assembly Name="*Application*" Dynamic="Required All" />  
     <TypeInstantiation Name="System.Collections.Generic.Dictionary"  
                        Arguments="System.String,GenericType.Example"  
                        Dynamic="Required Public" />  
  </Application>  
</Directives>  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [執行階段指示詞 (rd.xml) 組態檔參考](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)   
 [執行階段指示詞項目](../../../docs/framework/net-native/runtime-directive-elements.md)   
 [執行階段指示詞原則設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)