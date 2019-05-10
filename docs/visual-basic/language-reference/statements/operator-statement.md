---
title: Operator 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.operator
helpviewer_keywords:
- operators [Visual Basic]
- procedures [Visual Basic], operator
- Narrowing keyword [Visual Basic], conversion operators
- Visual Basic code, operators
- Widening keyword [Visual Basic], conversion operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
- Operator statement [Visual Basic]
- CType function [Visual Basic], Operator statement
ms.assetid: b12ec4af-1ad7-4a17-865b-c5ee96320ae5
ms.openlocfilehash: 4162f7cb5d8b89a1e5e8e7db429cf4e8dd9b700a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64583586"
---
# <a name="operator-statement"></a>Operator Statement
宣告運算子符號、 運算元與類別或結構定義的運算子程序的程式碼。  
  
## <a name="syntax"></a>語法  
  
```  
[ <attrlist> ] Public [ Overloads ] Shared [ Shadows ] [ Widening | Narrowing ]   
Operator operatorsymbol ( operand1 [, operand2 ]) [ As [ <attrlist> ] type ]  
    [ statements ]  
    [ statements ]  
    Return returnvalue  
    [ statements ]  
End Operator  
```  
  
## <a name="parts"></a>組件  
 `attrlist`  
 選擇性。 請參閱[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)。  
  
 `Public`  
 必要項。 表示這個運算子程序[公開](../../../visual-basic/language-reference/modifiers/public.md)存取。  
  
 `Overloads`  
 選擇性。 請參閱[多載](../../../visual-basic/language-reference/modifiers/overloads.md)。  
  
 `Shared`  
 必要項。 指出此運算子程序[共用](../../../visual-basic/language-reference/modifiers/shared.md)程序。  
  
 `Shadows`  
 選擇性。 請參閱[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)。  
  
 `Widening`  
 除非您指定所需的轉換運算子`Narrowing`。 表示定義這個運算子程序[Widening](../../../visual-basic/language-reference/modifiers/widening.md)轉換。 在此 [說明] 頁面上，請參閱 「 擴展和縮小轉換 」。  
  
 `Narrowing`  
 除非您指定所需的轉換運算子`Widening`。 表示定義這個運算子程序[Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)轉換。 在此 [說明] 頁面上，請參閱 「 擴展和縮小轉換 」。  
  
 `operatorsymbol`  
 必要項。 符號或運算子，此運算子程序定義的識別碼。  
  
 `operand1`  
 必要項。 名稱和類型的一元運算子 （包括轉換運算子） 的單一運算元或二元運算子的左的運算元。  
  
 `operand2`  
 二元運算子的必要項。 名稱和類型的二元運算子的右運算元。  
  
 `operand1` 和`operand2`具有下列語法和組成部分：  
  
 `[ ByVal ] operandname [ As operandtype ]`  
  
|組件|描述|  
|----------|-----------------|  
|`ByVal`|必須是選擇性，但傳遞機制[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)。|  
|`operandname`|必要項。 表示此運算元的變數名稱。 請參閱 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。|  
|`operandtype`|選擇性除非`Option Strict`是`On`。 此運算元資料類型。|  
  
 `type`  
 選擇性除非`Option Strict`是`On`。 傳回值的運算子程序的資料類型。  
  
 `statements`  
 選擇性。 運算子程序執行的陳述式區塊。  
  
 `returnvalue`  
 必要項。 運算子程序傳回呼叫程式碼的值。  
  
 `End` `Operator`  
 必要項。 此運算子程序的定義就會終止。  
  
## <a name="remarks"></a>備註  
 您可以使用`Operator`只能在類別或結構中。 這表示*宣告內容*運算子不能是原始程式檔、 命名空間、 模組、 介面、 程序或區塊。 如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 所有的操作員必須為`Public Shared`。 您無法指定`ByRef`， `Optional`，或`ParamArray`的任一個運算元。  
  
 您無法使用的運算子符號或識別項，傳回的值。 您必須使用`Return`陳述式，而且必須指定一個值。 任意數目的`Return`陳述式可以出現在任何位置的程序。  
  
 以這種方式定義的運算子會呼叫*運算子多載*無論您使用`Overloads`關鍵字。 下表列出您可以定義的運算子清單。  
  
