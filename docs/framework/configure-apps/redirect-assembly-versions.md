---
title: 重新導向組件版本
ms.date: 03/30/2017
helpviewer_keywords:
- assembly binding, redirection
- redirecting assembly binding to earlier version
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], binding redirection
ms.assetid: 88fb1a17-6ac9-4b57-8028-193aec1f727c
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: aad369b35837089d05f5d7517e023671f0178011
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507800"
---
# <a name="redirecting-assembly-versions"></a><span data-ttu-id="d72d2-102">重新導向組件版本</span><span class="sxs-lookup"><span data-stu-id="d72d2-102">Redirecting Assembly Versions</span></span>
<span data-ttu-id="d72d2-103">您可以將編譯時間繫結參考重新導向至 .NET Framework 組件、協力廠商組件或您自己的應用程式組件。</span><span class="sxs-lookup"><span data-stu-id="d72d2-103">You can redirect compile-time binding references to .NET Framework assemblies, third-party assemblies, or your own app's assemblies.</span></span> <span data-ttu-id="d72d2-104">您可以用多種方式將應用程式重新導向為使用其他版本的組件：透過發行者原則、透過應用程式設定檔或透過電腦設定檔。</span><span class="sxs-lookup"><span data-stu-id="d72d2-104">You can redirect your app to use a different version of an assembly in a number of ways: through publisher policy, through an app configuration file; or through the machine configuration file.</span></span> <span data-ttu-id="d72d2-105">本文討論 .NET Framework 中的組件繫結如何運作，以及其設定方式。</span><span class="sxs-lookup"><span data-stu-id="d72d2-105">This article discusses how assembly binding works in the .NET Framework and how it can be configured.</span></span>  
  
<a name="BKMK_Assemblyunificationanddefaultbinding"></a>   
## <a name="assembly-unification-and-default-binding"></a><span data-ttu-id="d72d2-106">組件統一和預設繫結</span><span class="sxs-lookup"><span data-stu-id="d72d2-106">Assembly unification and default binding</span></span>  
 <span data-ttu-id="d72d2-107">.NET Framework 組件的繫結有時會透過名為 *「組件統一」*(assembly unification) 的處理序進行重新導向。</span><span class="sxs-lookup"><span data-stu-id="d72d2-107">Bindings to .NET Framework assemblies are sometimes redirected through a process called *assembly unification*.</span></span> <span data-ttu-id="d72d2-108">.NET Framework 包含某個版本的通用語言執行平台，以及大約二十多個組成類型程式庫的 .NET Framework 組件。</span><span class="sxs-lookup"><span data-stu-id="d72d2-108">The .NET Framework consists of a version of the common language runtime and about two dozen .NET Framework assemblies that make up the type library.</span></span> <span data-ttu-id="d72d2-109">執行階段將這些 .NET Framework 組件視為單一單位。</span><span class="sxs-lookup"><span data-stu-id="d72d2-109">These .NET Framework assemblies are treated by the runtime as a single unit.</span></span> <span data-ttu-id="d72d2-110">根據預設，應用程式啟動時，任何類型參考只要位於執行階段所執行的程式碼中，都會導向至 .NET Framework 組件；且該組建將與載入處理序的執行階段具有相同的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="d72d2-110">By default, when an app is launched, all references to types in code run by the runtime are directed to .NET Framework assemblies that have the same version number as the runtime that is loaded in a process.</span></span> <span data-ttu-id="d72d2-111">與此模型同時發生的重新導向，皆為執行階段的預設行為。</span><span class="sxs-lookup"><span data-stu-id="d72d2-111">The redirections that occur with this model are the default behavior for the runtime.</span></span>  
  
 <span data-ttu-id="d72d2-112">例如，如果您的應用程式參考 System.XML 命名空間中的類型，而且是使用 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]所建立，則會包含隨附於執行階段 4.5 版之 System.XML 組件的靜態參考。</span><span class="sxs-lookup"><span data-stu-id="d72d2-112">For example, if your app references types in the System.XML namespace and was built by using the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], it contains static references to the System.XML assembly that ships with runtime version 4.5.</span></span> <span data-ttu-id="d72d2-113">如果您要將點的繫結參考重新導向至隨附於 .NET Framework 4 的 System.XML 組件，可以將重新導向資訊放在應用程式設定檔中。</span><span class="sxs-lookup"><span data-stu-id="d72d2-113">If you want to redirect the binding reference to point to the System.XML assembly that ship with the .NET Framework 4, you can put redirect information in the app configuration file.</span></span> <span data-ttu-id="d72d2-114">統一的 .NET Framework 組件之設定檔中的繫結重新導向會取消統一該組件。</span><span class="sxs-lookup"><span data-stu-id="d72d2-114">A binding redirection in a configuration file for a unified .NET Framework assembly cancels the unification for that assembly.</span></span>  
  
 <span data-ttu-id="d72d2-115">此外，如果有多個可用版本，您可能會想要以手動方式將協力廠商組件的組件繫結重新導向。</span><span class="sxs-lookup"><span data-stu-id="d72d2-115">In addition, you may want to manually redirect assembly binding for third-party assemblies if there are multiple versions available.</span></span>  
  
