---
title: Windows Communication Foundation 範例的單次安裝程序
ms.date: 03/30/2017
ms.assetid: a5848ffd-3eb5-432d-812e-bd948ccb6bca
ms.openlocfilehash: bf25ea4734bad007fa3ac19df0664932d981519c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548113"
---
# <a name="one-time-setup-procedure-for-the-windows-communication-foundation-samples"></a><span data-ttu-id="d832a-102">Windows Communication Foundation 範例的單次安裝程序</span><span class="sxs-lookup"><span data-stu-id="d832a-102">One-Time Setup Procedure for the Windows Communication Foundation Samples</span></span>

<span data-ttu-id="d832a-103">大部分的 Windows Communication Foundation (WCF) 範例都裝載于 Internet Information Services (IIS) 中，並從一般虛擬目錄執行。</span><span class="sxs-lookup"><span data-stu-id="d832a-103">Most of the Windows Communication Foundation (WCF) samples are hosted in Internet Information Services (IIS) and run from a common virtual directory.</span></span> <span data-ttu-id="d832a-104">此一次性安裝程式會在磁片上建立資料夾;它也會將虛擬目錄加入至名為 **ServiceModelSamples**的 IIS。</span><span class="sxs-lookup"><span data-stu-id="d832a-104">This one-time setup procedure creates a folder on the disk; it also adds a virtual directory to IIS named **ServiceModelSamples**.</span></span>

<span data-ttu-id="d832a-105">**ServiceModelSamples**虛擬目錄會用來建立及執行所有使用裝載于 IIS 之服務的範例。</span><span class="sxs-lookup"><span data-stu-id="d832a-105">The **ServiceModelSamples** virtual directory is used for building and running all samples that use an IIS-hosted service.</span></span> <span data-ttu-id="d832a-106">這是執行範例時唯一必要的虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="d832a-106">This is the only virtual directory that is required to run the samples.</span></span> <span data-ttu-id="d832a-107">建立範例將會取代此虛擬目錄中所有先前部署的服務；此虛擬目錄中只會部屬並提供最近建立的範例。</span><span class="sxs-lookup"><span data-stu-id="d832a-107">Building a sample will replace any previously deployed service at this virtual directory; only the most recently built sample will be deployed and available in this virtual directory.</span></span>

> [!NOTE]
> <span data-ttu-id="d832a-108">您必須在本機系統管理員帳戶下執行所有的命令。</span><span class="sxs-lookup"><span data-stu-id="d832a-108">You must run all commands under a local administrator account.</span></span> <span data-ttu-id="d832a-109">如果您使用的是 Windows 7、Windows Vista 或 Windows Server 2008 R2，您也必須以較高的許可權來執行命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="d832a-109">If you are using Windows 7, Windows Vista, or Windows Server 2008 R2, you must also run the command prompt with elevated privileges.</span></span> <span data-ttu-id="d832a-110">若要這樣做，請以滑鼠右鍵按一下命令提示字元圖示，然後按一下 [以 **系統管理員身分執行**]。</span><span class="sxs-lookup"><span data-stu-id="d832a-110">To do so, right-click the command prompt icon, and then click **Run as administrator**.</span></span> <span data-ttu-id="d832a-111">本主題中的所有命令都必須在擁有適當路徑設定的命令提示字元下執行。</span><span class="sxs-lookup"><span data-stu-id="d832a-111">All commands in this topic must be run in a command prompt that has the appropriate path settings.</span></span>  <span data-ttu-id="d832a-112">最簡單的確保方式就是使用 Visual Studio 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="d832a-112">The easiest way to ensure this is by using the Visual Studio Command Prompt.</span></span> <span data-ttu-id="d832a-113">若要開啟這個提示，請依序按一下 [ **開始**]、[ **所有程式**]、[ **Visual Studio 2010**]、[ **Visual Studio Tools**]、[ \*\*Visual Studio 命令提示字元] (2010) \*\*，然後按一下 [以 **系統管理員身分執行**]。</span><span class="sxs-lookup"><span data-stu-id="d832a-113">To open this prompt, click **Start**, select **All Programs**, scroll down to **Visual Studio 2010**, select **Visual Studio Tools**, right-click **Visual Studio Command Prompt (2010)**, and then click **Run as administrator**.</span></span> <span data-ttu-id="d832a-114">如果您已經安裝其中一個 Visual Studio Express Edition，就無法使用這個命令提示字元，而且您必須將 "C:\Windows\Microsoft.Net\Framework\v4.0" 加入至系統路徑中。</span><span class="sxs-lookup"><span data-stu-id="d832a-114">If you have one of the Visual Studio Express editions installed, this command prompt is not available, and you will have to add "C:\Windows\Microsoft.Net\Framework\v4.0" to the system path.</span></span>

