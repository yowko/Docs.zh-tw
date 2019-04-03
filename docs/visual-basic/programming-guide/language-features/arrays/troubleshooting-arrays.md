---
title: 疑難排解陣列 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
ms.openlocfilehash: 2b051d22fe3d331626f2e181c008043e576b7526
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833369"
---
# <a name="troubleshooting-arrays-visual-basic"></a>疑難排解陣列 (Visual Basic)
此頁面會列出使用陣列時所發生的一些常見問題。  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a>宣告和初始化陣列的編譯錯誤  
 從 宣告、 建立和初始化陣列的規則的誤解，可能會發生編譯錯誤。 錯誤的最常見的原因如下所示：  
  
-   提供[New 運算子](../../../../visual-basic/language-reference/operators/new-operator.md)陣列變數宣告中指定的維度長度之後的子句。 下列程式碼行顯示此類型的無效的宣告。  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
-   指定維度的長度超過一個最上層陣列的不規則陣列。 下列程式碼行顯示此類型的無效的宣告。  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
-   省略`New`關鍵字指定的項目值時。 下列程式碼行顯示此類型的無效的宣告。  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
-   提供`New`子句但不含大括號 (`{}`)。 下列程式碼行顯示此類型的無效的宣告。  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a>存取超出範圍的陣列  
 初始化陣列的程序將給每個維度的上限和下限。 每個存取陣列的項目必須指定有效的索引或註標，每個維度。 如果任何索引是低於其下限或高於其上限，<xref:System.IndexOutOfRangeException>例外狀況結果。 編譯器無法偵測這類錯誤，因此在執行階段發生錯誤。  
  
### <a name="determining-bounds"></a>判斷範圍  
 如果另一個元件會將陣列傳遞至您的程式碼，例如做為程序引數中，您不知道該陣列的大小或其維度的長度。 您嘗試存取任何項目之前，您一律應該判斷陣列的每個維度的上限。 如果已建立 Visual Basic 以外的其他方式的陣列`New`子句，下限看起來可能不是 0，而且它是最安全的方式決定也該下限。  
  
### <a name="specifying-the-dimension"></a>指定的維度  
 在決定多維度陣列的界限，負責指定維度的方式。 `dimension`的參數<xref:System.Array.GetLowerBound%2A>並<xref:System.Array.GetUpperBound%2A>方法是以 0 為基礎，同時`Rank`參數的 Visual Basic<xref:Microsoft.VisualBasic.Information.LBound%2A>和<xref:Microsoft.VisualBasic.Information.UBound%2A>函式是以 1 為基礎。  
  
## <a name="see-also"></a>另請參閱

- [陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [如何：初始化陣列變數在 Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
