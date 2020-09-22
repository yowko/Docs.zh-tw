---
title: + 運算子
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
ms.openlocfilehash: bc31e4c66c64d891e3fffd809b7ae99b9c9a0520
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873459"
---
# <a name="-operator-visual-basic"></a>+ 運算子 (Visual Basic)

加入兩個數字，或傳回數值運算式的正值。 也可以用來串連兩個字串運算式。  
  
## <a name="syntax"></a>Syntax  
  
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
|`expression1`|必要。 任何數值或字串運算式。|  
|`expression2`|除非 `+` 運算子計算負數值，否則為必要項。 任何數值或字串運算式。|  
  
## <a name="result"></a>結果  

 如果 `expression1` 和 `expression2` 都是數值，則結果為其算術總和。  
  
 如果 `expression2` 不存在， `+` 運算子就是運算式未變更值的 *一元* 識別運算子。 在這種情況下，作業包含保留的正負號 `expression1` ，因此如果是負數，則結果為負數 `expression1` 。  
  
 如果 `expression1` 和 `expression2` 都是字串，則結果會是其值的串連。  
  
 如果 `expression1` 和 `expression2` 屬於混合類型，則採取的動作取決於其類型、其內容，以及 [Option Strict 語句](../statements/option-strict-statement.md)的設定。 如需詳細資訊，請參閱「備註」中的表格。  
  
## <a name="supported-types"></a>支援的型別  

 所有數數值型別，包括不帶正負號的和浮點數類型，以及 `Decimal` 和 `String` 。  
  
## <a name="remarks"></a>備註  

 一般情況下， `+` 會盡可能執行算術加法，而且只有在兩個運算式都是字串時，才會串連。  
  
 如果兩個運算式都是 `Object` ，Visual Basic 會採取下列動作。  
  
|運算式的資料類型|依編譯器的動作|  
|---|---|  
|這兩個運算式都是數值資料類型 (`SByte` 、、、、、、、、 `Byte` `Short` `UShort` `Integer` `UInteger` `Long` `ULong` `Decimal` 、 `Single` 或 `Double`) |新增。 結果資料類型是適用于和之資料類型的數數值型別 `expression1` `expression2` 。 請參閱 [運算子結果資料類型](data-types-of-operator-results.md)中的「整數算術」資料表。|  
|這兩個運算式的類型為 `String`|連接。|  
|一個運算式是數值資料類型，另一個則是字串|如果 `Option Strict` 為 `On` ，則產生編譯器錯誤。<br /><br /> 如果 `Option Strict` 為 `Off` ，則會隱含地將轉換成 `String` `Double` 並加入。<br /><br /> 如果 `String` 無法轉換為 `Double` ，則會擲回 <xref:System.InvalidCastException> 例外狀況。|  
|一個運算式是數值資料類型，另一個則是 [Nothing](../nothing.md)|新增，其 `Nothing` 值為零。|  
|其中一個運算式是字串，另一個則是 `Nothing`|串連，其 `Nothing` 值為 ""。|  
  
 如果一個運算式是 `Object` 運算式，Visual Basic 會採取下列動作。  
  
|運算式的資料類型|依編譯器的動作|  
|---|---|  
|`Object` 運算式保存數值，另一個則是數值資料類型|如果 `Option Strict` 為 `On` ，則產生編譯器錯誤。<br /><br /> 如果 `Option Strict` 為 `Off` ，則加入。|  
|`Object` 運算式保存數值，另一個則是類型 `String`|如果 `Option Strict` 為 `On` ，則產生編譯器錯誤。<br /><br /> 如果 `Option Strict` 為 `Off` ，則會隱含地將轉換成 `String` `Double` 並加入。<br /><br /> 如果 `String` 無法轉換為 `Double` ，則會擲回 <xref:System.InvalidCastException> 例外狀況。|  
|`Object` 運算式保存字串，另一個則是數值資料類型|如果 `Option Strict` 為 `On` ，則產生編譯器錯誤。<br /><br /> 如果 `Option Strict` 為 `Off` ，則會隱含地將字串轉換 `Object` 為 `Double` 並加入。<br /><br /> 如果 `Object` 無法將字串轉換成 `Double` ，則會擲回 <xref:System.InvalidCastException> 例外狀況。|  
|`Object` 運算式保存字串，另一個則是類型 `String`|如果 `Option Strict` 為 `On` ，則產生編譯器錯誤。<br /><br /> 如果 `Option Strict` 為 `Off` ，則會隱含地轉換 `Object` 為 `String` 和串連。|  
  
 如果這兩個運算式都是 `Object` 運算式，Visual Basic 只會 () 採取下列動作 `Option Strict Off` 。  
  
|運算式的資料類型|依編譯器的動作|  
|---|---|  
|這兩個 `Object` 運算式都會保存數值|新增。|  
|這兩個 `Object` 運算式的類型為 `String`|連接。|  
|一個 `Object` 運算式會保存數值，另一個則保留一個字串|以隱含方式將字串轉換 `Object` 為 `Double` 並加入。<br /><br /> 如果字串 `Object` 無法轉換成數值，則會擲回 <xref:System.InvalidCastException> 例外狀況。|  
  
 如果任一個 `Object` 運算式評估為 [Nothing](../nothing.md) 或 <xref:System.DBNull> ，則 `+` 運算子會將它視為值為 `String` "" 的。  
  
> [!NOTE]
> 當您使用 `+` 運算子時，可能無法判斷是否會進行加法或字串串連。 使用 `&` 運算子進行串連以消除不明確的情況，並提供自我記錄程式碼。  
  
## <a name="overloading"></a>多載化  

 可以多載 `+` 運算子*overloaded*，這表示當運算元具有該類別或結構的型別時，類別或結構可以重新定義其行為。 如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  

 下列範例會使用 `+` 運算子來加入數位。 如果運算元都是數值，Visual Basic 會計算算術結果。 算術結果代表兩個運算元的總和。  
  
 [!code-vb[VbVbalrOperators#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#6)]  
  
 您也可以使用 `+` 運算子來串連字號串。 如果運算元都是字串，Visual Basic 串連它們。 串連結果代表單一字串，其中包含兩個運算元的內容。  
  
 如果運算元屬於混合類型，則結果取決於 [Option Strict 語句](../statements/option-strict-statement.md)的設定。 下列範例說明當為時的 `Option Strict` 結果 `On` 。  
  
 [!code-vb[VbVbalrOperators#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class3.vb#53)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#51)]  
  
 下列範例說明當為時的 `Option Strict` 結果 `Off` 。  
  
 [!code-vb[VbVbalrOperators#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#54)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#52)]  
  
 若要消除不明確的情況，您應該使用 `&` 運算子而非 `+` 串連。  
  
## <a name="see-also"></a>另請參閱

- [& 運算子](concatenation-operator.md)
- [串連運算子](concatenation-operators.md)
- [算術運算子](arithmetic-operators.md)
- [依功能列出運算子](operators-listed-by-functionality.md)
- [Visual Basic 中的運算子優先順序](operator-precedence.md)
- [Visual Basic 的算術運算子](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Long](../statements/option-strict-statement.md)
