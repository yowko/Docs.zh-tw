---
title: 比較運算子
ms.date: 07/20/2015
f1_keywords:
- vb.<>
- vb.>=
- vb.<=
- vb.>
- vb.<
helpviewer_keywords:
- greater than or equal to operator [Visual Basic]
- '>= operator [Visual Basic]'
- = operator [Visual Basic]
- < operator [Visual Basic]
- less than operator [Visual Basic]
- relational operators [Visual Basic], syntax
- Like operator [Visual Basic]
- <> operator [Visual Basic]
- '> operator [Visual Basic]'
- equal operator [Visual Basic]
- less than or equal to operator [Visual Basic]
- symbols, operators
- greater than operator [Visual Basic]
- comparing values [Visual Basic]
- operators [Visual Basic], relational
- string comparison [Visual Basic]
- not equal to comparison operator [Visual Basic]
- <= operator [Visual Basic]
- operators [Visual Basic], comparison
- Is operator [Visual Basic]
- comparison operators [Visual Basic], Visual Basic
ms.assetid: d6cb12a8-e52e-46a7-8aaf-f804d634a825
ms.openlocfilehash: fcbb9052a79fa4b20b5a0f8fdc15de73d55a4281
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873439"
---
# <a name="comparison-operators-visual-basic"></a>比較運算子 (Visual Basic)

以下是 Visual Basic 中定義的比較運算子。

 `<` 運算元

 `<=` 運算元

 `>` 運算元

 `>=` 運算元

 `=` 運算元

 `<>` 運算元

 [Is 運算子](is-operator.md)

 [IsNot 運算子](isnot-operator.md)

 [Like 運算子](like-operator.md)

 這些運算子會比較兩個運算式，判斷它們是否相等，如果不相等，則會有何不同。 `Is`、 `IsNot` 和 `Like` 會詳細討論個別的說明頁面。 本頁面將詳細討論關係比較運算子。

## <a name="syntax"></a>Syntax
  
```vb
result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a>組件

 `result`  
 必要。 `Boolean`代表比較結果的值。

 `expression1`, `expression2`  
 必要。 任何運算式。

 `comparisonoperator`  
 必要。 任何關係比較運算子。

 `object1`, `object2`  
 必要。 任何參考物件名稱。

 `string`  
 必要。 任何 `String` 運算式。

 `pattern`  
 必要。 任何 `String` 運算式或字元範圍。

## <a name="remarks"></a>備註

 下表包含關聯式比較運算子的清單，以及決定是否 `result` 為或的條件 `True` `False` 。

|運算子|`True` - |`False` - |
|--------------|---------------|----------------|
|`<` (小於) |`expression1` < `expression2`|`expression1` >= `expression2`|
|`<=` (小於或等於) |`expression1` <= `expression2`|`expression1` > `expression2`|
|`>` (大於) |`expression1` > `expression2`|`expression1` <= `expression2`|
|`>=` (大於或等於) |`expression1` >= `expression2`|`expression1` < `expression2`|
|`=` (等於) |`expression1` = `expression2`|`expression1` <> `expression2`|
|`<>` (不等於) |`expression1` <> `expression2`|`expression1` = `expression2`|

> [!NOTE]
> [= 運算子](assignment-operator.md)也可做為指派運算子。

 `Is`運算子、 `IsNot` 運算子和 `Like` 運算子具有與上表中運算子不同的特定比較功能。

## <a name="comparing-numbers"></a>比較數位

 當您比較型別的運算式 `Single` 與型別的其中一個時 `Double` ， `Single` 運算式會轉換成 `Double` 。 這種行為與 Visual Basic 6 中找到的行為相反。

 同樣地，當您比較型別的運算式 `Decimal` 與型別或的運算式時 `Single` `Double` ， `Decimal` 運算式會轉換成 `Single` 或 `Double` 。 若為 `Decimal` 運算式，任何小於 1e-28 的小數值可能都會遺失。 這類小數值遺失可能會導致兩個值在不相等時進行比較。 基於這個理由，當您使用相等 (`=`) 來比較兩個浮點數變數時，應該要特別小心。 測試兩個數字之間差異的絕對值是否小於小型可接受的容錯，是比較安全的做法。

### <a name="floating-point-imprecision"></a>浮點數不精確

 當您使用浮點數時，請記住它們不一定會在記憶體中有精確的標記法。 這可能會導致某些作業（例如值比較和 [Mod 運算子](mod-operator.md)）發生非預期的結果。 如需詳細資訊，請參閱 [疑難排解資料類型](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)。

## <a name="comparing-strings"></a>比較字串

 當您比較字串時，系統會根據其依字母順序排序次序來評估字串運算式，這取決於 `Option Compare` 設定。

 `Option Compare Binary` 根據從字元的內部二進位標記法衍生的排序次序來比較字串。 排序次序是由字碼頁所決定。 下列範例顯示一般的二進位排序次序。

 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

 `Option Compare Text` 根據您應用程式的地區設定，以不區分大小寫的文字排序次序來基底字串比較。 當您設定 `Option Compare Text` 和排序上述範例中的字元時，會套用下列文字排序次序：

 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`

