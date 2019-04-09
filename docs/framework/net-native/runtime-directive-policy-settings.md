---
title: 執行階段指示詞原則設定
ms.date: 03/30/2017
ms.assetid: cb52b1ef-47fd-4609-b69d-0586c818ac9e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9015ec35c2a3d13b986eb9524e4f2984d909eb21
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098230"
---
# <a name="runtime-directive-policy-settings"></a>執行階段指示詞原則設定
> [!NOTE]
>  本主題討論 .NET 原生開發人員預覽，這是發行前版本的軟體。 您可以從 [Microsoft Connect 網站](https://go.microsoft.com/fwlink/?LinkId=394611)下載預覽 (需要註冊)。  
  
 .NET Native 的執行階段指示詞原則設定，可決定類型和類型成員的中繼資料在執行階段的可用性。 如果沒有必要的中繼資料，依賴反映、序列化和還原序列化的作業，或是將 .NET Framework 類型封送處理至 COM 或 Windows 執行階段的作業會失敗，並擲回例外狀況。 最常見的例外狀況是 [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) 和 (在 Interop 的案例中) [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)。  
  
 執行階段原則設定是由執行階段指示詞 (.rd.xml) 檔案控制。 每個執行階段指示詞都會為特定的程式項目定義原則，這些程式項目像是組件 ([\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md) 項目)、類型 ([\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 項目) 或方法 ([\<Method>](../../../docs/framework/net-native/method-element-net-native.md) 項目)。 指示詞包含一或多個屬性，可定義反映原則類型、序列化原則類型，以及下一節將討論的 interop 原則類型。 屬性的值可定義原則設定。  
  
## <a name="policy-types"></a>原則類型  
 執行階段指示詞檔案會辨識三種原則類型：反映、序列化和 interop。  
  
-   反映原則類型可決定哪些中繼資料可在執行階段供反映使用：  
  
    -   `Activate` 控制對建構函式，以便啟動執行個體的執行階段存取。  
  
    -   `Browse` 控制項的相關資訊的查詢程式項目。  
  
    -   `Dynamic` 控制執行階段存取，所有類型和成員，以啟用動態程式設計。  
  
     下表列出反映原則類型，以及可與其搭配使用的程式元素。  
  
    |項目|啟動|瀏覽|動態|  
    |-------------|--------------|------------|-------------|  
    |[\<Application>](../../../docs/framework/net-native/application-element-net-native.md)|✓|✓|✓|  
    |[\<組件 >](../../../docs/framework/net-native/assembly-element-net-native.md)|✓|✓|✓|  
    |[\<AttributeImplies>](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|✓|✓|✓|  
    |[\<事件 >](../../../docs/framework/net-native/event-element-net-native.md)||✓|✓|  
    |[\<欄位 >](../../../docs/framework/net-native/field-element-net-native.md)||✓|✓|  
    |[\<GenericParameter>](../../../docs/framework/net-native/genericparameter-element-net-native.md)|✓|✓|✓|  
    |[\<ImpliesType>](../../../docs/framework/net-native/impliestype-element-net-native.md)|✓|✓|✓|  
    |[\<方法 >](../../../docs/framework/net-native/method-element-net-native.md)||✓|✓|  
    |[\<MethodInstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)||✓|✓|  
    |[\<命名空間 >](../../../docs/framework/net-native/namespace-element-net-native.md)|✓|✓|✓|  
    |[\<Parameter>](../../../docs/framework/net-native/parameter-element-net-native.md)|✓|✓|✓|  
    |[\<屬性 >](../../../docs/framework/net-native/property-element-net-native.md)||✓|✓|  
    |[\<子類型 >](../../../docs/framework/net-native/subtypes-element-net-native.md)|✓|✓|✓|  
    |[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|✓|✓|✓|  
    |[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|✓|✓|✓|  
    |[\<TypeParameter>](../../../docs/framework/net-native/typeparameter-element-net-native.md)|✓|✓|✓|  
  
-   序列化原則類型可決定哪些中繼資料可在執行階段供序列化和還原序列化使用：  
  
    -   `Serialize` 控制對建構函式、 欄位和屬性，以便 Newtonsoft JSON 序列化程式之類的協力廠商程式庫所要序列化的型別執行個體的執行階段存取。  
  
    -   `DataContractSerializer` 控制對建構函式、 欄位和屬性，讓類型執行個體所序列化的執行階段存取<xref:System.Runtime.Serialization.DataContractSerializer>類別。  
  
    -   `DataContractJsonSerializer` 控制對建構函式、 欄位和屬性，讓類型執行個體所序列化的執行階段存取<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>類別。  
  
    -   `XmlSerializer` 控制對建構函式、 欄位和屬性，讓類型執行個體所序列化的執行階段存取<xref:System.Xml.Serialization.XmlSerializer>類別。  
  
     下表列出序列化原則類型，以及可與其搭配使用的程式元素。  
  
    |項目|序列化|DataContractSerializer|DataContractJsonSerializer|XmlSerializer|  
    |-------------|---------------|----------------------------|--------------------------------|-------------------|  
    |[\<Application>](../../../docs/framework/net-native/application-element-net-native.md)|✓|✓|✓|✓|  
    |[\<組件 >](../../../docs/framework/net-native/assembly-element-net-native.md)|✓|✓|✓|✓|  
    |[\<AttributeImplies>](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|✓|✓|✓|✓|  
    |[\<事件 >](../../../docs/framework/net-native/event-element-net-native.md)|||||  
    |[\<欄位 >](../../../docs/framework/net-native/field-element-net-native.md)|✓||||  
    |[\<GenericParameter>](../../../docs/framework/net-native/genericparameter-element-net-native.md)|✓|✓|✓|✓|  
    |[\<ImpliesType>](../../../docs/framework/net-native/impliestype-element-net-native.md)|✓|✓|✓|✓|  
    |[\<方法 >](../../../docs/framework/net-native/method-element-net-native.md)|||||  
    |[\<MethodInstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|||||  
    |[\<命名空間 >](../../../docs/framework/net-native/namespace-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Parameter>](../../../docs/framework/net-native/parameter-element-net-native.md)|✓|✓|✓|✓|  
    |[\<屬性 >](../../../docs/framework/net-native/property-element-net-native.md)|✓||||  
    |[\<子類型 >](../../../docs/framework/net-native/subtypes-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|✓|✓|✓|✓|  
    |[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|✓|✓|✓|✓|  
    |[\<TypeParameter>](../../../docs/framework/net-native/typeparameter-element-net-native.md)|✓|✓|✓|✓|  
  
-   Interop 原則類型可決定哪些中繼資料在執行階段可供使用，以將參考類型、值類型和函式指標傳遞至 COM 和 Windows 執行階段：  
  
    -   `MarshalObject` 原生封送處理至 COM 和 Windows 執行階段參考類型的控制項。  
  
    -   `MarshalDelegate` 控制委派類型當作函式指標的原生封送處理。  
  
    -   `MarshalStructure` 原生封送處理至 COM 和 Windows 執行階段實值類型的控制項。  
  
     下表列出 interop 原則類型，以及可與其搭配使用的程式元素。  
  
    |項目|MarshalObject|MarshalDelegate|MarshalStructure|  
    |-------------|-------------------|---------------------|----------------------|  
    |[\<Application>](../../../docs/framework/net-native/application-element-net-native.md)|✓|✓|✓|  
    |[\<組件 >](../../../docs/framework/net-native/assembly-element-net-native.md)|✓|✓|✓|  
    |[\<AttributeImplies>](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|✓|✓|✓|  
    |[\<事件 >](../../../docs/framework/net-native/event-element-net-native.md)||||  
    |[\<欄位 >](../../../docs/framework/net-native/field-element-net-native.md)||||  
    |[\<GenericParameter>](../../../docs/framework/net-native/genericparameter-element-net-native.md)|✓|✓|✓|  
    |[\<ImpliesType>](../../../docs/framework/net-native/impliestype-element-net-native.md)|✓|✓|✓|  
    |[\<方法 >](../../../docs/framework/net-native/method-element-net-native.md)||||  
    |[\<MethodInstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)||||  
    |[\<命名空間 >](../../../docs/framework/net-native/namespace-element-net-native.md)|✓|✓|✓|  
    |[\<Parameter>](../../../docs/framework/net-native/parameter-element-net-native.md)|✓|✓|✓|  
    |[\<屬性 >](../../../docs/framework/net-native/property-element-net-native.md)||||  
    |[\<子類型 >](../../../docs/framework/net-native/subtypes-element-net-native.md)|✓|✓|✓|  
    |[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|✓|✓|✓|  
    |[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|✓|✓|✓|  
    |[\<TypeParameter>](../../../docs/framework/net-native/typeparameter-element-net-native.md)|✓|✓|✓|  
  
## <a name="policy-settings"></a>原則設定  
 每個原則類型都可以設定為下表列出的其中一個值。 請注意，代表類型成員的元素可支援不同於其他元素的原則設定集。  
  
|原則設定|描述|`Assembly``Namespace`， `Type`，和`TypeInstantiation`項目|`Event``Field`， `Method`， `MethodInstantiation`，和`Property`項目|  
|--------------------|-----------------|-----------------------------------------------------------------------|--------------------------------------------------------------------------------|  
|`All`|針對 .NET Native 工具鏈未移除的所有類型和成員啟用原則。|✓||  
|`Auto`|指定應將預設原則用於該程式元素的原則類型。 此設定如同省略該原則類型的原則。 `Auto` 通常用來表示從父元素繼承原則。|✓|✓|  
|`Excluded`|指定為特定程式元素停用原則。 例如，執行階段指示詞：<br /><br /> `<Type Name="BusinessClasses.Person" Browse="Excluded" Dynamic="Excluded" />`<br /><br /> 指定 `BusinessClasses.Person` 類別的中繼資料不能用來瀏覽，或是動態具現化及修改 `Person` 物件。|✓|✓|  
|`Included`|如果父類型的中繼資料可用，則啟用原則。||✓|  
|`Public`|為公用類型或成員啟用原則，除非工具鏈判斷該類型或成員是不必要的，並因此將它移除。 此設定不同於 `Required Public`，後者可確保公用類型和成員的中繼資料一律可供使用，即使工具鏈判斷為不必要也一樣。|✓||  
|`PublicAndInternal`|為公用和內部類型或成員啟用原則，除非工具鏈判斷該類型或成員是不必要的，並因此將它移除。 此設定不同於 `Required PublicAndInternal`，後者可確保公用和內部類型和成員的中繼資料一律可供使用，即使工具鏈判斷為不必要也一樣。|✓||  
|`Required`|指定成員的原則已啟用，而且即使可能會使用該成員，中繼資料還是可供使用。||✓|  
|`Required Public`|啟用公用類型或成員的原則，並確保公用類型和成員的中繼資料一律可供使用。 此設定不同於 `Public`，後者只會在工具鏈判斷為必要時，才會讓公用類型和成員的中繼資料可供使用。|✓||  
|`Required PublicAndInternal`|啟用公用及內部類型或成員的原則，並確保公用及內部類型和成員的中繼資料一律可供使用。 此設定不同於 `PublicAndInternal`，後者只會在工具鏈判斷為必要時，才會讓公用及內部類型和成員的中繼資料可供使用。|✓||  
|`Required All`|需要工具鏈保留所有類型和成員 (無論是否使用)，並為其啟用原則。|✓||  
  
## <a name="see-also"></a>另請參閱

- [執行階段指示詞 (rd.xml) 組態檔參考](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [執行階段指示詞項目](../../../docs/framework/net-native/runtime-directive-elements.md)
