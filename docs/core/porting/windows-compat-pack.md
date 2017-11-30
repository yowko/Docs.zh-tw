---
title: "移植到.NET Core-使用 Windows 相容性組件"
description: "Windows 相容性套件，請參閱了解如何使用它來連接埠現有.NET Framework 程式碼到.NET Core 和"
keywords: ".NET、.NET core、 Windows、 相容性"
author: terrajobst
ms.author: mairaw
ms.date: 11/13/2017
ms.topic: article
ms.prod: .net-core
ms.openlocfilehash: 5094baee77aba4d1e148f807d842a4a2d3405cf7
ms.sourcegitcommit: 86cf9b4c7104485a9870645705b9a1a4b6ca8e2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2017
---
# <a name="using-the-windows-compatibility-pack"></a><span data-ttu-id="360f2-104">使用 Windows 相容性組件</span><span class="sxs-lookup"><span data-stu-id="360f2-104">Using the Windows Compatibility Pack</span></span>

<span data-ttu-id="360f2-105">其中一個最常見移植到.NET Core 其現有的程式碼時，開發人員所面臨的問題是它們的相依應用程式開發介面和只存在於.NET Framework 中的技術。</span><span class="sxs-lookup"><span data-stu-id="360f2-105">One of the most common issues that developers face when porting their existing code to .NET Core is that they depend on APIs and technologies that only exist in the .NET Framework.</span></span> <span data-ttu-id="360f2-106">*Windows 相容性套件*即將提供其中許多技術建置.NET Core 應用程式，以及標準的.NET 程式庫會變成更可行的現有程式碼。</span><span class="sxs-lookup"><span data-stu-id="360f2-106">The *Windows Compatibility Pack* is about providing many of these technologies so that building .NET Core applications as well as .NET Standard libraries becomes much more viable for existing code.</span></span>

