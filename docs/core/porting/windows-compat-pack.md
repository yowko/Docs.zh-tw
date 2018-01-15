---
title: "移植到 .NET Core - 使用 Windows 相容性套件"
description: "了解 Windows 相容性套件，以及如何使用它將現有的 .NET Framework 程式碼移植到 .NET Core"
keywords: ".NET, .NET Core, Windows, 相容性"
author: terrajobst
ms.author: mairaw
ms.date: 11/13/2017
ms.topic: article
ms.prod: .net-core
ms.workload: dotnetcore
ms.openlocfilehash: 3b1fe02aad4f78499158ecb7fa9b8521cb7d992e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="using-the-windows-compatibility-pack"></a><span data-ttu-id="e04ef-104">使用 Windows 相容性套件</span><span class="sxs-lookup"><span data-stu-id="e04ef-104">Using the Windows Compatibility Pack</span></span>

<span data-ttu-id="e04ef-105">開發人員將其現有的程式碼移植到 .NET Core 時最常面對的問題之一，是他依賴的 API 和技術只存在於 .NET Framework 中。</span><span class="sxs-lookup"><span data-stu-id="e04ef-105">One of the most common issues that developers face when porting their existing code to .NET Core is that they depend on APIs and technologies that only exist in the .NET Framework.</span></span> <span data-ttu-id="e04ef-106">「Windows 相容性套件」即將提供許多這些技術，以便使用現有程式碼來建置 .NET Core 應用程式以及 .NET Standard 程式庫更為可行。</span><span class="sxs-lookup"><span data-stu-id="e04ef-106">The *Windows Compatibility Pack* is about providing many of these technologies so that building .NET Core applications as well as .NET Standard libraries becomes much more viable for existing code.</span></span>

