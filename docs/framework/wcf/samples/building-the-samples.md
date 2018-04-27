---
title: 建置 Windows Communication Foundation 範例
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2899e7a5-9cb2-4e8d-b8d2-f31391549198
caps.latest.revision: 33
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b8b3e3006072855673c37786ffb763fcd610e40c
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="building-the-windows-communication-foundation-samples"></a><span data-ttu-id="481f0-102">建置 Windows Communication Foundation 範例</span><span class="sxs-lookup"><span data-stu-id="481f0-102">Building the Windows Communication Foundation Samples</span></span>
<span data-ttu-id="481f0-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]範例可以使用 Visual Studio 2010 或建置**msbuild**從命令列命令。</span><span class="sxs-lookup"><span data-stu-id="481f0-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples can be built using Visual Studio 2010 or using the **msbuild** command from the command line.</span></span> <span data-ttu-id="481f0-104">本主題將同時說明這兩個程序。</span><span class="sxs-lookup"><span data-stu-id="481f0-104">Both procedures are described in this topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="481f0-105">在建置或執行任何之前[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]範例，請確定您已經執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="481f0-105">Before building or running any of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] samples, ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
### <a name="to-build-the-sample-using-a-command-prompt"></a><span data-ttu-id="481f0-106">若要使用命令提示字元建置範例</span><span class="sxs-lookup"><span data-stu-id="481f0-106">To build the sample using a command prompt</span></span>  
  
1.  <span data-ttu-id="481f0-107">使用系統管理員權限來開啟 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 命令提示字元，並巡覽至安裝範例所在目錄位置下任一語言特定子目錄。</span><span class="sxs-lookup"><span data-stu-id="481f0-107">Open the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt with administrator privileges and navigate to the language-specific subdirectory under the directory location where you installed the sample.</span></span>  
  
2.  <span data-ttu-id="481f0-108">型別`msbuild`在命令列。</span><span class="sxs-lookup"><span data-stu-id="481f0-108">Type `msbuild` at the command line.</span></span> <span data-ttu-id="481f0-109">用戶端程式檔會建置至 client\bin，服務程式檔則建置至 service\bin。</span><span class="sxs-lookup"><span data-stu-id="481f0-109">The client program files are built to client\bin and the service program files are built to service\bin.</span></span> <span data-ttu-id="481f0-110">如果服務是由 Internet Information Services (IIS) 裝載，則服務程式檔也會被複製到 servicemodelsamples 目錄及其 \bin 子目錄中。</span><span class="sxs-lookup"><span data-stu-id="481f0-110">If the service is hosted by Internet Information Services (IIS), the service program files are also copied to the servicemodelsamples directory and its \bin subdirectory.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="481f0-111">您必須在 %systemdrive%\inetpub\wwwroot 上設定 ACL 以將修改權限授予您用來執行的帳戶。</span><span class="sxs-lookup"><span data-stu-id="481f0-111">You must set the ACLs on %systemdrive%\inetpub\wwwroot to grant modify permissions to the account under which you are running.</span></span> <span data-ttu-id="481f0-112">否則，有些建置後事件將會失敗。</span><span class="sxs-lookup"><span data-stu-id="481f0-112">Otherwise some post build events fail.</span></span> <span data-ttu-id="481f0-113">或者，您也可以不去改變這些 ACL，而以系統管理員身分來執行 SDK 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="481f0-113">Alternatively, you can leave the ACLs as they are and run the SDK command prompt as administrator.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="481f0-114">若要使用 Visual Studio 建置範例</span><span class="sxs-lookup"><span data-stu-id="481f0-114">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="481f0-115">如果您使用[!INCLUDE[wv](../../../../includes/wv-md.md)]， [!INCLUDE[lserver](../../../../includes/lserver-md.md)]，Windows 7 或 Windows Server 2008 R2，且在執行[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]，您必須使用更高權限執行 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="481f0-115">If you are using [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], Windows 7, or Windows Server 2008 R2, and running [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], you must run Visual Studio with elevated permission.</span></span> <span data-ttu-id="481f0-116">若要這樣做，請以滑鼠右鍵按一下 開始 功能表上的圖示，然後按一下 **系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="481f0-116">To do so, right-click the icon on the Start menu and then click **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="481f0-117">從**檔案**功能表在 Visual Studio 中，按一下**開啟**，然後按一下 **專案/方案**。</span><span class="sxs-lookup"><span data-stu-id="481f0-117">From the **File** menu in Visual Studio, click **Open**, then click **Project/Solution**.</span></span> <span data-ttu-id="481f0-118">瀏覽至安裝範例所在的目錄下的特定語言子目錄，然後按兩下.sln 檔案圖示，以在 Visual Studio 中開啟方案。</span><span class="sxs-lookup"><span data-stu-id="481f0-118">Navigate to the language-specific subdirectory under the directory in which you installed the sample, and double-click the .sln file icon to open the solution in Visual Studio.</span></span>  
  
