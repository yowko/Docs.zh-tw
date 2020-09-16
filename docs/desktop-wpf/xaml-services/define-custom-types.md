---
title: 定義可搭配 .NET XAML 服務使用的自訂類型
ms.date: 03/30/2017
helpviewer_keywords:
- defining custom types [XAML Services]
ms.assetid: c2667cbd-2f46-4a7f-9dfc-53696e35e8e4
ms.openlocfilehash: 2c0578b5397172814c708706173c69ef69f91b2a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551774"
---
# <a name="define-custom-types-for-use-with-net-xaml-services"></a>定義搭配 .NET XAML 服務使用的自訂類型

當您定義屬於商務物件的自訂類型，或是沒有相依于特定架構的類型時，可以遵循 XAML 的一些最佳作法。 如果您遵循這些做法，.NET XAML 服務及其 XAML 讀取器和 XAML 寫入器可以探索您類型的 XAML 特性，並使用 XAML 型別系統在 XAML 節點資料流程中提供適當的標記法。 本主題說明型別定義、成員定義以及型別或成員的 CLR 類型的最佳作法。

## <a name="constructor-patterns-and-type-definitions-for-xaml"></a>XAML 的函式模式和類型定義

若要在 XAML 中具現化為物件元素，自訂類別必須符合下列需求：

- 自訂類別必須是公用的，而且必須公開無參數公用的函式。 (如需結構相關附註，請參閱下節)。

- 自訂類別不得為嵌套類別。 在完整名稱路徑中的額外「點」讓類別命名空間的除法不明確，並干擾其他 XAML 功能，例如附加屬性。
如果物件可以具現化為物件專案，則建立的物件可以填滿將物件做為其基礎型別的任何屬性（property element）形式的屬性（property element）。

如果您啟用值轉換器，您仍然可以針對不符合這些準則的類型提供物件值。 如需詳細資訊，請參閱 [XAML 的類型轉換器和標記延伸](type-converters-and-markup-extensions.md)。

### <a name="structures"></a>結構

結構一律可以透過 CLR 定義在 XAML 中進行。 這是因為 CLR 編譯器會隱含地為結構建立無參數的函式。 這個函式會將所有屬性值初始化為其預設值。

在某些情況下，不需要結構的預設結構行為。 這可能是因為結構的目的是要將值填滿，並且在概念上以聯集的方式運作。 以聯集的形式，包含的值可能會有互斥的解讀，因此不會設定其任何屬性。 WPF 詞彙中的這類結構範例為 <xref:System.Windows.GridLength> 。 這類結構應該採用型別轉換子，藉由使用可建立結構值之不同解讀或模式的字串慣例，以屬性形式表示值。 此結構也應該透過非參數的函式來公開程式碼結構的類似行為。

### <a name="interfaces"></a>介面

介面可以用來做為成員的基礎類型。 XAML 類型系統會檢查可指派的清單，並預期以值形式提供的物件可以指派給介面。 如果有相關的可指派型別支援 XAML 結構需求，就不需要將介面呈現為 XAML 型別。

### <a name="factory-methods"></a>Factory 方法

Factory 方法是 XAML 2009 功能。 它們會修改物件必須具有無參數的函式的 XAML 原則。 本文中未記載 Factory 方法。 請參閱 [x:FactoryMethod](xfactorymethod-directive.md)指示詞。

## <a name="enumerations"></a>列舉

列舉具有 XAML 原生類型轉換行為。 XAML 中指定的列舉常數名稱是根據基礎列舉型別來解析，並且將列舉值傳回給 XAML 物件寫入器。

XAML 針對已套用的列舉支援旗標樣式用法 <xref:System.FlagsAttribute> 。 如需詳細資訊，請參閱 [XAML 語法的詳細](/dotnet/desktop/wpf/advanced/xaml-syntax-in-detail)資訊。  ([Xaml 語法的詳細](/dotnet/desktop/wpf/advanced/xaml-syntax-in-detail) 資訊是針對 WPF 物件撰寫的，但該主題中大部分的資訊都與特定執行架構無關的 xaml 有關。 ) 

## <a name="member-definitions"></a>成員定義

類型可以定義 XAML 用法的成員。 類型可以定義可供 XAML 使用的成員，即使該特定型別不是 XAML 可用也是一樣。 這是可能的，因為 CLR 繼承。 只要有一些繼承成員的型別支援 XAML 使用方式做為型別，而成員支援其基礎類型的 XAML 使用方式，或有原生 XAML 語法可用，該成員就可以使用 XAML。

### <a name="properties"></a>屬性

