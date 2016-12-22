---
title: "Troubleshooting: Log Listeners (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "event logs, troubleshooting"
  - "troubleshooting Visual Basic, event logs"
  - "troubleshooting event logs"
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Troubleshooting: Log Listeners (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

您可以使用 `My.Application.Log` 和 `My.Log` 物件，記錄在應用程式中發生的事件資訊。  
  
 若要判斷接收這些訊息的記錄檔接聽程式，請參閱[逐步解說：判斷 My.Application.Log 寫入資訊的位置](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)。  
  
 `Log` 物件可以使用記錄檔篩選，限制所記錄的資訊數量。  如果不當設定篩選條件，則記錄檔可能會包含錯誤資訊。  如需篩選的詳細資訊，請參閱[Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)。  
  
 不過，如果未正確設定記錄檔，則可能會需要記錄檔目前組態的詳細資訊。  您可以藉由記錄檔的進階 `TraceSource` 屬性 \(Property\) 取得此項資訊。  
  
### 若要判斷程式碼中記錄物件的記錄檔接聽程式  
  
1.  請在程式碼檔的開頭匯入 <xref:System.Diagnostics> 命名空間。  如需詳細資訊，請參閱 [Imports Statement \(.NET Namespace and Type\)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。  
  
     [!CODE [VbVbalrMyApplicationLog#13](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog#13)]  
  
2.  建立會傳回字串的函式，該字串包含每個記錄檔接聽程式的資訊。  
  
     [!CODE [VbVbalrMyApplicationLog#14](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog#14)]  
  
3.  將記錄檔的追蹤接聽程式集合傳遞至 `GetListeners` 函式，並顯示傳回值。  
  
     [!CODE [VbVbalrMyApplicationLog#19](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog#19)]  
  
     如需詳細資訊，請參閱 <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName>   
 [使用應用程式記錄檔](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)   
 [逐步解說：判斷 My.Application.Log 寫入資訊的位置](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)