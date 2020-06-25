---
title: .NET Framework 和 .NET Core 之間的差異
description: 說明 Windows Presentation Foundation （WPF）和 .NET Core WPF 的 .NET Framework 執行之間的差異。 在遷移您的應用程式時，您應該考慮這些不相容性。
author: adegeo
ms.date: 09/21/2019
ms.author: adegeo
ms.openlocfilehash: 3bedc30046c36d4c5430feedf5854276ebaef8aa
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325685"
---
# <a name="differences-in-wpf"></a><span data-ttu-id="d14b9-104">WPF 的差異</span><span class="sxs-lookup"><span data-stu-id="d14b9-104">Differences in WPF</span></span>

<span data-ttu-id="d14b9-105">本文說明 .NET Core 上的 Windows Presentation Foundation （WPF）與 .NET Framework 之間的差異。</span><span class="sxs-lookup"><span data-stu-id="d14b9-105">This article describes the differences between Windows Presentation Foundation (WPF) on .NET Core and .NET Framework.</span></span> <span data-ttu-id="d14b9-106">適用于 .NET Core 的 WPF 是一個開放原始碼[架構](https://github.com/dotnet/wpf)，會從 .NET Framework 原始程式碼的原始 WPF 派生。</span><span class="sxs-lookup"><span data-stu-id="d14b9-106">WPF for .NET Core is an [open-source framework](https://github.com/dotnet/wpf) forked from the original WPF for .NET Framework source code.</span></span>

<span data-ttu-id="d14b9-107">.NET Core 不支援 .NET Framework 的幾項功能。</span><span class="sxs-lookup"><span data-stu-id="d14b9-107">There are a few features of .NET Framework that .NET Core doesn't support.</span></span> <span data-ttu-id="d14b9-108">如需不支援技術的詳細資訊，請參閱[.Net Core 上無法使用的 .NET Framework 技術](../../core/porting/net-framework-tech-unavailable.md)。</span><span class="sxs-lookup"><span data-stu-id="d14b9-108">For more information on unsupported technologies, see [.NET Framework technologies unavailable on .NET Core](../../core/porting/net-framework-tech-unavailable.md).</span></span>

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sdk-style-projects"></a><span data-ttu-id="d14b9-109">SDK 樣式專案</span><span class="sxs-lookup"><span data-stu-id="d14b9-109">SDK-style projects</span></span>

<span data-ttu-id="d14b9-110">.NET Core 使用 SDK 樣式的專案檔。</span><span class="sxs-lookup"><span data-stu-id="d14b9-110">.NET Core uses SDK-style project files.</span></span> <span data-ttu-id="d14b9-111">這些專案檔不同于 Visual Studio 所管理的傳統 .NET Framework 專案檔案。</span><span class="sxs-lookup"><span data-stu-id="d14b9-111">These project files are different from the traditional .NET Framework project files managed by Visual Studio.</span></span> <span data-ttu-id="d14b9-112">若要將您的 .NET Framework WPF 應用程式遷移至 .NET Core，您必須轉換專案。</span><span class="sxs-lookup"><span data-stu-id="d14b9-112">To migrate your .NET Framework WPF apps to .NET Core, you must convert your projects.</span></span> <span data-ttu-id="d14b9-113">如需詳細資訊，請參閱[將 WPF 應用程式遷移至 .Net Core 3.0](convert-project-from-net-framework.md)。</span><span class="sxs-lookup"><span data-stu-id="d14b9-113">For more information, see [Migrate WPF apps to .NET Core 3.0](convert-project-from-net-framework.md).</span></span>

## <a name="nuget-package-references"></a><span data-ttu-id="d14b9-114">NuGet 封裝參考</span><span class="sxs-lookup"><span data-stu-id="d14b9-114">NuGet package references</span></span>

<span data-ttu-id="d14b9-115">如果您的 .NET Framework 應用程式在*packages.config*檔案中列出其 NuGet 相依性，請遷移至 [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) 下列格式：</span><span class="sxs-lookup"><span data-stu-id="d14b9-115">If your .NET Framework app lists its NuGet dependencies in a *packages.config* file, migrate to the [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) format:</span></span>

1. <span data-ttu-id="d14b9-116">在 Visual Studio 中，開啟 [**方案總管**] 窗格。</span><span class="sxs-lookup"><span data-stu-id="d14b9-116">In Visual Studio, open the **Solution Explorer** pane.</span></span>
1. <span data-ttu-id="d14b9-117">在 WPF 專案中，以滑鼠右鍵按一下 [ **packages.config**  >  **將 packages.config 遷移至 PackageReference**]。</span><span class="sxs-lookup"><span data-stu-id="d14b9-117">In your WPF project, right-click **packages.config** > **Migrate packages.config to PackageReference**.</span></span>

![升級至 PackageReference](media/differences-from-net-framework/package-reference-migration.png)

<span data-ttu-id="d14b9-119">隨即會出現一個對話方塊，顯示計算的最上層 NuGet 相依性，並詢問哪些其他 NuGet 套件應該升級為最上層。</span><span class="sxs-lookup"><span data-stu-id="d14b9-119">A dialog will appear showing calculated top-level NuGet dependencies and asking which other NuGet packages should be promoted to top level.</span></span> <span data-ttu-id="d14b9-120">選取 [**確定]** ，將會從專案中移除*packages.config*檔案，而 `<PackageReference>` 元素會加入至專案檔。</span><span class="sxs-lookup"><span data-stu-id="d14b9-120">Select **OK** and the *packages.config* file will be removed from the project and `<PackageReference>` elements will be added to the project file.</span></span>

<span data-ttu-id="d14b9-121">當您的專案使用時 `<PackageReference>` ，封裝不會儲存在本機的*封裝*資料夾中，而是以全域方式儲存。</span><span class="sxs-lookup"><span data-stu-id="d14b9-121">When your project uses `<PackageReference>`, packages aren't stored locally in a *Packages* folder, they're stored globally.</span></span> <span data-ttu-id="d14b9-122">開啟專案檔，並移除任何 `<Analyzer>` 參考 [*封裝*] 資料夾的元素。</span><span class="sxs-lookup"><span data-stu-id="d14b9-122">Open the project file and remove any `<Analyzer>` elements that referred to the *Packages* folder.</span></span> <span data-ttu-id="d14b9-123">這些分析器會自動包含在 NuGet 套件參考中。</span><span class="sxs-lookup"><span data-stu-id="d14b9-123">These analyzers are automatically included with the NuGet package references.</span></span>

## <a name="code-access-security"></a><span data-ttu-id="d14b9-124">程式碼存取安全性</span><span class="sxs-lookup"><span data-stu-id="d14b9-124">Code Access Security</span></span>

<span data-ttu-id="d14b9-125">.Net Core 或適用于 .NET Core 的 WPF 不支援代碼啟用安全性（CAS）。</span><span class="sxs-lookup"><span data-stu-id="d14b9-125">Code Access Security (CAS) is not supported by .NET Core or WPF for .NET Core.</span></span> <span data-ttu-id="d14b9-126">所有與 CAS 相關的功能都會被視為完全信任的假設。</span><span class="sxs-lookup"><span data-stu-id="d14b9-126">All CAS-related functionality is treated under the assumption of full-trust.</span></span> <span data-ttu-id="d14b9-127">適用于 .NET Core 的 WPF 會移除 CAS 相關程式碼。</span><span class="sxs-lookup"><span data-stu-id="d14b9-127">WPF for .NET Core removes CAS-related code.</span></span> <span data-ttu-id="d14b9-128">這些類型的公用 API 介面仍然存在，以確保這些類型的呼叫會成功。</span><span class="sxs-lookup"><span data-stu-id="d14b9-128">The public API surface of these types still exists to ensure that calls into these types succeed.</span></span>

<span data-ttu-id="d14b9-129">公開定義的 CAS 相關類型已移出 WPF 元件和核心 .NET 程式庫元件。</span><span class="sxs-lookup"><span data-stu-id="d14b9-129">Publicly defined CAS-related types were moved out of the WPF assemblies and into the Core .NET library assemblies.</span></span> <span data-ttu-id="d14b9-130">WPF 元件會將類型轉送設定為已移動類型的新位置。</span><span class="sxs-lookup"><span data-stu-id="d14b9-130">The WPF assemblies have type-forwarding set to the new location of the moved types.</span></span>

| <span data-ttu-id="d14b9-131">來源元件</span><span class="sxs-lookup"><span data-stu-id="d14b9-131">Source assembly</span></span> | <span data-ttu-id="d14b9-132">目標群組件</span><span class="sxs-lookup"><span data-stu-id="d14b9-132">Target assembly</span></span> | <span data-ttu-id="d14b9-133">類型</span><span class="sxs-lookup"><span data-stu-id="d14b9-133">Type</span></span>                |
| --------------- | --------------- | ------------------- |
| <span data-ttu-id="d14b9-134">*WindowsBase.dll*</span><span class="sxs-lookup"><span data-stu-id="d14b9-134">*WindowsBase.dll*</span></span> | <span data-ttu-id="d14b9-135">*System.Security.Permissions.dll*</span><span class="sxs-lookup"><span data-stu-id="d14b9-135">*System.Security.Permissions.dll*</span></span> | <xref:System.Security.Permissions.MediaPermission> <br /> <xref:System.Security.Permissions.MediaPermissionAttribute> <br /> <xref:System.Security.Permissions.MediaPermissionAudio> <br /> <xref:System.Security.Permissions.MediaPermissionImage> <br /> <xref:System.Security.Permissions.MediaPermissionVideo> <br /> <xref:System.Security.Permissions.WebBrowserPermission> <br /> <xref:System.Security.Permissions.WebBrowserPermissionAttribute> <br /> <xref:System.Security.Permissions.WebBrowserPermissionLevel> |
| <span data-ttu-id="d14b9-136">*System.Xaml.dll*</span><span class="sxs-lookup"><span data-stu-id="d14b9-136">*System.Xaml.dll*</span></span> | <span data-ttu-id="d14b9-137">*System.Security.Permissions.dll*</span><span class="sxs-lookup"><span data-stu-id="d14b9-137">*System.Security.Permissions.dll*</span></span> | <xref:System.Xaml.Permissions.XamlLoadPermission> |
| <span data-ttu-id="d14b9-138">*System.Xaml.dll*</span><span class="sxs-lookup"><span data-stu-id="d14b9-138">*System.Xaml.dll*</span></span> | <span data-ttu-id="d14b9-139">*System.Windows.Extension.dll*</span><span class="sxs-lookup"><span data-stu-id="d14b9-139">*System.Windows.Extension.dll*</span></span>    | <xref:System.Xaml.Permissions.XamlAccessLevel><br/> |

> [!NOTE]
> <span data-ttu-id="d14b9-140">為了儘量減少移植的摩擦，儲存和抓取下列屬性相關資訊的功能已保留在 `XamlAccessLevel` 類型中。</span><span class="sxs-lookup"><span data-stu-id="d14b9-140">In order to minimize porting friction, the functionality for storing and retrieving information related to the following properties was retained in the `XamlAccessLevel` type.</span></span>
>
> - `PrivateAccessToTypeName`
> - `AssemblyNameString`

## <a name="next-steps"></a><span data-ttu-id="d14b9-141">後續步驟</span><span class="sxs-lookup"><span data-stu-id="d14b9-141">Next steps</span></span>

- [<span data-ttu-id="d14b9-142">瞭解如何將 .NET Framework WPF 應用程式移植到 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="d14b9-142">Learn how to port a .NET Framework WPF app to .NET Core.</span></span>](convert-project-from-net-framework.md)