如果您使用一般 CLR 和存取子模式和語言適當的 keywording，將屬性定義為公用 CLR 屬性， `get` `set` XAML 型別系統可以將屬性報告為具有提供給屬性之適當資訊的成員 <xref:System.Xaml.XamlMember> ，例如 <xref:System.Xaml.XamlMember.IsReadPublic%2A> 和 <xref:System.Xaml.XamlMember.IsWritePublic%2A> 。

特定屬性可以藉由套用來啟用文字語法 <xref:System.ComponentModel.TypeConverterAttribute> 。 如需詳細資訊，請參閱 [XAML 的類型轉換器和標記延伸](type-converters-and-markup-extensions.md)。

如果沒有文字語法或原生 XAML 轉換，而且沒有進一步的間接取值（例如標記延伸使用方式），則在 XAML 型別系統中 (的屬性型別， <xref:System.Xaml.XamlMember.TargetType%2A>) 必須能夠將目標型別視為 CLR 型別，以將實例傳回 xaml 物件寫入器。

如果使用 XAML 2009，如果不符合先前的考慮， [X:Reference 標記延伸](xreference-markup-extension.md) 可以用來提供值;不過，這比型別定義問題更是使用問題。

### <a name="events"></a>事件

如果您將事件定義為公用 CLR 事件，XAML 型別系統可以將附隨報告為具有 as 的 <xref:System.Xaml.XamlMember.IsEvent%2A> 成員 `true` 。 連接事件處理常式不在 .NET XAML 服務功能的範圍內;線路會留給特定的架構和實施。

### <a name="methods"></a>方法

方法的內嵌程式碼不是預設的 XAML 功能。 在大多數情況下，您不會直接從 XAML 參考方法成員，而 XAML 中方法的角色只是提供對特定 XAML 模式的支援。 [x:FactoryMethod](xfactorymethod-directive.md) 指示詞是例外狀況。

### <a name="fields"></a>欄位

CLR 設計方針不鼓勵非靜態欄位。 針對靜態欄位，您只能透過 [X:Static 標記延伸](xstatic-markup-extension.md)來存取靜態域值;在此情況下，您不會在 CLR 定義中執行任何特殊作業來公開 [x:Static](xstatic-markup-extension.md) 使用的欄位。

## <a name="attachable-members"></a>可附加成員

可附加的成員會透過定義型別的存取子方法模式，對 XAML 公開。 定義型別本身不需要當做物件使用 XAML。 事實上，常見的模式是宣告服務類別，其角色是擁有可附加的成員並執行相關的行為，但不提供任何其他功能（例如 UI 標記法）。 在下列各節中，預留位置 *屬性* 名稱代表可附加成員的名稱。 該名稱在 [XamlName 文法](xamlname-grammar.md)中必須是有效的。

請注意這些模式與類型的其他方法之間的名稱衝突。 如果有符合其中一個模式的成員存在，則它可以被 XAML 處理器視為可附加的成員使用路徑，即使這不是您的目的。

#### <a name="the-getpropertyname-accessor"></a>GetPropertyName 存取子

存取子的簽章 `GetPropertyName` 必須是：

`public static object GetPropertyName(object target)`

- `target` 物件可以指定為實作中的更特定類型。 您可以使用此值來限定可附加成員的使用方式;預期範圍之外的使用方式將會擲回不正確轉換例外狀況，然後由 XAML 剖析錯誤呈現。 參數名稱不是必要的 `target` ，但 `target` 在大部分的執行中依慣例命名。

- 傳回值可以指定為實作中的更特定類型。

若要 <xref:System.ComponentModel.TypeConverter> 針對可附加成員的屬性用法支援啟用的文字語法，請套用 <xref:System.ComponentModel.TypeConverterAttribute> 至存取子 `GetPropertyName` 。 套用至 `get` 而不是 `set` 直覺化; 不過，這個慣例可支援可序列化之唯讀可附加成員的概念，在設計工具案例中很有用。

#### <a name="the-setpropertyname-accessor"></a>SetPropertyName 存取子

存取子的簽章 `SetPropertyName` 必須是：

`public static void SetPropertyName(object target, object value)`

- `target`您可以將物件指定為您的實作為中的更特定類型，具有與上一節所述相同的邏輯和結果。

- `value` 物件可以指定為實作中的更特定類型。

請記住，這個方法的值是來自 XAML 使用方式的輸入，通常是在屬性表單中。 在屬性表單中，必須有 text 語法的值轉換器支援，而且您可以在 s 存取子上進行屬性 `GetPropertyName` 。

### <a name="attachable-member-stores"></a>可附加的成員存放區

