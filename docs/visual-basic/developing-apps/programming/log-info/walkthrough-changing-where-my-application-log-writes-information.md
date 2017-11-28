---
title: "變更 My.Application.Log 寫入資訊的位置 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Application.Log object, walkthroughs
- event logs, changing output location
ms.assetid: ecc74f95-743c-450d-93f6-09a30db0fe4a
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c4cd2e675bf1be4f065ee116795a95dae64d13d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-changing-where-myapplicationlog-writes-information-visual-basic"></a><span data-ttu-id="22c25-102">逐步解說：變更 My.Application.Log 寫入資訊的位置 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22c25-102">Walkthrough: Changing Where My.Application.Log Writes Information (Visual Basic)</span></span>
<span data-ttu-id="22c25-103">您可以使用 `My.Application.Log` 和 `My.Log` 物件來記錄應用程式中發生之事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="22c25-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="22c25-104">本逐步解說示範如何覆寫預設設定，而且使 `Log` 物件寫入至其他記錄檔接聽程式。</span><span class="sxs-lookup"><span data-stu-id="22c25-104">This walkthrough shows how to override the default settings and cause the `Log` object to write to other log listeners.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="22c25-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="22c25-105">Prerequisites</span></span>  
 <span data-ttu-id="22c25-106">`Log` 物件可以將資訊寫入數個記錄檔接聽程式。</span><span class="sxs-lookup"><span data-stu-id="22c25-106">The `Log` object can write information to several log listeners.</span></span> <span data-ttu-id="22c25-107">在變更設定前，您需要判斷目前的記錄檔接聽程式設定。</span><span class="sxs-lookup"><span data-stu-id="22c25-107">You need to determine the current configuration of the log listeners before changing the configurations.</span></span> <span data-ttu-id="22c25-108">如需詳細資訊，請參閱[逐步解說：判斷 My.Application.Log 寫入資訊的位置](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)。</span><span class="sxs-lookup"><span data-stu-id="22c25-108">For more information, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>  
  
 <span data-ttu-id="22c25-109">您也可以檢閱[如何：將事件資訊寫入至文字檔](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)，或[如何：寫入應用程式事件記錄檔](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)。</span><span class="sxs-lookup"><span data-stu-id="22c25-109">You may want to review [How to: Write Event Information to a Text File](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md) or [How to: Write to an Application Event Log](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md).</span></span>  
  
### <a name="to-add-listeners"></a><span data-ttu-id="22c25-110">加入接聽程式</span><span class="sxs-lookup"><span data-stu-id="22c25-110">To add listeners</span></span>  
  
1.  <span data-ttu-id="22c25-111">在 方案總管 中，以滑鼠右鍵按一下 app.config 並選擇 [開啟]。</span><span class="sxs-lookup"><span data-stu-id="22c25-111">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="22c25-112">\-或-</span><span class="sxs-lookup"><span data-stu-id="22c25-112">\- or -</span></span>  
  
     <span data-ttu-id="22c25-113">如果沒有 app.config 檔案︰</span><span class="sxs-lookup"><span data-stu-id="22c25-113">If there is no app.config file:</span></span>  
  
    1.  <span data-ttu-id="22c25-114">在 [ **專案** ] 功能表中，選擇 [ **加入新項目**]。</span><span class="sxs-lookup"><span data-stu-id="22c25-114">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="22c25-115">在 [加入新項目]  對話方塊中，選取 [應用程式組態檔] 。</span><span class="sxs-lookup"><span data-stu-id="22c25-115">From the **Add New Item** dialog box, select **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="22c25-116">按一下 [加入] 。</span><span class="sxs-lookup"><span data-stu-id="22c25-116">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="22c25-117">找出 `<listeners>` 區段，其位於 `<source>` 區段中具有 `name` 屬性 "DefaultSource" 的 `<sources>` 區段下。</span><span class="sxs-lookup"><span data-stu-id="22c25-117">Locate the `<listeners>` section, under the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section.</span></span> <span data-ttu-id="22c25-118">`<sources>` 區段位於最上層 `<system.diagnostics>` 區段中的 `<configuration>` 區段。</span><span class="sxs-lookup"><span data-stu-id="22c25-118">The `<sources>` section is in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
