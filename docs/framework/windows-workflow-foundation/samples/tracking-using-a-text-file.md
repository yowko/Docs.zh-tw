---
title: 使用文字檔追蹤
ms.date: 03/30/2017
ms.assetid: 56a82682-73c2-4b91-a206-4d8bb12c561b
ms.openlocfilehash: 19b4d544bc1d1c5bc9ebfa51b4ba28eb82c525d0
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "45969388"
---
# <a name="tracking-using-a-text-file"></a><span data-ttu-id="68c8d-102">使用文字檔追蹤</span><span class="sxs-lookup"><span data-stu-id="68c8d-102">Tracking Using a Text File</span></span>
<span data-ttu-id="68c8d-103">此範例示範如何建立自訂追蹤參與者來擴充追蹤在 Windows Workflow Foundation (WF)。</span><span class="sxs-lookup"><span data-stu-id="68c8d-103">This sample demonstrates how to extend tracking in Windows Workflow Foundation (WF) by creating a custom tracking participant.</span></span> <span data-ttu-id="68c8d-104">追蹤參與者是可接收執行階段所發出之追蹤記錄的 .NET Framework 類別。</span><span class="sxs-lookup"><span data-stu-id="68c8d-104">Tracking participants are .NET Framework classes that receive tracking records from the runtime as they are emitted.</span></span> <span data-ttu-id="68c8d-105">您可以建立追蹤參與者，將追蹤事件傳輸至特定狀況所需的任何目的地。</span><span class="sxs-lookup"><span data-stu-id="68c8d-105">You can create a tracking participant to transport the tracking events to whichever destination is required for your scenario.</span></span> <span data-ttu-id="68c8d-106">例如，ETW (Windows 事件追蹤) 追蹤參與者是在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 中提供的。</span><span class="sxs-lookup"><span data-stu-id="68c8d-106">For example, ETW (Event Tracing for Windows) Tracking Participant is provided as part of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="68c8d-107">這個範例中的追蹤參與者會將 XML 格式的記錄寫入至文字檔。</span><span class="sxs-lookup"><span data-stu-id="68c8d-107">The tracking participant in this sample writes the records in XML format to a text file.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="68c8d-108">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="68c8d-108">Sample details</span></span>  
 <span data-ttu-id="68c8d-109">若要最佳化追蹤參與者的實用性和強固性，必須完成一些額外步驟，將追蹤參與者適當連接至執行階段。</span><span class="sxs-lookup"><span data-stu-id="68c8d-109">To optimize the usefulness and robustness of your tracking participant, some additional steps must be completed to properly wire the tracking participant to the runtime.</span></span> <span data-ttu-id="68c8d-110">下表描述這個範例中建立以最佳作法編譯之追蹤參與者所用的類別。</span><span class="sxs-lookup"><span data-stu-id="68c8d-110">The following table describes the classes used in this sample to create a tracking participant that complies with best practices.</span></span>  
  
|<span data-ttu-id="68c8d-111">類別</span><span class="sxs-lookup"><span data-stu-id="68c8d-111">Class</span></span>|<span data-ttu-id="68c8d-112">描述</span><span class="sxs-lookup"><span data-stu-id="68c8d-112">Description</span></span>|  
|-----------|-----------------|  
|`TextFileTrackingExtensionElement`|<span data-ttu-id="68c8d-113"><xref:System.ServiceModel.Configuration.BehaviorExtensionElement> 是用來定義用於設定文字檔追蹤參與者的組態區段。</span><span class="sxs-lookup"><span data-stu-id="68c8d-113">A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> is used to define the configuration section used to configure the text file tracking participant.</span></span> <span data-ttu-id="68c8d-114">這可讓使用者使用標準 .NET Framework 組態檔來指定記錄檔的目的地。</span><span class="sxs-lookup"><span data-stu-id="68c8d-114">This allows users to specify the destination of the log file using standard .NET Framework configuration files.</span></span>|  
|`TextFileTrackingBehavior`|<span data-ttu-id="68c8d-115">WCF 中的行為可讓使用者將延伸模組插入執行階段。</span><span class="sxs-lookup"><span data-stu-id="68c8d-115">Behaviors in WCF allow users to inject extensions into the runtime.</span></span> <span data-ttu-id="68c8d-116">當服務啟動時，此行為會將追蹤參與者加入至服務。</span><span class="sxs-lookup"><span data-stu-id="68c8d-116">This behavior adds the tracking participant to the service when the service starts.</span></span>|  
|`TextFileTrackingParticipant`|<span data-ttu-id="68c8d-117">在執行階段，接收追蹤記錄並將其以 XML 格式儲存至記錄檔的追蹤參與者。</span><span class="sxs-lookup"><span data-stu-id="68c8d-117">The tracking participant that receives tracking participants at runtime and stores them to a log file as XML.</span></span>|  
  
