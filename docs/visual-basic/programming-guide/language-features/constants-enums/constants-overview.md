---
title: "Constants Overview (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "constants"
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# Constants Overview (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

常數是個取代不會變動的數字或字串的有意義名稱。  如同它的名稱所示，常數用來儲存應用程式執行過程中維持一樣的值。  您可以使用常數大大地提高程式碼的可讀性，並使它易於維護。  如果程式碼包含重複出現的值，或者是由某些很難記住或沒有明顯意義的數字所決定的值，則可以在程式碼中使用常數。  
  
## 如何建立和使用常數  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 包含許多預先定義的常數，主要用於列印或顯示功能。  您也可以使用 `Const` 陳述式建立自己的常數，使用原則跟建立變數名稱一樣。  如果 `Option Strict` 為 `On`，則必須明確宣告常數型別。  
  
 常數的範圍，也就是不需要完整限定常數名稱即可參考常數的所有程式碼的集合，跟相同位置所宣告的變數的範圍相同。  若要建立特定程序範圍中的常數，請在該程序中宣告。  若要建立整個應用程式都可以使用的常數，請在類別的宣告區段中使用 `Public` 關鍵字宣告這個常數。  
  
> [!NOTE]
>  雖然常數和變數相似，但是您不能像對變數一般地將常數加以修改或指派新值。  
  
 在程式碼中使用的常數，可以由所用控制項或元件的物件模型 \(Object Model\) 定義，也可以是由使用者定義的 \(也就是您自己建立的常數\)。  
  
## 編譯時期和執行階段常數  
 編譯時期常數是在程式碼編譯時期所運算的，而執行階段常數則只能在執行應用程式時加以運算。  每次執行應用程式時，編譯時期常數值都會相同，但執行階段常數則可能依次變更。  在陣列界限、case 運算式或列舉值初始設定式這類情況下，就需要有編譯時期常數。  
  
## 本章節內容  
  
|||  
|-|-|  
|定義|詞彙|  
|[How to: Declare A Constant](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)|說明如何使用 `Const` 陳述式宣告常數並設定其值，透過常數的宣告，將有意義的名稱指派給值。|  
|[User\-Defined Constants](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)|描述如何建立您自己的常數，包括範圍設定和如何避免循環參考的資訊。|  
|[Constant and Literal Data Types](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)|提供當 `Option Explicit` 為關閉時，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 編譯器 \(Compiler\) 如何初始化常數的資訊。|  
|[How to: Group Related Constant Values Together](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-group-related-constant-values-together.md)|示範如何將相關的常數值群組在一起。|  
  
## 參考資料  
  
|||  
|-|-|  
|定義|詞彙|  
|[Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)|列出 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 預先定義的常數。|  
|[Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md)|描述 `Const` 陳述式及其用法。|  
|[Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|說明 `Option Strict` 陳述式及其用法。|  
  
## 請參閱  
 [Enumerations Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)   
 [How to: Initialize an Array Variable in Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)