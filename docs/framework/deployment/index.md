---
title: 部署 .NET Framework 和應用程式
description: 開始使用您的應用程式來部署 .NET。 .NET 預設會提供不影響的應用程式、私用元件、控制的程式碼共用等等。
ms.date: 03/30/2017
helpviewer_keywords:
- deploying applications [.NET Framework], packaging
- deploying applications [.NET Framework]
- deploying applications [.NET Framework], features
- deploying applications [.NET Framework], distribution
- .NET Framework, deploying
- .NET Framework application deployment
ms.assetid: 238d8284-6042-4a38-a7f6-1ee8efd719da
ms.openlocfilehash: cce888c962c9ab83c13cce4040eb9ba50270972d
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803493"
---
# <a name="deploying-the-net-framework-and-applications"></a><span data-ttu-id="c0f12-104">部署 .NET Framework 和應用程式</span><span class="sxs-lookup"><span data-stu-id="c0f12-104">Deploying the .NET Framework and Applications</span></span>

<span data-ttu-id="c0f12-105">本文將協助您開始在應用程式上部署 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="c0f12-105">This article helps you get started deploying the .NET Framework with your application.</span></span> <span data-ttu-id="c0f12-106">大部分資訊的目標對象是開發人員、OEM 和企業系統管理員。</span><span class="sxs-lookup"><span data-stu-id="c0f12-106">Most of the information is intended for developers, OEMs, and enterprise administrators.</span></span> <span data-ttu-id="c0f12-107">想要在電腦上安裝 .NET Framework 的使用者應閱讀[安裝 .NET Framework](../install/index.md)。</span><span class="sxs-lookup"><span data-stu-id="c0f12-107">Users who want to install the .NET Framework on their computers should read [Installing the .NET Framework](../install/index.md).</span></span>

## <a name="key-deployment-resources"></a><span data-ttu-id="c0f12-108">主要部署資源</span><span class="sxs-lookup"><span data-stu-id="c0f12-108">Key Deployment Resources</span></span>

<span data-ttu-id="c0f12-109">使用下列連結連接至其他 MSDN 主題，了解有關 .NET Framework 部署和服務的特定資訊。</span><span class="sxs-lookup"><span data-stu-id="c0f12-109">Use the following links to other MSDN topics for specific information about deploying and servicing the .NET Framework.</span></span>

<span data-ttu-id="c0f12-110">**安裝和部署**</span><span class="sxs-lookup"><span data-stu-id="c0f12-110">**Setup and deployment**</span></span>

