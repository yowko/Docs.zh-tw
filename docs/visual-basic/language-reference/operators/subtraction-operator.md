---
title: '- 運算子'
ms.date: 07/20/2015
f1_keywords:
- vb.Negate
- vb.-
helpviewer_keywords:
- operator [Visual Basic]
- operators [Visual Basic], subtraction
- operators [Visual Basic], difference
- negation operator [Visual Basic]
- operators [Visual Basic], arithmetic
- subtraction operator [Visual Basic], syntax
- arithmetic operators [Visual Basic], subtraction
- difference operator [Visual Basic]
- math operators [Visual Basic]
- operators [Visual Basic], negation
- minus operator [Visual Basic]
ms.assetid: bff2c368-662d-4c92-ac87-1d9bdfd3426a
ms.openlocfilehash: 9687c366c5b23693c05ab5c6b34f50c04131dfda
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348229"
---
# <a name="--operator-visual-basic"></a>- 運算子 (Visual Basic)
傳回兩個數值運算式之間的差異，或數值運算式的負數值。  
  
## <a name="syntax"></a>語法  
  
```vb  
expression1 – expression2
```
  
或

```vb  
–expression1  
```  
  
## <a name="parts"></a>組件  
 `expression1`  
 必要。 任何數值運算式。  
  
 `expression2`  
 除非 `–` 運算子正在計算負數值，否則為必要。 任何數值運算式。  
  
## <a name="result"></a>結果  
 結果是 `expression1` 和 `expression2`之間的差異，或 `expression1`的負值。  
  
 結果資料類型是適用于 `expression1` 和 `expression2`的資料類型的數數值型別。 請參閱[運算子結果的資料類型](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)中的「整數算術」資料表。  
  
## <a name="supported-types"></a>支援的型別  
 所有數值類型。 這包括不帶正負號的和浮點類型，以及 `Decimal`。  
  
## <a name="remarks"></a>備註  
 在先前所示的語法中，第一次使用時，`–` 運算子是*二元*算術減法運算子，用於兩個數值運算式之間的差異。  
  
 在先前所示語法中所顯示的第二個使用方式中，`–` 運算子是運算式之負值的*一元*負運算子。 就這一點而言，否定是由反轉 `expression1` 的正負號所組成，因此如果 `expression1` 為負數，則結果為正數。  
  
 如果任一運算式評估為不是[任何](../../../visual-basic/language-reference/nothing.md)值，`–` 運算子會將它視為零。  
  
> [!NOTE]
> `–` 運算子可以多載 *，這*表示當運算元具有該類別或結構的類型時，類別或結構可以重新定義其行為。 如果您的程式碼在這類類別或結構上使用這個運算子，請確定您瞭解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用 `–` 運算子來計算並傳回兩個數字之間的差異，然後再將數位否定。  
  
 [!code-vb[VbVbalrOperators#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#10)]  
  
 執行這些語句之後，`binaryResult` 包含124.45 和 `unaryResult` contains –334.90。  
  
## <a name="see-also"></a>另請參閱

- [-= 運算子（Visual Basic）](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic 中的算術運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
