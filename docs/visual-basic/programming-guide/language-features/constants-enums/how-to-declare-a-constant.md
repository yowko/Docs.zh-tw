---
title: "如何︰ 宣告常數 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.constant
dev_langs:
- VB
helpviewer_keywords:
- Integer data type, declaring constants
- Single data type, declaring constants
- Const statement [Visual Basic], declaring constants
- procedures, declaration
- data types [Visual Basic], constants
- Long data type, declaring constants
- Visual Basic code, declaring variables and constants
- Double data type, declaring constants
- Boolean data type, declaring constants
- modules, declaring constants
- Byte data type, declaring constants
- constants, declaring
- Date data type, declaring constants
- String data type, declaring constants
- declaring constants, const keyword
- Currency data type, declaring constants and variants
- module-level constants and variables
- Object data type, declaring constants
ms.assetid: f901b4fa-481f-4621-822e-427060577ad1
caps.latest.revision: 20
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 401d0feb85fccf94a25308d38c3c75198ef9294c
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-declare-a-constant-visual-basic"></a>如何：宣告常數 (Visual Basic)
您使用`Const`陳述式來宣告常數，並將其值。 藉由宣告為常數，您可以指派有意義的名稱的值。 一旦宣告為常數，它無法修改或指派新值。  
  
 您可以宣告程序或模組、 類別或結構的宣告區段中的常數。 類別或結構層級常數`Private`根據預設，但是也可能會宣告為`Public`， `Friend`， `Protected`，或`Protected Friend`適當的層級的程式碼存取。  
  
 常數必須包含有效的符號名稱 （規則會建立變數名稱相同），以及組成的數值或字串常數和運算子 （但沒有函式呼叫） 運算式。  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-declare-a-constant"></a>若要宣告常數  
  
-   撰寫包含存取指定名稱的宣告`Const`關鍵字，且運算式，如下列範例所示︰  
  
     [!code-vb[VbEnumsTask #&8;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_1.vb)]  
  
     當[Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)是`Off`和[Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)是`On`，您必須明確宣告常數，指定的資料型別 (`Boolean`， `Byte`， `Char`， `DateTime`， `Decimal`， `Double`， `Integer`， `Long`， `Short`， `Single`，或`String`)。  
  
     當`Option Infer`是`On`或`Option Strict`是`Off`，您可以宣告但未指定的資料類型的常數`As`子句。 編譯器會判斷運算式的型別常數的類型。 如需詳細資訊，請參閱[常數和常值的資料型別](constant-and-literal-data-types.md)。  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a>若要宣告具有明確陳述的資料類型的常數  
  
-   撰寫包含宣告`As`關鍵字和明確的資料類型，如下列範例所示︰  
  
     [!code-vb[VbEnumsTask #&9;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_2.vb)]  
  
     雖然您的程式碼的可讀性宣告只有每行一個常數，您可以在同一行中，宣告多個常數。 如果您在同一行宣告多個常數，必須都是相同的存取層級 (`Public`， `Private`， `Friend`， `Protected`，或`Protected Friend`)。  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a>若要在同一行宣告多個常數  
  
-   分隔各個宣告使用逗號和空格，如下列範例所示︰  
  
    ```  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [Const 陳述式](../../../../visual-basic/language-reference/statements/const-statement.md)   
 [常數和常值資料類型](constant-and-literal-data-types.md)   
 [常數的概觀](constants-overview.md)
 [如何︰ 宣告常數](how-to-declare-a-constant.md)
 [使用者定義常數](user-defined-constants.md)
 [常數和常值的資料型別](constant-and-literal-data-types.md)
 [如何︰ 群組關聯的常數值一起](how-to-group-related-constant-values-together.md)
 [列舉類型的概觀](enumerations-overview.md)
 [如何︰ 宣告列舉](how-to-declare-enumerations.md)
 [如何︰ 參考列舉成員](how-to-refer-to-an-enumeration-member.md)
 [列舉型別和名稱限定](enumerations-and-name-qualification.md)
 [如何︰ 逐一查看列舉類型](how-to-iterate-through-an-enumeration.md)
 [How to︰ 判斷字串列舉值相關聯](how-to-determine-the-string-associated-with-an-enumeration-value.md)
 [何時使用列舉型別](when-to-use-an-enumeration.md)

 [列舉類型的概觀](enumerations-overview.md)   
 [常數的概觀](constants-overview.md)   
 [如何︰ 宣告列舉類型](how-to-declare-enumerations.md)   
 [列舉型別和名稱限定](enumerations-and-name-qualification.md)   
 [Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [常數和列舉](../../../../visual-basic/language-reference/constants-and-enumerations.md)

