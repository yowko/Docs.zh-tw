---
title: "如何：啟用和停用自動繫結重新導向"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
caps.latest.revision: "17"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: b6887706aeef3855c1e02c8b1379856022cdac04
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a><span data-ttu-id="f3844-102">如何：啟用和停用自動繫結重新導向</span><span class="sxs-lookup"><span data-stu-id="f3844-102">How to: Enable and Disable Automatic Binding Redirection</span></span>
<span data-ttu-id="f3844-103">從 [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] 開始，當您編譯目標為 [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] 的應用程式時，繫結重新導向會自動加入至應用程式組態檔以覆寫組件統一。</span><span class="sxs-lookup"><span data-stu-id="f3844-103">Starting with [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], when you compile apps that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], binding redirects may be automatically added to the app configuration file to override assembly unification.</span></span> <span data-ttu-id="f3844-104">如果您的應用程式或其元件參考相同組件的多個版本，即使您在應用程式的組態檔中手動指定繫結重新導向，仍會加入繫結重新導向。</span><span class="sxs-lookup"><span data-stu-id="f3844-104">Binding redirects are added if your app or its components reference more than one version of the same assembly, even if you manually specify binding redirects in the configuration file for your app.</span></span> <span data-ttu-id="f3844-105">自動繫結重新導向功能會影響以 [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] 為目標的傳統桌面應用程式和 Web 應用程式，不過 Web 應用程式的行為稍有不同。</span><span class="sxs-lookup"><span data-stu-id="f3844-105">The automatic binding redirection feature affects traditional desktop apps and web apps that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], although the behavior is slightly different for a web app.</span></span> <span data-ttu-id="f3844-106">如果您現有的應用程式是以舊版的 .NET Framework 為目標，就可以啟用自動繫結重新導向，如果您要保留手動撰寫的繫結重新導向，可以停用這項功能。</span><span class="sxs-lookup"><span data-stu-id="f3844-106">You can enable automatic binding redirection if you have existing apps that target previous versions of the .NET Framework, or you can disable this feature if you want to keep manually authored binding redirects.</span></span>  
  
## <a name="disabling-automatic-binding-redirects-in-desktop-apps"></a><span data-ttu-id="f3844-107">在桌面應用程式中停用自動繫結重新導向</span><span class="sxs-lookup"><span data-stu-id="f3844-107">Disabling automatic binding redirects in desktop apps</span></span>  
 <span data-ttu-id="f3844-108">在以 [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] 和較新版本為目標的傳統桌面應用程式中，自動繫結重新導向預設為啟用。</span><span class="sxs-lookup"><span data-stu-id="f3844-108">Automatic binding redirects are enabled by default for traditional desktop apps that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] and later versions.</span></span> <span data-ttu-id="f3844-109">繫結重新導向會在應用程式進行編譯時加入至輸出組態檔 (app.config)，並且覆寫可能進行的組件統一。</span><span class="sxs-lookup"><span data-stu-id="f3844-109">The binding redirects are added to the output configuration (app.config) file when the app is compiled and overrides the assembly unification that might otherwise take place.</span></span> <span data-ttu-id="f3844-110">來源 app.config 檔案則不會加以修改。</span><span class="sxs-lookup"><span data-stu-id="f3844-110">The source app.config file is not modified.</span></span> <span data-ttu-id="f3844-111">您可以修改應用程式的專案檔停用這項功能。</span><span class="sxs-lookup"><span data-stu-id="f3844-111">You can disable this feature by modifying the project file for the app.</span></span>  
  
#### <a name="to-disable-automatic-binding-redirects"></a><span data-ttu-id="f3844-112">若要停用自動繫結重新導向</span><span class="sxs-lookup"><span data-stu-id="f3844-112">To disable automatic binding redirects</span></span>  
  
