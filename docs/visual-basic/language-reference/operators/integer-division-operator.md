---
title: '\ 運算子'
ms.date: 07/20/2015
f1_keywords:
- vb.\
- '\'
helpviewer_keywords:
- division operator [Visual Basic], integer
- integer division operator [Visual Basic]
- zero, division by zero
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- backslash (\) [Visual Basic]
- '\ operator [Visual Basic]'
- integer quotient
- math operators [Visual Basic]
- quotients, integer
- truncation [Visual Basic], integer division
ms.assetid: 4b0ee347-950c-45c9-8e23-54bc85df208e
ms.openlocfilehash: cf2dc66532925d56cea6fd141f44a245bc2dd8dd
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873388"
---
# <a name="-operator-visual-basic"></a>\ 運算子 (Visual Basic)

兩數相除並傳回整數結果。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
expression1 \ expression2  
```  
  
## <a name="parts"></a>組件  

 `expression1`  
 必要。 任何數值運算式。  
  
 `expression2`  
 必要。 任何數值運算式。  
  
## <a name="supported-types"></a>支援的型別  

 所有數數值型別，包括不帶正負號的和浮點數類型，以及 `Decimal` 。  
  
## <a name="result"></a>結果  

 結果是除以的整數商 `expression1` `expression2` ，這會捨棄任何餘數並只保留整數部分。 這就是所謂的 *截斷*。  
  
 結果資料類型是適用于和之資料類型的數數值型別 `expression1` `expression2` 。 請參閱 [運算子結果資料類型](data-types-of-operator-results.md)中的「整數算術」資料表。  
  
 [/運算子 (Visual Basic) ](floating-point-division-operator.md)會傳回完整的商，這會保留小數部分的餘數。  
  
## <a name="remarks"></a>備註  

 在執行除法之前，Visual Basic 會嘗試將任何浮點數運算式轉換成 `Long` 。 如果 `Option Strict` 為 `On` ，則會發生編譯器錯誤。 如果 `Option Strict` 為 `Off` ，則 <xref:System.OverflowException> 如果值超出 [LONG 資料型別](../data-types/long-data-type.md)的範圍，則可能。 的轉換 `Long` 也會受限於 *銀行家的舍入*。 如需詳細資訊，請參閱 [類型轉換](../functions/type-conversion-functions.md)函式中的「小數部分」。  
  
 如果 `expression1` 或 `expression2` 評估為 [Nothing](../nothing.md)，則會將其視為零。  
  
## <a name="attempted-division-by-zero"></a>嘗試除以零  

 如果 `expression2` 評估為零，則運算子會擲回 `\` <xref:System.DivideByZeroException> 例外狀況。 這適用于運算元的所有數值資料類型。  
  
> [!NOTE]
> 可以多載 `\` 運算子*overloaded*，這表示當運算元具有該類別或結構的型別時，類別或結構可以重新定義其行為。 如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  

 下列範例會使用 `\` 運算子來執行整數除法。 結果是一個整數，表示兩個運算元的整數商，並捨棄餘數。  
  
 [!code-vb[VbVbalrOperators#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#18)]  
  
 上述範例中的運算式會分別傳回2、3、33和-22 的值。  
  
## <a name="see-also"></a>另請參閱

- [\\= 運算子](integer-division-assignment-operator.md)
- [/運算子 (Visual Basic) ](floating-point-division-operator.md)
- [Long](../statements/option-strict-statement.md)
- [算術運算子](arithmetic-operators.md)
- [Visual Basic 中的運算子優先順序](operator-precedence.md)
- [依功能列出運算子](operators-listed-by-functionality.md)
- [Visual Basic 的算術運算子](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
