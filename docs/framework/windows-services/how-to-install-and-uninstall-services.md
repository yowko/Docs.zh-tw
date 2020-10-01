---
title: 如何：安裝和卸載 Windows 服務
description: 請參閱如何安裝和卸載 Windows 服務。 如果您是使用 .NET 開發 Windows 服務，您可以使用 InstallUtil.exe 或 PowerShell。
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
ms.openlocfilehash: 6b7cfd8b241df4fe01c9c2a08888c88a1c749d13
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609677"
---
# <a name="how-to-install-and-uninstall-windows-services"></a><span data-ttu-id="45850-104">如何：安裝和卸載 Windows 服務</span><span class="sxs-lookup"><span data-stu-id="45850-104">How to: Install and uninstall Windows services</span></span>

<span data-ttu-id="45850-105">如果您要使用 .NET Framework 開發 Windows 服務，您可以使用 [*InstallUtil.exe*](../tools/installutil-exe-installer-tool.md) 命令列公用程式或 [PowerShell](/powershell/scripting/overview)來快速安裝服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="45850-105">If you’re developing a Windows service with the .NET Framework, you can quickly install your service app by using the [*InstallUtil.exe*](../tools/installutil-exe-installer-tool.md) command-line utility or [PowerShell](/powershell/scripting/overview).</span></span> <span data-ttu-id="45850-106">如果開發人員想要發行使用者可以安裝和卸載的 Windows 服務，則可以使用免費的 [WiX 工具](https://wixtoolset.org/) 組或商業工具，例如 [Advanced Installer](https://www.advancedinstaller.com/)、 [InstallShield](https://www.revenera.com/install/products/installshield.html)或其他工具。</span><span class="sxs-lookup"><span data-stu-id="45850-106">Developers who want to release a Windows service that users can install and uninstall can use the free [WiX Toolset](https://wixtoolset.org/) or commercial tools like [Advanced Installer](https://www.advancedinstaller.com/), [InstallShield](https://www.revenera.com/install/products/installshield.html), or others.</span></span> <span data-ttu-id="45850-107">如需詳細資訊，請參閱 [ (Windows 桌面) 建立安裝程式套件 ](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop)。</span><span class="sxs-lookup"><span data-stu-id="45850-107">For more information, see [Create an installer package (Windows desktop)](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).</span></span>

> [!WARNING]
> <span data-ttu-id="45850-108">如果您想要從電腦解除安裝服務，則不要遵循本文中的步驟。</span><span class="sxs-lookup"><span data-stu-id="45850-108">If you want to uninstall a service from your computer, don’t follow the steps in this article.</span></span> <span data-ttu-id="45850-109">請改為找出安裝服務的程式或軟體套件，然後在 [設定] 中選擇 [應用程式]\*\*\*\* 以解除安裝該程式。</span><span class="sxs-lookup"><span data-stu-id="45850-109">Instead, find out which program or software package installed the service, and then choose **Apps** in Settings to uninstall that program.</span></span> <span data-ttu-id="45850-110">請注意，許多服務都是 Windows 不可或缺的一部分；如果移除這些服務，可能會導致系統不穩定。</span><span class="sxs-lookup"><span data-stu-id="45850-110">Note that many services are integral parts of Windows; if you remove them, you might cause system instability.</span></span>

<span data-ttu-id="45850-111">若要使用本文中的步驟，首先需要將服務安裝程式新增至 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="45850-111">To use the steps in this article, you first need to add a service installer to your Windows service.</span></span> <span data-ttu-id="45850-112">如需詳細資訊，請參閱 [逐步解說：建立 Windows 服務應用程式](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="45850-112">For more information, see [Walkthrough: Creating a Windows service app](walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>

<span data-ttu-id="45850-113">您無法按下 F5，直接從 Visual Studio 開發環境中執行 Windows 服務專案。</span><span class="sxs-lookup"><span data-stu-id="45850-113">You can't run Windows service projects directly from the Visual Studio development environment by pressing F5.</span></span> <span data-ttu-id="45850-114">您必須先安裝專案中的服務，才可以執行專案。</span><span class="sxs-lookup"><span data-stu-id="45850-114">Before you can run the project, you must install the service in the project.</span></span>

> [!TIP]
> <span data-ttu-id="45850-115">您可以使用 [伺服器總管]\*\*\*\* 來確認您已安裝或解除安裝服務。</span><span class="sxs-lookup"><span data-stu-id="45850-115">You can use **Server Explorer** to verify that you've installed or uninstalled your service.</span></span> <span data-ttu-id="45850-116">如需詳細資訊，請參閱 [How to use Server Explorer in Visual Studio](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio) (如何在 Visual Studio 中使用伺服器總管)。</span><span class="sxs-lookup"><span data-stu-id="45850-116">For more information, see [How to use Server Explorer in Visual Studio](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).</span></span>

### <a name="install-your-service-manually-using-installutilexe-utility"></a><span data-ttu-id="45850-117">使用 InstallUtil.exe 公用程式以手動方式安裝您的服務</span><span class="sxs-lookup"><span data-stu-id="45850-117">Install your service manually using InstallUtil.exe utility</span></span>

1. <span data-ttu-id="45850-118">從 [**開始**] 功能表選取\*\* \<*version*> Visual Studio\*\*目錄，然後選取 [ **VS \<*version*> ] 開發人員命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="45850-118">From the **Start** menu, select the **Visual Studio \<*version*>** directory, then select **Developer Command Prompt for VS \<*version*>**.</span></span>

     <span data-ttu-id="45850-119">隨即顯示 Visual Studio 開發人員命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="45850-119">The Developer Command Prompt for Visual Studio appears.</span></span>

2. <span data-ttu-id="45850-120">存取您的專案已編譯之可執行檔所在的目錄。</span><span class="sxs-lookup"><span data-stu-id="45850-120">Access the directory where your project's compiled executable file is located.</span></span>

3. <span data-ttu-id="45850-121">從命令提示字元，以您專案的可執行檔作為參數來執行 *InstallUtil.exe*：</span><span class="sxs-lookup"><span data-stu-id="45850-121">Run *InstallUtil.exe* from the command prompt with your project's executable as a parameter:</span></span>

    ```console
    installutil <yourproject>.exe
    ```

     <span data-ttu-id="45850-122">如果您使用 Visual Studio 開發人員命令提示字元，*InstallUtil.exe* 應該位在系統路徑中。</span><span class="sxs-lookup"><span data-stu-id="45850-122">If you’re using the Developer Command Prompt for Visual Studio, *InstallUtil.exe* should be on the system path.</span></span> <span data-ttu-id="45850-123">否則，您可以將這個檔案新增至路徑，或使用完整路徑來叫用這個檔案。</span><span class="sxs-lookup"><span data-stu-id="45850-123">Otherwise, you can add it to the path, or use the fully qualified path to invoke it.</span></span> <span data-ttu-id="45850-124">此工具會隨 .NET Framework 安裝在 \*%WINDIR%\Microsoft.NET\Framework [64] \\<framework_version \> \*中。</span><span class="sxs-lookup"><span data-stu-id="45850-124">This tool is installed with the .NET Framework in *%WINDIR%\Microsoft.NET\Framework[64]\\<framework_version\>*.</span></span>

     <span data-ttu-id="45850-125">例如：</span><span class="sxs-lookup"><span data-stu-id="45850-125">For example:</span></span>
     - <span data-ttu-id="45850-126">針對 32 位元版本的 .NET Framework 4 或 4.5 和更新版本，如果您的 Windows 安裝目錄是 *C:\Windows*，則預設路徑為 *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*。</span><span class="sxs-lookup"><span data-stu-id="45850-126">For the 32-bit version of the .NET Framework 4 or 4.5 and later, if your Windows installation directory is *C:\Windows*, the default path is *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.</span></span>
     - <span data-ttu-id="45850-127">針對 64 位元版本的 .NET Framework 4 或 4.5 和更新版本，預設路徑為 *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*。</span><span class="sxs-lookup"><span data-stu-id="45850-127">For the 64-bit version of the .NET Framework 4 or 4.5 and later, the default path is *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span></span>

### <a name="uninstall-your-service-manually-using-installutilexe-utility"></a><span data-ttu-id="45850-128">使用 InstallUtil.exe 公用程式以手動方式卸載您的服務</span><span class="sxs-lookup"><span data-stu-id="45850-128">Uninstall your service manually using InstallUtil.exe utility</span></span>

1. <span data-ttu-id="45850-129">從 [**開始**] 功能表選取\*\* \<*version*> Visual Studio\*\*目錄，然後選取 [ **VS \<*version*> ] 開發人員命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="45850-129">From the **Start** menu, select the **Visual Studio \<*version*>** directory, then select **Developer Command Prompt for VS \<*version*>**.</span></span>

     <span data-ttu-id="45850-130">隨即顯示 Visual Studio 開發人員命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="45850-130">The Developer Command Prompt for Visual Studio appears.</span></span>

2. <span data-ttu-id="45850-131">從命令提示字元，以您專案的輸出作為參數來執行 *InstallUtil.exe*：</span><span class="sxs-lookup"><span data-stu-id="45850-131">Run *InstallUtil.exe* from the command prompt with your project's output as a parameter:</span></span>

    ```console
    installutil /u <yourproject>.exe
    ```

3. <span data-ttu-id="45850-132">刪除服務的可執行檔之後，服務可能還是會在登錄中。</span><span class="sxs-lookup"><span data-stu-id="45850-132">After the executable for a service is deleted, the service might still be present in the registry.</span></span> <span data-ttu-id="45850-133">如果是這種情況，請使用命令 [sc delete](/windows-server/administration/windows-commands/sc-delete) 來從登錄中移除服務項目。</span><span class="sxs-lookup"><span data-stu-id="45850-133">If that's the case, use the command [sc delete](/windows-server/administration/windows-commands/sc-delete) to remove the entry for the service from the registry.</span></span>

### <a name="install-your-service-manually-using-powershell"></a><span data-ttu-id="45850-134">使用 PowerShell 以手動方式安裝您的服務</span><span class="sxs-lookup"><span data-stu-id="45850-134">Install your service manually using PowerShell</span></span>

1. <span data-ttu-id="45850-135">從 [ **開始** ] 功能表選取 **Windows PowerShell** 目錄，然後選取 [ **Windows PowerShell**]。</span><span class="sxs-lookup"><span data-stu-id="45850-135">From the **Start** menu, select the **Windows PowerShell** directory, then select **Windows PowerShell**.</span></span>

2. <span data-ttu-id="45850-136">存取您的專案已編譯之可執行檔所在的目錄。</span><span class="sxs-lookup"><span data-stu-id="45850-136">Access the directory where your project's compiled executable file is located.</span></span>

3. <span data-ttu-id="45850-137">使用專案的輸出和服務名稱作為參數執行 [**新的-服務**](/powershell/module/microsoft.powershell.management/new-service) Cmdlet：</span><span class="sxs-lookup"><span data-stu-id="45850-137">Run the [**New-Service**](/powershell/module/microsoft.powershell.management/new-service) cmdlet with the with your project's output and a service name as parameters:</span></span>

    ```powershell
    New-Service -Name "YourServiceName" -BinaryPathName <yourproject>.exe
    ```

### <a name="uninstall-your-service-manually-using-powershell"></a><span data-ttu-id="45850-138">使用 PowerShell 以手動方式卸載您的服務</span><span class="sxs-lookup"><span data-stu-id="45850-138">Uninstall your service manually using PowerShell</span></span>

1. <span data-ttu-id="45850-139">從 [ **開始** ] 功能表選取 **Windows PowerShell** 目錄，然後選取 [ **Windows PowerShell**]。</span><span class="sxs-lookup"><span data-stu-id="45850-139">From the **Start** menu, select the **Windows PowerShell** directory, then select **Windows PowerShell**.</span></span>

2. <span data-ttu-id="45850-140">以您的服務名稱作為參數執行 [**移除服務**](/powershell/module/microsoft.powershell.management/remove-service) Cmdlet：</span><span class="sxs-lookup"><span data-stu-id="45850-140">Run the [**Remove-Service**](/powershell/module/microsoft.powershell.management/remove-service) cmdlet with the name of your service as parameter:</span></span>

    ```powershell
    Remove-Service -Name "YourServiceName"
    ```

3. <span data-ttu-id="45850-141">刪除服務的可執行檔之後，服務可能還是會在登錄中。</span><span class="sxs-lookup"><span data-stu-id="45850-141">After the executable for a service is deleted, the service might still be present in the registry.</span></span> <span data-ttu-id="45850-142">如果是這種情況，請使用命令 [sc delete](/windows-server/administration/windows-commands/sc-delete) 來從登錄中移除服務項目。</span><span class="sxs-lookup"><span data-stu-id="45850-142">If that's the case, use the command [sc delete](/windows-server/administration/windows-commands/sc-delete) to remove the entry for the service from the registry.</span></span>

    ```powershell
    sc.exe delete "YourServiceName"
    ```

## <a name="see-also"></a><span data-ttu-id="45850-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45850-143">See also</span></span>

- [<span data-ttu-id="45850-144">Windows 服務應用程式簡介</span><span class="sxs-lookup"><span data-stu-id="45850-144">Introduction to Windows service applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="45850-145">如何：建立 Windows 服務</span><span class="sxs-lookup"><span data-stu-id="45850-145">How to: Create Windows services</span></span>](how-to-create-windows-services.md)
- [<span data-ttu-id="45850-146">如何：將安裝程式新增至服務應用程式</span><span class="sxs-lookup"><span data-stu-id="45850-146">How to: Add installers to your service application</span></span>](how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="45850-147">Installutil.exe (安裝程式工具) </span><span class="sxs-lookup"><span data-stu-id="45850-147">Installutil.exe (Installer tool)</span></span>](../tools/installutil-exe-installer-tool.md)
