---
title: "如何：寫入應用程式事件記錄檔 (Visual Basic) | Microsoft Docs"
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
- Computer.EventLog element
- WriteEntry method
- My.Computer.EventLog element
- event logs, writing to
ms.assetid: cadbc8c1-87af-4746-934e-55b79a4f6e2b
caps.latest.revision: 21
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: ea527f0161a3bff759a8d33e4c5fa1c6c6e1df29
ms.contentlocale: zh-tw
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a>如何：寫入應用程式事件記錄檔 (Visual Basic)
您可以使用 `My.Application.Log` 和 `My.Log` 物件寫入發生在應用程式中之事件的相關資訊。 此範例示範如何設定事件記錄檔接聽程式，讓 `My.Application.Log` 將追蹤資訊寫入至應用程式事件記錄檔。  
  
 您無法寫入至安全性記錄檔。 要寫入至系統記錄檔，您必須是 LocalSystem 或 Administrator 帳戶的成員。  
  
 若要檢視事件記錄檔，您可以使用 [伺服器總管]  或 [Windows 事件檢視器] 。 如需詳細資訊，請參閱 [ETW Events in the .NET Framework](http://msdn.microsoft.com/library/d186276f-6afb-4dfd-bf3c-4251edc2c299)。  
  
> [!NOTE]
>  在 Windows 95、Windows 98 或 Windows Millennium Edition 上不支援事件記錄檔。  
  
### <a name="to-add-and-configure-the-event-log-listener"></a>加入及設定事件記錄檔接聽程式  
  
1.  在 方案總管 中，以滑鼠右鍵按一下 app.config 並選擇 [開啟]。  
  
     \-或-  
  
     如果沒有 app.config 檔案，  
  
    1.  在 [ **專案** ] 功能表中，選擇 [ **加入新項目**]。  
  
    2.  在 [加入新項目] 對話方塊中，選擇 [應用程式組態檔]。  
  
    3.  按一下 [加入] 。  
  
2.  在應用程式組態檔中找出 `<listeners>` 區段。  
  
     您會找到名稱屬性為 "DefaultSource" 之 `<listeners>` 區段 (位於最上層 `<source>` 區段底下 `<system.diagnostics>` 區段中) 中的 `<configuration>` 區段。  
  
3.  將此項目加入至該 `<listeners>` 區段︰  
  
    ```xml  
    <add name="EventLog"/>  
    ```  
  
4.  找出位於最上層 `<sharedListeners>` 區段中 `<system.diagnostics>` 區段的 `<configuration>` 區段。  
  
5.  將此項目加入至該 `<sharedListeners>` 區段︰  
  
    ```xml  
    <add name="EventLog"  
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
         initializeData="APPLICATION_NAME"/>  
    ```  
  
     以應用程式名稱取代 `APPLICATION_NAME` 。  
  
    > [!NOTE]
    >  一般而言，應用程式僅將錯誤寫入至事件記錄檔。 如需篩選記錄檔輸出的相關資訊，請參閱 [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)。  
  
### <a name="to-write-event-information-to-the-event-log"></a>將事件資訊寫入至事件記錄檔  
  
-   使用 `My.Application.Log.WriteEntry` 或 `My.Application.Log.WriteException` 方法，將資訊寫入事件記錄檔。 如需詳細資訊，請參閱[如何：寫入記錄訊息](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)和[如何：記錄例外狀況](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)。  
  
     設定組件的事件記錄檔接聽程式之後，接聽程式會接收從該組件寫入的所有訊息 `My.Applcation.Log` 。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>   
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>   
 [使用應用程式記錄檔](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)   
 [如何：記錄例外狀況](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)   
 [逐步解說：判斷 My.Application.Log 寫入資訊的位置](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