### <a name="locale-dependence"></a>地區設定相關性

 當您設定時 `Option Compare Text` ，字串比較的結果可能會根據應用程式執行所在的地區設定而定。 兩個字元可能會在同一個地區設定中比較為相等，但在另一個地區設定中 如果您使用字串比較來進行重要的決策（例如是否要接受登入的嘗試），您應該會在區分地區設定時發出警示。 請考慮設定 `Option Compare Binary` 或呼叫 <xref:Microsoft.VisualBasic.Strings.StrComp%2A> ，這會將地區設定納入考慮。

## <a name="typeless-programming-with-relational-comparison-operators"></a>使用關聯式比較運算子的無語言程式設計

 不允許使用具有運算式的關聯式比較運算子 `Object` `Option Strict On` 。 當 `Option Strict` 為時 `Off` ，且 `expression1` 或 `expression2` 為 `Object` 運算式時，執行時間類型會決定如何比較它們。 下表顯示如何比較運算式以及比較的結果，視運算元的執行時間型別而定。

|如果運算元為|比較是|
|---------------------|-------------------|
|對 `String`|以字串排序特性為基礎的排序比較。|
|這兩個數值|轉換成 `Double` 數值比較的物件。|
|一個數值和一個 `String`|`String`會轉換成 `Double` ，並執行數值比較。 如果 `String` 無法轉換為 `Double` ， <xref:System.InvalidCastException> 則會擲回。|
|其中一個或兩個都是以外的參考類型 `String`|擲回 <xref:System.InvalidCastException>。|

 數值比較視為 `Nothing` 0。 字串比較視為 `Nothing` `""` (空的字串) 。

## <a name="overloading"></a>多載化

 關聯式比較運算子 (`<` 。 `<=`、 `>` 、 `>=` 、 `=` 、 `<>`) 可以多*overloaded*載，這表示當運算元的類型為該類別或結構時，類別或結構可以重新定義其行為。 如果您的程式碼在這類類別或結構上使用上述任何運算子，請務必瞭解重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。

 請注意， [= 運算子](assignment-operator.md) 只能以關聯式比較運算子來多載，而不能以指派運算子的方式多載。

## <a name="example"></a>範例

 下列範例會示範用於比較運算式的各種關聯式比較運算子用途。 關聯式比較運算子會傳回 `Boolean` 結果，表示指定的運算式是否評估為 `True` 。 當您將 `>` 和 `<` 運算子套用至字串時，會使用字串的一般字母順序排序來進行比較。 此順序可能取決於您的地區設定。 排序是否區分大小寫，或不相依于 [選項比較](../statements/option-compare-statement.md) 設定。

 [!code-vb[VbVbalrOperators#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#1)]

 在上述範例中，第一個比較會傳回， `False` 而其餘的比較會傳回 `True` 。

## <a name="see-also"></a>另請參閱

- <xref:System.InvalidCastException>
- [= 運算子](assignment-operator.md)
- [Visual Basic 中的運算子優先順序](operator-precedence.md)
- [依功能列出運算子](operators-listed-by-functionality.md)
- [疑難排解資料類型的問題](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Comparison Operators in Visual Basic](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
