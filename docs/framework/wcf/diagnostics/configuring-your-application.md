---
title: 設定您的應用程式
ms.date: 03/30/2017
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
ms.openlocfilehash: 6fc33e7b114bb78f823575a2b456d601ae75db94
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937634"
---
# <a name="configuring-your-application"></a><span data-ttu-id="84602-102">設定您的應用程式</span><span class="sxs-lookup"><span data-stu-id="84602-102">Configuring Your Application</span></span>
<span data-ttu-id="84602-103">Windows Communication Foundation （WCF）會使用 .NET 設定系統，並可讓您在電腦和應用程式範圍中設定服務。</span><span class="sxs-lookup"><span data-stu-id="84602-103">Windows Communication Foundation (WCF) uses the .NET configuration system and allows you to configure services at both the machine and application scope.</span></span>  
  
 <span data-ttu-id="84602-104">WCF 所定義的 Configuration 設定位於 `<system.serviceModel>` 區段群組中。</span><span class="sxs-lookup"><span data-stu-id="84602-104">Configuration settings defined by WCF are located in the `<system.serviceModel>` section group.</span></span> <span data-ttu-id="84602-105">如需有關如何設定 WCF 服務的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="84602-105">For more information about how to configure a WCF service, see the following topics:</span></span>  
  
- [<span data-ttu-id="84602-106">設定服務</span><span class="sxs-lookup"><span data-stu-id="84602-106">Configuring Services</span></span>](../configuring-services.md)  
  
- [<span data-ttu-id="84602-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="84602-107">\<system.serviceModel></span></span>](../../configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 <span data-ttu-id="84602-108">應用程式定義的組態設定會定義在 `<appSettings>` 節群組中。</span><span class="sxs-lookup"><span data-stu-id="84602-108">Application-defined configurations settings are defined in the `<appSettings>` section group.</span></span> <span data-ttu-id="84602-109">如需 .NET 設定檔中應用程式設定的詳細資訊，請參閱[\<appSettings >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms228154(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="84602-109">For more information about application settings in .NET configuration files, see [\<appSettings>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms228154(v=vs.100)).</span></span>  
  
## <a name="using-the-configuration-editor"></a><span data-ttu-id="84602-110">使用組態編輯器</span><span class="sxs-lookup"><span data-stu-id="84602-110">Using the Configuration Editor</span></span>  
 <span data-ttu-id="84602-111">[WCF 設定[編輯器] 工具（svcconfigeditor.exe）](../configuration-editor-tool-svcconfigeditor-exe.md)可讓系統管理員和開發人員使用圖形化使用者介面來建立和修改 WCF 服務的設定。</span><span class="sxs-lookup"><span data-stu-id="84602-111">The WCF [Configuration Editor Tool (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md) allows administrators and developers to create and modify configuration settings for WCF services using a graphical user interface.</span></span> <span data-ttu-id="84602-112">使用此工具，您可以管理 WCF 系結、行為、服務及診斷的設定，而不需要直接編輯 XML 設定檔。</span><span class="sxs-lookup"><span data-stu-id="84602-112">With this tool, you can manage settings for WCF bindings, behaviors, services, and diagnostics without directly editing XML configuration files.</span></span>  
  
## <a name="editing-configuration-files-in-visual-studio"></a><span data-ttu-id="84602-113">在 Visual Studio 中編輯組態檔</span><span class="sxs-lookup"><span data-stu-id="84602-113">Editing Configuration Files in Visual Studio</span></span>  
 <span data-ttu-id="84602-114">若要在 Visual Studio 中編輯 WCF 服務專案的設定檔，請在**方案總管**中按一下滑鼠右鍵，然後選擇 [**編輯 WCF**設定] 內容功能表項目。</span><span class="sxs-lookup"><span data-stu-id="84602-114">To edit the configuration file of a WCF service project in Visual Studio, right click it in **Solution Explorer** and choose the **Edit WCF Config** context menu item.</span></span> <span data-ttu-id="84602-115">這會啟動設定[編輯器工具（svcconfigeditor.exe .exe）](../configuration-editor-tool-svcconfigeditor-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="84602-115">This launches the [Configuration Editor Tool (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="84602-116">如果您在**方案總管**中以滑鼠右鍵按一下 WCF Web 服務 Visual Studio 專案的設定檔案，請注意 [**編輯 wcf**設定] 內容功能表項目已遺失。</span><span class="sxs-lookup"><span data-stu-id="84602-116">If you edit the configuration file of a WCF Web Service project in Visual Studio by right-clicking it in **Solution Explorer**, notice that the **Edit WCF Config** context menu item is missing.</span></span> <span data-ttu-id="84602-117">若要解決此問題，請按一下 [**工具**] 功能表，然後選擇 [ **WCF 服務設定編輯器**]。</span><span class="sxs-lookup"><span data-stu-id="84602-117">To workaround this issue, click the **Tools** menu, and choose **WCF Service Config Editor**.</span></span> <span data-ttu-id="84602-118">之後，您可以在設定檔上按一下滑鼠右鍵，並使用 [**編輯 WCF**設定] 內容功能表項目。</span><span class="sxs-lookup"><span data-stu-id="84602-118">After that, you can right-click a configuration file and use the **Edit WCF Config** context menu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84602-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="84602-119">See also</span></span>

- [<span data-ttu-id="84602-120">設定編輯器工具 (SvcConfigEditor.exe)</span><span class="sxs-lookup"><span data-stu-id="84602-120">Configuration Editor Tool (SvcConfigEditor.exe)</span></span>](../configuration-editor-tool-svcconfigeditor-exe.md)
- [<span data-ttu-id="84602-121">設定服務</span><span class="sxs-lookup"><span data-stu-id="84602-121">Configuring Services</span></span>](../configuring-services.md)
- [<span data-ttu-id="84602-122">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="84602-122">\<system.serviceModel></span></span>](../../configure-apps/file-schema/wcf/system-servicemodel.md)
