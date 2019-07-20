---
title: 定義可搭配 .NET Framework XAML 服務使用的自訂類型
ms.date: 03/30/2017
helpviewer_keywords:
- defining custom types [XAML Services]
ms.assetid: c2667cbd-2f46-4a7f-9dfc-53696e35e8e4
ms.openlocfilehash: e563c0d7e5113d55d4b942fb1d175a64f5b71abc
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364302"
---
# <a name="defining-custom-types-for-use-with-net-framework-xaml-services"></a>定義可搭配 .NET Framework XAML 服務使用的自訂類型
當您定義的自訂類型為商務物件, 或其類型與特定架構沒有相依性時, 您可以遵循 XAML 的某些最佳作法。 如果您遵循這些做法, .NET Framework XAML 服務及其 XAML 讀取器和 XAML 撰寫者可以探索型別的 XAML 特性, 並使用 XAML 型別系統, 在 XAML 節點資料流程中提供適當的標記法。 本主題描述類型定義、成員定義以及類型或成員之 CLR 的最大型別的最佳作法。  
  
## <a name="constructor-patterns-and-type-definitions-for-xaml"></a>XAML 的函數模式和類型定義  
 若要在 XAML 中具現化為物件元素, 自訂類別必須符合下列需求:  
  
- 自訂類別必須是公用的, 而且必須公開預設的 (無參數) 公用函數。 (如需結構相關附註，請參閱下節)。  
  
- 自訂類別不得為嵌套類別。 在完整名稱路徑中的額外「點」會使類別命名空間相除不明確, 並干擾其他 XAML 功能, 例如附加屬性。  
  
 如果物件可以具現化為物件專案, 則所建立的物件可以填入任何屬性的屬性專案表單, 這些屬性會將物件當做其基礎類型。  
  
 如果您啟用值轉換器, 仍然可以針對不符合這些準則的類型提供物件值。 如需詳細資訊, 請參閱[XAML 的類型轉換器和標記延伸](type-converters-and-markup-extensions-for-xaml.md)。  
  
### <a name="structures"></a>結構  
 結構一律能夠在 XAML 中以 CLR 定義來進行構造。 這是因為 CLR 編譯器會隱含地建立結構的無參數的函式。 此函式會將所有屬性值初始化為其預設值。  
  
 在某些情況下, 不需要結構的預設結構行為。 這可能是因為結構是用來填滿值, 並在概念上當做聯集來運作。 做為聯集, 包含的值可能會有互斥的解讀, 因此無法設定其任何屬性。 在 WPF 詞彙中, 這類結構的範例是<xref:System.Windows.GridLength>。 這類結構應該會執行類型轉換器, 以便使用可建立結構值之不同解讀或模式的字串慣例, 以屬性形式表示值。 結構也應該透過非無參數的函式來公開程式碼結構的類似行為。  
  
### <a name="interfaces"></a>介面  
 介面可用來做為成員的基礎類型。 XAML 型別系統會檢查可指派的清單, 並預期當做值提供的物件可以指派給介面。 只要相關的可指派型別支援 XAML 結構需求, 就不能將介面呈現為 XAML 型別的概念。  
  
### <a name="factory-methods"></a>Factory 方法  
 Factory 方法是 XAML 2009 功能。 它們會修改物件必須具有無參數的構造函式的 XAML 原則。 Factory 方法未記載于本主題中。 請參閱[x:FactoryMethod](x-factorymethod-directive.md)指示詞。  
  
## <a name="enumerations"></a>列舉  
 列舉具有 XAML 原生類型轉換行為。 XAML 中指定的列舉常數名稱會針對基礎列舉型別解析, 並將列舉值傳回給 XAML 物件寫入器。  
  
 XAML 針對已套用的列舉, 支援旗標<xref:System.FlagsAttribute>樣式的使用方式。 如需詳細資訊, 請參閱[XAML 語法詳細資料](../wpf/advanced/xaml-syntax-in-detail.md)。 ([詳細說明 Xaml 語法](../wpf/advanced/xaml-syntax-in-detail.md)是針對 WPF 物件所撰寫, 但該主題中的大部分資訊都與特定的執行架構無關的 xaml 有關)。  
  
## <a name="member-definitions"></a>成員定義  
 類型可以定義 XAML 使用方式的成員。 定義可使用 XAML 之成員的類型有可能, 即使該特定類型不是 XAML 可用也一樣。 這是可能的, 因為 CLR 繼承。 只要某些繼承成員的型別支援 XAML 使用方式做為型別, 而且該成員支援其基礎型別的 XAML 用法, 或有可用的原生 XAML 語法, 該成員就能使用 XAML。  
  
