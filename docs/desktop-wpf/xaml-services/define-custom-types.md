---
title: 定義可搭配 .NET XAML 服務使用的自訂類型
ms.date: 03/30/2017
helpviewer_keywords:
- defining custom types [XAML Services]
ms.assetid: c2667cbd-2f46-4a7f-9dfc-53696e35e8e4
ms.openlocfilehash: ff7e4229450e801a6d618c5141efde8cdcbef03d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071854"
---
# <a name="define-custom-types-for-use-with-net-xaml-services"></a>定義為 .NET XAML 服務的自訂類型

當您定義業務物件或對特定框架不依賴的類型時,您可以遵循 XAML 的某些最佳做法。 如果您遵循這些實踐,.NET XAML 服務及其 XAML 讀取器和 XAML 編寫器可以發現您類型的 XAML 特徵,並使用 XAML 類型系統在 XAML 節點流中為其提供適當的表示形式。 本主題介紹類型定義、成員定義和類型或成員的 CLR 歸因的最佳做法。

## <a name="constructor-patterns-and-type-definitions-for-xaml"></a>XAML 的建構函式模式和類型定義

要在 XAML 中實體化為物件元素,自訂類必須滿足以下要求:

- 自定義類必須是公共的,並且必須公開無參數的公共構造函數。 (如需結構相關附註，請參閱下節)。

- 自定義類不能是嵌套類。 全名路徑中的額外"點"使類命名空間劃分不明確,並干擾其他 XAML 功能(如附加屬性)。
如果物件可以實例化為物件元素,則創建的物件可以填充將對象作為其基礎類型的任何屬性的屬性元素形式。

如果啟用值轉換器,仍可以為不符合這些標準的類型提供物件值。 有關詳細資訊,請參閱[XAML 的類型轉換器和標記延伸](type-converters-and-markup-extensions.md)。

### <a name="structures"></a>結構

結構始終能夠在 XAML 中透過 CLR 定義構造。 這是因為 CLR 編譯器隱式為結構創建了無參數構造函數。 此建構函數將所有屬性值初始化到其預設值。

在某些情況下,結構的預設構造行為是不需要的。 這可能是因為結構旨在填充值,並在概念上作為聯合進行函數。 作為聯合,包含的值可能具有互斥的解釋,因此,其屬性都不是可設置的。 WPF 字彙中這種結構的範例是<xref:System.Windows.GridLength>。 此類結構應實現類型轉換器,以便透過使用創建結構值的不同解釋或模式的字串約定,以屬性形式表示值。 結構還應通過非參數構造函數公開代碼構造的類似行為。

### <a name="interfaces"></a>介面

介面可用作成員的基礎類型。 XAML 類型系統檢查可分配清單,並期望作為值提供的物件可以分配給介面。 只要相關的可分配類型支援 XAML 建構要求,則對於介面必須作為 XAML 類型呈現的概念是沒有概念的。

### <a name="factory-methods"></a>工廠方法

工廠方法是 XAML 2009 功能。 它們修改了 XAML 原則,即物件必須具有無參數構造函數。 本文沒有記錄工廠方法。 請參考[x:工廠方法指令](xfactorymethod-directive.md)。

## <a name="enumerations"></a>列舉

枚舉具有 XAML 本機類型轉換行為。 根據基礎枚舉類型解析 XAML 中指定的枚舉常量名稱,並將枚舉值返回給 XAML 物件編寫器。

