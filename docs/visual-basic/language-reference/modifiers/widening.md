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
ms.openlocfilehash: 69040bf48b44a54f7a231738b88db1cbc716ebb3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359899"
---
# <a name="widening-visual-basic"></a>Widening (Visual Basic)
表示轉換運算子（ `CType` ）會將類別或結構轉換成可保存原始類別或結構之所有可能值的類型。  
  
## <a name="converting-with-the-widening-keyword"></a>使用加寬關鍵字進行轉換  
 轉換程式 `Public Shared` 除了之外，還必須指定 `Widening` 。  
  
 擴輾轉換一律會在執行時間成功，而且永遠不會產生資料遺失。 範例包括 `Single` 對 `Double` `Char` `String` 其基底類型的、至和衍生類型。 最後一次轉換是擴大的，因為衍生類型包含基底類型的所有成員，因此是基底類型的實例。  
  
 使用程式碼不需要用於 `CType` 擴輾轉換，即使 `Option Strict` 為 `On` 。  
  
 `Widening`關鍵字可以在此內容中使用：  
  
 [Operator Statement](../statements/operator-statement.md)  
  
 如需擴展和縮小轉換運算子的範例定義，請參閱[如何：定義轉換運算子](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)。  
  
## <a name="see-also"></a>另請參閱

- [Operator Statement](../statements/operator-statement.md)
- [Narrowing](narrowing.md)
- [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [如何：定義運算子](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [CType Function](../functions/ctype-function.md)
- [Long](../statements/option-strict-statement.md)
- [How to: Define a Conversion Operator](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
