---
title: "設定您的應用程式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7f22fac02616070ecd6498ad0e158782001681ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="configuring-your-application"></a><span data-ttu-id="88f77-102">設定您的應用程式</span><span class="sxs-lookup"><span data-stu-id="88f77-102">Configuring Your Application</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="88f77-103"> 會使用 .NET 組態系統，並讓您在機器和應用程式範圍內設定服務。</span><span class="sxs-lookup"><span data-stu-id="88f77-103"> uses the .NET configuration system and allows you to configure services at both the machine and application scope.</span></span>  
  
 <span data-ttu-id="88f77-104">由 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 定義的組態設定位於 `<system.serviceModel>` 節群組中。</span><span class="sxs-lookup"><span data-stu-id="88f77-104">Configuration settings defined by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] are located in the `<system.serviceModel>` section group.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="88f77-105">如何設定 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="88f77-105"> how to configure a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service, see the following topics:</span></span>  
  
-   [<span data-ttu-id="88f77-106">設定服務</span><span class="sxs-lookup"><span data-stu-id="88f77-106">Configuring Services</span></span>](../../../../docs/framework/wcf/configuring-services.md)  
  
-   [<span data-ttu-id="88f77-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="88f77-107">\<system.serviceModel></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 <span data-ttu-id="88f77-108">應用程式定義的組態設定會定義在 `<appSettings>` 節群組中。</span><span class="sxs-lookup"><span data-stu-id="88f77-108">Application-defined configurations settings are defined in the `<appSettings>` section group.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="88f77-109">應用程式設定.NET 設定檔中，請參閱[ \<appSettings >](http://go.microsoft.com/fwlink/?LinkId=95159)。</span><span class="sxs-lookup"><span data-stu-id="88f77-109"> application settings in .NET configuration files, see [\<appSettings>](http://go.microsoft.com/fwlink/?LinkId=95159).</span></span>  
  
## <a name="using-the-configuration-editor"></a><span data-ttu-id="88f77-110">使用組態編輯器</span><span class="sxs-lookup"><span data-stu-id="88f77-110">Using the Configuration Editor</span></span>  
 <span data-ttu-id="88f77-111">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)][組態編輯器工具 (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)可讓系統管理員和開發人員建立及修改組態設定[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]服務以使用圖形化使用者介面。</span><span class="sxs-lookup"><span data-stu-id="88f77-111">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)][Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) allows administrators and developers to create and modify configuration settings for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services using a graphical user interface.</span></span> <span data-ttu-id="88f77-112">有了這項工具，您可以管理 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 繫結、行為、服務及診斷的設定，而不用直接編輯 XML 組態檔。</span><span class="sxs-lookup"><span data-stu-id="88f77-112">With this tool, you can manage settings for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bindings, behaviors, services, and diagnostics without directly editing XML configuration files.</span></span>  
  
## <a name="editing-configuration-files-in-visual-studio"></a><span data-ttu-id="88f77-113">在 Visual Studio 中編輯組態檔</span><span class="sxs-lookup"><span data-stu-id="88f77-113">Editing Configuration Files in Visual Studio</span></span>  
 <span data-ttu-id="88f77-114">若要編輯的組態檔[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]服務專案中的[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]，以滑鼠右鍵按一下 [**方案總管] 中**選擇**編輯 WCF 組態**操作功能表項目。</span><span class="sxs-lookup"><span data-stu-id="88f77-114">To edit the configuration file of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service project in [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], right click it in **Solution Explorer** and choose the **Edit WCF Config** context menu item.</span></span> <span data-ttu-id="88f77-115">這會啟動[組態編輯器工具 (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="88f77-115">This launches the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="88f77-116">如果您編輯的組態檔[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]中的 Web 服務專案[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]以滑鼠右鍵按一下它在**方案總管 中**，請注意，**編輯 WCF 組態**操作功能表項目遺漏.</span><span class="sxs-lookup"><span data-stu-id="88f77-116">If you edit the configuration file of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web Service project in [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] by right-clicking it in **Solution Explorer**, notice that the **Edit WCF Config** context menu item is missing.</span></span> <span data-ttu-id="88f77-117">若要解決這個問題，請按一下**工具**功能表上，選擇  **WCF 服務組態編輯器**。</span><span class="sxs-lookup"><span data-stu-id="88f77-117">To workaround this issue, click the **Tools** menu, and choose **WCF Service Config Editor**.</span></span> <span data-ttu-id="88f77-118">在這之後，您可以以滑鼠右鍵按一下組態檔，並使用**編輯 WCF 組態**操作功能表項目。</span><span class="sxs-lookup"><span data-stu-id="88f77-118">After that, you can right-click a configuration file and use the **Edit WCF Config** context menu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88f77-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88f77-119">See Also</span></span>  
 [<span data-ttu-id="88f77-120">設定編輯器工具 (SvcConfigEditor.exe)</span><span class="sxs-lookup"><span data-stu-id="88f77-120">Configuration Editor Tool (SvcConfigEditor.exe)</span></span>](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
 [<span data-ttu-id="88f77-121">設定服務</span><span class="sxs-lookup"><span data-stu-id="88f77-121">Configuring Services</span></span>](../../../../docs/framework/wcf/configuring-services.md)  
 [<span data-ttu-id="88f77-122">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="88f77-122">\<system.serviceModel></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)
