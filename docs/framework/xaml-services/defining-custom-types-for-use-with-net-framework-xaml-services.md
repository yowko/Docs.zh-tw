---
title: 定義可搭配 .NET Framework XAML 服務使用的自訂類型
ms.date: 03/30/2017
helpviewer_keywords:
- defining custom types [XAML Services]
ms.assetid: c2667cbd-2f46-4a7f-9dfc-53696e35e8e4
ms.openlocfilehash: 672660f73e9e6faf25985a651290e979f9deb9f4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492503"
---
# <a name="defining-custom-types-for-use-with-net-framework-xaml-services"></a>定義可搭配 .NET Framework XAML 服務使用的自訂類型
當您定義了商務物件的自訂類型，或在特定架構上沒有相依性的類型時，但也有特定的 XAML，您可以遵循的最佳作法。 如果您遵循這些作法時，.NET Framework XAML 服務及其 XAML 讀取器和 XAML 寫入器可以探索您類型的 XAML 特性，並提供適當的表示，使用 XAML 型別系統的 XAML 節點資料流中。 本主題說明類型定義、 成員定義，以及 CLR 屬性的型別或成員的最佳作法。  
  
## <a name="constructor-patterns-and-type-definitions-for-xaml"></a>建構函式模式和 XAML 的類型定義  
 若要具現化為物件項目在 XAML 中，自訂類別必須符合下列需求：  
  
-   自訂類別必須是公用，而且必須公開 （expose） 的預設 （無參數） 公用建構函式。 (如需結構相關附註，請參閱下節)。  
  
-   自訂類別不能巢狀的類別。 「 點 」 的完整名稱的路徑中的額外類別命名空間除法模稜兩可，並會干擾其他 XAML 功能，例如附加屬性。  
  
 如果物件可以具現化為物件項目中，所建立的物件可以填入屬性項目表單的任何採用物件作為其基礎類型的屬性。  
  
 您仍然可以提供物件的值類型不符合這些條件，如果您啟用的值轉換器。 如需詳細資訊，請參閱 < [Type Converters and Markup Extensions for XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)。  
  
### <a name="structures"></a>結構  
 結構都可以建構在 XAML 中，CLR 定義。 這是因為 CLR 編譯器隱含建立結構的預設建構函式。 這個建構函式會初始化為其預設值的所有屬性值。  
  
 在某些情況下，您可能不想要的結構的預設建構行為。 這可能是因為結構為了在概念上，為聯集填入值和函式。 聯集，包含的值可能會有互斥解譯，並因此，其屬性都是可設定。 舉例來說，這種結構中的 WPF 詞彙<xref:System.Windows.GridLength>。 這類結構應該實作類型轉換器，可以使用建立的不同解譯或模式的結構值的字串慣例來以屬性形式表示的值。 此結構也應該透過非預設建構函式進行程式碼建構來公開類似行為。  
  
### <a name="interfaces"></a>介面  
 介面可用來當做基礎類型的成員。 XAML 類型系統會檢查指派的清單，並預期提供做為值的物件都可以指派給介面。 沒有介面如何必須呈現為 XAML 型別，只要相關的可指派型別支援 XAML 建構需求的概念。  
  
### <a name="factory-methods"></a>Factory 方法  
 Factory 方法，是 XAML 2009 功能。 它們修改的物件都必須有預設建構函式的 XAML 原則。 本主題中未記載的 factory 方法。 請參閱[X:factorymethod 指示詞](../../../docs/framework/xaml-services/x-factorymethod-directive.md)。  
  
## <a name="enumerations"></a>列舉  
 列舉型別具有 XAML 原生型別轉換行為。 在 XAML 中指定的列舉常數名稱對基礎的列舉型別，解決，而且傳回至 XAML 物件寫入器的列舉值。  
  
 XAML 支援列舉型別與旗標式使用量<xref:System.FlagsAttribute>套用。 如需詳細資訊，請參閱 < [XAML 語法詳細資料](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)。 ([XAML 語法詳細資料](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)的撰寫對 WPF 的對象，但大部分的該主題中的資訊是關於並非專屬於特定的實作架構的 XAML。)  
  
## <a name="member-definitions"></a>成員定義  
 類型可以定義 XAML 使用的成員。 可以定義成員，即使該特定的型別不是使用 XAML 的 XAML 使用的類型。 這可能是因為 CLR 繼承。 只要繼承成員的型別支援 XAML 用法，做為類型，且該成員支援 XAML 用法，其基礎類型，或有可用的原生 XAML 語法，該成員是 XAML 可用。  
  