### <a name="one-time-setup-procedure-for-wcf-samples"></a><span data-ttu-id="d832a-115">WCF 範例的單次安裝程序</span><span class="sxs-lookup"><span data-stu-id="d832a-115">One-time setup procedure for WCF samples</span></span>

1. <span data-ttu-id="d832a-116">確定已設定 ASP.NET。</span><span class="sxs-lookup"><span data-stu-id="d832a-116">Ensure that ASP.NET is set up.</span></span> <span data-ttu-id="d832a-117">如需有關如何設定 ASP.NET 的詳細資訊，請參閱 [網際網路資訊服務裝載指示](internet-information-service-hosting-instructions.md)。</span><span class="sxs-lookup"><span data-stu-id="d832a-117">For more information about how to set up ASP.NET, see [Internet Information Service Hosting Instructions](internet-information-service-hosting-instructions.md).</span></span>

2. <span data-ttu-id="d832a-118">確定已安裝 .NET Framework 4。</span><span class="sxs-lookup"><span data-stu-id="d832a-118">Ensure that .NET Framework 4 is installed.</span></span> <span data-ttu-id="d832a-119">在下列目錄中搜尋 v4.0 (或更新版本) ： **\Windows\Microsoft.NET\Framework**</span><span class="sxs-lookup"><span data-stu-id="d832a-119">Search the following directory for v4.0 (or later): **\Windows\Microsoft.NET\Framework**</span></span>

3. <span data-ttu-id="d832a-120">確定您已安裝 Visual Studio 2012 或更新版本，或者您的作業系統是 Windows Server 2008 SP2 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="d832a-120">Ensure you have Visual Studio 2012 or later installed, or your operating system is Windows Server 2008 SP2 or later.</span></span>