XAML<xref:System.FlagsAttribute>支援 應用的枚舉標記樣式用法。 有關詳細資訊,請參閱[XAML 語法詳細資訊](../../framework/wpf/advanced/xaml-syntax-in-detail.md)。 [(XAML 語法詳細](../../framework/wpf/advanced/xaml-syntax-in-detail.md)為 WPF 受眾編寫,但該主題中的大多數資訊與不特定於特定實現框架的 XAML 相關。

## <a name="member-definitions"></a>成員定義

類型可以為 XAML 使用定義成員。 類型可以定義 XAML 可用的成員,即使該特定類型不可用於 XAML。 這是可能的,因為CLR繼承。 只要繼承該成員的某些類型支援 XAML 使用作為類型,並且該成員支援其基礎類型的 XAML 用法或具有本機 XAML 語法可用,該成員即可用於 XAML。

### <a name="properties"></a>屬性

如果使用典型的`get`CLR 和訪問`set`模式以及 語言適當的關鍵字將屬性定義為公共 CLR 屬性,則 XAML 類型系統可以將該屬性<xref:System.Xaml.XamlMember>報告為成員<xref:System.Xaml.XamlMember.IsReadPublic%2A>,<xref:System.Xaml.XamlMember.IsWritePublic%2A>並提供有關 屬性(如和 )等屬性的適當資訊。

特定屬性可以透過<xref:System.ComponentModel.TypeConverterAttribute>應用 啟用文本語法來啟用文本語法。 有關詳細資訊,請參閱[XAML 的類型轉換器和標記延伸](type-converters-and-markup-extensions.md)。

在沒有文字語法或本機 XAML 轉換的情況下,在沒有進一步間接(如標記擴展用法)的情況下,屬性的<xref:System.Xaml.XamlMember.TargetType%2A>類型( 在 XAML 類型系統中)必須能夠將實例視為 CLR 類型,將實例返回到 XAML 物件編寫器。

如果使用 XAML 2009,則如果未滿足以前的注意事項,可以使用[x:參考標記擴展](xreference-markup-extension.md)提供值;但是,這更多的是使用問題,而不是類型定義問題。

### <a name="events"></a>事件

如果將事件定義為公共 CLR 事件,XAML 類型系統可以將事件<xref:System.Xaml.XamlMember.IsEvent%2A>報告為具有`true`的成員。 連接事件處理程式不在 .NET XAML 服務功能範圍內;因此,在 .NET XAML 服務功能範圍內,則對事件處理程序進行佈線。線路留給特定的框架和實現。

### <a name="methods"></a>方法

方法的內聯代碼不是預設的 XAML 功能。 在大多數情況下,您不會直接引用 XAML 中的方法成員,並且方法在 XAML 中的角色只是為特定的 XAML 模式提供支援。 [x:工廠方法指令](xfactorymethod-directive.md)是一個例外。

### <a name="fields"></a>欄位

CLR 設計指南阻止非靜態欄位。 對於靜態欄位,只能通過[x:靜態標記擴展](xstatic-markup-extension.md)訪問靜態欄位值。在這種情況下,您沒有在 CLR 定義中執行任何特殊操作來公開[x:靜態](xstatic-markup-extension.md)用法的欄位。

## <a name="attachable-members"></a>可附加成員

可附加成員通過定義類型上的訪問器方法模式向 XAML 公開。 定義類型本身不需要 XAML 作為物件可用。 實際上,一種常見模式是聲明服務類,其作用是擁有可附加成員並實現相關行為,但不提供其他函數,如 UI 表示形式。 對於以下部分,占位符*屬性名稱*表示可附加成員的名稱。 該名稱必須在[XamlName 語法](xamlname-grammar.md)中有效。

小心這些模式和類型的其他方法之間的名稱衝突。 如果存在與其中一種模式匹配的成員,則 XAML 處理器可以將其解釋為可附加成員使用路徑,即使這不是您的意圖。

#### <a name="the-getpropertyname-accessor"></a>取得屬性名稱存取器

存取器的`GetPropertyName`簽章 必須為:

`public static object GetPropertyName(object target)`

- `target` 物件可以指定為實作中的更特定類型。 您可以使用它來限定可附加成員的使用範圍;預期範圍以外的用法將引發無效強制轉換異常,然後由 XAML 分析錯誤顯示。 參數名稱`target`不是要求,但在大多數實現中按`target`約定 命名。

- 傳回值可以指定為實作中的更特定類型。

要支援<xref:System.ComponentModel.TypeConverter>啟用的文本語法,以便附加成員的屬性使用,請應用<xref:System.ComponentModel.TypeConverterAttribute>`GetPropertyName`於訪問器。 申請`get`,`set`而不是 可能看起來不直觀;但是,此約定可以支援可序列化的唯讀可附加成員的概念,這在設計器方案中很有用。

#### <a name="the-setpropertyname-accessor"></a>設定屬性名稱存取器

存取器的`SetPropertyName`簽章 必須為:

`public static void SetPropertyName(object target, object value)`

- 該`target`物件可以指定為實現中更具體的類型,其邏輯和後果與上一節所述相同。

- `value` 物件可以指定為實作中的更特定類型。

請記住,此方法的值是來自 XAML 用法的輸入,通常以屬性形式提供。 從屬性表單中,必須支援文字語法的值轉換器,並且對`GetPropertyName`s 訪問器的屬性。

### <a name="attachable-member-stores"></a>可附加會員商店

訪問器方法通常不足以提供將可附加成員值放入物件圖形的方法,或從物件圖中檢索值並正確序列化它們。 要提供此功能,`target`以前存取器簽名中的物件必須能夠儲存值。 儲存機制應符合可附加成員原則,即成員可附加到可附加成員不在成員清單中的目標。 .NET XAML 服務通過<xref:System.Xaml.IAttachedPropertyStore><xref:System.Xaml.AttachablePropertyServices>API 和 為可附加成員存儲提供了一種實現技術。 <xref:System.Xaml.IAttachedPropertyStore>XAML 編寫器用於發現存儲實現,並且應在訪問`target`器的類型上實現。 靜態<xref:System.Xaml.AttachablePropertyServices>API 在訪問器的正文中使用,並<xref:System.Xaml.AttachableMemberIdentifier>透過其引用可連接成員。

## <a name="xaml-related-clr-attributes"></a>與 XAML 相關的 CLR 屬性

正確配置類型、成員和程式集對於向 .NET XAML 服務報告 XAML 類型系統資訊非常重要。 如果適用以下任一情況,報告 XAML 類型系統資訊是相關的:

- 您希望類型與直接基於 .NET XAML 服務 XAML 服務讀取器和 XAML 寫入器的 XAML 系統一起使用。
- 您定義或使用基於這些 XAML 讀取器和 XAML 編寫器的 XAML 利用框架。

有關與自訂類型的 XAML 支援相關的每個 XAML 相關屬性的清單,請參閱[自訂類型和函式庫的 XAML 相關 CLR 屬性](clr-attributes-with-custom-types-and-libraries.md)。

## <a name="usage"></a>使用量

自訂類型的使用要求標記作者必須映射包含自訂類型的程式集和 CLR 命名空間的前置碼。 本主題中未記錄此過程。

## <a name="access-level"></a>存取層級

XAML 提供了一種載入和實例化`internal`具有 存取等級的類型的方法。 提供此功能,以便用戶代碼可以定義自己的類型,然後從也是同一用戶代碼作用域的標記實例化這些類。

WPF 的一個範例是,每當用戶代碼<xref:System.Windows.Controls.UserControl>定義旨在重構 UI 行為的方法時,而不是作為任何可能的擴展機制的一部分,這些擴展機制可能`public`通過聲明具有 訪問級別的支援類來暗示。 如果支援<xref:System.Windows.Controls.UserControl>程式碼編譯到`internal`引用 XAML 類型的同一程式集中,則可以透過權限宣告此類 。

對於在完全信任下載入 XAML<xref:System.Xaml.XamlObjectWriter>並使用的應用程式,始終`internal`啟用具有 訪問級別的載入類。

對於在部分信任下載入 XAML 的應用程式,<xref:System.Xaml.Permissions.XamlAccessLevel>可以使用 API 來控制存取等級特徵。 此外,延遲機制(如 WPF 範本系統)必須能夠傳播任何訪問級別許可權,並將其保留為最終的運行時評估;這通過傳遞資訊在<xref:System.Xaml.Permissions.XamlAccessLevel>內部處理。

### <a name="wpf-implementation"></a>WPF 實施

WPF XAML 使用部分信任訪問模型,其中如果BAML在部分信任下載入<xref:System.Xaml.Permissions.XamlAccessLevel.AssemblyAccessTo%2A>,則訪問僅限於作為BAML源的程式集。 對於延遲,WPF 用<xref:System.Xaml.IXamlObjectWriterFactory.GetParentSettings%2A?displayProperty=nameWithType>作 傳遞訪問級別資訊的機制。

在 WPF XAML 術語中,*內部類型*是由同一程式集定義的類型,該程式集還包括引用 XAML。 此類類型可以透過 XAML 命名空間映射,該命名空間有意省略映射的程式`xmlns:local="clr-namespace:WPFApplication1"`集部分, 例如 。 如果 BAML 引用內部類型,`internal`並且該 類型具有訪問級別`GeneratedInternalTypeHelper`,這將為程式集生成一個類。 如果要避免`GeneratedInternalTypeHelper`,則必須`public`使用 訪問級別,或者必須將相關類考慮到單獨的程式集中,並使該程式集與程式集相關。

## <a name="see-also"></a>另請參閱

- [自訂類型和程式庫的 XAML 相關 CLR 屬性](clr-attributes-with-custom-types-and-libraries.md)
- [XAML 服務](../../../api/index.md)
