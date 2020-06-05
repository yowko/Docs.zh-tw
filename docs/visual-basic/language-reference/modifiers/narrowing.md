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
ms.openlocfilehash: f7724053e3732c909523e4e2d3b65bb1918c29d3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84362355"
---
# <a name="narrowing-visual-basic"></a>Narrowing (Visual Basic)
表示轉換運算子（ `CType` ）會將類別或結構轉換成可能無法保存原始類別或結構之某些可能值的類型。  
  
## <a name="converting-with-the-narrowing-keyword"></a>使用縮小關鍵字進行轉換  
 轉換程式 `Public Shared` 除了之外，還必須指定 `Narrowing` 。  
  
 縮小轉換在執行時間不一定會成功，而且可能會失敗或產生資料遺失。 範例包括 `Long` 對 `Integer` `String` 衍生類型的、至以及 `Date` 基底類型。 最後一個轉換會縮小，因為基底類型可能不包含衍生類型的所有成員，因此不是衍生類型的實例。  
  
 如果 `Option Strict` 為 `On` ，則取用程式碼必須用於 `CType` 所有縮小轉換。  
  
 `Narrowing`關鍵字可以在此內容中使用：  
  
 [Operator Statement](../statements/operator-statement.md)  
  
## <a name="see-also"></a>另請參閱

- [Operator Statement](../statements/operator-statement.md)
- [Widening](widening.md)
- [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [如何：定義運算子](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [CType Function](../functions/ctype-function.md)
- [Long](../statements/option-strict-statement.md)
