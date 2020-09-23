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
ms.openlocfilehash: e0cb1008f4182331b7380db81d7a92a0fd45f2f4
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086357"
---
# <a name="troubleshooting-arrays-visual-basic"></a>疑難排解陣列 (Visual Basic)

此頁面列出使用陣列時可能發生的一些常見問題。  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a>宣告和初始化陣列的編譯錯誤  

 宣告、建立及初始化陣列的規則誤解可能會發生編譯錯誤。 錯誤的最常見原因如下：  
  
- 在陣列變數宣告中指定維度長度之後，提供 [新的 Operator](../../../language-reference/operators/new-operator.md) 子句。 下列程式程式碼會顯示此類型的無效宣告。  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
- 針對不規則陣列的最上層陣列指定維度長度。 下列程式程式碼顯示此類型的無效宣告。  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
- `New`指定元素值時省略關鍵字。 下列程式程式碼顯示此類型的無效宣告。  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
- 提供 `New` 不含大括弧 (`{}`) 的子句。 下列程式程式碼會顯示此類型的無效宣告。  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a>存取陣列超出範圍  

 初始化陣列的程式會將上限和下限指派給每個維度。 陣列元素的每個存取都必須為每個維度指定有效的索引或注標。 如果任何索引低於其下限或高於其上限，則會 <xref:System.IndexOutOfRangeException> 產生例外狀況結果。 編譯器無法偵測到這類錯誤，因此在執行時間發生錯誤。  
  
### <a name="determining-bounds"></a>判斷界限  

 如果另一個元件將陣列傳遞至您的程式碼（例如，程式引數），您就不知道該陣列的大小或其維度的長度。 在嘗試存取任何專案之前，您應該一律決定陣列的每個維度的上限。 如果陣列是以 Visual Basic 子句以外的某種方式建立 `New` ，則下限可能是0以外的部分，而且最安全的方式是判斷下限。  
  
### <a name="specifying-the-dimension"></a>指定維度  

 判斷多維陣列的界限時，請小心指定維度的方式。 `dimension`和方法的參數 <xref:System.Array.GetLowerBound%2A> <xref:System.Array.GetUpperBound%2A> 是以0為基礎，而 `Rank` Visual Basic <xref:Microsoft.VisualBasic.Information.LBound%2A> 和函數的參數 <xref:Microsoft.VisualBasic.Information.UBound%2A> 是以1為基礎。  
  
## <a name="see-also"></a>另請參閱

- [陣列](index.md)
- [如何：在 Visual Basic 中初始化陣列變數](how-to-initialize-an-array-variable.md)