<a name="BKMK_Redirectingassemblyversionsbyusingpublisherpolicy"></a>   
## <a name="redirecting-assembly-versions-by-using-publisher-policy"></a><span data-ttu-id="d72d2-116">使用發行者原則將組件版本重新導向</span><span class="sxs-lookup"><span data-stu-id="d72d2-116">Redirecting assembly versions by using publisher policy</span></span>  
 <span data-ttu-id="d72d2-117">組件的廠商可以加入具有新組件的發行者原則檔，藉此將應用程式導向至較新版的組件。</span><span class="sxs-lookup"><span data-stu-id="d72d2-117">Vendors of assemblies can direct apps to a newer version of an assembly by including a publisher policy file with the new assembly.</span></span> <span data-ttu-id="d72d2-118">發行者原則檔位於全域組件快取，其中包含組件重新導向設定。</span><span class="sxs-lookup"><span data-stu-id="d72d2-118">The publisher policy file, which is located in the global assembly cache, contains assembly redirection settings.</span></span>  
  
 <span data-ttu-id="d72d2-119">組件的每個主要 .次要 版本都有自己的發行者原則檔。</span><span class="sxs-lookup"><span data-stu-id="d72d2-119">Each *major*.*minor* version of an assembly has its own publisher policy file.</span></span> <span data-ttu-id="d72d2-120">例如，從 2.0.2.222 版重新導向至 2.0.3.000 版，以及從 2.0.2.321 版重新導向至 2.0.3.000 版，兩者的目標檔案皆相同，因為已透過 2.0 版建立了關係。</span><span class="sxs-lookup"><span data-stu-id="d72d2-120">For example, redirections from version 2.0.2.222 to 2.0.3.000 and from version 2.0.2.321 to version 2.0.3.000 both go into the same file, because they are associated with version 2.0.</span></span> <span data-ttu-id="d72d2-121">然而，從 3.0.0.999 版重新導向至 4.0.0.000 版則會傳入 3.0.999 版的檔案。</span><span class="sxs-lookup"><span data-stu-id="d72d2-121">However, a redirection from version 3.0.0.999 to version 4.0.0.000 goes into the file for version 3.0.999.</span></span> <span data-ttu-id="d72d2-122">.NET Framework 的每個主要版本都有自己的發行者原則檔。</span><span class="sxs-lookup"><span data-stu-id="d72d2-122">Each major version of the .NET Framework has its own publisher policy file.</span></span>  
  
 <span data-ttu-id="d72d2-123">如果組件有發行者原則檔，則執行階段會在檢查組件的資訊清單和應用程式設定檔後，檢查此檔案。</span><span class="sxs-lookup"><span data-stu-id="d72d2-123">If a publisher policy file exists for an assembly, the runtime checks this file after checking the assembly's manifest and app configuration file.</span></span> <span data-ttu-id="d72d2-124">廠商必須只在新組件與重新導向的舊版組件相容時，才使用發行者原則檔。</span><span class="sxs-lookup"><span data-stu-id="d72d2-124">Vendors should use publisher policy files only when the new assembly is backward compatible with the assembly being redirected.</span></span>  
  
 <span data-ttu-id="d72d2-125">您可以指定應用程式設定檔中的設定，藉此略過應用程式的發行者原則，方法詳述於 [略過發行者原則章節](#bypass_PP)。</span><span class="sxs-lookup"><span data-stu-id="d72d2-125">You can bypass publisher policy for your app by specifying settings in the app configuration file, as discussed in the [Bypassing publisher policy section](#bypass_PP).</span></span>  
  
<a name="BKMK_Redirectingassemblyversionsattheapplevel"></a>   
## <a name="redirecting-assembly-versions-at-the-app-level"></a><span data-ttu-id="d72d2-126">將應用程式層級的組件版本重新導向</span><span class="sxs-lookup"><span data-stu-id="d72d2-126">Redirecting assembly versions at the app level</span></span>  
 <span data-ttu-id="d72d2-127">有數種不同技術可透過應用程式設定檔變更應用程式的繫結行為：您可以手動編輯應用程式設定檔、可以依賴自動繫結重新導向，也可以略過發行者原則以指定繫結行為。</span><span class="sxs-lookup"><span data-stu-id="d72d2-127">There are a few different techniques for changing the binding behavior for your app through the app configuration file: you can manually edit the file, you can rely on automatic binding redirection, or you can specify binding behavior by bypassing publisher policy.</span></span>  
  
### <a name="manually-editing-the-app-config-file"></a><span data-ttu-id="d72d2-128">手動編輯應用程式設定檔</span><span class="sxs-lookup"><span data-stu-id="d72d2-128">Manually editing the app config file</span></span>  
 <span data-ttu-id="d72d2-129">您可以手動編輯應用程式設定檔以解決組件問題。</span><span class="sxs-lookup"><span data-stu-id="d72d2-129">You can manually edit the app configuration file to resolve assembly issues.</span></span> <span data-ttu-id="d72d2-130">例如，如果廠商可能發行您應用程式所使用的組件較新版本，但因為不保證與舊版相容而未提供發行者原則，則可以將組件繫結資訊放在應用程式的設定檔中 (如下所示)，藉此將應用程式重新導向為使用較新版的組件。</span><span class="sxs-lookup"><span data-stu-id="d72d2-130">For example, if a vendor might release a newer version of an assembly that your app uses without supplying a publisher policy, because they do not guarantee backward compatibility, you can direct your app to use the newer version of the assembly by putting assembly binding information in your app's configuration file as follows.</span></span>  
  
```xml  
<dependentAssembly>  
  <assemblyIdentity name="someAssembly"  
    publicKeyToken="32ab4ba45e0a69a1"  
    culture="en-us" />  
  <bindingRedirect oldVersion="7.0.0.0" newVersion="8.0.0.0" />  
</dependentAssembly>  
```  
  
### <a name="relying-on-automatic-binding-redirection"></a><span data-ttu-id="d72d2-131">依賴自動繫結重新導向</span><span class="sxs-lookup"><span data-stu-id="d72d2-131">Relying on automatic binding redirection</span></span>  
 <span data-ttu-id="d72d2-132">從 [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)]開始，以 [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] 為目標的新桌面應用程式會使用自動繫結重新導向。</span><span class="sxs-lookup"><span data-stu-id="d72d2-132">Starting with [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], new desktop apps that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] use automatic binding redirection.</span></span> <span data-ttu-id="d72d2-133">這表示如果兩個元件參考了同一個強式名稱組件的不同版本，則執行階段會自動將繫結重新導向加入較新版組件的輸出應用程式設定檔 (app.config)。</span><span class="sxs-lookup"><span data-stu-id="d72d2-133">This means that if two components reference different versions of the same strong-named assembly, the runtime automatically adds a binding redirection to the newer version of the assembly in the output app configuration (app.config) file.</span></span> <span data-ttu-id="d72d2-134">此重新導向會覆寫可能執行的組件統一。</span><span class="sxs-lookup"><span data-stu-id="d72d2-134">This redirection overrides the assembly unification that might otherwise take place.</span></span> <span data-ttu-id="d72d2-135">來源 app.config 檔案則不會加以修改。</span><span class="sxs-lookup"><span data-stu-id="d72d2-135">The source app.config file is not modified.</span></span> <span data-ttu-id="d72d2-136">例如，假設您的應用程式直接參考頻外 .NET Framework 元件，但使用以相同元件較舊版本為目標的協力廠商程式庫。</span><span class="sxs-lookup"><span data-stu-id="d72d2-136">For example, let's say that your app directly references an out-of-band .NET Framework component but uses a third-party library that targets an older version of the same component.</span></span> <span data-ttu-id="d72d2-137">當您編譯應用程式時，輸出應用程式設定檔已修改為包含較新版元件的繫結重新導向。</span><span class="sxs-lookup"><span data-stu-id="d72d2-137">When you compile the app, the output app configuration file is modified to contain a binding redirection to the newer version of the component.</span></span> <span data-ttu-id="d72d2-138">如果您建立的是 Web 應用程式，則會收到有關繫結衝突的建置警告，從而提供您選項將必要的繫結重新導向加入來源 Web 設定檔中。</span><span class="sxs-lookup"><span data-stu-id="d72d2-138">If you create a web app, you receive a build warning regarding the binding conflict, which in turn, gives you the option to add the necessary binding redirect to the source web configuration file.</span></span>  
  
 <span data-ttu-id="d72d2-139">如果您在編譯期間以手動方式將繫結重新導向加入來源 app.config 檔案中， [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] 會嘗試依據您加入的繫結重新導向來統一組件。</span><span class="sxs-lookup"><span data-stu-id="d72d2-139">If you  manually add binding redirects to the source app.config file, at compile time, [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] tries to unify the assemblies based on the binding redirects you added.</span></span> <span data-ttu-id="d72d2-140">例如，假設您為組件插入下列繫結重新導向：</span><span class="sxs-lookup"><span data-stu-id="d72d2-140">For example, let's say you insert the following binding redirect for an assembly:</span></span>  
  
 `<bindingRedirect oldVersion="3.0.0.0" newVersion="2.0.0.0" />`  
  
 <span data-ttu-id="d72d2-141">如果應用程式中另一個專案參考同一個組件的 1.0.0.0 版，自動繫結重新導向會將下列項目加入輸出 app.config 檔案，使得應用程式在此組件的 2.0.0.0 版上統一：</span><span class="sxs-lookup"><span data-stu-id="d72d2-141">If another project in your app references version 1.0.0.0 of the same assembly, automatic binding redirection adds the following entry to the output app.config file so that the app is unified on version 2.0.0.0 of this assembly:</span></span>  
  
 `<bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0" />`  
  
 <span data-ttu-id="d72d2-142">如果您的應用程式以 [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)]中的舊版 .NET Framework 為目標，您可以啟用自動繫結重新導向。</span><span class="sxs-lookup"><span data-stu-id="d72d2-142">You can enable automatic binding redirection if your app targets older versions of the .NET Framework in [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)].</span></span> <span data-ttu-id="d72d2-143">您可以為任何組件提供 app.config 檔中的繫結重新導向資訊，藉此覆寫此預設行為，或關閉繫結重新導向功能。</span><span class="sxs-lookup"><span data-stu-id="d72d2-143">You can override this default behavior by providing binding redirection information in the app.config file for any assembly, or turn off the binding redirection feature.</span></span> <span data-ttu-id="d72d2-144">如需有關如何開啟或關閉這項功能的資訊，請參閱 <<c0> [ 如何： 啟用和停用自動繫結重新導向](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)。</span><span class="sxs-lookup"><span data-stu-id="d72d2-144">For information about how to turn this feature on or off, see [How to: Enable and Disable Automatic Binding Redirection](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md).</span></span>  
  
