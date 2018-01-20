---
title: "如何：安裝及解除安裝服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, deploying
- services, uninstalling
- services, installing
- installing Windows Services
- uninstalling applications, Windows Services
- installation, Windows Services
- uninstalling Windows Services
- installutil.exe tool
ms.assetid: c89c5169-f567-4305-9d62-db31a1de5481
caps.latest.revision: "19"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 1fcbc8e7a84b16d244561e0cd69f8661236e63de
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-install-and-uninstall-services"></a><span data-ttu-id="f8fed-102">如何：安裝及解除安裝服務</span><span class="sxs-lookup"><span data-stu-id="f8fed-102">How to: Install and Uninstall Services</span></span>
<span data-ttu-id="f8fed-103">如果您正在使用 .NET Framework 開發 Windows 服務，您可以使用稱為 InstallUtil.exe 的命令列公用程式來快速安裝服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="f8fed-103">If you’re developing a Windows Service by using the .NET Framework, you can quickly install your service application by using a command-line utility called InstallUtil.exe.</span></span> <span data-ttu-id="f8fed-104">如果您是開發人員並且想發行使用者可安裝及解除安裝的 Windows 服務，則應該使用 InstallShield。</span><span class="sxs-lookup"><span data-stu-id="f8fed-104">If you’re a developer who wants to release a Windows Service that users can install and uninstall  you should use InstallShield.</span></span> <span data-ttu-id="f8fed-105">請參閱[Windows Installer 部署](http://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)。</span><span class="sxs-lookup"><span data-stu-id="f8fed-105">See [Windows Installer Deployment](http://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="f8fed-106">如果您想要從電腦解除安裝服務，則不要遵循本文中的步驟。</span><span class="sxs-lookup"><span data-stu-id="f8fed-106">If you want to uninstall a service from your computer, don’t follow the steps in this article.</span></span> <span data-ttu-id="f8fed-107">相反地，了解的程式或軟體套件安裝服務，然後選擇**新增/移除程式**在控制台中解除安裝該程式。</span><span class="sxs-lookup"><span data-stu-id="f8fed-107">Instead, find out which program or software package installed the service, and then choose **Add/Remove Programs** in Control Panel to uninstall that program.</span></span> <span data-ttu-id="f8fed-108">請注意，許多服務都是 Windows 不可或缺的一部分；如果移除這些服務，可能會導致系統不穩定。</span><span class="sxs-lookup"><span data-stu-id="f8fed-108">Note that many services are integral parts of Windows; if you remove them, you might cause system instability.</span></span>  
  
 <span data-ttu-id="f8fed-109">若要使用本文中的步驟，首先需要將服務安裝程式加入 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="f8fed-109">In order to use the steps in this article, you first need to add a service installer to your Windows Service.</span></span> <span data-ttu-id="f8fed-110">請參閱[逐步解說： 建立 Windows 服務元件設計工具中的應用程式](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="f8fed-110">See [Walkthrough: Creating a Windows Service Application in the Component Designer](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>  
  
 <span data-ttu-id="f8fed-111">您無法按下 F5，直接從 Visual Studio 開發環境中執行 Windows 服務專案。</span><span class="sxs-lookup"><span data-stu-id="f8fed-111">Windows Service projects cannot be run directly from the Visual Studio development environment by pressing F5.</span></span> <span data-ttu-id="f8fed-112">這是因為您必須先安裝專案中的服務，才可以執行專案。</span><span class="sxs-lookup"><span data-stu-id="f8fed-112">This is because the service in the project must be installed before you can run the project.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="f8fed-113">您可以啟動**伺服器總管**並確認您的服務已安裝或解除安裝。</span><span class="sxs-lookup"><span data-stu-id="f8fed-113">You can launch **Server Explorer** and verify that your service has been installed or uninstalled.</span></span> <span data-ttu-id="f8fed-114">如需詳細資訊，請參閱 < 如何： 存取及初始化伺服器總管資料庫總管。</span><span class="sxs-lookup"><span data-stu-id="f8fed-114">For more information, see How to: Access and Initialize Server Explorer-Database Explorer.</span></span>  
  
### <a name="to-install-your-service-manually"></a><span data-ttu-id="f8fed-115">以手動方式安裝您的服務</span><span class="sxs-lookup"><span data-stu-id="f8fed-115">To install your service manually</span></span>  
  
1.  <span data-ttu-id="f8fed-116">在 Windows**啟動**功能表或**啟動**畫面上，選擇**Visual Studio** ， **Visual Studio Tools**，**開發人員命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="f8fed-116">On the Windows **Start** menu or **Start** screen, choose **Visual Studio** , **Visual Studio Tools**, **Developer Command Prompt**.</span></span>  
  
     <span data-ttu-id="f8fed-117">Visual Studio 命令提示字元隨即出現。</span><span class="sxs-lookup"><span data-stu-id="f8fed-117">A Visual Studio command prompt appears.</span></span>  
  
2.  <span data-ttu-id="f8fed-118">存取您的專案已編譯之可執行檔所在的目錄。</span><span class="sxs-lookup"><span data-stu-id="f8fed-118">Access the directory where your project's compiled executable file is located.</span></span>  
  
3.  <span data-ttu-id="f8fed-119">從命令提示字元，以您專案的可執行檔做為參數來執行 InstallUtil.exe：</span><span class="sxs-lookup"><span data-stu-id="f8fed-119">Run InstallUtil.exe from the command prompt with your project's executable as a parameter:</span></span>  
  
    ```  
    installutil <yourproject>.exe  
    ```  
  
     <span data-ttu-id="f8fed-120">如果您使用 Visual Studio 命令提示字元，InstallUtil.exe 應該在系統路徑中。</span><span class="sxs-lookup"><span data-stu-id="f8fed-120">If you’re using the Visual Studio command prompt, InstallUtil.exe should be on the system path.</span></span> <span data-ttu-id="f8fed-121">如果不在，您可以將這個檔案加入路徑，或使用完整路徑來叫用這個檔案。</span><span class="sxs-lookup"><span data-stu-id="f8fed-121">If not, you can add it to the path, or use the fully qualified path to invoke it.</span></span> <span data-ttu-id="f8fed-122">這個工具會隨 .NET Framework 安裝，且其路徑為 `%WINDIR%\Microsoft.NET\Framework[64]\<framework_version>`。</span><span class="sxs-lookup"><span data-stu-id="f8fed-122">This tool is installed with the .NET Framework, and its path is `%WINDIR%\Microsoft.NET\Framework[64]\<framework_version>`.</span></span> <span data-ttu-id="f8fed-123">例如，針對 32 位元版本的 .NET Framework 4 或 4.5.\*，如果您的 Windows 安裝目錄是 C:\Windows，則路徑為 `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`。</span><span class="sxs-lookup"><span data-stu-id="f8fed-123">For example, for the 32-bit version of the .NET Framework 4 or 4.5.\*, if your Windows installation directory is C:\Windows, the path is `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`.</span></span> <span data-ttu-id="f8fed-124">64 位元版本的.NET Framework 4 或 4.5。\*，預設路徑是`C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe`。</span><span class="sxs-lookup"><span data-stu-id="f8fed-124">For the 64-bit version of the .NET Framework 4 or 4.5.\*, the default path is `C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe`.</span></span>  
  
### <a name="to-uninstall-your-service-manually"></a><span data-ttu-id="f8fed-125">以手動方式解除安裝您的服務</span><span class="sxs-lookup"><span data-stu-id="f8fed-125">To uninstall your service manually</span></span>  
  
1.  <span data-ttu-id="f8fed-126">在 Windows**啟動**功能表或**啟動**畫面上，選擇**Visual Studio**， **Visual Studio Tools**，**開發人員命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="f8fed-126">On the Windows **Start** menu or **Start** screen, choose **Visual Studio**, **Visual Studio Tools**, **Developer Command Prompt**.</span></span>  
  
     <span data-ttu-id="f8fed-127">Visual Studio 命令提示字元隨即出現。</span><span class="sxs-lookup"><span data-stu-id="f8fed-127">A Visual Studio command prompt appears.</span></span>  
  
2.  <span data-ttu-id="f8fed-128">從命令提示字元，以您專案的輸出做為參數來執行 InstallUtil.exe：</span><span class="sxs-lookup"><span data-stu-id="f8fed-128">Run InstallUtil.exe from the command prompt with your project's output as a parameter:</span></span>  
  
    ```  
    installutil /u <yourproject>.exe  
    ```  
  
3.  <span data-ttu-id="f8fed-129">有時候，刪除服務的可執行檔之後，服務可能還是會在登錄中。</span><span class="sxs-lookup"><span data-stu-id="f8fed-129">Sometimes, after the executable for a service is deleted, the service might still be present in the registry.</span></span> <span data-ttu-id="f8fed-130">在此情況下，使用命令[sc delete](http://technet.microsoft.com/library/cc742045.aspx)從登錄移除服務項目。</span><span class="sxs-lookup"><span data-stu-id="f8fed-130">In that case, use the command [sc delete](http://technet.microsoft.com/library/cc742045.aspx) to remove the entry for the service from the registry.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8fed-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="f8fed-131">See Also</span></span>  
 [<span data-ttu-id="f8fed-132">Windows 服務應用程式簡介</span><span class="sxs-lookup"><span data-stu-id="f8fed-132">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="f8fed-133">如何：建立 Windows 服務</span><span class="sxs-lookup"><span data-stu-id="f8fed-133">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [<span data-ttu-id="f8fed-134">如何：將 Installer 新增至服務應用程式</span><span class="sxs-lookup"><span data-stu-id="f8fed-134">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [<span data-ttu-id="f8fed-135">Installutil.exe (安裝程式工具)</span><span class="sxs-lookup"><span data-stu-id="f8fed-135">Installutil.exe (Installer Tool)</span></span>](../../../docs/framework/tools/installutil-exe-installer-tool.md)
