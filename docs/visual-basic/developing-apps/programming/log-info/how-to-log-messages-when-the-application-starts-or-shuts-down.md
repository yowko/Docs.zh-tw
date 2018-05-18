---
title: 如何：在應用程式啟動或關閉時記錄訊息 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, shutdown
- My.Application.Log object, logging
- Startup event [Visual Basic]
- event logs, startup
- Shutdown event [Visual Basic]
- My.Log object, logging
ms.assetid: 67624d05-cddf-48b7-8c36-5c99baa4c621
ms.openlocfilehash: 80b07e67cb307d461e63df9f94c9d0962eb6374a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a>如何：在應用程式啟動或關閉時記錄訊息 (Visual Basic)
您可以使用 `My.Application.Log` 和 `My.Log` 物件來記錄應用程式中發生之事件的相關資訊。 此範例示範如何使用 `My.Application.Log.WriteEntry` 方法 `Startup` 和 `Shutdown` 事件寫入追蹤資訊。  
  
### <a name="to-access-the-applications-event-handler-code"></a>存取應用程式的事件處理常式程式碼  
  
1.  在 **方案總管**中選取專案。 在 [ **專案** ] 功能表上，選擇 [ **屬性**]。  
  
2.  按一下 [應用程式]  索引標籤。  
  
3.  按一下 [檢視應用程式事件]  按鈕以開啟 [程式碼編輯器]。  
  
     這會開啟 ApplicationEvents.vb 檔案。  
  
### <a name="to-log-messages-when-the-application-starts"></a>在應用程式啟動時記錄訊息  
  
1.  在 [程式碼編輯器] 中開啟 ApplicationEvents.vb 檔案。 在 [一般]  功能表上，選擇 [MyApplication 事件] 。  
  
2.  在 [宣告]  功能表上，選擇 [啟動] 。  
  
     應用程式在主應用程式執行之前，引發 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> 事件。  
  
3.  將 `My.Application.Log.WriteEntry` 方法加入 `Startup` 事件處理常式。  
  
     [!code-vb[VbVbalrMyApplicationLog#1](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_1.vb)]  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a>在應用程式關閉時記錄訊息  
  
1.  在 [程式碼編輯器] 中開啟 ApplicationEvents.vb 檔案。 在 [一般]  功能表上，選擇 [MyApplication 事件] 。  
  
2.  在 [宣告]  功能表上，選擇 [關機] 。  
  
     應用程式在主應用程式執行後，但在關閉前引發 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> 事件。  
  
3.  將 `My.Application.Log.WriteEntry` 方法加入 `Shutdown` 事件處理常式。  
  
     [!code-vb[VbVbalrMyApplicationLog#2](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_2.vb)]  
  
## <a name="example"></a>範例  
 您可以使用 [專案設計工具] 在 [程式碼編輯器] 中存取應用程式事件。 如需詳細資訊，請參閱[專案設計工具、應用程式頁 (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)。  
  
 [!code-vb[VbVbalrMyApplicationLog#3](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_3.vb)]  
  
## <a name="see-also"></a>請參閱  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 [專案設計工具、應用程式頁面 (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)  
 [使用應用程式記錄檔](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
