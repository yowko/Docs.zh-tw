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
ms.openlocfilehash: 92be0b3b0fd1212c4254a449f902b85e998aa148
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="xcode-intrinsic-xaml-type"></a>x:Code 內建 XAML 類型
允許在 XAML 生產的程式碼的位置。 這類程式碼可以編譯任何 XAML 處理器實作編譯 XAML 或由執行階段在 XAML 生產的更新版本使用，如解譯左邊。  
  
## <a name="xaml-object-element-usage"></a>XAML 物件項目用法  
  
```  
<x:Code>  
   // code instructions, usually enclosed by CDATA...  
</x:Code>  
```  
  
## <a name="remarks"></a>備註  
 中的程式碼`x:Code`XAML 指示詞項目，而且仍然解譯一般的 XML 命名空間中提供的 XAML 命名空間。 因此，它是通常會需要使用程式碼括`x:Code`內`CDATA`區段。  
  
 `x:Code` 不允許用於 XAML 生產的所有可能的部署機制。 必須編譯程式碼中特定架構 (例如 WPF)。 用於其他架構，`x:Code`可能通常不允許使用方式。  
  
 允許受管理的介面架構`x:Code`內容，正確的語言編譯器使用`x:Code`內容取決於設定和用來編譯應用程式包含專案的目標。  
  
## <a name="wpf-usage-notes"></a>WPF 使用注意事項  
 程式碼中宣告`x:Code`WPF 有一些值得注意的限制：  
  
-   `x:Code`指示詞項目必須是在 XAML 生產的根元素的直系子元素。  
  
-   [X:class 指示詞](../../../docs/framework/xaml-services/x-class-directive.md)必須提供在父根元素。  
  
-   程式碼置於`x:Code`會編譯到已建立該 XAML 頁面的部分類別的範圍內所處理。 因此您定義的所有程式碼必須是成員或該部分類別的變數。  
  
-   您不能定義其他類別，而不是藉由巢狀內部的部分類別的類別 （允許巢狀結構，但它不是標準因為無法在 XAML 中參考巢狀的類別）。 無法定義或新增至用於現有的部分類別的命名空間以外的 CLR 命名空間。  
  
-   部分類別的 CLR 命名空間外部的程式碼實體的參考都必須完全符合規定。 如果宣告的成員會覆寫部分的類別可覆寫的成員，這必須指定以特定語言覆寫的關鍵字。 如果成員宣告中`x:Code`與從 XAML 建立部分類別的成員衝突的範圍、 的方式，編譯器會回報衝突，XAML 檔案無法編譯或載入。  
  
## <a name="see-also"></a>另請參閱  
 [x:Class 指示詞](../../../docs/framework/xaml-services/x-class-directive.md)  
 [WPF 中的程式碼後置和 XAML](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)  
 [XAML 概觀 (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
