---
title: Operator 陳述式
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
ms.openlocfilehash: aa6ae3977977ded05e47d12dabe72f09251f262d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353799"
---
# <a name="operator-statement"></a>Operator 陳述式

宣告運算子符號、運算元，以及在類別或結構上定義運算子程式的程式碼。

## <a name="syntax"></a>語法

```vb
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
必要。 指出此運算子程式具有[公用](../../../visual-basic/language-reference/modifiers/public.md)存取權。

`Overloads`  
選擇性。 請[參閱](../../../visual-basic/language-reference/modifiers/overloads.md)多載。

`Shared`  
必要。 表示此運算子程式是[共用](../../../visual-basic/language-reference/modifiers/shared.md)程式。

`Shadows`  
選擇性。 請參閱[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)。

`Widening`  
轉換運算子的必要參數，除非您指定 `Narrowing`。 表示此運算子程式會定義[擴展](../../../visual-basic/language-reference/modifiers/widening.md)轉換。 請參閱此說明頁面上的「擴展和縮小轉換」。

`Narrowing`  
轉換運算子的必要參數，除非您指定 `Widening`。 表示此運算子程式會定義[縮小](../../../visual-basic/language-reference/modifiers/narrowing.md)轉換。 請參閱此說明頁面上的「擴展和縮小轉換」。

`operatorsymbol`  
必要。 這個運算子程式所定義之運算子的符號或識別碼。

`operand1`  
必要。 一元運算子之單一運算元的名稱和類型（包括轉換運算子）或二元運算子的左運算元。

`operand2`  
二元運算子的必要參數。 二元運算子右運算元的名稱和類型。

`operand1` 和 `operand2` 具有下列語法和部分：

`[ ByVal ] operandname [ As operandtype ]`

|組件|描述|
|----------|-----------------|
|`ByVal`|選擇性，但傳遞機制必須是[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)。|
|`operandname`|必要。 代表這個運算元之變數的名稱。 請參閱 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。|
|`operandtype`|除非 `On``Option Strict`，否則為選擇性。 這個運算元的資料類型。|

`type`  
除非 `On``Option Strict`，否則為選擇性。 運算子程式傳回值的資料類型。

`statements`  
選擇性。 運算子程式執行的語句區塊。

`returnvalue`  
必要。 運算子程式傳回給呼叫程式碼的值。

`End` `Operator`  
必要。 終止此運算子程式的定義。

## <a name="remarks"></a>備註

您只能在類別或結構中使用 `Operator`。 這表示運算子的宣告*內容*不能是原始程式檔、命名空間、模組、介面、程式或區塊。 如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。

所有的運算子都必須 `Public Shared`。 您不能為任一運算元指定 `ByRef`、`Optional`或 `ParamArray`。

您不能使用運算子符號或識別碼來保存傳回值。 您必須使用 `Return` 語句，而且必須指定值。 任何數目的 `Return` 語句都可以出現在程式中的任何位置。

不論您是否使用 `Overloads` 關鍵字，以這種方式定義運算子稱為「*運算子*多載」。 下表列出您可以定義的運算子清單。

|類型|運算子|
|----------|---------------|
|一元|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|
|Binary|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|
|轉換 (一元)|`CType`|

請注意，二進位清單中的 `=` 運算子是比較運算子，而不是指派運算子。

當您定義 `CType`時，您必須指定 [`Widening`] 或 [`Narrowing`]。

## <a name="matched-pairs"></a>相符的配對

您必須將某些運算子定義為相符的配對。 如果您定義這類配對的任一個運算子，則也必須定義另一個。 相符的配對如下所示：

- `=` 和 `<>`

- `>` 和 `<`

- `>=` 和 `<=`

- `IsTrue` 和 `IsFalse`

## <a name="data-type-restrictions"></a>資料類型限制

您定義的每個運算子都必須包含您定義它所在的類別或結構。 這表示類別或結構必須以下列資料類型的形式出現：

- 一元運算子的運算元。

- 二元運算子的至少一個運算元。

- 轉換運算子的運算元或傳回型別。

 某些運算子具有額外的資料類型限制，如下所示：

- 如果您定義 `IsTrue` 和 `IsFalse` 運算子，則兩者都必須傳回 `Boolean` 類型。

- 如果您定義 `<<` 和 `>>` 運算子，它們必須同時為 `operand2`的 `operandtype` 指定 `Integer` 類型。

傳回型別不一定要對應至任一運算元的型別。 例如，即使兩個運算元都不 `Boolean`，比較運算子（例如 `=` 或 `<>` 也可以傳回 `Boolean`。

## <a name="logical-and-bitwise-operators"></a>邏輯運算子和位元運算子

`And`、`Or`、`Not`和 `Xor` 運算子可以在 Visual Basic 中執行邏輯 or 位運算。 不過，如果您在類別或結構上定義其中一個運算子，則只能定義其位運算。

您不能直接使用 `Operator` 語句來定義 `AndAlso` 運算子。 不過，如果您已完成下列條件，您可以使用 `AndAlso`：

- 您已在要用於 `AndAlso`的相同運算元類型上定義 `And`。

- 您的 `And` 定義會傳回與您已定義的類別或結構相同的類型。

- 您已在定義 `And`的類別或結構上定義 `IsFalse` 運算子。

同樣地，如果您已在相同的運算元上定義 `Or`、使用類別或結構的傳回型別，而且您已在類別或結構上定義 `IsTrue`，則可以使用 `OrElse`。

## <a name="widening-and-narrowing-conversions"></a>Widening and Narrowing Conversions

*擴輾轉換*一律會在執行時間成功，而*縮小轉換*可能會在執行時間失敗。 如需詳細資訊，請參閱 [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。

如果您宣告要 `Widening`的轉換過程，程式碼就不能產生任何失敗。 這表示：

- 它必須一律傳回 `type`類型的有效值。

- 它必須處理所有可能的例外狀況和其他錯誤情況。

- 它必須處理從它所呼叫的任何程式傳回的任何錯誤。

如果轉換程式可能不會成功，或可能造成未處理的例外狀況，您必須將它宣告為 `Narrowing`。

## <a name="example"></a>範例

下列程式碼範例會使用 `Operator` 語句來定義結構的外框，其中包含 `And`、`Or`、`IsFalse`和 `IsTrue` 運算子的運算子程式。 `And` 和 `Or` 都會採用類型 `abc` 的兩個運算元，並 `abc`傳回型別。 `IsFalse` 和 `IsTrue` 都會採用類型 `abc` 的單一運算元，並傳回 `Boolean`。 這些定義可讓呼叫程式碼使用 `And`、`AndAlso`、`Or`和 `OrElse`，並搭配 `abc`類型的運算元。

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
