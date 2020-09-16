---
title: XML 字元實體和 XAML
ms.date: 03/30/2017
f1_keywords:
- '&'
- '&amp'
- '&gt'
- '&lt'
helpviewer_keywords:
- XAML [XAML Services], special characters
- ampersand (&) [XAML Services]
- special characters [XAML Services]
- apostrophe (') [XAML Services]
- greater-than (>) character [XAML Services]
- XAML [XAML Services], quotation mark (")
- XAML [XAML Services], apostrophe (')
- '& (ampersand) [XAML Services]'
- XAML [XAML Services], & (ampersand)
- XAML [XAML Services], escape sequence
- quotation mark (") [XAML Services]
- less-than (<) character [XAML Services]
ms.assetid: 6896d0ce-74f7-420a-9ab4-de9bbf390e8d
ms.openlocfilehash: 1ba99cda512bc5e18c646b09f26672a39c1cf53c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548188"
---
# <a name="xml-character-entities-and-xaml"></a>XML 字元實體和 XAML

XAML 使用 XML 中針對特殊字元定義的字元實體。 本主題說明一些特定字元實體，以及針對 XAML 中其他 XML 概念的一般考量。

## <a name="character-entities-and-escaping-issues-that-are-unique-to-xaml"></a>XAML 特有的字元實體和逸出問題

XAML 標記通常會使用 XML 中定義的相同字元實體和逸出序列。

主要的差異在於大括號 ({ 和 }) 在 XAML 中具有顯著意義，因為這些字元會通知 XAML 處理器，包含在大括號內的字元序列必須解譯為標記延伸。 如需標記延伸的詳細資訊，請參閱 [Markup Extensions for XAML Overview](markup-extensions-overview.md)。

不過，您還是可以使用 XAML (而不是 XML) 特有的逸出序列，將大括號顯示為常值字元。 如需詳細資訊，請參閱[ {} Escape Sequence-標記延伸](escape-sequence-markup-extension.md)。

請注意，反斜線 (\\) 在當做字串處理時，不需要有 escape 順序。

## <a name="xml-character-entities"></a>XML 字元實體

如前所述，通常用於撰寫 XAML 標記的大多數字元實體和逸出序列都是由 XML 定義的。 本主題並未提供這些實體的完整清單，您可以在外部文件 (例如 XML 規格) 中找到這些實體的詳細參考資料。 不過，為了方便起見，本主題會列出 XAML 標記中常用的 XML 字元實體。

|字元|單位|注意|
|---------------|------------|-----------|
|& (連字號)|\&amp;|必須用於屬性值和項目內容。|
|> (大於字元) |\&gt;|必須用於屬性值，但前提是 > 可作為元素的內容，只要 < 不在前面。|
|< (小於字元) |\&lt;|必須用於屬性值，但不能 \< is acceptable as the content of an element as long as > 跟隨。|
|" (雙引號)|\&quot;|必須用於屬性值，但可接受雙引號 (") 做為項目內容。 請注意，屬性值可以使用單引號 (') 或雙引號 ('') 括住；先出現的字元會定義括住的屬性值，而另一種引號則可以接著用來括住值內的常值。|
|' (單引號)|\&apos;|必須用於屬性值，但可接受單引號 (') 做為項目內容。 請注意，屬性值可以使用單引號 (') 或雙引號 ('') 括住；先出現的字元會定義括住的屬性值，而另一種引號則可以接著用來括住值內的常值。|
|(數字字元對應)|&#*[整數]*;或 & # x *[hex]*;|XAML 支援將數字字元對應至使用中的編碼方式。|
|(不分行空格)|&\#160; (假設 UTF-8 編碼) |對於非固定格式文件項目，或是接受文字的項目 (例如 WPF <xref:System.Windows.Controls.TextBox>)，即使 `xml:space="default"`，也不會在標記外部將不分行空格標準化。 如需詳細資訊，請參閱 [XAML 中](white-space-processing.md)的空白字元處理 (。 ) |

## <a name="xml-comment-format"></a>XML 註解格式

XAML 使用 XML 註解格式：註解的開頭為 `<!--`，註解的結尾為 `-->,`，而且在註解內不能出現 `--` 序列。

## <a name="xml-processing-instructions"></a>XML 處理指令

XAML 會根據 XML 規格來處理 XML 處理指令，該規格表示必須將指令傳遞通過。 .NET XAML 服務中的 XAML 處理不會使用任何處理指示。 其他使用 XAML 的現有架構，也都不會使用 XAML 的處理指令。

## <a name="see-also"></a>另請參閱

- [XAML 概觀 (WPF)](../fundamentals/xaml.md)
- [標記延伸和 WPF XAML](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml)
- [XamlName 文法](xamlname-grammar.md)
- [XAML 中的空白字元處理](white-space-processing.md)
