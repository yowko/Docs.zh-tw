---
title: '&amp; 運算子'
ms.date: 07/20/2015
f1_keywords:
- vb.&
helpviewer_keywords:
- And (&) operator
- ampersand operator (&)
- '& operator'
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
ms.assetid: fefc3d00-cbf1-475c-8c5e-6fb213b3f85a
ms.openlocfilehash: d778c0c99d6d074fe8b73aaf3660074643e7e136
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371605"
---
# <a name="amp-operator-visual-basic"></a>&amp;運算子（Visual Basic）
產生兩個運算式的字串串連。  
  
## <a name="syntax"></a>語法  
  
```vb  
result = expression1 & expression2  
```  
  
## <a name="parts"></a>組件  
 `result`  
 必要。 Any `String` 或 `Object` variable。  
  
 `expression1`  
 必要。 具有擴展至之資料類型的任何運算式 `String` 。  
  
 `expression2`  
 必要。 具有擴展至之資料類型的任何運算式 `String` 。  
  
## <a name="remarks"></a>備註  
 如果或的資料類型 `expression1` `expression2` 不是 `String` ，而是擴大 `String` 到，則會將它轉換成 `String` 。 如果其中一種資料類型不會擴展到 `String` ，編譯器會產生錯誤。  
  
 的資料類型 `result` 為 `String` 。 如果其中一個或兩個運算式評估為不是[任何](../nothing.md)值，或其值為 <xref:System.DBNull.Value?displayProperty=nameWithType> ，則會將它們視為字串，其值為 ""。  
  
> [!NOTE]
> `&`運算子可以多載*overloaded*，這表示當運算元具有該類別或結構的類型時，類別或結構可以重新定義其行為。 如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。  
  
> [!NOTE]
> & 符號（&）字元也可以用來將變數識別為類型 `Long` 。 如需詳細資訊，請參閱[類型字元](../../programming-guide/language-features/data-types/type-characters.md)。  
  
## <a name="example"></a>範例  
 這個範例會使用 `&` 運算子來強制執行字串串連。 結果為字串值，表示兩個字串運算元的串連。  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>另請參閱

- [&= 運算子](and-assignment-operator.md)
- [串連運算子](concatenation-operators.md)
- [Visual Basic 中的運算子優先順序](operator-precedence.md)
- [依功能列出運算子](operators-listed-by-functionality.md)
- [Visual Basic 中的串連運算子](../../programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
