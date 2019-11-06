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
ms.openlocfilehash: 7312c59cdcddfdbda39a4a9f05788b6a021f9b75
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459596"
---
# <a name="xcode-intrinsic-xaml-type"></a>x:Code 內建 XAML 類型
允許在 XAML 生產環境中放置程式碼。 這類程式碼可以由任何編譯 XAML 的 XAML 處理器執行進行編譯，或在 XAML 生產環境中保留，以供稍後使用，例如執行時間的轉譯。  
  
## <a name="xaml-object-element-usage"></a>XAML 物件項目用法  
  
```xaml  
<x:Code>  
   // code instructions, usually enclosed by CDATA...  
</x:Code>  
```  
  
## <a name="remarks"></a>備註  
 `x:Code` XAML 指示詞專案內的程式碼仍會在一般 XML 命名空間和所提供的 XAML 命名空間內加以解讀。 因此，通常必須將用於 `x:Code` 的程式碼括在 `CDATA` 區段內。  
  
 XAML 生產的所有可能部署機制都不允許 `x:Code`。 在特定架構（例如 WPF）中，必須編譯器代碼。 在其他架構中，通常會不允許 `x:Code` 使用方式。  
  
 對於允許 managed `x:Code` 內容的架構，用於 `x:Code` 內容的正確語言編譯器是由用來編譯應用程式之包含專案的設定和目標所決定。  
  
## <a name="wpf-usage-notes"></a>WPF 使用注意事項  
 在 WPF 的 `x:Code` 中宣告的程式碼有數個值得注意的限制：  
  
- `x:Code` 指示詞專案必須是 XAML 生產的根項目的直屬子項目。  
  
- 必須在父根項目上提供[x：Class](x-class-directive.md)指示詞。  
  
- 放在 `x:Code` 中的程式碼會被編譯處理，使其位於已針對該 XAML 頁面建立之部分類別的範圍內。 因此，您定義的所有程式碼都必須是該部分類別的成員或變數。  
  
- 除了在部分類別中嵌套類別以外，您無法定義其他類別（允許嵌套，但不是一般的，因為在 XAML 中無法參考嵌套類別）。 除了用於現有部分類別的命名空間以外的 CLR 命名空間無法定義或加入至。  
  
- 部分類別 CLR 命名空間外之程式碼實體的參考必須全部都是完整的。 如果宣告的成員會覆寫至部分類別可重寫成員，則必須使用語言特定的 override 關鍵字來指定。 如果在 `x:Code` 範圍中宣告的成員與從 XAML 建立的部分類別的成員發生衝突，則在這種情況下，編譯器會報告衝突，因此 XAML 檔案無法編譯或載入。  
  
## <a name="see-also"></a>請參閱

- [x:Class 指示詞](x-class-directive.md)
- [WPF 中的程式碼後置和 XAML](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [XAML 概觀 (WPF)](../../desktop-wpf/fundamentals/xaml.md)
