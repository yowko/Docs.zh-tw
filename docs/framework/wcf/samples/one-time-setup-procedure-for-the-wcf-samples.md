---
title: Windows Communication Foundation 範例的單次安裝程序
ms.date: 03/30/2017
ms.assetid: a5848ffd-3eb5-432d-812e-bd948ccb6bca
ms.openlocfilehash: 954ec04d2ef1ca7667b4f75a8a6652010b5dbd33
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121622"
---
# <a name="one-time-setup-procedure-for-the-windows-communication-foundation-samples"></a><span data-ttu-id="a74d1-102">Windows Communication Foundation 範例的單次安裝程序</span><span class="sxs-lookup"><span data-stu-id="a74d1-102">One-Time Setup Procedure for the Windows Communication Foundation Samples</span></span>

<span data-ttu-id="a74d1-103">大多數 Windows 通訊基礎 (WCF) 範例託管在 Internet 資訊服務 (IIS) 中,並且從公共虛擬目錄運行。</span><span class="sxs-lookup"><span data-stu-id="a74d1-103">Most of the Windows Communication Foundation (WCF) samples are hosted in Internet Information Services (IIS) and run from a common virtual directory.</span></span> <span data-ttu-id="a74d1-104">此一次性設置過程在磁碟上創建一個資料夾;它還向名為 **「服務模型範例**」的 IIS 添加了一個虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="a74d1-104">This one-time setup procedure creates a folder on the disk; it also adds a virtual directory to IIS named **ServiceModelSamples**.</span></span>

<span data-ttu-id="a74d1-105">**ServiceModelSample**虛擬目錄用於生成和運行使用IIS託管服務的所有範例。</span><span class="sxs-lookup"><span data-stu-id="a74d1-105">The **ServiceModelSamples** virtual directory is used for building and running all samples that use an IIS-hosted service.</span></span> <span data-ttu-id="a74d1-106">這是執行範例時唯一必要的虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="a74d1-106">This is the only virtual directory that is required to run the samples.</span></span> <span data-ttu-id="a74d1-107">建立範例將會取代此虛擬目錄中所有先前部署的服務；此虛擬目錄中只會部屬並提供最近建立的範例。</span><span class="sxs-lookup"><span data-stu-id="a74d1-107">Building a sample will replace any previously deployed service at this virtual directory; only the most recently built sample will be deployed and available in this virtual directory.</span></span>

> [!NOTE]
> <span data-ttu-id="a74d1-108">您必須在本機系統管理員帳戶下執行所有的命令。</span><span class="sxs-lookup"><span data-stu-id="a74d1-108">You must run all commands under a local administrator account.</span></span> <span data-ttu-id="a74d1-109">如果使用 Windows 7、Windows Vista 或 Windows Server 2008 R2,則還必須使用提升的許可權執行命令提示符。</span><span class="sxs-lookup"><span data-stu-id="a74d1-109">If you are using Windows 7, Windows Vista, or Windows Server 2008 R2, you must also run the command prompt with elevated privileges.</span></span> <span data-ttu-id="a74d1-110">為此,請右鍵單擊命令提示圖示,然後單擊"**以管理員身份運行**"。</span><span class="sxs-lookup"><span data-stu-id="a74d1-110">To do so, right-click the command prompt icon, and then click **Run as administrator**.</span></span> <span data-ttu-id="a74d1-111">本主題中的所有命令都必須在擁有適當路徑設定的命令提示字元下執行。</span><span class="sxs-lookup"><span data-stu-id="a74d1-111">All commands in this topic must be run in a command prompt that has the appropriate path settings.</span></span>  <span data-ttu-id="a74d1-112">最簡單的確保方式就是使用 Visual Studio 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="a74d1-112">The easiest way to ensure this is by using the Visual Studio Command Prompt.</span></span> <span data-ttu-id="a74d1-113">要打開此提示,請按下 **「開始**」,選擇 **「所有程式**」,向下滾動到**Visual Studio 2010**,選擇**視覺化工作室工具**,右鍵按下**視覺工作室命令提示(2010),** 然後按下 **「 以管理員身份執行**」。。</span><span class="sxs-lookup"><span data-stu-id="a74d1-113">To open this prompt, click **Start**, select **All Programs**, scroll down to **Visual Studio 2010**, select **Visual Studio Tools**, right-click **Visual Studio Command Prompt (2010)**, and then click **Run as administrator**.</span></span> <span data-ttu-id="a74d1-114">如果您已經安裝其中一個 Visual Studio Express Edition，就無法使用這個命令提示字元，而且您必須將 "C:\Windows\Microsoft.Net\Framework\v4.0" 加入至系統路徑中。</span><span class="sxs-lookup"><span data-stu-id="a74d1-114">If you have one of the Visual Studio Express editions installed, this command prompt is not available, and you will have to add "C:\Windows\Microsoft.Net\Framework\v4.0" to the system path.</span></span>