<a name="bypass_PP"></a>   
### <a name="bypassing-publisher-policy"></a><span data-ttu-id="d72d2-145">略過發行者原則</span><span class="sxs-lookup"><span data-stu-id="d72d2-145">Bypassing publisher policy</span></span>  
 <span data-ttu-id="d72d2-146">您可以在必要時覆寫應用程式設定檔中的發行者原則。</span><span class="sxs-lookup"><span data-stu-id="d72d2-146">You can override publisher policy in the app configuration file if necessary.</span></span> <span data-ttu-id="d72d2-147">例如，宣告與舊版相容的新版組件仍可能中斷應用程式。</span><span class="sxs-lookup"><span data-stu-id="d72d2-147">For example, new versions of assemblies that claim to be backward compatible can still break an app.</span></span> <span data-ttu-id="d72d2-148">如果您想略過發行者原則，新增[ \<publisherPolicy >](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)項目[ \<dependentAssembly >](../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md)組與應用程式組態檔中的項目**套用**屬性設定為**沒有**，它會覆寫任何先前**是**設定。</span><span class="sxs-lookup"><span data-stu-id="d72d2-148">If you want to bypass publisher policy, add a [\<publisherPolicy>](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) element to the [\<dependentAssembly>](../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md) element in the app configuration file, and set the **apply** attribute to **no**, which overrides any previous **yes** settings.</span></span>  
  
 `<publisherPolicy apply="no" />`  
  
 <span data-ttu-id="d72d2-149">略過發行者原則可讓應用程式持續為使用者執行，但請務必將您的問題回報給組件的廠商。</span><span class="sxs-lookup"><span data-stu-id="d72d2-149">Bypass publisher policy to keep your app running for your users, but make sure you report the problem to the assembly vendor.</span></span> <span data-ttu-id="d72d2-150">如果組件有發行者原則檔，廠商應確保該組件與舊版相容，並確保用戶端使用新版時受到最少的限制。</span><span class="sxs-lookup"><span data-stu-id="d72d2-150">If an assembly has a publisher policy file, the vendor should make sure that the assembly is backward compatible and that clients can use the new version as much as possible.</span></span>  
  
