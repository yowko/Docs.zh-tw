---
title: 在 Visual Basic 中使用應用程式記錄檔
ms.date: 07/20/2015
helpviewer_keywords:
- logs, application
- application event logs, Visual Basic
- application event logs
ms.assetid: 2581afd1-5791-4bc4-86b2-46244e9fe468
ms.openlocfilehash: c11e1f0c99b3189c7a353e6778c701667b0a1d12
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "43000026"
---
# <a name="working-with-application-logs-in-visual-basic"></a><span data-ttu-id="e23d5-102">在 Visual Basic 中使用應用程式記錄檔</span><span class="sxs-lookup"><span data-stu-id="e23d5-102">Working with Application Logs in Visual Basic</span></span>
<span data-ttu-id="e23d5-103">`My.Applicaton.Log` 和 `My.Log` 物件讓您輕鬆地將記錄和追蹤資訊寫入記錄檔。</span><span class="sxs-lookup"><span data-stu-id="e23d5-103">The `My.Applicaton.Log` and `My.Log` objects make it easy to write logging and tracing information to logs.</span></span>  
  
## <a name="how-messages-are-logged"></a><span data-ttu-id="e23d5-104">記錄訊息的方式</span><span class="sxs-lookup"><span data-stu-id="e23d5-104">How Messages are Logged</span></span>  
 <span data-ttu-id="e23d5-105">首先，會以記錄檔之 <xref:System.Diagnostics.TraceSource.Switch%2A> 屬性中的 <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> 屬性檢查訊息的嚴重性。</span><span class="sxs-lookup"><span data-stu-id="e23d5-105">First, the severity of the message is checked with the <xref:System.Diagnostics.TraceSource.Switch%2A> property of the log's <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> property.</span></span> <span data-ttu-id="e23d5-106">根據預設，只有嚴重性為「資訊」和更高等級的訊息會傳遞至追蹤接聽項 (該追蹤接聽項於記錄檔的 `TraceListener` 集合中指定)。</span><span class="sxs-lookup"><span data-stu-id="e23d5-106">By default, only messages of severity "Information" and higher are passed on to the trace listeners, specified in the log's `TraceListener` collection.</span></span> <span data-ttu-id="e23d5-107">然後，每個接聽程式會將訊息嚴重性和接聽程式的 <xref:System.Diagnostics.TraceSource.Switch%2A> 屬性進行比較。</span><span class="sxs-lookup"><span data-stu-id="e23d5-107">Then, each listener compares the severity of the message to the listener's <xref:System.Diagnostics.TraceSource.Switch%2A> property.</span></span> <span data-ttu-id="e23d5-108">如果訊息的嚴重性夠高，接聽程式會寫出訊息。</span><span class="sxs-lookup"><span data-stu-id="e23d5-108">If the message's severity is high enough, the listener writes out the message.</span></span>  
  
 <span data-ttu-id="e23d5-109">下列圖表顯示寫入至 `WriteEntry` 方法的訊息如何傳遞至記錄檔追蹤接聽項的 `WriteLine` 方法︰</span><span class="sxs-lookup"><span data-stu-id="e23d5-109">The following diagram shows how a message written to the `WriteEntry` method gets passed to the `WriteLine` methods of the log's trace listeners:</span></span>  
  
 <span data-ttu-id="e23d5-110">![My 記錄檔呼叫](../../../../visual-basic/developing-apps/programming/log-info/media/mylogcall.png "MyLogCall")</span><span class="sxs-lookup"><span data-stu-id="e23d5-110">![My Log Call](../../../../visual-basic/developing-apps/programming/log-info/media/mylogcall.png "MyLogCall")</span></span>  
  
 <span data-ttu-id="e23d5-111">您可以藉由變更應用程式的組態檔來變更記錄檔和追蹤接聽項的行為。</span><span class="sxs-lookup"><span data-stu-id="e23d5-111">You can change the behavior of the log and the trace listeners by changing the application's configuration file.</span></span> <span data-ttu-id="e23d5-112">下列圖表顯示記錄檔組件和組態檔之間的通信。</span><span class="sxs-lookup"><span data-stu-id="e23d5-112">The following diagram shows the correspondence between the parts of the log and the configuration file.</span></span>  
  
 <span data-ttu-id="e23d5-113">![My 記錄檔組態](../../../../visual-basic/developing-apps/programming/log-info/media/mylogconfig.png "MyLogConfig")</span><span class="sxs-lookup"><span data-stu-id="e23d5-113">![My Log Configuration](../../../../visual-basic/developing-apps/programming/log-info/media/mylogconfig.png "MyLogConfig")</span></span>  
  
