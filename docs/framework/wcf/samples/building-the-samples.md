---
title: 建置 Windows Communication Foundation 範例
ms.date: 03/30/2017
ms.assetid: 2899e7a5-9cb2-4e8d-b8d2-f31391549198
ms.openlocfilehash: ee1c8101e31464fa203341d53137525433782c18
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253828"
---
# <a name="building-the-windows-communication-foundation-samples"></a><span data-ttu-id="a9dcc-102">建置 Windows Communication Foundation 範例</span><span class="sxs-lookup"><span data-stu-id="a9dcc-102">Building the Windows Communication Foundation Samples</span></span>

<span data-ttu-id="a9dcc-103">Windows Communication Foundation (WCF) 範例可以使用 Visual Studio IDE 或從命令列使用 **msbuild** 命令來建立。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-103">The Windows Communication Foundation (WCF) samples can be built using the Visual Studio IDE or using the **msbuild** command from the command line.</span></span> <span data-ttu-id="a9dcc-104">本主題將同時說明這兩個程序。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-104">Both procedures are described in this topic.</span></span>

> [!NOTE]
> <span data-ttu-id="a9dcc-105">在建立或執行任何 WCF 範例之前，請確定您已執行 [Windows Communication Foundation 範例的單次安裝程式](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-105">Before building or running any of the WCF samples, ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

## <a name="to-build-the-sample-using-a-command-prompt"></a><span data-ttu-id="a9dcc-106">若要使用命令提示字元建置範例</span><span class="sxs-lookup"><span data-stu-id="a9dcc-106">To build the sample using a command prompt</span></span>

1. <span data-ttu-id="a9dcc-107">開啟 Visual Studio 的開發人員命令提示字元，然後在您安裝範例的目錄位置下流覽至特定語言的子目錄。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-107">Open Developer Command Prompt for Visual Studio and navigate to the language-specific subdirectory under the directory location where you installed the sample.</span></span>

2. <span data-ttu-id="a9dcc-108">`msbuild`在命令列輸入。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-108">Type `msbuild` at the command line.</span></span> <span data-ttu-id="a9dcc-109">用戶端程式檔案是 *client\bin* 建立的，而且服務程式檔案是 *service\bin* 的。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-109">The client program files are built to *client\bin* and the service program files are built to *service\bin*.</span></span> <span data-ttu-id="a9dcc-110">如果服務是由 Internet Information Services (IIS) 所裝載，則服務程式檔也會複製到 *servicemodelsamples* 目錄及其 *\bin* 子目錄中。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-110">If the service is hosted by Internet Information Services (IIS), the service program files are also copied to the *servicemodelsamples* directory and its *\bin* subdirectory.</span></span>

> [!NOTE]
> <span data-ttu-id="a9dcc-111">您必須在 *%systemdrive%\inetpub\wwwroot* 上設定 acl，以將 modify 許可權授與您執行的帳戶。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-111">You must set the ACLs on *%systemdrive%\inetpub\wwwroot* to grant modify permissions to the account under which you are running.</span></span> <span data-ttu-id="a9dcc-112">否則，有些建置後事件將會失敗。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-112">Otherwise some post build events fail.</span></span> <span data-ttu-id="a9dcc-113">或者，您也可以不去改變這些 ACL，而以系統管理員身分來執行 SDK 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-113">Alternatively, you can leave the ACLs as they are and run the SDK command prompt as administrator.</span></span>

## <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="a9dcc-114">若要使用 Visual Studio 建置範例</span><span class="sxs-lookup"><span data-stu-id="a9dcc-114">To build the sample using Visual Studio</span></span>

1. <span data-ttu-id="a9dcc-115">從 Visual Studio **的 [檔案**] 功能表中，選取 [**開啟**  >  **專案/方案**]。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-115">From the **File** menu in Visual Studio, select **Open** > **Project/Solution**.</span></span> <span data-ttu-id="a9dcc-116">流覽至您在其中安裝範例的目錄下的語言特定子目錄，然後按兩下 .sln 檔案圖示，在 Visual Studio 中開啟方案。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-116">Navigate to the language-specific subdirectory under the directory in which you installed the sample, and double-click the .sln file icon to open the solution in Visual Studio.</span></span>

1. <span data-ttu-id="a9dcc-117">從 [ **組建** ] 功能表中，選取 [ **重建方案**]。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-117">From the **Build** menu, select **Rebuild Solution**.</span></span>

   <span data-ttu-id="a9dcc-118">用戶端程式檔會建置至 client\bin，服務程式檔則建置至 service\bin。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-118">The client program files are built to client\bin and the service program files are built to service\bin.</span></span> <span data-ttu-id="a9dcc-119">如果服務是裝載在 IIS 中，則服務程式檔也會複製到 *servicemodelsamples* 目錄及其 *\bin* 子目錄中。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-119">If the service is hosted in IIS, the service program files are also copied to the *servicemodelsamples* directory and its *\bin* subdirectory.</span></span>

> [!NOTE]
> <span data-ttu-id="a9dcc-120">您必須在 %systemdrive%\inetpub\wwwroot 上設定 ACL 以將修改權限授予您用來執行的帳戶。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-120">You must set the ACLs on %systemdrive%\inetpub\wwwroot to grant modify permissions to the account under which you are running.</span></span> <span data-ttu-id="a9dcc-121">否則，有些建置後事件將會失敗。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-121">Otherwise some post build events fail.</span></span> <span data-ttu-id="a9dcc-122">不過，您也可以不去改變這些 ACL，而以系統管理員身分來執行 SDK 命令提示字元或 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-122">Alternatively, you can leave the ACLs as they are and run the SDK command prompt or Visual Studio as administrator.</span></span> <span data-ttu-id="a9dcc-123">某些 Visual Studio 動作 (例如，將偵錯工具附加至 ASP.NET 背景工作進程) 也需要系統管理許可權。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-123">Some Visual Studio actions (such as attaching a debugger to the ASP.NET worker process) also require administrative privileges.</span></span>

## <a name="setup-batch-files-and-scripts"></a><span data-ttu-id="a9dcc-124">設定批次檔和指令碼</span><span class="sxs-lookup"><span data-stu-id="a9dcc-124">Setup Batch Files and Scripts</span></span>

 <span data-ttu-id="a9dcc-125">Setup.exe 和 Cleanup.exe 批次檔和腳本應從開發人員命令提示字元執行，以進行 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-125">Setup.exe and Cleanup.exe batch files and scripts should be run from Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="a9dcc-126">數種設定與清除檔案會執行需要系統管理員權限才能執行與啟動的工作。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-126">Several set up and clean up files perform tasks that require administrative privileges and should be launched with administrator privileges.</span></span>

## <a name="important-security-information-about-metadata-endpoints"></a><span data-ttu-id="a9dcc-127">關於中繼資料端點的重要安全性資訊</span><span class="sxs-lookup"><span data-stu-id="a9dcc-127">Important Security Information about Metadata Endpoints</span></span>

 <span data-ttu-id="a9dcc-128">為了避免意外洩漏潛在的機密服務中繼資料，Windows Communication Foundation (WCF) 服務的預設設定會停用中繼資料發行。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-128">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="a9dcc-129">這個行為依預設為安全行為，但也表示您無法使用中繼資料匯入工具 (例如 Svcutil.exe) 來產生呼叫服務所需的用戶端程式碼，除非組態中已明確啟用服務的中繼發行行為。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-129">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span> <span data-ttu-id="a9dcc-130">為了讓範例的實驗順利進行，幾乎所有範例都會公開不安全的中繼資料發行端點。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-130">To make experimenting with the samples easier, almost all samples expose an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="a9dcc-131">未經驗證的匿名使用者可能可以使用這類端點，所以部署前必須小心謹慎，才能確保公開服務中繼資料是否適切。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-131">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span> <span data-ttu-id="a9dcc-132">如需發行服務中繼資料的詳細資訊，請參閱 [中繼資料發行行為](metadata-publishing-behavior.md) 範例。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-132">For more information about publishing service metadata, see the [Metadata Publishing Behavior](metadata-publishing-behavior.md) sample.</span></span> <span data-ttu-id="a9dcc-133">如需保護中繼資料端點的範例，請參閱 [自訂安全中繼資料端點](custom-secure-metadata-endpoint.md) 範例。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-133">See the [Custom Secure Metadata Endpoint](custom-secure-metadata-endpoint.md) sample for a sample securing a metadata endpoint.</span></span>

## <a name="exception-handling"></a><span data-ttu-id="a9dcc-134">例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="a9dcc-134">Exception Handling</span></span>

 <span data-ttu-id="a9dcc-135">一般來說，這些範例不包含例外狀況處理，以便讓程式碼專注在範例主題上。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-135">Generally speaking these samples do not include exception handling to keep the code focused on the subject of the sample.</span></span> <span data-ttu-id="a9dcc-136">如需例外狀況處理的詳細資訊，請參閱 [預期的例外](expected-exceptions.md) 狀況範例。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-136">For more information about exception handling, see the [Expected Exceptions](expected-exceptions.md) sample.</span></span>

## <a name="regenerating-clients-and-configuration-with-svcutil"></a><span data-ttu-id="a9dcc-137">使用 Svcutil 重新產生用戶端與組態</span><span class="sxs-lookup"><span data-stu-id="a9dcc-137">Regenerating Clients and Configuration with Svcutil</span></span>

 <span data-ttu-id="a9dcc-138">您可以使用 [配置 [中繼資料公用程式] 工具 ( # A0) ](../servicemodel-metadata-utility-tool-svcutil-exe.md) 來重新產生大部分範例的用戶端程式代碼和設定。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-138">You can use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to regenerate client code and configuration for most of the samples.</span></span> <span data-ttu-id="a9dcc-139">某些範例需要您手動編輯組態。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-139">Some samples require manually edited configuration.</span></span> <span data-ttu-id="a9dcc-140">例如，如果您使用 Svcutil.exe 針對使用用戶端憑證認證的範例重新產生組態，則您必須手動指定先前設定的認證。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-140">For example, if you use Svcutil.exe to regenerate the configuration for a sample that uses client certificate credentials, you must manually specify the credentials previously configured.</span></span> <span data-ttu-id="a9dcc-141">某些範例使用特定的 Svcutil.exe 選項來影響產生的程式碼，而這些選項都會在特定的範例主題中加以指定。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-141">Some samples use specific Svcutil.exe options to affect the generated code, these options are specified in the specific sample topics.</span></span>

### <a name="to-regenerate-the-client-and-configuration-files"></a><span data-ttu-id="a9dcc-142">若要重新產生用戶端與組態檔</span><span class="sxs-lookup"><span data-stu-id="a9dcc-142">To regenerate the client and configuration files</span></span>

1. <span data-ttu-id="a9dcc-143">開啟 [SDK 命令提示字元]，並巡覽至安裝範例所在目錄位置下任一語言特定子目錄。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-143">Open an SDK command prompt and navigate to the language-specific subdirectory under the directory location where you installed the sample.</span></span>

2. <span data-ttu-id="a9dcc-144">如果服務是 Web 裝載的型別，請使用下列命令。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-144">If the service is a Web-hosted type, use the following command.</span></span>

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs
    ```

     <span data-ttu-id="a9dcc-145">如果服務是自我裝載的型別，請使用下列命令。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-145">If the service is a self-hosted type the following command.</span></span>

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /out:generatedClient.cs
    ```

     <span data-ttu-id="a9dcc-146">取代 `http://localhost:8000/ServiceModelSamples/service.svc/mex` 為自我裝載服務 mex 端點的位址。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-146">Replace `http://localhost:8000/ServiceModelSamples/service.svc/mex` with the address of the self-hosted service's mex endpoint.</span></span>

     <span data-ttu-id="a9dcc-147">若要以 Visual Basic 型別來產生用戶端，請使用下列命令。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-147">To generate the client in a Visual Basic type, use the following command.</span></span>

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb
    ```

     <span data-ttu-id="a9dcc-148">如果服務是自我裝載的型別，請使用下列命令。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-148">If the service is a self-hosted type, use the following command.</span></span>

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb
    ```

    > [!NOTE]
    > <span data-ttu-id="a9dcc-149">若要略過用戶端設定的產生，請新增 **/noConfig** 選項。</span><span class="sxs-lookup"><span data-stu-id="a9dcc-149">To skip the generation of client configuration add the **/noConfig** option.</span></span>

## <a name="see-also"></a><span data-ttu-id="a9dcc-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9dcc-150">See also</span></span>

- [<span data-ttu-id="a9dcc-151">執行 Windows Communication Foundation 範例</span><span class="sxs-lookup"><span data-stu-id="a9dcc-151">Running the Windows Communication Foundation Samples</span></span>](running-the-samples.md)
- [<span data-ttu-id="a9dcc-152">ServiceModel 中繼資料公用程式工具 (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="a9dcc-152">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
