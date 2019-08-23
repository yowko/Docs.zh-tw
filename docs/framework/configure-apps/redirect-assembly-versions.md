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
ms.openlocfilehash: c9670b00ea4a6b552469b7f33e924b8ab128d9d0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948031"
---
# <a name="redirecting-assembly-versions"></a><span data-ttu-id="e747a-102">重新導向組件版本</span><span class="sxs-lookup"><span data-stu-id="e747a-102">Redirecting Assembly Versions</span></span>

<span data-ttu-id="e747a-103">您可以將編譯時間繫結參考重新導向至 .NET Framework 組件、協力廠商組件或您自己的應用程式組件。</span><span class="sxs-lookup"><span data-stu-id="e747a-103">You can redirect compile-time binding references to .NET Framework assemblies, third-party assemblies, or your own app's assemblies.</span></span> <span data-ttu-id="e747a-104">您可以用多種方式將應用程式重新導向為使用其他版本的組件：透過發行者原則、透過應用程式設定檔或透過電腦設定檔。</span><span class="sxs-lookup"><span data-stu-id="e747a-104">You can redirect your app to use a different version of an assembly in a number of ways: through publisher policy, through an app configuration file; or through the machine configuration file.</span></span> <span data-ttu-id="e747a-105">本文討論 .NET Framework 中的組件繫結如何運作，以及其設定方式。</span><span class="sxs-lookup"><span data-stu-id="e747a-105">This article discusses how assembly binding works in the .NET Framework and how it can be configured.</span></span>

<a name="BKMK_Assemblyunificationanddefaultbinding"></a>
## <a name="assembly-unification-and-default-binding"></a><span data-ttu-id="e747a-106">組件統一和預設繫結</span><span class="sxs-lookup"><span data-stu-id="e747a-106">Assembly unification and default binding</span></span>
 <span data-ttu-id="e747a-107">.NET Framework 組件的繫結有時會透過名為 *「組件統一」* (assembly unification) 的處理序進行重新導向。</span><span class="sxs-lookup"><span data-stu-id="e747a-107">Bindings to .NET Framework assemblies are sometimes redirected through a process called *assembly unification*.</span></span> <span data-ttu-id="e747a-108">.NET Framework 包含某個版本的通用語言執行平台，以及大約二十多個組成類型程式庫的 .NET Framework 組件。</span><span class="sxs-lookup"><span data-stu-id="e747a-108">The .NET Framework consists of a version of the common language runtime and about two dozen .NET Framework assemblies that make up the type library.</span></span> <span data-ttu-id="e747a-109">執行階段將這些 .NET Framework 組件視為單一單位。</span><span class="sxs-lookup"><span data-stu-id="e747a-109">These .NET Framework assemblies are treated by the runtime as a single unit.</span></span> <span data-ttu-id="e747a-110">根據預設，應用程式啟動時，任何類型參考只要位於執行階段所執行的程式碼中，都會導向至 .NET Framework 組件；且該組建將與載入處理序的執行階段具有相同的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="e747a-110">By default, when an app is launched, all references to types in code run by the runtime are directed to .NET Framework assemblies that have the same version number as the runtime that is loaded in a process.</span></span> <span data-ttu-id="e747a-111">與此模型同時發生的重新導向，皆為執行階段的預設行為。</span><span class="sxs-lookup"><span data-stu-id="e747a-111">The redirections that occur with this model are the default behavior for the runtime.</span></span>

 <span data-ttu-id="e747a-112">例如, 如果您的應用程式參考了 system.string 命名空間中的類型, 而且是使用 .NET Framework 4.5 建立的, 它就會包含執行階段版本4.5 隨附之 system.string 元件的靜態參考。</span><span class="sxs-lookup"><span data-stu-id="e747a-112">For example, if your app references types in the System.XML namespace and was built by using the .NET Framework 4.5, it contains static references to the System.XML assembly that ships with runtime version 4.5.</span></span> <span data-ttu-id="e747a-113">如果您要將點的繫結參考重新導向至隨附於 .NET Framework 4 的 System.XML 組件，可以將重新導向資訊放在應用程式設定檔中。</span><span class="sxs-lookup"><span data-stu-id="e747a-113">If you want to redirect the binding reference to point to the System.XML assembly that ship with the .NET Framework 4, you can put redirect information in the app configuration file.</span></span> <span data-ttu-id="e747a-114">統一的 .NET Framework 組件之設定檔中的繫結重新導向會取消統一該組件。</span><span class="sxs-lookup"><span data-stu-id="e747a-114">A binding redirection in a configuration file for a unified .NET Framework assembly cancels the unification for that assembly.</span></span>

 <span data-ttu-id="e747a-115">此外，如果有多個可用版本，您可能會想要以手動方式將協力廠商組件的組件繫結重新導向。</span><span class="sxs-lookup"><span data-stu-id="e747a-115">In addition, you may want to manually redirect assembly binding for third-party assemblies if there are multiple versions available.</span></span>

