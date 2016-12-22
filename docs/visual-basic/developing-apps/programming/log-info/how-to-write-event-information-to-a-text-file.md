---
title: "How to: Write Event Information to a Text File (Visual Basic) | Microsoft Docs"
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
  - "event logs [Visual Studio], writing event information"
  - "text files, writing event information to a text file"
  - "events [Visual Basic], writing event information to a text file"
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Write Event Information to a Text File (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

您可以使用 `My.Application.Log` 和 `My.Log` 物件，記錄在應用程式中發生的事件資訊。  這個範例會顯示如何使用 `My.Application.Log.WriteEntry` 方法，將追蹤資訊記錄到記錄檔。  
  
### 若要加入和設定檔案的記錄檔接聽程式  
  
1.  以滑鼠右鍵按一下 \[**方案總管**\] 的 \[app.config\]，並選擇 \[**開啟**\]。  
  
     \-或\-  
  
     如果沒有 app.config 檔：  
  
    1.  在 \[**專案**\] 功能表中，選擇 \[**加入新項目**\]。  
  
    2.  從 \[**加入新項目**\] 對話方塊中選擇 \[**應用程式組態檔**\]。  
  
    3.  按一下 \[**加入**\]。  
  
2.  在應用程式組態檔中尋找 `<listeners>` 區段。  
  
     您可以利用名稱屬性 \(Attribute\) "DefaultSource"，在 \<source\> 區段中找到 \<listeners\> 區段，以巢狀方式放在最上層 \<configuration\> 區段的 \<system.diagnostics\> 區段下。  
  
3.  將這個項目加入至此 `<listeners>` 區段：  
  
    ```  
    <add name="FileLogListener" />  
    ```  
  
4.  在以巢狀方式放在最上層 `<configuration>` 區段下的 `<system.diagnostics>` 區段中，尋找 `<sharedListeners>` 區段。  
  
5.  將這個項目加入至此 `<sharedListeners>` 區段：  
  
    ```  
    <add name="FileLogListener"   
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,   
              PublicKeyToken=b03f5f7f11d50a3a"  
        initializeData="FileLogListenerWriter"  
        location="Custom"  
        customlocation="c:\temp\" />  
    ```  
  
     將 `customlocation` 屬性的值變更為記錄檔目錄。  
  
    > [!NOTE]
    >  若要設定接聽程式屬性 \(Property\) 的值，請使用與屬性 \(Property\) 擁有相同名稱的屬性 \(Attribute\)，而該名稱中的所有字母皆為小寫。  例如，`location` 和 `customlocation` 屬性 \(Attribute\) 都會設定 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> 和 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> 屬性 \(Property\) 的值。  
  
### 若要將事件資訊寫入檔案記錄檔  
  
-   使用 `My.Application.Log.WriteEntry` 或 `My.Application.Log.WriteException` 方法，將資訊寫入檔案記錄檔。  如需詳細資訊，請參閱 [如何：寫入記錄訊息](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)和 [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)。  
  
     設定組件 \(Assembly\) 的檔案記錄檔接聽程式後，會從該組件中收到 `My.Application.Log` 寫入的所有訊息。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>   
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>   
 [使用應用程式記錄檔](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)   
 [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)