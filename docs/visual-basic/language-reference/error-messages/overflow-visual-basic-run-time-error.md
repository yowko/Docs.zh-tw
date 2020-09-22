---
title: 溢位 (Visual Basic 執行階段錯誤)
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: e287d6c24eca75d8bf20181a201056f467d6fc4e
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871226"
---
# <a name="overflow-visual-basic-run-time-error"></a>溢位 (Visual Basic 執行階段錯誤)

當您嘗試的指派超過指派的目標限制時，就會產生溢位。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 請確定指派、計算和資料類型轉換的結果不太大而無法在該類型值所允許的變數範圍內表示，並視需要將值指派給可保存較大範圍之值的型別變數。  
  
2. 請確定屬性的指派符合它們所做的屬性範圍。  
  
3. 請確定已強制轉型為整數的計算中所使用的數位沒有大於整數的結果。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Int32.MaxValue?displayProperty=nameWithType>
- <xref:System.Double.MaxValue?displayProperty=nameWithType>
- [Data types (資料類型)](../data-types/index.md)
- [錯誤類型](../../programming-guide/language-features/error-types.md)
