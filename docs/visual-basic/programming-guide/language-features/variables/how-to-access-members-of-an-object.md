---
title: 如何：存取物件的成員
ms.date: 07/20/2015
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
ms.openlocfilehash: d44b538e8413eb1412e937375e9bca77600a29b7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348663"
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a>如何：存取物件的成員 (Visual Basic)

當您有參考物件的物件變數時，您通常會想要使用該物件的成員，例如其方法、屬性、欄位和事件。 例如，建立新的 <xref:System.Windows.Forms.Form> 物件之後，您可能會想要設定其 <xref:System.Windows.Forms.Control.Text%2A> 屬性或呼叫其 <xref:System.Windows.Forms.Control.Focus%2A> 方法。

## <a name="accessing-members"></a>存取成員

您可以透過參考它的變數來存取物件的成員。

#### <a name="to-access-members-of-an-object"></a>存取物件的成員

- 在物件變數名稱和成員名稱之間使用成員存取運算子（`.`）。

    ```vb
    currentText = newForm.Text
    ```

    如果成員是[共用](../../../../visual-basic/language-reference/modifiers/shared.md)的，您就不需要變數來存取它。

## <a name="accessing-members-of-an-object-of-known-type"></a>存取已知型別之物件的成員

如果您在編譯時期知道物件的類型，您可以針對參考它的變數使用*早期繫結*。

#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a>存取您在編譯時期知道型別之物件的成員

1. 將物件變數宣告為您想要指派給變數之物件的型別。

    ```vb
    Dim extraForm As System.Windows.Forms.Form
    ```

    使用 `Option Strict On`，您只能將 <xref:System.Windows.Forms.Form> 物件（或衍生自 <xref:System.Windows.Forms.Form>的類型物件）指派給 `extraForm`。 如果您已定義具有擴展 `CType` 轉換為 <xref:System.Windows.Forms.Form>的類別或結構，您也可以將該類別或結構指派給 `extraForm`。

2. 在物件變數名稱和成員名稱之間使用成員存取運算子（`.`）。

    ```vb
    extraForm.Show()
    ```

    不論 `Option Strict` 設定為何，您都可以存取 <xref:System.Windows.Forms.Form> 類別特定的所有方法和屬性。

## <a name="accessing-members-of-an-object-of-unknown-type"></a>存取未知類型物件的成員

如果您在編譯時期不知道物件的型別，則必須針對參考它的任何變數使用*晚期繫結*。

#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a>若要存取在編譯時期不知道型別之物件的成員

1. 將物件變數宣告為[物件資料類型](../../../../visual-basic/language-reference/data-types/object-data-type.md)。 （將變數宣告為 `Object` 與將它宣告為 <xref:System.Object?displayProperty=nameWithType>相同）。

    ```vb
    Dim someControl As Object
    ```

    使用 `Option Strict On`，您只能存取在 <xref:System.Object> 類別上定義的成員。

2. 在物件變數名稱和成員名稱之間使用成員存取運算子（`.`）。

    ```vb
    someControl.GetType()
    ```

    若要能夠存取您指派給物件變數之任何物件的成員，您必須設定 `Option Strict Off`。 當您這麼做時，編譯器無法保證指定的成員是由您指派給變數的物件所公開。 如果物件未公開您嘗試存取的成員，就會發生 <xref:System.MemberAccessException> 例外狀況。

## <a name="see-also"></a>請參閱

- <xref:System.Object>
- <xref:System.Windows.Forms.Form>
- <xref:System.MemberAccessException>
- [物件變數](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [物件變數宣告](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
