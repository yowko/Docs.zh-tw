---
title: 如何：宣告常數
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
ms.openlocfilehash: 138dd58dac9d1983e35e61f8b98a77810fc6e38b
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058842"
---
# <a name="how-to-declare-a-constant-visual-basic"></a>如何：宣告常數 (Visual Basic)

您可以使用 `Const` 語句來宣告常數，並設定其值。 藉由宣告常數，您可以將有意義的名稱指派給值。 一旦宣告常數之後，就無法修改或指派新的值給它。  
  
 您可以在程式或模組、類別或結構的宣告區段中宣告常數。 類別或結構層級常數 `Private` 預設為，但也可以宣告為、、 `Public` 或 `Friend` 適用 `Protected` `Protected Friend` 于適當的程式碼存取層級。  
  
 常數必須有有效的符號名稱 (規則與建立變數名稱的規則相同，) 和包含數值或字串常數和運算子的運算式 (但不) 函式呼叫。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a>宣告常數  
  
- 撰寫包含存取規範、 `Const` 關鍵字和運算式的宣告，如下列範例所示：  
  
     [!code-vb[VbEnumsTask#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#8)]  
  
     當 [option 推斷](../../../language-reference/statements/option-infer-statement.md) 為 `Off` 且 [option Strict](../../../language-reference/statements/option-strict-statement.md) 為時 `On` ，您必須指定資料類型 (、、、、、、、、、 `Boolean` `Byte` `Char` `DateTime` `Decimal` `Double` `Integer` `Long` `Short` `Single` 或 `String`) ，明確地宣告常數。  
  
     當 `Option Infer` 是 `On` 或 `Option Strict` 時 `Off` ，您可以宣告常數，而不需要使用子句來指定資料類型 `As` 。 編譯器會從運算式的型別判斷常數的型別。 如需詳細資訊，請參閱 [常數和常值資料類型](constant-and-literal-data-types.md)。  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a>宣告具有明確陳述資料類型的常數  
  
- 撰寫包含 `As` 關鍵字和明確資料類型的宣告，如下列範例所示：  
  
     [!code-vb[VbEnumsTask#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#9)]  
  
     您可以在同一行宣告多個常數，不過如果您的程式碼每行只會宣告一個常數，則您的程式碼會更容易讀取。 如果您在同一行宣告多個常數，它們必須具有相同的存取層級 (`Public` 、 `Private` 、 `Friend` 、 `Protected` 或 `Protected Friend`) 。  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a>在同一行宣告多個常數  
  
- 以逗號和空格分隔宣告，如下列範例所示：  
  
    ```vb  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a>另請參閱

- [Const 陳述式](../../../language-reference/statements/const-statement.md)
- [常數和常值資料類型](constant-and-literal-data-types.md)
- [常數的概觀](constants-overview.md)
- [如何：宣告常數](how-to-declare-a-constant.md)
- [使用者定義的常數](user-defined-constants.md)
- [常數和常值資料類型](constant-and-literal-data-types.md)
- [如何：將關聯的常數值群組在一起](how-to-group-related-constant-values-together.md)
- [列舉的概觀](enumerations-overview.md)
- [如何：宣告列舉](how-to-declare-enumerations.md)
- [如何：參考列舉類型成員](how-to-refer-to-an-enumeration-member.md)
- [列舉和名稱限定性條件](enumerations-and-name-qualification.md)
- [如何：逐一查看列舉](how-to-iterate-through-an-enumeration.md)
- [如何：決定與列舉值相關聯的字串](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [何時使用列舉類型](when-to-use-an-enumeration.md)

- [列舉的概觀](enumerations-overview.md)
- [常數的概觀](constants-overview.md)
- [如何：宣告列舉類型](how-to-declare-enumerations.md)
- [列舉和名稱限定性條件](enumerations-and-name-qualification.md)
- [Long](../../../language-reference/statements/option-strict-statement.md)
- [常數和列舉](../../../language-reference/constants-and-enumerations.md)
