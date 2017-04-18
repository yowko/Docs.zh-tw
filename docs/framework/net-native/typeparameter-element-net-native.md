---
title: "&lt;TypeParameter&gt; 項目 (.NET Native) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d37bb1b7-1ddc-4c6d-8ecf-583f804a2479
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# &lt;TypeParameter&gt; 項目 (.NET Native)
將原則套用至傳遞給某個方法之類型引數所代表的類型。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<Parameter Name="parameter_name"  
           Activate="policy_type"  
           Browse="policy_type"  
           Dynamic="policy_type"  
           Serialize="policy_type"  
           DataContractSerializer="policy_type"  
           DataContractJsonSerializer="policy_type"  
           XmlSerializer="policy_type"  
           MarshalObject="policy_type"  
           MarshalDelegate="policy_type"  
           MarshalStructure="policy_type" />  
  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|屬性類型|描述|  
|---------------|--------------------|-----------------|  
|`Name`|一般|必要屬性。 類型參數名稱<xref:System.Type>。 例如，對於方法簽章 `Type.GetInterfaceMap(Type interfaceType)`，`Name` 屬性的值為 "interfaceType"。|  
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
|*parameter_name*|類型參數名稱<xref:System.Type>。 例如，對於方法簽章 `Type.GetInterfaceMap(Type interfaceType)`，`Name` 屬性的值為 "interfaceType"。|  
  
## <a name="all-other-attributes"></a>所有其他屬性  
  
|值|說明|  
|-----------|-----------------|  
|*policy_setting*|要套用到此原則類型的設定。 可能的值為 `All`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal` 和 `Required All`。 如需詳細資訊，請參閱[執行階段指示詞原則設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)。|  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[<>\>](../../../docs/framework/net-native/method-element-net-native.md)|將執行階段反映原則套用到建構函式或方法。|  
  
## <a name="remarks"></a>備註  
 `<TypeParameter>`項目是類似於[ <> \> ](../../../docs/framework/net-native/parameter-element-net-native.md)項目，但它可以只會套用至型別參數的<xref:System.Type>。 這個項目會將原則套用至 `Name` 屬性所指定的類型引數在執行階段所代表的任何類型。  
  
 例如，NewtonSoft JSON 序列化程式包含靜態 `JsonConvert.DeserializeObject(String value, Type type)` 方法。 下列反映指示詞：  
  
```xml  
  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject">  
         <GenericParameter Name="type" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
  
```  
  
 指定所代表的執行階段類型的中繼資料`type`引數應該可供進行序列化。 如果這些執行階段指示詞套用至包含下列原始程式碼的專案：  
  
```csharp  
  
Type t = typeof(StockQuote);  
Object obj = JsonConvert.DeserializeObject(data, t);  
  
```  
  
 反映指示詞會在執行階段，將 `StockQuote` 類型的中繼資料提供給 NewtonSoft JSON 序列化程式。  
  
## <a name="see-also"></a>另請參閱  
 [<>\>項目](../../../docs/framework/net-native/method-element-net-native.md)   
 [執行階段指示詞 (rd.xml) 組態檔參考](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)   
 [執行階段指示詞原則設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)   
 [執行階段指示詞項目](../../../docs/framework/net-native/runtime-directive-elements.md)