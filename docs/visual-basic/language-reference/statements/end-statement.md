---
title: "End Statement | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.End"
  - "End"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "execution, ending"
  - "files, closing"
  - "End keyword, End statements"
  - "programs, quitting"
  - "code, exiting"
  - "program termination"
  - "End statement"
  - "execution, stopping"
ms.assetid: 0e64467c-0f34-4aab-9ddd-43f8b9d55d90
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# End Statement
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

立即結束執行。  
  
## 語法  
  
```  
End  
```  
  
## 備註  
 您可以將 `End` 陳述式放在程序之中任何位置，以強制整個應用程式停止執行。  `End` 會關閉任何以 `Open` 陳述式開頭的檔案，並清除應用程式的所有變數。  一旦沒有其他程式會儲存物件的參考，也沒有程式碼在執行時，應用程式就會立即關閉。  
  
> [!NOTE]
>  `End` 陳述式會突然停止程式碼的執行，而不會叫用 `Dispose` 或 `Finalize` 方法，或任何其他的 Visual Basic 程式碼。  由其他程式使用的物件參考會失效。  若是在 `Try` 或 `Catch` 區塊中遇到 `End` 陳述式，控制權便不會傳送至相對應的 `Finally` 區塊。  
  
 `Stop` 陳述式暫停程式執行，但不像 `End`，它並不關閉任何檔案或清除任何變數 \(除非是在編譯過的可執行檔 \(.exe\) 中遇到它\)。  
  
 因為 `End` 在終止應用程式時並不會理會任何可能已開啟的資源，因此在使用它之前，您應該嘗試徹底地關閉所有資源。  例如，若應用程式已開啟了任何表單，則您應該在控制權到達 `End` 陳述式之前先將它關閉。  
  
 您應該謹慎地使用 `End`，而且只有在需要時立即停止使用。  終止程序的正常方法 \([Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) 與 [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)\) 不只會徹底地關閉程序，而且還會提供呼叫程式碼徹底關閉的機會。  例如，主控台應用程式可以簡單地從 `Main` 程序 `Return`。  
  
> [!IMPORTANT]
>  `End` 陳述式會呼叫 <xref:System.Environment> 類別的 <xref:System.Environment.Exit%2A> 方法 \(在 <xref:System> 命名空間中\)。  <xref:System.Environment.Exit%2A> 要求您具備 `UnmanagedCode` 權限。  如果您沒有，則會發生 <xref:System.Security.SecurityException> 錯誤。  
  
 在 [End \<keyword\> Statement](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md) 後面加上其他的關鍵字時，它會描述適當程式或區塊之定義的結束。  例如，`End Function` 會終止 `Function` 程序的定義。  
  
## 範例  
 下列範例會使用 `End` 陳述式，終止程式碼的執行 \(若使用者要求的話\)。  
  
 [!CODE [VbVersHelp60Controls#64](../CodeSnippet/VS_Snippets_VBCSharp/VbVersHelp60Controls#64)]  
  
## 智慧型裝置開發人員注意事項  
 不支援此陳述式。  
  
## 請參閱  
 <xref:System.Security.Permissions.SecurityPermissionFlag>   
 [Stop Statement](../../../visual-basic/language-reference/statements/stop-statement.md)   
 [End \<keyword\> Statement](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)