### <a name="properties"></a>屬性  
 如果您使用一般的 clr `get`和`set`存取子模式以及語言適當的 keywording, 將屬性定義為公用 clr 屬性, XAML 類型系統可以將屬性報告為具有提供之適當資訊的成員<xref:System.Xaml.XamlMember>屬性,<xref:System.Xaml.XamlMember.IsReadPublic%2A>例如和<xref:System.Xaml.XamlMember.IsWritePublic%2A>。  
  
 特定屬性可以藉由套用來<xref:System.ComponentModel.TypeConverterAttribute>啟用文字語法。 如需詳細資訊, 請參閱[XAML 的類型轉換器和標記延伸](type-converters-and-markup-extensions-for-xaml.md)。  
  
 如果沒有文字語法或原生 XAML 轉換, 而且沒有進一步的間接取值 (例如標記延伸使用方式), 屬性的類型 (<xref:System.Xaml.XamlMember.TargetType%2A>在 xaml 類型系統中) 必須藉由將 t 視為 xaml 物件寫入器,目標 a) 類型做為 CLR 類型。  
  
 如果使用 XAML 2009, 如果不符合先前的考慮, 則可以使用[X:Reference 標記延伸](x-reference-markup-extension.md)來提供值。不過, 這比類型定義問題更有使用問題。  
  
### <a name="events"></a>事件  
 如果您將事件定義為公用 CLR 事件, XAML 類型系統可以使用<xref:System.Xaml.XamlMember.IsEvent%2A>做為`true`成員, 將附隨報告為。 連接事件處理常式不在 .NET Framework XAML 服務功能的範圍內;這會留給特定的架構和實現。  
  
### <a name="methods"></a>方法  
 方法的內嵌程式碼不是預設的 XAML 功能。 在大部分情況下, 您不會直接從 XAML 參考方法成員, 而 XAML 中的方法角色只是為了提供特定 XAML 模式的支援。 [x:FactoryMethod](x-factorymethod-directive.md)指示詞是例外狀況。  
  
### <a name="fields"></a>欄位  
 CLR 設計方針不鼓勵非靜態欄位。 對於靜態欄位, 您只能透過[X:Static 標記延伸](x-static-markup-extension.md)來存取靜態域值。在此情況下, 您不會在 CLR 定義中執行任何特殊動作, 以公開[x:Static](x-static-markup-extension.md)使用方式的欄位。  
  
## <a name="attachable-members"></a>可附加成員  
 可附加的成員會透過定義類型上的存取子方法模式, 向 XAML 公開。 定義類型本身不需要是 XAML 可用的物件。 事實上, 常見的模式是宣告一個服務類別, 其角色是要擁有可附加的成員並執行相關的行為, 但不提供其他功能, 例如 UI 標記法。 在下列各節中, 預留位置*PropertyName*代表可附加成員的名稱。 該名稱在[XamlName 文法](xamlname-grammar.md)中必須是有效的。  
  
 請注意這些模式和類型的其他方法之間的名稱衝突。 如果符合其中一種模式的成員存在, 則即使不是您的意圖, 也可以透過 XAML 處理器將它解讀為可附加的成員使用路徑。  
  
#### <a name="the-getpropertyname-accessor"></a>GetPropertyName 存取子  
 `Get`<屬性名稱>  存取子的簽章必須是︰  
  
 `public static object Get` <屬性名稱>  `(object`  `target` `)`  
  
- `target` 物件可以指定為實作中的更特定類型。 您可以使用此值來界定可附加成員的使用範圍;在您預期範圍外的使用方式將會擲回不正確轉換例外狀況, 然後由 XAML 剖析錯誤呈現。 參數名稱`target`不是必要條件, 但在大部分的程式`target`中都是依照慣例來命名。  
  
- 傳回值可以指定為實作中的更特定類型。  
  
 若要支援<xref:System.ComponentModel.TypeConverter>可附加成員之屬性使用方式的已啟用文字語法<xref:System.ComponentModel.TypeConverterAttribute> , 請`Get`將套用至*PropertyName*存取子。 套用至`get`而不`set`是可能會 nonintuitive; 不過, 這個慣例可以支援可序列化之唯讀可附加成員的概念, 這在設計工具案例中很有用。  
  
#### <a name="the-setpropertyname-accessor"></a>SetPropertyName 存取子  
 Set*PropertyName*存取子的簽章必須是:  
  
 `public static void Set` <屬性名稱>  `(object`  `target` `, object`  `value` `)`  
  
- 在您的執行中, 可以將物件指定為更特定的類型,且具有與上一節中所述相同的邏輯和結果。`target`  
  
- `value` 物件可以指定為實作中的更特定類型。  
  
 請記住, 這個方法的值是來自 XAML 用法的輸入, 通常是以屬性形式呈現。 在屬性形式中, 文字語法必須有值轉換器支援, 而且您可以在*PropertyName*存取`Get`子上使用屬性。  
  
