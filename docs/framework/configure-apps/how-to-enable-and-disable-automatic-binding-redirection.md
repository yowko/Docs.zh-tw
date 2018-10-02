---
title: 如何：啟用和停用自動繫結重新導向
ms.date: 09/12/2018
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 9b9c9cbdb89ccf67942dcccee37ea410c6fa39a5
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48036191"
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a><span data-ttu-id="d7d59-102">如何：啟用和停用自動繫結重新導向</span><span class="sxs-lookup"><span data-stu-id="d7d59-102">How to: Enable and Disable Automatic Binding Redirection</span></span>

<span data-ttu-id="d7d59-103">在 Visual Studio 中為目標的應用程式的編譯時[!INCLUDE[net_v451](../../../includes/net-v451-md.md)]和更新版本中，繫結重新導向可能會自動加入至應用程式組態檔覆寫組件統一。</span><span class="sxs-lookup"><span data-stu-id="d7d59-103">When you compile apps in Visual Studio that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] and later versions, binding redirects may be automatically added to the app configuration file to override assembly unification.</span></span> <span data-ttu-id="d7d59-104">如果您的應用程式或其元件參考相同組件的多個版本，即使您在應用程式的組態檔中手動指定繫結重新導向，仍會加入繫結重新導向。</span><span class="sxs-lookup"><span data-stu-id="d7d59-104">Binding redirects are added if your app or its components reference more than one version of the same assembly, even if you manually specify binding redirects in the configuration file for your app.</span></span> <span data-ttu-id="d7d59-105">自動繫結重新導向功能會影響傳統桌面應用程式和 web 應用程式為目標[!INCLUDE[net_v451](../../../includes/net-v451-md.md)]或更新版本中，雖然行為會稍有不同的 web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d7d59-105">The automatic binding redirection feature affects traditional desktop apps and web apps that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] or a later version, although the behavior is slightly different for a web app.</span></span> <span data-ttu-id="d7d59-106">如果您現有的應用程式是以舊版的 .NET Framework 為目標，就可以啟用自動繫結重新導向，如果您要保留手動撰寫的繫結重新導向，可以停用這項功能。</span><span class="sxs-lookup"><span data-stu-id="d7d59-106">You can enable automatic binding redirection if you have existing apps that target previous versions of the .NET Framework, or you can disable this feature if you want to keep manually authored binding redirects.</span></span>

## <a name="disable-automatic-binding-redirects-in-desktop-apps"></a><span data-ttu-id="d7d59-107">停用自動繫結重新導向桌面應用程式中</span><span class="sxs-lookup"><span data-stu-id="d7d59-107">Disable automatic binding redirects in desktop apps</span></span>

<span data-ttu-id="d7d59-108">在以 [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] 和較新版本為目標的傳統桌面應用程式中，自動繫結重新導向預設為啟用。</span><span class="sxs-lookup"><span data-stu-id="d7d59-108">Automatic binding redirects are enabled by default for traditional desktop apps that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] and later versions.</span></span> <span data-ttu-id="d7d59-109">繫結重新導向會在應用程式進行編譯時加入至輸出組態檔 (app.config)，並且覆寫可能進行的組件統一。</span><span class="sxs-lookup"><span data-stu-id="d7d59-109">The binding redirects are added to the output configuration (app.config) file when the app is compiled and overrides the assembly unification that might otherwise take place.</span></span> <span data-ttu-id="d7d59-110">來源 app.config 檔案則不會加以修改。</span><span class="sxs-lookup"><span data-stu-id="d7d59-110">The source app.config file is not modified.</span></span> <span data-ttu-id="d7d59-111">您可以修改應用程式的專案檔停用這項功能。</span><span class="sxs-lookup"><span data-stu-id="d7d59-111">You can disable this feature by modifying the project file for the app.</span></span>

