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
ms.openlocfilehash: 4ab6d376ad8652e460e33c4f2c3285e8c80286fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654257"
---
# <a name="troubleshooting-arrays-visual-basic"></a>疑難排解陣列 (Visual Basic)
此頁面會列出可以使用陣列時會發生的一些常見問題。  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a>宣告和初始化陣列的編譯錯誤  
 編譯錯誤所引起的宣告、 建立和初始化陣列的規則的誤解。 最常見的錯誤原因如下：  
  
-   提供[New 運算子](../../../../visual-basic/language-reference/operators/new-operator.md)之後陣列變數宣告中指定的維度長度的子句。 下列程式碼行顯示此類型的無效的宣告。  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
-   指定維度長度已超過最上層陣列的不規則陣列。 下列程式碼行顯示此類型無效的宣告。  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
-   省略`New`關鍵字時指定的項目值。 下列程式碼行顯示此類型無效的宣告。  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
-   提供`New`子句但不含大括號 (`{}`)。 下列程式碼行顯示此類型的無效的宣告。  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a>存取超出範圍的陣列  
 初始化陣列的程序指派每個維度的上限和下限。 每次存取陣列項目必須指定有效的索引或註標，每個維度。 如果任何索引低於其下限，或超過其上限，<xref:System.IndexOutOfRangeException>例外狀況結果。 編譯器無法偵測這類錯誤，因此在執行階段發生錯誤。  
  
### <a name="determining-bounds"></a>決定界限  
 如果另一個元件會將陣列傳遞至您的程式碼，例如做為程序引數，您不知道該陣列的大小或其維度的長度。 您嘗試存取任何項目之前，您應該一律判斷陣列的每個維度的上限。 如果陣列已建立 Visual Basic 以外的其他方式`New`子句，下限看起來可能不是 0，而且是先決定以及該下限。  
  
### <a name="specifying-the-dimension"></a>指定維度  
 在決定多維度陣列的界限時，小心指定維度的方式。 `dimension`參數<xref:System.Array.GetLowerBound%2A>和<xref:System.Array.GetUpperBound%2A>方法是以 0 為基礎，同時`Rank`參數的 Visual Basic<xref:Microsoft.VisualBasic.Information.LBound%2A>和<xref:Microsoft.VisualBasic.Information.UBound%2A>函式是以 1 為基礎。  
  
## <a name="see-also"></a>另請參閱  
 [陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [如何：在 Visual Basic 中初始化陣列變數](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
