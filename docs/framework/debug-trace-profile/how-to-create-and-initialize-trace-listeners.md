---
title: "如何：建立和初始設定追蹤接聽項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- initializing trace listeners
- trace listeners, creating
- trace listeners, initializing
- tracing [.NET Framework], trace listeners
- logs, trace listeners
ms.assetid: 21726de1-61ee-4fdc-9dd0-3be49324d066
caps.latest.revision: 12
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 38b2240f3f245e01f3aefaec14f5b7510a67ceae
ms.contentlocale: zh-tw
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-create-and-initialize-trace-listeners"></a>如何：建立和初始設定追蹤接聽項
<xref:System.Diagnostics.Debug?displayProperty=fullName> 和 <xref:System.Diagnostics.Trace?displayProperty=fullName> 類別會將訊息傳送給名稱為接聽程式的物件，以接收和處理這些訊息。 <xref:System.Diagnostics.DefaultTraceListener?displayProperty=fullName> 就是這類接聽程式之一，其會在啟用追蹤或偵錯時自動建立與初始化。 如果您要將 <xref:System.Diagnostics.Trace> 或 <xref:System.Diagnostics.Debug> 輸出導向任何其他來源，您必須建立和初始化其他的追蹤接聽程式。  
  
 您建立的接聽程式應反映出您應用程式的需求。 例如，如果您想要取得所有追蹤輸出的文字記錄，可建立 <xref:System.Diagnostics.TextWriterTraceListener> 接聽程式，以在啟用時，將所有輸出寫入新的文字檔。 反之，如果您只想在應用程式執行期間檢視輸出，可建立 <xref:System.Diagnostics.ConsoleTraceListener> 接聽程式，將所有輸出導向主控台視窗。 <xref:System.Diagnostics.EventLogTraceListener> 可以將追蹤輸出導向事件記錄檔。 如需詳細資訊，請參閱[追蹤接聽項](../../../docs/framework/debug-trace-profile/trace-listeners.md)。  
  
 您可以在[應用程式組態檔](../../../docs/framework/configure-apps/index.md)或程式碼中建立追蹤接聽項。 建議您使用應用程式組態檔，因為它們可讓您新增、修改或移除追蹤接聽程式，而不必變更程式碼。  
  
### <a name="to-create-and-use-a-trace-listener-by-using-a-configuration-file"></a>若要使用組態檔建立及使用追蹤接聽程式  
  
1.  在應用程式組態檔中，宣告您的追蹤接聽程式。 如果您要建立的接聽程式需要任何其他物件，請一併將其宣告。 下列範例示範如何建立名稱為 `myListener` 的接聽程式，以進行文字檔 `TextWriterOutput.log` 的寫入作業。  
  
    ```xml  
    <configuration>  
      <system.diagnostics>  
        <trace autoflush="false" indentsize="4">  
          <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener" initializeData="TextWriterOutput.log" />  
            <remove name="Default" />  
          </listeners>  
        </trace>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
2.  使用程式碼中的 <xref:System.Diagnostics.Trace> 類別，將訊息寫入追蹤接聽程式。  
  
    ```vb  
    Trace.TraceInformation("Test message.")  
    ' You must close or flush the trace to empty the output buffer.  
    Trace.Flush()  
    ```  
  
    ```csharp  
    Trace.TraceInformation("Test message.");  
    // You must close or flush the trace to empty the output buffer.  
    Trace.Flush();  
    ```  
  
### <a name="to-create-and-use-a-trace-listener-in-code"></a>若要建立及使用程式碼中的追蹤接聽程式  
  
-   將追蹤接聽程式加入 <xref:System.Diagnostics.Trace.Listeners%2A> 集合，並傳送追蹤資訊給接聽程式。  
  
    ```vb  
    Trace.Listeners.Add(New TextWriterTraceListener("TextWriterOutput.log", "myListener"))  
    Trace.TraceInformation("Test message.")  
    ' You must close or flush the trace to empty the output buffer.  
    Trace.Flush()  
    ```  
  
    ```csharp  
    Trace.Listeners.Add(new TextWriterTraceListener("TextWriterOutput.log", "myListener"));  
    Trace.TraceInformation("Test message.");  
    // You must close or flush the trace to empty the output buffer.  
    Trace.Flush();  
    ```  
  
     - 或 -  
  
-   如果您不想讓接聽程式接收追蹤輸出，請不要將它加入 <xref:System.Diagnostics.Trace.Listeners%2A> 集合。 您可以呼叫接聽程式自己的輸出方法，透過獨立於 <xref:System.Diagnostics.Trace.Listeners%2A> 集合的接聽程式來發出輸出。 下列範例示範如何將指令行寫入不在 <xref:System.Diagnostics.Trace.Listeners%2A> 集合內的接聽程式。  
  
    ```vb  
    Dim myListener As New TextWriterTraceListener("TextWriterOutput.log", "myListener")  
    myListener.WriteLine("Test message.")  
    ' You must close or flush the trace listener to empty the output buffer.  
    myListener.Flush()  
    ```  
  
    ```csharp  
    TextWriterTraceListener myListener = new TextWriterTraceListener("TextWriterOutput.log", "myListener");  
    myListener.WriteLine("Test message.");  
    // You must close or flush the trace listener to empty the output buffer.  
    myListener.Flush();  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [追蹤接聽項](../../../docs/framework/debug-trace-profile/trace-listeners.md)   
 [追蹤參數](../../../docs/framework/debug-trace-profile/trace-switches.md)   
 [如何：將追蹤陳述式新增至應用程式程式碼](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)   
 [追蹤和檢測應用程式](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)