1. <span data-ttu-id="d7d59-112">開啟專案檔案進行編輯使用下列方法之一：</span><span class="sxs-lookup"><span data-stu-id="d7d59-112">Open the project file for editing using one of the following methods:</span></span>

   - <span data-ttu-id="d7d59-113">在 Visual Studio 中，選取專案**方案總管 中**，然後選擇**在檔案總管 中開啟資料夾**從捷徑功能表。</span><span class="sxs-lookup"><span data-stu-id="d7d59-113">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span> <span data-ttu-id="d7d59-114">在 [檔案總管] 中，尋找專案 （.csproj 或.vbproj） 檔，並在記事本中開啟它。</span><span class="sxs-lookup"><span data-stu-id="d7d59-114">In File Explorer, find the project (.csproj or .vbproj) file and open it in Notepad.</span></span>
   - <span data-ttu-id="d7d59-115">在 Visual Studio 中，在**方案總管**，以滑鼠右鍵按一下專案，然後選擇**卸載專案**。</span><span class="sxs-lookup"><span data-stu-id="d7d59-115">In Visual Studio, in **Solution Explorer**, right-click the project and choose **Unload Project**.</span></span> <span data-ttu-id="d7d59-116">同樣地，以滑鼠右鍵按一下已卸載的專案，然後選擇 [**編輯 [projectname.csproj]]**。</span><span class="sxs-lookup"><span data-stu-id="d7d59-116">Right-click the unloaded project again, and then choose **Edit [projectname.csproj]**.</span></span>

2. <span data-ttu-id="d7d59-117">在專案檔中尋找下列屬性項目：</span><span class="sxs-lookup"><span data-stu-id="d7d59-117">In the project file, find the following property entry:</span></span>

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

3. <span data-ttu-id="d7d59-118">將 `true` 變更為 `false`：</span><span class="sxs-lookup"><span data-stu-id="d7d59-118">Change `true` to `false`:</span></span>

   ```xml
   <AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>
   ```

## <a name="enable-automatic-binding-redirects-manually"></a><span data-ttu-id="d7d59-119">以手動方式啟用自動繫結重新導向</span><span class="sxs-lookup"><span data-stu-id="d7d59-119">Enable automatic binding redirects manually</span></span>

<span data-ttu-id="d7d59-120">您可以啟用自動繫結重新導向，現有的應用程式中較舊版本為目標的.NET Framework 中，或在情況下，您不會自動加入重新導向系統提示時。</span><span class="sxs-lookup"><span data-stu-id="d7d59-120">You can enable automatic binding redirects in existing apps that target older versions of the .NET Framework, or in cases where you're not automatically prompted to add a redirect.</span></span> <span data-ttu-id="d7d59-121">如果您較新的 framework 版本為目標，但不要收到自動提示加入重新導向，您可能會建議您重新對應組件的組建輸出。</span><span class="sxs-lookup"><span data-stu-id="d7d59-121">If you're targeting a newer version of the framework but do not get automatically prompted to add a redirect, you'll likely get build output that suggests you remap assemblies.</span></span>

1. <span data-ttu-id="d7d59-122">開啟專案檔案進行編輯使用下列方法之一：</span><span class="sxs-lookup"><span data-stu-id="d7d59-122">Open the project file for editing using one of the following methods:</span></span>

   - <span data-ttu-id="d7d59-123">在 Visual Studio 中，選取專案**方案總管 中**，然後選擇**在檔案總管 中開啟資料夾**從捷徑功能表。</span><span class="sxs-lookup"><span data-stu-id="d7d59-123">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span> <span data-ttu-id="d7d59-124">在 [檔案總管] 中，尋找專案 （.csproj 或.vbproj） 檔，並在記事本中開啟它。</span><span class="sxs-lookup"><span data-stu-id="d7d59-124">In File Explorer, find the project (.csproj or .vbproj) file and open it in Notepad.</span></span>
   - <span data-ttu-id="d7d59-125">在 Visual Studio 中，在**方案總管**，以滑鼠右鍵按一下專案，然後選擇**卸載專案**。</span><span class="sxs-lookup"><span data-stu-id="d7d59-125">In Visual Studio, in **Solution Explorer**, right-click the project and choose **Unload Project**.</span></span> <span data-ttu-id="d7d59-126">同樣地，以滑鼠右鍵按一下已卸載的專案，然後選擇 [**編輯 [projectname.csproj]]**。</span><span class="sxs-lookup"><span data-stu-id="d7d59-126">Right-click the unloaded project again, and then choose **Edit [projectname.csproj]**.</span></span>

