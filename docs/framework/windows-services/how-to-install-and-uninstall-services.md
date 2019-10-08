---
title: HOW TO：安裝和解除安裝 Windows 服務
ms.date: 02/05/2019
helpviewer_keywords:
- Windows Service applications, deploying
- services, uninstalling
- services, installing
- installing Windows Services
- uninstalling applications, apps, Windows services
- installation, Windows services
- uninstalling Windows services
- installutil.exe tool
ms.assetid: c89c5169-f567-4305-9d62-db31a1de5481
author: ghogen
ms.openlocfilehash: 38fc0172b5f97561d69fe495237e95597d7b9727
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003130"
---
# <a name="how-to-install-and-uninstall-windows-services"></a><span data-ttu-id="16cca-102">HOW TO：安裝和解除安裝 Windows 服務</span><span class="sxs-lookup"><span data-stu-id="16cca-102">How to: Install and uninstall Windows services</span></span>

<span data-ttu-id="16cca-103">如果您要使用 .NET Framework 開發 Windows 服務，您可以使用[*installutil.exe*](../tools/installutil-exe-installer-tool.md)命令列公用程式或[PowerShell](/powershell/scripting/overview)來快速安裝服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="16cca-103">If you’re developing a Windows service with the .NET Framework, you can quickly install your service app by using the [*InstallUtil.exe*](../tools/installutil-exe-installer-tool.md) command-line utility or [PowerShell](/powershell/scripting/overview).</span></span> <span data-ttu-id="16cca-104">開發人員若想發行使用者可安裝及解除安裝的 Windows 服務，則應該使用 InstallShield。</span><span class="sxs-lookup"><span data-stu-id="16cca-104">Developers who want to release a Windows service that users can install and uninstall should use InstallShield.</span></span> <span data-ttu-id="16cca-105">如需詳細資訊，請參閱[建立安裝程式套件 (Windows 用戶端)](https://docs.microsoft.com/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-client)。</span><span class="sxs-lookup"><span data-stu-id="16cca-105">For more information, see [Create an installer package (Windows client)](https://docs.microsoft.com/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-client).</span></span>

> [!WARNING]
> <span data-ttu-id="16cca-106">如果您想要從電腦解除安裝服務，則不要遵循本文中的步驟。</span><span class="sxs-lookup"><span data-stu-id="16cca-106">If you want to uninstall a service from your computer, don’t follow the steps in this article.</span></span> <span data-ttu-id="16cca-107">請改為找出安裝服務的程式或軟體套件，然後在 [設定] 中選擇 [應用程式] 以解除安裝該程式。</span><span class="sxs-lookup"><span data-stu-id="16cca-107">Instead, find out which program or software package installed the service, and then choose **Apps** in Settings to uninstall that program.</span></span> <span data-ttu-id="16cca-108">請注意，許多服務都是 Windows 不可或缺的一部分；如果移除這些服務，可能會導致系統不穩定。</span><span class="sxs-lookup"><span data-stu-id="16cca-108">Note that many services are integral parts of Windows; if you remove them, you might cause system instability.</span></span>

<span data-ttu-id="16cca-109">若要使用本文中的步驟，首先需要將服務安裝程式新增至 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="16cca-109">To use the steps in this article, you first need to add a service installer to your Windows service.</span></span> <span data-ttu-id="16cca-110">如需詳細資訊，請參閱[逐步解說：建立 Windows 服務應用程式](../windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="16cca-110">For more information, see [Walkthrough: Creating a Windows service app](../windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>

<span data-ttu-id="16cca-111">您無法按下 F5，直接從 Visual Studio 開發環境中執行 Windows 服務專案。</span><span class="sxs-lookup"><span data-stu-id="16cca-111">You can't run Windows service projects directly from the Visual Studio development environment by pressing F5.</span></span> <span data-ttu-id="16cca-112">您必須先安裝專案中的服務，才可以執行專案。</span><span class="sxs-lookup"><span data-stu-id="16cca-112">Before you can run the project, you must install the service in the project.</span></span>

> [!TIP]
> <span data-ttu-id="16cca-113">您可以使用 [伺服器總管] 來確認您已安裝或解除安裝服務。</span><span class="sxs-lookup"><span data-stu-id="16cca-113">You can use **Server Explorer** to verify that you've installed or uninstalled your service.</span></span> <span data-ttu-id="16cca-114">如需詳細資訊，請參閱 [How to use Server Explorer in Visual Studio](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio) (如何在 Visual Studio 中使用伺服器總管)。</span><span class="sxs-lookup"><span data-stu-id="16cca-114">For more information, see [How to use Server Explorer in Visual Studio](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).</span></span>

### <a name="install-your-service-manually-using-installutilexe-utility"></a><span data-ttu-id="16cca-115">使用 Installutil.exe 公用程式手動安裝您的服務</span><span class="sxs-lookup"><span data-stu-id="16cca-115">Install your service manually using InstallUtil.exe utility</span></span>

1. <span data-ttu-id="16cca-116">從 [開始] 功能表，選取 [Visual Studio \<版本>] 目錄，然後選取 [VS \<版本> 開發人員命令提示字元]。</span><span class="sxs-lookup"><span data-stu-id="16cca-116">From the **Start** menu, select the **Visual Studio \<*version*>** directory, then select **Developer Command Prompt for VS \<*version*>**.</span></span>

     <span data-ttu-id="16cca-117">隨即顯示 Visual Studio 開發人員命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="16cca-117">The Developer Command Prompt for Visual Studio appears.</span></span>

2. <span data-ttu-id="16cca-118">存取您的專案已編譯之可執行檔所在的目錄。</span><span class="sxs-lookup"><span data-stu-id="16cca-118">Access the directory where your project's compiled executable file is located.</span></span>

3. <span data-ttu-id="16cca-119">從命令提示字元，以您專案的可執行檔作為參數來執行 *InstallUtil.exe*：</span><span class="sxs-lookup"><span data-stu-id="16cca-119">Run *InstallUtil.exe* from the command prompt with your project's executable as a parameter:</span></span>

    ```console
    installutil <yourproject>.exe
    ```

     <span data-ttu-id="16cca-120">如果您使用 Visual Studio 開發人員命令提示字元，*InstallUtil.exe* 應該位在系統路徑中。</span><span class="sxs-lookup"><span data-stu-id="16cca-120">If you’re using the Developer Command Prompt for Visual Studio, *InstallUtil.exe* should be on the system path.</span></span> <span data-ttu-id="16cca-121">否則，您可以將這個檔案新增至路徑，或使用完整路徑來叫用這個檔案。</span><span class="sxs-lookup"><span data-stu-id="16cca-121">Otherwise, you can add it to the path, or use the fully qualified path to invoke it.</span></span> <span data-ttu-id="16cca-122">此工具會透過 .NET Framework 安裝至 *%WINDIR%\Microsoft.NET\Framework[64]\\<framework_version\>* 。</span><span class="sxs-lookup"><span data-stu-id="16cca-122">This tool is installed with the .NET Framework in *%WINDIR%\Microsoft.NET\Framework[64]\\<framework_version\>*.</span></span>

     <span data-ttu-id="16cca-123">例如:</span><span class="sxs-lookup"><span data-stu-id="16cca-123">For example:</span></span>
     - <span data-ttu-id="16cca-124">針對 32 位元版本的 .NET Framework 4 或 4.5 和更新版本，如果您的 Windows 安裝目錄是 *C:\Windows*，則預設路徑為 *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*。</span><span class="sxs-lookup"><span data-stu-id="16cca-124">For the 32-bit version of the .NET Framework 4 or 4.5 and later, if your Windows installation directory is *C:\Windows*, the default path is *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.</span></span>
     - <span data-ttu-id="16cca-125">針對 64 位元版本的 .NET Framework 4 或 4.5 和更新版本，預設路徑為 *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*。</span><span class="sxs-lookup"><span data-stu-id="16cca-125">For the 64-bit version of the .NET Framework 4 or 4.5 and later, the default path is *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span></span>

### <a name="uninstall-your-service-manually-using-installutilexe-utility"></a><span data-ttu-id="16cca-126">使用 Installutil.exe 公用程式手動卸載您的服務</span><span class="sxs-lookup"><span data-stu-id="16cca-126">Uninstall your service manually using InstallUtil.exe utility</span></span>

1. <span data-ttu-id="16cca-127">從 [開始] 功能表，選取 [Visual Studio \<版本>] 目錄，然後選取 [VS \<版本> 開發人員命令提示字元]。</span><span class="sxs-lookup"><span data-stu-id="16cca-127">From the **Start** menu, select the **Visual Studio \<*version*>** directory, then select **Developer Command Prompt for VS \<*version*>**.</span></span>

     <span data-ttu-id="16cca-128">隨即顯示 Visual Studio 開發人員命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="16cca-128">The Developer Command Prompt for Visual Studio appears.</span></span>

2. <span data-ttu-id="16cca-129">從命令提示字元，以您專案的輸出作為參數來執行 *InstallUtil.exe*：</span><span class="sxs-lookup"><span data-stu-id="16cca-129">Run *InstallUtil.exe* from the command prompt with your project's output as a parameter:</span></span>

    ```console
    installutil /u <yourproject>.exe
    ```

3. <span data-ttu-id="16cca-130">刪除服務的可執行檔之後，服務可能還是會在登錄中。</span><span class="sxs-lookup"><span data-stu-id="16cca-130">After the executable for a service is deleted, the service might still be present in the registry.</span></span> <span data-ttu-id="16cca-131">如果是這種情況，請使用命令 [sc delete](/windows-server/administration/windows-commands/sc-delete) 來從登錄中移除服務項目。</span><span class="sxs-lookup"><span data-stu-id="16cca-131">If that's the case, use the command [sc delete](/windows-server/administration/windows-commands/sc-delete) to remove the entry for the service from the registry.</span></span>

### <a name="install-your-service-manually-using-powershell"></a><span data-ttu-id="16cca-132">使用 PowerShell 手動安裝您的服務</span><span class="sxs-lookup"><span data-stu-id="16cca-132">Install your service manually using PowerShell</span></span>

1. <span data-ttu-id="16cca-133">從 [**開始**] 功能表中，選取 [ **windows powershell** ] 目錄，然後選取 [ **windows powershell**]。</span><span class="sxs-lookup"><span data-stu-id="16cca-133">From the **Start** menu, select the **Windows PowerShell** directory, then select **Windows PowerShell**.</span></span>

2. <span data-ttu-id="16cca-134">存取您的專案已編譯之可執行檔所在的目錄。</span><span class="sxs-lookup"><span data-stu-id="16cca-134">Access the directory where your project's compiled executable file is located.</span></span>

3. <span data-ttu-id="16cca-135">使用搭配專案的輸出和服務名稱作為參數，執行[**新的-Service**](/powershell/module/microsoft.powershell.management/new-service) Cmdlet：</span><span class="sxs-lookup"><span data-stu-id="16cca-135">Run the [**New-Service**](/powershell/module/microsoft.powershell.management/new-service) cmdlet with the with your project's output and a service name as parameters:</span></span>

    ```powershell
    New-Service -Name "YourServiceName" -BinaryPathName <yourproject>.exe
    ```

### <a name="uninstall-your-service-manually-using-powershell"></a><span data-ttu-id="16cca-136">使用 PowerShell 手動卸載您的服務</span><span class="sxs-lookup"><span data-stu-id="16cca-136">Uninstall your service manually using PowerShell</span></span>

1. <span data-ttu-id="16cca-137">從 [**開始**] 功能表中，選取 [ **windows powershell** ] 目錄，然後選取 [ **windows powershell**]。</span><span class="sxs-lookup"><span data-stu-id="16cca-137">From the **Start** menu, select the **Windows PowerShell** directory, then select **Windows PowerShell**.</span></span>

2. <span data-ttu-id="16cca-138">使用您的服務名稱作為參數來執行[**Remove-Service**](/powershell/module/microsoft.powershell.management/remove-service) Cmdlet：</span><span class="sxs-lookup"><span data-stu-id="16cca-138">Run the [**Remove-Service**](/powershell/module/microsoft.powershell.management/remove-service) cmdlet with the name of your service as parameter:</span></span>

    ```powershell
    Remove-Service -Name "YourServiceName"
    ```

3. <span data-ttu-id="16cca-139">刪除服務的可執行檔之後，服務可能還是會在登錄中。</span><span class="sxs-lookup"><span data-stu-id="16cca-139">After the executable for a service is deleted, the service might still be present in the registry.</span></span> <span data-ttu-id="16cca-140">如果是這種情況，請使用命令 [sc delete](/windows-server/administration/windows-commands/sc-delete) 來從登錄中移除服務項目。</span><span class="sxs-lookup"><span data-stu-id="16cca-140">If that's the case, use the command [sc delete](/windows-server/administration/windows-commands/sc-delete) to remove the entry for the service from the registry.</span></span>

    ```powershell
    sc.exe delete "YourServiceName"
    ```

## <a name="see-also"></a><span data-ttu-id="16cca-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16cca-141">See also</span></span>

- [<span data-ttu-id="16cca-142">Windows 服務應用程式簡介</span><span class="sxs-lookup"><span data-stu-id="16cca-142">Introduction to Windows service applications</span></span>](../windows-services/introduction-to-windows-service-applications.md)
- [<span data-ttu-id="16cca-143">如何：建立 Windows 服務</span><span class="sxs-lookup"><span data-stu-id="16cca-143">How to: Create Windows services</span></span>](../windows-services/how-to-create-windows-services.md)
- [<span data-ttu-id="16cca-144">如何：將安裝程式新增至服務應用程式</span><span class="sxs-lookup"><span data-stu-id="16cca-144">How to: Add installers to your service application</span></span>](../windows-services/how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="16cca-145">Installutil.exe (安裝程式工具)</span><span class="sxs-lookup"><span data-stu-id="16cca-145">Installutil.exe (Installer tool)</span></span>](../tools/installutil-exe-installer-tool.md)