3.  <span data-ttu-id="22c25-119">將這些項目加入至該 `<listeners>` 區段。</span><span class="sxs-lookup"><span data-stu-id="22c25-119">Add these elements to that `<listeners>` section.</span></span>  
  
    ```xml  
    <!-- Uncomment to connect the application file log. -->  
    <!-- <add name="FileLog" /> -->  
    <!-- Uncomment to connect the event log. -->  
    <!-- <add name="EventLog" /> -->  
    <!-- Uncomment to connect the event log. -->  
    <!-- <add name="Delimited" /> -->  
    <!-- Uncomment to connect the XML log. -->  
    <!-- <add name="XmlWriter" /> -->  
    <!-- Uncomment to connect the console log. -->  
    <!-- <add name="Console" /> -->  
    ```  
  
4.  <span data-ttu-id="22c25-120">取消註解您想要收到 `Log` 訊息的記錄檔接聽程式。</span><span class="sxs-lookup"><span data-stu-id="22c25-120">Uncomment the log listeners that you want to receive `Log` messages.</span></span>  
  
5.  <span data-ttu-id="22c25-121">找出位於最上層 `<sharedListeners>` 區段中 `<system.diagnostics>` 區段的 `<configuration>` 區段。</span><span class="sxs-lookup"><span data-stu-id="22c25-121">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
6.  <span data-ttu-id="22c25-122">將這些項目加入至該 `<sharedListeners>` 區段。</span><span class="sxs-lookup"><span data-stu-id="22c25-122">Add these elements to that `<sharedListeners>` section.</span></span>  
  
    ```xml  
    <add name="FileLog"  
         type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
               Microsoft.VisualBasic, Version=8.0.0.0,   
               Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"  
         initializeData="FileLogWriter" />  
    <add name="EventLog"  
         type="System.Diagnostics.EventLogTraceListener,   
               System, Version=2.0.0.0,   
               Culture=neutral, PublicKeyToken=b77a5c561934e089"  
         initializeData="sample application"/>  
    <add name="Delimited"   
         type="System.Diagnostics.DelimitedListTraceListener,   
               System, Version=2.0.0.0,   
               Culture=neutral, PublicKeyToken=b77a5c561934e089"  
         initializeData="c:\temp\sampleDelimitedFile.txt"  
         traceOutputOptions="DateTime" />  
    <add name="XmlWriter"  
         type="System.Diagnostics.XmlWriterTraceListener,   
               System, Version=2.0.0.0,   
               Culture=neutral, PublicKeyToken=b77a5c561934e089"  
         initializeData="c:\temp\sampleLogFile.xml" />  
    <add name="Console"  
         type="System.Diagnostics.ConsoleTraceListener,   
               System, Version=2.0.0.0,   
               Culture=neutral, PublicKeyToken=b77a5c561934e089"  
         initializeData="true" />  
    ```  
  