- <span data-ttu-id="c0f12-111">一般安裝程式和部署資訊：</span><span class="sxs-lookup"><span data-stu-id="c0f12-111">General installer and deployment information:</span></span>

  - <span data-ttu-id="c0f12-112">安裝程式選項：</span><span class="sxs-lookup"><span data-stu-id="c0f12-112">Installer options:</span></span>

    - [<span data-ttu-id="c0f12-113">Web 安裝程式</span><span class="sxs-lookup"><span data-stu-id="c0f12-113">Web installer</span></span>](../install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

    - [<span data-ttu-id="c0f12-114">離線安裝程式</span><span class="sxs-lookup"><span data-stu-id="c0f12-114">Offline installer</span></span>](../install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

  - <span data-ttu-id="c0f12-115">安裝模式：</span><span class="sxs-lookup"><span data-stu-id="c0f12-115">Installation modes:</span></span>

    - [<span data-ttu-id="c0f12-116">無訊息安裝</span><span class="sxs-lookup"><span data-stu-id="c0f12-116">Silent installation</span></span>](deployment-guide-for-developers.md#chaining_custom)

    - [<span data-ttu-id="c0f12-117">顯示 UI</span><span class="sxs-lookup"><span data-stu-id="c0f12-117">Displaying a UI</span></span>](deployment-guide-for-developers.md#chaining_default)

  - [<span data-ttu-id="c0f12-118">在 .NET Framework 4.5 安裝期間減少系統重新啟動的次數</span><span class="sxs-lookup"><span data-stu-id="c0f12-118">Reducing system restarts during .NET Framework 4.5 installations</span></span>](reducing-system-restarts.md)

  - [<span data-ttu-id="c0f12-119">疑難排解 .NET Framework 安裝和解除安裝遭封鎖的問題</span><span class="sxs-lookup"><span data-stu-id="c0f12-119">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](../install/troubleshoot-blocked-installations-and-uninstallations.md)

- <span data-ttu-id="c0f12-120">在用戶端應用程式上部署 .NET Framework (適用於開發人員)：</span><span class="sxs-lookup"><span data-stu-id="c0f12-120">Deploying the .NET Framework with a client application (for developers):</span></span>

  - <span data-ttu-id="c0f12-121">在安裝和部署專案中[使用 InstallShield](deployment-guide-for-developers.md#installshield-deployment)</span><span class="sxs-lookup"><span data-stu-id="c0f12-121">[Using InstallShield](deployment-guide-for-developers.md#installshield-deployment) in a setup and deployment project</span></span>

  - [<span data-ttu-id="c0f12-122">使用 Visual Studio ClickOnce 應用程式</span><span class="sxs-lookup"><span data-stu-id="c0f12-122">Using a Visual Studio ClickOnce application</span></span>](deployment-guide-for-developers.md#clickonce-deployment)

  - [<span data-ttu-id="c0f12-123">建立 WiX 安裝套件</span><span class="sxs-lookup"><span data-stu-id="c0f12-123">Creating a WiX installation package</span></span>](deployment-guide-for-developers.md#wix)

  - [<span data-ttu-id="c0f12-124">使用自訂安裝程式</span><span class="sxs-lookup"><span data-stu-id="c0f12-124">Using a custom installer</span></span>](deployment-guide-for-developers.md#chaining)

  - <span data-ttu-id="c0f12-125">適用於開發人員的[其他資訊](deployment-guide-for-developers.md)</span><span class="sxs-lookup"><span data-stu-id="c0f12-125">[Additional information](deployment-guide-for-developers.md) for developers</span></span>

- <span data-ttu-id="c0f12-126">部署 .NET Framework (適用於 OEM 和系統管理員)：</span><span class="sxs-lookup"><span data-stu-id="c0f12-126">Deploying the .NET Framework (for OEMs and administrators):</span></span>

  - [<span data-ttu-id="c0f12-127">Windows 評定及部署套件 (ADK)</span><span class="sxs-lookup"><span data-stu-id="c0f12-127">Windows Assessment and Deployment Kit (ADK)</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=254976)

  - [<span data-ttu-id="c0f12-128">系統管理員手冊</span><span class="sxs-lookup"><span data-stu-id="c0f12-128">Administrator's guide</span></span>](guide-for-administrators.md)

<span data-ttu-id="c0f12-129">**服務**</span><span class="sxs-lookup"><span data-stu-id="c0f12-129">**Servicing**</span></span>

- <span data-ttu-id="c0f12-130">如需一般資訊，請參閱[.NET Framework 的 blog](https://devblogs.microsoft.com/dotnet/)。</span><span class="sxs-lookup"><span data-stu-id="c0f12-130">For general information, see the [.NET Framework blog](https://devblogs.microsoft.com/dotnet/).</span></span>

- [<span data-ttu-id="c0f12-131">偵測版本</span><span class="sxs-lookup"><span data-stu-id="c0f12-131">Detecting versions</span></span>](../migration-guide/how-to-determine-which-versions-are-installed.md)

- [<span data-ttu-id="c0f12-132">偵測 Service Pack 和更新</span><span class="sxs-lookup"><span data-stu-id="c0f12-132">Detecting service packs and updates</span></span>](../migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)

## <a name="features-that-simplify-deployment"></a><span data-ttu-id="c0f12-133">簡化部署的功能</span><span class="sxs-lookup"><span data-stu-id="c0f12-133">Features That Simplify Deployment</span></span>

<span data-ttu-id="c0f12-134">.NET Framework 提供了一些基本功能，讓部署應用程式更為容易：</span><span class="sxs-lookup"><span data-stu-id="c0f12-134">The .NET Framework provides a number of basic features that make it easier to deploy your applications:</span></span>

- <span data-ttu-id="c0f12-135">不受影響的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c0f12-135">No-impact applications.</span></span>

     <span data-ttu-id="c0f12-136">這項功能提供應用程式隔離，並排除 DLL 衝突。</span><span class="sxs-lookup"><span data-stu-id="c0f12-136">This feature provides application isolation and eliminates DLL conflicts.</span></span> <span data-ttu-id="c0f12-137">根據預設，元件不會影響其他應用程式。</span><span class="sxs-lookup"><span data-stu-id="c0f12-137">By default, components do not affect other applications.</span></span>

- <span data-ttu-id="c0f12-138">預設為私用元件。</span><span class="sxs-lookup"><span data-stu-id="c0f12-138">Private components by default.</span></span>

     <span data-ttu-id="c0f12-139">根據預設，元件會部署到應用程式目錄，並且只有對包含的應用程式為可見的。</span><span class="sxs-lookup"><span data-stu-id="c0f12-139">By default, components are deployed to the application directory and are visible only to the containing application.</span></span>

- <span data-ttu-id="c0f12-140">受控制的程式碼共用。</span><span class="sxs-lookup"><span data-stu-id="c0f12-140">Controlled code sharing.</span></span>

     <span data-ttu-id="c0f12-141">程式碼共用需要您明確地將程式碼設定為共用，而不是使用預設行為。</span><span class="sxs-lookup"><span data-stu-id="c0f12-141">Code sharing requires you to explicitly make code available for sharing instead of being the default behavior.</span></span>

- <span data-ttu-id="c0f12-142">並存版本。</span><span class="sxs-lookup"><span data-stu-id="c0f12-142">Side-by-side versioning.</span></span>

     <span data-ttu-id="c0f12-143">元件或應用程式的多個版本可以共存，您可以選擇要使用哪個版本，而且 Common Language Runtime 會強制執行版本原則。</span><span class="sxs-lookup"><span data-stu-id="c0f12-143">Multiple versions of a component or application can coexist, you can choose which versions to use, and the common language runtime enforces versioning policy.</span></span>

- <span data-ttu-id="c0f12-144">XCOPY 部署和複寫。</span><span class="sxs-lookup"><span data-stu-id="c0f12-144">XCOPY deployment and replication.</span></span>

     <span data-ttu-id="c0f12-145">自我描述和獨立的元件和應用程式不需登錄項目或相依性即可部署。</span><span class="sxs-lookup"><span data-stu-id="c0f12-145">Self-described and self-contained components and applications can be deployed without registry entries or dependencies.</span></span>

- <span data-ttu-id="c0f12-146">動態更新。</span><span class="sxs-lookup"><span data-stu-id="c0f12-146">On-the-fly updates.</span></span>

     <span data-ttu-id="c0f12-147">系統管理員可以使用主應用程式 (例如 ASP.NET) 來更新程式 DLL，甚至是在遠端電腦上。</span><span class="sxs-lookup"><span data-stu-id="c0f12-147">Administrators can use hosts, such as ASP.NET, to update program DLLs, even on remote computers.</span></span>

- <span data-ttu-id="c0f12-148">與 Windows Installer 整合</span><span class="sxs-lookup"><span data-stu-id="c0f12-148">Integration with the Windows Installer.</span></span>

     <span data-ttu-id="c0f12-149">部署您的應用程式時，通告、發行、修復和隨選安裝全部都可以使用。</span><span class="sxs-lookup"><span data-stu-id="c0f12-149">Advertisement, publishing, repair, and install-on-demand are all available when deploying your application.</span></span>

- <span data-ttu-id="c0f12-150">企業部署。</span><span class="sxs-lookup"><span data-stu-id="c0f12-150">Enterprise deployment.</span></span>

     <span data-ttu-id="c0f12-151">這項功能可讓您輕鬆散發軟體，包括使用 Active Directory。</span><span class="sxs-lookup"><span data-stu-id="c0f12-151">This feature provides easy software distribution, including using Active Directory.</span></span>

- <span data-ttu-id="c0f12-152">下載和快取。</span><span class="sxs-lookup"><span data-stu-id="c0f12-152">Downloading and caching.</span></span>

     <span data-ttu-id="c0f12-153">累加下載會維持較小的下載，而且會隔離元件，僅供對部署影響較小的應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="c0f12-153">Incremental downloads keep downloads smaller, and components can be isolated for use only by the application for low-impact deployment.</span></span>

- <span data-ttu-id="c0f12-154">部分信任的程式碼</span><span class="sxs-lookup"><span data-stu-id="c0f12-154">Partially trusted code.</span></span>

     <span data-ttu-id="c0f12-155">識別的依據是程式碼而非使用者，而且不會出現憑證對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c0f12-155">Identity is based on the code instead of the user, and no certificate dialog boxes appear.</span></span>

## <a name="packaging-and-distributing-net-framework-applications"></a><span data-ttu-id="c0f12-156">封裝和散發 .NET Framework 應用程式</span><span class="sxs-lookup"><span data-stu-id="c0f12-156">Packaging and Distributing .NET Framework Applications</span></span>

<span data-ttu-id="c0f12-157">文件的其他章節將說明 .NET Framework 的一些封裝和部署資訊。</span><span class="sxs-lookup"><span data-stu-id="c0f12-157">Some of the packaging and deployment information for the .NET Framework is described in other sections of the documentation.</span></span> <span data-ttu-id="c0f12-158">那些小節針對下列內容提供相關資訊：稱為[組件](../../standard/assembly/index.md)的自我描述單位 (不需要登錄項目)、[強式名稱的組件](../../standard/assembly/strong-named.md) (能確保名稱唯一性並防止名稱冒用)，以及[組件版本控制](../../standard/assembly/versioning.md) (能處理許多與 DLL 衝突相關的問題)。</span><span class="sxs-lookup"><span data-stu-id="c0f12-158">Those sections provide information about the self-describing units called [assemblies](../../standard/assembly/index.md), which require no registry entries, [strong-named assemblies](../../standard/assembly/strong-named.md), which ensure name uniqueness and prevent name spoofing, and [assembly versioning](../../standard/assembly/versioning.md), which addresses many of the problems associated with DLL conflicts.</span></span> <span data-ttu-id="c0f12-159">下列章節提供封裝和散發 .NET Framework 應用程式的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c0f12-159">The following sections provide information about packaging and distributing .NET Framework applications.</span></span>

### <a name="packaging"></a><span data-ttu-id="c0f12-160">包裝</span><span class="sxs-lookup"><span data-stu-id="c0f12-160">Packaging</span></span>

<span data-ttu-id="c0f12-161">.NET Framework 提供下列封裝應用程式的選項：</span><span class="sxs-lookup"><span data-stu-id="c0f12-161">The .NET Framework provides the following options for packaging applications:</span></span>

- <span data-ttu-id="c0f12-162">當做單一組件或組件集合。</span><span class="sxs-lookup"><span data-stu-id="c0f12-162">As a single assembly or as a collection of assemblies.</span></span>

     <span data-ttu-id="c0f12-163">使用這個選項時，您會直接依建置時原狀使用 .dll 或 .exe 檔。</span><span class="sxs-lookup"><span data-stu-id="c0f12-163">With this option, you simply use the .dll or .exe files as they were built.</span></span>

- <span data-ttu-id="c0f12-164">當做封包 (CAB) 檔案。</span><span class="sxs-lookup"><span data-stu-id="c0f12-164">As cabinet (CAB) files.</span></span>

     <span data-ttu-id="c0f12-165">使用這個選項時，您會將檔案壓縮成 .cab 檔，讓散發或下載較不費時。</span><span class="sxs-lookup"><span data-stu-id="c0f12-165">With this option, you compress files into .cab files to make distribution or download less time consuming.</span></span>

- <span data-ttu-id="c0f12-166">當做 Windows Installer 套件或採用其他安裝程式的格式。</span><span class="sxs-lookup"><span data-stu-id="c0f12-166">As a Windows Installer package or in other installer formats.</span></span>

     <span data-ttu-id="c0f12-167">使用這個選項時，您將會建立搭配 Windows Installer 使用的 .msi 檔，或封裝您的應用程式以搭配另一個安裝程式使用。</span><span class="sxs-lookup"><span data-stu-id="c0f12-167">With this option, you create .msi files for use with the Windows Installer, or you package your application for use with some other installer.</span></span>

### <a name="distribution"></a><span data-ttu-id="c0f12-168">散發</span><span class="sxs-lookup"><span data-stu-id="c0f12-168">Distribution</span></span>

<span data-ttu-id="c0f12-169">.NET Framework 提供下列散發應用程式的選項：</span><span class="sxs-lookup"><span data-stu-id="c0f12-169">The .NET Framework provides the following options for distributing applications:</span></span>

- <span data-ttu-id="c0f12-170">使用 XCOPY 或 FTP。</span><span class="sxs-lookup"><span data-stu-id="c0f12-170">Use XCOPY or FTP.</span></span>

     <span data-ttu-id="c0f12-171">由於 Common Language Runtime 應用程式是自我描述且不需要登錄項目，因此您可以使用 XCOPY 或 FTP 直接將應用程式複製到適當的目錄。</span><span class="sxs-lookup"><span data-stu-id="c0f12-171">Because common language runtime applications are self-describing and require no registry entries, you can use XCOPY or FTP to simply copy the application to an appropriate directory.</span></span> <span data-ttu-id="c0f12-172">接著便可從該目錄執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="c0f12-172">The application can then be run from that directory.</span></span>

- <span data-ttu-id="c0f12-173">使用程式碼下載。</span><span class="sxs-lookup"><span data-stu-id="c0f12-173">Use code download.</span></span>

     <span data-ttu-id="c0f12-174">如果您正在網際網路上或透過公司內部網路散發應用程式，您可以直接將程式碼下載到電腦，並在電腦上執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="c0f12-174">If you are distributing your application over the Internet or through a corporate intranet, you can simply download the code to a computer and run the application there.</span></span>

- <span data-ttu-id="c0f12-175">使用安裝程式，例如 Windows Installer 2.0。</span><span class="sxs-lookup"><span data-stu-id="c0f12-175">Use an installer program such as Windows Installer 2.0.</span></span>

     <span data-ttu-id="c0f12-176">Windows Installer 2.0 可以在全域組件快取和私人目錄中安裝、修復或移除 .NET Framework 組件。</span><span class="sxs-lookup"><span data-stu-id="c0f12-176">Windows Installer 2.0 can install, repair, or remove .NET Framework assemblies in the global assembly cache and in private directories.</span></span>

### <a name="installation-location"></a><span data-ttu-id="c0f12-177">安裝位置</span><span class="sxs-lookup"><span data-stu-id="c0f12-177">Installation Location</span></span>

<span data-ttu-id="c0f12-178">若要決定應用程式的組件應該部署在哪裡，使執行階段能夠找到它們，請參閱[執行階段如何找出組件](how-the-runtime-locates-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="c0f12-178">To determine where to deploy your application's assemblies so they can be found by the runtime, see [How the Runtime Locates Assemblies](how-the-runtime-locates-assemblies.md).</span></span>

<span data-ttu-id="c0f12-179">安全性考量也可能影響您部署應用程式的方式。</span><span class="sxs-lookup"><span data-stu-id="c0f12-179">Security considerations can also affect how you deploy your application.</span></span> <span data-ttu-id="c0f12-180">在對 Managed 程式碼授與安全性權限時，依據的是程式碼的位置。</span><span class="sxs-lookup"><span data-stu-id="c0f12-180">Security permissions are granted to managed code according to where the code is located.</span></span> <span data-ttu-id="c0f12-181">如果將應用程式或元件部署到信任度極低的位置 (例如網際網路)，應用程式或元件所能執行的工作則會受限。</span><span class="sxs-lookup"><span data-stu-id="c0f12-181">Deploying an application or component to a location where it receives little trust, such as the Internet, limits what the application or component can do.</span></span> <span data-ttu-id="c0f12-182">如需部署和安全性考量的詳細資訊，請參閱[程式碼存取安全性的基本概念](../misc/code-access-security-basics.md)。</span><span class="sxs-lookup"><span data-stu-id="c0f12-182">For more information about deployment and security considerations, see [Code Access Security Basics](../misc/code-access-security-basics.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="c0f12-183">相關主題</span><span class="sxs-lookup"><span data-stu-id="c0f12-183">Related Topics</span></span>

|<span data-ttu-id="c0f12-184">Title</span><span class="sxs-lookup"><span data-stu-id="c0f12-184">Title</span></span>|<span data-ttu-id="c0f12-185">描述</span><span class="sxs-lookup"><span data-stu-id="c0f12-185">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="c0f12-186">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="c0f12-186">How the Runtime Locates Assemblies</span></span>](how-the-runtime-locates-assemblies.md)|<span data-ttu-id="c0f12-187">描述 Common Language Runtime 如何決定要用哪個組件來實現繫結要求。</span><span class="sxs-lookup"><span data-stu-id="c0f12-187">Describes how the common language runtime determines which assembly to use to fulfill a binding request.</span></span>|
|[<span data-ttu-id="c0f12-188">組件載入的最佳做法</span><span class="sxs-lookup"><span data-stu-id="c0f12-188">Best Practices for Assembly Loading</span></span>](best-practices-for-assembly-loading.md)|<span data-ttu-id="c0f12-189">討論如何避免發生可能造成 <xref:System.InvalidCastException>、<xref:System.MissingMethodException> 和其他錯誤之類型識別的問題。</span><span class="sxs-lookup"><span data-stu-id="c0f12-189">Discusses ways to avoid problems of type identity that can lead to <xref:System.InvalidCastException>, <xref:System.MissingMethodException>, and other errors.</span></span>|
|[<span data-ttu-id="c0f12-190">減少 .NET Framework 4.5 安裝期間的系統重新開機</span><span class="sxs-lookup"><span data-stu-id="c0f12-190">Reducing System Restarts During .NET Framework 4.5 Installations</span></span>](reducing-system-restarts.md)|<span data-ttu-id="c0f12-191">描述可防止在任何可能的情況下重新開機的重新啟動管理員，並說明安裝 .NET Framework 的應用程式如何利用 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="c0f12-191">Describes the Restart Manager, which prevents reboots whenever possible, and explains how applications that install the .NET Framework can take advantage of it.</span></span>|
|[<span data-ttu-id="c0f12-192">系統管理員部署手冊</span><span class="sxs-lookup"><span data-stu-id="c0f12-192">Deployment Guide for Administrators</span></span>](guide-for-administrators.md)|<span data-ttu-id="c0f12-193">說明系統管理員如何使用 Microsoft 端點 Configuration Manager，在網路上部署 .NET Framework 及其系統相依性。</span><span class="sxs-lookup"><span data-stu-id="c0f12-193">Explains how a system administrator can deploy the .NET Framework and its system dependencies across a network by using Microsoft Endpoint Configuration Manager.</span></span>|
|[<span data-ttu-id="c0f12-194">開發人員部署手冊</span><span class="sxs-lookup"><span data-stu-id="c0f12-194">Deployment Guide for Developers</span></span>](deployment-guide-for-developers.md)|<span data-ttu-id="c0f12-195">說明開發人員如何將 .NET Framework 隨使用者的應用程式安裝在其電腦上。</span><span class="sxs-lookup"><span data-stu-id="c0f12-195">Explains how developers can install .NET Framework on their users' computers with their applications.</span></span>|
|[<span data-ttu-id="c0f12-196">部署應用程式、服務和元件</span><span class="sxs-lookup"><span data-stu-id="c0f12-196">Deploying Applications, Services, and Components</span></span>](/visualstudio/deployment/deploying-applications-services-and-components)|<span data-ttu-id="c0f12-197">討論 Visual Studio 中的部署選項，包括使用 ClickOnce 和 Windows Installer 技術發行應用程式的指示。</span><span class="sxs-lookup"><span data-stu-id="c0f12-197">Discusses deployment options in Visual Studio, including instructions for publishing an application using the ClickOnce and Windows Installer technologies.</span></span>|
|[<span data-ttu-id="c0f12-198">發行 ClickOnce 應用程式</span><span class="sxs-lookup"><span data-stu-id="c0f12-198">Publishing ClickOnce Applications</span></span>](/visualstudio/deployment/publishing-clickonce-applications)|<span data-ttu-id="c0f12-199">描述如何封裝 Windows Forms 應用程式，並使用 ClickOnce 將它部署到網路上的用戶端電腦。</span><span class="sxs-lookup"><span data-stu-id="c0f12-199">Describes how to package a Windows Forms application and deploy it with ClickOnce to client computers on a network.</span></span>|
|[<span data-ttu-id="c0f12-200">封裝和部署資源</span><span class="sxs-lookup"><span data-stu-id="c0f12-200">Packaging and Deploying Resources</span></span>](../resources/packaging-and-deploying-resources-in-desktop-apps.md)|<span data-ttu-id="c0f12-201">描述 .NET Framework 用來封裝及部署資源的中樞和輪輻模型；內容涵蓋資源命名慣例、後援程序和封裝替代方式。</span><span class="sxs-lookup"><span data-stu-id="c0f12-201">Describes the hub and spoke model that the .NET Framework uses to package and deploy resources; covers resource naming conventions, fallback process, and packaging alternatives.</span></span>|
|[<span data-ttu-id="c0f12-202">部署 Interop 應用程式</span><span class="sxs-lookup"><span data-stu-id="c0f12-202">Deploying an Interop Application</span></span>](../interop/deploying-an-interop-application.md)|<span data-ttu-id="c0f12-203">描述如何交付及安裝 Interop 應用程式，這類應用程式通常包含 .NET Framework 用戶端組件、代表各種不同 COM 類型程式庫的一或多個 Interop 組件，以及一或多個已註冊的 COM 元件。</span><span class="sxs-lookup"><span data-stu-id="c0f12-203">Explains how to ship and install interop applications, which typically include a .NET Framework client assembly, one or more interop assemblies representing distinct COM type libraries, and one or more registered COM components.</span></span>|
|[<span data-ttu-id="c0f12-204">如何：取得 .NET Framework 4.5 安裝程式的進度</span><span class="sxs-lookup"><span data-stu-id="c0f12-204">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>](how-to-get-progress-from-the-dotnet-installer.md)|<span data-ttu-id="c0f12-205">描述如何以無訊息模式啟動並追蹤 .NET Framework 安裝程序，並同時顯示您自己的安裝進度檢視。</span><span class="sxs-lookup"><span data-stu-id="c0f12-205">Describes how to silently launch and track the .NET Framework setup process while showing your own view of the setup progress.</span></span>|

## <a name="see-also"></a><span data-ttu-id="c0f12-206">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0f12-206">See also</span></span>

- [<span data-ttu-id="c0f12-207">開發指南</span><span class="sxs-lookup"><span data-stu-id="c0f12-207">Development Guide</span></span>](../development-guide.md)