## <a name="behavior-extension-elements-configuration"></a><span data-ttu-id="68c8d-118">行為延伸項目組態</span><span class="sxs-lookup"><span data-stu-id="68c8d-118">Behavior Extension Elements Configuration</span></span>  
 <span data-ttu-id="68c8d-119">必須完成另一個步驟，才能透過 .NET Framework 組態檔來利用先前描述的行為延伸項目。</span><span class="sxs-lookup"><span data-stu-id="68c8d-119">One more step is required to make use of the behavior extension element previously described using .NET Framework configuration files.</span></span> <span data-ttu-id="68c8d-120">下列組態必須放置在要使用此延伸模組的組態檔中。</span><span class="sxs-lookup"><span data-stu-id="68c8d-120">The following configuration must be placed in configuration files where the extension is to be used.</span></span>  
  
```xml  
<system.serviceModel>  
    <extensions>  
      <behaviorExtensions>  
        <add name="textFileTracking" type="Microsoft.Samples.TextFileTracking.TextFileTrackingExtensionElement, WFStockPriceApplication, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </behaviorExtensions>  
    </extensions>  
…  
  </system.serviceModel>  
```  
  
> [!NOTE]
>  <span data-ttu-id="68c8d-121">如需行為延伸項目組態的完整範例使用方式，請參閱範例中的 Web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="68c8d-121">See the Web.config file in the sample for a complete example usage of behavior extension elements configuration.</span></span>  
  
## <a name="custom-tracking-records"></a><span data-ttu-id="68c8d-122">自訂追蹤記錄</span><span class="sxs-lookup"><span data-stu-id="68c8d-122">Custom Tracking Records</span></span>  
 <span data-ttu-id="68c8d-123">GetStockPrices.cs 檔案示範如何從 <xref:System.Activities.CodeActivity> 中建立自訂追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="68c8d-123">The GetStockPrices.cs file demonstrates how to create custom tracking records from within a <xref:System.Activities.CodeActivity>.</span></span> <span data-ttu-id="68c8d-124">在執行範例時請尋找此記錄。</span><span class="sxs-lookup"><span data-stu-id="68c8d-124">Look for this record when running the sample.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="68c8d-125">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="68c8d-125">To use this sample</span></span>  
  
1.  <span data-ttu-id="68c8d-126">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 WFStockPriceApplication.sln 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="68c8d-126">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the WFStockPriceApplication.sln solution file.</span></span>  
  
2.  <span data-ttu-id="68c8d-127">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="68c8d-127">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="68c8d-128">若要執行此方案，請按下 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="68c8d-128">To run the solution, press CTRL+F5.</span></span>  
  
     <span data-ttu-id="68c8d-129">瀏覽器視窗隨即開啟並顯示應用程式的目錄清單。</span><span class="sxs-lookup"><span data-stu-id="68c8d-129">The browser window opens and shows the directory listing for the application.</span></span>  
  
4.  <span data-ttu-id="68c8d-130">在瀏覽器中，按一下 StockPriceService.xamlx。</span><span class="sxs-lookup"><span data-stu-id="68c8d-130">In the browser, click StockPriceService.xamlx.</span></span>  
  
5.  <span data-ttu-id="68c8d-131">瀏覽器會顯示**StockPriceService**頁面，其中包含本機服務 wsdl 位址。</span><span class="sxs-lookup"><span data-stu-id="68c8d-131">The browser displays the **StockPriceService** page, which contains the local service wsdl address.</span></span> <span data-ttu-id="68c8d-132">複製此位址。</span><span class="sxs-lookup"><span data-stu-id="68c8d-132">Copy this address.</span></span>  
  
     <span data-ttu-id="68c8d-133">本機服務 wsdl 位址的範例是 http://localhost:53797/StockPriceService.xamlx?wsdl 。</span><span class="sxs-lookup"><span data-stu-id="68c8d-133">An example of the local service wsdl address is http://localhost:53797/StockPriceService.xamlx?wsdl.</span></span>  
  