### <a name="one-time-setup-procedure-for-wcf-samples"></a><span data-ttu-id="a74d1-115">WCF 範例的單次安裝程序</span><span class="sxs-lookup"><span data-stu-id="a74d1-115">One-time setup procedure for WCF samples</span></span>

1. <span data-ttu-id="a74d1-116">確保設置了ASP.NET。</span><span class="sxs-lookup"><span data-stu-id="a74d1-116">Ensure that ASP.NET is set up.</span></span> <span data-ttu-id="a74d1-117">有關如何設置ASP.NET的詳細資訊,請參閱[網路資訊服務託管說明](internet-information-service-hosting-instructions.md)。</span><span class="sxs-lookup"><span data-stu-id="a74d1-117">For more information about how to set up ASP.NET, see [Internet Information Service Hosting Instructions](internet-information-service-hosting-instructions.md).</span></span>

2. <span data-ttu-id="a74d1-118">確保安裝了 .NET 框架 4。</span><span class="sxs-lookup"><span data-stu-id="a74d1-118">Ensure that .NET Framework 4 is installed.</span></span> <span data-ttu-id="a74d1-119">搜尋以下目錄搜尋 v4.0(或更高版本): **[Windows]Microsoft.NET_Framework**</span><span class="sxs-lookup"><span data-stu-id="a74d1-119">Search the following directory for v4.0 (or later): **\Windows\Microsoft.NET\Framework**</span></span>

3. <span data-ttu-id="a74d1-120">確保您安裝了 Visual Studio 2012 或更高版本,或者您的作業系統是 Windows Server 2008 SP2 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="a74d1-120">Ensure you have Visual Studio 2012 or later installed, or your operating system is Windows Server 2008 SP2 or later.</span></span>

