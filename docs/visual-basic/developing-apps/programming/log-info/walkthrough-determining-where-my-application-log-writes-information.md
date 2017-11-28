---
title: "判斷 My.Application.Log 寫入資訊的位置 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Log object, output location
- output, application log location
- My.Application.Log object, outpout location
- event logs, determining output location
- application event logs, output location
- applications [Visual Basic], output location
ms.assetid: 5b70143a-7741-45f2-ae1d-03324a3a4189
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4df7a80907b29a5eea79992f46c46603cbe2cc81
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a>逐步解說：判斷 My.Application.Log 寫入資訊的位置 (Visual Basic)
`My.Application.Log` 物件可以將資訊寫入數個記錄檔接聽程式。 記錄檔接聽程式由電腦組態檔所設定，而且可以由應用程式組態檔覆寫。 本主題將說明預設設定，以及如何判斷應用程式的設定。  
  
 如需預設輸出位置的詳細資訊，請參閱[使用應用程式記錄檔](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)。  
  
### <a name="to-determine-the-listeners-for-myapplicationlog"></a>判斷 My.Application.Log 的接聽程式  
  
1.  找出組件的組態檔。 如果您正在開發組件，您可以從 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] 方案總管 **存取在**中的 app.config。 否則組態檔名稱會是組件的名稱加上 ".config"，而且會位於與組件相同的目錄內。  
  
    > [!NOTE]
    >  並非每個組件都有組態檔。  
  
     組態檔為 XML 檔案。  
  
2.  在 `<listeners>` 區段下，具有 `<source>` 屬性 "DefaultSource" 的 `name` 區段中找出 `<sources>` 區段。 `<sources>` 區段位於最上層 `<system.diagnostics>` 區段中的 `<configuration>` 區段內。  
  
     如果這些區段不存在，則電腦的組態檔可能會設定 `My.Application.Log` 記錄接聽程式。 下列步驟描述如何判斷電腦組態檔能夠定義哪些事︰  
  
    1.  找出電腦的 machine.config 檔案。 一般而言，它位於 *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* 目錄中，其中 `SystemRoot` 為作業系統的目錄，而 `frameworkVersion` 為 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]的版本。  
  
         machine.config 中的設定可以由應用程式組態檔覆寫。  
  
         如果下列選擇性項目不存在的話，您可以建立它們。  
  
    2.  在最上層 `<listeners>` 區段下， `<source>` 區段的 `name` 區段內，具備 `<sources>` 屬性 "DefaultSource" 的 `<system.diagnostics>` 區段中找出 `<configuration>` 區段。  
  
         如果這些區段不存在的話，則 `My.Application.Log` 只具有預設記錄檔接聽程式。  
  
3.  找出 <`listeners>` 區段中的 <`add>` 項目。  
  
     這些項目將已命名的記錄檔接聽程式加入至 `My.Application.Log` 來源。  
  
4.  在最上層 `<add>` 區段下， `<sharedListeners>` 區段中的 `<system.diagnostics>` 區段內，找出具有記錄檔接聽程式名稱 `<configuration>` 項目。  
  
5.  對於許多共用接聽項的類型，接聽程式的初始化資料包含接聽程式將資料導向何處的描述︰  
  
    -   如簡介中所述，<xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> 接聽程式會寫入檔案記錄檔。  
  
    -   <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> 接聽程式會將資訊寫入由 `initializeData` 參數所指定的電腦事件記錄檔。 若要檢視事件記錄檔，您可以使用 [伺服器總管]  或 [Windows 事件檢視器] 。 如需詳細資訊，請參閱 [ETW Events in the .NET Framework](http://msdn.microsoft.com/library/d186276f-6afb-4dfd-bf3c-4251edc2c299)。  
  
    -   <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> 和 <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> 接聽程式會寫入 `initializeData` 參數中指定的檔案。  
  
    -   <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> 接聽程式會寫入命令列主控台。  
  
    -   如需其他記錄檔接聽程式類型在何處寫入資訊的相關資訊，請查閱該類型的文件。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 <xref:System.Diagnostics.DelimitedListTraceListener>  
 <xref:System.Diagnostics.XmlWriterTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics>  
 [使用應用程式記錄檔](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [如何：記錄例外狀況](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)  
 [如何：寫入記錄檔訊息](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)  
 [逐步解說：變更 My.Application.Log 寫入資訊的位置](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)  
 [.NET Framework 中的 ETW 事件](http://msdn.microsoft.com/library/d186276f-6afb-4dfd-bf3c-4251edc2c299)  
 [疑難排解：記錄檔接聽程式](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)
