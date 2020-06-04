---
title: 溢位 (Visual Basic 執行階段錯誤)
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: 5606ae8188c12142800adef46819791b732ff73c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387266"
---
# <a name="overflow-visual-basic-run-time-error"></a>溢位 (Visual Basic 執行階段錯誤)
當您嘗試指派超過指派目標的限制時，會產生溢位。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 請確定指派、計算和資料類型轉換的結果不會太大，而無法在該類型值所允許的變數範圍內呈現，並視需要將值指派給可保留較大範圍值的類型變數。  
  
2. 請確定 [屬性] 的 [指派] 符合所做屬性的範圍。  
  
3. 請確定在轉換成整數的計算中使用的數位沒有大於整數的結果。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Int32.MaxValue?displayProperty=nameWithType>
- <xref:System.Double.MaxValue?displayProperty=nameWithType>
- [資料類型](../data-types/index.md)
- [錯誤類型](../../programming-guide/language-features/error-types.md)
