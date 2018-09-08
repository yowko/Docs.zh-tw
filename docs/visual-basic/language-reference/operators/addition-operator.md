---
title: + 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.+
helpviewer_keywords:
- arithmetic operators [Visual Basic], addition
- + operator
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
- sum operator [Visual Basic]
ms.assetid: 5694778f-0a2c-4539-8009-f66f318fb46d
ms.openlocfilehash: 91806c204c313956b292eb9c9be078991f733b4e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44188523"
---
# <a name="-operator-visual-basic"></a>+ 運算子 (Visual Basic)
兩個數字相加，或傳回數值運算式的正值。 也可以用來串連兩個字串運算式。  
  
## <a name="syntax"></a>語法  
  
```vb
expression1 + expression2  
- or -  
+ expression1  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`expression1`|必要。 任何數值或字串的運算式。|  
|`expression2`|除非`+`運算子會計算為負數值。 任何數值或字串的運算式。|  
  
## <a name="result"></a>結果  
 如果`expression1`和`expression2`兩者都是數值，結果就是其算術的總和。  
  
 如果`expression2`不存在，`+`運算子*一元*身分識別操作員未變更值的運算式。 在這種情況下，作業會組成保留正負號的`expression1`，結果為負的因此如果`expression1`為負數。  
  
 如果`expression1`和`expression2`都是字串，結果就是其值的串連。  
  
 如果`expression1`並`expression2`是混合的類型，所採取的動作取決於其類型、 其內容，以及設定[Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)。 如需詳細資訊，請參閱 < 備註 >。 中的資料表  
  
## <a name="supported-types"></a>支援的型別  
 所有的數字類型，包括不帶正負號和浮點類型和`Decimal`，和`String`。  
  
## <a name="remarks"></a>備註  
 一般情況下，`+`執行算術加法，如果可能的話，並串連僅當這兩個運算式都是字串。  
  
 如果兩個運算式是`Object`，Visual Basic 會採取下列動作。  
  
|資料類型的運算式|編譯器的動作|  
|---|---|  
|這兩個運算式都是數值資料類型 (`SByte`， `Byte`， `Short`， `UShort`， `Integer`， `UInteger`， `Long`， `ULong`， `Decimal`， `Single`，或`Double`)|新增。 將結果資料類型是數值類型適合的資料型別`expression1`和`expression2`。 請參閱中的 「 整數算術 」 表格[資料類型的運算子結果](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)。|  
|這兩個運算式屬於類型 `String`|串連。|  
|一個運算式為數值資料類型，另一個是字串|如果`Option Strict`是`On`，然後產生編譯器錯誤。<br /><br /> 如果`Option Strict`是`Off`，然後以隱含方式轉換`String`到`Double`並新增。<br /><br /> 如果`String`無法轉換成`Double`，然後擲回<xref:System.InvalidCastException>例外狀況。|  
|一個運算式為數值資料類型，而另一個是[Nothing](../../../visual-basic/language-reference/nothing.md)|新增，請使用`Nothing`值為零。|  
|一個運算式是字串，而且另一個則是 `Nothing`|串連，與`Nothing`值為""。|  
  
 如果一個運算式`Object`運算式中，Visual Basic 會採取下列動作。  
  
|資料類型的運算式|編譯器的動作|  
|---|---|  
|`Object` 運算式包含數值，另一個是數值資料類型|如果`Option Strict`是`On`，然後產生編譯器錯誤。<br /><br /> 如果`Option Strict`是`Off`，然後新增。|  
|`Object` 運算式會保留一個數字值，另一個是類型 `String`|如果`Option Strict`是`On`，然後產生編譯器錯誤。<br /><br /> 如果`Option Strict`是`Off`，然後以隱含方式轉換`String`到`Double`並新增。<br /><br /> 如果`String`無法轉換成`Double`，然後擲回<xref:System.InvalidCastException>例外狀況。|  
|`Object` 運算式會保留為字串，另一個是數值資料類型|如果`Option Strict`是`On`，然後產生編譯器錯誤。<br /><br /> 如果`Option Strict`是`Off`，然後以隱含方式將字串轉換`Object`到`Double`並新增。<br /><br /> 如果字串`Object`無法轉換成`Double`，然後擲回<xref:System.InvalidCastException>例外狀況。|  
|`Object` 運算式會保留為字串，另一個是類型 `String`|如果`Option Strict`是`On`，然後產生編譯器錯誤。<br /><br /> 如果`Option Strict`是`Off`，然後以隱含方式轉換`Object`到`String`和串連。|  
  
 如果這兩個運算式都`Object`運算式，Visual Basic 會採取下列動作 (`Option Strict Off`只)。  
  
|資料類型的運算式|編譯器的動作|  
|---|---|  
|兩者`Object`運算式保存數值|新增。|  
|兩者`Object`運算式屬於類型 `String`|串連。|  
|一個`Object`運算式包含數值，而其他則會保留字串|將字串隱含轉換`Object`至`Double`並新增。<br /><br /> 如果字串`Object`無法轉換成數值，則會擲回<xref:System.InvalidCastException>例外狀況。|  
  
 如果有任一個`Object`運算式會評估為[Nothing](../../../visual-basic/language-reference/nothing.md)或<xref:System.DBNull>，則`+`運算子會將其視為`String`值是""。  
  
> [!NOTE]
>  當您使用`+`運算子，可能無法判斷是否會發生加法或字串的串連。 使用`&`運算子串連消除模稜兩可，並提供自我記錄程式碼。  
  
## <a name="overloading"></a>多載化  
 `+`運算子只能*多載*，這表示，類別或結構可以重新定義其行為時運算元具有該類別或結構的型別。 如果您的程式碼會使用這個運算子，這類類別或結構上，請務必了解其已重新定義的行為。 如需詳細資訊，請參閱 <<c0> [ 運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`+`運算子，將數字。 如果運算元是數字的同時，Visual Basic 會計算算術的結果。 算術的結果表示兩個運算元的總和。  
  
 [!code-vb[VbVbalrOperators#6](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_1.vb)]  
  
 您也可以使用`+`運算子來串連字串。 如果運算元都是字串，Visual Basic 會串連它們。 串連結果代表接續所組成的兩個運算元其中一個內容的單一字串。  
  
 如果混合類型的運算元，結果會取決於設定[Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)。 下列範例說明結果時`Option Strict`是`On`。  
  
 [!code-vb[VbVbalrOperators#53](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_2.vb)]  
  
 [!code-vb[VbVbalrOperators#50](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_3.vb)]  
[!code-vb[VbVbalrOperators#51](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_4.vb)]  
  
 下列範例說明結果時`Option Strict`是`Off`。  
  
 [!code-vb[VbVbalrOperators#54](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_5.vb)]  
  
 [!code-vb[VbVbalrOperators#50](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_3.vb)]  
[!code-vb[VbVbalrOperators#52](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_6.vb)]  
  
 若要避免模稜兩可，您應該使用`&`運算子來取代`+`串連。  
  
## <a name="see-also"></a>另請參閱  
 [& 運算子](../../../visual-basic/language-reference/operators/concatenation-operator.md)  
 [串連運算子](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [在 Visual Basic 中的算術運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)