### <a name="properties"></a>屬性  
 如果您定義屬性為公用的 CLR 屬性，使用一般的 CLR`get`和`set`存取子模式和適當語言 keywording，XAML 類型系統可以報告提供包含適當資訊的成員為屬性<xref:System.Xaml.XamlMember>屬性，例如<xref:System.Xaml.XamlMember.IsReadPublic%2A>和<xref:System.Xaml.XamlMember.IsWritePublic%2A>。  
  
 特定的屬性可以藉由套用可讓文字語法<xref:System.ComponentModel.TypeConverterAttribute>。 如需詳細資訊，請參閱 < [Type Converters and Markup Extensions for XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)。  
  
 沒有文字語法或原生 XAML 轉換，並進一步間接取值，例如標記延伸使用方式，屬性的型別不存在 (<xref:System.Xaml.XamlMember.TargetType%2A>中 XAML 類型系統) 必須能夠傳回給 XAML 物件寫入器的執行個體，藉由將 t為 CLR 型別 arget 型別。  
  
 如果使用 XAML 2009 [X:reference 標記延伸](../../../docs/framework/xaml-services/x-reference-markup-extension.md)可用來提供值，如果不符合先前的考量，不過，這是多個類型定義問題比使用問題。  
  
### <a name="events"></a>事件  
 如果您定義為公用的 CLR 事件的事件，XAML 類型系統可以做為成員與報告事件<xref:System.Xaml.XamlMember.IsEvent%2A>做為`true`。 傳入事件處理常式不是.NET Framework XAML 服務功能; 的範圍內這會保留給特定的架構和實作。  
  
### <a name="methods"></a>方法  
 方法的內嵌程式碼不是預設的 XAML 功能。 在大部分情況下您不要直接參照方法成員的 XAML，和方法，在 XAML 中的角色只是為了特定 XAML 模式提供支援。 [X:factorymethod 指示詞](../../../docs/framework/xaml-services/x-factorymethod-directive.md)例外狀況。  
  
### <a name="fields"></a>欄位  
 CLR 設計指導方針不鼓勵非靜態欄位。 對於靜態欄位，您可以存取靜態欄位值只能透過[X:static 標記延伸](../../../docs/framework/xaml-services/x-static-markup-extension.md); 在此情況下您在不進行任何 CLR 定義公開 （expose） 的欄位中的特殊[X:static](../../../docs/framework/xaml-services/x-static-markup-extension.md)使用方式。  
  
## <a name="attachable-members"></a>可附加成員  
 可附加成員會公開至 XAML 中，透過定義的類型存取子方法模式。 不需要定義的型別本身不會用作 XAML-物件。 事實上，常見的模式是以宣告的服務類別，其角色為自己的可附加成員及實作相關的行為，但不提供任何其他功能，例如 UI 表示法。 如下列章節中，將預留位置*PropertyName*代表您可附加成員的名稱。 該名稱必須是有效[XamlName 文法](../../../docs/framework/xaml-services/xamlname-grammar.md)。  
  
 留意這些模式和類型的其他方法之間的名稱衝突。 如果成員存在，並符合其中一個模式，它可以解譯為可附加成員用法路徑由 XAML 處理器即使這不是您的意圖。  
  
#### <a name="the-getpropertyname-accessor"></a>GetPropertyName 存取子  
 `Get`<屬性名稱> 存取子的簽章必須是︰  
  
 `public static object Get` <屬性名稱> `(object`  `target` `)`  
  
-   `target` 物件可以指定為實作中的更特定類型。 您可以使用這個限定範圍的使用量，您可附加成員;您預期的範圍之外的使用方式，就會擲回無效轉換例外狀況，然後呈現由 XAML 剖析錯誤。 參數名稱`target`並非必要，但名為`target`依照慣例，在大部分的實作。  
  
-   傳回值可以指定為實作中的更特定類型。  
  
 若要支援<xref:System.ComponentModel.TypeConverter>套用的屬性使用方式的可附加成員，啟用的文字語法<xref:System.ComponentModel.TypeConverterAttribute>要`Get` *PropertyName*存取子。 將套用至`get`而不是`set`似乎不被察覺; 不過，這個慣例可以支援這個概念的唯讀狀態可附加成員都是可序列化，這是在設計工具的情況下很有用。  
  
#### <a name="the-setpropertyname-accessor"></a>SetPropertyName 存取子  
 集合的簽章*PropertyName*存取子必須是：  
  
 `public static void Set` <屬性名稱> `(object`  `target` `, object`  `value` `)`  
  
-   `target`物件可以指定為在您實作中，使用相同的邏輯和結果的更特定類型，如上一節所述。  
  
