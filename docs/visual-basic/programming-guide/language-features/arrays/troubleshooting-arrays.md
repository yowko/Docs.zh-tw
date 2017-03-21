---
title: "疑難排解陣列 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
caps.latest.revision: 17
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: db38c0c2a4f8b74a6b862f86f426b4d8837f4424
ms.lasthandoff: 03/13/2017

---
# <a name="troubleshooting-arrays-visual-basic"></a>疑難排解陣列 (Visual Basic)
此頁面列出使用陣列時所發生的一些常見問題。  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a>宣告和初始化陣列的編譯錯誤  
 因為不瞭解的宣告、 建立和初始化陣列的規則可能會發生編譯錯誤。 最常見的錯誤原因如下所示︰  
  
-   提供[New 運算子](../../../../visual-basic/language-reference/operators/new-operator.md)之後陣列變數宣告中指定的維度長度的子句。 下列程式碼行顯示此類型的無效宣告。  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
-   指定維度長度已超過最上層不規則陣列的陣列。 下列程式碼行顯示此類型無效的宣告。  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
-   省略`New`關鍵字時指定的項目值。 下列程式碼行顯示此類型無效的宣告。  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
-   提供`New`子句但不含大括號 (`{}`)。 下列程式碼行顯示此類型的無效宣告。  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a>存取超出界限的陣列  
 初始化陣列的程序指派每個維度的上限和下限。 每次存取陣列的元素必須指定有效的索引，或是註標，每個維度。 如果任何索引是其下限低於或高於其上限，<xref:System.IndexOutOfRangeException>產生例外狀況。</xref:System.IndexOutOfRangeException> 編譯器無法偵測這類錯誤，因此在執行階段發生錯誤。  
  
### <a name="determining-bounds"></a>決定界限  
 如果另一個元件會將陣列傳遞至您的程式碼，例如做為程序引數，您不知道該陣列的大小或其維度的長度。 您嘗試存取任何項目之前，您應該一律判斷陣列中的每個維度的上限。 如果已建立陣列的方法以外的其他[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]`New`子句，下限可能不是 0，而且很安全決定的最小值。  
  
### <a name="specifying-the-dimension"></a>指定維度  
 在決定多維度陣列的界限時，小心指定維度的方式。 `dimension`參數<xref:System.Array.GetLowerBound%2A>和<xref:System.Array.GetUpperBound%2A>方法是以 0 為基礎，同時`Rank`參數[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<xref:Microsoft.VisualBasic.Information.LBound%2A>和<xref:Microsoft.VisualBasic.Information.UBound%2A>函式是以 1 為基礎。</xref:Microsoft.VisualBasic.Information.UBound%2A> </xref:Microsoft.VisualBasic.Information.LBound%2A> </xref:System.Array.GetUpperBound%2A> </xref:System.Array.GetLowerBound%2A>  
  
## <a name="see-also"></a>另請參閱  
 [陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [如何︰ 在 Visual Basic 中的將陣列變數初始化](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