4. <span data-ttu-id="a74d1-121">執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="a74d1-121">Run the following commands.</span></span> <span data-ttu-id="a74d1-122">有關必須運行這些命令的原因的詳細資訊,請參閱[IIS 託管服務失敗](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752252(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="a74d1-122">For more information about why these commands must be run, see [IIS Hosted Service Fails](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752252(v=vs.90)).</span></span>

    > [!WARNING]
    > <span data-ttu-id="a74d1-123">如果您重新安裝了 IIS，就必須再次執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="a74d1-123">If IIS is reinstalled, the following commands will need to be run again.</span></span>

    ```console
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\aspnet_regiis" –i –enable
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\ServiceModelReg.exe" -r
    ```

    > [!WARNING]
    > <span data-ttu-id="a74d1-124">運行該命令`aspnet_regiis –i –enable`將使預設應用池使用 .NET Framework 4 運行,這可能會為同一台電腦上的其他應用程序帶來不相容問題。</span><span class="sxs-lookup"><span data-stu-id="a74d1-124">Running the command `aspnet_regiis –i –enable` will make the Default App Pool run using .NET Framework 4, which may produce incompatibility issues for other applications on the same computer.</span></span>

5. <span data-ttu-id="a74d1-125">按照[防火牆說明](firewall-instructions.md)啟用示例使用的埠。</span><span class="sxs-lookup"><span data-stu-id="a74d1-125">Follow the [Firewall Instructions](firewall-instructions.md) for enabling the ports used by the samples.</span></span>

6. <span data-ttu-id="a74d1-126">檢查以下預設目錄:\<安裝磁碟機>:**\WF_WCF_Samples**。</span><span class="sxs-lookup"><span data-stu-id="a74d1-126">Check for the following default directory: \<InstallDrive>:**\WF_WCF_Samples**.</span></span> <span data-ttu-id="a74d1-127">如果先前安裝了範例，這就是預設目錄。</span><span class="sxs-lookup"><span data-stu-id="a74d1-127">If the samples were previously installed, this is the default directory.</span></span>

7. <span data-ttu-id="a74d1-128">如果未安裝範例,請從 .NET 框架 4 的[Windows 通信基礎 (WCF) 和 Windows 工作流基礎 (WF) 範例](https://www.microsoft.com/download/details.aspx?id=21459)安裝它們。</span><span class="sxs-lookup"><span data-stu-id="a74d1-128">If the samples are not installed, install them from [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).</span></span>

8. <span data-ttu-id="a74d1-129">安裝範例後,轉到\<: 安裝驅動器>:**\\{WF_WCF_Samples\WCF_ 安裝程式**</span><span class="sxs-lookup"><span data-stu-id="a74d1-129">After installing the samples, go to : \<InstallDrive>:**\WF_WCF_Samples\WCF\Setup\\**</span></span>

9. <span data-ttu-id="a74d1-130">運行**Setupvroot.bat**批次處理檔。</span><span class="sxs-lookup"><span data-stu-id="a74d1-130">Run the **Setupvroot.bat** batch file.</span></span> <span data-ttu-id="a74d1-131">會執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="a74d1-131">The following steps are performed:</span></span>

    - <span data-ttu-id="a74d1-132">在 IIS 中建立名為 ServiceModelSamples 的虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="a74d1-132">A virtual directory is created in IIS named ServiceModelSamples.</span></span>

    - <span data-ttu-id="a74d1-133">建立名為 %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples 和 %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples\bin 的新磁碟目錄。</span><span class="sxs-lookup"><span data-stu-id="a74d1-133">New disk directories are created named %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples and %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples\bin.</span></span>

    <span data-ttu-id="a74d1-134">如果您希望手動設定這些目錄,請參考[虛擬目錄設定說明](virtual-directory-setup-instructions.md)。</span><span class="sxs-lookup"><span data-stu-id="a74d1-134">If you prefer to set up these directories manually, see the [Virtual Directory Setup Instructions](virtual-directory-setup-instructions.md).</span></span> <span data-ttu-id="a74d1-135">若要還原此步驟中完成的所有變更，請在範例使用完畢之後執行 cleanupvroot.bat。</span><span class="sxs-lookup"><span data-stu-id="a74d1-135">To revert all changes done in this step, run cleanupvroot.bat after you finish using the samples.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a74d1-136">除非您執行 cleanupvroot.bat，否則只要在電腦上執行這個程序一次即可。</span><span class="sxs-lookup"><span data-stu-id="a74d1-136">This procedure must be performed only once on a computer, unless cleanupvroot.bat is run.</span></span>

10. <span data-ttu-id="a74d1-137">您必須將修改 %SystemDrive%\inetpub\wwwroot 的權限，授與您要用來建置範例和 Network Service 使用者的帳戶。</span><span class="sxs-lookup"><span data-stu-id="a74d1-137">You must grant permission to modify for %SystemDrive%\inetpub\wwwroot to the account under which you are building the samples and the Network Service user.</span></span> <span data-ttu-id="a74d1-138">在建立時，有些 Web 裝載的範例可能會嘗試將編譯後的二進位複製到先前所述的位置，如果您沒有設定適當的權限，建立就會中斷。</span><span class="sxs-lookup"><span data-stu-id="a74d1-138">While building, some Web-hosted samples might attempt to copy the compiled binaries to the previously mentioned location, and if you have not set the appropriate permissions, the build will break.</span></span> <span data-ttu-id="a74d1-139">或者,您可以保留許可權,並將 SDK 命令提示符或 Visual Studio 命令提示符 (2012) 作為管理員運行,或者在 Visual Studio 2012 中生成範例,也可以作為管理員運行。</span><span class="sxs-lookup"><span data-stu-id="a74d1-139">Alternatively, you can leave the permissions as they are and run the SDK command prompt or Visual Studio Command Prompt (2012) as Administrator, or build the samples in Visual Studio 2012, also run as Administrator.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a74d1-140">如果沒有完成這個步驟，所有 IIS 裝載的範例都會在建立時失敗。</span><span class="sxs-lookup"><span data-stu-id="a74d1-140">If this step is not completed, all IIS-hosted samples will fail while building.</span></span> <span data-ttu-id="a74d1-141">請確定權限的設定正確，或以系統管理員身分同時執行 SDK 命令提示字元和 Visual Studio 命令提示字元 (2012)。</span><span class="sxs-lookup"><span data-stu-id="a74d1-141">Ensure that you set the permissions correctly, or run both the SDK command prompt and Visual Studio Command Prompt (2012) as Administrator.</span></span>

11. <span data-ttu-id="a74d1-142">在電腦上建立 C:\logs 目錄；某些案例可能會需要這個目錄。</span><span class="sxs-lookup"><span data-stu-id="a74d1-142">Create a C:\logs directory on the computer; some samples might be expecting it.</span></span> <span data-ttu-id="a74d1-143">請確認適當的帳戶已經將寫入權限授與此資料夾。</span><span class="sxs-lookup"><span data-stu-id="a74d1-143">Make sure that the appropriate account has write access granted to this folder.</span></span> <span data-ttu-id="a74d1-144">對於 Windows 7、Windows Vista 和 Windows 伺服器 2008 R2,此帳戶為**網路服務**。</span><span class="sxs-lookup"><span data-stu-id="a74d1-144">For Windows 7, Windows Vista, and Windows Server 2008 R2, this account is **Network Service**.</span></span> <span data-ttu-id="a74d1-145">對於 Windows 伺服器 2008,該帳戶為 NT 頒發機構+網路服務。</span><span class="sxs-lookup"><span data-stu-id="a74d1-145">For  Windows Server 2008, the account is NT Authority\Network Service.</span></span> <span data-ttu-id="a74d1-146">對於 Windows XP 和 Windows 伺服器 2003,該帳戶為 ASPNET。</span><span class="sxs-lookup"><span data-stu-id="a74d1-146">For Windows XP and Windows Server 2003, the account is ASPNET.</span></span>

12. <span data-ttu-id="a74d1-147">執行 Setupcerttool.bat 檔案。</span><span class="sxs-lookup"><span data-stu-id="a74d1-147">Run the Setupcerttool.bat file.</span></span> <span data-ttu-id="a74d1-148">此檔案位於\<「安裝路徑>\WF_WCF_Samples_WCF_安裝程式]資料夾中。</span><span class="sxs-lookup"><span data-stu-id="a74d1-148">This file is located in the  \<InstallPath>\WF_WCF_Samples\WCF\Setup\  folder.</span></span>  <span data-ttu-id="a74d1-149">這個指令碼會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="a74d1-149">This script will perform the following tasks:</span></span>

    - <span data-ttu-id="a74d1-150">建立 FindPrivateKey 工具。</span><span class="sxs-lookup"><span data-stu-id="a74d1-150">Build the FindPrivateKey tool.</span></span>

    - <span data-ttu-id="a74d1-151">建立名為 %ProgramFiles%\ServiceModelSampleTools 的目錄。</span><span class="sxs-lookup"><span data-stu-id="a74d1-151">Create a directory called %ProgramFiles%\ServiceModelSampleTools.</span></span>

    - <span data-ttu-id="a74d1-152">將新的 FindPrivateKey 工具複製到此目錄。</span><span class="sxs-lookup"><span data-stu-id="a74d1-152">Copy the new FindPrivateKey tool to this directory.</span></span>

    <span data-ttu-id="a74d1-153">使用憑證且裝載在 IIS 中的範例需要這項工具。</span><span class="sxs-lookup"><span data-stu-id="a74d1-153">This tool is required by samples that use certificates and are hosted in IIS.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a74d1-154">基於安全性考量，在您完成範例後，請記得執行名為 Cleanupvroot.bat 的批次檔，移除虛擬目錄定義以及在上述安裝步驟中授與的權限。</span><span class="sxs-lookup"><span data-stu-id="a74d1-154">For security purposes, remember to remove the virtual directory definition and permissions granted in the setup steps above by running the batch file named Cleanupvroot.bat after you are finished with the samples.</span></span>

13. <span data-ttu-id="a74d1-155">自我裝載 (而非裝載於 IIS) 的範例必須有權限將 HTTP 位址註冊到電腦上，以便進行接聽。</span><span class="sxs-lookup"><span data-stu-id="a74d1-155">Samples that are self-hosted (not hosted in IIS) require permission to register HTTP addresses on the computer for listening.</span></span> <span data-ttu-id="a74d1-156">HTTP 命名空間保留區的權限來自用以執行範例的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="a74d1-156">The permission for an HTTP namespace reservation comes from the user account used to run the sample.</span></span> <span data-ttu-id="a74d1-157">根據預設，系統管理員帳戶擁有註冊任何 HTTP 位址的權限。</span><span class="sxs-lookup"><span data-stu-id="a74d1-157">By default, administrator accounts have the permission to register any HTTP address.</span></span> <span data-ttu-id="a74d1-158">至於非系統管理員帳戶，則必須具有範例所用之 HTTP 命名空間的權限。</span><span class="sxs-lookup"><span data-stu-id="a74d1-158">Non-administrator accounts must be granted permission for the HTTP namespaces used by the samples.</span></span> <span data-ttu-id="a74d1-159">如需如何設定命名空間保留的詳細資訊，請參閱[設定 HTTP 和 HTTPS](../feature-details/configuring-http-and-https.md)。</span><span class="sxs-lookup"><span data-stu-id="a74d1-159">For more information about how to configure namespace reservations, see [Configuring HTTP and HTTPS](../feature-details/configuring-http-and-https.md).</span></span>

14. <span data-ttu-id="a74d1-160">有些範例需要訊息佇列。</span><span class="sxs-lookup"><span data-stu-id="a74d1-160">Some samples require Message Queuing.</span></span> <span data-ttu-id="a74d1-161">有關安裝說明,請參閱[安裝消息佇列 (MSMQ)。](installing-message-queuing-msmq.md)</span><span class="sxs-lookup"><span data-stu-id="a74d1-161">See [Installing Message Queuing (MSMQ)](installing-message-queuing-msmq.md) for installation instructions.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a74d1-162">請務必在您執行需要訊息佇列的任何範例之前，啟動 MSMQ 服務。</span><span class="sxs-lookup"><span data-stu-id="a74d1-162">Ensure that you start the MSMQ service before you run any samples that require Message Queuing.</span></span>

15. <span data-ttu-id="a74d1-163">有些範例需要憑證。</span><span class="sxs-lookup"><span data-stu-id="a74d1-163">Some samples require certificates.</span></span> <span data-ttu-id="a74d1-164">請參考[網際網路資訊服務 (IIS) 伺服器憑證安裝說明](iis-server-certificate-installation-instructions.md)。</span><span class="sxs-lookup"><span data-stu-id="a74d1-164">See [Internet Information Services (IIS) Server Certificate Installation Instructions](iis-server-certificate-installation-instructions.md).</span></span>
