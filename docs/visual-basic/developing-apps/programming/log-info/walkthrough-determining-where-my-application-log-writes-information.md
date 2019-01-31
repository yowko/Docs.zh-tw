---
title: 判斷 My.Application.Log 寫入資訊的位置 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, output location
- output, application log location
- My.Application.Log object, outpout location
- event logs, determining output location
- application event logs, output location
- applications [Visual Basic], output location
ms.assetid: 5b70143a-7741-45f2-ae1d-03324a3a4189
ms.openlocfilehash: bafb307eff6a5ce6fd6dff823abe2f68b7725f51
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662669"
---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a><span data-ttu-id="3270c-102">逐步解說：判斷 My.Application.Log 寫入資訊的位置 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3270c-102">Walkthrough: Determining Where My.Application.Log Writes Information (Visual Basic)</span></span>
<span data-ttu-id="3270c-103">`My.Application.Log` 物件可以將資訊寫入數個記錄檔接聽程式。</span><span class="sxs-lookup"><span data-stu-id="3270c-103">The `My.Application.Log` object can write information to several log listeners.</span></span> <span data-ttu-id="3270c-104">記錄檔接聽程式由電腦組態檔所設定，而且可以由應用程式組態檔覆寫。</span><span class="sxs-lookup"><span data-stu-id="3270c-104">The log listeners are configured by the computer's configuration file and can be overridden by an application's configuration file.</span></span> <span data-ttu-id="3270c-105">本主題將說明預設設定，以及如何判斷應用程式的設定。</span><span class="sxs-lookup"><span data-stu-id="3270c-105">This topic describes the default settings and how to determine the settings for your application.</span></span>  
  
 <span data-ttu-id="3270c-106">如需預設輸出位置的詳細資訊，請參閱[使用應用程式記錄檔](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)。</span><span class="sxs-lookup"><span data-stu-id="3270c-106">For more information about the default output locations, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>  
  
### <a name="to-determine-the-listeners-for-myapplicationlog"></a><span data-ttu-id="3270c-107">判斷 My.Application.Log 的接聽程式</span><span class="sxs-lookup"><span data-stu-id="3270c-107">To determine the listeners for My.Application.Log</span></span>  
  
1.  <span data-ttu-id="3270c-108">找出組件的組態檔。</span><span class="sxs-lookup"><span data-stu-id="3270c-108">Locate the assembly's configuration file.</span></span> <span data-ttu-id="3270c-109">如果您正在開發組件，則可以從 [方案總管] 存取 Visual Studio 中的 app.config。</span><span class="sxs-lookup"><span data-stu-id="3270c-109">If you are developing the assembly, you can access the app.config in Visual Studio from the **Solution Explorer**.</span></span> <span data-ttu-id="3270c-110">否則組態檔名稱會是組件的名稱加上 ".config"，而且會位於與組件相同的目錄內。</span><span class="sxs-lookup"><span data-stu-id="3270c-110">Otherwise, the configuration file name is the assembly's name appended with ".config", and it is located in the same directory as the assembly.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3270c-111">並非每個組件都有組態檔。</span><span class="sxs-lookup"><span data-stu-id="3270c-111">Not every assembly has a configuration file.</span></span>  
  
     <span data-ttu-id="3270c-112">組態檔為 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="3270c-112">The configuration file is an XML file.</span></span>  
  
2.  <span data-ttu-id="3270c-113">在 `<listeners>` 區段下，具有 `<source>` 屬性 "DefaultSource" 的 `name` 區段中找出 `<sources>` 區段。</span><span class="sxs-lookup"><span data-stu-id="3270c-113">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="3270c-114">`<sources>` 區段位於最上層 `<system.diagnostics>` 區段中的 `<configuration>` 區段內。</span><span class="sxs-lookup"><span data-stu-id="3270c-114">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
     <span data-ttu-id="3270c-115">如果這些區段不存在，則電腦的組態檔可能會設定 `My.Application.Log` 記錄接聽程式。</span><span class="sxs-lookup"><span data-stu-id="3270c-115">If these sections do not exist, then the computer's configuration file may configure the `My.Application.Log` log listeners.</span></span> <span data-ttu-id="3270c-116">下列步驟描述如何判斷電腦組態檔能夠定義哪些事︰</span><span class="sxs-lookup"><span data-stu-id="3270c-116">The following steps describe how to determine what the computer configuration file defines:</span></span>  
  
    1.  <span data-ttu-id="3270c-117">找出電腦的 machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="3270c-117">Locate the computer's machine.config file.</span></span> <span data-ttu-id="3270c-118">一般而言，它位於 *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* 目錄中，其中 `SystemRoot` 為作業系統的目錄，而 `frameworkVersion` 為 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]的版本。</span><span class="sxs-lookup"><span data-stu-id="3270c-118">Typically, it is located in the *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* directory, where `SystemRoot` is the operating system directory, and `frameworkVersion` is the version of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span>  
  
         <span data-ttu-id="3270c-119">machine.config 中的設定可以由應用程式組態檔覆寫。</span><span class="sxs-lookup"><span data-stu-id="3270c-119">The settings in machine.config can be overridden by an application's configuration file.</span></span>  
  
         <span data-ttu-id="3270c-120">如果下列選擇性項目不存在的話，您可以建立它們。</span><span class="sxs-lookup"><span data-stu-id="3270c-120">If the optional elements listed below do not exist, you can create them.</span></span>  
  
    2.  <span data-ttu-id="3270c-121">在最上層 `<listeners>` 區段下， `<source>` 區段的 `name` 區段內，具備 `<sources>` 屬性 "DefaultSource" 的 `<system.diagnostics>` 區段中找出 `<configuration>` 區段。</span><span class="sxs-lookup"><span data-stu-id="3270c-121">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
         <span data-ttu-id="3270c-122">如果這些區段不存在的話，則 `My.Application.Log` 只具有預設記錄檔接聽程式。</span><span class="sxs-lookup"><span data-stu-id="3270c-122">If these sections do not exist, then the `My.Application.Log` has only the default log listeners.</span></span>  
  
