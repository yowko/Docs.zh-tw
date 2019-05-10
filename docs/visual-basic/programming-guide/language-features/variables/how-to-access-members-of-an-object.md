---
title: HOW TO：存取成員的物件 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
ms.openlocfilehash: 46c5eb9bc79b3a408a5a4fc9f40fee7391937c58
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663593"
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a>HOW TO：存取成員的物件 (Visual Basic)
當您參考之物件的物件變數時，您通常會想要使用該物件，例如方法、 屬性、 欄位和事件的成員。 例如，一旦您建立新<xref:System.Windows.Forms.Form>物件，您可能想要設定其<xref:System.Windows.Forms.Control.Text%2A>屬性或呼叫其<xref:System.Windows.Forms.Control.Focus%2A>方法。  
  
## <a name="accessing-members"></a>存取成員  
 您可以存取物件的成員透過參考該變數。  
  
#### <a name="to-access-members-of-an-object"></a>若要存取物件的成員  
  
- 使用成員存取運算子 (`.`) 之間的物件變數的名稱和成員名稱。  
  
    ```  
    currentText = newForm.Text  
    ```  
  
     如果成員是[共用](../../../../visual-basic/language-reference/modifiers/shared.md)，您不需要存取的變數。  
  
## <a name="accessing-members-of-an-object-of-known-type"></a>存取已知型別的物件的成員  
 如果您在編譯時期知道物件類型，您可以使用*早期繫結*變數參考它。  
  
#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a>若要存取，您知道在編譯時期類型物件的成員  
  
1. 宣告物件變數是您想要指派給變數物件的類型。  
  
    ```  
    Dim extraForm As System.Windows.Forms.Form  
    ```  
  
     具有`Option Strict On`，您可以僅指派<xref:System.Windows.Forms.Form>物件 (或類型的物件衍生自<xref:System.Windows.Forms.Form>) 來`extraForm`。 如果您已定義類別或結構與擴展`CType`轉換成<xref:System.Windows.Forms.Form>，您也可以指派該類別或結構`extraForm`。  
  
2. 使用成員存取運算子 (`.`) 之間的物件變數的名稱和成員名稱。  
  
    ```  
    extraForm.Show()  
    ```  
  
     您可以存取所有的方法和屬性的特定<xref:System.Windows.Forms.Form>類別，無論什麼`Option Strict`設定。  
  
## <a name="accessing-members-of-an-object-of-unknown-type"></a>存取成員的未知類型的物件  
 如果您在編譯時期不知道物件類型，您必須使用*晚期繫結*參考它的任何變數。  
  
#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a>若要存取，您不知道類型在編譯時期物件的成員  
  
1. 將物件變數的宣告[Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)。 (宣告為變數`Object`等同於它宣告為<xref:System.Object?displayProperty=nameWithType>。)  
  
    ```  
    Dim someControl As Object  
    ```  
  
     具有`Option Strict On`，您可以存取只有成員上定義之<xref:System.Object>類別。  
  
2. 使用成員存取運算子 (`.`) 之間的物件變數的名稱和成員名稱。  
  
    ```  
    someControl.GetType()  
    ```  
  
     若要能夠存取您指派給物件變數的任何物件的成員，您必須設定`Option Strict Off`。 當您這樣做時，編譯器無法保證指定的成員由您指派給變數的物件。 如果物件不會公開的成員，您嘗試存取，<xref:System.MemberAccessException>發生例外狀況。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Object>
- <xref:System.Windows.Forms.Form>
- <xref:System.MemberAccessException>
- [物件變數](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [物件變數宣告](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Object 資料類型](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