<a name="BKMK_Redirectingassemblyversionsatthemachinelevel"></a>   
## <a name="redirecting-assembly-versions-at-the-machine-level"></a><span data-ttu-id="d72d2-151">將電腦層級的組件版本重新導向</span><span class="sxs-lookup"><span data-stu-id="d72d2-151">Redirecting assembly versions at the machine level</span></span>  
 <span data-ttu-id="d72d2-152">電腦系統管理員要讓電腦上所有應用程式都使用特定版本組件的案例很少見。</span><span class="sxs-lookup"><span data-stu-id="d72d2-152">There might be rare cases when a machine administrator wants all apps on a computer to use a specific version of an assembly.</span></span> <span data-ttu-id="d72d2-153">例如，因為特定的組件版本可修正安全性漏洞，所以系統管理員可能會想讓所有應用程式都使用該版本。</span><span class="sxs-lookup"><span data-stu-id="d72d2-153">For example, the administrator might want every app to use a particular assembly version, because that version fixes a security hole.</span></span> <span data-ttu-id="d72d2-154">如果在電腦的設定檔中將組件重新導向，則該電腦上所有使用舊版的應用程式都會重新導向為使用新版。</span><span class="sxs-lookup"><span data-stu-id="d72d2-154">If an assembly is redirected in the machine's configuration file, all apps on that machine that use the old version will be directed to use the new version.</span></span> <span data-ttu-id="d72d2-155">電腦設定檔會覆寫應用程式設定檔和發行者原則檔。</span><span class="sxs-lookup"><span data-stu-id="d72d2-155">The machine configuration file overrides the app configuration file and the publisher policy file.</span></span> <span data-ttu-id="d72d2-156">這個檔案位於 %*runtime install path*%\Config 目錄中。</span><span class="sxs-lookup"><span data-stu-id="d72d2-156">This file is located in the %*runtime install path*%\Config directory.</span></span> <span data-ttu-id="d72d2-157">.NET Framework 通常會安裝在 %drive%\Windows\Microsoft.NET\Framework 目錄中。</span><span class="sxs-lookup"><span data-stu-id="d72d2-157">Typically, the .NET Framework is installed in the %drive%\Windows\Microsoft.NET\Framework directory.</span></span>  
  
