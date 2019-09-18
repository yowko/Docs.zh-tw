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
ms.openlocfilehash: 2b7713548b6269f079ef32b5bf1fe4fa630edcc8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053786"
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
 `x:Code` Xaml 指示詞專案中的程式碼仍會在一般 XML 命名空間和所提供的 XAML 命名空間內加以解讀。 因此，通常需要將用於`x:Code` `CDATA`區段內的程式碼括住。  
  
 `x:Code`不允許用於 XAML 生產環境的所有可能部署機制。 在特定架構（例如 WPF）中，必須編譯器代碼。 在其他架構中`x:Code` ，通常會不允許使用。  
  
 對於允許受控`x:Code`內容的架構，用於`x:Code`內容的正確語言編譯器是由用來編譯應用程式之包含專案的設定和目標所決定。  
  
## <a name="wpf-usage-notes"></a>WPF 使用注意事項  
 在 for WPF `x:Code`中宣告的程式碼有數個值得注意的限制：  
  
- `x:Code`指示詞專案必須是 XAML 生產的根項目的直屬子項目。  
  
- 必須在父根項目上提供[x：Class](x-class-directive.md)指示詞。  
  
- 放在內`x:Code`的程式碼會由編譯處理，以在已針對該 XAML 頁面建立的部分類別範圍內。 因此，您定義的所有程式碼都必須是該部分類別的成員或變數。  
  
- 除了在部分類別中嵌套類別以外，您無法定義其他類別（允許嵌套，但不是一般的，因為在 XAML 中無法參考嵌套類別）。 除了用於現有部分類別的命名空間以外的 CLR 命名空間無法定義或加入至。  
  
- 部分類別 CLR 命名空間外之程式碼實體的參考必須全部都是完整的。 如果宣告的成員會覆寫至部分類別可重寫成員，則必須使用語言特定的 override 關鍵字來指定。 如果在範圍中`x:Code`宣告的成員與從 XAML 建立之部分類別的成員衝突，則在此情況下，編譯器會報告衝突，XAML 檔案就無法編譯或載入。  
  
## <a name="see-also"></a>另請參閱

- [x:Class 指示詞](x-class-directive.md)
- [WPF 中的程式碼後置和 XAML](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [XAML 概觀 (WPF)](../wpf/advanced/xaml-overview-wpf.md)