存取子方法通常不足以提供方法，將可附加的成員值放入物件圖形中，或從物件圖形取出值並正確地加以序列化。 若要提供這項功能，先前存取子簽章 `target` 中的物件必須能夠儲存值。 儲存機制應該與可附加的成員主體一致，該成員可附加至可附加成員不在成員清單中的目標。 .NET XAML 服務透過 Api 和提供可附加的成員存放區的實作為方法 <xref:System.Xaml.IAttachedPropertyStore> <xref:System.Xaml.AttachablePropertyServices> 。 <xref:System.Xaml.IAttachedPropertyStore> XAML 寫入器會使用來探索存放區的執行，而且應該在存取子的類型上執行 `target` 。 靜態 <xref:System.Xaml.AttachablePropertyServices> api 用於存取子的主體內，並由其參考可附加的成員 <xref:System.Xaml.AttachableMemberIdentifier> 。

## <a name="xaml-related-clr-attributes"></a>XAML 相關 CLR 屬性

正確地將型別、成員和元件的特性化，是為了將 XAML 類型系統資訊回報給 .NET XAML 服務的重要。 如果適用下列其中一種情況，則報告 XAML 類型系統資訊是相關的：

- 您想要搭配直接以 .NET XAML 服務 XAML 讀取器和 XAML 寫入器為基礎的 XAML 系統使用類型。
- 您可以根據 xaml 讀取器和 XAML 寫入器，定義或使用以 XAML 為基礎的架構。

如需與自訂類型的 XAML 支援相關之每個 XAML 相關屬性的清單，請參閱 [自訂類型和程式庫的 Xaml 相關 CLR 屬性](clr-attributes-with-custom-types-and-libraries.md)。

## <a name="usage"></a>使用方式

使用自訂類型時，標記作者必須針對包含自訂類型的元件和 CLR 命名空間對應前置詞。 本主題未記載此程式。

## <a name="access-level"></a>存取層級

XAML 提供載入和具現化具有存取層級之類型的方法 `internal` 。 提供這項功能的目的是讓使用者程式碼可以定義自己的型別，然後從同時也屬於相同使用者程式碼範圍的標記將這些類別具現化。

WPF 中的一個範例，就是當使用者程式碼定義了，其 <xref:System.Windows.Controls.UserControl> 目的是要做為重構 UI 行為的方式，但不是任何可能的擴充機制的一部分，因為宣告支援的類別具有 `public` 存取層級。 <xref:System.Windows.Controls.UserControl> `internal` 如果支援的程式碼編譯成相同的元件，而這些程式碼會被視為 XAML 型別，則可以使用存取權來宣告這類。

對於在完全信任和使用下載入 XAML 的應用程式 <xref:System.Xaml.XamlObjectWriter> ， `internal` 一律會啟用以存取層級載入類別的功能。

針對在部分信任下載入 XAML 的應用程式，您可以使用 API 來控制存取層級的特性 <xref:System.Xaml.Permissions.XamlAccessLevel> 。 此外，延遲機制 (例如 WPF 範本系統) 必須能夠傳播任何存取層級許可權，並保留這些許可權以進行最終的執行時間評估;這會藉由傳遞資訊在內部處理 <xref:System.Xaml.Permissions.XamlAccessLevel> 。

### <a name="wpf-implementation"></a>WPF 執行

WPF XAML 使用部分信任存取模型，其中如果 BAML 是在部分信任下載入，則會限制為 <xref:System.Xaml.Permissions.XamlAccessLevel.AssemblyAccessTo%2A> baml 來源元件的存取權。 針對延遲，WPF 會使用 <xref:System.Xaml.IXamlObjectWriterFactory.GetParentSettings%2A?displayProperty=nameWithType> 做為傳遞存取層級資訊的機制。

在 WPF XAML 術語中， *內部型* 別是由相同元件所定義的型別，也包括參考的 XAML。 這類型別可透過 XAML 命名空間進行對應，該命名空間會刻意省略對應的元件 = 部分，例如 `xmlns:local="clr-namespace:WPFApplication1"` 。 如果 BAML 參考內部型別，而該型別具有 `internal` 存取層級， `GeneratedInternalTypeHelper` 則會產生元件的類別。 如果您想要避免 `GeneratedInternalTypeHelper` ，您必須使用 `public` 存取層級，或必須將相關的類別納入不同的元件，並使該元件相依。

## <a name="see-also"></a>另請參閱

- [自訂類型和程式庫的 XAML 相關 CLR 屬性](clr-attributes-with-custom-types-and-libraries.md)
- [XAML 服務](../../../api/index.md)
