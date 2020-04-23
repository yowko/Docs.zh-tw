---
title: .NET 架構和 .NET 核心之間的差異
description: 描述 Windows 示範基礎 (WPF) 的 .NET 框架實現和 .NET 核心 WPF 之間的差異。 遷移應用時,應考慮這些不相容因素。
author: thraka
ms.date: 09/21/2019
ms.author: adegeo
ms.openlocfilehash: 341e576f17c522fbcbb9c417176e9d4a13ab1b18
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82072204"
---
# <a name="differences-in-wpf"></a><span data-ttu-id="6923d-104">WPF 的差異</span><span class="sxs-lookup"><span data-stu-id="6923d-104">Differences in WPF</span></span>

<span data-ttu-id="6923d-105">本文介紹了 .NET 核心和 .NET 框架上的 Windows 演示基礎 (WPF) 之間的差異。</span><span class="sxs-lookup"><span data-stu-id="6923d-105">This article describes the differences between Windows Presentation Foundation (WPF) on .NET Core and .NET Framework.</span></span> <span data-ttu-id="6923d-106">.NET Core 的 WPF 是從原始 WPF 為 .NET 框架原始程式碼分叉的[開源框架](https://github.com/dotnet/wpf)。</span><span class="sxs-lookup"><span data-stu-id="6923d-106">WPF for .NET Core is an [open-source framework](https://github.com/dotnet/wpf) forked from the original WPF for .NET Framework source code.</span></span>

<span data-ttu-id="6923d-107">.NET 框架有幾個功能,而 .NET Core 不支援這些功能。</span><span class="sxs-lookup"><span data-stu-id="6923d-107">There are a few features of .NET Framework that .NET Core doesn't support.</span></span> <span data-ttu-id="6923d-108">有關不支援的技術的詳細資訊,請參閱[.NET 框架技術在 .NET Core 上不可用](../../core/porting/net-framework-tech-unavailable.md)。</span><span class="sxs-lookup"><span data-stu-id="6923d-108">For more information on unsupported technologies, see [.NET Framework technologies unavailable on .NET Core](../../core/porting/net-framework-tech-unavailable.md).</span></span>

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sdk-style-projects"></a><span data-ttu-id="6923d-109">SDK 風格的項目</span><span class="sxs-lookup"><span data-stu-id="6923d-109">SDK-style projects</span></span>

<span data-ttu-id="6923d-110">.NET Core 使用 SDK 風格的專案檔。</span><span class="sxs-lookup"><span data-stu-id="6923d-110">.NET Core uses SDK-style project files.</span></span> <span data-ttu-id="6923d-111">這些專案檔不同於 Visual Studio 管理的傳統 .NET 框架專案檔。</span><span class="sxs-lookup"><span data-stu-id="6923d-111">These project files are different from the traditional .NET Framework project files managed by Visual Studio.</span></span> <span data-ttu-id="6923d-112">要將 .NET 框架 WPF 應用遷移到 .NET Core,必須轉換專案。</span><span class="sxs-lookup"><span data-stu-id="6923d-112">To migrate your .NET Framework WPF apps to .NET Core, you must convert your projects.</span></span> <span data-ttu-id="6923d-113">有關詳細資訊,請參閱將[WPF 應用遷移到 .NET 核心 3.0](convert-project-from-net-framework.md)。</span><span class="sxs-lookup"><span data-stu-id="6923d-113">For more information, see [Migrate WPF apps to .NET Core 3.0](convert-project-from-net-framework.md).</span></span>

## <a name="nuget-package-references"></a><span data-ttu-id="6923d-114">NuGet 封裝參考</span><span class="sxs-lookup"><span data-stu-id="6923d-114">NuGet package references</span></span>

<span data-ttu-id="6923d-115">如果您的 .NET Framework 應用在套件中列出了其 NuGet 相依項 *。* [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files)</span><span class="sxs-lookup"><span data-stu-id="6923d-115">If your .NET Framework app lists its NuGet dependencies in a *packages.config* file, migrate to the [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) format:</span></span>

1. <span data-ttu-id="6923d-116">在可視化工作室中,打開 **「解決方案資源管理器」** 窗格。</span><span class="sxs-lookup"><span data-stu-id="6923d-116">In Visual Studio, open the **Solution Explorer** pane.</span></span>
1. <span data-ttu-id="6923d-117">在 WPF 專案中,右鍵按下**套件.config** > **移轉包。config 到套件參考**。</span><span class="sxs-lookup"><span data-stu-id="6923d-117">In your WPF project, right-click **packages.config** > **Migrate packages.config to PackageReference**.</span></span>

![升級到包參考](media/differences-from-net-framework/package-reference-migration.png)

<span data-ttu-id="6923d-119">將顯示一個對話框,顯示計算的頂級 NuGet 依賴項,並詢問應將哪些其他 NuGet 包提升到頂層。</span><span class="sxs-lookup"><span data-stu-id="6923d-119">A dialog will appear showing calculated top-level NuGet dependencies and asking which other NuGet packages should be promoted to top level.</span></span> <span data-ttu-id="6923d-120">選擇 **「 確定**」*套件.config*檔將從項目中`<PackageReference>`刪除, 元素將新增到專案檔中。</span><span class="sxs-lookup"><span data-stu-id="6923d-120">Select **OK** and the *packages.config* file will be removed from the project and `<PackageReference>` elements will be added to the project file.</span></span>

<span data-ttu-id="6923d-121">當專案使用`<PackageReference>`時,包不會存儲在 *「包」* 資料夾中本地,它們存儲在全域。</span><span class="sxs-lookup"><span data-stu-id="6923d-121">When your project uses `<PackageReference>`, packages aren't stored locally in a *Packages* folder, they're stored globally.</span></span> <span data-ttu-id="6923d-122">開啟專案檔並刪除參考`<Analyzer>`*「包」* 資料夾的任何元素。</span><span class="sxs-lookup"><span data-stu-id="6923d-122">Open the project file and remove any `<Analyzer>` elements that referred to the *Packages* folder.</span></span> <span data-ttu-id="6923d-123">這些分析器會自動包含在 NuGet 包引用中。</span><span class="sxs-lookup"><span data-stu-id="6923d-123">These analyzers are automatically included with the NuGet package references.</span></span>

## <a name="code-access-security"></a><span data-ttu-id="6923d-124">程式碼存取安全性</span><span class="sxs-lookup"><span data-stu-id="6923d-124">Code Access Security</span></span>

<span data-ttu-id="6923d-125">.NET 核心或 .NET Core 的 WPF 不支援代碼存取安全性 (CAS)。</span><span class="sxs-lookup"><span data-stu-id="6923d-125">Code Access Security (CAS) is not supported by .NET Core or WPF for .NET Core.</span></span> <span data-ttu-id="6923d-126">所有 CAS 相關功能均以完全信任為假設處理。</span><span class="sxs-lookup"><span data-stu-id="6923d-126">All CAS-related functionality is treated under the assumption of full-trust.</span></span> <span data-ttu-id="6923d-127">.NET Core 的 WPF 刪除 CAS 相關代碼。</span><span class="sxs-lookup"><span data-stu-id="6923d-127">WPF for .NET Core removes CAS-related code.</span></span> <span data-ttu-id="6923d-128">這些類型的公共 API 表面仍然存在,以確保對這些類型的調用成功。</span><span class="sxs-lookup"><span data-stu-id="6923d-128">The public API surface of these types still exists to ensure that calls into these types succeed.</span></span>

<span data-ttu-id="6923d-129">公開定義的 CAS 相關類型從 WPF 程式集移出並移動到 Core .NET 庫程式集中。</span><span class="sxs-lookup"><span data-stu-id="6923d-129">Publicly defined CAS-related types were moved out of the WPF assemblies and into the Core .NET library assemblies.</span></span> <span data-ttu-id="6923d-130">WPF 程式集具有類型轉發設置為行動類型的新位置。</span><span class="sxs-lookup"><span data-stu-id="6923d-130">The WPF assemblies have type-forwarding set to the new location of the moved types.</span></span>

| <span data-ttu-id="6923d-131">來源程式集</span><span class="sxs-lookup"><span data-stu-id="6923d-131">Source assembly</span></span> | <span data-ttu-id="6923d-132">目標程式集</span><span class="sxs-lookup"><span data-stu-id="6923d-132">Target assembly</span></span> | <span data-ttu-id="6923d-133">類型</span><span class="sxs-lookup"><span data-stu-id="6923d-133">Type</span></span>                |
| --------------- | --------------- | ------------------- |
| <span data-ttu-id="6923d-134">*WindowsBase.dll*</span><span class="sxs-lookup"><span data-stu-id="6923d-134">*WindowsBase.dll*</span></span> | <span data-ttu-id="6923d-135">*系統.安全.許可權.dll*</span><span class="sxs-lookup"><span data-stu-id="6923d-135">*System.Security.Permissions.dll*</span></span> | <xref:System.Security.Permissions.MediaPermission> <br /> <xref:System.Security.Permissions.MediaPermissionAttribute> <br /> <xref:System.Security.Permissions.MediaPermissionAudio> <br /> <xref:System.Security.Permissions.MediaPermissionImage> <br /> <xref:System.Security.Permissions.MediaPermissionVideo> <br /> <xref:System.Security.Permissions.WebBrowserPermission> <br /> <xref:System.Security.Permissions.WebBrowserPermissionAttribute> <br /> <xref:System.Security.Permissions.WebBrowserPermissionLevel> |
| <span data-ttu-id="6923d-136">*System.Xaml.dll*</span><span class="sxs-lookup"><span data-stu-id="6923d-136">*System.Xaml.dll*</span></span> | <span data-ttu-id="6923d-137">*系統.安全.許可權.dll*</span><span class="sxs-lookup"><span data-stu-id="6923d-137">*System.Security.Permissions.dll*</span></span> | <xref:System.Xaml.Permissions.XamlLoadPermission> |
| <span data-ttu-id="6923d-138">*System.Xaml.dll*</span><span class="sxs-lookup"><span data-stu-id="6923d-138">*System.Xaml.dll*</span></span> | <span data-ttu-id="6923d-139">*系統.Windows.擴展.dll*</span><span class="sxs-lookup"><span data-stu-id="6923d-139">*System.Windows.Extension.dll*</span></span>    | <xref:System.Xaml.Permissions.XamlAccessLevel><br/> |

> [!NOTE]
> <span data-ttu-id="6923d-140">為了盡量減少移植摩擦,在類型中保留了存儲和檢索與以下屬性相關的資訊的功能`XamlAccessLevel`。</span><span class="sxs-lookup"><span data-stu-id="6923d-140">In order to minimize porting friction, the functionality for storing and retrieving information related to the following properties was retained in the `XamlAccessLevel` type.</span></span>
>
> - `PrivateAccessToTypeName`
> - `AssemblyNameString`

## <a name="next-steps"></a><span data-ttu-id="6923d-141">後續步驟</span><span class="sxs-lookup"><span data-stu-id="6923d-141">Next steps</span></span>

- [<span data-ttu-id="6923d-142">瞭解如何將 .NET 框架 WPF 應用移植到 .NET 核心。</span><span class="sxs-lookup"><span data-stu-id="6923d-142">Learn how to port a .NET Framework WPF app to .NET Core.</span></span>](convert-project-from-net-framework.md)