## <a name="where-messages-are-logged"></a><span data-ttu-id="e23d5-114">記錄訊息的位置</span><span class="sxs-lookup"><span data-stu-id="e23d5-114">Where Messages are Logged</span></span>  
 <span data-ttu-id="e23d5-115">如果組件沒有組態檔， `My.Application.Log` 和 `My.Log` 物件會寫入至應用程式的偵錯輸出 (透過 <xref:System.Diagnostics.DefaultTraceListener> 類別)。</span><span class="sxs-lookup"><span data-stu-id="e23d5-115">If the assembly has no configuration file, the `My.Application.Log` and `My.Log` objects write to the application's debug output (through the <xref:System.Diagnostics.DefaultTraceListener> class).</span></span> <span data-ttu-id="e23d5-116">此外，`My.Application.Log` 物件會寫入組件的記錄檔 (透過 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> 類別)，而 `My.Log` 物件會寫入 ASP.NET 網頁的輸出 (透過 <xref:System.Web.WebPageTraceListener> 類別)。</span><span class="sxs-lookup"><span data-stu-id="e23d5-116">In addition, the `My.Application.Log` object writes to the assembly's log file (through the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class), while the `My.Log` object writes to the ASP.NET Web page's output (through the <xref:System.Web.WebPageTraceListener> class).</span></span>  
  
 <span data-ttu-id="e23d5-117">以偵錯模式執行應用程式時，您可以在 Visual Studio [輸出] 視窗中檢視偵錯輸出。</span><span class="sxs-lookup"><span data-stu-id="e23d5-117">The debug output can be viewed in the Visual Studio **Output** window when running your application in debug mode.</span></span> <span data-ttu-id="e23d5-118">若要開啟 [輸出] 視窗，請按一下 [偵錯] 功能表項目並指向 [Windows] ，然後按一下 [輸出] 。</span><span class="sxs-lookup"><span data-stu-id="e23d5-118">To open the **Output** window, click the **Debug** menu item, point to **Windows**, and then click **Output**.</span></span> <span data-ttu-id="e23d5-119">在 [輸出]  視窗中，從 [顯示輸出來源]  方塊中選取 [偵錯]  。</span><span class="sxs-lookup"><span data-stu-id="e23d5-119">In the **Output** window, select **Debug** from the **Show output from** box.</span></span>  
  
 <span data-ttu-id="e23d5-120">根據預設， `My.Application.Log` 寫入至位於使用者應用程式資料路徑中的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="e23d5-120">By default, `My.Application.Log` writes the log file in the path for the user's application data.</span></span> <span data-ttu-id="e23d5-121">您可以從 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> 物件的 <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> 屬性取得路徑。</span><span class="sxs-lookup"><span data-stu-id="e23d5-121">You can get the path from the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> property of the <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> object.</span></span> <span data-ttu-id="e23d5-122">該路徑的格式如下所示︰</span><span class="sxs-lookup"><span data-stu-id="e23d5-122">The format of that path is as follows:</span></span>  
  
 `BasePath`\\`CompanyName`\\`ProductName`\\`ProductVersion`  
  
 <span data-ttu-id="e23d5-123">`BasePath` 的一般值如下所示。</span><span class="sxs-lookup"><span data-stu-id="e23d5-123">A typical value for `BasePath` is as follows.</span></span>  
  
 <span data-ttu-id="e23d5-124">C:\Documents and Settings\\`username`\Application Data</span><span class="sxs-lookup"><span data-stu-id="e23d5-124">C:\Documents and Settings\\`username`\Application Data</span></span>  
  
 <span data-ttu-id="e23d5-125">`CompanyName`、 `ProductName`和 `ProductVersion` 的值都來自應用程式的組件資訊。</span><span class="sxs-lookup"><span data-stu-id="e23d5-125">The values of `CompanyName`, `ProductName`, and `ProductVersion` come from the application's assembly information.</span></span> <span data-ttu-id="e23d5-126">記錄檔名稱的格式為 *AssemblyName*.log，其中 *AssemblyName* 為不含副檔名的組件檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="e23d5-126">The form of the log file name is *AssemblyName*.log, where *AssemblyName* is the file name of the assembly without the extension.</span></span> <span data-ttu-id="e23d5-127">若需要多個記錄檔 (像是當應用程式嘗試寫入至記錄檔而原始記錄檔無法使用時)，記錄檔名稱的格式為 *AssemblyName*-*iteration*.log，其中 `iteration` 為正 `Integer`。</span><span class="sxs-lookup"><span data-stu-id="e23d5-127">If more than one log file is needed, such as when the original log is unavailable when the application attempts to write to the log, the form for the log file name is *AssemblyName*-*iteration*.log, where `iteration` is a positive `Integer`.</span></span>  
  
 <span data-ttu-id="e23d5-128">您可以藉由加入或變更電腦和應用程式的組態檔以覆寫預設行為。</span><span class="sxs-lookup"><span data-stu-id="e23d5-128">You can override the default behavior by adding or changing the computer's and the application's configuration files.</span></span> <span data-ttu-id="e23d5-129">如需詳細資訊，請參閱 [Walkthrough: Changing Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)。</span><span class="sxs-lookup"><span data-stu-id="e23d5-129">For more information, see [Walkthrough: Changing Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md).</span></span>  
  
