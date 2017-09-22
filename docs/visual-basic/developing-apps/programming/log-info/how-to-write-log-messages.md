---
title: "如何：寫入記錄訊息 (Visual Basic)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- My.Application.Log object, writing log messags
ms.assetid: 972a3e0c-2996-4623-a7a9-d7ebc4d207f8
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ffc45b93250ba9e909776352b702be2e8295435d
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# 如何：寫入記錄訊息 (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

您可以使用 `My.Application.Log` 和 `My.Log` 物件記錄應用程式的相關資訊。 此範例示範如何使用 `My.Application.Log.WriteEntry` 方法寫入追蹤資訊。  
  
 如需記錄例外狀況資訊，請使用 `My.Application.Log.WriteException` 方法；請參閱 [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)。  
  
## 範例  
 此範例使用 `My.Application.Log.WriteEntry` 方法以寫出追蹤資訊。  
  
 [!code-vb[VbVbalrMyApplicationLog#11](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-write-log-messages_1.vb)]  
  
## .NET Framework 安全性  
 請確定您寫入記錄檔的資料不包含機密資訊，例如使用者密碼。 如需詳細資訊，請參閱[使用應用程式記錄檔](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>   
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>   
 [使用應用程式記錄檔](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)   
 [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)   
 [逐步解說：判斷 My.Application.Log 寫入資訊的位置](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)   
 [逐步解說：變更 My.Application.Log 寫入資訊的位置](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)   
 [逐步解說：篩選 My.Application.Log 輸出](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)

