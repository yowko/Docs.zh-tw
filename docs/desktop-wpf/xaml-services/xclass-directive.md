---
title: x:Class 指示詞
ms.date: 03/30/2017
f1_keywords:
- x:Class
- xClass
- Class
helpviewer_keywords:
- Class attribute in XAML [XAML Services]
- XAML [XAML Services], x:Class attribute
- x:Class attribute [XAML Services]
ms.assetid: bc4a3d8e-76e2-423e-a5d1-159a023e82ec
ms.openlocfilehash: f589fa70c2ee1c56544fa0f0152990478aa3761f
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072036"
---
# <a name="xclass-directive"></a>x:Class 指示詞
配置 XAML 標籤編譯以在標記和代碼後面之間聯接部分類。 代碼部分類以通用語言規範 (CLS) 語言在單獨的代碼檔中定義,而標記部分類通常在 XAML 編譯期間由代碼生成創建。

## <a name="xaml-attribute-usage"></a>XAML Attribute Usage

```xaml
<object x:Class="namespace.classname"...>
  ...
</object>
```

## <a name="xaml-values"></a>XAML 值

|||
|-|-|
|`namespace`|選擇性。 指定包含 由`classname`識別的部分類的 CLR 命名空間。 如果`namespace`指定,點 (.) 會`namespace`分`classname`隔與 。 請參閱＜備註＞。|
|`classname`|必要。 指定連接載入的 XAML 和該 XAML 的代碼後面的部分類的 CLR 名稱。|

## <a name="dependencies"></a>相依性

`x:Class`只能在 XAML 生產的根元素上指定。 `x:Class`在 XAML 生產中具有父物件的任何對象上無效。 有關詳細資訊,請參閱[\[MS-XAML\]部分 4.3.1.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))。

## <a name="remarks"></a>備註

該`namespace`值可能包含其他點,用於將相關命名空間組織到名稱層次結構中,這是 .NET 程式設計中的一種常見技術。 只有`x:Class`值字串中的最後一個點被解釋為分隔`namespace`,`classname.`用作類的`x:Class`類 不能是嵌套類。 不允許嵌套類,因為如果允許嵌套類,則確定字串`x:Class`的點含義不明確。

在使用`x:Class`的現有程式設計模型中,`x:Class`是可選的,因為 XAML 頁沒有代碼背後,是完全有效的。 但是,該功能與使用 XAML 的框架實現的生成操作進行交互。 `x:Class`功能還受 XAML 指定內容的各種分類在應用程式模型和相應的生成操作中的角色的影響。 如果 XAML 聲明事件處理屬性值或實例化定義類位於代碼後面類中的自定義元素,則必須向相應的`x:Class`類提供 指令引用(或[x:sub 類](xsubclass-directive.md))以進行代碼後面。

`x:Class`指令的值必須是指定類完全限定名稱但沒有任何程式集資訊(等效於<xref:System.Type.FullName%2A?displayProperty=nameWithType>) 的字串。 對於簡單應用程式,如果代碼後面也以這種方式構造(代碼定義從類級別開始),則可以省略 CLR 命名空間資訊。

頁面或應用程式定義的代碼背後的文件必須位於代碼檔中,該檔包含在生成已編譯的應用程式並涉及標記編譯的專案的一部分中。 您必須遵循 CLR 類的名稱規則。 有關詳細資訊,請參閱[框架設計指南](../../../api/index.md)。 預設情況下,代碼後面類必須為`public`;但是,您可以使用[x:Class 修改器指令](xclassmodifier-directive.md)在不同的存取級別定義它。

該屬性的`x:Class`此解釋僅適用於基於 CLR 的 XAML 實現,尤其是 .NET XAML 服務。 其他不基於 CLR 且不使用 .NET XAML 服務的其他 XAML 實現可能使用不同的解析公式來連接 XAML 標記和備份執行時代碼。 有關 有關的更多一般解釋的詳細`x:Class`資訊 ,請參閱[\[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))。

在一定的體系結構等級中,在 .NET XAML 服務中`x:Class`未定義 。 這是因為 .NET XAML 服務沒有指定連接 XAML 標記和備份代碼的程式設計模型。 `x:Class`該指令的其他用途可能由使用程式設計模型或應用程式模型來定義如何連接 XAML 標記和基於 CLR 的代碼背後的特定框架實現。 每個框架都可以有自己的生成操作,這些操作啟用生成環境中必須包括的某些行為或特定元件。 在框架中,生成操作也可能因用於代碼後面的特定 CLR 語言而異。

## <a name="xclass-in-the-wpf-programming-model"></a>x:WPF 程式設計模型

在 WPF 應用程式和`x:Class`WPF 應用程式模型中,可以聲明為作為 XAML 檔根並正在編譯的任何元素的屬性(其中`Page`XAML 包含在具有生成操作的 WPF 應用程式<xref:System.Windows.Application>專案中),也可以聲明為已編譯 WPF 應用程式的應用程式定義中的根元素。 在`x:Class`頁面根或應用程式根以外的元素上聲明,或在未編譯的 WPF XAML 檔中進行聲明,在 .NET 框架 3.0 和 .NET 框架 3.5 WPF XAML 編譯器下會導致編譯時錯誤。 有關 WPF`x:Class`中 處理的其他方面的資訊,請參閱[WPF 中的代碼背後和 XAML。](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)

## <a name="xclass-for-windows-workflow-foundation"></a>x:Windows 工作流基礎類
對於 Windows`x:Class`工作流 基礎,請命名完全在 XAML 中組成的自訂活動的類,或者為具有代碼後面的活動設計器命名 XAML 頁的部分類。

## <a name="silverlight-usage-notes"></a>銀光使用說明

`x:Class`銀光單獨記錄。 有關詳細資訊,請參閱[XAML 命名空間 (x:)語言功能(銀光)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).

## <a name="see-also"></a>另請參閱

- [x:Subclass 指示詞](xsubclass-directive.md)
- [WPF 的 XAML 和自訂類別](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [x:ClassModifier 指示詞](xclassmodifier-directive.md)
- [從 WPF 移轉至 System.Xaml 的類型](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
