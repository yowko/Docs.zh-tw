---
title: 執行階段指示詞 (rd.xml) 組態檔參考
ms.date: 03/30/2017
ms.assetid: 8241523f-d8e1-4fb6-bf6a-b29bfe07b38a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3c6f1a2d23d5f33ba7e4f0d51f795e75d7cf785e
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2019
ms.locfileid: "66052444"
---
# <a name="runtime-directives-rdxml-configuration-file-reference"></a>執行階段指示詞 (rd.xml) 組態檔參考

執行階段指示詞 (.rd.xml) 檔案是 XML 組態檔，指定所委任的程式元素是否適用於反映。 以下是執行階段指示詞檔案的範例：

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
<Application>
  <Namespace Name="Contoso.Cloud.AppServices" Serialize="Required Public" />
  <Namespace Name="ContosoClient.ViewModels" Serialize="Required Public" />
  <Namespace Name="ContosoClient.DataModel" Serialize="Required Public" />
  <Namespace Name="Contoso.Reader.UtilityLib" Serialize="Required Public" />

  <Namespace Name="System.Collections.ObjectModel" >
    <TypeInstantiation Name="ObservableCollection"
          Arguments="ContosoClient.DataModel.ProductItem" Serialize="Public" />
    <TypeInstantiation Name="ReadOnlyObservableCollection"
          Arguments="ContosoClient.DataModel.ProductGroup" Serialize="Public" />
  </Namespace>
</Application>
</Directives>
```

## <a name="the-structure-of-a-runtime-directives-file"></a>執行階段指示詞檔案的結構

執行階段指示詞檔案使用 `http://schemas.microsoft.com/netfx/2013/01/metadata` 命名空間。

根項目是 [Directives](../../../docs/framework/net-native/directives-element-net-native.md) 項目。 它可以包含零 (含) 個以上的 [Library](../../../docs/framework/net-native/library-element-net-native.md) 項目，以及零或一個的 [Application](../../../docs/framework/net-native/application-element-net-native.md) 項目，如下列結構所示。 [Application](../../../docs/framework/net-native/application-element-net-native.md) 項目的屬性可以定義整個應用程式的執行階段反映原則，或是作為子項目的容器。 另一方面，[Library](../../../docs/framework/net-native/library-element-net-native.md) 項目只是容器。 [Application](../../../docs/framework/net-native/application-element-net-native.md) 和 [Library](../../../docs/framework/net-native/library-element-net-native.md) 項目的子項可定義適用於反映的類型、方法、欄位、屬性和事件。

如需參考資訊，請從下列結構中選擇項目，或參閱[執行階段指示詞項目](../../../docs/framework/net-native/runtime-directive-elements.md)。 在下列階層中，省略符號標記了遞迴結構。 方括號中的資訊指出該元素是選用或必要元素，以及如果使用該元素，可允許多少執行個體 (一個或多個)。

