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
ms.openlocfilehash: 5054d4a4fc02d8bd22efceb01770fc54167d8cb3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347475"
---
# <a name="how-to-declare-a-constant-visual-basic"></a>如何：宣告常數 (Visual Basic)
您可以使用 `Const` 語句來宣告常數並設定其值。 藉由宣告常數，您可以將有意義的名稱指派給值。 一旦宣告了常數，就無法修改或指派新的值。  
  
 您在程式內或在模組、類別或結構的宣告區段中宣告常數。 類別或結構層級常數預設為 `Private`，但也可以宣告為適當的程式碼存取層級 `Public`、`Friend`、`Protected`或 `Protected Friend`。  
  
 常數必須具有有效的符號名稱（規則與建立變數名稱的規則相同），以及由數值或字串常數和運算子（但不含函式呼叫）組成的運算式。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a>若要宣告常數  
  
- 撰寫包含存取規範、`Const` 關鍵字和運算式的宣告，如下列範例所示：  
  
     [!code-vb[VbEnumsTask#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#8)]  
  
     當[Option 推斷](../../../../visual-basic/language-reference/statements/option-infer-statement.md)為 `Off`，且[option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)為 `On`時，您必須指定資料類型（`Boolean`、`Byte`、`Char`、`DateTime`、`Decimal`、`Double`、`Integer`、`Long`、`Short`、`Single`或 `String`）明確地宣告常數。  
  
     當 `Option Infer` `On` 或 `Option Strict` `Off`時，您可以宣告常數，而不需使用 `As` 子句來指定資料類型。 編譯器會從運算式的類型判斷常數的類型。 如需詳細資訊，請參閱[常數和常值資料類型](constant-and-literal-data-types.md)。  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a>若要宣告具有明確陳述之資料類型的常數  
  
- 撰寫包含 `As` 關鍵字和明確資料類型的宣告，如下列範例所示：  
  
     [!code-vb[VbEnumsTask#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#9)]  
  
     您可以在同一行宣告多個常數，不過，如果您的程式碼在每行只宣告一個常數，則會更容易閱讀。 如果您在單一行上宣告多個常數，它們都必須具有相同的存取層級（`Public`、`Private`、`Friend`、`Protected`或 `Protected Friend`）。  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a>若要在同一行宣告多個常數  
  
- 以逗號和空格分隔宣告，如下列範例所示：  
  
    ```vb  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a>請參閱

- [Const 陳述式](../../../../visual-basic/language-reference/statements/const-statement.md)
- [常數和常值資料類型](constant-and-literal-data-types.md)
- [常數的概觀](constants-overview.md)
- [如何：宣告常數](how-to-declare-a-constant.md)
- [使用者定義的常數](user-defined-constants.md)
- [常數和常值資料類型](constant-and-literal-data-types.md)
- [如何：將關聯的常數值群組在一起](how-to-group-related-constant-values-together.md)
- [列舉的概觀](enumerations-overview.md)
- [如何：宣告列舉](how-to-declare-enumerations.md)
- [如何：參考列舉成員](how-to-refer-to-an-enumeration-member.md)
- [列舉和名稱限定性條件](enumerations-and-name-qualification.md)
- [如何：逐一查看列舉](how-to-iterate-through-an-enumeration.md)
- [如何：決定與列舉值相關聯的字串](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [何時使用列舉](when-to-use-an-enumeration.md)

- [列舉的概觀](enumerations-overview.md)
- [常數的概觀](constants-overview.md)
- [如何：宣告列舉](how-to-declare-enumerations.md)
- [列舉和名稱限定性條件](enumerations-and-name-qualification.md)
- [Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [常數和列舉](../../../../visual-basic/language-reference/constants-and-enumerations.md)