3.  <span data-ttu-id="481f0-119">在**建置**功能表上，選取**重建方案**。</span><span class="sxs-lookup"><span data-stu-id="481f0-119">In the **Build** menu, select **Rebuild Solution**.</span></span> <span data-ttu-id="481f0-120">用戶端程式檔會建置至 client\bin，服務程式檔則建置至 service\bin。</span><span class="sxs-lookup"><span data-stu-id="481f0-120">The client program files are built to client\bin and the service program files are built to service\bin.</span></span> <span data-ttu-id="481f0-121">如果服務是由 IIS 裝載，則服務程式檔也會被複製到 servicemodelsamples 目錄及其 \bin 子目錄中。</span><span class="sxs-lookup"><span data-stu-id="481f0-121">If the service is hosted in IIS, the service program files are also copied to the servicemodelsamples directory and its \bin subdirectory.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="481f0-122">您必須在 %systemdrive%\inetpub\wwwroot 上設定 ACL 以將修改權限授予您用來執行的帳戶。</span><span class="sxs-lookup"><span data-stu-id="481f0-122">You must set the ACLs on %systemdrive%\inetpub\wwwroot to grant modify permissions to the account under which you are running.</span></span> <span data-ttu-id="481f0-123">否則，有些建置後事件將會失敗。</span><span class="sxs-lookup"><span data-stu-id="481f0-123">Otherwise some post build events fail.</span></span> <span data-ttu-id="481f0-124">不過，您也可以不去改變這些 ACL，而以系統管理員身分來執行 SDK 命令提示字元或 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="481f0-124">Alternatively, you can leave the ACLs as they are and run the SDK command prompt or Visual Studio as administrator.</span></span> <span data-ttu-id="481f0-125">有些 Visual Studio 動作 (例如將偵錯工具附加到 ASP.Net 工作處理序中) 同時要求具備系統管理員權限。</span><span class="sxs-lookup"><span data-stu-id="481f0-125">Some Visual Studio actions (such as attaching a debugger to the ASP.Net worker process) also require administrative privileges.</span></span>  
  
## <a name="setup-batch-files-and-scripts"></a><span data-ttu-id="481f0-126">設定批次檔和指令碼</span><span class="sxs-lookup"><span data-stu-id="481f0-126">Setup Batch Files and Scripts</span></span>  
 <span data-ttu-id="481f0-127">Setup.exe 和 Cleanup.exe 批次檔與指令碼必須透過 Visual Studio 命令提示字元來執行。</span><span class="sxs-lookup"><span data-stu-id="481f0-127">Setup.exe and Cleanup.exe batch files and scripts should be run from a Visual Studio command prompt.</span></span> <span data-ttu-id="481f0-128">數種設定與清除檔案會執行需要系統管理員權限才能執行與啟動的工作。</span><span class="sxs-lookup"><span data-stu-id="481f0-128">Several set up and clean up files perform tasks that require administrative privileges and should be launched with administrator privileges.</span></span>  
  