7.  <span data-ttu-id="22c25-123">App.config 檔案的內容應該類似下列 XML：</span><span class="sxs-lookup"><span data-stu-id="22c25-123">The content of the app.config file should be similar to the following XML:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <!-- This section configures My.Application.Log -->  
          <source name="DefaultSource" switchName="DefaultSwitch">  
            <listeners>  
              <add name="FileLog"/>  
              <!-- Uncomment to connect the application file log. -->  
              <!-- <add name="FileLog" /> -->  
              <!-- Uncomment to connect the event log. -->  
              <!-- <add name="EventLog" /> -->  
              <!-- Uncomment to connect the event log. -->  
              <!-- <add name="Delimited" /> -->  
              <!-- Uncomment to connect the XML log. -->  
              <!-- <add name="XmlWriter" /> -->  
              <!-- Uncomment to connect the console log. -->  
              <!-- <add name="Console" /> -->  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="DefaultSwitch" value="Information" />  
        </switches>  
        <sharedListeners>  
          <add name="FileLog"  
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
                     Microsoft.VisualBasic, Version=8.0.0.0,   
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"  
               initializeData="FileLogWriter" />  
          <add name="EventLog"  
               type="System.Diagnostics.EventLogTraceListener,   
                     System, Version=2.0.0.0,   
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"  
               initializeData="sample application"/>  
          <add name="Delimited"   
               type="System.Diagnostics.DelimitedListTraceListener,   
                     System, Version=2.0.0.0,   
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"  
               initializeData="c:\temp\sampleDelimitedFile.txt"  
               traceOutputOptions="DateTime" />  
          <add name="XmlWriter"  
               type="System.Diagnostics.XmlWriterTraceListener,   
                     System, Version=2.0.0.0,   
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"  
               initializeData="c:\temp\sampleLogFile.xml" />  
          <add name="Console"  
               type="System.Diagnostics.ConsoleTraceListener,   
                     System, Version=2.0.0.0,   
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"  
               initializeData="true" />  
        </sharedListeners>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
### <a name="to-reconfigure-a-listener"></a><span data-ttu-id="22c25-124">重新設定接聽程式</span><span class="sxs-lookup"><span data-stu-id="22c25-124">To reconfigure a listener</span></span>  
  
1.  <span data-ttu-id="22c25-125">從 `<add>` 區段找出接聽程式的 `<sharedListeners>` 項目。</span><span class="sxs-lookup"><span data-stu-id="22c25-125">Locate the listener's `<add>` element from the `<sharedListeners>` section.</span></span>  
  
2.  <span data-ttu-id="22c25-126">`type` 屬性提供接聽程式類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="22c25-126">The `type` attribute gives the name of the listener type.</span></span> <span data-ttu-id="22c25-127">此類型必須繼承自 <xref:System.Diagnostics.TraceListener> 類別。</span><span class="sxs-lookup"><span data-stu-id="22c25-127">This type must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="22c25-128">使用以強式名稱方式命名的類型名稱來確定使用了正確的類型。</span><span class="sxs-lookup"><span data-stu-id="22c25-128">Use the strongly named type name to ensure that the right type is used.</span></span> <span data-ttu-id="22c25-129">如需詳細資訊，請參閱下列＜參考強制命名的類型＞一節。</span><span class="sxs-lookup"><span data-stu-id="22c25-129">For more information, see the "To reference a strongly named type" section below.</span></span>  
  
     <span data-ttu-id="22c25-130">您可以使用的類型如下︰</span><span class="sxs-lookup"><span data-stu-id="22c25-130">Some types that you can use are:</span></span>  
  
    -   <span data-ttu-id="22c25-131">寫入檔案記錄檔的 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> 接聽程式。</span><span class="sxs-lookup"><span data-stu-id="22c25-131">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> listener, which writes to a file log.</span></span>  
  
    -   <span data-ttu-id="22c25-132">將資訊寫入由 `initializeData` 參數指定之電腦事件記錄檔的 <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> 接聽程式。</span><span class="sxs-lookup"><span data-stu-id="22c25-132">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> listener, which writes information to the computer event log specified by the `initializeData` parameter.</span></span>  
  
    -   <span data-ttu-id="22c25-133">寫入由 `initializeData` 參數中指定之檔案的 <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> 和 <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> 接聽程式。</span><span class="sxs-lookup"><span data-stu-id="22c25-133">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> listeners, which write to the file specified in the `initializeData` parameter.</span></span>  
  
    -   <span data-ttu-id="22c25-134">寫入命令列主控台的 <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> 接聽程式。</span><span class="sxs-lookup"><span data-stu-id="22c25-134">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> listener, which writes to the command-line console.</span></span>  
  
     <span data-ttu-id="22c25-135">如需其他記錄檔接聽程式類型在何處寫入資訊的相關資訊，請查閱該類型的文件。</span><span class="sxs-lookup"><span data-stu-id="22c25-135">For information about where other types of log listeners write information, consult that type's documentation.</span></span>  
  