|類型|運算子|  
|----------|---------------|  
|一元|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|二元|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|轉換 (一元)|`CType`|  
  
 請注意， `=` ，二元清單中的運算子為比較運算子，而不是指派運算子。  
  
 當您定義`CType`，您必須指定`Widening`或`Narrowing`。  
  
## <a name="matched-pairs"></a>相符的配對  
 您必須定義特定的運算子為相符的配對。 如果您定義這類組的其中一個運算子，您必須將另也定義。 相符的配對，如下所示：  
  
- `=` 和 `<>`  
  
- `>` 和 `<`  
  
- `>=` 和 `<=`  
  
- `IsTrue` 和 `IsFalse`  
  
## <a name="data-type-restrictions"></a>資料類型限制  
 您定義每個運算子必須投入您定義它所在的類別或結構。 這表示類別或結構必須顯示為下列資料類型：  
  
- 一元運算子的運算元。  
  
- 至少其中一個二元運算子的運算元。  
  
- 運算元或轉換運算子的傳回型別。  
  
 某些運算子具有其他資料型別限制，如下所示：  
  
- 如果您定義`IsTrue`並`IsFalse`運算子，它們必須都傳回`Boolean`型別。  
  
- 如果您定義`<<`並`>>`運算子，它們必須同時指定`Integer`類型`operandtype`的`operand2`。  
  
 傳回的型別沒有對應至其中一個運算元的類型。 比方說，這類的比較運算子`=`或是`<>`可能會傳回`Boolean`即使兩個運算元是`Boolean`。  
  
## <a name="logical-and-bitwise-operators"></a>邏輯運算子和位元運算子  
 `And`， `Or`， `Not`，和`Xor`運算子可以執行在 Visual Basic 中的邏輯或位元運算。 不過，如果您定義這些運算子的其中一個類別或結構上，您可以定義只有其位元的作業。  
  
 您不能定義`AndAlso`直接與運算子`Operator`陳述式。 不過，您可以使用`AndAlso`如果您已符合下列條件：  
  
- 您已定義`And`在您想要使用的相同運算元類型`AndAlso`。  
  
- 您定義`And`傳回相同的類型為類別或結構的項目，在其上已定義它。  
  
- 您已定義`IsFalse`上類別或結構的項目，您已定義的運算子`And`。  
  
 同樣地，您可以使用`OrElse`如果您已定義`Or`相同的運算元，使用類別或結構，而您的傳回型別已定義`IsTrue`類別或結構上。  
  
## <a name="widening-and-narrowing-conversions"></a>Widening and Narrowing Conversions  
 A*擴展轉換*一定會成功在執行階段，而*縮小轉換*可以在執行階段失敗。 如需詳細資訊，請參閱 [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。  
  
 如果您宣告轉換程序，才能`Widening`，您的程序程式碼必須產生任何失敗。 這表示：  
  
- 它必須一律傳回有效的值型別的`type`。  
  
- 它必須處理所有可能的例外狀況或其他錯誤狀況。  
  
- 它必須處理傳回的任何程序，它會呼叫任何錯誤。  
  
 如果已轉換程序可能不會成功，或是它可能會造成未處理的例外狀況，您必須將它宣告`Narrowing`。  
  
## <a name="example"></a>範例  
 下列程式碼範例會使用`Operator`陳述式來定義結構，其中包含的運算子程序的外框`And`， `Or`， `IsFalse`，和`IsTrue`運算子。 `And` 並`Or`各自採用兩個運算元的型別`abc`並傳回型別`abc`。 `IsFalse` 並`IsTrue`各自採用單一類型的運算元`abc`，並傳回`Boolean`。 這些定義允許呼叫的程式碼，以使用`And`， `AndAlso`， `Or`，以及`OrElse`類型的運算元使用`abc`。  
  
 [!code-vb[VbVbalrStatements#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#44)]  
  
## <a name="see-also"></a>另請參閱

- [IsFalse 運算子](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [IsTrue 運算子](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [Widening](../../../visual-basic/language-reference/modifiers/widening.md)
- [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [擴展和縮小轉換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [如何：定義運算子](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [如何：定義轉換運算子](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [如何：呼叫運算子程序](../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)
- [如何：使用定義運算子的類別](../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)
