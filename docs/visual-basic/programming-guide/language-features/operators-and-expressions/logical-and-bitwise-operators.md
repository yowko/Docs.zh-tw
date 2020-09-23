---
title: 邏輯運算子和位元運算子
ms.date: 07/20/2015
helpviewer_keywords:
- short-circuiting
- Boolean expressions
- logical operators [Visual Basic], Boolean expressions
- operators [Visual Basic], logical
- AndAlso operator [Visual Basic]
- Not operator [Visual Basic], Boolean expressions
- Xor operator [Visual Basic], Boolean expressions
- And operator [Visual Basic], logical operators
- logical operators [Visual Basic]
- expressions [Visual Basic], Boolean
- Or operator [Visual Basic], logical operators
- Visual Basic code, operators
- short-circuiting [Visual Basic], logical operators
- logical operators [Visual Basic], short-circuiting
- Visual Basic code, expressions
- logical operators [Visual Basic], binary
- OrElse operator [Visual Basic]
- logical operators [Visual Basic], unary
ms.assetid: ca474e13-567d-4b1d-a18b-301433705e57
ms.openlocfilehash: c15b9337f262563941699c0ff8fe5219ca6a5c93
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085993"
---
# <a name="logical-and-bitwise-operators-in-visual-basic"></a>Visual Basic 中的邏輯運算子和位元運算子

邏輯運算子會比較 `Boolean` 運算式並傳回 `Boolean` 結果。 `And`、、 `Or` `AndAlso` 、 `OrElse` 和 `Xor` 運算子是*二元*的，因為它們採用兩個運算元，而 `Not` 運算子是*一元*，因為它採用單一運算元。 其中某些運算子也可以對整數值執行位邏輯運算。  
  
