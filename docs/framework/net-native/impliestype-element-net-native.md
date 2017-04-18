---
title: "&lt;ImpliesType&gt; 項目 (.NET Native) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# &lt;ImpliesType&gt; 項目 (.NET Native)
如果原則已套用至包含類型或方法，則會將該原則套用至類型。  
  
## <a name="syntax"></a>語法  
  
```vb  
  
<ImpliesType Name="type_name"  
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
  
|屬性|屬性類型|描述|  
|---------------|--------------------|-----------------|  
|`Name`|一般|必要屬性。 指定類型名稱。|  
|`Activate`|反射|選擇性屬性。 控制建構函式的執行階段存取，以便啟動執行個體。|  
|`Browse`|反射|選擇性屬性。 控制程式項目相關資訊的查詢，但不會啟用任何執行階段存取。|  
|`Dynamic`|反射|選擇性屬性。 控制對所有類型成員 (包括建構函式、方法、欄位、屬性和事件) 的執行階段存取，以啟用動態程式設計。|  
|`Serialize`|序列化|選擇性屬性。 控制建構函式、欄位和屬性的執行階段存取，以便 Newtonsoft JSON 序列化程式等程式庫可對類型執行個體進行序列化和還原序列化。|  
|`DataContractSerializer`|序列化|選擇性屬性。 控制使用的序列化原則<xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName>類別。|  
|`DataContractJsonSerializer`|序列化|選擇性屬性。 控制使用的 JSON 序列化原則<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=fullName>類別。|  
|`XmlSerializer`|序列化|選擇性屬性。 使用 XML 序列化原則會控制<xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName>類別。|  
|`MarshalObject`|Interop|選擇性屬性。 控制 Windows 執行階段和 COM 之參考類型的封送處理原則。|  
|`MarshalDelegate`|Interop|選擇性屬性。 控制將委派類型當作函式指標封送處理至機器碼的原則。|  
|`MarshalStructure`|Interop|選擇性屬性。 控制將值類型封送處理為原生程式碼的原則。|  
  
## <a name="name-attribute"></a>Name 屬性  
  
|值|說明|  
|-----------|-----------------|  
|*type_name*|類型名稱。 如果型別表示由此`<ImpliesType>`項目是否位於相同的命名空間，做為其包含`<Type>`項目， *type_name*可以包含的型別，而不需要它的命名空間名稱。 否則， *type_name*必須包含完整型別名稱。|  
  
## <a name="all-other-attributes"></a>所有其他屬性  
  
|值|說明|  
|-----------|-----------------|  
|*policy_setting*|要套用到此原則類型的設定。 可能的值為 `All`、`Auto`、`Excluded`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal` 和 `Required All`。 如需詳細資訊，請參閱[執行階段指示詞原則設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)。|  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[<>\>](../../../docs/framework/net-native/type-element-net-native.md)|將反映原則套用至類型及其所有成員。|  
|[<>\>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|將反映原則套用至建構的泛型類型及其所有成員。|  
|[<>\>](../../../docs/framework/net-native/method-element-net-native.md)|將反映原則套用至方法。|  
  
## <a name="remarks"></a>備註  
 `<ImpliesType>` 元素的主要目的是要供程式庫使用。 它可以解決下列情況：  
  
-   如果常式需要反映在一個類型上，則一定需要反映在第二個類型上。  
  
-   否則，無法將中繼資料用於第二個類型的隱含具現化，因為靜態分析並未指出中繼資料是必要的。  
  
 大多數情況下，這兩個類型是含有共用類型引數的泛型具現化。  
  
 `<ImpliesType>` 元素的定義是假設如果需要反映在其父元素指定的類型上，則表示需要反映在 `<ImpliesType>` 元素所指定的類型上。 例如，下列反映指示詞套用至 `Explicit<T>` 和 `Implicit<T>` 這兩種類型。  
  
```xml  
  
<Type Name=”Explicit{ET}”>  
    <ImpliesType Name=”Implicit{ET}” Dynamic=”Required Public” />  
</Type>  
  
```  
  
 除非 `Explicit` 的具現化具有已定義的 `Dynamic` 原則設定，否則這個指示詞沒有任何作用。 例如，如果 `Explicit<Int32>` 是這種情形，則會以其公用成員為基礎來將 `Implicit<Int32>` 具現化，並使其中繼資料可供存取來進行動態程式設計。  
  
 下列是套用到至少一個序列化程式的真實世界範例。 指示詞擷取需求︰ 反映的組件的型別為`IList<`*東西*`>` ，也需要反映在相對應`List<`*東西*`>`而不需要任何個別應用程式註釋的型別。  
  
```xml  
  
<Type Name=”System.Collections.Generic.IList{T}”>  
   <ImpliesType Name=”System.Collections.Generic.List{T}” Serialize=”Public” />  
</Type>  
  
```  
  
 `<ImpliesType>` 元素也會出現在 `<Method>` 元素中，因為在某些情況下，具現化泛型方法表示要反映在類型具現化上。 例如，假設泛型方法`IEnumerable<T> MakeEnumerable<T>(string` `spelling``, T` `defaultValue``)`特定程式庫將以動態方式存取隨著相關聯<xref:System.Collections.Generic.List%601>和<xref:System.Array>型別。 這可以表示成：  
  
```xml  
  
<Type Name=”MyType”>  
    <Method Name=”MakeEnumerable{T}” Signature=”(System.String, T)” Dynamic=”Included”>  
        <ImpliesType Name=”T[]” Dynamic=”Public” />  
        <ImpliesType Name=”System.Collections.Generic.List{T}” Dynamic=”Public”>  
    </Method>  
</Type>  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [執行階段指示詞 (rd.xml) 組態檔參考](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)   
 [執行階段指示詞項目](../../../docs/framework/net-native/runtime-directive-elements.md)   
 [執行階段指示詞原則設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)