## <a name="configuring-log-settings"></a><span data-ttu-id="e23d5-130">設定記錄檔設定</span><span class="sxs-lookup"><span data-stu-id="e23d5-130">Configuring Log Settings</span></span>  
 <span data-ttu-id="e23d5-131">`Log` 物件具有不需應用程式組態檔 app.config 即可運作的預設實作。若要變更預設，您必須加入具有新設定的組態檔。</span><span class="sxs-lookup"><span data-stu-id="e23d5-131">The `Log` object has a default implementation that works without an application configuration file, app.config. To change the defaults, you must add a configuration file with the new settings.</span></span> <span data-ttu-id="e23d5-132">如需詳細資訊，請參閱 [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)。</span><span class="sxs-lookup"><span data-stu-id="e23d5-132">For more information, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>  
  
 <span data-ttu-id="e23d5-133">記錄檔組態區段位於 app.config 檔案主 `<system.diagnostics>` 節點的 `<configuration>` 節點中。</span><span class="sxs-lookup"><span data-stu-id="e23d5-133">The log configuration sections are located in the `<system.diagnostics>` node in the main `<configuration>` node of the app.config file.</span></span> <span data-ttu-id="e23d5-134">記錄檔資訊在數個節點內定義︰</span><span class="sxs-lookup"><span data-stu-id="e23d5-134">Log information is defined in several nodes:</span></span>  
  
-   <span data-ttu-id="e23d5-135">`Log` 物件的接聽程式在名為 DefaultSource 的 `<sources>` 節點中定義。</span><span class="sxs-lookup"><span data-stu-id="e23d5-135">The listeners for the `Log` object are defined in the `<sources>` node named DefaultSource.</span></span>  
  
-   <span data-ttu-id="e23d5-136">`Log` 物件的嚴重性篩選條件在名為 DefaultSwitch 的 `<switches>` 節點中定義。</span><span class="sxs-lookup"><span data-stu-id="e23d5-136">The severity filter for the `Log` object is defined in the `<switches>` node named DefaultSwitch.</span></span>  
  
-   <span data-ttu-id="e23d5-137">記錄檔接聽程式在 `<sharedListeners>` 節點中定義。</span><span class="sxs-lookup"><span data-stu-id="e23d5-137">The log listeners are defined in the `<sharedListeners>` node.</span></span>  
  
 <span data-ttu-id="e23d5-138">`<sources>`、 `<switches>`和 `<sharedListeners>` 節點的範例於下列程式碼內顯示︰</span><span class="sxs-lookup"><span data-stu-id="e23d5-138">Examples of `<sources>`, `<switches>`, and `<sharedListeners>` nodes are shown in the following code:</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="DefaultSource" switchName="DefaultSwitch">  
        <listeners>  
          <add name="FileLog"/>  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="DefaultSwitch" value="Information" />  
    </switches>  
    <sharedListeners>  
      <add name="FileLog"  
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,  
          Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,   
          PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL"  
        initializeData="FileLogWriter"  
      />  
    </sharedListeners>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="changing-log-settings-after-deployment"></a><span data-ttu-id="e23d5-139">在部署後變更記錄檔設定</span><span class="sxs-lookup"><span data-stu-id="e23d5-139">Changing Log Settings after Deployment</span></span>  
 <span data-ttu-id="e23d5-140">當您開發應用程式時，其組態設定儲存在 app.config 檔案中，如上述範例所示。</span><span class="sxs-lookup"><span data-stu-id="e23d5-140">When you develop an application, its configuration settings are stored in the app.config file, as shown in the examples above.</span></span> <span data-ttu-id="e23d5-141">部署應用程式之後，您仍然可以透過編輯組態檔來設定記錄檔。</span><span class="sxs-lookup"><span data-stu-id="e23d5-141">After you deploy your application, you can still configure the log by editing the configuration file.</span></span> <span data-ttu-id="e23d5-142">在以 Windows 為基礎的應用程式中，此檔案名稱為 *applicationName*.exe.config，而且必須位於與可執行檔相同的資料夾內。</span><span class="sxs-lookup"><span data-stu-id="e23d5-142">In a Windows-based application, this file's name is *applicationName*.exe.config, and it must reside in the same folder as the executable file.</span></span> <span data-ttu-id="e23d5-143">若為 Web 應用程式，這會是與專案關聯的 Web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="e23d5-143">For a Web application, this is the Web.config file associated with the project.</span></span>  
  
 <span data-ttu-id="e23d5-144">當應用程式第一次執行建立類別執行個體的程式碼時，會檢查組態檔是否具有物件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e23d5-144">When your application executes the code that creates an instance of a class for the first time, it checks the configuration file for information about the object.</span></span> <span data-ttu-id="e23d5-145">對 `Log` 物件來說，這發生在第一次存取 `Log` 物件時。</span><span class="sxs-lookup"><span data-stu-id="e23d5-145">For the `Log` object, this happens the first time the `Log` object is accessed.</span></span> <span data-ttu-id="e23d5-146">系統只會針對組態檔是否有任何特定物件進行單次檢查，也就是在應用程式第一次建立物件時。</span><span class="sxs-lookup"><span data-stu-id="e23d5-146">The system examines the configuration file only once for any particular object—the first time your application creates the object.</span></span> <span data-ttu-id="e23d5-147">因此，您可能需要重新啟動應用程式以使變更生效。</span><span class="sxs-lookup"><span data-stu-id="e23d5-147">Therefore, you may need to restart the application for the changes to take effect.</span></span>  
  
 <span data-ttu-id="e23d5-148">在部署的應用程式中，您可以在應用程式啟動前，藉由重新設定交換器物件來啟用追蹤程式碼。</span><span class="sxs-lookup"><span data-stu-id="e23d5-148">In a deployed application, you enable trace code by reconfiguring switch objects before your application starts.</span></span> <span data-ttu-id="e23d5-149">這通常涉及開啟和關閉交換器物件，或是變更追蹤層級，然後再重新啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="e23d5-149">Typically, this involves turning the switch objects on and off or by changing the tracing levels, and then restarting your application.</span></span>  
  