<a name="BKMK_Specifyingassemblybindinginconfigurationfiles"></a>   
## <a name="specifying-assembly-binding-in-configuration-files"></a><span data-ttu-id="d72d2-158">指定設定檔中的組件繫結</span><span class="sxs-lookup"><span data-stu-id="d72d2-158">Specifying assembly binding in configuration files</span></span>  
 <span data-ttu-id="d72d2-159">無論繫結重新導向位於應用程式設定檔、電腦設定檔或發行者原則檔，您都可以使用相同的 XML 格式加以指定。</span><span class="sxs-lookup"><span data-stu-id="d72d2-159">You use the same XML format to specify binding redirects whether it’s in the app configuration file, the machine configuration file, or the publisher policy file.</span></span> <span data-ttu-id="d72d2-160">若要將一個組件版本重新導向至另一個，使用[ \<bindingRedirect >](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)項目。</span><span class="sxs-lookup"><span data-stu-id="d72d2-160">To redirect one assembly version to another, use the [\<bindingRedirect>](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md) element.</span></span> <span data-ttu-id="d72d2-161">**oldVersion** 屬性可指定單一或一個範圍的組件版本。</span><span class="sxs-lookup"><span data-stu-id="d72d2-161">The **oldVersion** attribute can specify a single assembly version or a range of versions.</span></span> <span data-ttu-id="d72d2-162">`newVersion` 屬性應指定單一版本。</span><span class="sxs-lookup"><span data-stu-id="d72d2-162">The `newVersion` attribute should specify a single version.</span></span>  <span data-ttu-id="d72d2-163">例如， `<bindingRedirect oldVersion="1.1.0.0-1.2.0.0" newVersion="2.0.0.0"/>` 可指定執行階段使用 2.0.0.0 版，而非指定介於 1.1.0.0 和 1.2.0.0 之間的組件版本。</span><span class="sxs-lookup"><span data-stu-id="d72d2-163">For example, `<bindingRedirect oldVersion="1.1.0.0-1.2.0.0" newVersion="2.0.0.0"/>` specifies that the runtime should use version 2.0.0.0 instead of the assembly versions between 1.1.0.0 and 1.2.0.0.</span></span>  
  
 <span data-ttu-id="d72d2-164">下列程式碼範例示範多種繫結重新導向情節。</span><span class="sxs-lookup"><span data-stu-id="d72d2-164">The following code example demonstrates a variety of binding redirect scenarios.</span></span> <span data-ttu-id="d72d2-165">此範例為一個範圍的 `myAssembly`版本指定重新導向，並為 `mySecondAssembly`指定單一繫結重新導向。</span><span class="sxs-lookup"><span data-stu-id="d72d2-165">The example specifies a redirect for a range of versions for `myAssembly`, and a single binding redirect for `mySecondAssembly`.</span></span> <span data-ttu-id="d72d2-166">範例同時指定發行者原則檔不會覆寫 `myThirdAssembly`的繫結重新導向。</span><span class="sxs-lookup"><span data-stu-id="d72d2-166">The example also specifies that publisher policy file will not override the binding redirects for `myThirdAssembly`.</span></span>  
  
 <span data-ttu-id="d72d2-167">要繫結組件，您必須指定字串"urn: schemas-microsoft-microsoft-com:asm.v1"與**xmlns**屬性中[ \<assemblyBinding >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md)標記。</span><span class="sxs-lookup"><span data-stu-id="d72d2-167">To bind an assembly, you must specify the string "urn:schemas-microsoft-com:asm.v1" with the **xmlns** attribute in the [\<assemblyBinding>](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) tag.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
      <dependentAssembly>  
        <assemblyIdentity name="myAssembly"  
          publicKeyToken="32ab4ba45e0a69a1"  
          culture="en-us" />  
        <!-- Assembly versions can be redirected in app,   
          publisher policy, or machine configuration files. -->  
        <bindingRedirect oldVersion="1.0.0.0-2.0.0.0" newVersion="3.0.0.0" />  
      </dependentAssembly>  
  <dependentAssembly>  
        <assemblyIdentity name="mySecondAssembly"  
          publicKeyToken="32ab4ba45e0a69a1"  
          culture="en-us" />  
             <bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0" />  
      </dependentAssembly>  
      <dependentAssembly>  
      <assemblyIdentity name="myThirdAssembly"  
        publicKeyToken="32ab4ba45e0a69a1"  
        culture="en-us" />  
        <!-- Publisher policy can be set only in the app   
          configuration file. -->  
        <publisherPolicy apply="no" />  
      </dependentAssembly>  
    </assemblyBinding>  
  </runtime>  