6.  <span data-ttu-id="68c8d-134">使用 [[!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)]] 移至 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 資料夾 (預設安裝資料夾為 %SystemDrive%\Program Files\Microsoft Visual Studio 10.0)。</span><span class="sxs-lookup"><span data-stu-id="68c8d-134">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], go to your [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] folder (the default installation folder is %SystemDrive%\Program Files\Microsoft Visual Studio 10.0).</span></span> <span data-ttu-id="68c8d-135">然後尋找 Common7\IDE\ 子資料夾。</span><span class="sxs-lookup"><span data-stu-id="68c8d-135">Then locate the Common7\IDE\ subfolder.</span></span>  
  
7.  <span data-ttu-id="68c8d-136">按兩下 WcfTestClient.exe 檔案以啟動 WCF 測試用戶端。</span><span class="sxs-lookup"><span data-stu-id="68c8d-136">Double-click the WcfTestClient.exe file to launch the WCF Test Client.</span></span>  
  
8.  <span data-ttu-id="68c8d-137">在 WCF 測試用戶端中，選取 **新增服務...**</span><span class="sxs-lookup"><span data-stu-id="68c8d-137">In the WCF Test Client, select **Add Service…**</span></span> <span data-ttu-id="68c8d-138">從**檔案**功能表。</span><span class="sxs-lookup"><span data-stu-id="68c8d-138">from the **File** menu.</span></span>  
  
9. <span data-ttu-id="68c8d-139">將剛才複製的 URL 貼到文字方塊中。</span><span class="sxs-lookup"><span data-stu-id="68c8d-139">Paste the URL you just copied into the text box.</span></span>  
  
10. <span data-ttu-id="68c8d-140">按一下 **確定**以關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="68c8d-140">Click **OK** to close the dialog.</span></span>  
  
11. <span data-ttu-id="68c8d-141">使用 WCF 測試用戶端測試此服務。</span><span class="sxs-lookup"><span data-stu-id="68c8d-141">Test the service using the WCF Test Client.</span></span>  
  
    1.  <span data-ttu-id="68c8d-142">在 WCF 測試用戶端中，按兩下**Istockpriceservice**下方**getstockprice （)** 節點。</span><span class="sxs-lookup"><span data-stu-id="68c8d-142">In the WCF Test Client, double-click **GetStockPrice()** under the **IStockPriceService** node.</span></span>  
  
         <span data-ttu-id="68c8d-143">**Istockpriceservice**方法會出現在右窗格中，具有一個參數。</span><span class="sxs-lookup"><span data-stu-id="68c8d-143">The **GetStockPrice()** method appears in the right pane, with one parameter.</span></span>  
  
    2.  <span data-ttu-id="68c8d-144">輸入 Contoso 做為參數值。</span><span class="sxs-lookup"><span data-stu-id="68c8d-144">Type in Contoso as the value for the parameter.</span></span>  
  
    3.  <span data-ttu-id="68c8d-145">按一下 **叫用**。</span><span class="sxs-lookup"><span data-stu-id="68c8d-145">Click **Invoke**.</span></span>  
  
12. <span data-ttu-id="68c8d-146">查看位於應用程式目錄之記錄檔 (即 %APPDATA%\trackingRecords.log) 的追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="68c8d-146">See the tracked events in the log file located in your application data directory at %APPDATA%\trackingRecords.log.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="68c8d-147">%APPDATA%是環境變數，可解析成 %SystemDrive%\Users\\< 使用者名稱\>中的 \AppData\Roaming [!INCLUDE[wv](../../../../includes/wv-md.md)]， [!INCLUDE[lserver](../../../../includes/lserver-md.md)]，或 Windows Server 2008。</span><span class="sxs-lookup"><span data-stu-id="68c8d-147">The %APPDATA% is an environment variable that resolves to %SystemDrive%\Users\\<username\>\AppData\Roaming in [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], or Windows Server 2008.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="68c8d-148">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="68c8d-148">The samples may already be installed on your computer.</span></span> <span data-ttu-id="68c8d-149">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="68c8d-149">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="68c8d-150">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="68c8d-150">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="68c8d-151">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="68c8d-151">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\TextFileTracking`  
  
## <a name="see-also"></a><span data-ttu-id="68c8d-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68c8d-152">See Also</span></span>  
 [<span data-ttu-id="68c8d-153">AppFabric 監控範例</span><span class="sxs-lookup"><span data-stu-id="68c8d-153">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
