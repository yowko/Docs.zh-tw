---
title: "如何：在 Visual Basic 中記錄例外狀況 | Microsoft Docs"
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
- exceptions, logging
- exceptions, tracking
ms.assetid: a26c60e2-ae39-444a-aebb-33eccadc0eeb
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 8a5233f5e39c5e6c423a453cd241be40877d2ba8
ms.contentlocale: zh-tw
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-log-exceptions-in-visual-basic"></a>如何：在 Visual Basic 中記錄例外狀況
您可以使用 `My.Application.Log` 和 `My.Log` 物件來記錄應用程式中發生之例外狀況的相關資訊。 下列範例示範如何使用 `My.Application.Log.WriteException` 方法，以記錄您明確攔截到的例外狀況和未處理的例外狀況。  
  
 如需記錄追蹤資訊，請使用 `My.Application.Log.WriteEntry` 方法。 如需詳細資訊，請參閱 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>。  
  
### <a name="to-log-a-handled-exception"></a>記錄已處理的例外狀況  
  
1.  建立將產生例外狀況資訊的方法。  
  
     [!code-vb[VbVbalrMyApplicationLog#9](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_1.vb)]  
  
2.  使用 `Try...Catch` 區塊來攔截例外狀況。  
  
     [!code-vb[VbVbalrMyApplicationLog#6](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_2.vb)]  
  
3.  將可產生例外狀況的程式碼放在 `Try` 區塊中。  
  
     將 `Dim` 和 `MsgBox` 行取消註解，會導致 <xref:System.NullReferenceException> 例外狀況。  
  
     [!code-vb[VbVbalrMyApplicationLog#7](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_3.vb)]  
  
4.  在 `Catch` 區塊中，使用 `My.Application.Log.WriteException` 方法來寫入例外狀況資訊。  
  
     [!code-vb[VbVbalrMyApplicationLog#8](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_4.vb)]  
  
     下列範例顯示用於記錄已處理例外狀況的完整程式碼。  
  
     [!code-vb[VbVbalrMyApplicationLog#10](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_5.vb)]  
  
### <a name="to-log-an-unhandled-exception"></a>記錄未處理的例外狀況  
  
1.  在 **方案總管**中選取專案。 在 [ **專案** ] 功能表上，選擇 [ **屬性**]。  
  
2.  按一下 [應用程式] 索引標籤。  
  
3.  按一下 [檢視應用程式事件] 按鈕以開啟 [程式碼編輯器]。  
  
     這會開啟 ApplicationEvents.vb 檔案。  
  
4.  在 [程式碼編輯器] 中開啟 ApplicationEvents.vb 檔案。 在 [一般] 功能表上，選擇 [MyApplication 事件]。  
  
5.  在 [宣告] 功能表上，選擇 [未處理的例外狀況]。  
  
     應用程式會在主應用程式執行之前引發 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> 事件。  
  
6.  將 `My.Application.Log.WriteException` 方法加入 `UnhandledException` 事件處理常式。  
  
     [!code-vb[VbVbalrMyApplicationLog#4](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_6.vb)]  
  
     下列範例顯示用於記錄未處理例外狀況的完整程式碼。  
  
     [!code-vb[VbVbalrMyApplicationLog#5](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_7.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>   
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>   
 [使用應用程式記錄檔](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)   
 [如何：寫入記錄檔訊息](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)   
 [逐步解說：判斷 My.Application.Log 寫入資訊的位置](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)   
 [逐步解說：變更 My.Application.Log 寫入資訊的位置](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