2. <span data-ttu-id="d7d59-127">將下列項目新增至第一個組態屬性群組 (在\<PropertyGroup > 標記):</span><span class="sxs-lookup"><span data-stu-id="d7d59-127">Add the following element to the first configuration property group (under the \<PropertyGroup> tag):</span></span>

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

   <span data-ttu-id="d7d59-128">下列範例顯示的範例專案檔案與插入的項目：</span><span class="sxs-lookup"><span data-stu-id="d7d59-128">The following shows an example project file with the element inserted:</span></span>

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

3. <span data-ttu-id="d7d59-129">編譯您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d7d59-129">Compile your app.</span></span>

## <a name="enable-automatic-binding-redirects-in-web-apps"></a><span data-ttu-id="d7d59-130">啟用 web 應用程式中的自動繫結重新導向</span><span class="sxs-lookup"><span data-stu-id="d7d59-130">Enable automatic binding redirects in web apps</span></span>

<span data-ttu-id="d7d59-131">在 Web 應用程式中，自動繫結重新導向是以不同的方式實作。</span><span class="sxs-lookup"><span data-stu-id="d7d59-131">Automatic binding redirects are implemented differently for web apps.</span></span> <span data-ttu-id="d7d59-132">由於 Web 應用程式的來源組態檔 (web.config) 必須經過修改，因此繫結重新導向不會自動加入至組態檔。</span><span class="sxs-lookup"><span data-stu-id="d7d59-132">Because the source configuration (web.config) file must be modified for web apps, binding redirects are not automatically added to the configuration file.</span></span> <span data-ttu-id="d7d59-133">不過，如果發生繫結衝突，Visual Studio 會通知您，那麼您就可以加入繫結重新導向來解決衝突。</span><span class="sxs-lookup"><span data-stu-id="d7d59-133">However, Visual Studio notifies you of binding conflicts, and you can add binding redirects to resolve the conflicts.</span></span> <span data-ttu-id="d7d59-134">由於系統一律提示您新增繫結重新導向，您不需要明確停用此功能的 web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d7d59-134">Because you're always prompted to add binding redirects, you don't need to explicitly disable this feature for a web app.</span></span>

<span data-ttu-id="d7d59-135">若要新增繫結重新導向到 web.config 檔案：</span><span class="sxs-lookup"><span data-stu-id="d7d59-135">To add binding redirects to a web.config file:</span></span>

1. <span data-ttu-id="d7d59-136">在 Visual Studio 中編譯應用程式，並檢查是否有建置警告。</span><span class="sxs-lookup"><span data-stu-id="d7d59-136">In Visual Studio, compile the app, and check for build warnings.</span></span>

   <span data-ttu-id="d7d59-137">![建置組件參考衝突的警告](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span><span class="sxs-lookup"><span data-stu-id="d7d59-137">![Build warning for assembly reference conflicts](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span></span>

2. <span data-ttu-id="d7d59-138">如果有組件繫結衝突，則會出現警告。</span><span class="sxs-lookup"><span data-stu-id="d7d59-138">If there are assembly binding conflicts, a warning appears.</span></span> <span data-ttu-id="d7d59-139">按兩下該警告，或選取警告並按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="d7d59-139">Double-click the warning, or select the warning and press **Enter**.</span></span>

   <span data-ttu-id="d7d59-140">對話方塊隨即出現，可讓您將必要的繫結重新導向自動加入至來源 web.config 檔。</span><span class="sxs-lookup"><span data-stu-id="d7d59-140">A dialog box that enables you to automatically add the necessary binding redirects to the source web.config file appears.</span></span>

   <span data-ttu-id="d7d59-141">![繫結重新導向的權限 對話方塊](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span><span class="sxs-lookup"><span data-stu-id="d7d59-141">![Binding redirect permission dialog](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span></span>

## <a name="see-also"></a><span data-ttu-id="d7d59-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7d59-142">See also</span></span>

- [<span data-ttu-id="d7d59-143">\<bindingRedirect > 項目</span><span class="sxs-lookup"><span data-stu-id="d7d59-143">\<bindingRedirect> Element</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)
- [<span data-ttu-id="d7d59-144">重新導向組件版本</span><span class="sxs-lookup"><span data-stu-id="d7d59-144">Redirecting Assembly Versions</span></span>](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