-   `value` 物件可以指定為實作中的更特定類型。  
  
 請記住，此方法的值來自 XAML 用法，通常是以屬性形式的輸入。 從屬性形式必須是值轉換子支援文字語法中，而且您屬性`Get` *PropertyName*存取子。  
  
### <a name="attachable-member-stores"></a>可附加成員存放區  
 存取子方法，還通常不足以提供可附加成員的值放入物件圖形，或以擷取物件圖形的值，並將其序列化到正確的方法。 若要提供這項功能，`target`的上一個存取子的簽章中的物件必須能夠儲存的值。 儲存機制應該與該成員是可附加至目標的可附加成員不在成員清單中的可附加成員原則一致。 .NET framework XAML 服務提供的實作方法，針對可附加成員存放區透過 Api<xref:System.Xaml.IAttachedPropertyStore>和<xref:System.Xaml.AttachablePropertyServices>。 <xref:System.Xaml.IAttachedPropertyStore> 可由 XAML 寫入器來探索存放區實作中，並應該是類型上實作`target`存取子。 靜態<xref:System.Xaml.AttachablePropertyServices>Api 的存取子的主體內使用和的可附加成員是指其<xref:System.Xaml.AttachableMemberIdentifier>。  
  
## <a name="xaml-related-clr-attributes"></a>XAML 相關 CLR 屬性  
 正確設定其屬性，您的型別、 成員和組件是以.NET Framework XAML 服務 XAML 類型系統資訊 報告的順序很重要。 如果您想要您的型別，用於 XAML 系統直接根據.NET Framework XAML 服務 XAML 讀取器和 XAML 寫入器，或如果您要定義或使用這些 XAML 讀取器和 XAML 寫入器為基礎的 XAML 使用的架構，這是相關。  
  
 如需相關的 XAML 支援，您的自訂類型的每個 XAML 相關屬性的清單，請參閱[XAML-Related CLR 屬性的自訂型別和程式庫](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md)。  
  
## <a name="usage"></a>使用量  
 使用的自訂型別都需要標記作者必須對應包含自訂類型的組件和 CLR 命名空間的前置詞。 本主題不會詳細說明此程序。  
  
## <a name="access-level"></a>存取層級  
 XAML 會提供一個方法來載入並具現化具有型別`internal`存取層級。 這項功能被提供，讓使用者程式碼可以定義自己的類型，然後具現化這些類別也是相同的使用者程式碼範圍的一部分的標記。  
  
 WPF 的範例是，每當使用者程式碼會定義<xref:System.Windows.Controls.UserControl>，用來重構 UI 行為，但不是可能會隱含宣告支援的類別與任何可能的延伸模組機制的一部分`public`存取層級。 這類<xref:System.Windows.Controls.UserControl>可以使用宣告`internal`如果支援程式碼會編譯成相同的組件的參考為 XAML 型別存取。  
  
 在完全信任下載入 XAML，並使用的應用程式<xref:System.Xaml.XamlObjectWriter>，載入類別`internal`一律啟用的存取層級。  
  
 在部分信任環境中載入 XAML 的應用程式，您可以使用控制存取層級特性<xref:System.Xaml.Permissions.XamlAccessLevel>API。 此外，延遲機制 （例如 WPF 範本系統） 必須要能夠傳播任何存取層級的權限，並保留供最終的執行的階段評估;這在內部處理傳遞<xref:System.Xaml.Permissions.XamlAccessLevel>資訊。  
  
### <a name="wpf-implementation"></a>WPF 實作  
 WPF XAML 使用部分信任存取模型，如果 BAML 已載入在部分信任下，存取僅限於<xref:System.Xaml.Permissions.XamlAccessLevel.AssemblyAccessTo%2A>BAML 來源組件。 對於延遲，WPF 會使用<xref:System.Xaml.IXamlObjectWriterFactory.GetParentSettings%2A?displayProperty=nameWithType>做為傳遞的存取層級資訊的機制。  
  
 在 WPF XAML 術語*內部型別*是相同的組件也包含參考的 XAML 所定義的型別。 這種類型可以對應 XAML 命名空間，刻意省略組件 = 部分的對應，比方說， `xmlns:local="clr-namespace:WPFApplication1"`。  如果 BAML 參考內部的型別和型別具有`internal`存取層級，這會產生`GeneratedInternalTypeHelper`組件的類別。 如果您想要避免`GeneratedInternalTypeHelper`，您必須使用`public`存取層級，或必須納入個別的組件相關的類別，並將該組件相依。  
  
## <a name="see-also"></a>另請參閱
- [自訂類型和程式庫的 XAML 相關 CLR 屬性](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md)
- [XAML Services](../../../docs/framework/xaml-services/index.md)
