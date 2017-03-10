---
title: "Efficient Use of Data Types (Visual Basic) | Microsoft Docs"
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
  - "performance, data type efficiency"
  - "data types [Visual Basic], weak typing"
  - "AscW function, preferred to Asc"
  - "data types [Visual Basic], using efficiently"
  - "optimization, data types"
  - "data types [Visual Basic], strong typing"
  - "strong typing"
  - "typing, strong"
  - "data types [Visual Basic], optimizing"
  - "ChrW function, preferred to Chr"
ms.assetid: 28f5e4ba-ec24-4f37-b90a-e8ee822f778a
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Efficient Use of Data Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

未宣告的變數以及不具資料型別的宣告變數都會指定為 `Object` 資料型別。  這會加快程式的撰寫，但可能會使程式的執行變慢。  
  
## 強型別指定  
 指定所有變數的資料型別稱為「*強型別指定*」\(Strong Typing\)。  使用強型別指定有以下幾點好處：  
  
-   讓 IntelliSense 能夠支援變數。  這能讓您在輸入程式碼時看到變數的屬性及其他成員。  
  
-   可以利用編譯器型別檢查，  這能找出可能因錯誤 \(例如溢位\) 而在 Run Time 失敗的陳述式。  這也能夠偵測在不支援變數的物件上所進行的方法呼叫。  
  
-   執行程式碼的速度較快。  
  
## 最有效率的資料型別  
 針對從不包含分數的變數來說，整數資料型別的效率要比非整數型別的效率高。  在 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中，`Integer` 與 `UInteger` 是最有效率的數字型別 \(Numeric Type\)。  
  
 而對於分數來說，`Double` 是最有效率的資料型別，因為目前平台上的處理器是以雙精度浮點數 \(Double\) 執行浮點運算。  然而，`Double` 作業不會像 `Integer` 的整數類資料型別一樣快。  
  
## 指定資料型別  
 使用 [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) 宣告特定型別的變數。  您可以使用 [Public](../../../../visual-basic/language-reference/modifiers/public.md)、[Protected](../../../../visual-basic/language-reference/modifiers/protected.md)、[Friend](../../../../visual-basic/language-reference/modifiers/friend.md) 或 [Private](../../../../visual-basic/language-reference/modifiers/private.md) 關鍵字同時指定存取等級，如下列範例所示。  
  
```  
Private x As Double  
Protected s As String  
```  
  
## 字元轉換  
 `AscW` 和 `ChrW` 函式以 Unicode 格式作業。  這些函式的使用順序優先於 `Asc` 和 `Chr`，因為要使用這兩個函式，必須轉譯為 Unicode，再從 Unicode 轉譯回來。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>   
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>   
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>   
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>   
 [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Numeric Data Types](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)   
 [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [使用 IntelliSense](/visual-studio/ide/using-intellisense)