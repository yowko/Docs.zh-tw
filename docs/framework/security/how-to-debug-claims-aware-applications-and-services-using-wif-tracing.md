---
title: "操作說明：使用 WIF 追蹤對宣告感知應用程式和服務進行偵錯"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d51ba59-3adb-4ca4-bd33-5027531af687
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 36cb961345cb724597d8e48ec3be6cbb84df4632
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-debug-claims-aware-applications-and-services-using-wif-tracing"></a><span data-ttu-id="42192-102">操作說明：使用 WIF 追蹤對宣告感知應用程式和服務進行偵錯</span><span class="sxs-lookup"><span data-stu-id="42192-102">How To: Debug Claims-Aware Applications And Services Using WIF Tracing</span></span>
## <a name="applies-to"></a><span data-ttu-id="42192-103">適用於</span><span class="sxs-lookup"><span data-stu-id="42192-103">Applies To</span></span>  
  
-   <span data-ttu-id="42192-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="42192-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="42192-105">服務追蹤檢視器工具 (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="42192-105">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>  
  
-   <span data-ttu-id="42192-106">疑難排解和偵錯 WIF 應用程式</span><span class="sxs-lookup"><span data-stu-id="42192-106">Troubleshooting and Debugging WIF Applications</span></span>  
  
## <a name="summary"></a><span data-ttu-id="42192-107">摘要</span><span class="sxs-lookup"><span data-stu-id="42192-107">Summary</span></span>  
 <span data-ttu-id="42192-108">本使用說明針對如何設定 WIF 追蹤、收集追蹤記錄檔，以及如何使用追蹤檢視器工具來分析追蹤記錄檔，說明所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="42192-108">This How-To describes required steps for how to configure WIF tracing, collect trace logs, and how to analyze the trace logs using Trace Viewer tool.</span></span> <span data-ttu-id="42192-109">其針對 WIF 相關問題的疑難排解，提供所需之追蹤項目對動作的一般對應。</span><span class="sxs-lookup"><span data-stu-id="42192-109">It provides general mapping for trace entries to actions needed to troubleshoot issues related to WIF.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="42192-110">內容</span><span class="sxs-lookup"><span data-stu-id="42192-110">Contents</span></span>  
  
-   <span data-ttu-id="42192-111">目標</span><span class="sxs-lookup"><span data-stu-id="42192-111">Objectives</span></span>  
  
-   <span data-ttu-id="42192-112">步驟摘要</span><span class="sxs-lookup"><span data-stu-id="42192-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="42192-113">步驟 1 – 使用 Web.config 組態檔來設定 WIF 追蹤</span><span class="sxs-lookup"><span data-stu-id="42192-113">Step 1 – Configure WIF Tracing Using Web.config Configuration File</span></span>  
  
-   <span data-ttu-id="42192-114">步驟 2 – 使用追蹤檢視器工具來分析 WIF 追蹤檔案</span><span class="sxs-lookup"><span data-stu-id="42192-114">Step 2 – Analyze WIF Trace Files Using Trace Viewer Tool</span></span>  
  
-   <span data-ttu-id="42192-115">步驟 3 – 識別用來修正 WIF 相關問題的方案</span><span class="sxs-lookup"><span data-stu-id="42192-115">Step 3 – Identify Solutions to Fix WIF Related Issues</span></span>  
  
-   <span data-ttu-id="42192-116">相關項目</span><span class="sxs-lookup"><span data-stu-id="42192-116">Related Items</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="42192-117">目標</span><span class="sxs-lookup"><span data-stu-id="42192-117">Objectives</span></span>  
  
-   <span data-ttu-id="42192-118">設定 WIF 追蹤。</span><span class="sxs-lookup"><span data-stu-id="42192-118">Configure WIF tracing.</span></span>  
  
-   <span data-ttu-id="42192-119">在追蹤檢視器工具中檢視追蹤記錄檔。</span><span class="sxs-lookup"><span data-stu-id="42192-119">View trace logs in the Trace Viewer tool.</span></span>  
  
-   <span data-ttu-id="42192-120">在追蹤記錄檔中識別 WIF 的相關問題。</span><span class="sxs-lookup"><span data-stu-id="42192-120">Identify WIF related issues in the trace logs.</span></span>  
  
-   <span data-ttu-id="42192-121">將更正動作套用到在追蹤記錄中發現的 WIF 相關問題。</span><span class="sxs-lookup"><span data-stu-id="42192-121">Apply corrective actions to WIF related issues found in the trace logs.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="42192-122">步驟摘要</span><span class="sxs-lookup"><span data-stu-id="42192-122">Summary of Steps</span></span>  
  
-   <span data-ttu-id="42192-123">步驟 1 – 使用 Web.config 組態檔來設定 WIF 追蹤</span><span class="sxs-lookup"><span data-stu-id="42192-123">Step 1 – Configure WIF Tracing Using Web.config Configuration File</span></span>  
  
-   <span data-ttu-id="42192-124">步驟 2 – 使用追蹤檢視器工具來分析 WIF 追蹤檔案</span><span class="sxs-lookup"><span data-stu-id="42192-124">Step 2 – Analyze WIF Trace Files Using Trace Viewer Tool</span></span>  
  
-   <span data-ttu-id="42192-125">步驟 3 – 識別用來修正 WIF 相關問題的方案</span><span class="sxs-lookup"><span data-stu-id="42192-125">Step 3 – Identify Solutions to Fix WIF Related Issues</span></span>  
  
## <a name="step-1--configure-wif-tracing-using-webconfig-configuration-file"></a><span data-ttu-id="42192-126">步驟 1 – 使用 Web.config 組態檔來設定 WIF 追蹤</span><span class="sxs-lookup"><span data-stu-id="42192-126">Step 1 – Configure WIF Tracing Using Web.config Configuration File</span></span>  
 <span data-ttu-id="42192-127">在此步驟中，您要將變更新增至 *Web.config* 檔案中的組態區段，讓 WIF 能夠追蹤它的事件，並將其儲存在追蹤記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="42192-127">In this step, you will add changes to configuration sections in the *Web.config* file that enable WIF to trace its events and store them in a trace log.</span></span>  
  
#### <a name="to-configure-wif-tracing-using-webconfig-configuration-file"></a><span data-ttu-id="42192-128">使用 Web.config 組態檔來設定 WIF 追蹤</span><span class="sxs-lookup"><span data-stu-id="42192-128">To configure WIF tracing using Web.config configuration file</span></span>  
  
1.  <span data-ttu-id="42192-129">在方案總管中按兩下根 **Web.config** 或 **App.config** 組態檔，以在 Visual Studio 編輯器中將其開啟。</span><span class="sxs-lookup"><span data-stu-id="42192-129">Open the root **Web.config** or **App.config** configuration file in the Visual Studio editor by double clicking on it in **Solution Explorer**.</span></span> <span data-ttu-id="42192-130">如果您的方案沒有 **Web.config** 或 **App.config** 組態檔，請在方案總管 中，以滑鼠右鍵按一下該方案，並按一下 [新增]，然後按一下 [新增項目...]，以新增檔案。</span><span class="sxs-lookup"><span data-stu-id="42192-130">If your solution does not have **Web.config** or **App.config** configuration file, add it by right clicking on the solution in the **Solution Explorer** and clicking **Add**, then clicking **New Item…**.</span></span> <span data-ttu-id="42192-131">在 [新增項目] 對話方塊中，從清單選取 [應用程式組態檔] (若要使用 **App.config**) 或 [Web 組態檔] (若要使用 **Web.config**)，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="42192-131">On the **New Item** dialog, Select **Application Configuration File** for **App.config** or **Web Configuration File** for **Web.config** from the list and click **OK**.</span></span>  
  
2.  <span data-ttu-id="42192-132">將類似下列的組態項目新增至組態檔，位於組態檔結尾的 **\<configuration>** 節點中：</span><span class="sxs-lookup"><span data-stu-id="42192-132">Add the configuration entries similar to the following to the configuration file inside **\<configuration>** node at the end of the configuration file:</span></span>  
  
    ```xml  
    <system.diagnostics>  
        <sources>  
            <source name="System.IdentityModel" switchValue="Verbose">  
                <listeners>  
                    <add name="xml" type="System.Diagnostics.XmlWriterTraceListener" initializeData="WIFTrace.e2e"/>  
                </listeners>  
            </source>  
        </sources>  
        <trace autoflush="true"/>  
    </system.diagnostics>  
    ```  
  
3.  <span data-ttu-id="42192-133">上述組態會指示 WIF 產生詳細追蹤事件，並將其記錄在 *WIFTrace.e2e* 檔案中。</span><span class="sxs-lookup"><span data-stu-id="42192-133">The above configuration instructs WIF to generate verbose trace events and log them into *WIFTrace.e2e* file.</span></span> <span data-ttu-id="42192-134">如需 **switchValue** 變數值的完整清單，請參閱下列主題中的「追蹤層級」表格：[設定追蹤](http://msdn.microsoft.com/library/ms733025.aspx)。</span><span class="sxs-lookup"><span data-stu-id="42192-134">For a complete list of values for the **switchValue** switch, refer to the Trace Level table found in the following topic: [Configuring Tracing](http://msdn.microsoft.com/library/ms733025.aspx).</span></span>  
  
## <a name="step-2--analyze-wif-trace-files-using-trace-viewer-tool"></a><span data-ttu-id="42192-135">步驟 2 – 使用追蹤檢視器工具來分析 WIF 追蹤檔案</span><span class="sxs-lookup"><span data-stu-id="42192-135">Step 2 – Analyze WIF Trace Files Using Trace Viewer Tool</span></span>  
 <span data-ttu-id="42192-136">在此步驟中，您要使用追蹤檢視器工具 (SvcTraceViewer.exe) 來分析 WIF 追蹤記錄檔。</span><span class="sxs-lookup"><span data-stu-id="42192-136">In this step, you will use the Trace Viewer Tool (SvcTraceViewer.exe) to analyze WIF trace logs.</span></span>  
  
#### <a name="to-analyze-wif-trace-logs-using-trace-viewer-tool-svctraceviewerexe"></a><span data-ttu-id="42192-137">使用追蹤檢視器工具 (SvcTraceViewer.exe) 來分析 WIF 追蹤記錄檔</span><span class="sxs-lookup"><span data-stu-id="42192-137">To analyze WIF trace logs using Trace Viewer tool (SvcTraceViewer.exe)</span></span>  
  
1.  <span data-ttu-id="42192-138">追蹤檢視器工具 (SvcTraceViewer.exe) 隨附於 Windows SDK。</span><span class="sxs-lookup"><span data-stu-id="42192-138">Trace Viewer tool (SvcTraceViewer.exe) ships as part of the Windows SDK.</span></span> <span data-ttu-id="42192-139">如果您還沒有安裝 Windows SDK，可以在這裡下載：[Windows SDK](http://www.microsoft.com/download/en/details.aspx?id=8279)。</span><span class="sxs-lookup"><span data-stu-id="42192-139">If you haven’t already installed the Windows SDK, you can download it here: [Windows SDK](http://www.microsoft.com/download/en/details.aspx?id=8279).</span></span>  
  
2.  <span data-ttu-id="42192-140">執行追蹤檢視器工具 (SvcTraceViewer.exe)。</span><span class="sxs-lookup"><span data-stu-id="42192-140">Run the Trace Viewer tool (SvcTraceViewer.exe).</span></span> <span data-ttu-id="42192-141">它通常會在安裝路徑的 **Bin** 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="42192-141">It is typically available in the **Bin** folder of the installation path.</span></span>  
  
3.  <span data-ttu-id="42192-142">開啟 WIF 追蹤記錄檔，例如，藉由選取 WIFTrace.e2e**檔案**，**開啟...**</span><span class="sxs-lookup"><span data-stu-id="42192-142">Open the WIF trace log file, for example, WIFTrace.e2e by selecting **File**, **Open…**</span></span> <span data-ttu-id="42192-143">在功能表選項，或使用**Ctrl + O**捷徑。</span><span class="sxs-lookup"><span data-stu-id="42192-143">option in the menu or using the **Ctrl+O** shortcut.</span></span> <span data-ttu-id="42192-144">追蹤記錄檔會在追蹤檢視器工具中開啟。</span><span class="sxs-lookup"><span data-stu-id="42192-144">The trace log file opens in the Trace Viewer tool.</span></span>  
  
4.  <span data-ttu-id="42192-145">檢閱 [活動] 索引標籤中的項目。每個項目都應該會包含活動號碼、所記錄的追蹤數目、活動的持續時間，以及其開始和結束時間戳記。</span><span class="sxs-lookup"><span data-stu-id="42192-145">Review entries in the **Activity** tab. Each entry should contain an activity number, the number of traces that were logged, duration of the activity and its start and end timestamps.</span></span>  
  
5.  <span data-ttu-id="42192-146">按一下 [活動] 索引標籤。您應該會在此工具的主要區域中，看到詳細的追蹤項目。</span><span class="sxs-lookup"><span data-stu-id="42192-146">Click on the **Activity** tab. You should see detailed trace entries in the main area of the tool.</span></span> <span data-ttu-id="42192-147">使用功能表上的 [層級] 下拉式清單，來篩選特定層級的追蹤，例如：[全部]、[警告]、[錯誤]、[資訊] 等等。</span><span class="sxs-lookup"><span data-stu-id="42192-147">Use the **Level** dropdown list on the menu to filter specific level of traces, for example: **All**, **Warning**, **Errors**, **Information**, etc.</span></span>  
  
6.  <span data-ttu-id="42192-148">按一下特定追蹤項目，以檢閱工具下方區域中的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="42192-148">Click on specific trace entries to review the details in the lower area of the tool.</span></span> <span data-ttu-id="42192-149">您可以選擇對應的索引標籤，使用 [格式化] 和 [XML] 來檢視詳細資料。</span><span class="sxs-lookup"><span data-stu-id="42192-149">The details can be viewed using **Formatted** and **XML** view by choosing corresponding tabs.</span></span>  
  
## <a name="step-3--identify-solutions-to-fix-wif-related-issues"></a><span data-ttu-id="42192-150">步驟 3 – 識別用來修正 WIF 相關問題的方案</span><span class="sxs-lookup"><span data-stu-id="42192-150">Step 3 – Identify Solutions to Fix WIF Related Issues</span></span>  
 <span data-ttu-id="42192-151">在此步驟中，您可以針對使用 WIF 追蹤記錄檔和追蹤檢視器工具來識別的 WIF 相關問題，找出方案。</span><span class="sxs-lookup"><span data-stu-id="42192-151">In this step, you can identify solutions for WIF-related issues identified by using the WIF trace log and Trace Viewer tool.</span></span> <span data-ttu-id="42192-152">本文將針對 WIF 相關例外狀況與可能的方案或疑難排解此問題所需的動作，提供一般對應。</span><span class="sxs-lookup"><span data-stu-id="42192-152">It outlines general mapping of WIF related exceptions to potential solutions or required actions to troubleshoot the issue.</span></span>  
  
#### <a name="to-identify-solutions-to-fix-wif-related-issues"></a><span data-ttu-id="42192-153">識別用來修正 WIF 相關問題的方案</span><span class="sxs-lookup"><span data-stu-id="42192-153">To identify solutions to fix WIF related issues</span></span>  
  
1.  <span data-ttu-id="42192-154">檢閱下面 WIF 例外狀況與更正問題所需動作的表格。</span><span class="sxs-lookup"><span data-stu-id="42192-154">Review the following table of WIF exceptions and the required actions to correct the issues.</span></span>  
  
|<span data-ttu-id="42192-155">**錯誤識別碼**</span><span class="sxs-lookup"><span data-stu-id="42192-155">**Error ID**</span></span>|<span data-ttu-id="42192-156">**錯誤訊息**</span><span class="sxs-lookup"><span data-stu-id="42192-156">**Error Message**</span></span>|<span data-ttu-id="42192-157">**修正錯誤所需的動作**</span><span class="sxs-lookup"><span data-stu-id="42192-157">**Action needed to fix the error**</span></span>|  
|-|-|-|  
|<span data-ttu-id="42192-158">ID4175</span><span class="sxs-lookup"><span data-stu-id="42192-158">ID4175</span></span>|<span data-ttu-id="42192-159">IssuerNameRegistry 無法辨識安全性權杖的簽發者。</span><span class="sxs-lookup"><span data-stu-id="42192-159">The issuer of the security token was not recognized by the IssuerNameRegistry.</span></span>  <span data-ttu-id="42192-160">若要接受來自這個簽發者的安全性權杖，請設定 IssuerNameRegistry，以傳回此簽發者的有效名稱。</span><span class="sxs-lookup"><span data-stu-id="42192-160">To accept security tokens from this issuer, configure the IssuerNameRegistry to return a valid name for this issuer.</span></span>|<span data-ttu-id="42192-161">造成此錯誤的原因，可能是您從 MMC 嵌入式管理單元複製指紋，並將其貼到 *Web.config* 檔案中。</span><span class="sxs-lookup"><span data-stu-id="42192-161">This error can be caused by copying a thumbprint from the MMC snap-in and pasting it into the *Web.config* file.</span></span> <span data-ttu-id="42192-162">具體而言，您可以在從憑證屬性視窗複製時，在文字字串中取得額外的不可列印字元。</span><span class="sxs-lookup"><span data-stu-id="42192-162">Specifically, you can get an extra non-printable character in the text string when copying from the certificate properties window.</span></span> <span data-ttu-id="42192-163">這個額外的字元導致指紋比對失敗。您可以在這裡找到正確複製指紋的程序：[http://msdn.microsoft.com/library/ff359102.aspx](http://msdn.microsoft.com/library/ff359102.aspx)</span><span class="sxs-lookup"><span data-stu-id="42192-163">This extra character causes the thumbprint match to fail.The procedure for correctly copying the thumbprint can be found here: [http://msdn.microsoft.com/library/ff359102.aspx](http://msdn.microsoft.com/library/ff359102.aspx)</span></span>|  
  
## <a name="related-items"></a><span data-ttu-id="42192-164">相關項目</span><span class="sxs-lookup"><span data-stu-id="42192-164">Related Items</span></span>  
  
-   [<span data-ttu-id="42192-165">使用服務追蹤檢視器檢視相關追蹤並進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="42192-165">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](http://msdn.microsoft.com/library/aa751795.aspx)