4. <span data-ttu-id="d832a-121">執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="d832a-121">Run the following commands.</span></span> <span data-ttu-id="d832a-122">如需這些命令的執行原因的詳細資訊，請參閱 [IIS 託管服務失敗](/previous-versions/dotnet/netframework-3.5/ms752252(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="d832a-122">For more information about why these commands must be run, see [IIS Hosted Service Fails](/previous-versions/dotnet/netframework-3.5/ms752252(v=vs.90)).</span></span>

    > [!WARNING]
    > <span data-ttu-id="d832a-123">如果您重新安裝了 IIS，就必須再次執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="d832a-123">If IIS is reinstalled, the following commands will need to be run again.</span></span>

    ```console
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\aspnet_regiis" –i –enable
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\ServiceModelReg.exe" -r
    ```

    > [!WARNING]
    > <span data-ttu-id="d832a-124">執行命令 `aspnet_regiis –i –enable` 會使用 .NET Framework 4 來執行預設的應用程式集區，這可能會對相同電腦上的其他應用程式產生不相容的問題。</span><span class="sxs-lookup"><span data-stu-id="d832a-124">Running the command `aspnet_regiis –i –enable` will make the Default App Pool run using .NET Framework 4, which may produce incompatibility issues for other applications on the same computer.</span></span>

5. <span data-ttu-id="d832a-125">遵循 [防火牆指示](firewall-instructions.md) 來啟用範例所使用的埠。</span><span class="sxs-lookup"><span data-stu-id="d832a-125">Follow the [Firewall Instructions](firewall-instructions.md) for enabling the ports used by the samples.</span></span>

6. <span data-ttu-id="d832a-126">檢查下列預設目錄： \<InstallDrive> ：**\ WF_WCF_Samples**。</span><span class="sxs-lookup"><span data-stu-id="d832a-126">Check for the following default directory: \<InstallDrive>:**\WF_WCF_Samples**.</span></span> <span data-ttu-id="d832a-127">如果先前安裝了範例，這就是預設目錄。</span><span class="sxs-lookup"><span data-stu-id="d832a-127">If the samples were previously installed, this is the default directory.</span></span>

7. <span data-ttu-id="d832a-128">如果未安裝範例，請從 [Windows Communication Foundation (WCF) 安裝它們，並 Windows Workflow Foundation (適用于) 4 的 WF .NET Framework 範例](https://www.microsoft.com/download/details.aspx?id=21459)。</span><span class="sxs-lookup"><span data-stu-id="d832a-128">If the samples are not installed, install them from [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).</span></span>

8. <span data-ttu-id="d832a-129">安裝範例之後，請移至： \<InstallDrive> ：\*\*\ WF_WCF_Samples \wcf\setup \\ \*\*</span><span class="sxs-lookup"><span data-stu-id="d832a-129">After installing the samples, go to : \<InstallDrive>:**\WF_WCF_Samples\WCF\Setup\\**</span></span>

9. <span data-ttu-id="d832a-130">執行 **Setupvroot.bat** 批次檔。</span><span class="sxs-lookup"><span data-stu-id="d832a-130">Run the **Setupvroot.bat** batch file.</span></span> <span data-ttu-id="d832a-131">會執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="d832a-131">The following steps are performed:</span></span>

    - <span data-ttu-id="d832a-132">在 IIS 中建立名為 ServiceModelSamples 的虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="d832a-132">A virtual directory is created in IIS named ServiceModelSamples.</span></span>

    - <span data-ttu-id="d832a-133">建立名為 %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples 和 %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples\bin 的新磁碟目錄。</span><span class="sxs-lookup"><span data-stu-id="d832a-133">New disk directories are created named %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples and %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples\bin.</span></span>

    <span data-ttu-id="d832a-134">如果您想要手動設定這些目錄，請參閱 [虛擬目錄安裝指示](virtual-directory-setup-instructions.md)。</span><span class="sxs-lookup"><span data-stu-id="d832a-134">If you prefer to set up these directories manually, see the [Virtual Directory Setup Instructions](virtual-directory-setup-instructions.md).</span></span> <span data-ttu-id="d832a-135">若要還原此步驟中完成的所有變更，請在範例使用完畢之後執行 cleanupvroot.bat。</span><span class="sxs-lookup"><span data-stu-id="d832a-135">To revert all changes done in this step, run cleanupvroot.bat after you finish using the samples.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d832a-136">除非您執行 cleanupvroot.bat，否則只要在電腦上執行這個程序一次即可。</span><span class="sxs-lookup"><span data-stu-id="d832a-136">This procedure must be performed only once on a computer, unless cleanupvroot.bat is run.</span></span>

10. <span data-ttu-id="d832a-137">您必須將修改 %SystemDrive%\inetpub\wwwroot 的權限，授與您要用來建置範例和 Network Service 使用者的帳戶。</span><span class="sxs-lookup"><span data-stu-id="d832a-137">You must grant permission to modify for %SystemDrive%\inetpub\wwwroot to the account under which you are building the samples and the Network Service user.</span></span> <span data-ttu-id="d832a-138">在建立時，有些 Web 裝載的範例可能會嘗試將編譯後的二進位複製到先前所述的位置，如果您沒有設定適當的權限，建立就會中斷。</span><span class="sxs-lookup"><span data-stu-id="d832a-138">While building, some Web-hosted samples might attempt to copy the compiled binaries to the previously mentioned location, and if you have not set the appropriate permissions, the build will break.</span></span> <span data-ttu-id="d832a-139">或者，您可以保留許可權，然後以系統管理員身分執行 SDK 命令提示字元，或以系統管理員身分 (2012) 來 Visual Studio 命令提示字元，或在 Visual Studio 2012 中建立範例，也就是以系統管理員身分執行。</span><span class="sxs-lookup"><span data-stu-id="d832a-139">Alternatively, you can leave the permissions as they are and run the SDK command prompt or Visual Studio Command Prompt (2012) as Administrator, or build the samples in Visual Studio 2012, also run as Administrator.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d832a-140">如果沒有完成這個步驟，所有 IIS 裝載的範例都會在建立時失敗。</span><span class="sxs-lookup"><span data-stu-id="d832a-140">If this step is not completed, all IIS-hosted samples will fail while building.</span></span> <span data-ttu-id="d832a-141">請確定權限的設定正確，或以系統管理員身分同時執行 SDK 命令提示字元和 Visual Studio 命令提示字元 (2012)。</span><span class="sxs-lookup"><span data-stu-id="d832a-141">Ensure that you set the permissions correctly, or run both the SDK command prompt and Visual Studio Command Prompt (2012) as Administrator.</span></span>

11. <span data-ttu-id="d832a-142">在電腦上建立 C:\logs 目錄；某些案例可能會需要這個目錄。</span><span class="sxs-lookup"><span data-stu-id="d832a-142">Create a C:\logs directory on the computer; some samples might be expecting it.</span></span> <span data-ttu-id="d832a-143">請確認適當的帳戶已經將寫入權限授與此資料夾。</span><span class="sxs-lookup"><span data-stu-id="d832a-143">Make sure that the appropriate account has write access granted to this folder.</span></span> <span data-ttu-id="d832a-144">若為 Windows 7、Windows Vista 和 Windows Server 2008 R2，此帳戶為 **Network Service**。</span><span class="sxs-lookup"><span data-stu-id="d832a-144">For Windows 7, Windows Vista, and Windows Server 2008 R2, this account is **Network Service**.</span></span> <span data-ttu-id="d832a-145">若為 Windows Server 2008，此帳戶為 NT Authority\Network Service。</span><span class="sxs-lookup"><span data-stu-id="d832a-145">For  Windows Server 2008, the account is NT Authority\Network Service.</span></span> <span data-ttu-id="d832a-146">針對 Windows XP 和 Windows Server 2003，此帳戶為 ASPNET。</span><span class="sxs-lookup"><span data-stu-id="d832a-146">For Windows XP and Windows Server 2003, the account is ASPNET.</span></span>

12. <span data-ttu-id="d832a-147">執行 Setupcerttool.bat 檔案。</span><span class="sxs-lookup"><span data-stu-id="d832a-147">Run the Setupcerttool.bat file.</span></span> <span data-ttu-id="d832a-148">這個檔案位於  \<InstallPath> \ WF_WCF_Samples \wcf\setup\ 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="d832a-148">This file is located in the  \<InstallPath>\WF_WCF_Samples\WCF\Setup\  folder.</span></span>  <span data-ttu-id="d832a-149">這個指令碼會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="d832a-149">This script will perform the following tasks:</span></span>

    - <span data-ttu-id="d832a-150">建立 FindPrivateKey 工具。</span><span class="sxs-lookup"><span data-stu-id="d832a-150">Build the FindPrivateKey tool.</span></span>

    - <span data-ttu-id="d832a-151">建立名為 %ProgramFiles%\ServiceModelSampleTools 的目錄。</span><span class="sxs-lookup"><span data-stu-id="d832a-151">Create a directory called %ProgramFiles%\ServiceModelSampleTools.</span></span>

    - <span data-ttu-id="d832a-152">將新的 FindPrivateKey 工具複製到此目錄。</span><span class="sxs-lookup"><span data-stu-id="d832a-152">Copy the new FindPrivateKey tool to this directory.</span></span>

    <span data-ttu-id="d832a-153">使用憑證且裝載在 IIS 中的範例需要這項工具。</span><span class="sxs-lookup"><span data-stu-id="d832a-153">This tool is required by samples that use certificates and are hosted in IIS.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d832a-154">基於安全性考量，在您完成範例後，請記得執行名為 Cleanupvroot.bat 的批次檔，移除虛擬目錄定義以及在上述安裝步驟中授與的權限。</span><span class="sxs-lookup"><span data-stu-id="d832a-154">For security purposes, remember to remove the virtual directory definition and permissions granted in the setup steps above by running the batch file named Cleanupvroot.bat after you are finished with the samples.</span></span>

13. <span data-ttu-id="d832a-155">自我裝載 (而非裝載於 IIS) 的範例必須有權限將 HTTP 位址註冊到電腦上，以便進行接聽。</span><span class="sxs-lookup"><span data-stu-id="d832a-155">Samples that are self-hosted (not hosted in IIS) require permission to register HTTP addresses on the computer for listening.</span></span> <span data-ttu-id="d832a-156">HTTP 命名空間保留區的權限來自用以執行範例的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="d832a-156">The permission for an HTTP namespace reservation comes from the user account used to run the sample.</span></span> <span data-ttu-id="d832a-157">根據預設，系統管理員帳戶擁有註冊任何 HTTP 位址的權限。</span><span class="sxs-lookup"><span data-stu-id="d832a-157">By default, administrator accounts have the permission to register any HTTP address.</span></span> <span data-ttu-id="d832a-158">至於非系統管理員帳戶，則必須具有範例所用之 HTTP 命名空間的權限。</span><span class="sxs-lookup"><span data-stu-id="d832a-158">Non-administrator accounts must be granted permission for the HTTP namespaces used by the samples.</span></span> <span data-ttu-id="d832a-159">如需如何設定命名空間保留的詳細資訊，請參閱[設定 HTTP 和 HTTPS](../feature-details/configuring-http-and-https.md)。</span><span class="sxs-lookup"><span data-stu-id="d832a-159">For more information about how to configure namespace reservations, see [Configuring HTTP and HTTPS](../feature-details/configuring-http-and-https.md).</span></span>

14. <span data-ttu-id="d832a-160">有些範例需要訊息佇列。</span><span class="sxs-lookup"><span data-stu-id="d832a-160">Some samples require Message Queuing.</span></span> <span data-ttu-id="d832a-161">如需安裝指示，請參閱 [安裝訊息佇列 (MSMQ) ](installing-message-queuing-msmq.md) 。</span><span class="sxs-lookup"><span data-stu-id="d832a-161">See [Installing Message Queuing (MSMQ)](installing-message-queuing-msmq.md) for installation instructions.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d832a-162">請務必在您執行需要訊息佇列的任何範例之前，啟動 MSMQ 服務。</span><span class="sxs-lookup"><span data-stu-id="d832a-162">Ensure that you start the MSMQ service before you run any samples that require Message Queuing.</span></span>

15. <span data-ttu-id="d832a-163">有些範例需要憑證。</span><span class="sxs-lookup"><span data-stu-id="d832a-163">Some samples require certificates.</span></span> <span data-ttu-id="d832a-164">請參閱 [Internet Information Services (IIS) 伺服器憑證安裝指示](iis-server-certificate-installation-instructions.md)。</span><span class="sxs-lookup"><span data-stu-id="d832a-164">See [Internet Information Services (IIS) Server Certificate Installation Instructions](iis-server-certificate-installation-instructions.md).</span></span>
