---
title: IsTrue 運算子
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: bc129d3a3aec76285d5ea8fb727fc72c3064c9cf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370644"
---
# <a name="istrue-operator-visual-basic"></a>IsTrue 運算子 (Visual Basic)
判斷運算式是否為 `True` 。  
  
 您無法 `IsTrue` 在程式碼中明確呼叫，但是 Visual Basic 編譯器可以使用它來產生來自子句的程式碼 `OrElse` 。 如果您定義了類別或結構，然後在子句中使用該類型的變數 `OrElse` ，您必須 `IsTrue` 在該類別或結構上定義。  
  
 編譯器會將 `IsTrue` 和 `IsFalse` 運算子視為相符的*配對*。 這表示如果您定義其中一個，則也必須定義另一個。  
  
## <a name="compiler-use-of-istrue"></a>編譯器使用 IsTrue  
 當您定義了類別或結構時，可以在 `For` 、 `If` 、 `Else If` 或 `While` 語句中，或在 `When` 子句中使用該類型的變數。 如果您這樣做，編譯器需要一個運算子，將您的型別轉換成 `Boolean` 值，讓它可以測試條件。 它會依下列順序搜尋適合的運算子：  
  
1. 從您的類別或結構到的擴輾轉換運算子 `Boolean` 。  
  
2. 從您的類別或結構到的擴輾轉換運算子 `Boolean?` 。  
  
3. `IsTrue`類別或結構上的運算子。  
  
4. 的縮小轉換 `Boolean?` 不牽涉到從轉換 `Boolean` 成的 `Boolean?` 。  
  
5. 從您的類別或結構到的縮小轉換運算子 `Boolean` 。  
  
 如果您尚未定義任何對 `Boolean` 或運算子的轉換 `IsTrue` ，則編譯器會發出錯誤信號。  
  
> [!NOTE]
> `IsTrue`運算子可以多載*overloaded*，這表示當類別或結構的運算元具有該類別或結構的類型時，可以重新定義其行為。 如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列程式碼範例會定義包含和運算子之定義的結構外框 `IsFalse` `IsTrue` 。  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>另請參閱

- [IsFalse 運算子](isfalse-operator.md)
- [如何：定義運算子](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [OrElse 運算子](orelse-operator.md)