1.  <span data-ttu-id="f3844-113">在 Visual Studio 中選取專案**方案總管 中**，然後選擇 **在檔案總管 中開啟資料夾**從捷徑功能表。</span><span class="sxs-lookup"><span data-stu-id="f3844-113">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="f3844-114">在 [檔案總管] 中尋找專案檔 (.csproj 或 .vbproj)，然後在 [記事本] 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="f3844-114">In File Explorer, find the project (.csproj or .vbproj) file, and open it in Notepad.</span></span>  
  
3.  <span data-ttu-id="f3844-115">在專案檔中尋找下列屬性項目：</span><span class="sxs-lookup"><span data-stu-id="f3844-115">In the project file, find the following property entry:</span></span>  
  
     `<AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>`  
  
4.  <span data-ttu-id="f3844-116">將 `true` 變更為 `false`：</span><span class="sxs-lookup"><span data-stu-id="f3844-116">Change `true` to `false`:</span></span>  
  
     `<AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>`  
  
## <a name="enabling-automatic-binding-redirects-manually"></a><span data-ttu-id="f3844-117">手動啟用自動繫結重新導向</span><span class="sxs-lookup"><span data-stu-id="f3844-117">Enabling automatic binding redirects manually</span></span>  
 <span data-ttu-id="f3844-118">在以舊版 .NET Framework 為目標的現有應用程式中，或是當系統未自動提示您加入重新導向時，您可以啟用自動繫結重新導向。</span><span class="sxs-lookup"><span data-stu-id="f3844-118">You can enable automatic binding redirects in existing apps that target older versions of the .NET Framework, or in cases where you are not automatically prompted to add a redirect.</span></span> <span data-ttu-id="f3844-119">如果您是以較新版架構為目標，但系統未自動提示您加入重新導向，您可能會取得建議您重新對應組件的組建輸出。</span><span class="sxs-lookup"><span data-stu-id="f3844-119">If you are targeting a newer version of the framework but do not get automatically prompted to add a redirect, you will likely get   build output that suggests you remap assemblies.</span></span>  
  
#### <a name="to-manually-add-an-automatic-binding-redirect-property"></a><span data-ttu-id="f3844-120">手動加入自動繫結重新導向屬性</span><span class="sxs-lookup"><span data-stu-id="f3844-120">To manually add an automatic binding redirect property</span></span>  
  
1.  <span data-ttu-id="f3844-121">在 Visual Studio 中選取專案**方案總管 中**，然後選擇 **在檔案總管 中開啟資料夾**從捷徑功能表。</span><span class="sxs-lookup"><span data-stu-id="f3844-121">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="f3844-122">在 [檔案總管] 中尋找專案檔 (.csproj 或 .vbproj)，然後在 [記事本] 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="f3844-122">In File Explorer, find the project (.csproj or .vbproj) file, and open it in Notepad.</span></span>  
  