## <a name="unary-logical-operator"></a>一元邏輯運算子  

 [Not 運算子會](../../../language-reference/operators/not-operator.md)對運算式*negation*執行邏輯否定 `Boolean` 。 它會產生相對於其運算元的邏輯。 如果運算式評估為 `True` ，則會 `Not` 傳回 `False` ; 如果運算式評估為 `False` ，則 `Not` `True` 會傳回。 下列範例將說明這點。  
  
 [!code-vb[VbVbalrOperators#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#77)]  
  
## <a name="binary-logical-operators"></a>二元邏輯運算子  

 [And 運算子](../../../language-reference/operators/and-operator.md)會在兩個運算式上執行邏輯*結合* `Boolean` 。 如果兩個運算式都評估為 `True` ，則會傳回 `And` `True` 。 如果至少有一個運算式評估為 `False` ，則會傳回 `And` `False` 。  
  
 [Or 運算子](../../../language-reference/operators/or-operator.md)會在兩個運算式上*執行邏輯分離*或*包含* `Boolean` 。 如果任一個運算式評估為 `True` ，或兩者都評估為 `True` ，則會傳回 `Or` `True` 。 如果兩個運算式都未評估為，就會傳回 `True` `Or` `False` 。  
  
 [Xor 運算子](../../../language-reference/operators/xor-operator.md)會在兩個運算式上執行邏輯*排除* `Boolean` 。 如果只有一個運算式評估為 `True` （但不是兩者），則會傳回 `Xor` `True` 。 如果兩個運算式都評估為 `True` 或兩者都評估為，則會傳回 `False` `Xor` `False` 。  
  
 下列範例說明 `And` 、 `Or` 和 `Xor` 運算子。  
  
 [!code-vb[VbVbalrOperators#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#78)]  
  
## <a name="short-circuiting-logical-operations"></a>短路邏輯作業  

 [AndAlso 運算子](../../../language-reference/operators/andalso-operator.md)與運算子非常類似 `And` ，因為它也會在兩個運算式上執行邏輯結合 `Boolean` 。 兩者之間的主要差異在於 `AndAlso` 展現 *短路* 行為。 如果運算式中的第一個運算式 `AndAlso` 評估為 `False` ，則不會評估第二個運算式，因為它無法改變最後的結果，而且會傳回 `AndAlso` `False` 。  
  
 同樣地， [OrElse 運算子](../../../language-reference/operators/orelse-operator.md) 會在兩個運算式上執行最少運算邏輯分離 `Boolean` 。 如果運算式中的第一個運算式 `OrElse` 評估為 `True` ，則不會評估第二個運算式，因為它無法改變最後的結果，而且會傳回 `OrElse` `True` 。  
  
### <a name="short-circuiting-trade-offs"></a>短路取捨  

 最少運算可以藉由不評估無法改變邏輯運算結果的運算式，來改善效能。 但是，如果該運算式執行其他動作，則會略過這些動作。 例如，如果運算式包含對程式的呼叫，則 `Function` 不會在運算式縮短時呼叫該程式，而且所包含的任何其他程式碼都不會 `Function` 執行。 因此，函式可能只會偶爾執行，而且可能無法正確地進行測試。 或者，程式邏輯可能相依于中的程式碼 `Function` 。  
  
 下列範例說明 `And` 、 `Or` 和它們的短路對應專案之間的差異。  
  
 [!code-vb[VbVbalrOperators#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#81)]  
  
 [!code-vb[VbVbalrOperators#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#80)]  
  
 [!code-vb[VbVbalrOperators#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#79)]  
  
 在上述範例中，請注意，不會在 `checkIfValid()` 呼叫縮短時執行內的一些重要程式碼。 第一個 `If` 語句 `checkIfValid()` 會呼叫，即使傳回，也是一樣 `12 > 45` `False` ，因為不 `And` 會短路。 第二個 `If` 語句不會呼叫 `checkIfValid()` ，因為當傳回時 `12 > 45` ，會 `False` `AndAlso` 將第二個運算式縮短。 第三個 `If` 語句 `checkIfValid()` 會呼叫，即使傳回，也是一樣 `12 < 45` `True` ，因為不 `Or` 會短路。 第四個 `If` 語句不會呼叫 `checkIfValid()` ，因為當傳回時 `12 < 45` ，會 `True` `OrElse` 將第二個運算式縮短。  
  
## <a name="bitwise-operations"></a>位運算  

 位運算會以二進位 (基底 2) 形式來評估兩個整數值。 它們會比較對應位置的位，然後根據比較來指派值。 下列範例說明 `And` 運算子。  
  
 [!code-vb[VbVbalrConcepts#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#2)]  
  
 上述範例會將的值設定 `x` 為1。 發生此問題的原因如下：  
  
- 這些值會視為二進位：  
  
     3二進位格式 = 011  
  
     5（二進位格式 = 101）  
  
- `And`運算子會比較二進位標記法，一個二進位位置 (位) 一次。 如果指定位置的兩個位都是1，則會在結果中將1放在該位置。 如果任一個位為0，則結果中會將0放在該位置。 在上述範例中，這會以下面方式運作：  
  
     binary 格式的 011 (3)   
  
     101 (5 二進位格式)   
  
     001 (結果，以二進位格式)   
  
- 結果會被視為 decimal。 值001是1的二進位標記法，因此 `x` = 1。  
  
 位 `Or` 運算很類似，不同之處在于如果其中一或兩個比較的位為1，則會將1指派給結果位。 `Xor` 如果只有一個比較的位 (不是兩個) 都是1，則會將1指派給結果位。 `Not` 採用單一運算元並反轉所有位（包括正負號位），並將該值指派給結果。 這表示對於帶正負號的正數，一律會傳回 `Not` 負值，而針對負數，一律會傳回 `Not` 正值或零值。  
  
 `AndAlso`和 `OrElse` 運算子不支援位運算。  
  
> [!NOTE]
> 位運算只能在整數類型上執行。 必須先將浮點值轉換成整數類資料類型，然後才能繼續進行位運算。  
  
## <a name="see-also"></a>另請參閱

- [邏輯/位元運算子 (Visual Basic)](../../../language-reference/operators/logical-bitwise-operators.md)
- [布林運算式](boolean-expressions.md)
- [Visual Basic 的算術運算子](arithmetic-operators.md)
- [Comparison Operators in Visual Basic](comparison-operators.md)
- [Visual Basic 中的串連運算子](concatenation-operators.md)
- [有效的運算子組合](efficient-combination-of-operators.md)
