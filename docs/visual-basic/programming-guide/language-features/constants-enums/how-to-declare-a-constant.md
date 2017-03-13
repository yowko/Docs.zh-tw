---
title: "How to: Declare A Constant (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.constant"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Integer data type, declaring constants"
  - "Single data type, declaring constants"
  - "Const statement [Visual Basic], declaring constants"
  - "procedures, declaration"
  - "data types [Visual Basic], constants"
  - "Long data type, declaring constants"
  - "Visual Basic code, declaring variables and constants"
  - "Double data type, declaring constants"
  - "Boolean data type, declaring constants"
  - "modules, declaring constants"
  - "Byte data type, declaring constants"
  - "constants, declaring"
  - "Date data type, declaring constants"
  - "String data type, declaring constants"
  - "declaring constants, const keyword"
  - "Currency data type, declaring constants and variants"
  - "module-level constants and variables"
  - "Object data type, declaring constants"
ms.assetid: f901b4fa-481f-4621-822e-427060577ad1
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 20
---
# How to: Declare A Constant (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

您可以使用 `Const` 陳述式來宣告常數並設定其值。  藉由宣告常數，您可以將有意義的名稱指派至某個值。  常數在宣告後，便無法修改或指派新的值。  
  
 您可以在程序中，或於模組、類別、結構的宣告區段中宣告常數。  根據預設，類別或結構層級常數為 `Private`，但也可能宣告為 `Public`、`Friend`、`Protected` 或 `Protected Friend`，以存取適當層級的程式碼。  
  
 常數必須包含有效的符號名稱 \(其規則與建立變數名稱的規則相同\)，以及由數值或字串常數和運算子組成的運算式 \(但不包含函式呼叫\)。  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
### 若要宣告常數  
  
-   撰寫包含存取規範、`Const` 關鍵字及運算式的宣告，如以下範例所示：  
  
     [!code-vb[VbEnumsTask#8](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_1.vb)]  
  
     當 [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) 為 `Off`，而 [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) 為 `On` 時，您必須指定資料型別來明確宣告常數 \(`Boolean`、`Byte`、`Char`、`DateTime`、`Decimal`、`Double`、`Integer`、`Long`、`Short`、`Single` 或 `String`\)。  
  
     當 `Option Infer` 為 `On`，或 `Option Strict` 為 `Off` 時，您可以宣告常數，而不指定具有 `As` 子句的資料型別。  編譯器會從運算式的型別判斷常數的型別。  如需詳細資訊，請參閱[Constant and Literal Data Types](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)。  
  
### 若要宣告已經明確指定資料型別的常數  
  
-   撰寫包含 `As` 關鍵字和明確資料型別的宣告，如以下範例所示：  
  
     [!code-vb[VbEnumsTask#9](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_2.vb)]  
  
     您可以在同一行中宣告多個常數，但是以程式碼的可讀性考量而言，在每一行應該只宣告一個常數。  如果您在同一行中宣告多個常數，它們必須要有相同的存取層級 \(`Public`、`Private`、`Friend`、`Protected` 或 `Protected Friend`\)。  
  
### 若要在同一行中宣告多個常數  
  
-   請使用逗號與空格分隔各個宣告，如下列範例所示：  
  
    ```  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## 請參閱  
 [Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md)   
 [Constant and Literal Data Types](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)   
 [Constants and Enumerations](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)   
 [Enumerations Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)   
 [Constants Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)   
 [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)