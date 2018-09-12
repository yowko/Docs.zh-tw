---
title: 執行 Windows Communication Foundation 範例
ms.date: 03/30/2017
ms.assetid: db8a83da-95c1-4a21-a9d2-48caeb6398ea
ms.openlocfilehash: d6fc93af217bfc282ce7030973be32baf7d864cd
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2018
ms.locfileid: "44510151"
---
# <a name="running-the-windows-communication-foundation-samples"></a><span data-ttu-id="fe2da-102">執行 Windows Communication Foundation 範例</span><span class="sxs-lookup"><span data-stu-id="fe2da-102">Running the Windows Communication Foundation Samples</span></span>
<span data-ttu-id="fe2da-103">可以在單一電腦或跨電腦組態中執行的 Windows Communication Foundation (WCF) 範例。</span><span class="sxs-lookup"><span data-stu-id="fe2da-103">The Windows Communication Foundation (WCF) samples can be run in a single-machine or cross-machine configuration.</span></span> <span data-ttu-id="fe2da-104">這些範例可依提供現狀直接執行於單一機器上。</span><span class="sxs-lookup"><span data-stu-id="fe2da-104">As supplied, the samples are ready for running on a single machine.</span></span> <span data-ttu-id="fe2da-105">在跨機器組態中，就需要修改範例的組態檔設定。</span><span class="sxs-lookup"><span data-stu-id="fe2da-105">In a cross-machine configuration, it is necessary to modify a sample's configuration file settings.</span></span> <span data-ttu-id="fe2da-106">下列程序會說明如何在相同機器與跨機器組態中執行此範例。</span><span class="sxs-lookup"><span data-stu-id="fe2da-106">The following procedures explain how to run a sample in same-machine and cross-machine configurations.</span></span> <span data-ttu-id="fe2da-107">請注意，透過網際網路資訊服務 (IIS) 裝載與自我裝載範例中的服務步驟會有所變化。</span><span class="sxs-lookup"><span data-stu-id="fe2da-107">Note that there are variations in the steps for services hosted in Internet Information Services (IIS) and the self-hosted samples.</span></span> <span data-ttu-id="fe2da-108">大部分的範例都是以 IIS 進行裝載；請參閱範例讀我資訊以決定其裝載方式。</span><span class="sxs-lookup"><span data-stu-id="fe2da-108">Most samples are hosted in IIS; see the sample readme information to determine how it is hosted.</span></span>  
  
 <span data-ttu-id="fe2da-109">在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 上，不是裝載在 IIS 中的範例需要更高的權限向 Http.sys 註冊接聽項。</span><span class="sxs-lookup"><span data-stu-id="fe2da-109">On [!INCLUDE[wv](../../../../includes/wv-md.md)], samples that are not hosted in IIS require elevated privileges to register a listener with Http.sys.</span></span> <span data-ttu-id="fe2da-110">請使用 Httpcfg.exe 以在其中執行服務的帳戶來註冊服務的接聽位址，或從使用系統管理員權限執行的命令提示字元來啟用服務。</span><span class="sxs-lookup"><span data-stu-id="fe2da-110">Use Httpcfg.exe to register the service's listening addresses with the account the service is running under, or launch the service from a command prompt running with administrator privileges.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fe2da-111">建置或之前執行任何 WCF 範例，請務必在您執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="fe2da-111">Before building or running any of the WCF samples, be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="fe2da-112">若要在同一部機器上執行範例</span><span class="sxs-lookup"><span data-stu-id="fe2da-112">To run the sample on the same machine</span></span>  
  
1.  <span data-ttu-id="fe2da-113">如果服務由 IIS 裝載，請確定您可以使用瀏覽器中輸入下列位址的服務： http://localhost/servicemodelsamples/service.svc。</span><span class="sxs-lookup"><span data-stu-id="fe2da-113">If the service is hosted by IIS, ensure that you can access the service using a browser by entering the following address: http://localhost/servicemodelsamples/service.svc.</span></span> <span data-ttu-id="fe2da-114">確認頁面應該會顯示在回應中。</span><span class="sxs-lookup"><span data-stu-id="fe2da-114">A confirmation page should be displayed in response.</span></span> <span data-ttu-id="fe2da-115">如果未顯示 [確認] 頁面，請參閱[疑難排解祕訣](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)。</span><span class="sxs-lookup"><span data-stu-id="fe2da-115">If the confirmation page is not displayed, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
2.  <span data-ttu-id="fe2da-116">如果服務是自我裝載，請從語言特定資料夾中的 \service\bin 執行 Service.exe。</span><span class="sxs-lookup"><span data-stu-id="fe2da-116">If the service is self-hosted, run Service.exe from \service\bin, from under the language-specific folder.</span></span> <span data-ttu-id="fe2da-117">服務活動會顯示在服務主控台視窗上。</span><span class="sxs-lookup"><span data-stu-id="fe2da-117">Service activity is displayed on the service console window.</span></span>  
  
