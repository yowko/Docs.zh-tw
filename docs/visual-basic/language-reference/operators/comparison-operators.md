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
ms.openlocfilehash: bcd51d70c5c7bd08991c7433e244316a82daa9da
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371787"
---
# <a name="comparison-operators-visual-basic"></a>比較運算子 (Visual Basic)
以下是在 Visual Basic 中定義的比較運算子。

 `<`操作

 `<=`操作

 `>`操作

 `>=`操作

 `=`操作

 `<>`操作

 [Is 運算子](is-operator.md)

 [IsNot 運算子](isnot-operator.md)

 [Like 運算子](like-operator.md)

 這些運算子會比較兩個運算式，以判斷它們是否相等，如果不是，則會有何差異。 `Is``IsNot` `Like` 個別的說明頁面會詳細討論、和。 本頁面會詳細討論關聯式比較運算子。

## <a name="syntax"></a>語法
  
```vb
result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a>組件
 `result`  
 必要。 `Boolean`值，表示比較的結果。

 `expression1`, `expression2`  
 必要。 任何運算式。

 `comparisonoperator`  
 必要。 任何關聯式比較運算子。

 `object1`, `object2`  
 必要。 任何參考物件名稱。

 `string`  
 必要。 任何 `String` 運算式。

 `pattern`  
 必要。 任何 `String` 運算式或字元範圍。

## <a name="remarks"></a>備註
 下表包含關聯式比較運算子的清單，以及判斷是否 `result` 為或的條件 `True` `False` 。

|運算子|`True` - |`False` - |
|--------------|---------------|----------------|
|`<`（小於）|`expression1` < `expression2`|`expression1` >= `expression2`|
|`<=`（小於或等於）|`expression1` <= `expression2`|`expression1` > `expression2`|
|`>`（大於）|`expression1` > `expression2`|`expression1` <= `expression2`|
|`>=`（大於或等於）|`expression1` >= `expression2`|`expression1` < `expression2`|
|`=`（等於）|`expression1` = `expression2`|`expression1` <> `expression2`|
|`<>`（不等於）|`expression1` <> `expression2`|`expression1` = `expression2`|

> [!NOTE]
> [= 運算子](assignment-operator.md)也會用來做為指派運算子。

 `Is`運算子、 `IsNot` 運算子和 `Like` 運算子具有與上表中運算子不同的特定比較功能。

## <a name="comparing-numbers"></a>比較數位
 當您比較類型 `Single` 的運算式與類型之一時 `Double` ， `Single` 運算式會轉換成 `Double` 。 這種行為與 Visual Basic 6 中找到的行為相反。

 同樣地，當您將類型的運算式與類型或的運算式進行比較時， `Decimal` `Single` `Double` `Decimal` 運算式會轉換成 `Single` 或 `Double` 。 若為 `Decimal` 運算式，任何小於 1e-28 的小數值可能會遺失。 這類小數值遺失可能會導致兩個值在不相等時進行比較。 基於這個理由，您應該小心使用相等（ `=` ）來比較兩個浮點變數。 測試兩個數字之間的差值絕對值是否小於較小的可接受容錯，是比較安全的作法。

### <a name="floating-point-imprecision"></a>浮點不精確
 當您使用浮點數時，請記住它們不一定會在記憶體中有精確的標記法。 這可能會導致某些作業產生非預期的結果，例如值比較和[Mod 運算子](mod-operator.md)。 如需詳細資訊，請參閱針對[資料類型進行疑難排解](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)。

## <a name="comparing-strings"></a>比較字串
 當您比較字串時，字串運算式會根據其順序排序次序進行評估，這取決於 `Option Compare` 設定。

 `Option Compare Binary`根據從字元的內部二進位標記法衍生的排序次序，建立字串比較的基礎。 排序次序是由字碼頁所決定。 下列範例顯示典型的二進位排序次序。

 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

 `Option Compare Text`根據您應用程式的地區設定所決定的區分大小寫、文字排序次序來建立字串比較。 當您設定 `Option Compare Text` 和排序上述範例中的字元時，會套用下列文字排序次序：

 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`

### <a name="locale-dependence"></a>地區設定相關性
 當您設定時 `Option Compare Text` ，字串比較的結果可能取決於應用程式執行的地區設定。 在一個地區設定中，兩個字元可能會比較成相等，但另一個則不會。 如果您使用字串比較來做出重要決策，例如是否要接受登入的嘗試，您應該會在區分地區設定的情況下發出警示。 請考慮設定 `Option Compare Binary` 或呼叫 <xref:Microsoft.VisualBasic.Strings.StrComp%2A> ，這會將地區設定納入考慮。

## <a name="typeless-programming-with-relational-comparison-operators"></a>使用關聯式比較運算子進行無程式設計
 下不允許使用具有運算式的關聯式比較運算子 `Object` `Option Strict On` 。 當 `Option Strict` 為 `Off` ，且 `expression1` 或 `expression2` 為運算式時 `Object` ，執行時間類型會決定它們的比較方式。 下表顯示如何比較運算式和比較的結果，端視運算元的執行時間類型而定。

|如果運算元為|比較|
|---------------------|-------------------|
|既`String`|根據字串排序特性排序比較。|
|兩者都是數值|轉換成 `Double` 的物件，數值比較。|
|一個數值和一個`String`|`String`會轉換成 `Double` ，並執行數值比較。 如果 `String` 無法轉換成 `Double` ， <xref:System.InvalidCastException> 則會擲回。|
|或兩者都是以外的參考型別`String`|擲回 <xref:System.InvalidCastException>。|

 數值比較會視為 `Nothing` 0。 字串比較會 `Nothing` 視為 `""` （空字串）。

## <a name="overloading"></a>多載化
 關聯式比較運算子（ `<` 。 `<=`、 `>` 、 `>=` 、 `=` 、 `<>` ）可以多*overloaded*載，這表示當運算元具有該類別或結構的類型時，類別或結構可以重新定義其行為。 如果您的程式碼在這類類別或結構上使用上述任何運算子，請務必瞭解已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。

 請注意， [= 運算子](assignment-operator.md)只能多載為關聯式比較運算子，而不是指派運算子。

## <a name="example"></a>範例
 下列範例顯示關聯式比較運算子的各種用法，您可以用來比較運算式。 關聯式比較運算子會傳回一個 `Boolean` 結果，表示指定的運算式是否評估為 `True` 。 當您將 `>` 和 `<` 運算子套用至字串時，會使用字串的一般字母順序排序來進行比較。 此順序可能取決於您的地區設定。 排序是否區分大小寫，或不取決於 [[選項比較](../statements/option-compare-statement.md)] 設定。

 [!code-vb[VbVbalrOperators#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#1)]

 在上述範例中，第一個比較會傳回 `False` ，而其餘的比較則會傳回 `True` 。

## <a name="see-also"></a>另請參閱

- <xref:System.InvalidCastException>
- [= 運算子](assignment-operator.md)
- [Visual Basic 中的運算子優先順序](operator-precedence.md)
- [依功能列出運算子](operators-listed-by-functionality.md)
- [疑難排解資料類型的問題](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Comparison Operators in Visual Basic](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