</configuration>  
```  
  
### <a name="limiting-assembly--bindings-to-a-specific-version"></a><span data-ttu-id="d72d2-168">將組件繫結限制在特定版本</span><span class="sxs-lookup"><span data-stu-id="d72d2-168">Limiting assembly  bindings to a specific version</span></span>  
 <span data-ttu-id="d72d2-169">您可以使用**appliesTo**屬性上[ \<assemblyBinding >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md)程式來重新導向至特定版本的.net 組件繫結參考的應用程式組態檔中的項目架構。</span><span class="sxs-lookup"><span data-stu-id="d72d2-169">You can use the **appliesTo** attribute on the [\<assemblyBinding>](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) element in an app configuration file to redirect assembly binding references to a specific version of the .NET Framework.</span></span> <span data-ttu-id="d72d2-170">這個選擇性屬性會使用 .NET Framework 版本號碼，以表示它適用於哪一個版本。</span><span class="sxs-lookup"><span data-stu-id="d72d2-170">This optional attribute uses a .NET Framework version number to indicate what version it applies to.</span></span> <span data-ttu-id="d72d2-171">如果未指定 **appliesTo** 屬性，則 [\<assemblyBinding>](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) 項目會套用至所有的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="d72d2-171">If no **appliesTo** attribute is specified, the [\<assemblyBinding>](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) element applies to all versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="d72d2-172">例如，若要將 .NET Framework 3.5 組件的組件繫結重新導向，您會將下列 XML 程式碼加入您的應用程式設定檔中。</span><span class="sxs-lookup"><span data-stu-id="d72d2-172">For example, to redirect assembly binding for a .NET Framework 3.5 assembly, you would include the following XML code in your app configuration file.</span></span>  
  
```xml  
<runtime>  
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1"   
    appliesTo="v3.5">  
    <dependentAssembly>   
      <!-- assembly information goes here -->  
    </dependentAssembly>  
  </assemblyBinding>  
