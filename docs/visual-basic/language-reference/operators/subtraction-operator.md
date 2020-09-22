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
ms.openlocfilehash: b5129c2dbb361940fa6da2cb424ee23736ba72c5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875336"
---
# <a name="--operator-visual-basic"></a>- 運算子 (Visual Basic)

傳回兩個數值運算式或數值運算式的負數值之間的差異。  
  
## <a name="syntax"></a>Syntax  
  
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
 除非 `–` 運算子計算負數值，否則為必要項。 任何數值運算式。  
  
## <a name="result"></a>結果  

 結果是和之間的差異 `expression1` `expression2` ，或的負數值 `expression1` 。  
  
 結果資料類型是適用于和之資料類型的數數值型別 `expression1` `expression2` 。 請參閱 [運算子結果資料類型](data-types-of-operator-results.md)中的「整數算術」資料表。  
  
## <a name="supported-types"></a>支援的型別  

 所有數值類型。 這包括不帶正負號的和浮點數類型和 `Decimal` 。  
  
## <a name="remarks"></a>備註  

 在先前所顯示的語法中， `–` 運算子是兩個數值運算式之間差異的 *二進位* 算術減法運算子。  
  
 在先前所顯示的語法中， `–` 運算子是運算式負數值的 *一元* 負運算子。 在這種情況下，負號包含反轉的正負號， `expression1` 因此如果是負數，則結果為正數 `expression1` 。  
  
 如果任一個運算式評估為 [Nothing](../nothing.md)， `–` 運算子就會將它視為零。  
  
> [!NOTE]
> 可以多載 `–` 運算子*overloaded*，這表示當運算元具有該類別或結構的型別時，類別或結構可以重新定義其行為。 如果您的程式碼在這類類別或結構上使用這個運算子，請確定您瞭解其重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  

 下列範例會使用 `–` 運算子來計算並傳回兩個數字之間的差異，然後再對數位進行否定。  
  
 [!code-vb[VbVbalrOperators#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#10)]  
  
 執行這些語句之後，會 `binaryResult` 包含124.45 且 `unaryResult` contains –334.90。  
  
## <a name="see-also"></a>另請參閱

- [-= 運算子 (Visual Basic) ](subtraction-assignment-operator.md)
- [算術運算子](arithmetic-operators.md)
- [Visual Basic 中的運算子優先順序](operator-precedence.md)
- [依功能列出運算子](operators-listed-by-functionality.md)
- [Visual Basic 的算術運算子](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