3.  <span data-ttu-id="3270c-123">找出 <`listeners>` 區段中的 <`add>` 項目。</span><span class="sxs-lookup"><span data-stu-id="3270c-123">Locate the <`add>` elements in the <`listeners>` section.</span></span>  
  
     <span data-ttu-id="3270c-124">這些項目將已命名的記錄檔接聽程式加入至 `My.Application.Log` 來源。</span><span class="sxs-lookup"><span data-stu-id="3270c-124">These elements add the named log listeners to `My.Application.Log` source.</span></span>  
  
4.  <span data-ttu-id="3270c-125">在最上層 `<add>` 區段下， `<sharedListeners>` 區段中的 `<system.diagnostics>` 區段內，找出具有記錄檔接聽程式名稱 `<configuration>` 項目。</span><span class="sxs-lookup"><span data-stu-id="3270c-125">Locate the `<add>` elements with the names of the log listeners in the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
5.  <span data-ttu-id="3270c-126">對於許多共用接聽項的類型，接聽程式的初始化資料包含接聽程式將資料導向何處的描述︰</span><span class="sxs-lookup"><span data-stu-id="3270c-126">For many types of shared listeners, the listener's initialization data includes a description of where the listener directs the data:</span></span>  
  
    -   <span data-ttu-id="3270c-127">如簡介中所述，<xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> 接聽程式會寫入檔案記錄檔。</span><span class="sxs-lookup"><span data-stu-id="3270c-127">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> listener writes to a file log, as described in the introduction.</span></span>  
  
    -   <span data-ttu-id="3270c-128"><xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> 接聽程式會將資訊寫入由 `initializeData` 參數所指定的電腦事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="3270c-128">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> listener writes information to the computer event log specified by the `initializeData` parameter.</span></span> <span data-ttu-id="3270c-129">若要檢視事件記錄檔，您可以使用 [伺服器總管] 或 [Windows 事件檢視器]。</span><span class="sxs-lookup"><span data-stu-id="3270c-129">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="3270c-130">如需詳細資訊，請參閱 [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md)。</span><span class="sxs-lookup"><span data-stu-id="3270c-130">For more information, see [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md).</span></span>  
  
    -   <span data-ttu-id="3270c-131"><xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> 和 <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> 接聽程式會寫入 `initializeData` 參數中指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="3270c-131">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> listeners write to the file specified in the `initializeData` parameter.</span></span>  
  
    -   <span data-ttu-id="3270c-132"><xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> 接聽程式會寫入命令列主控台。</span><span class="sxs-lookup"><span data-stu-id="3270c-132">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> listener writes to the command-line console.</span></span>  
  
    -   <span data-ttu-id="3270c-133">如需其他記錄檔接聽程式類型在何處寫入資訊的相關資訊，請查閱該類型的文件。</span><span class="sxs-lookup"><span data-stu-id="3270c-133">For information about where other types of log listeners write information, consult that type's documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3270c-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3270c-134">See also</span></span>
- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DelimitedListTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics>
- [<span data-ttu-id="3270c-135">使用應用程式記錄檔</span><span class="sxs-lookup"><span data-stu-id="3270c-135">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="3270c-136">如何：記錄例外狀況</span><span class="sxs-lookup"><span data-stu-id="3270c-136">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="3270c-137">如何：寫入記錄檔訊息</span><span class="sxs-lookup"><span data-stu-id="3270c-137">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="3270c-138">逐步解說：變更 My.Application.Log 寫入資訊的位置</span><span class="sxs-lookup"><span data-stu-id="3270c-138">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [<span data-ttu-id="3270c-139">.NET Framework 中的 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="3270c-139">ETW Events in the .NET Framework</span></span>](../../../../framework/performance/etw-events.md)
- [<span data-ttu-id="3270c-140">疑難排解：記錄檔接聽程式</span><span class="sxs-lookup"><span data-stu-id="3270c-140">Troubleshooting: Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)
