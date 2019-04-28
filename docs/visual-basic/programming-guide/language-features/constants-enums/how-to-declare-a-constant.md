---
title: HOW TO：宣告常數 (Visual Basic)
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
ms.openlocfilehash: 95bfa3da5499c518dad0c235b539784fee2bb522
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61975971"
---
# <a name="how-to-declare-a-constant-visual-basic"></a>HOW TO：宣告常數 (Visual Basic)
您使用`Const`陳述式來宣告常數，並將其值設定。 藉由宣告為常數，您可以指派有意義的名稱的值。 一旦宣告為常數，它無法修改或指派新值。  
  
 您宣告程序內或在模組、 類別或結構的宣告區段中的常數。 類別或結構層級常數`Private`根據預設，但也可能會宣告為`Public`， `Friend`， `Protected`，或`Protected Friend`適當層級的程式碼存取。  
  
 常數必須包含有效的符號名稱 （規則所建立的變數名稱相同），以及組成的數值或字串常數和運算子 （但沒有函式呼叫） 運算式。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a>若要宣告常數  
  
- 撰寫包含存取規範，宣告`Const`關鍵字，且運算式，如下列範例所示：  
  
     [!code-vb[VbEnumsTask#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#8)]  
  
     當[Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)是`Off`並[Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)是`On`，您必須明確宣告為常數，藉由指定的資料類型 (`Boolean`， `Byte`， `Char`， `DateTime`， `Decimal`， `Double`， `Integer`， `Long`， `Short`， `Single`，或`String`)。  
  
     當`Option Infer`是`On`或是`Option Strict`是`Off`，您可以宣告但未指定的資料類型的常數`As`子句。 編譯器會判斷運算式的類型從常數的類型。 如需詳細資訊，請參閱 <<c0> [ 常數和常值的資料型別](constant-and-literal-data-types.md)。  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a>若要宣告具有明確陳述的資料類型的常數  
  
- 撰寫包含宣告`As`關鍵字和明確的資料類型，如下列範例所示：  
  
     [!code-vb[VbEnumsTask#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#9)]  
  
     雖然您的程式碼更容易閱讀如果您宣告僅每行一個常數，您可以在單一行中宣告多個常數。 如果您在單一行宣告多個常數，則必須有相同的存取層級 (`Public`， `Private`， `Friend`， `Protected`，或`Protected Friend`)。  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a>若要在單一行中宣告多個常數  
  
- 分隔的宣告，使用逗號和空格，如下列範例所示：  
  
    ```  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a>另請參閱

- [Const 陳述式](../../../../visual-basic/language-reference/statements/const-statement.md)
- [常數和常值資料類型](constant-and-literal-data-types.md)
- [常數的概觀](constants-overview.md)
- [如何：宣告常數](how-to-declare-a-constant.md)
- [使用者定義的常數](user-defined-constants.md)
- [常數和常值資料類型](constant-and-literal-data-types.md)
- [如何：群組關聯的常數值在一起](how-to-group-related-constant-values-together.md)
- [列舉的概觀](enumerations-overview.md)
- [如何：宣告列舉](how-to-declare-enumerations.md)
- [如何：參考列舉成員](how-to-refer-to-an-enumeration-member.md)
- [列舉和名稱限定性條件](enumerations-and-name-qualification.md)
- [如何：逐一查看列舉類型](how-to-iterate-through-an-enumeration.md)
- [如何：決定與列舉值關聯的字串](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [何時使用列舉](when-to-use-an-enumeration.md)

- [列舉的概觀](enumerations-overview.md)
- [常數的概觀](constants-overview.md)
- [如何：宣告列舉](how-to-declare-enumerations.md)
- [列舉和名稱限定性條件](enumerations-and-name-qualification.md)
- [Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [常數和列舉](../../../../visual-basic/language-reference/constants-and-enumerations.md)