</runtime>  
```  
  
 <span data-ttu-id="d72d2-173">您必須依版本順序輸入重新導向資訊。</span><span class="sxs-lookup"><span data-stu-id="d72d2-173">You should enter redirection information in version order.</span></span> <span data-ttu-id="d72d2-174">例如，請先輸入 .NET Framework 3.5 組件的組件繫結重新導向資訊，接著再輸入 .NET Framework 4.5 組件的資訊。</span><span class="sxs-lookup"><span data-stu-id="d72d2-174">For example, enter assembly binding redirection information for .NET Framework 3.5 assemblies followed by .NET Framework 4.5 assemblies.</span></span> <span data-ttu-id="d72d2-175">最後，請輸入不使用 **appliesTo** 屬性的任何 .NET Framework 組件重新導向之組件繫結重新導向資訊，如此一來會適用於所有版本的 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="d72d2-175">Finally, enter assembly binding redirection information for any .NET Framework assembly redirection that does not use the **appliesTo** attribute and therefore applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="d72d2-176">如果重新導向發生衝突，會使用設定檔中第一筆相符的重新導向陳述式。</span><span class="sxs-lookup"><span data-stu-id="d72d2-176">If there is a conflict in redirection, the first matching redirection statement in the configuration file is used.</span></span>  
  
 <span data-ttu-id="d72d2-177">例如，若要將一個參考重新導向至 .NET Framework 3.5 組件，並將另一個參考重新導向至 .NET Framework 4 組件，則您可以使用下列虛擬程式碼所示的模式。</span><span class="sxs-lookup"><span data-stu-id="d72d2-177">For example, to redirect one reference to a .NET Framework 3.5 assembly and another reference to a .NET Framework 4 assembly, use the pattern shown in the following pseudocode.</span></span>  
  
```xml  
<assemblyBinding xmlns="..." appliesTo="v3.5 ">   
  <!—.NET Framework version 3.5 redirects here -->   