<span data-ttu-id="e04ef-107">此套件是邏輯的 [.NET Standard 2.0 延伸模組](../whats-new/index.md#api-changes-and-library-support)，可大幅增加 API 集和現有的程式碼編譯，幾乎不需要修改。</span><span class="sxs-lookup"><span data-stu-id="e04ef-107">This package is a logical [extension of .NET Standard 2.0](../whats-new/index.md#api-changes-and-library-support) that significantly increases API set and existing code compiles with almost no modifications.</span></span> <span data-ttu-id="e04ef-108">但為信守 .NET Standard 的承諾 (「它是所有 .NET 實作提供的 API 集」)，這不包括無法跨所有平台的技術，例如登錄、Windows Management Instrumentation (WMI) 或反映發出 API。</span><span class="sxs-lookup"><span data-stu-id="e04ef-108">But in order to keep the promise of .NET Standard ("it is the set of APIs that all .NET implementations provide"), this didn't include technologies that can't work across all platforms, such as registry, Windows Management Instrumentation (WMI), or reflection emit APIs.</span></span>

<span data-ttu-id="e04ef-109">「Windows 相容性套件」位階高於 .NET Standard，並提供存取僅限 Windows 的技術。</span><span class="sxs-lookup"><span data-stu-id="e04ef-109">The *Windows Compatibility Pack* sits on top of .NET Standard and provides access to technologies that are Windows only.</span></span> <span data-ttu-id="e04ef-110">它特別適合想要移至 .NET Core，但第一個步驟計劃停留在 Windows 的客戶。</span><span class="sxs-lookup"><span data-stu-id="e04ef-110">It's especially useful for customers that want to move to .NET Core but plan to stay on Windows as a first step.</span></span> <span data-ttu-id="e04ef-111">在這種情況下，無法使用僅限 Windows 技術只是無架構優勢的移轉障礙。</span><span class="sxs-lookup"><span data-stu-id="e04ef-111">In that scenario, not being able to use Windows-only technologies is only a migration hurdle with zero architectural benefits.</span></span>

## <a name="package-contents"></a><span data-ttu-id="e04ef-112">套件內容</span><span class="sxs-lookup"><span data-stu-id="e04ef-112">Package contents</span></span>

<span data-ttu-id="e04ef-113">「Windows 相容性套件」透過 NuGet 套件 [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) 提供，可從以 .NET Core 或 .NET Standard 為目標的專案參考。</span><span class="sxs-lookup"><span data-stu-id="e04ef-113">The *Windows Compatibility Pack* is provided via the NuGet Package [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) and can be referenced from projects targeting .NET Core or .NET Standard.</span></span>

<span data-ttu-id="e04ef-114">它提供約 20,000 個 API，包括僅限 Windows 以及來自下列技術領域的跨平台 API：</span><span class="sxs-lookup"><span data-stu-id="e04ef-114">It provides about 20,000 APIs, including Windows-only as well as cross-platform APIs from the following technology areas:</span></span>

* <span data-ttu-id="e04ef-115">字碼頁</span><span class="sxs-lookup"><span data-stu-id="e04ef-115">Code Pages</span></span>
* <span data-ttu-id="e04ef-116">CodeDom</span><span class="sxs-lookup"><span data-stu-id="e04ef-116">CodeDom</span></span>
* <span data-ttu-id="e04ef-117">組態</span><span class="sxs-lookup"><span data-stu-id="e04ef-117">Configuration</span></span>
* <span data-ttu-id="e04ef-118">目錄服務</span><span class="sxs-lookup"><span data-stu-id="e04ef-118">Directory Services</span></span>
* <span data-ttu-id="e04ef-119">繪圖</span><span class="sxs-lookup"><span data-stu-id="e04ef-119">Drawing</span></span>
* <span data-ttu-id="e04ef-120">ODBC</span><span class="sxs-lookup"><span data-stu-id="e04ef-120">ODBC</span></span>
* <span data-ttu-id="e04ef-121">權限</span><span class="sxs-lookup"><span data-stu-id="e04ef-121">Permissions</span></span>
* <span data-ttu-id="e04ef-122">連接埠</span><span class="sxs-lookup"><span data-stu-id="e04ef-122">Ports</span></span>
* <span data-ttu-id="e04ef-123">Windows 存取控制清單 (ACL)</span><span class="sxs-lookup"><span data-stu-id="e04ef-123">Windows Access Control Lists (ACL)</span></span>
* <span data-ttu-id="e04ef-124">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="e04ef-124">Windows Communication Foundation (WCF)</span></span>
* <span data-ttu-id="e04ef-125">Windows 加密</span><span class="sxs-lookup"><span data-stu-id="e04ef-125">Windows Cryptography</span></span>
* <span data-ttu-id="e04ef-126">Windows EventLog</span><span class="sxs-lookup"><span data-stu-id="e04ef-126">Windows EventLog</span></span>
* <span data-ttu-id="e04ef-127">Windows Management Instrumentation (WMI)</span><span class="sxs-lookup"><span data-stu-id="e04ef-127">Windows Management Instrumentation (WMI)</span></span>
* <span data-ttu-id="e04ef-128">Windows 效能計數器</span><span class="sxs-lookup"><span data-stu-id="e04ef-128">Windows Performance Counters</span></span>
* <span data-ttu-id="e04ef-129">Windows 登錄</span><span class="sxs-lookup"><span data-stu-id="e04ef-129">Windows Registry</span></span>
* <span data-ttu-id="e04ef-130">Windows 執行階段快取</span><span class="sxs-lookup"><span data-stu-id="e04ef-130">Windows Runtime Caching</span></span>
* <span data-ttu-id="e04ef-131">Windows 服務</span><span class="sxs-lookup"><span data-stu-id="e04ef-131">Windows Services</span></span>

<span data-ttu-id="e04ef-132">如需詳細資訊，請參閱[相容性套件規格](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md)。</span><span class="sxs-lookup"><span data-stu-id="e04ef-132">For more information, see the [spec of the compatibility pack](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="e04ef-133">開始使用</span><span class="sxs-lookup"><span data-stu-id="e04ef-133">Get started</span></span>

1. <span data-ttu-id="e04ef-134">移植前，請務必查看[移植程序](index.md)。</span><span class="sxs-lookup"><span data-stu-id="e04ef-134">Before porting, make sure to take a look at the [Porting Process](index.md).</span></span>

2. <span data-ttu-id="e04ef-135">將現有的程式碼移植到 .NET Core 或 .NET Standard 時，請安裝 NuGet 套件 [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility)。</span><span class="sxs-lookup"><span data-stu-id="e04ef-135">When porting existing code to .NET Core or .NET Standard, install the NuGet package [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span>

3. <span data-ttu-id="e04ef-136">如果您想要留在 Windows，即已完成所有準備。</span><span class="sxs-lookup"><span data-stu-id="e04ef-136">If you want to stay on Windows, you're all set.</span></span>

4. <span data-ttu-id="e04ef-137">如果您想要在 Linux 或 macOS 上執行 .NET Core 應用程式或 .NET Standard 程式庫，請使用 [API 分析器](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/)尋找無法跨平台運作的 API 使用方式。</span><span class="sxs-lookup"><span data-stu-id="e04ef-137">If you want to run the .NET Core application or .NET Standard library on Linux or macOS, use the [API Analyzer](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) to find usage of APIs that won't work cross-platform.</span></span>

5. <span data-ttu-id="e04ef-138">移除這些 API 的使用方式，以跨平台的替代方案取代，或使用平台檢查保護它們，例如：</span><span class="sxs-lookup"><span data-stu-id="e04ef-138">Either remove the usages of those APIs, replace them with cross-platform alternatives, or guard them using a platform check, like:</span></span>

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

<span data-ttu-id="e04ef-139">如需示範，請查看 [Channel 9 的 Windows 相容性套件影片](https://channel9.msdn.com/Events/Connect/2017/T123)。</span><span class="sxs-lookup"><span data-stu-id="e04ef-139">For a demo, check out the [Channel 9 video of the Windows Compatibility Pack](https://channel9.msdn.com/Events/Connect/2017/T123).</span></span>