## <a name="important-security-information-about-metadata-endpoints"></a><span data-ttu-id="481f0-129">關於中繼資料端點的重要安全性資訊</span><span class="sxs-lookup"><span data-stu-id="481f0-129">Important Security Information about Metadata Endpoints</span></span>  
 <span data-ttu-id="481f0-130">為了避免意外洩露潛在的敏感服務中繼資料，[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務的預設組態會停用中繼資料發行。</span><span class="sxs-lookup"><span data-stu-id="481f0-130">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services disables metadata publishing.</span></span> <span data-ttu-id="481f0-131">這個行為依預設為安全行為，但也表示您無法使用中繼資料匯入工具 (例如 Svcutil.exe) 來產生呼叫服務所需的用戶端程式碼，除非組態中已明確啟用服務的中繼發行行為。</span><span class="sxs-lookup"><span data-stu-id="481f0-131">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span> <span data-ttu-id="481f0-132">為了讓範例的實驗順利進行，幾乎所有範例都會公開不安全的中繼資料發行端點。</span><span class="sxs-lookup"><span data-stu-id="481f0-132">To make experimenting with the samples easier, almost all samples expose an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="481f0-133">未經驗證的匿名使用者可能可以使用這類端點，所以部署前必須小心謹慎，才能確保公開服務中繼資料是否適切。</span><span class="sxs-lookup"><span data-stu-id="481f0-133">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="481f0-134"> 發行服務中繼資料，請參閱[中繼資料發行行為](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)範例。</span><span class="sxs-lookup"><span data-stu-id="481f0-134"> publishing service metadata, see the [Metadata Publishing Behavior](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md) sample.</span></span> <span data-ttu-id="481f0-135">請參閱[自訂安全中繼資料端點](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)範例如保障安全的中繼資料端點的範例。</span><span class="sxs-lookup"><span data-stu-id="481f0-135">See the [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) sample for a sample securing a metadata endpoint.</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="481f0-136">例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="481f0-136">Exception Handling</span></span>  
 <span data-ttu-id="481f0-137">一般來說，這些範例不包含例外狀況處理，以便讓程式碼專注在範例主題上。</span><span class="sxs-lookup"><span data-stu-id="481f0-137">Generally speaking these samples do not include exception handling to keep the code focused on the subject of the sample.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="481f0-138"> 例外狀況處理，請參閱[預期的例外狀況](../../../../docs/framework/wcf/samples/expected-exceptions.md)範例。</span><span class="sxs-lookup"><span data-stu-id="481f0-138"> exception handling, see the [Expected Exceptions](../../../../docs/framework/wcf/samples/expected-exceptions.md) sample.</span></span>  
  
## <a name="regenerating-clients-and-configuration-with-svcutil"></a><span data-ttu-id="481f0-139">使用 Svcutil 重新產生用戶端與組態</span><span class="sxs-lookup"><span data-stu-id="481f0-139">Regenerating Clients and Configuration with Svcutil</span></span>  
 <span data-ttu-id="481f0-140">您可以使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)重新產生用戶端程式碼和組態的範例。</span><span class="sxs-lookup"><span data-stu-id="481f0-140">You can use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to regenerate client code and configuration for most of the samples.</span></span> <span data-ttu-id="481f0-141">某些範例需要您手動編輯組態。</span><span class="sxs-lookup"><span data-stu-id="481f0-141">Some samples require manually edited configuration.</span></span> <span data-ttu-id="481f0-142">例如，如果您使用 Svcutil.exe 針對使用用戶端憑證認證的範例重新產生組態，則您必須手動指定先前設定的認證。</span><span class="sxs-lookup"><span data-stu-id="481f0-142">For example, if you use Svcutil.exe to regenerate the configuration for a sample that uses client certificate credentials, you must manually specify the credentials previously configured.</span></span> <span data-ttu-id="481f0-143">某些範例使用特定的 Svcutil.exe 選項來影響產生的程式碼，而這些選項都會在特定的範例主題中加以指定。</span><span class="sxs-lookup"><span data-stu-id="481f0-143">Some samples use specific Svcutil.exe options to affect the generated code, these options are specified in the specific sample topics.</span></span>  
  
#### <a name="to-regenerate-the-client-and-configuration-files"></a><span data-ttu-id="481f0-144">若要重新產生用戶端與組態檔</span><span class="sxs-lookup"><span data-stu-id="481f0-144">To regenerate the client and configuration files</span></span>  
  
1.  <span data-ttu-id="481f0-145">開啟 [SDK 命令提示字元]，並巡覽至安裝範例所在目錄位置下任一語言特定子目錄。</span><span class="sxs-lookup"><span data-stu-id="481f0-145">Open an SDK command prompt and navigate to the language-specific subdirectory under the directory location where you installed the sample.</span></span>  
  
2.  <span data-ttu-id="481f0-146">如果服務是 Web 裝載的型別，請使用下列命令。</span><span class="sxs-lookup"><span data-stu-id="481f0-146">If the service is a Web-hosted type, use the following command.</span></span>  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs  
    ```  
  
     <span data-ttu-id="481f0-147">如果服務是自我裝載的型別，請使用下列命令。</span><span class="sxs-lookup"><span data-stu-id="481f0-147">If the service is a self-hosted type the following command.</span></span>  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /out:generatedClient.cs  
    ```  
  
     <span data-ttu-id="481f0-148">取代http://localhost:8000/ServiceModelSamples/service.svc/mex自我裝載的服務的 mex 端點的位址。</span><span class="sxs-lookup"><span data-stu-id="481f0-148">Replace http://localhost:8000/ServiceModelSamples/service.svc/mex with the address of the self-hosted service's mex endpoint.</span></span>  
  
     <span data-ttu-id="481f0-149">若要以 Visual Basic 型別來產生用戶端，請使用下列命令。</span><span class="sxs-lookup"><span data-stu-id="481f0-149">To generate the client in a Visual Basic type, use the following command.</span></span>  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb  
    ```  
  
     <span data-ttu-id="481f0-150">如果服務是自我裝載的型別，請使用下列命令。</span><span class="sxs-lookup"><span data-stu-id="481f0-150">If the service is a self-hosted type, use the following command.</span></span>  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="481f0-151">略過加入產生的用戶端設定 **/noConfig**選項。</span><span class="sxs-lookup"><span data-stu-id="481f0-151">To skip the generation of client configuration add the **/noConfig** option.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="481f0-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="481f0-152">See Also</span></span>  
 [<span data-ttu-id="481f0-153">執行 Windows Communication Foundation 範例</span><span class="sxs-lookup"><span data-stu-id="481f0-153">Running the Windows Communication Foundation Samples</span></span>](../../../../docs/framework/wcf/samples/running-the-samples.md)  
 [<span data-ttu-id="481f0-154">ServiceModel 中繼資料公用程式工具 (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="481f0-154">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
