---
title: 針對陣列進行疑難排解
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
ms.openlocfilehash: e633c5a00693f188270b1610abaf2decb656b00a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414591"
---
# <a name="troubleshooting-arrays-visual-basic"></a>疑難排解陣列 (Visual Basic)
此頁面會列出使用陣列時可能發生的一些常見問題。  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a>宣告和初始化陣列的編譯錯誤  
 編譯錯誤可能來自于宣告、建立和初始化陣列的規則誤解。 錯誤的最常見原因如下：  
  
- 在陣列變數宣告中指定維度長度之後，提供[新的 Operator](../../../language-reference/operators/new-operator.md)子句。 下列程式程式碼會顯示此類型的無效宣告。  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
- 指定超出不規則陣列最上層陣列的維度長度。 下列程式程式碼會顯示此類型的無效宣告。  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
- `New`指定元素值時省略關鍵字。 下列程式程式碼會顯示此類型的無效宣告。  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
- 提供 `New` 不含大括弧（ `{}` ）的子句。 下列程式程式碼會顯示此類型的無效宣告。  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a>存取超出範圍的陣列  
 初始化陣列的程式會指派上限和下限給每個維度。 陣列元素的每個存取都必須為每個維度指定有效的索引或注標。 如果任何索引低於其下限或高於上限，就會 <xref:System.IndexOutOfRangeException> 產生例外狀況。 編譯器無法偵測到這類錯誤，因此在執行時間發生錯誤。  
  
### <a name="determining-bounds"></a>判斷界限  
 如果另一個元件將陣列傳遞至您的程式碼（例如當做程式引數），您就不知道該陣列的大小或其維度的長度。 在嘗試存取任何元素之前，您應該一律判斷陣列的每個維度的上限。 如果陣列是由 Visual Basic 子句以外的某些方法所建立 `New` ，則下限可能是0以外的專案，而且也會最安全地判斷下限。  
  
### <a name="specifying-the-dimension"></a>指定維度  
 在判斷多維陣列的界限時，請留意您指定維度的方式。 `dimension`和方法的參數 <xref:System.Array.GetLowerBound%2A> <xref:System.Array.GetUpperBound%2A> 是以0為基礎，而 `Rank` Visual Basic <xref:Microsoft.VisualBasic.Information.LBound%2A> 和函數的參數 <xref:Microsoft.VisualBasic.Information.UBound%2A> 是以1為基礎。  
  
## <a name="see-also"></a>另請參閱

- [陣列](index.md)
- [如何：在 Visual Basic 中初始化陣列變數](how-to-initialize-an-array-variable.md)
