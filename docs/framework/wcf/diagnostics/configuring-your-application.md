---
title: 設定您的應用程式
ms.date: 03/30/2017
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
ms.openlocfilehash: 1844c20ef961f191fb667e31d548518b193a7134
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803646"
---
# <a name="configuring-your-application"></a><span data-ttu-id="1eca2-102">設定您的應用程式</span><span class="sxs-lookup"><span data-stu-id="1eca2-102">Configuring Your Application</span></span>
<span data-ttu-id="1eca2-103">Windows Communication Foundation (WCF) 會使用.NET 組態系統，並可讓您設定服務在電腦和應用程式的範圍。</span><span class="sxs-lookup"><span data-stu-id="1eca2-103">Windows Communication Foundation (WCF) uses the .NET configuration system and allows you to configure services at both the machine and application scope.</span></span>  
  
 <span data-ttu-id="1eca2-104">WCF 所定義的組態設定位於`<system.serviceModel>`區段群組。</span><span class="sxs-lookup"><span data-stu-id="1eca2-104">Configuration settings defined by WCF are located in the `<system.serviceModel>` section group.</span></span> <span data-ttu-id="1eca2-105">如需如何設定 WCF 服務的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="1eca2-105">For more information about how to configure a WCF service, see the following topics:</span></span>  
  
-   [<span data-ttu-id="1eca2-106">設定服務</span><span class="sxs-lookup"><span data-stu-id="1eca2-106">Configuring Services</span></span>](../../../../docs/framework/wcf/configuring-services.md)  
  
-   [<span data-ttu-id="1eca2-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1eca2-107">\<system.serviceModel></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 <span data-ttu-id="1eca2-108">應用程式定義的組態設定會定義在 `<appSettings>` 節群組中。</span><span class="sxs-lookup"><span data-stu-id="1eca2-108">Application-defined configurations settings are defined in the `<appSettings>` section group.</span></span> <span data-ttu-id="1eca2-109">如需.NET 組態檔中的應用程式設定的詳細資訊，請參閱[ \<appSettings >](http://go.microsoft.com/fwlink/?LinkId=95159)。</span><span class="sxs-lookup"><span data-stu-id="1eca2-109">For more information about application settings in .NET configuration files, see [\<appSettings>](http://go.microsoft.com/fwlink/?LinkId=95159).</span></span>  
  
## <a name="using-the-configuration-editor"></a><span data-ttu-id="1eca2-110">使用組態編輯器</span><span class="sxs-lookup"><span data-stu-id="1eca2-110">Using the Configuration Editor</span></span>  
 <span data-ttu-id="1eca2-111">WCF[組態編輯器工具 (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)可讓管理員和開發人員建立及修改 WCF 服務使用圖形化使用者介面的組態設定。</span><span class="sxs-lookup"><span data-stu-id="1eca2-111">The WCF[Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) allows administrators and developers to create and modify configuration settings for WCF services using a graphical user interface.</span></span> <span data-ttu-id="1eca2-112">使用這個工具，您可以管理設定 WCF 繫結、 行為、 服務和診斷，而不用直接編輯 XML 組態檔。</span><span class="sxs-lookup"><span data-stu-id="1eca2-112">With this tool, you can manage settings for WCF bindings, behaviors, services, and diagnostics without directly editing XML configuration files.</span></span>  
  
## <a name="editing-configuration-files-in-visual-studio"></a><span data-ttu-id="1eca2-113">在 Visual Studio 中編輯組態檔</span><span class="sxs-lookup"><span data-stu-id="1eca2-113">Editing Configuration Files in Visual Studio</span></span>  
 <span data-ttu-id="1eca2-114">若要編輯的 Visual Studio 中的 WCF 服務專案的組態檔，以滑鼠右鍵按一下 [**方案總管] 中**選擇**編輯 WCF 組態**操作功能表項目。</span><span class="sxs-lookup"><span data-stu-id="1eca2-114">To edit the configuration file of a WCF service project in Visual Studio, right click it in **Solution Explorer** and choose the **Edit WCF Config** context menu item.</span></span> <span data-ttu-id="1eca2-115">這會啟動[組態編輯器工具 (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="1eca2-115">This launches the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1eca2-116">如果您編輯 Visual Studio 中的 WCF Web 服務專案的組態檔，以滑鼠右鍵按一下它在**方案總管 中**，請注意，**編輯 WCF 組態**操作功能表項目已遺失。</span><span class="sxs-lookup"><span data-stu-id="1eca2-116">If you edit the configuration file of a WCF Web Service project in Visual Studio by right-clicking it in **Solution Explorer**, notice that the **Edit WCF Config** context menu item is missing.</span></span> <span data-ttu-id="1eca2-117">若要解決這個問題，請按一下**工具**功能表上，選擇  **WCF 服務組態編輯器**。</span><span class="sxs-lookup"><span data-stu-id="1eca2-117">To workaround this issue, click the **Tools** menu, and choose **WCF Service Config Editor**.</span></span> <span data-ttu-id="1eca2-118">在這之後，您可以以滑鼠右鍵按一下組態檔，並使用**編輯 WCF 組態**操作功能表項目。</span><span class="sxs-lookup"><span data-stu-id="1eca2-118">After that, you can right-click a configuration file and use the **Edit WCF Config** context menu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1eca2-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1eca2-119">See Also</span></span>  
 [<span data-ttu-id="1eca2-120">設定編輯器工具 (SvcConfigEditor.exe)</span><span class="sxs-lookup"><span data-stu-id="1eca2-120">Configuration Editor Tool (SvcConfigEditor.exe)</span></span>](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
 [<span data-ttu-id="1eca2-121">設定服務</span><span class="sxs-lookup"><span data-stu-id="1eca2-121">Configuring Services</span></span>](../../../../docs/framework/wcf/configuring-services.md)  
 [<span data-ttu-id="1eca2-122">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1eca2-122">\<system.serviceModel></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)