3.  <span data-ttu-id="22c25-136">當應用程式建立記錄檔接聽程式物件時，會傳遞 `initializeData` 屬性作為建構函式參數。</span><span class="sxs-lookup"><span data-stu-id="22c25-136">When the application creates the log-listener object, it passes the `initializeData` attribute as the constructor parameter.</span></span> <span data-ttu-id="22c25-137">`initializeData` 屬性的意義取決於追蹤接聽項。</span><span class="sxs-lookup"><span data-stu-id="22c25-137">The meaning of the `initializeData` attribute depends on the trace listener.</span></span>  
  
4.  <span data-ttu-id="22c25-138">建立記錄檔接聽程式之後，應用程式會設定接聽程式的屬性。</span><span class="sxs-lookup"><span data-stu-id="22c25-138">After creating the log listener, the application sets the listener's properties.</span></span> <span data-ttu-id="22c25-139">這些屬性由 `<add>` 項目中的其他屬性定義。</span><span class="sxs-lookup"><span data-stu-id="22c25-139">These properties are defined by the other attributes in the `<add>` element.</span></span> <span data-ttu-id="22c25-140">如需特定接聽程式屬性的詳細資訊，請參閱該接聽程式類型的文件。</span><span class="sxs-lookup"><span data-stu-id="22c25-140">For more information on the properties for a particular listener, see the documentation for that listener's type.</span></span>  
  
### <a name="to-reference-a-strongly-named-type"></a><span data-ttu-id="22c25-141">參考強式命名的類型</span><span class="sxs-lookup"><span data-stu-id="22c25-141">To reference a strongly named type</span></span>  
  
1.  <span data-ttu-id="22c25-142">若要確保記錄檔接聽程式使用正確的類型，請務必使用完整類型名稱和強式命名的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="22c25-142">To ensure that the right type is used for your log listener, make sure to use the fully qualified type name and the strongly named assembly name.</span></span> <span data-ttu-id="22c25-143">強式命名的類型語法如下所示︰</span><span class="sxs-lookup"><span data-stu-id="22c25-143">The syntax of a strongly named type is as follows:</span></span>  
  
     <span data-ttu-id="22c25-144">\<*類型名稱*>, \<*組件名稱*>, \<*版本號碼*>, \<*文化特性*>, \<*強式名稱*></span><span class="sxs-lookup"><span data-stu-id="22c25-144">\<*type name*>, \<*assembly name*>, \<*version number*>, \<*culture*>, \<*strong name*></span></span>  
  
2.  <span data-ttu-id="22c25-145">這個程式碼範例示範在此情況下如何判斷完整類型 "System.Diagnostics.FileLogTraceListener" 之強式命名的類型。</span><span class="sxs-lookup"><span data-stu-id="22c25-145">This code example shows how to determine the strongly named type name for a fully qualified type—"System.Diagnostics.FileLogTraceListener" in this case.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#15](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-changing-where-my-application-log-writes-information_1.vb)]  
  
     <span data-ttu-id="22c25-146">這就是輸出的資料，並可用於唯一參考強式命名的類型，如上方「加入接聽程式」 程序所示。</span><span class="sxs-lookup"><span data-stu-id="22c25-146">This is the output, and it can be used to uniquely reference a strongly named type, as in the "To add listeners" procedure above.</span></span>  
  
     `Microsoft.VisualBasic.Logging.FileLogTraceListener, Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`  
  
## <a name="see-also"></a><span data-ttu-id="22c25-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22c25-147">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>  
 <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>  
 [<span data-ttu-id="22c25-148">如何：將事件資訊寫入至文字檔</span><span class="sxs-lookup"><span data-stu-id="22c25-148">How to: Write Event Information to a Text File</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)  
 [<span data-ttu-id="22c25-149">如何：寫入應用程式事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="22c25-149">How to: Write to an Application Event Log</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)
