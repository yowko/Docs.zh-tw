---
title: 溢位 (Visual Basic 執行階段錯誤)
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: 9db79071c4895d49680352bde2d0824a3756d941
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594171"
---
# <a name="overflow-visual-basic-run-time-error"></a>溢位 (Visual Basic 執行階段錯誤)
嘗試設定超出限制的指派的目標時，就會造成溢位。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請確定指派、 計算和資料類型轉換不會太大，而無法表示變數的值，該類型所允許的範圍內，並將值指派給類型的變數的結果可以保存較大範圍的值如有必要。  
  
2.  請確定屬性的指派，符合所建立的屬性的範圍。  
  
3.  請確定強制轉換為整數的計算中使用的數字，並沒有比整數較大的結果。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Int32.MaxValue?displayProperty=nameWithType>  
 <xref:System.Double.MaxValue?displayProperty=nameWithType>  
 [資料類型](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [錯誤類型](../../../visual-basic/programming-guide/language-features/error-types.md)