### <a name="attachable-member-stores"></a>可附加的成員存放區  
 存取子方法通常不足以提供將可附加的成員值放入物件圖形的方法, 或是從物件圖形抓取值並正確地加以序列化。 為了提供這項功能, `target`先前存取子簽章中的物件必須能夠儲存值。 儲存機制應該與可附加的成員 (可附加的成員不在成員清單中的目標) 保持一致。 .NET Framework XAML 服務會透過 api <xref:System.Xaml.IAttachedPropertyStore>和<xref:System.Xaml.AttachablePropertyServices>提供可附加成員存放區的執行技術。 <xref:System.Xaml.IAttachedPropertyStore>XAML 寫入器會使用來探索存放區的執行, 而且應該在做為`target`存取子之的類型上執行。 靜態<xref:System.Xaml.AttachablePropertyServices> api 會在存取子的主體內使用, 並透過其<xref:System.Xaml.AttachableMemberIdentifier>參考可附加的成員。  
  
## <a name="xaml-related-clr-attributes"></a>XAML 相關的 CLR 屬性  
 將 XAML 類型系統資訊報告為 .NET Framework XAML 服務時, 正確地將類型、成員和元件的特性化會很重要。 如果您想要讓型別與直接以 .NET Framework XAML 服務 XAML 讀取器和 XAML 寫入器為基礎的 XAML 系統搭配使用, 或如果您定義或使用以 xaml 讀取器和 XAML 寫入器為基礎的 xaml 型架構, 這就是相關的。  
  
 如需與自訂類型的 XAML 支援相關之每個 XAML 相關屬性的清單, 請參閱[自訂類型和程式庫的 Xaml 相關 CLR 屬性](xaml-related-clr-attributes-for-custom-types-and-libraries.md)。  
  
## <a name="usage"></a>使用量  
 使用自訂類型時, 標記作者必須對應包含自訂類型之元件與 CLR 命名空間的前置詞。 本主題未記載此程式。  
  
## <a name="access-level"></a>存取層級  
 XAML 提供載入及具現化具有`internal`存取層級之類型的方法。 提供這項功能的目的是讓使用者程式碼可以定義自己的型別, 然後從同時也屬於相同使用者程式碼範圍的標記, 將這些類別具現化。  
  
 WPF 的一個範例, 就是當使用者程式<xref:System.Windows.Controls.UserControl>代碼定義, 其目的是要用來重構 UI 行為, 而不是使用`public`存取層級宣告支援的類別時, 可能會隱含的任何可能擴充機制的一部分。 如果支援程式碼編譯成`internal`與當做 XAML 類型參考的相同元件, 則可以使用存取來宣告這類。<xref:System.Windows.Controls.UserControl>  
  
 對於在完全信任下載入 XAML 並使用<xref:System.Xaml.XamlObjectWriter>的應用程式, 一律會啟用載入具有存取層級的`internal`類別。  
  
 對於在部分信任下載入 XAML 的應用程式, 您可以使用<xref:System.Xaml.Permissions.XamlAccessLevel> API 來控制存取層級的特性。 此外, 延遲機制 (例如 WPF 範本系統) 必須能夠傳播任何存取層級許可權, 並保留它們以進行最終的執行時間評估;這是藉由傳遞<xref:System.Xaml.Permissions.XamlAccessLevel>資訊在內部處理。  
  
### <a name="wpf-implementation"></a>WPF 執行  
 WPF XAML 會使用部分信任存取模型, 其中如果 baml 是在部分信任下載入, 則對屬於<xref:System.Xaml.Permissions.XamlAccessLevel.AssemblyAccessTo%2A> BAML 來源的元件而言, 存取權會受到限制。 對於延遲, WPF 會<xref:System.Xaml.IXamlObjectWriterFactory.GetParentSettings%2A?displayProperty=nameWithType>使用做為傳遞存取層級資訊的機制。  
  
 在 WPF XAML 術語中,*內部類型*是由相同元件所定義的類型, 其中也包含參考 XAML。 這類型別可以透過 XAML 命名空間來對應, 此命名空間故意省略對應的元件 = 部分, `xmlns:local="clr-namespace:WPFApplication1"`例如。  如果 BAML 參考內部型別, 而該型`internal`別具有存取層級, `GeneratedInternalTypeHelper`這就會產生元件的類別。 如果您想要避免`GeneratedInternalTypeHelper`, 您必須使用`public`存取層級, 或必須將相關的類別納入個別的元件中, 並使該元件相依。  
  
## <a name="see-also"></a>另請參閱

- [自訂類型和程式庫的 XAML 相關 CLR 屬性](xaml-related-clr-attributes-for-custom-types-and-libraries.md)
- [XAML Services](index.md)