<span data-ttu-id="360f2-107">此封裝是邏輯[延伸模組的.NET 標準 2.0](../whats-new/index.md#api-changes-and-library-support) ，大幅增加 API 集和現有的程式碼會編譯幾乎不需要修改。</span><span class="sxs-lookup"><span data-stu-id="360f2-107">This package is a logical [extension of .NET Standard 2.0](../whats-new/index.md#api-changes-and-library-support) that significantly increases API set and existing code compiles with almost no modifications.</span></span> <span data-ttu-id="360f2-108">但若要保留的.NET 標準承諾 （「 它是所有.NET 實作所都提供的 Api 集 」），這不包括無法跨所有平台，例如登錄，Windows Management Instrumentation (WMI) 的技術或反映發出應用程式開發介面。</span><span class="sxs-lookup"><span data-stu-id="360f2-108">But in order to keep the promise of .NET Standard ("it is the set of APIs that all .NET implementations provide"), this didn't include technologies that can't work across all platforms, such as registry, Windows Management Instrumentation (WMI), or reflection emit APIs.</span></span>

<span data-ttu-id="360f2-109">*Windows 相容性套件*總結.NET 標準，並提供存取只是 Windows 的技術。</span><span class="sxs-lookup"><span data-stu-id="360f2-109">The *Windows Compatibility Pack* sits on top of .NET Standard and provides access to technologies that are Windows only.</span></span> <span data-ttu-id="360f2-110">它特別適用於想要移動到.NET Core 但放入 Windows，做為第一個步驟中的計劃的客戶。</span><span class="sxs-lookup"><span data-stu-id="360f2-110">It's especially useful for customers that want to move to .NET Core but plan to stay on Windows as a first step.</span></span> <span data-ttu-id="360f2-111">在這種情況下，無法使用僅限 Windows 技術是只使用零架構的優點移轉障礙。</span><span class="sxs-lookup"><span data-stu-id="360f2-111">In that scenario, not being able to use Windows-only technologies is only a migration hurdle with zero architectural benefits.</span></span>

## <a name="package-contents"></a><span data-ttu-id="360f2-112">封裝內容</span><span class="sxs-lookup"><span data-stu-id="360f2-112">Package contents</span></span>

<span data-ttu-id="360f2-113">*Windows 相容性套件*會透過 NuGet 套件提供[Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility)而且可以從.NET Core 或標準.NET 為目標的專案參考。</span><span class="sxs-lookup"><span data-stu-id="360f2-113">The *Windows Compatibility Pack* is provided via the NuGet Package [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) and can be referenced from projects targeting .NET Core or .NET Standard.</span></span>

<span data-ttu-id="360f2-114">它提供了大約 20000 Api，包括僅限 Windows，以及跨平台 Api，從下列技術領域：</span><span class="sxs-lookup"><span data-stu-id="360f2-114">It provides about 20,000 APIs, including Windows-only as well as cross-platform APIs from the following technology areas:</span></span>

* <span data-ttu-id="360f2-115">字碼頁</span><span class="sxs-lookup"><span data-stu-id="360f2-115">Code Pages</span></span>
* <span data-ttu-id="360f2-116">CodeDom</span><span class="sxs-lookup"><span data-stu-id="360f2-116">CodeDom</span></span>
* <span data-ttu-id="360f2-117">組態</span><span class="sxs-lookup"><span data-stu-id="360f2-117">Configuration</span></span>
* <span data-ttu-id="360f2-118">目錄服務</span><span class="sxs-lookup"><span data-stu-id="360f2-118">Directory Services</span></span>
* <span data-ttu-id="360f2-119">繪圖</span><span class="sxs-lookup"><span data-stu-id="360f2-119">Drawing</span></span>
* <span data-ttu-id="360f2-120">ODBC</span><span class="sxs-lookup"><span data-stu-id="360f2-120">ODBC</span></span>
* <span data-ttu-id="360f2-121">權限</span><span class="sxs-lookup"><span data-stu-id="360f2-121">Permissions</span></span>
* <span data-ttu-id="360f2-122">連接埠</span><span class="sxs-lookup"><span data-stu-id="360f2-122">Ports</span></span>
* <span data-ttu-id="360f2-123">Windows 存取控制清單 (ACL)</span><span class="sxs-lookup"><span data-stu-id="360f2-123">Windows Access Control Lists (ACL)</span></span>
* <span data-ttu-id="360f2-124">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="360f2-124">Windows Communication Foundation (WCF)</span></span>
* <span data-ttu-id="360f2-125">Windows 密碼編譯</span><span class="sxs-lookup"><span data-stu-id="360f2-125">Windows Cryptography</span></span>
* <span data-ttu-id="360f2-126">Windows 事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="360f2-126">Windows EventLog</span></span>
* <span data-ttu-id="360f2-127">Windows Management Instrumentation (WMI)</span><span class="sxs-lookup"><span data-stu-id="360f2-127">Windows Management Instrumentation (WMI)</span></span>
* <span data-ttu-id="360f2-128">Windows 效能計數器</span><span class="sxs-lookup"><span data-stu-id="360f2-128">Windows Performance Counters</span></span>
* <span data-ttu-id="360f2-129">Windows 登錄</span><span class="sxs-lookup"><span data-stu-id="360f2-129">Windows Registry</span></span>
* <span data-ttu-id="360f2-130">Windows 執行階段快取</span><span class="sxs-lookup"><span data-stu-id="360f2-130">Windows Runtime Caching</span></span>
* <span data-ttu-id="360f2-131">Windows 服務</span><span class="sxs-lookup"><span data-stu-id="360f2-131">Windows Services</span></span>

<span data-ttu-id="360f2-132">如需詳細資訊，請參閱[規格的相容性套件](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md)。</span><span class="sxs-lookup"><span data-stu-id="360f2-132">For more information, see the [spec of the compatibility pack](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="360f2-133">開始使用</span><span class="sxs-lookup"><span data-stu-id="360f2-133">Get started</span></span>

1. <span data-ttu-id="360f2-134">在之前移轉，請確定看看[移轉程序](index.md)。</span><span class="sxs-lookup"><span data-stu-id="360f2-134">Before porting, make sure to take a look at the [Porting Process](index.md).</span></span>

2. <span data-ttu-id="360f2-135">當現有程式碼移植到.NET Core 或.NET 標準，安裝 NuGet 套件[Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility)。</span><span class="sxs-lookup"><span data-stu-id="360f2-135">When porting existing code to .NET Core or .NET Standard, install the NuGet package [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span>

3. <span data-ttu-id="360f2-136">如果您想要放入 Windows 時，所有設定。</span><span class="sxs-lookup"><span data-stu-id="360f2-136">If you want to stay on Windows, you're all set.</span></span>

4. <span data-ttu-id="360f2-137">如果您想要在 Linux 或 macOS 執行.NET Core 應用程式或.NET 標準程式庫，使用[API 分析器](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/)若要尋找的 Api，將無法運作的跨平台的使用方式。</span><span class="sxs-lookup"><span data-stu-id="360f2-137">If you want to run the .NET Core application or .NET Standard library on Linux or macOS, use the [API Analyzer](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) to find usage of APIs that won't work cross-platform.</span></span>

5. <span data-ttu-id="360f2-138">請移除這些 Api 的用法，取代跨平台的替代方案，或保護使用平台檢查，例如：</span><span class="sxs-lookup"><span data-stu-id="360f2-138">Either remove the usages of those APIs, replace them with cross-platform alternatives, or guard them using a platform check, like:</span></span>

    ```csharp
    private static string GetLoggingPath()
    {
        // Verify the code is running on Windows.
        if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
        {
            using (var key = Registry.CurrentUser.OpenSubKey(@"Software\Fabrikam\AssetManagement"))
            {
                if (key?.GetValue("LoggingDirectoryPath") is string configuredPath)
                    return configuredPath;
            }
        }

        // This is either not running on Windows or no logging path was configured,
        // so just use the path for non-roaming user-specific data files.
        var appDataPath = Environment.GetFolderPath(Environment.SpecialFolder.LocalApplicationData);
        return Path.Combine(appDataPath, "Fabrikam", "AssetManagement", "Logging");
    }
    ```

<span data-ttu-id="360f2-139">如需示範，查看[的 Windows 相容性套件的 Channel 9 影片](https://channel9.msdn.com/Events/Connect/2017/T123)。</span><span class="sxs-lookup"><span data-stu-id="360f2-139">For a demo, check out the [Channel 9 video of the Windows Compatibility Pack](https://channel9.msdn.com/Events/Connect/2017/T123).</span></span>

