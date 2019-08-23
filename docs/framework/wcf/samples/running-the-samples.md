---
title: 執行 Windows Communication Foundation 範例
ms.date: 03/30/2017
ms.assetid: db8a83da-95c1-4a21-a9d2-48caeb6398ea
ms.openlocfilehash: df984f2464084948cdaa51dab96554de9400911f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965503"
---
# <a name="running-the-windows-communication-foundation-samples"></a><span data-ttu-id="0e577-102">執行 Windows Communication Foundation 範例</span><span class="sxs-lookup"><span data-stu-id="0e577-102">Running the Windows Communication Foundation Samples</span></span>
<span data-ttu-id="0e577-103">Windows Communication Foundation (WCF) 範例可以在單一電腦或跨電腦設定中執行。</span><span class="sxs-lookup"><span data-stu-id="0e577-103">The Windows Communication Foundation (WCF) samples can be run in a single-machine or cross-machine configuration.</span></span> <span data-ttu-id="0e577-104">這些範例可依提供現狀直接執行於單一機器上。</span><span class="sxs-lookup"><span data-stu-id="0e577-104">As supplied, the samples are ready for running on a single machine.</span></span> <span data-ttu-id="0e577-105">在跨機器組態中，就需要修改範例的組態檔設定。</span><span class="sxs-lookup"><span data-stu-id="0e577-105">In a cross-machine configuration, it is necessary to modify a sample's configuration file settings.</span></span> <span data-ttu-id="0e577-106">下列程序會說明如何在相同機器與跨機器組態中執行此範例。</span><span class="sxs-lookup"><span data-stu-id="0e577-106">The following procedures explain how to run a sample in same-machine and cross-machine configurations.</span></span> <span data-ttu-id="0e577-107">請注意，透過網際網路資訊服務 (IIS) 裝載與自我裝載範例中的服務步驟會有所變化。</span><span class="sxs-lookup"><span data-stu-id="0e577-107">Note that there are variations in the steps for services hosted in Internet Information Services (IIS) and the self-hosted samples.</span></span> <span data-ttu-id="0e577-108">大部分的範例都是以 IIS 進行裝載；請參閱範例讀我資訊以決定其裝載方式。</span><span class="sxs-lookup"><span data-stu-id="0e577-108">Most samples are hosted in IIS; see the sample readme information to determine how it is hosted.</span></span>  
  
 <span data-ttu-id="0e577-109">在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 上，不是裝載在 IIS 中的範例需要更高的權限向 Http.sys 註冊接聽項。</span><span class="sxs-lookup"><span data-stu-id="0e577-109">On [!INCLUDE[wv](../../../../includes/wv-md.md)], samples that are not hosted in IIS require elevated privileges to register a listener with Http.sys.</span></span> <span data-ttu-id="0e577-110">請使用 Httpcfg.exe 以在其中執行服務的帳戶來註冊服務的接聽位址，或從使用系統管理員權限執行的命令提示字元來啟用服務。</span><span class="sxs-lookup"><span data-stu-id="0e577-110">Use Httpcfg.exe to register the service's listening addresses with the account the service is running under, or launch the service from a command prompt running with administrator privileges.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0e577-111">建立或執行任何 WCF 範例之前, 請確定您已[針對 Windows Communication Foundation 範例執行一次設定程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="0e577-111">Before building or running any of the WCF samples, be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="0e577-112">若要在同一部機器上執行範例</span><span class="sxs-lookup"><span data-stu-id="0e577-112">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="0e577-113">如果服務是由 IIS 裝載, 請確定您可以使用瀏覽器來存取服務, 方法是輸入下列位址: `http://localhost/servicemodelsamples/service.svc`。</span><span class="sxs-lookup"><span data-stu-id="0e577-113">If the service is hosted by IIS, ensure that you can access the service using a browser by entering the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="0e577-114">確認頁面應該會顯示在回應中。</span><span class="sxs-lookup"><span data-stu-id="0e577-114">A confirmation page should be displayed in response.</span></span> <span data-ttu-id="0e577-115">如果未顯示 [確認] 頁面, 請參閱[WCF 範例的疑難排解秘訣](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="0e577-115">If the confirmation page is not displayed, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
2. <span data-ttu-id="0e577-116">如果服務是自我裝載，請從語言特定資料夾中的 \service\bin 執行 Service.exe。</span><span class="sxs-lookup"><span data-stu-id="0e577-116">If the service is self-hosted, run Service.exe from \service\bin, from under the language-specific folder.</span></span> <span data-ttu-id="0e577-117">服務活動會顯示在服務主控台視窗上。</span><span class="sxs-lookup"><span data-stu-id="0e577-117">Service activity is displayed on the service console window.</span></span>  
  
