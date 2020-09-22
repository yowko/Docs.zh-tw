---
title: Widening
ms.date: 07/20/2015
f1_keywords:
- vb.widening
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Widening keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 646ae263-94d3-40a2-b0cc-64f619292f56
ms.openlocfilehash: 14e0b026f4fc3b0bf202ea643a28d6f1a7df2b7c
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867644"
---
# <a name="widening-visual-basic"></a>Widening (Visual Basic)

指出轉換運算子 (`CType`) 將類別或結構轉換成可保存原始類別或結構之所有可能值的型別。  
  
## <a name="converting-with-the-widening-keyword"></a>使用擴展關鍵字進行轉換  

 除了以外，轉換程式 `Public Shared` 還必須指定 `Widening` 。  
  
 擴輾轉換一律會在執行時間成功，且不會產生資料遺失。 範例為 `Single` `Double` `Char` `String` 其基底類型的、到和衍生型別。 這項最後的轉換是擴展的，因為衍生型別包含基底類型的所有成員，因此是基底類型的實例。  
  
 使用程式碼不一定要用於 `CType` 擴輾轉換，即使 `Option Strict` 是 `On` 。  
  
 `Widening`關鍵字可用於此內容中：  
  
 [Operator Statement](../statements/operator-statement.md)  
  
 如需擴展和縮小轉換運算子的範例定義，請參閱 [如何：定義轉換運算子](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)。  
  
## <a name="see-also"></a>另請參閱

- [Operator Statement](../statements/operator-statement.md)
- [Narrowing](narrowing.md)
- [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [如何：定義運算子](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [CType Function](../functions/ctype-function.md)
- [Long](../statements/option-strict-statement.md)
- [How to: Define a Conversion Operator](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
