---
title: += 運算子
ms.date: 07/20/2015
f1_keywords:
- vb.+=
helpviewer_keywords:
- += operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- += operator [Visual Basic], appending strings
- compound assignment statements [Visual Basic]
ms.assetid: d3e959f4-85d4-4e47-87c4-77b62335a5b3
ms.openlocfilehash: c2ce384901a9f0207e8279a5a07a88600c875e7f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372203"
---
# <a name="-operator-visual-basic"></a>+= 運算子 (Visual Basic)
將數值運算式的值加入數值變數或屬性的值，並將結果指派給變數或屬性。 也可以用來將運算式串連 `String` 至 `String` 變數或屬性，並將結果指派給變數或屬性。  
  
## <a name="syntax"></a>語法  
  
```vb  
variableorproperty += expression  
```  
  
## <a name="parts"></a>組件  
 `variableorproperty`  
 必要。 任何數值或 `String` 變數或屬性。  
  
 `expression`  
 必要。 任何數值或 `String` 運算式。  
  
## <a name="remarks"></a>備註  
 運算子左邊的元素 `+=` 可以是簡單的純量變數、屬性或陣列的元素。 變數或屬性不可為[ReadOnly](../modifiers/readonly.md)。  
  
 `+=`運算子會將其右邊的值加到其左邊的變數或屬性，並將結果指派給其左邊的變數或屬性。 `+=`運算子也可以用來將 `String` 其右邊的運算式串連至 `String` 其左邊的變數或屬性，並將結果指派給其左邊的變數或屬性。  
  
> [!NOTE]
> 當您使用 `+=` 運算子時，可能無法判斷是否會進行加法或字串串連。 使用 `&=` 運算子進行串連，以消除不明確的情況，並提供自我記錄程式碼。  
  
 如果編譯環境強制執行嚴格的語義，則此指派運算子會隱含地執行擴展，但不會縮小轉換。 如需這些轉換的詳細資訊，請參閱[擴展和縮小轉換](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。 如需 strict 和寬鬆語義的詳細資訊，請參閱[Option Strict 語句](../statements/option-strict-statement.md)。  
  
 如果允許寬鬆的語義， `+=` 運算子會隱含地執行各種字串和數值轉換，與運算子所執行的相同 `+` 。 如需這些轉換的詳細資訊，請參閱[+ 運算子](addition-operator.md)。  
  
## <a name="overloading"></a>多載化  
 `+`運算子可以多載*overloaded*，這表示當運算元具有該類別或結構的類型時，類別或結構可以重新定義其行為。 多載 `+` 運算子會影響運算子的行為 `+=` 。 如果您的程式碼在多載 `+=` 的類別或結構上使用 `+` ，請務必瞭解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用 `+=` 運算子，將一個變數的值與另一個變數結合。 第一個部分會使用搭配 `+=` 數值變數，將一個值新增至另一個。 第二個部分會使用搭配 `+=` `String` 變數來串連一個值與另一個值。 在這兩種情況下，都會將結果指派給第一個變數。  
  
 [!code-vb[VbVbalrOperators#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#7)]  
  
 [!code-vb[VbVbalrOperators#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#8)]  
  
 的值 `num1` 現在是13，而的值 `str1` 現在是 "103"。  
  
## <a name="see-also"></a>另請參閱

- [+ 運算子](addition-operator.md)
- [指派運算子](assignment-operators.md)
- [算術運算子](arithmetic-operators.md)
- [串連運算子](concatenation-operators.md)
- [Visual Basic 中的運算子優先順序](operator-precedence.md)
- [依功能列出運算子](operators-listed-by-functionality.md)
- [陳述式](../../programming-guide/language-features/statements.md)
