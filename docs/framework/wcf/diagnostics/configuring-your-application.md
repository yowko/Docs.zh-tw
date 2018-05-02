---
title: 設定您的應用程式
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 170583239ed357904e723aebdaef9809938b5123
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="configuring-your-application"></a><span data-ttu-id="97fbd-102">設定您的應用程式</span><span class="sxs-lookup"><span data-stu-id="97fbd-102">Configuring Your Application</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="97fbd-103"> 會使用 .NET 組態系統，並讓您在機器和應用程式範圍內設定服務。</span><span class="sxs-lookup"><span data-stu-id="97fbd-103"> uses the .NET configuration system and allows you to configure services at both the machine and application scope.</span></span>  
  
 <span data-ttu-id="97fbd-104">由 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 定義的組態設定位於 `<system.serviceModel>` 節群組中。</span><span class="sxs-lookup"><span data-stu-id="97fbd-104">Configuration settings defined by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] are located in the `<system.serviceModel>` section group.</span></span> <span data-ttu-id="97fbd-105">如需有關如何設定[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]服務，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="97fbd-105">For more information about how to configure a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service, see the following topics:</span></span>  
  
-   [<span data-ttu-id="97fbd-106">設定服務</span><span class="sxs-lookup"><span data-stu-id="97fbd-106">Configuring Services</span></span>](../../../../docs/framework/wcf/configuring-services.md)  
  
-   [<span data-ttu-id="97fbd-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="97fbd-107">\<system.serviceModel></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 <span data-ttu-id="97fbd-108">應用程式定義的組態設定會定義在 `<appSettings>` 節群組中。</span><span class="sxs-lookup"><span data-stu-id="97fbd-108">Application-defined configurations settings are defined in the `<appSettings>` section group.</span></span> <span data-ttu-id="97fbd-109">如需.NET 組態檔中的應用程式設定的詳細資訊，請參閱[ \<appSettings >](http://go.microsoft.com/fwlink/?LinkId=95159)。</span><span class="sxs-lookup"><span data-stu-id="97fbd-109">For more information about application settings in .NET configuration files, see [\<appSettings>](http://go.microsoft.com/fwlink/?LinkId=95159).</span></span>  
  
## <a name="using-the-configuration-editor"></a><span data-ttu-id="97fbd-110">使用組態編輯器</span><span class="sxs-lookup"><span data-stu-id="97fbd-110">Using the Configuration Editor</span></span>  
 <span data-ttu-id="97fbd-111">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)][組態編輯器工具 (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)可讓系統管理員和開發人員建立及修改組態設定[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]服務以使用圖形化使用者介面。</span><span class="sxs-lookup"><span data-stu-id="97fbd-111">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)][Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) allows administrators and developers to create and modify configuration settings for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services using a graphical user interface.</span></span> <span data-ttu-id="97fbd-112">有了這項工具，您可以管理 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 繫結、行為、服務及診斷的設定，而不用直接編輯 XML 組態檔。</span><span class="sxs-lookup"><span data-stu-id="97fbd-112">With this tool, you can manage settings for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bindings, behaviors, services, and diagnostics without directly editing XML configuration files.</span></span>  
  
## <a name="editing-configuration-files-in-visual-studio"></a><span data-ttu-id="97fbd-113">在 Visual Studio 中編輯組態檔</span><span class="sxs-lookup"><span data-stu-id="97fbd-113">Editing Configuration Files in Visual Studio</span></span>  
 <span data-ttu-id="97fbd-114">若要編輯的組態檔[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]服務 Visual Studio 專案中的，以滑鼠右鍵按一下 **[方案總管 中]** 選擇**編輯 WCF 組態**操作功能表項目。</span><span class="sxs-lookup"><span data-stu-id="97fbd-114">To edit the configuration file of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service project in Visual Studio, right click it in **Solution Explorer** and choose the **Edit WCF Config** context menu item.</span></span> <span data-ttu-id="97fbd-115">這會啟動[組態編輯器工具 (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="97fbd-115">This launches the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="97fbd-116">如果您編輯的組態檔[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Visual Studio 中的 Web 服務專案，以滑鼠右鍵按一下它在**方案總管 中**，請注意，**編輯 WCF 組態**操作功能表項目已遺失。</span><span class="sxs-lookup"><span data-stu-id="97fbd-116">If you edit the configuration file of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web Service project in Visual Studio by right-clicking it in **Solution Explorer**, notice that the **Edit WCF Config** context menu item is missing.</span></span> <span data-ttu-id="97fbd-117">若要解決這個問題，請按一下**工具**功能表上，選擇  **WCF 服務組態編輯器**。</span><span class="sxs-lookup"><span data-stu-id="97fbd-117">To workaround this issue, click the **Tools** menu, and choose **WCF Service Config Editor**.</span></span> <span data-ttu-id="97fbd-118">在這之後，您可以以滑鼠右鍵按一下組態檔，並使用**編輯 WCF 組態**操作功能表項目。</span><span class="sxs-lookup"><span data-stu-id="97fbd-118">After that, you can right-click a configuration file and use the **Edit WCF Config** context menu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97fbd-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97fbd-119">See Also</span></span>  
 [<span data-ttu-id="97fbd-120">設定編輯器工具 (SvcConfigEditor.exe)</span><span class="sxs-lookup"><span data-stu-id="97fbd-120">Configuration Editor Tool (SvcConfigEditor.exe)</span></span>](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
 [<span data-ttu-id="97fbd-121">設定服務</span><span class="sxs-lookup"><span data-stu-id="97fbd-121">Configuring Services</span></span>](../../../../docs/framework/wcf/configuring-services.md)  
 [<span data-ttu-id="97fbd-122">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="97fbd-122">\<system.serviceModel></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)
