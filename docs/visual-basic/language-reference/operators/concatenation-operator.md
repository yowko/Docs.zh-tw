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
ms.openlocfilehash: 20c2e2088691e68221872cc1dfc5486413515a4d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867156"
---
# <a name="amp-operator-visual-basic"></a>&amp; 運算子 (Visual Basic) 

產生兩個運算式的字串串連。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
result = expression1 & expression2  
```  
  
## <a name="parts"></a>組件  

 `result`  
 必要。 任何 `String` 或 `Object` 變數。  
  
 `expression1`  
 必要。 具有擴展至之資料類型的任何運算式 `String` 。  
  
 `expression2`  
 必要。 具有擴展至之資料類型的任何運算式 `String` 。  
  
## <a name="remarks"></a>備註  

 如果或的資料類型 `expression1` `expression2` 不是 `String` 擴展至，則 `String` 會轉換成 `String` 。 如果其中一種資料類型不會擴展至 `String` ，則編譯器會產生錯誤。  
  
 的資料類型 `result` 為 `String` 。 如果其中一或兩個運算式評估為 [Nothing](../nothing.md) 或值為 <xref:System.DBNull.Value?displayProperty=nameWithType> ，則會將它們視為字串，其值為 ""。  
  
> [!NOTE]
> 可以多載 `&` 運算子*overloaded*，這表示當運算元具有該類別或結構的型別時，類別或結構可以重新定義其行為。 如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。  
  
> [!NOTE]
> 連字號 ( # A0) 字元也可以用來將變數識別為類型 `Long` 。 如需詳細資訊，請參閱 [類型字元](../../programming-guide/language-features/data-types/type-characters.md)。  
  
## <a name="example"></a>範例  

 這個範例會使用 `&` 運算子來強制執行字串串連。 結果是字串值，表示兩個字串運算元的串連。  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>另請參閱

- [&= 運算子](and-assignment-operator.md)
- [串連運算子](concatenation-operators.md)
- [Visual Basic 中的運算子優先順序](operator-precedence.md)
- [依功能列出運算子](operators-listed-by-functionality.md)
- [Visual Basic 中的串連運算子](../../programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
