---
title: "Error Messages (Visual Basic) | Microsoft Docs"
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
  - "errors [Visual Basic]"
  - "error messages"
  - "trappable errors"
  - "errors [Visual Basic], trappable"
ms.assetid: f2dda05b-baef-41f5-8bb1-598bd7cf239f
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# Error Messages (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

當您撰寫，編譯或執行Visual Basic應用程式時，下列錯誤類型可能會發生:  
  
1.  設計階段錯誤，就會發生，當您在Visual Studio撰寫應用程式。  
  
2.  編譯時期錯誤，就會發生，當您編譯應用程式在Visual Studio中或在命令提示字元。  
  
3.  執行階段錯誤，就會發生，才能在執行的應用程式\(Visual Studio或當做獨立的可執行檔。  
  
 如需如何疑難排解特定錯誤的詳細資訊，請參閱 [Additional Resources for Visual Basic Programmers](../../../visual-basic/getting-started/additional-resources.md)。  
  
## 執行階段錯誤  
 如果Visual Basic應用程式嘗試執行系統無法執行的動作，就會發生執行階段錯誤和 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 擲回 `Exception` 物件。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會使用 `Throw` 陳述式，產生任何資料型別的自訂錯誤，包括 `Exception` 物件。  應用程式可以藉由顯示攔截之例外狀況的錯誤代碼和訊息識別這個錯誤。  如果未攔截錯誤，程式就會結束。  
  
 程式碼可截獲和檢查執行階段錯誤。  如果您將產生在 `Try` 區塊中的錯誤的程式碼，您可以尋找相符的 `Catch` 區塊內的任何擲回的錯誤。  如需如何截獲錯誤在執行階段和回應的資訊會在程式碼，請參閱 [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。  
  
## 編譯時間錯誤  
 如果Visual Basic編譯器在程式碼有問題，便會發生編譯時期錯誤。  在程式碼編輯器中，您可以輕鬆地識別哪一行程式碼會造成錯誤，因為波浪線出現下此程式碼行。  錯誤訊息，如果您指向波浪底線或開啟 **錯誤清單**，也會顯示其他訊息。  
  
 如果識別項具有波浪底線，而且短底線會出現在最右邊的字元之下，您可以產生類別、建構函式、方法、屬性、欄位或列舉的Stub。  如需詳細資訊，請參閱[使用時產生](/visual-cpp/misc/generate-from-usage)。  
  
 您可以從解析Visual Basic編譯器顯示的警告，您可以撰寫更快速地執行較少Bug的程式碼。  這些警告識別可能導致錯誤的程式碼，在應用程式執行時。  例如，編譯器警告時，如果嘗試叫用\(Invoke\)未指派之物件變數的成員，則從函式傳回，而不需要將傳回值或執行具有錯誤的 `Try` 區塊在邏輯攔截例外狀況。  如需警告的詳細資訊，包括如何開啟和關閉它們，請參閱 [在 Visual Basic 中設定警告](/visual-studio/ide/configuring-warnings-in-visual-basic)。