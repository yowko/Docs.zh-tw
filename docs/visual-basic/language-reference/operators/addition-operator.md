---
title: + 運算子（Visual Basic）
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
ms.openlocfilehash: 3187551afb7d25470f48dad894188766a811bb0a
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701003"
---
# <a name="-operator-visual-basic"></a>+ 運算子 (Visual Basic)
將兩個數字相加，或傳回數值運算式的正數值。 也可以用來串連兩個字串運算式。  
  
## <a name="syntax"></a>語法  
  
```vb
expression1 + expression2
```
  
或

```vb  
+expression1  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`expression1`|必要項。 任何數值或字串運算式。|  
|`expression2`|除非`+`運算子正在計算負數值，否則為必要。 任何數值或字串運算式。|  
  
## <a name="result"></a>結果  
 如果`expression1` 和`expression2`都是數值，則結果會是其算術總和。  
  
 如果 `expression2` 不存在，則 `+` 運算子是運算式未變更值的*一元*識別運算子。 就這一點而言，此作業包含保留的正負號`expression1`，因此如果`expression1`為負數，則結果為負數。  
  
 如果`expression1` 和`expression2`都是字串，則結果會是其值的串連。  
  
 如果 `expression1`，而 `expression2` 是混合類型，則採取的動作取決於其類型、其內容，以及[Option Strict 語句](../../../visual-basic/language-reference/statements/option-strict-statement.md)的設定。 如需詳細資訊，請參閱「備註」中的表格。  
  
## <a name="supported-types"></a>支援的型別  
 所有數數值型別，包括不帶正負號的和浮點類型`Decimal`，以及`String`和。  
  
## <a name="remarks"></a>備註  
 一般來說， `+`會在可能的情況下執行算術加法，而且只有在兩個運算式都是字串時，才會串連。  
  
 如果兩個運算式都`Object`不是，Visual Basic 會採取下列動作。  
  
|運算式的資料類型|由編譯器執行的動作|  
|---|---|  
|這兩個運算式都是數值`SByte`資料`Byte`類型（ `UShort`、 `Integer` `ULong` `UInteger` `Short` 、、`Single`、、 `Decimal` 、、`Double`、、或） `Long`|載入. 結果資料類型是適用于和`expression1` `expression2`之資料類型的數數值型別。 請參閱[運算子結果的資料類型](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)中的「整數算術」資料表。|  
|這兩個運算式的類型都是`String`|串連.|  
|一個運算式是數值資料類型，另一個則是字串|如果`Option Strict`為`On`，則會產生編譯器錯誤。<br /><br /> 如果`Option Strict`為`Off` ，`Double`則會隱含地將轉換成並加入。`String`<br /><br /> 如果無法轉換成`Double`，則會擲<xref:System.InvalidCastException>回例外狀況。 `String`|  
|一個運算式是數值資料類型，另一個則不是[任何](../../../visual-basic/language-reference/nothing.md)值|加入，其`Nothing`值為零。|  
|一個運算式是字串，另一個則是`Nothing`|串連，`Nothing` 的值為 ""。|  
  
 如果一個運算式是`Object`運算式，Visual Basic 會採取下列動作。  
  
|運算式的資料類型|由編譯器執行的動作|  
|---|---|  
|`Object`運算式會保存數值，另一個則是數值資料類型|如果`Option Strict`為`On`，則會產生編譯器錯誤。<br /><br /> 如果`Option Strict` 為`Off`，則新增。|  
|`Object`運算式會保存數值，另一個則屬於類型`String`|如果`Option Strict`為`On`，則會產生編譯器錯誤。<br /><br /> 如果`Option Strict`為`Off` ，`Double`則會隱含地將轉換成並加入。`String`<br /><br /> 如果無法轉換成`Double`，則會擲<xref:System.InvalidCastException>回例外狀況。 `String`|  
|`Object`運算式會保存字串，另一個則是數值資料類型|如果`Option Strict`為`On`，則會產生編譯器錯誤。<br /><br /> 如果`Option Strict`為`Off`，則會隱含地將`Object`字串`Double`轉換成並加入。<br /><br /> 如果字串`Object`無法轉換成`Double`，則會擲<xref:System.InvalidCastException>回例外狀況。|  
|`Object`運算式會保存一個字串，另一個則屬於類型`String`|如果`Option Strict`為`On`，則會產生編譯器錯誤。<br /><br /> 如果`Option Strict`為`Off`，則會隱含`Object`地`String`轉換為，並串連。|  
  
 如果兩個運算式`Object`都是運算式，Visual Basic 會採取下列`Option Strict Off`動作（僅限）。  
  
|運算式的資料類型|由編譯器執行的動作|  
|---|---|  
|兩`Object`個運算式都包含數值|載入.|  
|這`Object`兩個運算式的類型都是`String`|串連.|  
|一個`Object`運算式保存一個數值，另一個則保存一個字串|將字串`Object`隱含地轉換`Double`為，並加入。<br /><br /> 如果字串`Object`無法轉換為數值，則會<xref:System.InvalidCastException>擲回例外狀況。|  
  
 如果任`Object`一個運算式評估為[任何](../../../visual-basic/language-reference/nothing.md) 或 <xref:System.DBNull>`String`，`+`則運算子會將它視為具有值 "" 的。  
  
> [!NOTE]
> 當您使用`+`運算子時，可能無法判斷是否會進行加法或字串串連。 `&`使用運算子進行串連，以消除不明確的情況，並提供自我記錄程式碼。  
  
## <a name="overloading"></a>多載化  
 @No__t-0 運算子可以多載 *，這*表示當運算元具有該類別或結構的類型時，類別或結構可以重新定義其行為。 如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`+`運算子來加入數位。 如果運算元都是數值，Visual Basic 會計算算術結果。 算術結果表示兩個運算元的總和。  
  
 [!code-vb[VbVbalrOperators#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#6)]  
  
 您也可以使用`+`運算子來串連字號串。 如果運算元都是字串，Visual Basic 串連它們。 串連結果代表單一字串，其中包含兩個運算元的內容一次。  
  
 如果運算元是混合類型，則結果會視[Option Strict 語句](../../../visual-basic/language-reference/statements/option-strict-statement.md)的設定而定。 下列範例說明當為`Option Strict` `On`時的結果。  
  
 [!code-vb[VbVbalrOperators#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class3.vb#53)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#51)]  
  
 下列範例說明當為`Option Strict` `Off`時的結果。  
  
 [!code-vb[VbVbalrOperators#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#54)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#52)]  
  
 若要消除不明確的情況`&` `+` ，您應該使用運算子，而不是進行串連。  
  
## <a name="see-also"></a>另請參閱

- [& 運算子](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [串連運算子](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Visual Basic 中的算術運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)