3.  <span data-ttu-id="fe2da-118">從 \client\bin 執行 Client.exe\\，從語言特定資料夾之下。</span><span class="sxs-lookup"><span data-stu-id="fe2da-118">Run Client.exe from \client\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="fe2da-119">用戶端活動會顯示在用戶端主控台視窗上。</span><span class="sxs-lookup"><span data-stu-id="fe2da-119">Client activity is displayed on the client console window.</span></span>  
  
4.  <span data-ttu-id="fe2da-120">如果用戶端和服務能夠進行通訊，請參閱[疑難排解祕訣](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)。</span><span class="sxs-lookup"><span data-stu-id="fe2da-120">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="fe2da-121">若要跨機器執行範例</span><span class="sxs-lookup"><span data-stu-id="fe2da-121">To run the sample across machines</span></span>  
  
1.  <span data-ttu-id="fe2da-122">如果服務是以 IIS 裝載：</span><span class="sxs-lookup"><span data-stu-id="fe2da-122">If the service is hosted in IIS:</span></span>  
  
    1.  <span data-ttu-id="fe2da-123">在服務機器上，建立一個名稱為 ServiceModelSamples 的虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="fe2da-123">On the service machine, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="fe2da-124">批次檔 Setupvroot.bat 隨附[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)可用來建立磁碟目錄與虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="fe2da-124">The batch file Setupvroot.bat included with [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) can be used to create the disk directory and virtual directory.</span></span>  
  
    2.  <span data-ttu-id="fe2da-125">將服務程式檔案從 %SystemDrive%\Inetpub\wwwroot\servicemodelsamples 複製到服務機器上的 ServiceModelSamples 虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="fe2da-125">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service machine.</span></span> <span data-ttu-id="fe2da-126">確定您有將這些檔案包含至 \bin 目錄中。</span><span class="sxs-lookup"><span data-stu-id="fe2da-126">Ensure that you include the files in the \bin directory.</span></span>  
  
    3.  <span data-ttu-id="fe2da-127">測試您是否能夠使用瀏覽器，從用戶端機器存取服務。</span><span class="sxs-lookup"><span data-stu-id="fe2da-127">Test that you can access the service from the client machine using a browser.</span></span>  
  
     <span data-ttu-id="fe2da-128">如果服務是自我裝載：</span><span class="sxs-lookup"><span data-stu-id="fe2da-128">If the service is self-hosted:</span></span>  
  
    1.  <span data-ttu-id="fe2da-129">在服務機器上，建立可儲存這些服務檔案的目錄。</span><span class="sxs-lookup"><span data-stu-id="fe2da-129">On the service machine, create a directory to hold the service files.</span></span>  
  
    2.  <span data-ttu-id="fe2da-130">將語言特定資料夾下 \service\bin\ 資料夾中的服務程式檔複製到服務機器中。</span><span class="sxs-lookup"><span data-stu-id="fe2da-130">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service machine.</span></span>  
  
    3.  <span data-ttu-id="fe2da-131">在服務組態檔案中，將端點定義的位址值變更成符合服務的新位址。</span><span class="sxs-lookup"><span data-stu-id="fe2da-131">In the service configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="fe2da-132">以位址中的完整網域名稱取代 "localhost" 的任何參考。</span><span class="sxs-lookup"><span data-stu-id="fe2da-132">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
    4.  <span data-ttu-id="fe2da-133">從命令提示字元啟動 Service.exe。</span><span class="sxs-lookup"><span data-stu-id="fe2da-133">Launch Service.exe from a command prompt.</span></span>  
  
2.  <span data-ttu-id="fe2da-134">將語言特定資料夾下 \client\bin\ 資料夾中的用戶端程式檔案複製到用戶端機器中。</span><span class="sxs-lookup"><span data-stu-id="fe2da-134">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machine.</span></span>  
  
