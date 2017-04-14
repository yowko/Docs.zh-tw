---
title: "&lt;GenericParameter&gt; 項目 (.NET Native) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cbd49732-3615-49a5-a900-f96947cdc3e6
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# &lt;GenericParameter&gt; 項目 (.NET Native)
將原則套用到泛型類型或方法的參數類型。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<GenericParameter Name="generic_parameter_name"  
                  Activate="policy_type"  
                  Browse="policy_type"  
                  Dynamic="policy_type"  
                  Serialize="policy_type" />  
                  DataContractSerializer="policy_type"  
                  DataContractJsonSerializer="policy_type"  
                  XmlSerializer="policy_type"  
                  MarshalObject="policy_type"  
                  MarshalDelegate="policy_type"  
                  MarshalStructure="policy_type"  
  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|屬性類型|說明|  
|---------------|--------------------|-----------------|  
|`Name`|一般|必要屬性。 泛型參數的名稱。 例如，針對泛型委派<xref:System.Func%603>，值`Name`屬性是"TResult"，將執行階段原則套用至委派的傳回值。\</T1, T2, TResult>|  
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
|*generic_parameter_name*|必要屬性。 泛型類型參數的名稱。 例如，針對泛型委派<xref:System.Func%603>、 *generic_parameter_name* "Tresult"的值執行階段原則套用至委派的傳回值。\</T1, T2, TResult>|  
  
## <a name="all-other-attributes"></a>所有其他屬性  
  
|值|說明|  
|-----------|-----------------|  
|*policy_setting*|要套用到此原則類型的設定。 可能的值為 `All`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal` 和 `Required All`。 如需詳細資訊，請參閱[執行階段指示詞原則設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)。|  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[<>\>](../../../docs/framework/net-native/method-element-net-native.md)|將執行階段反映原則套用到建構函式或方法。|  
|[<>\>](../../../docs/framework/net-native/type-element-net-native.md)|將執行階段反映原則套用至特定類型，例如類別或結構。|  
  
## <a name="remarks"></a>備註  
 `<GenericParameter>`元素是子系[ <> \> ](../../../docs/framework/net-native/method-element-net-native.md)或[ <> \> ](../../../docs/framework/net-native/type-element-net-native.md)項目，用來將原則套用至特定泛型類型參數，這是由其泛型型別或方法簽章中的名稱。  
  
 `<GenericParameter>` 元素與序列化程式搭配使用時最有用。 下列範例會使用`<GenericParameter>`將原則套用至類型的項目`T`NewtonSoft JSON 序列化程式的呼叫中[JsonConvert.DeserializeObject<>\>（字串）](http://james.newtonking.com/json/help/index.html?topic=html/T_Newtonsoft_Json_JsonConvert.htm)方法多載。  
  
```xml  
  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject{T}">  
         <GenericParameter Name="T" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [<>\>項目](../../../docs/framework/net-native/method-element-net-native.md)   
 [<>\>項目](../../../docs/framework/net-native/type-element-net-native.md)   
 [執行階段指示詞 (rd.xml) 組態檔參考](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)   
 [執行階段指示詞原則設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)   
 [執行階段指示詞項目](../../../docs/framework/net-native/runtime-directive-elements.md)