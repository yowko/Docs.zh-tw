---
title: 如何：宣告常數 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.constant
helpviewer_keywords:
- Integer data type [Visual Basic], declaring constants
- Single data type [Visual Basic], declaring constants
- Const statement [Visual Basic], declaring constants
- procedures [Visual Basic], declaration
- data types [Visual Basic], constants
- Long data type [Visual Basic], declaring constants
- Visual Basic code, declaring variables and constants
- Double data type [Visual Basic], declaring constants
- Boolean data type [Visual Basic], declaring constants
- modules, declaring constants
- Byte data type [Visual Basic], declaring constants
- constants [Visual Basic], declaring
- Date data type [Visual Basic], declaring constants
- String data type [Visual Basic], declaring constants
- declaring constants [Visual Basic], const keyword
- Currency data type [Visual Basic], declaring constants and variants
- module-level constants and variables
- Object data type [Visual Basic], declaring constants
ms.assetid: f901b4fa-481f-4621-822e-427060577ad1
ms.openlocfilehash: ce45e4df7f74cd68bde0fb2adba10197a11edb1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-declare-a-constant-visual-basic"></a>如何：宣告常數 (Visual Basic)
您使用`Const`陳述式來宣告常數，並將其值設定。 藉由宣告為常數，您可以指派有意義的名稱的值。 一旦已宣告為常數，它不能修改或指派新值。  
  
 您宣告常數程序內或在模組、 類別或結構的宣告區段中。 類別或結構層級常數`Private`根據預設，但也可能會宣告為`Public`， `Friend`， `Protected`，或`Protected Friend`適當層級的程式碼存取。  
  
 常數必須包含有效的符號名稱 （規則會建立變數名稱相同），以及組成的數值或字串常數和運算子 （但沒有函式呼叫） 運算式。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a>若要宣告常數  
  
-   寫入包含存取指定名稱的宣告`Const`關鍵字和運算式，如下列範例所示：  
  
     [!code-vb[VbEnumsTask#8](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_1.vb)]  
  
     當[Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)是`Off`和[Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)是`On`，您必須明確宣告為常數，藉由指定的資料類型 (`Boolean`， `Byte`， `Char`， `DateTime`， `Decimal`， `Double`， `Integer`， `Long`， `Short`， `Single`，或`String`)。  
  
     當`Option Infer`是`On`或`Option Strict`是`Off`，您可以宣告常數但未指定的資料型別`As`子句。 編譯器會判斷運算式的型別常數的類型。 如需詳細資訊，請參閱[常數和常值的資料型別](constant-and-literal-data-types.md)。  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a>若要宣告常數有明確陳述的資料類型  
  
-   撰寫包含宣告`As`關鍵字和明確的資料類型，如下列範例所示：  
  
     [!code-vb[VbEnumsTask#9](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_2.vb)]  
  
     雖然您的程式碼更容易閱讀如果您宣告僅每行一個常數，您可以在單一行中，宣告多個常數。 如果您宣告多個常數在單一行，則必須有相同的存取層級 (`Public`， `Private`， `Friend`， `Protected`，或`Protected Friend`)。  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a>若要在單行中宣告多個常數  
  
-   分隔宣告使用逗號和空格，如下列範例所示：  
  
    ```  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [Const 陳述式](../../../../visual-basic/language-reference/statements/const-statement.md)  
 [常數和常值資料類型](constant-and-literal-data-types.md)  
 [常數的概觀](constants-overview.md)[如何： 宣告常數](how-to-declare-a-constant.md)[使用者定義常數](user-defined-constants.md)[常數和常值的資料型別](constant-and-literal-data-types.md) [How to： 群組相互關聯的常數值](how-to-group-related-constant-values-together.md)[列舉類型的概觀](enumerations-overview.md)[如何： 宣告列舉](how-to-declare-enumerations.md)[如何： 參考列舉成員](how-to-refer-to-an-enumeration-member.md)[列舉型別和名稱限定](enumerations-and-name-qualification.md)[如何： 逐一查看列舉類型](how-to-iterate-through-an-enumeration.md)[如何： 決定與列舉值關聯的字串](how-to-determine-the-string-associated-with-an-enumeration-value.md)[何時使用列舉](when-to-use-an-enumeration.md)

 [列舉的概觀](enumerations-overview.md)  
 [常數的概觀](constants-overview.md)  
 [如何： 宣告列舉](how-to-declare-enumerations.md)  
 [列舉和名稱限定性條件](enumerations-and-name-qualification.md)  
 [Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [常數和列舉](../../../../visual-basic/language-reference/constants-and-enumerations.md)