3.  <span data-ttu-id="f3844-123">將下列項目加入至第一個組態屬性群組 (下\<PropertyGroup > 標記):</span><span class="sxs-lookup"><span data-stu-id="f3844-123">Add the following element to the first configuration property group (under the \<PropertyGroup> tag):</span></span>  
  
     `<AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>`  
  
     <span data-ttu-id="f3844-124">下面顯示已插入項目的專案檔範例。</span><span class="sxs-lookup"><span data-stu-id="f3844-124">The following shows an example project file with the element inserted.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Project ToolsVersion="12.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" Condition="Exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props')" />  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == ''     ">Debug</Configuration>  
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
        <ProjectGuid>{123334}</ProjectGuid>  
        ...  
        <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>  
      </PropertyGroup>  
    ...  
    </Project>  
    ```  
  
4.  <span data-ttu-id="f3844-125">編譯您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f3844-125">Compile your app.</span></span>  
  
## <a name="enabling-automatic-binding-redirects-in-web-apps"></a><span data-ttu-id="f3844-126">在 Web 應用程式中啟用自動繫結重新導向</span><span class="sxs-lookup"><span data-stu-id="f3844-126">Enabling automatic binding redirects in web apps</span></span>  
 <span data-ttu-id="f3844-127">在 Web 應用程式中，自動繫結重新導向是以不同的方式實作。</span><span class="sxs-lookup"><span data-stu-id="f3844-127">Automatic binding redirects are implemented differently for web apps.</span></span> <span data-ttu-id="f3844-128">由於 Web 應用程式的來源組態檔 (web.config) 必須經過修改，因此繫結重新導向不會自動加入至組態檔。</span><span class="sxs-lookup"><span data-stu-id="f3844-128">Because the source configuration (web.config) file must be modified for web apps, binding redirects are not automatically added to the configuration file.</span></span> <span data-ttu-id="f3844-129">不過，如果發生繫結衝突，Visual Studio 會通知您，那麼您就可以加入繫結重新導向來解決衝突。</span><span class="sxs-lookup"><span data-stu-id="f3844-129">However, Visual Studio notifies you of binding conflicts, and you can add binding redirects to resolve the conflicts.</span></span> <span data-ttu-id="f3844-130">由於系統一律提示您加入繫結重新導向，因此您不需要明確停用 Web 應用程式的這項功能。</span><span class="sxs-lookup"><span data-stu-id="f3844-130">Because you are always prompted to add binding redirects, you do not need to explicitly disable this feature for a web app.</span></span>  
  
#### <a name="to-add-binding-redirects-to-a-webconfig-file"></a><span data-ttu-id="f3844-131">若要將繫結重新導向加入至 web.config 檔</span><span class="sxs-lookup"><span data-stu-id="f3844-131">To add binding redirects to a web.config file</span></span>  
  
1.  <span data-ttu-id="f3844-132">在 Visual Studio 中編譯應用程式，並檢查是否有建置警告。</span><span class="sxs-lookup"><span data-stu-id="f3844-132">In Visual Studio, compile the app, and check for build warnings.</span></span>  
  
     <span data-ttu-id="f3844-133">![建置組件參考衝突的警告](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span><span class="sxs-lookup"><span data-stu-id="f3844-133">![Build warning for assembly reference conflicts](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span></span>  
  
2.  <span data-ttu-id="f3844-134">如果有組件繫結衝突，則會出現警告。</span><span class="sxs-lookup"><span data-stu-id="f3844-134">If there are assembly binding conflicts, a warning appears.</span></span> <span data-ttu-id="f3844-135">按兩下警告 </span><span class="sxs-lookup"><span data-stu-id="f3844-135">Double-click the warning.</span></span> <span data-ttu-id="f3844-136">(鍵盤： 選取警告並按下**Enter**。)</span><span class="sxs-lookup"><span data-stu-id="f3844-136">(Keyboard: Select the warning and press **Enter**.)</span></span>  
  
     <span data-ttu-id="f3844-137">對話方塊隨即出現，可讓您將必要的繫結重新導向自動加入至來源 web.config 檔。</span><span class="sxs-lookup"><span data-stu-id="f3844-137">A dialog box that enables you to automatically add the necessary binding redirects to the source web.config file appears.</span></span>  
  
     <span data-ttu-id="f3844-138">![繫結重新導向 權限對話方塊](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span><span class="sxs-lookup"><span data-stu-id="f3844-138">![Binding redirect permission dialog](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3844-139">請參閱</span><span class="sxs-lookup"><span data-stu-id="f3844-139">See Also</span></span>  
 [<span data-ttu-id="f3844-140">\<bindingRedirect > 項目</span><span class="sxs-lookup"><span data-stu-id="f3844-140">\<bindingRedirect> Element</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)  
 [<span data-ttu-id="f3844-141">重新導向組件版本</span><span class="sxs-lookup"><span data-stu-id="f3844-141">Redirecting Assembly Versions</span></span>](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