3.  <span data-ttu-id="fe2da-135">設定端點位址。</span><span class="sxs-lookup"><span data-stu-id="fe2da-135">Set the endpoint address.</span></span>  
  
    1.  <span data-ttu-id="fe2da-136">如果服務不是使用網域帳戶執行，請開啟用戶端組態檔，並將端點定義的位址值變更成符合服務的新位址。</span><span class="sxs-lookup"><span data-stu-id="fe2da-136">If the service is not running under a domain account, open the client configuration file and change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="fe2da-137">以位址中的完整網域名稱取代 "localhost" 的任何參考。</span><span class="sxs-lookup"><span data-stu-id="fe2da-137">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
    2.  <span data-ttu-id="fe2da-138">如果服務是使用網域帳戶執行，請針對服務執行 Svcutil.exe 以重新產生用戶端組態。</span><span class="sxs-lookup"><span data-stu-id="fe2da-138">If the service is running under a domain account, regenerate the client configuration by running Svcutil.exe against the service.</span></span> <span data-ttu-id="fe2da-139">如需執行 Svcutil.exe 的詳細資訊，請參閱 <<c0> [ 建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="fe2da-139">For more information about running Svcutil.exe, see [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span> <span data-ttu-id="fe2da-140">使用產生的檔案，而不要使用範例中的組態檔。</span><span class="sxs-lookup"><span data-stu-id="fe2da-140">Use the generated file instead of the configuration file in the sample.</span></span> <span data-ttu-id="fe2da-141">產生的組態檔還有其他身分識別資訊，而且包含連接至服務端點需要的所有設定 (即使是預設的設定)。</span><span class="sxs-lookup"><span data-stu-id="fe2da-141">The generated configuration file has additional identity information, and contains all settings necessary to connect to the service endpoint even though they are the default settings.</span></span> <span data-ttu-id="fe2da-142">如需身分識別資訊的詳細資訊，請參閱[服務身分識別和驗證](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)，並[\<身分識別 >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)。</span><span class="sxs-lookup"><span data-stu-id="fe2da-142">For more information about identity information, see [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md), and [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md).</span></span>  
  
4.  <span data-ttu-id="fe2da-143">在用戶端機器上，從命令提示字元啟動 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="fe2da-143">On the client machine, launch Client.exe from a command prompt.</span></span>  
  
### <a name="to-debug-a-service"></a><span data-ttu-id="fe2da-144">偵錯服務</span><span class="sxs-lookup"><span data-stu-id="fe2da-144">To debug a service</span></span>  
  
1.  <span data-ttu-id="fe2da-145">方案 （用戶端和服務） 使用的組建**建置**功能表或 CTRL + SHIFT + B。</span><span class="sxs-lookup"><span data-stu-id="fe2da-145">Build the solution (both client and service) using the **Build** menu or CTRL+SHIFT+B.</span></span>  
  
2.  <span data-ttu-id="fe2da-146">如果服務是以 IIS 裝載：</span><span class="sxs-lookup"><span data-stu-id="fe2da-146">If the service is hosted in IIS:</span></span>  
  
    1.  <span data-ttu-id="fe2da-147">啟用服務使用瀏覽器輸入位址 http://localhost/servicemodelsamples/service.svc。</span><span class="sxs-lookup"><span data-stu-id="fe2da-147">Activate the service using a browser by entering the address http://localhost/servicemodelsamples/service.svc.</span></span>  
  
    2.  <span data-ttu-id="fe2da-148">在方案中，選擇**偵錯** 功能表並**附加至處理序**功能表項目。</span><span class="sxs-lookup"><span data-stu-id="fe2da-148">In the solution, choose the **Debug** menu and the **Attach to Process** menu item.</span></span>  
  
    3.  <span data-ttu-id="fe2da-149">選取 [顯示所有使用者的處理序] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="fe2da-149">Select the **Show processes from all users** check box.</span></span>  
  
    4.  <span data-ttu-id="fe2da-150">選取主機背景工作處理序 W3wp.exe 來進行偵錯 (在 Windows XP 中選取 ASPNet_wp.exe)。</span><span class="sxs-lookup"><span data-stu-id="fe2da-150">Select the host worker process W3wp.exe to debug (select ASPNet_wp.exe on Windows XP).</span></span>  
  
3.  <span data-ttu-id="fe2da-151">您現在可以在服務程式碼中設定中斷點，然後啟用發生例外狀況時的中斷點。</span><span class="sxs-lookup"><span data-stu-id="fe2da-151">You can now set breakpoints in the service code and enable breakpoints on exceptions.</span></span>  
  
4.  <span data-ttu-id="fe2da-152">以滑鼠右鍵按一下 用戶端專案項目，然後選擇 **偵錯**，**開始新執行個體**。</span><span class="sxs-lookup"><span data-stu-id="fe2da-152">Right-click the client project item and choose **Debug**, **Start new instance**.</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="fe2da-153">若要在使用範例之後進行清除</span><span class="sxs-lookup"><span data-stu-id="fe2da-153">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="fe2da-154">如果因為考量安全性而以 IIS 裝載服務，則請在完成範例時，移除虛擬目錄定義以及在安裝步驟中所授與的權限。</span><span class="sxs-lookup"><span data-stu-id="fe2da-154">If the service is hosted in IIS for security purposes, remove the virtual directory definition and permissions granted in the setup steps when you are finished with the samples.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe2da-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe2da-155">See Also</span></span>  
 [<span data-ttu-id="fe2da-156">建置 Windows Communication Foundation 範例</span><span class="sxs-lookup"><span data-stu-id="fe2da-156">Building the Windows Communication Foundation Samples</span></span>](../../../../docs/framework/wcf/samples/building-the-samples.md)  
 [<span data-ttu-id="fe2da-157">工作群組中與跨電腦執行範例</span><span class="sxs-lookup"><span data-stu-id="fe2da-157">Running the Samples in a Workgroup and Across Machines</span></span>](https://msdn.microsoft.com/library/a451a525-e7ce-452d-9da9-620221260113)  
 [<span data-ttu-id="fe2da-158">疑難排解祕訣</span><span class="sxs-lookup"><span data-stu-id="fe2da-158">Troubleshooting Tips</span></span>](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)
