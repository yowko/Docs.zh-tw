---
title: '* 運算子'
ms.date: 07/20/2015
f1_keywords:
- vb.*
helpviewer_keywords:
- arithmetic operators [Visual Basic], multiplication
- operators [Visual Basic], multiplication
- '* operator [Visual Basic]'
- multiplication operator [Visual Basic], syntax
- math operators [Visual Basic]
ms.assetid: 2b210382-99da-4195-89ba-b1d06f5e89ad
ms.openlocfilehash: 7038fef4258d190b726a851b26f2a2840ff3c0ea
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873369"
---
# <a name="-operator-visual-basic"></a>* 運算子 (Visual Basic)

兩個數目相乘。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
number1 * number2  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`number1`|必要。 任何數值運算式。|  
|`number2`|必要。 任何數值運算式。|  
  
## <a name="result"></a>結果  

 結果會是和的乘積 `number1` `number2` 。  
  
## <a name="supported-types"></a>支援的型別  

 所有數數值型別，包括不帶正負號的和浮點數類型，以及 `Decimal` 。  
  
## <a name="remarks"></a>備註  

 結果的資料類型取決於運算元的類型。 下表顯示如何決定結果的資料類型。  
  
|運算元資料類型|結果資料類型|  
|---|---|  
|這兩個運算式都是整數資料類型 ([SByte](../data-types/sbyte-data-type.md)、 [Byte](../data-types/byte-data-type.md)、 [Short](../data-types/short-data-type.md)、 [UShort](../data-types/ushort-data-type.md)、 [Integer](../data-types/integer-data-type.md)、 [UInteger](../data-types/uinteger-data-type.md)、 [Long](../data-types/long-data-type.md)、 [ULong](../data-types/ulong-data-type.md)) |適用于和之資料類型的數值資料類型 `number1` `number2` 。 請參閱 [運算子結果資料類型](data-types-of-operator-results.md)中的「整數算術」資料表。|  
|這兩個運算式都是 [Decimal](../data-types/decimal-data-type.md)|`Decimal`|  
|這兩個運算式都是 [Single](../data-types/single-data-type.md)|`Single`|  
|任一個運算式是浮點數資料類型 (`Single` 或 [Double](../data-types/double-data-type.md)) 但不是兩個 `Single` (附注都不是 `Decimal` 浮點數資料類型) |`Double`|  
  
 如果運算式評估為 [Nothing](../nothing.md)，則會將其視為零。  
  
## <a name="overloading"></a>多載化  

 可以多載 `*` 運算子*overloaded*，這表示當運算元具有該類別或結構的型別時，類別或結構可以重新定義其行為。 如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  

 這個範例會使用 `*` 運算子來將兩個數字相乘。 結果會是兩個運算元的乘積。  
  
 [!code-vb[VbVbalrOperators#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#4)]  
  
## <a name="see-also"></a>另請參閱

- [* = 運算子](multiplication-assignment-operator.md)
- [算術運算子](arithmetic-operators.md)
- [Visual Basic 中的運算子優先順序](operator-precedence.md)
- [依功能列出運算子](operators-listed-by-functionality.md)
- [Visual Basic 的算術運算子](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
