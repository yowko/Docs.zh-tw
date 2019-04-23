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
ms.openlocfilehash: 7bb78b05be7b3edc4471bc276010eabd92a07a14
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59145232"
---
# <a name="xcode-intrinsic-xaml-type"></a>x:Code 內建 XAML 類型
可讓 XAML 生產環境中的程式碼的位置。 可以將 XAML 或留在稍後使用，例如解譯的 XAML 生產環境中的執行階段編譯任何 XAML 處理器實作編譯這類程式碼。  
  
## <a name="xaml-object-element-usage"></a>XAML 物件項目用法  
  
```  
<x:Code>  
   // code instructions, usually enclosed by CDATA...  
</x:Code>  
```  
  
## <a name="remarks"></a>備註  
 中的程式碼`x:Code`XAML 指示詞項目是仍在一般的 XML 命名空間中解譯和提供的 XAML 命名空間。 因此，它是括住的程式碼通常會需要`x:Code`內`CDATA`區段。  
  
 `x:Code` 不允許針對 XAML 生產的所有可能的部署機制。 在特定架構 (例如 WPF) 中程式碼必須編譯。 在 其他架構，`x:Code`可能通常不允許使用方式。  
  
 允許受管理的架構`x:Code`內容，正確的語言編譯器使用`x:Code`內容取決於設定和用來編譯應用程式所包含專案的目標。  
  
## <a name="wpf-usage-notes"></a>WPF 使用注意事項  
 程式碼內宣告`x:Code`WPF 有幾個值得注意的限制：  
  
-   `x:Code`指示詞項目必須是 XAML 生產的根元素的直系子元素。  
  
-   [X:class 指示詞](x-class-directive.md)必須提供在父根項目。  
  
-   程式碼置於`x:Code`會被編譯到已建立該 XAML 頁面的部分類別的範圍內。 因此您所定義的所有程式碼必須是成員或該部分類別的變數。  
  
-   您不能定義其他類別，而非巢狀內的部分類別的類別 （允許巢狀結構，但它不是一般因為 XAML 中不得參考巢狀的類別）。 無法定義或加入至用於現有的部分類別的命名空間以外的 CLR 命名空間。  
  
-   部分類別的 CLR 命名空間外部的程式碼實體的參考必須全部是完整名稱。 如果宣告的成員會覆寫部分類別可覆寫成員，這必須指定與語言特定覆寫的關鍵字。 如果成員宣告中`x:Code`與 XAML 建立的部分類別的成員相衝突的範圍，一種，編譯器會報告衝突，XAML 檔案無法編譯或載入。  
  
## <a name="see-also"></a>另請參閱

- [x:Class 指示詞](x-class-directive.md)
- [WPF 中的程式碼後置和 XAML](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [XAML 概觀 (WPF)](../wpf/advanced/xaml-overview-wpf.md)