3. <span data-ttu-id="0e577-118">從語言特定資料夾下的\\\client\bin 執行 Client .exe。</span><span class="sxs-lookup"><span data-stu-id="0e577-118">Run Client.exe from \client\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="0e577-119">用戶端活動會顯示在用戶端主控台視窗上。</span><span class="sxs-lookup"><span data-stu-id="0e577-119">Client activity is displayed on the client console window.</span></span>  
  
4. <span data-ttu-id="0e577-120">如果用戶端和服務無法通訊, 請參閱[WCF 範例的疑難排解秘訣](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="0e577-120">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="0e577-121">若要跨機器執行範例</span><span class="sxs-lookup"><span data-stu-id="0e577-121">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="0e577-122">如果服務是以 IIS 裝載：</span><span class="sxs-lookup"><span data-stu-id="0e577-122">If the service is hosted in IIS:</span></span>  
  
    1. <span data-ttu-id="0e577-123">在服務機器上，建立一個名稱為 ServiceModelSamples 的虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="0e577-123">On the service machine, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="0e577-124">[Windows Communication Foundation 範例的單次安裝程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)隨附的批次檔 setupvroot.bat, 可以用來建立磁碟目錄和虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="0e577-124">The batch file Setupvroot.bat included with [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) can be used to create the disk directory and virtual directory.</span></span>  
  
    2. <span data-ttu-id="0e577-125">將服務程式檔案從 %SystemDrive%\Inetpub\wwwroot\servicemodelsamples 複製到服務機器上的 ServiceModelSamples 虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="0e577-125">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service machine.</span></span> <span data-ttu-id="0e577-126">確定您有將這些檔案包含至 \bin 目錄中。</span><span class="sxs-lookup"><span data-stu-id="0e577-126">Ensure that you include the files in the \bin directory.</span></span>  
  
    3. <span data-ttu-id="0e577-127">測試您是否能夠使用瀏覽器，從用戶端機器存取服務。</span><span class="sxs-lookup"><span data-stu-id="0e577-127">Test that you can access the service from the client machine using a browser.</span></span>  
  
     <span data-ttu-id="0e577-128">如果服務是自我裝載：</span><span class="sxs-lookup"><span data-stu-id="0e577-128">If the service is self-hosted:</span></span>  
  
    1. <span data-ttu-id="0e577-129">在服務機器上，建立可儲存這些服務檔案的目錄。</span><span class="sxs-lookup"><span data-stu-id="0e577-129">On the service machine, create a directory to hold the service files.</span></span>  
  
    2. <span data-ttu-id="0e577-130">將語言特定資料夾下 \service\bin\ 資料夾中的服務程式檔複製到服務機器中。</span><span class="sxs-lookup"><span data-stu-id="0e577-130">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service machine.</span></span>  
  
    3. <span data-ttu-id="0e577-131">在服務組態檔案中，將端點定義的位址值變更成符合服務的新位址。</span><span class="sxs-lookup"><span data-stu-id="0e577-131">In the service configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="0e577-132">以位址中的完整網域名稱取代 "localhost" 的任何參考。</span><span class="sxs-lookup"><span data-stu-id="0e577-132">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
    4. <span data-ttu-id="0e577-133">從命令提示字元啟動 Service.exe。</span><span class="sxs-lookup"><span data-stu-id="0e577-133">Launch Service.exe from a command prompt.</span></span>  
  
2. <span data-ttu-id="0e577-134">將語言特定資料夾下 \client\bin\ 資料夾中的用戶端程式檔案複製到用戶端機器中。</span><span class="sxs-lookup"><span data-stu-id="0e577-134">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machine.</span></span>  
  
3. <span data-ttu-id="0e577-135">設定端點位址。</span><span class="sxs-lookup"><span data-stu-id="0e577-135">Set the endpoint address.</span></span>  
  
    1. <span data-ttu-id="0e577-136">如果服務不是使用網域帳戶執行，請開啟用戶端組態檔，並將端點定義的位址值變更成符合服務的新位址。</span><span class="sxs-lookup"><span data-stu-id="0e577-136">If the service is not running under a domain account, open the client configuration file and change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="0e577-137">以位址中的完整網域名稱取代 "localhost" 的任何參考。</span><span class="sxs-lookup"><span data-stu-id="0e577-137">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
    2. <span data-ttu-id="0e577-138">如果服務是使用網域帳戶執行，請針對服務執行 Svcutil.exe 以重新產生用戶端組態。</span><span class="sxs-lookup"><span data-stu-id="0e577-138">If the service is running under a domain account, regenerate the client configuration by running Svcutil.exe against the service.</span></span> <span data-ttu-id="0e577-139">如需執行 Svcutil 的詳細資訊, 請參閱[建立 Windows Communication Foundation 的範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="0e577-139">For more information about running Svcutil.exe, see [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span> <span data-ttu-id="0e577-140">使用產生的檔案，而不要使用範例中的組態檔。</span><span class="sxs-lookup"><span data-stu-id="0e577-140">Use the generated file instead of the configuration file in the sample.</span></span> <span data-ttu-id="0e577-141">產生的組態檔還有其他身分識別資訊，而且包含連接至服務端點需要的所有設定 (即使是預設的設定)。</span><span class="sxs-lookup"><span data-stu-id="0e577-141">The generated configuration file has additional identity information, and contains all settings necessary to connect to the service endpoint even though they are the default settings.</span></span> <span data-ttu-id="0e577-142">如需身分識別資訊的詳細資訊, 請參閱[服務身分識別和驗證](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)和[ \<身分識別 >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)。</span><span class="sxs-lookup"><span data-stu-id="0e577-142">For more information about identity information, see [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md), and [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md).</span></span>  
  
4. <span data-ttu-id="0e577-143">在用戶端機器上，從命令提示字元啟動 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="0e577-143">On the client machine, launch Client.exe from a command prompt.</span></span>  
  
### <a name="to-debug-a-service"></a><span data-ttu-id="0e577-144">偵錯服務</span><span class="sxs-lookup"><span data-stu-id="0e577-144">To debug a service</span></span>  
  
1. <span data-ttu-id="0e577-145">使用 [**建立**] 功能表或 CTRL + SHIFT + B 來建立解決方案 (用戶端和服務)。</span><span class="sxs-lookup"><span data-stu-id="0e577-145">Build the solution (both client and service) using the **Build** menu or CTRL+SHIFT+B.</span></span>  
  
2. <span data-ttu-id="0e577-146">如果服務是以 IIS 裝載：</span><span class="sxs-lookup"><span data-stu-id="0e577-146">If the service is hosted in IIS:</span></span>  
  
    1. <span data-ttu-id="0e577-147">藉由輸入位址`http://localhost/servicemodelsamples/service.svc`, 使用瀏覽器來啟動服務。</span><span class="sxs-lookup"><span data-stu-id="0e577-147">Activate the service using a browser by entering the address `http://localhost/servicemodelsamples/service.svc`.</span></span>  
  
    2. <span data-ttu-id="0e577-148">在解決方案中, 選擇 [**調試**程式] 功能表和 [**附加至進程**] 功能表項目。</span><span class="sxs-lookup"><span data-stu-id="0e577-148">In the solution, choose the **Debug** menu and the **Attach to Process** menu item.</span></span>  
  
    3. <span data-ttu-id="0e577-149">選取 [顯示所有使用者的處理序] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="0e577-149">Select the **Show processes from all users** check box.</span></span>  
  
    4. <span data-ttu-id="0e577-150">選取主機背景工作處理序 W3wp.exe 來進行偵錯 (在 Windows XP 中選取 ASPNet_wp.exe)。</span><span class="sxs-lookup"><span data-stu-id="0e577-150">Select the host worker process W3wp.exe to debug (select ASPNet_wp.exe on Windows XP).</span></span>  
  
3. <span data-ttu-id="0e577-151">您現在可以在服務程式碼中設定中斷點，然後啟用發生例外狀況時的中斷點。</span><span class="sxs-lookup"><span data-stu-id="0e577-151">You can now set breakpoints in the service code and enable breakpoints on exceptions.</span></span>  
  
4. <span data-ttu-id="0e577-152">以滑鼠右鍵按一下用戶端專案專案, 然後選擇 [ **Debug**]、[**開始新實例**]。</span><span class="sxs-lookup"><span data-stu-id="0e577-152">Right-click the client project item and choose **Debug**, **Start new instance**.</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="0e577-153">若要在使用範例之後進行清除</span><span class="sxs-lookup"><span data-stu-id="0e577-153">To clean up after the sample</span></span>  
  
- <span data-ttu-id="0e577-154">如果因為考量安全性而以 IIS 裝載服務，則請在完成範例時，移除虛擬目錄定義以及在安裝步驟中所授與的權限。</span><span class="sxs-lookup"><span data-stu-id="0e577-154">If the service is hosted in IIS for security purposes, remove the virtual directory definition and permissions granted in the setup steps when you are finished with the samples.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e577-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e577-155">See also</span></span>

- [<span data-ttu-id="0e577-156">建置 Windows Communication Foundation 範例</span><span class="sxs-lookup"><span data-stu-id="0e577-156">Building the Windows Communication Foundation Samples</span></span>](../../../../docs/framework/wcf/samples/building-the-samples.md)
- <span data-ttu-id="0e577-157">[WCF 範例的疑難排解秘訣](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="0e577-157">[Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))</span></span>
