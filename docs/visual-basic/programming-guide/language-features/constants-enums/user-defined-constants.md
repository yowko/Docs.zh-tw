---
title: "User-Defined Constants (Visual Basic) | Microsoft Docs"
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
  - "constants, circular references"
  - "Const statement [Visual Basic], user-defined constants"
  - "user-defined constants"
  - "scope, constants"
  - "constants, user-defined"
  - "circular references between constants"
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# User-Defined Constants (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

常數是個取代不會變動的數字或字串的有意義名稱。  如同它的名稱所示，常數用來儲存應用程式執行過程中維持不變的值。  您可以使用操作中控制項或元件所定義的常數，或是自己建立常數。  您自己建立的常數就是所謂的「*使用者定義*」\(User\-defined\) 常數。  
  
 您可使用 `Const` 陳述式宣告常數，方式和建立變數名稱一樣。  如果 `Option Strict` 為 `On`，則必須明確宣告常數型別。  
  
## Const 陳述式的使用方式  
 `Const` 陳述式可以表示數學或日期\/時間數量。  
  
 [!code-vb[VbEnumsTask#10](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_1.vb)]  
  
 它也可以定義 `String` 常數：  
  
 [!code-vb[VbEnumsTask#13](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_2.vb)]  
  
 等號 \(`=`\) 右邊的運算式通常是個數字或常值字串，但也可以是產生數字或字串的運算式 \(雖然運算式無法包含函式呼叫\)。  您甚至可以根據之前定義的常數來定義新的常數：  
  
 [!code-vb[VbEnumsTask#15](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_3.vb)]  
  
## 使用者定義常數的範圍  
 `Const` 陳述式的範圍和在相同位置所宣告的變數範圍一樣。  您可以用下列任一方式指定範圍：  
  
-   若要建立只在一個程序中存在的常數，請在該程序內宣告這個常數。  
  
-   若要建立可被類別中所有程序使用，但不可以被該模組外的程式碼使用的常數，請在類別的宣告區段中宣告這個常數。  
  
-   若要建立可由組件的所有成員使用，但不可由組件外部用戶端使用的常數，請在類別的宣告區段中使用 `Friend` 關鍵字宣告這個常數。  
  
-   若要建立整個應用程式都可以使用的常數，請在類別的宣告區段中使用 `Public` 關鍵字宣告這個常數。  
  
 如需詳細資訊，請參閱 [How to: Declare A Constant](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)。  
  
### 避免循環參考  
 由於可以根據其他常數定義常數，因此可能會不小心在兩個或多個常數間建立「*循環*」\(Cycle\) 或循環參考。  當您有兩個或多個公用常數，而每個都是根據其他常數而定義時，便會發生循環，如下列範例所示：  
  
 [!code-vb[VbEnumsTask#16](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_4.vb)]  
[!code-vb[VbEnumsTask#17](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_5.vb)]  
  
 發生循環時，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會產生編譯器錯誤。  
  
## 請參閱  
 [Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md)   
 [Constant and Literal Data Types](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)   
 [Constants and Enumerations](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)   
 [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)   
 [Enumerations Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)   
 [Constants Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)   
 [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)