</assemblyBinding>   
  
<assemblyBinding xmlns="..." appliesTo="v4.0.30319">   
  <!—.NET Framework version 4.0 redirects here -->   
</assemblyBinding>   
  
<assemblyBinding xmlns="...">   
  <!-- redirects meant for all versions of the runtime -->   
</assemblyBinding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d72d2-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d72d2-178">See Also</span></span>  
 [<span data-ttu-id="d72d2-179">如何：啟用和停用自動繫結重新導向</span><span class="sxs-lookup"><span data-stu-id="d72d2-179">How to: Enable and Disable Automatic Binding Redirection</span></span>](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)  
 [<span data-ttu-id="d72d2-180">\<bindingRedirect > 項目</span><span class="sxs-lookup"><span data-stu-id="d72d2-180">\<bindingRedirect> Element</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)  
 [<span data-ttu-id="d72d2-181">組件繫結重新導向安全性使用權限</span><span class="sxs-lookup"><span data-stu-id="d72d2-181">Assembly Binding Redirection Security Permission</span></span>](../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md)  
 [<span data-ttu-id="d72d2-182">Common Language Runtime 中的組件</span><span class="sxs-lookup"><span data-stu-id="d72d2-182">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [<span data-ttu-id="d72d2-183">使用組件設計程式</span><span class="sxs-lookup"><span data-stu-id="d72d2-183">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [<span data-ttu-id="d72d2-184">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="d72d2-184">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="d72d2-185">設定應用程式</span><span class="sxs-lookup"><span data-stu-id="d72d2-185">Configuring Apps</span></span>](../../../docs/framework/configure-apps/index.md)  
 [<span data-ttu-id="d72d2-186">設定.NET Framework 應用程式</span><span class="sxs-lookup"><span data-stu-id="d72d2-186">Configuring .NET Framework Apps</span></span>](https://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)  
 [<span data-ttu-id="d72d2-187">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="d72d2-187">Runtime Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="d72d2-188">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="d72d2-188">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="d72d2-189">如何：建立發行者原則</span><span class="sxs-lookup"><span data-stu-id="d72d2-189">How to: Create a Publisher Policy</span></span>](../../../docs/framework/configure-apps/how-to-create-a-publisher-policy.md)