[指示詞](../../../docs/framework/net-native/directives-element-net-native.md)[1:1][應用程式](../../../docs/framework/net-native/application-element-net-native.md)[0:1][組件](../../../docs/framework/net-native/assembly-element-net-native.md)[0: m][命名空間](../../../docs/framework/net-native/namespace-element-net-native.md)[0: m]。 。 。
[型別](../../../docs/framework/net-native/type-element-net-native.md)[0: m]。 。 。
[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) （建構的泛型型別） [0: m]。 。 。
[命名空間](../../../docs/framework/net-native/namespace-element-net-native.md)[0: m][命名空間](../../../docs/framework/net-native/namespace-element-net-native.md)[0: m]。 。 。
[型別](../../../docs/framework/net-native/type-element-net-native.md)[0: m]。 。 。
[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) （建構的泛型型別） [0: m]。 。 。
[型別](../../../docs/framework/net-native/type-element-net-native.md)[0: m] [Subtypes](../../../docs/framework/net-native/subtypes-element-net-native.md) （包含類型的子類別） [O:1][類型](../../../docs/framework/net-native/type-element-net-native.md)[0: m]。 。 。
[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) （建構的泛型型別） [0: m]。 。 。
[AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md) （包含類型是屬性） [O:1] [GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0: m][方法](../../../docs/framework/net-native/method-element-net-native.md)[0: m][參數](../../../docs/framework/net-native/parameter-element-net-native.md)[0: m] [TypeParameter](../../../docs/framework/net-native/typeparameter-element-net-native.md) [0: m] [GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0: m] [MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) （建構的泛型方法） [0: m][屬性](../../../docs/framework/net-native/property-element-net-native.md)[0: m][欄位](../../../docs/framework/net-native/field-element-net-native.md)[0: m][事件](../../../docs/framework/net-native/event-element-net-native.md)[0: m] [Typeinstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) （建構的泛型型別） [0: m][類型](../../../docs/framework/net-native/type-element-net-native.md)[0: m]。 。 。
[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) （建構的泛型型別） [0: m]。 。 。
[方法](../../../docs/framework/net-native/method-element-net-native.md)[0: m][參數](../../../docs/framework/net-native/parameter-element-net-native.md)[0: m] [TypeParameter](../../../docs/framework/net-native/typeparameter-element-net-native.md) [0: m] [GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0: m] [MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (建構的泛型方法） [0: m][屬性](../../../docs/framework/net-native/property-element-net-native.md)[0: m][欄位](../../../docs/framework/net-native/field-element-net-native.md)[0: m][事件](../../../docs/framework/net-native/event-element-net-native.md)[0: m][文件庫](../../../docs/framework/net-native/library-element-net-native.md)[0: m] [組件](../../../docs/framework/net-native/assembly-element-net-native.md)[0: m][命名空間](../../../docs/framework/net-native/namespace-element-net-native.md)[0: m]。 。 。
[型別](../../../docs/framework/net-native/type-element-net-native.md)[0: m]。 。 。
[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) （建構的泛型型別） [0: m]。 。 。
[命名空間](../../../docs/framework/net-native/namespace-element-net-native.md)[0: m][命名空間](../../../docs/framework/net-native/namespace-element-net-native.md)[0: m]。 。 。
[型別](../../../docs/framework/net-native/type-element-net-native.md)[0: m]。 。 。
[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) （建構的泛型型別） [0: m]。 。 。
[型別](../../../docs/framework/net-native/type-element-net-native.md)[0: m] [Subtypes](../../../docs/framework/net-native/subtypes-element-net-native.md) （包含類型的子類別） [O:1][類型](../../../docs/framework/net-native/type-element-net-native.md)[0: m]。 。 。
[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) （建構的泛型型別） [0: m]。 。 。
[AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md) （包含類型是屬性） [O:1] [GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0: m][方法](../../../docs/framework/net-native/method-element-net-native.md)[0: m] [MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) （建構的泛型方法） [0: m][屬性](../../../docs/framework/net-native/property-element-net-native.md)[0: m][欄位](../../../docs/framework/net-native/field-element-net-native.md)[0: m][事件](../../../docs/framework/net-native/event-element-net-native.md)[0: m] [Typeinstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) （建構的泛型型別） [0:M][型別](../../../docs/framework/net-native/type-element-net-native.md)[0: m]。 。 。
[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) （建構的泛型型別） [0: m]。 。 。
[方法](../../../docs/framework/net-native/method-element-net-native.md)[0: m] [MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) （建構的泛型方法） [0: m][屬性](../../../docs/framework/net-native/property-element-net-native.md)[0: m][欄位](../../../docs/framework/net-native/field-element-net-native.md)[0: m][事件](../../../docs/framework/net-native/event-element-net-native.md)[0: m]

[Application](../../../docs/framework/net-native/application-element-net-native.md) 項目可以沒有任何屬性，或者可以有[執行階段指示詞和原則](#Directives)一節中所描述的原則屬性。

[Library](../../../docs/framework/net-native/library-element-net-native.md) 項目具有單一屬性 `Name`，可指定程式庫或組件的名稱，但不含副檔名。 例如，下列 [Library](../../../docs/framework/net-native/library-element-net-native.md) 項目套用於名為 Extensions.dll 的組件。

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
     <!-- Child elements go here -->
  </Application>
  <Library Name="Extensions">
     <!-- Child elements go here -->
  </Library>
</Directives>
```

<a name="Directives"></a>

## <a name="runtime-directives-and-policy"></a>執行階段指示詞和原則

[Application](../../../docs/framework/net-native/application-element-net-native.md) 項目本身以及 [Library](../../../docs/framework/net-native/library-element-net-native.md) 和 [Application](../../../docs/framework/net-native/application-element-net-native.md) 項目的子項目表示原則；也就是說，其定義應用程式可以將反映套用於程式項目的方式。 原則類型是由元素的屬性 (例如 `Serialize`) 來定義。 原則值是由屬性的值 (例如 `Serialize="Required"`) 來定義。

元素屬性所指定的任何原則，都會套用至沒有為該原則指定值的所有子元素。 例如，如果以 [Type](../../../docs/framework/net-native/type-element-net-native.md) 項目來指定原則，則該原則會套用至未明確指定原則的所有內含類型和成員。

可以使用 [Application](../../../docs/framework/net-native/application-element-net-native.md)、[Assembly](../../../docs/framework/net-native/assembly-element-net-native.md)、[AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md)、[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md)、[Subtypes](../../../docs/framework/net-native/subtypes-element-net-native.md) 和 [Type](../../../docs/framework/net-native/type-element-net-native.md) 項目表示的原則，不同於可以為個別成員表示的原則 (使用 [Method](../../../docs/framework/net-native/method-element-net-native.md)、[Property](../../../docs/framework/net-native/property-element-net-native.md)、[Field](../../../docs/framework/net-native/field-element-net-native.md) 和 [Event](../../../docs/framework/net-native/event-element-net-native.md) 項目)。

### <a name="specifying-policy-for-assemblies-namespaces-and-types"></a>為組件、命名空間和類型指定原則

[Application](../../../docs/framework/net-native/application-element-net-native.md)、[Assembly](../../../docs/framework/net-native/assembly-element-net-native.md)、[AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md)、[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md)、[Subtypes](../../../docs/framework/net-native/subtypes-element-net-native.md) 和 [Type](../../../docs/framework/net-native/type-element-net-native.md) 項目支援下列原則類型：

- `Activate`. 控制建構函式的執行階段存取，以便啟動執行個體。

- `Browse`. 控制程式項目相關資訊的查詢，但不會啟用任何執行階段存取。

- `Dynamic`. 控制對所有類型成員 (包括建構函式、方法、欄位、屬性和事件) 的執行階段存取，以啟用動態程式設計。

- `Serialize`. 控制對建構函式、欄位和屬性的執行階段存取，讓類型執行個體能夠以 Newtonsoft JSON 序列化程式之類的協力廠商程式庫來序列化和還原序列化。

- `DataContractSerializer`. 控制使用 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> 類別的序列化原則。

- `DataContractJsonSerializer`. 控制使用 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> 類別的 JSON 序列化原則。

- `XmlSerializer`. 控制使用 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> 類別的 XML 序列化原則。

- `MarshalObject`. 控制將參考類型封送處理至 WinRT 及 COM 的原則。

- `MarshalDelegate`. 控制將委派類型當作函式指標封送處理至機器碼的原則。

- `MarshalStructure` . 控制將結構封送處理至機器碼的原則。

與這些原則類型相關聯的設定如下：

- `All`. 針對工具鏈未移除的所有類型和成員，啟用原則。

- `Auto`. 使用預設行為。 (除非原則被 (例如父元素) 覆寫，否則，不指定原則相當於將該原則設定為 `Auto`。)

- `Excluded`. 為程式元素停用原則。

- `Public`. 為公用類型或成員啟用原則，除非工具鏈判斷該成員是不必要的，並因此將它移除。 (在後者的情況下，您必須使用 `Required Public` 以確保該成員會保留，而且具有反映功能。)

- `PublicAndInternal`. 如果公用和內部類型或成員沒有被工具鏈移除，則為其啟用原則。

- `Required Public`. 需要工具鏈保留公用類型和成員 (無論是否使用)，並為其啟用原則。

- `Required PublicAndInternal`. 需要工具鏈同時保留公用和內部類型和成員 (無論是否使用)，並為其啟用原則。

- `Required All`. 需要工具鏈保留所有類型和成員 (無論是否使用)，並為其啟用原則。

例如，下列執行階段指示詞檔案會為組件 DataClasses.dll 中的所有類型和成員定義原則。 它會為所有公用屬性 (property) 的序列化啟用反映功能，為所有類型和類型成員啟用瀏覽功能，為所有類型啟用啟動功能 (因為 `Dynamic` 屬性 (attribute))，並為所有公用類型和成員啟用反映功能。

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public"
                Browse="All" Activate="PublicAndInternal"
                Dynamic="Public"  />
   </Application>
   <Library Name="UtilityLibrary">
     <!-- Child elements go here -->
   </Library>
</Directives>
```

### <a name="specifying-policy-for-members"></a>為成員指定原則

[Property](../../../docs/framework/net-native/property-element-net-native.md) 和 [Field](../../../docs/framework/net-native/field-element-net-native.md) 項目支援下列原則類型：

- `Browse` - 控制對此成員相關資訊的查詢，但不會啟用任何執行階段存取。

- `Dynamic` - 控制對所有類型成員 (包括建構函式、方法、欄位、屬性和事件) 的執行階段存取，以啟用動態程式設計。 另外也會控制對包含類型相關資訊的查詢。

- `Serialize` - 控制對成員的執行階段存取，讓類型執行個體能夠以 Newtonsoft JSON 序列化程式之類的程式庫來序列化和還原序列化。 這個原則可以套用至建構函式、欄位和屬性。

[Method](../../../docs/framework/net-native/method-element-net-native.md) 和 [Event](../../../docs/framework/net-native/event-element-net-native.md) 項目支援下列原則類型：

- `Browse` - 控制對此成員相關資訊的查詢，但不會啟用任何執行階段存取。

- `Dynamic` - 控制對所有類型成員 (包括建構函式、方法、欄位、屬性和事件) 的執行階段存取，以啟用動態程式設計。 另外也會控制對包含類型相關資訊的查詢。

 與這些原則類型相關聯的設定如下：

- `Auto` - 使用預設行為。 (除非原則被覆寫，否則，不指定原則相當於將該原則設定為 `Auto`。）

- `Excluded` - 永不包含成員的中繼資料。

- `Included` - 如果父類型出現在輸出中，則啟用原則。

- `Required` - 需要工具鏈保留此成員 (即使看似未使用)，並為其啟用原則。

## <a name="runtime-directives-file-semantics"></a>執行階段指示詞檔案語意

可以將原則同時定義給較高層級和較低層級的元素。 例如，可以將原則定義給組件，以及該組件內含的一些類型。 如果未表示特定較低層級的元素，它會繼承其父元素的原則。 例如，如果 `Assembly` 元素存在，但 `Type` 元素不存在，則 `Assembly` 元素中指定的原則會套用至組件中的每個類型。 多個元素也可以將原則套用至相同的程式元素。 例如，個別的 [Assembly](../../../docs/framework/net-native/assembly-element-net-native.md) 項目可能會以不同的方式，為相同的組件定義相同的原則項目。 以下章節將說明在這些情況下，如何解析特定類型的原則。

泛型型別或方法的 [Type](../../../docs/framework/net-native/type-element-net-native.md) 或 [Method](../../../docs/framework/net-native/method-element-net-native.md) 項目，會將其原則套用至沒有自己原則的所有具現化。 例如，為 `Type` 指定原則的 <xref:System.Collections.Generic.List%601> 元素，會套用至該泛型類型的所有建構執行個體，除非已針對特定的建構泛型類型 (例如 `List<Int32>`)，以 `TypeInstantiation` 元素將它覆寫， 否則，元素會為所指名的程式元素定義原則。

當元素模稜兩可時，引擎會尋找相符項目，如果找到完全相符的項目，就會使用它。 如果找到多個相符項目，則會產生警告或錯誤。

### <a name="if-two-directives-apply-policy-to-the-same-program-element"></a>如果有兩個指示詞將原則套用至相同的程式元素

如果不同執行階段指示詞檔案中的兩個元素，嘗試將相同程式元素 (例如組件或類型) 的相同原則類型設定為不同的值，則會以下列方式解決衝突：

1. 如果 `Excluded` 元素存在，則以它為優先。

2. `Required` 的優先順序高於非 `Required`。

3. `All` 的優先順序高於 `PublicAndInternal`，而後者的優先順序高於 `Public`。

4. 任何明確的設定皆優先於 `Auto`。

例如，如果單一專案包含下列兩個執行階段指示詞檔案，則 DataClasses.dll 的序列化原則會同時設為 `Required Public` 和 `All`。 在此情況下，序列化原則會被解析成 `Required All`。

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public"/>
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="All" />
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

不過，如果單一執行階段指示詞檔案中的兩個指示詞嘗試為相同的程式元素設定相同的原則類型，則 XML 配置定義工具會顯示錯誤訊息。

### <a name="if-child-and-parent-elements-apply-the-same-policy-type"></a>如果子元素和父元素套用相同的原則類型

子元素會覆寫其父元素，包括 `Excluded` 設定。 覆寫是您會想要指定 `Auto` 的主要原因。

在下列範例中，針對 `DataClasses` 中不在 `DataClasses.ViewModels` 內的所有項目，序列化原則設定為 `Required Public`，而針對不在 `DataClasses` 和 `DataClasses.ViewModels` 內的所有項目，則為 `All`。

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public" >
         <Namespace Name="DataClasses.ViewModels" Serialize="All" />
      </Assembly>
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

### <a name="if-open-generics-and-instantiated-elements-apply-the-same-policy-type"></a>如果開放式泛型和具現化的元素套用相同的原則類型

在下列範例中，當引擎有必須為 `Dictionary<int,int>` 指定 `Browse` 原則的其他理由時，才會為其指派 `Browse` 原則 (否則為預設行為)；<xref:System.Collections.Generic.Dictionary%602> 的每個其他具現化都會使其所有成員可供瀏覽。

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public" >
         <Namespace Name="DataClasses.ViewModels" Serialize="All" />
      </Assembly>
      <Namespace Name="DataClasses.Generics" />
      <Type Name="Dictionary" Browse="All" />
      <TypeInstantiation Name="Dictionary"
                         Arguments="System.Int32,System.Int32" Browse="Auto" />
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

### <a name="how-policy-is-inferred"></a>推斷原則的方式

每個原則類型都有一組不同的規則，用以判斷該原則類型的存在對其他建構有何影響。

#### <a name="the-effect-of-browse-policy"></a>瀏覽原則的效果

將 `Browse` 原則套用至類型牽涉到下列原則變更：

- 類型的基底類型會標示 `Browse` 原則。

- 如果類型是具現化泛型，則該類型的未具現化版本會標示 `Browse` 原則。

- 如果類型是委派，則該類型上的 `Invoke` 方法會標示 `Dynamic` 原則。

- 類型的每個介面都會標示 `Browse` 原則。

- 套用至類型的每個屬性類型都會標示 `Browse` 原則。

- 如果類型是泛型，則每個條件約束類型都會標示 `Browse` 原則。

- 如果類型是泛型，則具現化類型之下的類型會標示 `Browse` 原則。

將 `Browse` 原則套用至方法牽涉到下列原則變更：

- 方法的每個參數類型會標示 `Browse` 原則。

- 方法的傳回型別會標示 `Browse` 原則。

- 方法的包含類型會標示 `Browse` 原則。

- 如果方法是具現化泛型方法，則未具現化的泛型方法會標示 `Browse` 原則。

- 套用至方法的每個屬性類型都會標示 `Browse` 原則。

- 如果方法是泛型，則每個條件約束類型都會標示 `Browse` 原則。

- 如果方法是泛型，則具現化方法之下的類型會標示 `Browse` 原則。

將 `Browse` 原則套用至欄位牽涉到下列原則變更：

- 套用至欄位的每個屬性類型都會標示 `Browse` 原則。

- 欄位的類型會標示 `Browse` 原則。

- 欄位所屬的類型會標示 `Browse` 原則。

#### <a name="the-effect-of-dynamic-policy"></a>動態原則的效果

將 `Dynamic` 原則套用至類型牽涉到下列原則變更：

- 類型的基底類型會標示 `Dynamic` 原則。

- 如果類型是具現化泛型，則該類型的未具現化版本會標示 `Dynamic` 原則。

- 如果類型是委派類型，則該類型上的 `Invoke` 方法會標示 `Dynamic` 原則。

- 類型的每個介面都會標示 `Browse` 原則。

- 套用至類型的每個屬性類型都會標示 `Browse` 原則。

- 如果類型是泛型，則每個條件約束類型都會標示 `Browse` 原則。

- 如果類型是泛型，則具現化類型之下的類型會標示 `Browse` 原則。

將 `Dynamic` 原則套用至方法牽涉到下列原則變更：

- 方法的每個參數類型會標示 `Browse` 原則。

- 方法的傳回型別會標示 `Dynamic` 原則。

- 方法的包含類型會標示 `Dynamic` 原則。

- 如果方法是具現化泛型方法，則未具現化的泛型方法會標示 `Browse` 原則。

- 套用至方法的每個屬性類型都會標示 `Browse` 原則。

- 如果方法是泛型，則每個條件約束類型都會標示 `Browse` 原則。

- 如果方法是泛型，則具現化方法之下的類型會標示 `Browse` 原則。

- 可以藉由 `MethodInfo.Invoke` 來叫用方法，而藉由 <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType> 就能夠進行委派建立。

將 `Dynamic` 原則套用至欄位牽涉到下列原則變更：

- 套用至欄位的每個屬性類型都會標示 `Browse` 原則。

- 欄位的類型會標示 `Dynamic` 原則。

- 欄位所屬的類型會標示 `Dynamic` 原則。

#### <a name="the-effect-of-activation-policy"></a>啟動原則的效果

將啟動原則套用至類型牽涉到下列原則變更：

- 如果類型是具現化泛型，則該類型的未具現化版本會標示 `Browse` 原則。

- 如果類型是委派類型，則該類型上的 `Invoke` 方法會標示 `Dynamic` 原則。

- 類型的建構函式會標示 `Activation` 原則。

將 `Activation` 原則套用至方法牽涉到下列原則變更：

- 可以藉由 <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> 和 <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> 方法來叫用建構函式。 對於方法，`Activation` 原則只會影響建構函式。

將 `Activation` 原則套用至欄位並沒有效果。

#### <a name="the-effect-of-serialize-policy"></a>序列化原則的效果

`Serialize` 原則可以啟用一般反映型序列化程式。 不過，由於 Microsoft 並不清楚非 Microsoft 序列化程式的確切反映存取模式，所以此原則可能不是全面有效。

將 `Serialize` 原則套用至類型牽涉到下列原則變更：

- 類型的基底類型會標示 `Serialize` 原則。

- 如果類型是具現化泛型，則該類型的未具現化版本會標示 `Browse` 原則。

- 如果類型是委派類型，則該類型上的 `Invoke` 方法會標示 `Dynamic` 原則。

- 如果類型是列舉，則類型的陣列會標示 `Serialize` 原則。

- 如果類型實作 <xref:System.Collections.Generic.IEnumerable%601>，則 `T` 會標示 `Serialize` 原則。

- 如果類型是 <xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.Generic.IList%601>、<xref:System.Collections.Generic.ICollection%601>、<xref:System.Collections.Generic.IReadOnlyCollection%601> 或 <xref:System.Collections.Generic.IReadOnlyList%601>，則 `T[]` 和 <xref:System.Collections.Generic.List%601> 會標示 `Serialize` 原則，但介面類型沒有任何成員會標示 `Serialize` 原則。

- 如果類型是 <xref:System.Collections.Generic.List%601>，則沒有任何類型成員會標示 `Serialize` 原則。

- 如果類型是 <xref:System.Collections.Generic.IDictionary%602>，則 <xref:System.Collections.Generic.Dictionary%602> 會標示 `Serialize` 原則， 但沒有任何類型成員會標示 `Serialize` 原則。

- 如果類型是 <xref:System.Collections.Generic.Dictionary%602>，則沒有任何類型成員會標示 `Serialize` 原則。

- 如果類型實作 <xref:System.Collections.Generic.IDictionary%602>，則 `TKey` 和 `TValue` 會標示 `Serialize` 原則。

- 每個建構函式、每個屬性存取子和每個欄位都會標示 `Serialize` 原則。

將 `Serialize` 原則套用至方法牽涉到下列原則變更：

- 包含類型會標示 `Serialize` 原則。

- 方法的傳回型別會標示 `Serialize` 原則。

將 `Serialize` 原則套用至欄位牽涉到下列原則變更：

- 包含類型會標示 `Serialize` 原則。

- 欄位的類型會標示 `Serialize` 原則。

#### <a name="the-effect-of-xmlserializer-datacontractserializer-and-datacontractjsonserializer-policies"></a>XmlSerializer、 DataContractSerializer 和 DataContractJsonSerializer 原則的效果

不同於`Serialize`原則，主要用於反映型序列化程式，這<xref:System.Xml.Serialization.XmlSerializer>， <xref:System.Runtime.Serialization.DataContractSerializer>，和<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>原則用來啟用.NET Native 工具鏈已知的序列化程式的一組。 這些序列化程式不是使用反映來實作，但是可以用類似可反映式類型的方法，來判斷可以在執行階段序列化的類型集。

將這些原則的其中之一套用至類型，可讓該類型以相符的序列化程式來進行序列化。 此外，序列化引擎可以用靜態方式判斷為需要序列化的任何類型，也都可以序列化。

這些原則對方法或欄位沒有任何效果。

如需詳細資訊，請參閱[將您的 Windows 市集應用程式移轉至 .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)中的＜序列化程式的差異＞一節。

## <a name="see-also"></a>另請參閱

- [執行階段指示詞項目](../../../docs/framework/net-native/runtime-directive-elements.md)
- [反映和 .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md)
