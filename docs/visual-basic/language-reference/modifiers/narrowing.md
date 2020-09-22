---
title: Narrowing
ms.date: 07/20/2015
f1_keywords:
- vb.narrowing
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Narrowing keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
ms.openlocfilehash: 77515357ac9dc972992df09c471695aad13985c4
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867936"
---
# <a name="narrowing-visual-basic"></a>Narrowing (Visual Basic)

指出轉換運算子 (`CType`) 將類別或結構轉換成可能無法保存某些原始類別或結構之可能值的類型。  
  
## <a name="converting-with-the-narrowing-keyword"></a>使用縮小關鍵字進行轉換  

 除了以外，轉換程式 `Public Shared` 還必須指定 `Narrowing` 。  
  
 縮小轉換在執行時間不一定會成功，而且可能會失敗或導致資料遺失。 例如 `Long` ，to `Integer` 、 `String` to `Date` 和 base type to a 衍生型別。 因為基底類型可能不包含衍生類型的所有成員，因此不是衍生型別的實例，所以最後一個轉換會縮小。  
  
 如果 `Option Strict` 是 `On` ，使用中的程式碼必須用於 `CType` 所有縮小轉換。  
  
 `Narrowing`關鍵字可用於此內容中：  
  
 [Operator Statement](../statements/operator-statement.md)  
  
## <a name="see-also"></a>另請參閱

- [Operator Statement](../statements/operator-statement.md)
- [Widening](widening.md)
- [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [如何：定義運算子](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [CType Function](../functions/ctype-function.md)
- [Long](../statements/option-strict-statement.md)
