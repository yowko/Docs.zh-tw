---
title: x:Code 內建 XAML 類型
ms.date: 03/30/2017
f1_keywords:
- Code
- x:Code
- xCode
helpviewer_keywords:
- Code directive in XAML [XAML Services]
- x:Code XAML directive element [XAML Services]
- XAML [XAML Services], x:Code directive element
ms.assetid: 87986b13-1a2e-4830-ae36-15f9dc5629e8
ms.openlocfilehash: ea7bc17cba19137b4e4ca2d8cddb32e6630887c9
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544839"
---
# <a name="xcode-intrinsic-xaml-type"></a>x:Code 內建 XAML 類型
允許在 XAML 生產環境內放置程式碼。 這類程式碼可以由任何編譯 XAML 的 XAML 處理器執行編譯，或留在 XAML 生產環境中，以供稍後使用，例如由執行時間所進行的轉譯。

## <a name="xaml-object-element-usage"></a>XAML 物件項目用法

```xaml
<x:Code>
   // code instructions, usually enclosed by CDATA...
</x:Code>
```

## <a name="remarks"></a>備註

Xaml 指示詞元素內的 `x:Code` 程式碼仍會在一般 XML 命名空間和提供的 xaml 命名空間內進行解讀。 因此，通常必須將用於區段內的程式碼括住 `x:Code` `CDATA` 。

`x:Code` 不允許 XAML 生產環境的所有可能部署機制使用。 在特定的 framework (例如 WPF) 必須編譯器代碼。 在其他架構中， `x:Code` 通常可能不允許使用。

針對允許受控內容的架構 `x:Code` ，用於內容的正確語言編譯器 `x:Code` 是由用來編譯應用程式之包含專案的設定和目標所決定。

## <a name="wpf-usage-notes"></a>WPF 使用注意事項

在 `x:Code` FOR WPF 內宣告的程式碼有幾個值得注意的限制：

- 指示詞 `x:Code` 元素必須是 XAML 生產的根項目的直屬子項目。

- 必須在父根項目上提供[x：Class](xclass-directive.md)指示詞。

- 放在裡面的 `x:Code` 程式碼將會被編譯，在部分類別的範圍內，而此部分類別已在該 XAML 頁面中建立。 因此，您定義的所有程式碼都必須是該部分類別的成員或變數。

- 除了在部分類別中嵌套類別以外，您也無法定義其他類別 (允許嵌套，但這並不常見，因為無法在 XAML) 中參考嵌套類別。 非用於現有部分類別之命名空間的 CLR 命名空間無法定義或新增至。

- 部分類別 CLR 命名空間外部程式碼實體的參考必須全部都是完整的。 如果宣告的成員是覆寫部分類別可覆寫成員的，則必須使用特定語言的覆寫關鍵字來指定此成員。 如果在範圍中宣告的成員 `x:Code` 與 xaml 所建立之部分類別的成員發生衝突，則在編譯器報告衝突的情況下，XAML 檔案就無法編譯或載入。

## <a name="see-also"></a>另請參閱

- [x:Class 指示詞](xclass-directive.md)
- [WPF 中的程式碼後置和 XAML](/dotnet/desktop/wpf/advanced/code-behind-and-xaml-in-wpf)
- [XAML 概觀 (WPF)](../fundamentals/xaml.md)
