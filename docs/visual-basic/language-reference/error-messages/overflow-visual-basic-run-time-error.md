---
title: 溢位 (Visual Basic 執行階段錯誤)
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: 7546676b85465577b357b7ad0757b4db8d40dbe3
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863347"
---
# <a name="overflow-visual-basic-run-time-error"></a>溢位 (Visual Basic 執行階段錯誤)
當您嘗試超過限制的指派目標的指派時，就會造成溢位。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請確定指派、 計算和資料類型轉換不會太大而無法表示變數的值，該類型所允許的範圍內，並將值指派給類型的變數的結果可以保存較大範圍的值如有必要。  
  
2.  請確定指派屬性符合的屬性會將所做的範圍。  
  
3.  請確定會強制轉型成整數的計算中使用的數字，並沒有比整數較大的結果。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Int32.MaxValue?displayProperty=nameWithType>  
 <xref:System.Double.MaxValue?displayProperty=nameWithType>  
 [資料類型](../../../visual-basic/language-reference/data-types/index.md)  
 [錯誤類型](../../../visual-basic/programming-guide/language-features/error-types.md)