## <a name="security-considerations"></a><span data-ttu-id="e23d5-150">安全性考量</span><span class="sxs-lookup"><span data-stu-id="e23d5-150">Security Considerations</span></span>  
 <span data-ttu-id="e23d5-151">將資料寫入至記錄檔時，請考慮下列項目︰</span><span class="sxs-lookup"><span data-stu-id="e23d5-151">Consider the following when writing data to the log:</span></span>  
  
-   <span data-ttu-id="e23d5-152">**避免流失使用者資訊。**</span><span class="sxs-lookup"><span data-stu-id="e23d5-152">**Avoid leaking user information.**</span></span> <span data-ttu-id="e23d5-153">確保您的應用程式僅將核准的資訊寫入記錄檔。</span><span class="sxs-lookup"><span data-stu-id="e23d5-153">Ensure that your application writes only approved information to the log.</span></span> <span data-ttu-id="e23d5-154">例如，應用程式記錄檔或許可以包含使用者名稱，但不能包含使用者密碼。</span><span class="sxs-lookup"><span data-stu-id="e23d5-154">For example, it may be acceptable for the application log to contain user names, but not user passwords.</span></span>  
  
-   <span data-ttu-id="e23d5-155">**保護記錄檔位置的安全。**</span><span class="sxs-lookup"><span data-stu-id="e23d5-155">**Make log locations secure.**</span></span> <span data-ttu-id="e23d5-156">任何包含潛在機密資訊的記錄都應該儲存在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="e23d5-156">Any log that contains potentially sensitive information should be stored in a secure location.</span></span>  
  
-   <span data-ttu-id="e23d5-157">**避免可能造成誤導的資訊。**</span><span class="sxs-lookup"><span data-stu-id="e23d5-157">**Avoid misleading information.**</span></span> <span data-ttu-id="e23d5-158">一般情況下，您的應用程式應該先驗證所有使用者輸入的資料，然後才能使用該資料。</span><span class="sxs-lookup"><span data-stu-id="e23d5-158">In general, your application should validate all data entered by a user before using that data.</span></span> <span data-ttu-id="e23d5-159">這包括將資料寫入至應用程式記錄檔。</span><span class="sxs-lookup"><span data-stu-id="e23d5-159">This includes writing data to the application log.</span></span>  
  
-   <span data-ttu-id="e23d5-160">**避免拒絕服務的發生。**</span><span class="sxs-lookup"><span data-stu-id="e23d5-160">**Avoid denial of service.**</span></span> <span data-ttu-id="e23d5-161">如果您的應用程式將過多的資訊寫入記錄檔，它可能會填滿記錄檔或讓您難以尋找重要資訊。</span><span class="sxs-lookup"><span data-stu-id="e23d5-161">If your application writes too much information to the log, it could fill the log or make finding important information difficult.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e23d5-162">請參閱</span><span class="sxs-lookup"><span data-stu-id="e23d5-162">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 [<span data-ttu-id="e23d5-163">記錄來自應用程式的資訊</span><span class="sxs-lookup"><span data-stu-id="e23d5-163">Logging Information from the Application</span></span>](../../../../visual-basic/developing-apps/programming/log-info/index.md)
