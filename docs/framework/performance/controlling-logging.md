---
title: "控制 .NET Framework 記錄"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: CLR ETW events, logging
ms.assetid: ce13088e-3095-4f0e-9f6b-fad30bbd3d41
caps.latest.revision: "40"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 90de9dd6bd32eb2142dceb98c142f3c50a0a5691
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="controlling-net-framework-logging"></a><span data-ttu-id="04543-102">控制 .NET Framework 記錄</span><span class="sxs-lookup"><span data-stu-id="04543-102">Controlling .NET Framework Logging</span></span>
<span data-ttu-id="04543-103">您可以使用 Windows 事件追蹤 (ETW) 來記錄通用語言執行平台 (CLR) 事件。</span><span class="sxs-lookup"><span data-stu-id="04543-103">You can use event tracing for Windows (ETW) to record common language runtime (CLR) events.</span></span> <span data-ttu-id="04543-104">您可以使用下列工具來建立和檢視追蹤：</span><span class="sxs-lookup"><span data-stu-id="04543-104">You can create and view traces by using the following tools:</span></span>  
  
-   <span data-ttu-id="04543-105">[Logman](http://go.microsoft.com/fwlink/?LinkId=150916) 和 [Tracerpt](http://go.microsoft.com/fwlink/?LinkId=150919) 命令列工具，隨附於 Windows 作業系統。</span><span class="sxs-lookup"><span data-stu-id="04543-105">The [Logman](http://go.microsoft.com/fwlink/?LinkId=150916) and [Tracerpt](http://go.microsoft.com/fwlink/?LinkId=150919) command-line tools, which are included with the Windows operating system.</span></span>  
  
-   <span data-ttu-id="04543-106">[Windows 效能工具組](http://msdn.microsoft.com/library/windows/hardware/hh162945.aspx)中的 [Xperf](http://msdn.microsoft.com/library/windows/hardware/hh162920.aspx) 工具。</span><span class="sxs-lookup"><span data-stu-id="04543-106">The [Xperf](http://msdn.microsoft.com/library/windows/hardware/hh162920.aspx) tools in the [Windows Performance Toolkit](http://msdn.microsoft.com/library/windows/hardware/hh162945.aspx).</span></span> <span data-ttu-id="04543-107">如需 Xperf 的詳細資訊，請參閱 [Windows 效能部落格](http://go.microsoft.com/fwlink/?LinkId=179509)。</span><span class="sxs-lookup"><span data-stu-id="04543-107">For more information about Xperf, see the [Windows Performance blog](http://go.microsoft.com/fwlink/?LinkId=179509).</span></span>  
  
 <span data-ttu-id="04543-108">若要擷取 CLR 事件資訊，您必須在電腦上安裝 CLR 提供者。</span><span class="sxs-lookup"><span data-stu-id="04543-108">To capture CLR event information, the CLR provider must be installed on your computer.</span></span> <span data-ttu-id="04543-109">若要確認是否已安裝此提供者，請在命令提示字元中輸入 `logman query providers`。</span><span class="sxs-lookup"><span data-stu-id="04543-109">To confirm that the provider is installed, type `logman query providers` at the command prompt.</span></span> <span data-ttu-id="04543-110">提供者的清單隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="04543-110">A list of providers is displayed.</span></span> <span data-ttu-id="04543-111">此清單應該會包含 CLR 提供者的項目，如下所示。</span><span class="sxs-lookup"><span data-stu-id="04543-111">This list should contain an entry for the CLR provider, as follows.</span></span>  
  
```  
Provider                                 GUID  
-------------------------------------------------------------------------------  
.NET Common Language Runtime    {E13C0D23-CCBC-4E12-931B-D9CC2EEE27E4}.  
```  
  
 <span data-ttu-id="04543-112">如果未列出 CLR 提供者，您可以使用 Windows [Wevtutil](http://go.microsoft.com/fwlink/?LinkID=150915) 命令列工具，在 Windows Vista 和更新版本的作業系統上安裝此提供者。</span><span class="sxs-lookup"><span data-stu-id="04543-112">If the CLR provider is not listed, you can install it on Windows Vista and later operating systems by using the Windows [Wevtutil](http://go.microsoft.com/fwlink/?LinkID=150915) command-line tool.</span></span> <span data-ttu-id="04543-113">以系統管理員身分開啟 [命令提示字元] 視窗。</span><span class="sxs-lookup"><span data-stu-id="04543-113">Open the Command Prompt window as an administrator.</span></span> <span data-ttu-id="04543-114">將提示目錄變更為 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 資料夾 (%WINDIR%\Microsoft.NET\Framework[64]\v4.\<.NET 版本>\)。</span><span class="sxs-lookup"><span data-stu-id="04543-114">Change the prompt directory to the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] folder (%WINDIR%\Microsoft.NET\Framework[64]\v4.\<.NET version>\ ).</span></span> <span data-ttu-id="04543-115">這個資料夾包含 CLR-ETW.man 檔案。</span><span class="sxs-lookup"><span data-stu-id="04543-115">This folder contains the CLR-ETW.man file.</span></span> <span data-ttu-id="04543-116">在命令提示字元中，輸入下列命令，即可安裝 CLR 提供者：</span><span class="sxs-lookup"><span data-stu-id="04543-116">At the command prompt, type the following command to install the CLR provider:</span></span>  
  
 `wevtutil im CLR-ETW.man`  
  
## <a name="capturing-clr-etw-events"></a><span data-ttu-id="04543-117">擷取 CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="04543-117">Capturing CLR ETW Events</span></span>  
 <span data-ttu-id="04543-118">您可以使用 [Logman](http://go.microsoft.com/fwlink/?LinkId=150916) 和 [Xperf](http://msdn.microsoft.com/library/windows/hardware/hh162920.aspx) 命令列工具擷取 ETW 事件，以及使用 [Tracerpt](http://go.microsoft.com/fwlink/?LinkId=150919) 和 [Xperf](http://msdn.microsoft.com/library/windows/hardware/hh162920.aspx) 工具解碼追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="04543-118">You can use the [Logman](http://go.microsoft.com/fwlink/?LinkId=150916) and [Xperf](http://msdn.microsoft.com/library/windows/hardware/hh162920.aspx) command-line tools to capture ETW events, and the [Tracerpt](http://go.microsoft.com/fwlink/?LinkId=150919) and [Xperf](http://msdn.microsoft.com/library/windows/hardware/hh162920.aspx) tools to decode the trace events.</span></span>  
  
 <span data-ttu-id="04543-119">若要開啟記錄，使用者必須指定三個項目：</span><span class="sxs-lookup"><span data-stu-id="04543-119">To turn on logging, a user must specify three things:</span></span>  
  
-   <span data-ttu-id="04543-120">要與之通訊的提供者。</span><span class="sxs-lookup"><span data-stu-id="04543-120">The provider to communicate to.</span></span>  
  
-   <span data-ttu-id="04543-121">表示一組關鍵字的 64 位元數字。</span><span class="sxs-lookup"><span data-stu-id="04543-121">A 64-bit number that represents a set of keywords.</span></span> <span data-ttu-id="04543-122">每個關鍵字各表示一組提供者可以開啟的事件。</span><span class="sxs-lookup"><span data-stu-id="04543-122">Each keyword represents a set of events that the provider can turn on.</span></span> <span data-ttu-id="04543-123">數字綜合表示一組要開啟的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="04543-123">The number represents a combined set of keywords to turn on.</span></span>  
  
-   <span data-ttu-id="04543-124">很小的數字，表示要記錄的 (詳細) 層級。</span><span class="sxs-lookup"><span data-stu-id="04543-124">A small number representing the level (verbosity) to log at.</span></span> <span data-ttu-id="04543-125">層級 1 最不詳細，而層級 5 則是最詳細。</span><span class="sxs-lookup"><span data-stu-id="04543-125">Level 1 is the least verbose, and level 5 is the most verbose.</span></span> <span data-ttu-id="04543-126">層級 0 為預設值，意思是提供者特有的事件。</span><span class="sxs-lookup"><span data-stu-id="04543-126">Level 0 is a default whose meaning is provider-specific.</span></span>  
  
#### <a name="to-capture-clr-etw-events-using-logman"></a><span data-ttu-id="04543-127">若要使用 Logman 來擷取 CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="04543-127">To capture CLR ETW events using Logman</span></span>  
  
1.  <span data-ttu-id="04543-128">在命令提示中，輸入：</span><span class="sxs-lookup"><span data-stu-id="04543-128">At the command prompt, type:</span></span>  
  
     `logman start clrevents -p {e13c0d23-ccbc-4e12-931b-d9cc2eee27e4} 0x1CCBD 0x5 -ets -ct perf`  
  
     <span data-ttu-id="04543-129">其中：</span><span class="sxs-lookup"><span data-stu-id="04543-129">where:</span></span>  
  
    -   <span data-ttu-id="04543-130">`-p` 參數會識別提供者 GUID。</span><span class="sxs-lookup"><span data-stu-id="04543-130">The `-p` parameter identifies the provider GUID.</span></span>  
  
    -   <span data-ttu-id="04543-131">`0x1CCBD` 會指定即將引發之事件的分類。</span><span class="sxs-lookup"><span data-stu-id="04543-131">`0x1CCBD` specifies the categories of events that will be raised.</span></span>  
  
    -   <span data-ttu-id="04543-132">`0x5` 會設定記錄的層級 (在本例中，設為詳細資訊 (5))。</span><span class="sxs-lookup"><span data-stu-id="04543-132">`0x5` sets the level of logging (in this case, verbose (5)).</span></span>  
  
    -   <span data-ttu-id="04543-133">`-ets` 參數會指示 Logman 傳送命令給事件追蹤工作階段。</span><span class="sxs-lookup"><span data-stu-id="04543-133">The `-ets` parameter instructs Logman to send commands to event tracing sessions.</span></span>  
  
    -   <span data-ttu-id="04543-134">`-ct perf` 參數會指定要使用 `QueryPerformanceCounter` 函式來記錄每個事件的時間戳記。</span><span class="sxs-lookup"><span data-stu-id="04543-134">The `-ct perf` parameter specifies that the `QueryPerformanceCounter` function will be used to log the time stamp for each event.</span></span>  
  
2.  <span data-ttu-id="04543-135">若要停止記錄事件，請輸入：</span><span class="sxs-lookup"><span data-stu-id="04543-135">To stop logging the events, type:</span></span>  
  
     `logman stop clrevents -ets`  
  
     <span data-ttu-id="04543-136">這個命令會建立名為 clrevents.etl 的二進位追蹤檔。</span><span class="sxs-lookup"><span data-stu-id="04543-136">This command creates a binary trace file named clrevents.etl.</span></span>  
  
#### <a name="to-capture-clr-etw-events-using-xperf"></a><span data-ttu-id="04543-137">若要使用 Xperf 來擷取 CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="04543-137">To capture CLR ETW events using Xperf</span></span>  
  
1.  <span data-ttu-id="04543-138">在命令提示中，輸入：</span><span class="sxs-lookup"><span data-stu-id="04543-138">At the command prompt, type:</span></span>  
  
     `xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:5 -f clrevents.etl`  
  
     <span data-ttu-id="04543-139">其中，GUID 是 CLR ETW 提供者 GUID，而且 `0x1CCBD:5` 會追蹤層級 5 (詳細資訊) 以下的每個事件。</span><span class="sxs-lookup"><span data-stu-id="04543-139">where the GUID is the CLR ETW provider GUID, and `0x1CCBD:5` traces everything at and below level 5 (verbose).</span></span>  
  
2.  <span data-ttu-id="04543-140">若要停止追蹤，請輸入：</span><span class="sxs-lookup"><span data-stu-id="04543-140">To stop tracing, type:</span></span>  
  
     `Xperf -stop clr`  
  
     <span data-ttu-id="04543-141">這個命令會建立名為 clrevents.etl 的追蹤檔。</span><span class="sxs-lookup"><span data-stu-id="04543-141">This command creates a trace file named clrevents.etl.</span></span>  
  
## <a name="viewing-clr-etw-events"></a><span data-ttu-id="04543-142">檢視 CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="04543-142">Viewing CLR ETW Events</span></span>  
 <span data-ttu-id="04543-143">您可以使用下列命令來檢視 CLR ETW 事件。</span><span class="sxs-lookup"><span data-stu-id="04543-143">Use the commands listed below to view the CLR ETW events.</span></span> <span data-ttu-id="04543-144">如需這些事件的描述，請參閱 [CLR ETW 事件](../../../docs/framework/performance/clr-etw-events.md)。</span><span class="sxs-lookup"><span data-stu-id="04543-144">For a description of the events, see [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md).</span></span>  
  
#### <a name="to-view-clr-etw-events-using-tracerpt"></a><span data-ttu-id="04543-145">若要使用 Tracerpt 來檢視 CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="04543-145">To view CLR ETW events using Tracerpt</span></span>  
  
-   <span data-ttu-id="04543-146">在命令提示中，輸入：</span><span class="sxs-lookup"><span data-stu-id="04543-146">At the command prompt, type:</span></span>  
  
     `tracerpt clrevents.etl`  
  
     <span data-ttu-id="04543-147">這個命令會建立兩個檔案：dumpfile.xml 和 summary.txt。</span><span class="sxs-lookup"><span data-stu-id="04543-147">This command creates two files: dumpfile.xml and summary.txt.</span></span> <span data-ttu-id="04543-148">dumpfile.xml 檔案會列出所有事件，而 summary.txt 會提供這些事件的摘要。</span><span class="sxs-lookup"><span data-stu-id="04543-148">The dumpfile.xml file lists all the events, and summary.txt provides a summary of the events.</span></span>  
  
#### <a name="to-view-clr-etw-events-using-xperf"></a><span data-ttu-id="04543-149">若要使用 Xperf 來檢視 CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="04543-149">To view CLR ETW events using Xperf</span></span>  
  
-   <span data-ttu-id="04543-150">在命令提示中，輸入：</span><span class="sxs-lookup"><span data-stu-id="04543-150">At the command prompt, type:</span></span>  
  
     `xperf clrevents.etl`  
  
     <span data-ttu-id="04543-151">這個命令會開啟 Xperf ETL 檔案檢視器。</span><span class="sxs-lookup"><span data-stu-id="04543-151">This command opens the Xperf ETL file viewer.</span></span> <span data-ttu-id="04543-152">在這個檢視器中，CLR 事件會顯示在 [一般事件] 檢視中。</span><span class="sxs-lookup"><span data-stu-id="04543-152">In this viewer, the CLR events show up in the **Generic Events** view.</span></span> <span data-ttu-id="04543-153">若要顯示依類型分類的事件資料格，請在這個檢視中選取一個時間區域，並按一下滑鼠右鍵，然後選取 [摘要]。</span><span class="sxs-lookup"><span data-stu-id="04543-153">To display a data grid of events categorized by type, select a region of time in this view, and then right-click and select **Summary**.</span></span>  
  
#### <a name="to-convert-the-etl-file-to-a-comma-separated-value-file"></a><span data-ttu-id="04543-154">若要將 .etl 檔案轉換為逗點分隔值檔案</span><span class="sxs-lookup"><span data-stu-id="04543-154">To convert the .etl file to a comma-separated value file</span></span>  
  
-   <span data-ttu-id="04543-155">在命令提示中，輸入：</span><span class="sxs-lookup"><span data-stu-id="04543-155">At the command prompt, type:</span></span>  
  
     `xperf -i clrevents.etl -f clrevents.csv`  
  
     <span data-ttu-id="04543-156">這個命令會讓 XPerf 以您可以檢視的逗點分隔值 (CSV) 檔案的形式傾印事件。</span><span class="sxs-lookup"><span data-stu-id="04543-156">This command causes XPerf to dump the events as a comma separated value (CSV) file that you can view.</span></span> <span data-ttu-id="04543-157">因為不同的事件有不同的欄位，所以這個 CSV 檔案中的資料前面會有多行標頭。</span><span class="sxs-lookup"><span data-stu-id="04543-157">Because different events have different fields, this CSV file is contains more than one header line before the data.</span></span> <span data-ttu-id="04543-158">每行的第一個欄位都是事件類型，表示應使用哪一行的標頭來判斷其餘的欄位。</span><span class="sxs-lookup"><span data-stu-id="04543-158">The first field of every line is the event type, which indicates which header should be used to determine the rest of the fields.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04543-159">請參閱</span><span class="sxs-lookup"><span data-stu-id="04543-159">See Also</span></span>  
 [<span data-ttu-id="04543-160">Windows 效能工具組</span><span class="sxs-lookup"><span data-stu-id="04543-160">Windows Performance Toolkit</span></span>](http://go.microsoft.com/fwlink/?LinkID=161141)  
 [<span data-ttu-id="04543-161">Common Language Runtime 中的 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="04543-161">ETW Events in the Common Language Runtime</span></span>](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
