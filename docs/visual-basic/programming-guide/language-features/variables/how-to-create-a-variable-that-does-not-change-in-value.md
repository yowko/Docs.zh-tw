---
title: 作法：建立不會在值中變更的變數 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
ms.openlocfilehash: d201e95463dd0431825fee03ebfd340ac80cc552
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630893"
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a>HOW TO：建立不會在值中變更的變數 (Visual Basic)

未變更其值的變數概念可能會顯示為衝突。 但在某些情況下, 常數並不可行, 而且具有固定值的變數會很有用。 在這種情況下, 您可以使用[ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md)關鍵字來定義成員變數。

在下列情況下, 您無法使用[Const 語句](../../../../visual-basic/language-reference/statements/const-statement.md)來宣告和指派常數值:

- `Const`語句不接受您想要使用的資料類型

- 您在編譯時期不知道此值

- 您無法在編譯時期計算常數值

### <a name="to-create-a-variable-that-does-not-change-in-value"></a>若要建立不會在值中變更的變數

1. 在模組層級, 使用[Dim 語句](../../../../visual-basic/language-reference/statements/dim-statement.md)宣告成員變數, 並包含[ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md)關鍵字。

    ```vb
    Dim ReadOnly timeStarted
    ```

    您只能在`ReadOnly`成員變數上指定。 這表示您必須在任何程式之外的模組層級定義變數。

2. 如果您可以在編譯時期計算單一語句中的值, 請在`Dim`語句中使用初始化子句。 請在[As](../../../../visual-basic/language-reference/statements/as-clause.md)子句後面加上等號`=`(), 後面接著運算式。 請確定編譯器可以將此運算式評估為常數值。

    ```vb
    Dim ReadOnly timeStarted As Date = Now
    ```

    您只能將值指派給`ReadOnly`變數一次。 一旦您這麼做, 任何程式碼都不會變更其值。

    如果您在編譯時期不知道此值, 或是在編譯時期無法使用單一語句來計算該值, 您仍然可以在執行時間于函式中指派它。 若要這樣做, 您必須`ReadOnly`在類別或結構層級宣告變數。 在該類別或結構的函式中, 計算變數的固定值, 並將它指派給變數, 然後再從函式傳回。

## <a name="see-also"></a>另請參閱

- [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)
- [Const 陳述式](../../../../visual-basic/language-reference/statements/const-statement.md)