<a name="BKMK_Redirectingassemblyversionsbyusingpublisherpolicy"></a>
## <a name="redirecting-assembly-versions-by-using-publisher-policy"></a><span data-ttu-id="e747a-116">使用發行者原則將組件版本重新導向</span><span class="sxs-lookup"><span data-stu-id="e747a-116">Redirecting assembly versions by using publisher policy</span></span>
 <span data-ttu-id="e747a-117">組件的廠商可以加入具有新組件的發行者原則檔，藉此將應用程式導向至較新版的組件。</span><span class="sxs-lookup"><span data-stu-id="e747a-117">Vendors of assemblies can direct apps to a newer version of an assembly by including a publisher policy file with the new assembly.</span></span> <span data-ttu-id="e747a-118">發行者原則檔位於全域組件快取，其中包含組件重新導向設定。</span><span class="sxs-lookup"><span data-stu-id="e747a-118">The publisher policy file, which is located in the global assembly cache, contains assembly redirection settings.</span></span>

 <span data-ttu-id="e747a-119">組件的每個主要.次要 版本都有自己的發行者原則檔。</span><span class="sxs-lookup"><span data-stu-id="e747a-119">Each *major*.*minor* version of an assembly has its own publisher policy file.</span></span> <span data-ttu-id="e747a-120">例如，從 2.0.2.222 版重新導向至 2.0.3.000 版，以及從 2.0.2.321 版重新導向至 2.0.3.000 版，兩者的目標檔案皆相同，因為已透過 2.0 版建立了關係。</span><span class="sxs-lookup"><span data-stu-id="e747a-120">For example, redirections from version 2.0.2.222 to 2.0.3.000 and from version 2.0.2.321 to version 2.0.3.000 both go into the same file, because they are associated with version 2.0.</span></span> <span data-ttu-id="e747a-121">然而，從 3.0.0.999 版重新導向至 4.0.0.000 版則會傳入 3.0.999 版的檔案。</span><span class="sxs-lookup"><span data-stu-id="e747a-121">However, a redirection from version 3.0.0.999 to version 4.0.0.000 goes into the file for version 3.0.999.</span></span> <span data-ttu-id="e747a-122">.NET Framework 的每個主要版本都有自己的發行者原則檔。</span><span class="sxs-lookup"><span data-stu-id="e747a-122">Each major version of the .NET Framework has its own publisher policy file.</span></span>

 <span data-ttu-id="e747a-123">如果組件有發行者原則檔，則執行階段會在檢查組件的資訊清單和應用程式設定檔後，檢查此檔案。</span><span class="sxs-lookup"><span data-stu-id="e747a-123">If a publisher policy file exists for an assembly, the runtime checks this file after checking the assembly's manifest and app configuration file.</span></span> <span data-ttu-id="e747a-124">廠商必須只在新組件與重新導向的舊版組件相容時，才使用發行者原則檔。</span><span class="sxs-lookup"><span data-stu-id="e747a-124">Vendors should use publisher policy files only when the new assembly is backward compatible with the assembly being redirected.</span></span>

 <span data-ttu-id="e747a-125">您可以指定應用程式設定檔中的設定，藉此略過應用程式的發行者原則，方法詳述於 [略過發行者原則章節](#bypass_PP)。</span><span class="sxs-lookup"><span data-stu-id="e747a-125">You can bypass publisher policy for your app by specifying settings in the app configuration file, as discussed in the [Bypassing publisher policy section](#bypass_PP).</span></span>

<a name="BKMK_Redirectingassemblyversionsattheapplevel"></a>
## <a name="redirecting-assembly-versions-at-the-app-level"></a><span data-ttu-id="e747a-126">將應用程式層級的組件版本重新導向</span><span class="sxs-lookup"><span data-stu-id="e747a-126">Redirecting assembly versions at the app level</span></span>
 <span data-ttu-id="e747a-127">有數種不同技術可透過應用程式設定檔變更應用程式的繫結行為：您可以手動編輯應用程式設定檔、可以依賴自動繫結重新導向，也可以略過發行者原則以指定繫結行為。</span><span class="sxs-lookup"><span data-stu-id="e747a-127">There are a few different techniques for changing the binding behavior for your app through the app configuration file: you can manually edit the file, you can rely on automatic binding redirection, or you can specify binding behavior by bypassing publisher policy.</span></span>

### <a name="manually-editing-the-app-config-file"></a><span data-ttu-id="e747a-128">手動編輯應用程式設定檔</span><span class="sxs-lookup"><span data-stu-id="e747a-128">Manually editing the app config file</span></span>
 <span data-ttu-id="e747a-129">您可以手動編輯應用程式設定檔以解決組件問題。</span><span class="sxs-lookup"><span data-stu-id="e747a-129">You can manually edit the app configuration file to resolve assembly issues.</span></span> <span data-ttu-id="e747a-130">例如，如果廠商可能發行您應用程式所使用的組件較新版本，但因為不保證與舊版相容而未提供發行者原則，則可以將組件繫結資訊放在應用程式的設定檔中 (如下所示)，藉此將應用程式重新導向為使用較新版的組件。</span><span class="sxs-lookup"><span data-stu-id="e747a-130">For example, if a vendor might release a newer version of an assembly that your app uses without supplying a publisher policy, because they do not guarantee backward compatibility, you can direct your app to use the newer version of the assembly by putting assembly binding information in your app's configuration file as follows.</span></span>

```xml
<dependentAssembly>
  <assemblyIdentity name="someAssembly"
    publicKeyToken="32ab4ba45e0a69a1"
    culture="en-us" />
  <bindingRedirect oldVersion="7.0.0.0" newVersion="8.0.0.0" />
</dependentAssembly>
```

### <a name="relying-on-automatic-binding-redirection"></a><span data-ttu-id="e747a-131">依賴自動繫結重新導向</span><span class="sxs-lookup"><span data-stu-id="e747a-131">Relying on automatic binding redirection</span></span>

<span data-ttu-id="e747a-132">當您在以 .NET Framework 4.5.1 或更新版本為目標的 Visual Studio 中建立桌面應用程式時, 應用程式會使用自動系結重新導向。</span><span class="sxs-lookup"><span data-stu-id="e747a-132">When you create a desktop app in Visual Studio that targets the .NET Framework 4.5.1 or a later version, the app uses automatic binding redirection.</span></span> <span data-ttu-id="e747a-133">這表示如果兩個元件參考了同一個強式名稱組件的不同版本，則執行階段會自動將繫結重新導向加入較新版組件的輸出應用程式設定檔 (app.config)。</span><span class="sxs-lookup"><span data-stu-id="e747a-133">This means that if two components reference different versions of the same strong-named assembly, the runtime automatically adds a binding redirection to the newer version of the assembly in the output app configuration (app.config) file.</span></span> <span data-ttu-id="e747a-134">此重新導向會覆寫可能執行的組件統一。</span><span class="sxs-lookup"><span data-stu-id="e747a-134">This redirection overrides the assembly unification that might otherwise take place.</span></span> <span data-ttu-id="e747a-135">來源 app.config 檔案則不會加以修改。</span><span class="sxs-lookup"><span data-stu-id="e747a-135">The source app.config file is not modified.</span></span> <span data-ttu-id="e747a-136">例如，假設您的應用程式直接參考頻外 .NET Framework 元件，但使用以相同元件較舊版本為目標的協力廠商程式庫。</span><span class="sxs-lookup"><span data-stu-id="e747a-136">For example, let's say that your app directly references an out-of-band .NET Framework component but uses a third-party library that targets an older version of the same component.</span></span> <span data-ttu-id="e747a-137">當您編譯應用程式時，輸出應用程式設定檔已修改為包含較新版元件的繫結重新導向。</span><span class="sxs-lookup"><span data-stu-id="e747a-137">When you compile the app, the output app configuration file is modified to contain a binding redirection to the newer version of the component.</span></span> <span data-ttu-id="e747a-138">如果您建立的是 Web 應用程式，則會收到有關繫結衝突的建置警告，從而提供您選項將必要的繫結重新導向加入來源 Web 設定檔中。</span><span class="sxs-lookup"><span data-stu-id="e747a-138">If you create a web app, you receive a build warning regarding the binding conflict, which in turn, gives you the option to add the necessary binding redirect to the source web configuration file.</span></span>

<span data-ttu-id="e747a-139">如果您以手動方式將系結重新導向加入至來源 app.config 檔案, 在編譯時期, Visual Studio 會嘗試根據您新增的系結重新導向來整合元件。</span><span class="sxs-lookup"><span data-stu-id="e747a-139">If you manually add binding redirects to the source app.config file, at compile time, Visual Studio tries to unify the assemblies based on the binding redirects you added.</span></span> <span data-ttu-id="e747a-140">例如，假設您為組件插入下列繫結重新導向：</span><span class="sxs-lookup"><span data-stu-id="e747a-140">For example, let's say you insert the following binding redirect for an assembly:</span></span>

`<bindingRedirect oldVersion="3.0.0.0" newVersion="2.0.0.0" />`

<span data-ttu-id="e747a-141">如果應用程式中另一個專案參考同一個組件的 1.0.0.0 版，自動繫結重新導向會將下列項目加入輸出 app.config 檔案，使得應用程式在此組件的 2.0.0.0 版上統一：</span><span class="sxs-lookup"><span data-stu-id="e747a-141">If another project in your app references version 1.0.0.0 of the same assembly, automatic binding redirection adds the following entry to the output app.config file so that the app is unified on version 2.0.0.0 of this assembly:</span></span>

`<bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0" />`

<span data-ttu-id="e747a-142">如果您的應用程式是以較舊版本的 .NET Framework 為目標, 您可以啟用自動系結重新導向。</span><span class="sxs-lookup"><span data-stu-id="e747a-142">You can enable automatic binding redirection if your app targets older versions of the .NET Framework.</span></span> <span data-ttu-id="e747a-143">您可以覆寫此預設行為, 方法是在 app.config 檔案中提供任何元件的系結重新導向資訊, 或關閉系結重新導向功能。</span><span class="sxs-lookup"><span data-stu-id="e747a-143">You can override this default behavior by providing binding redirection information in the app.config file for any assembly, or by turning off the binding redirection feature.</span></span> <span data-ttu-id="e747a-144">如需如何開啟或關閉此功能的相關資訊, 請[參閱如何:啟用和停用自動繫結重新導向](how-to-enable-and-disable-automatic-binding-redirection.md)。</span><span class="sxs-lookup"><span data-stu-id="e747a-144">For information about how to turn this feature on or off, see [How to: Enable and Disable Automatic Binding Redirection](how-to-enable-and-disable-automatic-binding-redirection.md).</span></span>

<a name="bypass_PP"></a>
### <a name="bypassing-publisher-policy"></a><span data-ttu-id="e747a-145">略過發行者原則</span><span class="sxs-lookup"><span data-stu-id="e747a-145">Bypassing publisher policy</span></span>
 <span data-ttu-id="e747a-146">您可以在必要時覆寫應用程式設定檔中的發行者原則。</span><span class="sxs-lookup"><span data-stu-id="e747a-146">You can override publisher policy in the app configuration file if necessary.</span></span> <span data-ttu-id="e747a-147">例如，宣告與舊版相容的新版組件仍可能中斷應用程式。</span><span class="sxs-lookup"><span data-stu-id="e747a-147">For example, new versions of assemblies that claim to be backward compatible can still break an app.</span></span> <span data-ttu-id="e747a-148">如果您想要略過發行者原則, 請將[ \<publisherPolicy >](./file-schema/runtime/publisherpolicy-element.md)元素新增至應用程式佈建檔中的[ \<dependentAssembly >](./file-schema/runtime/dependentassembly-element.md)專案, 並將 [套用屬性] 設定為 [**否**],覆寫任何先前的**yes**設定。</span><span class="sxs-lookup"><span data-stu-id="e747a-148">If you want to bypass publisher policy, add a [\<publisherPolicy>](./file-schema/runtime/publisherpolicy-element.md) element to the [\<dependentAssembly>](./file-schema/runtime/dependentassembly-element.md) element in the app configuration file, and set the **apply** attribute to **no**, which overrides any previous **yes** settings.</span></span>

 `<publisherPolicy apply="no" />`

 <span data-ttu-id="e747a-149">略過發行者原則可讓應用程式持續為使用者執行，但請務必將您的問題回報給組件的廠商。</span><span class="sxs-lookup"><span data-stu-id="e747a-149">Bypass publisher policy to keep your app running for your users, but make sure you report the problem to the assembly vendor.</span></span> <span data-ttu-id="e747a-150">如果組件有發行者原則檔，廠商應確保該組件與舊版相容，並確保用戶端使用新版時受到最少的限制。</span><span class="sxs-lookup"><span data-stu-id="e747a-150">If an assembly has a publisher policy file, the vendor should make sure that the assembly is backward compatible and that clients can use the new version as much as possible.</span></span>

<a name="BKMK_Redirectingassemblyversionsatthemachinelevel"></a>
## <a name="redirecting-assembly-versions-at-the-machine-level"></a><span data-ttu-id="e747a-151">將電腦層級的組件版本重新導向</span><span class="sxs-lookup"><span data-stu-id="e747a-151">Redirecting assembly versions at the machine level</span></span>
 <span data-ttu-id="e747a-152">電腦系統管理員要讓電腦上所有應用程式都使用特定版本組件的案例很少見。</span><span class="sxs-lookup"><span data-stu-id="e747a-152">There might be rare cases when a machine administrator wants all apps on a computer to use a specific version of an assembly.</span></span> <span data-ttu-id="e747a-153">例如，因為特定的組件版本可修正安全性漏洞，所以系統管理員可能會想讓所有應用程式都使用該版本。</span><span class="sxs-lookup"><span data-stu-id="e747a-153">For example, the administrator might want every app to use a particular assembly version, because that version fixes a security hole.</span></span> <span data-ttu-id="e747a-154">如果在電腦的設定檔中將組件重新導向，則該電腦上所有使用舊版的應用程式都會重新導向為使用新版。</span><span class="sxs-lookup"><span data-stu-id="e747a-154">If an assembly is redirected in the machine's configuration file, all apps on that machine that use the old version will be directed to use the new version.</span></span> <span data-ttu-id="e747a-155">電腦設定檔會覆寫應用程式設定檔和發行者原則檔。</span><span class="sxs-lookup"><span data-stu-id="e747a-155">The machine configuration file overrides the app configuration file and the publisher policy file.</span></span> <span data-ttu-id="e747a-156">這個檔案位於 %*runtime install path*%\Config 目錄中。</span><span class="sxs-lookup"><span data-stu-id="e747a-156">This file is located in the %*runtime install path*%\Config directory.</span></span> <span data-ttu-id="e747a-157">.NET Framework 通常會安裝在 %drive%\Windows\Microsoft.NET\Framework 目錄中。</span><span class="sxs-lookup"><span data-stu-id="e747a-157">Typically, the .NET Framework is installed in the %drive%\Windows\Microsoft.NET\Framework directory.</span></span>

<a name="BKMK_Specifyingassemblybindinginconfigurationfiles"></a>
## <a name="specifying-assembly-binding-in-configuration-files"></a><span data-ttu-id="e747a-158">指定設定檔中的組件繫結</span><span class="sxs-lookup"><span data-stu-id="e747a-158">Specifying assembly binding in configuration files</span></span>
 <span data-ttu-id="e747a-159">無論繫結重新導向位於應用程式設定檔、電腦設定檔或發行者原則檔，您都可以使用相同的 XML 格式加以指定。</span><span class="sxs-lookup"><span data-stu-id="e747a-159">You use the same XML format to specify binding redirects whether it’s in the app configuration file, the machine configuration file, or the publisher policy file.</span></span> <span data-ttu-id="e747a-160">若要將一個元件版本重新導向至另一個, 請使用[ \<bindingRedirect >](./file-schema/runtime/bindingredirect-element.md)元素。</span><span class="sxs-lookup"><span data-stu-id="e747a-160">To redirect one assembly version to another, use the [\<bindingRedirect>](./file-schema/runtime/bindingredirect-element.md) element.</span></span> <span data-ttu-id="e747a-161">**oldVersion** 屬性可指定單一或一個範圍的組件版本。</span><span class="sxs-lookup"><span data-stu-id="e747a-161">The **oldVersion** attribute can specify a single assembly version or a range of versions.</span></span> <span data-ttu-id="e747a-162">`newVersion` 屬性應指定單一版本。</span><span class="sxs-lookup"><span data-stu-id="e747a-162">The `newVersion` attribute should specify a single version.</span></span>  <span data-ttu-id="e747a-163">例如， `<bindingRedirect oldVersion="1.1.0.0-1.2.0.0" newVersion="2.0.0.0"/>` 可指定執行階段使用 2.0.0.0 版，而非指定介於 1.1.0.0 和 1.2.0.0 之間的組件版本。</span><span class="sxs-lookup"><span data-stu-id="e747a-163">For example, `<bindingRedirect oldVersion="1.1.0.0-1.2.0.0" newVersion="2.0.0.0"/>` specifies that the runtime should use version 2.0.0.0 instead of the assembly versions between 1.1.0.0 and 1.2.0.0.</span></span>

 <span data-ttu-id="e747a-164">下列程式碼範例示範多種繫結重新導向情節。</span><span class="sxs-lookup"><span data-stu-id="e747a-164">The following code example demonstrates a variety of binding redirect scenarios.</span></span> <span data-ttu-id="e747a-165">此範例為一個範圍的 `myAssembly`版本指定重新導向，並為 `mySecondAssembly`指定單一繫結重新導向。</span><span class="sxs-lookup"><span data-stu-id="e747a-165">The example specifies a redirect for a range of versions for `myAssembly`, and a single binding redirect for `mySecondAssembly`.</span></span> <span data-ttu-id="e747a-166">範例同時指定發行者原則檔不會覆寫 `myThirdAssembly`的繫結重新導向。</span><span class="sxs-lookup"><span data-stu-id="e747a-166">The example also specifies that publisher policy file will not override the binding redirects for `myThirdAssembly`.</span></span>

 <span data-ttu-id="e747a-167">若要系結元件, 您必須在[ \<assemblyBinding >](./file-schema/runtime/assemblybinding-element-for-runtime.md)標籤中, 以**xmlns**屬性指定字串 "urn: 架構-microsoft-com: asm. v1"。</span><span class="sxs-lookup"><span data-stu-id="e747a-167">To bind an assembly, you must specify the string "urn:schemas-microsoft-com:asm.v1" with the **xmlns** attribute in the [\<assemblyBinding>](./file-schema/runtime/assemblybinding-element-for-runtime.md) tag.</span></span>

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

### <a name="limiting-assembly--bindings-to-a-specific-version"></a><span data-ttu-id="e747a-168">將組件繫結限制在特定版本</span><span class="sxs-lookup"><span data-stu-id="e747a-168">Limiting assembly  bindings to a specific version</span></span>
 <span data-ttu-id="e747a-169">您可以使用應用程式佈建檔中[ \<assemblyBinding >](./file-schema/runtime/assemblybinding-element-for-runtime.md)元素上的**appliesTo**屬性, 將元件系結參考重新導向至特定版本的 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="e747a-169">You can use the **appliesTo** attribute on the [\<assemblyBinding>](./file-schema/runtime/assemblybinding-element-for-runtime.md) element in an app configuration file to redirect assembly binding references to a specific version of the .NET Framework.</span></span> <span data-ttu-id="e747a-170">這個選擇性屬性會使用 .NET Framework 版本號碼，以表示它適用於哪一個版本。</span><span class="sxs-lookup"><span data-stu-id="e747a-170">This optional attribute uses a .NET Framework version number to indicate what version it applies to.</span></span> <span data-ttu-id="e747a-171">如果未指定 **appliesTo** 屬性，則 [\<assemblyBinding>](./file-schema/runtime/assemblybinding-element-for-runtime.md) 項目會套用至所有的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="e747a-171">If no **appliesTo** attribute is specified, the [\<assemblyBinding>](./file-schema/runtime/assemblybinding-element-for-runtime.md) element applies to all versions of the .NET Framework.</span></span>

 <span data-ttu-id="e747a-172">例如，若要將 .NET Framework 3.5 組件的組件繫結重新導向，您會將下列 XML 程式碼加入您的應用程式設定檔中。</span><span class="sxs-lookup"><span data-stu-id="e747a-172">For example, to redirect assembly binding for a .NET Framework 3.5 assembly, you would include the following XML code in your app configuration file.</span></span>

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

 <span data-ttu-id="e747a-173">您必須依版本順序輸入重新導向資訊。</span><span class="sxs-lookup"><span data-stu-id="e747a-173">You should enter redirection information in version order.</span></span> <span data-ttu-id="e747a-174">例如，請先輸入 .NET Framework 3.5 組件的組件繫結重新導向資訊，接著再輸入 .NET Framework 4.5 組件的資訊。</span><span class="sxs-lookup"><span data-stu-id="e747a-174">For example, enter assembly binding redirection information for .NET Framework 3.5 assemblies followed by .NET Framework 4.5 assemblies.</span></span> <span data-ttu-id="e747a-175">最後，請輸入不使用 **appliesTo** 屬性的任何 .NET Framework 組件重新導向之組件繫結重新導向資訊，如此一來會適用於所有版本的 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="e747a-175">Finally, enter assembly binding redirection information for any .NET Framework assembly redirection that does not use the **appliesTo** attribute and therefore applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="e747a-176">如果重新導向發生衝突，會使用設定檔中第一筆相符的重新導向陳述式。</span><span class="sxs-lookup"><span data-stu-id="e747a-176">If there is a conflict in redirection, the first matching redirection statement in the configuration file is used.</span></span>

 <span data-ttu-id="e747a-177">例如，若要將一個參考重新導向至 .NET Framework 3.5 組件，並將另一個參考重新導向至 .NET Framework 4 組件，則您可以使用下列虛擬程式碼所示的模式。</span><span class="sxs-lookup"><span data-stu-id="e747a-177">For example, to redirect one reference to a .NET Framework 3.5 assembly and another reference to a .NET Framework 4 assembly, use the pattern shown in the following pseudocode.</span></span>

```xml
<assemblyBinding xmlns="..." appliesTo="v3.5 ">
  <!--.NET Framework version 3.5 redirects here -->
</assemblyBinding>

<assemblyBinding xmlns="..." appliesTo="v4.0.30319">
  <!--.NET Framework version 4.0 redirects here -->
</assemblyBinding>

<assemblyBinding xmlns="...">
  <!-- redirects meant for all versions of the runtime -->
</assemblyBinding>
```

## <a name="see-also"></a><span data-ttu-id="e747a-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e747a-178">See also</span></span>

- [<span data-ttu-id="e747a-179">如何：啟用和停用自動繫結重新導向</span><span class="sxs-lookup"><span data-stu-id="e747a-179">How to: Enable and Disable Automatic Binding Redirection</span></span>](how-to-enable-and-disable-automatic-binding-redirection.md)
- [<span data-ttu-id="e747a-180">\<bindingRedirect > 元素</span><span class="sxs-lookup"><span data-stu-id="e747a-180">\<bindingRedirect> Element</span></span>](./file-schema/runtime/bindingredirect-element.md)
- [<span data-ttu-id="e747a-181">組件繫結重新導向安全性使用權限</span><span class="sxs-lookup"><span data-stu-id="e747a-181">Assembly Binding Redirection Security Permission</span></span>](assembly-binding-redirection-security-permission.md)
- [<span data-ttu-id="e747a-182">Common Language Runtime 中的組件</span><span class="sxs-lookup"><span data-stu-id="e747a-182">Assemblies in the Common Language Runtime</span></span>](../app-domains/assemblies-in-the-common-language-runtime.md)
- [<span data-ttu-id="e747a-183">使用組件設計程式</span><span class="sxs-lookup"><span data-stu-id="e747a-183">Programming with Assemblies</span></span>](../app-domains/programming-with-assemblies.md)
- [<span data-ttu-id="e747a-184">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="e747a-184">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="e747a-185">設定應用程式</span><span class="sxs-lookup"><span data-stu-id="e747a-185">Configuring Apps</span></span>](index.md)
- [<span data-ttu-id="e747a-186">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="e747a-186">Runtime Settings Schema</span></span>](./file-schema/runtime/index.md)
- [<span data-ttu-id="e747a-187">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="e747a-187">Configuration File Schema</span></span>](./file-schema/index.md)
- [<span data-ttu-id="e747a-188">如何：建立發行者原則</span><span class="sxs-lookup"><span data-stu-id="e747a-188">How to: Create a Publisher Policy</span></span>](how-to-create-a-publisher-policy.md)
