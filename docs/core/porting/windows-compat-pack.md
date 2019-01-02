---
title: 使用 Windows 相容性套件將程式碼移植到 .NET Core
description: 了解 Windows 相容性套件，以及如何使用它將現有的 .NET Framework 程式碼移植到 .NET Core
author: terrajobst
ms.date: 11/13/2017
ms.custom: seodec18
ms.openlocfilehash: 0a409c953ce38ed4c2959adaf4de9d3730ce37f4
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169933"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a><span data-ttu-id="de473-103">使用 Windows 相容性套件將程式碼移植到 .NET Core</span><span class="sxs-lookup"><span data-stu-id="de473-103">Use the Windows Compatibility Pack to port code to .NET Core</span></span>

<span data-ttu-id="de473-104">將現有程式碼移植到 .NET Core 時發現的一些最常見問題，是僅在 .NET Framework 中找到的 API 和技術相依性。</span><span class="sxs-lookup"><span data-stu-id="de473-104">Some of the most common issues found when porting existing code to .NET Core are dependencies on APIs and technologies that are only found in the .NET Framework.</span></span> <span data-ttu-id="de473-105">*Windows 相容性套件*提供許多這些技術，因此建置 .NET Core 應用程式和 .NET Standard 程式庫很容易。</span><span class="sxs-lookup"><span data-stu-id="de473-105">The *Windows Compatibility Pack* provides many of these technologies, so it's much easier to build .NET Core applications and .NET Standard libraries.</span></span>

<span data-ttu-id="de473-106">此套件是邏輯的 [.NET Standard 2.0 延伸模組](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support)，可大幅增加 API 集和現有的程式碼編譯，幾乎不需要修改。</span><span class="sxs-lookup"><span data-stu-id="de473-106">This package is a logical [extension of .NET Standard 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) that significantly increases API set and existing code compiles with almost no modifications.</span></span> <span data-ttu-id="de473-107">但為信守 .NET Standard 的承諾 (「它是所有 .NET 實作提供的 API 集」)，這不包括無法跨所有平台的技術，例如登錄、Windows Management Instrumentation (WMI) 或反映發出 API。</span><span class="sxs-lookup"><span data-stu-id="de473-107">But in order to keep the promise of .NET Standard ("it is the set of APIs that all .NET implementations provide"), this didn't include technologies that can't work across all platforms, such as registry, Windows Management Instrumentation (WMI), or reflection emit APIs.</span></span>

<span data-ttu-id="de473-108">「Windows 相容性套件」位階高於 .NET Standard，並提供存取僅限 Windows 的技術。</span><span class="sxs-lookup"><span data-stu-id="de473-108">The *Windows Compatibility Pack* sits on top of .NET Standard and provides access to technologies that are Windows only.</span></span> <span data-ttu-id="de473-109">它特別適合想要移至 .NET Core，但第一個步驟計劃停留在 Windows 的客戶。</span><span class="sxs-lookup"><span data-stu-id="de473-109">It's especially useful for customers that want to move to .NET Core but plan to stay on Windows as a first step.</span></span> <span data-ttu-id="de473-110">在這種情況下，無法使用僅限 Windows 技術只是無架構優勢的移轉障礙。</span><span class="sxs-lookup"><span data-stu-id="de473-110">In that scenario, not being able to use Windows-only technologies is only a migration hurdle with zero architectural benefits.</span></span>

## <a name="package-contents"></a><span data-ttu-id="de473-111">套件內容</span><span class="sxs-lookup"><span data-stu-id="de473-111">Package contents</span></span>

<span data-ttu-id="de473-112">「Windows 相容性套件」透過 NuGet 套件 [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) 提供，可從以 .NET Core 或 .NET Standard 為目標的專案參考。</span><span class="sxs-lookup"><span data-stu-id="de473-112">The *Windows Compatibility Pack* is provided via the NuGet Package [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) and can be referenced from projects targeting .NET Core or .NET Standard.</span></span>

<span data-ttu-id="de473-113">它提供約 20,000 個 API，包括僅限 Windows 以及來自下列技術領域的跨平台 API：</span><span class="sxs-lookup"><span data-stu-id="de473-113">It provides about 20,000 APIs, including Windows-only as well as cross-platform APIs from the following technology areas:</span></span>

* <span data-ttu-id="de473-114">字碼頁</span><span class="sxs-lookup"><span data-stu-id="de473-114">Code Pages</span></span>
* <span data-ttu-id="de473-115">CodeDom</span><span class="sxs-lookup"><span data-stu-id="de473-115">CodeDom</span></span>
* <span data-ttu-id="de473-116">Configuration</span><span class="sxs-lookup"><span data-stu-id="de473-116">Configuration</span></span>
* <span data-ttu-id="de473-117">目錄服務</span><span class="sxs-lookup"><span data-stu-id="de473-117">Directory Services</span></span>
* <span data-ttu-id="de473-118">繪圖</span><span class="sxs-lookup"><span data-stu-id="de473-118">Drawing</span></span>
* <span data-ttu-id="de473-119">ODBC</span><span class="sxs-lookup"><span data-stu-id="de473-119">ODBC</span></span>
* <span data-ttu-id="de473-120">權限</span><span class="sxs-lookup"><span data-stu-id="de473-120">Permissions</span></span>
* <span data-ttu-id="de473-121">連接埠</span><span class="sxs-lookup"><span data-stu-id="de473-121">Ports</span></span>
* <span data-ttu-id="de473-122">Windows 存取控制清單 (ACL)</span><span class="sxs-lookup"><span data-stu-id="de473-122">Windows Access Control Lists (ACL)</span></span>
* <span data-ttu-id="de473-123">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="de473-123">Windows Communication Foundation (WCF)</span></span>
* <span data-ttu-id="de473-124">Windows 加密</span><span class="sxs-lookup"><span data-stu-id="de473-124">Windows Cryptography</span></span>
* <span data-ttu-id="de473-125">Windows EventLog</span><span class="sxs-lookup"><span data-stu-id="de473-125">Windows EventLog</span></span>
* <span data-ttu-id="de473-126">Windows Management Instrumentation (WMI)</span><span class="sxs-lookup"><span data-stu-id="de473-126">Windows Management Instrumentation (WMI)</span></span>
* <span data-ttu-id="de473-127">Windows 效能計數器</span><span class="sxs-lookup"><span data-stu-id="de473-127">Windows Performance Counters</span></span>
* <span data-ttu-id="de473-128">Windows 登錄</span><span class="sxs-lookup"><span data-stu-id="de473-128">Windows Registry</span></span>
* <span data-ttu-id="de473-129">Windows 執行階段快取</span><span class="sxs-lookup"><span data-stu-id="de473-129">Windows Runtime Caching</span></span>
* <span data-ttu-id="de473-130">Windows 服務</span><span class="sxs-lookup"><span data-stu-id="de473-130">Windows Services</span></span>

<span data-ttu-id="de473-131">如需詳細資訊，請參閱[相容性套件規格](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md)。</span><span class="sxs-lookup"><span data-stu-id="de473-131">For more information, see the [spec of the compatibility pack](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="de473-132">開始使用</span><span class="sxs-lookup"><span data-stu-id="de473-132">Get started</span></span>

1. <span data-ttu-id="de473-133">移植前，請務必查看[移植程序](index.md)。</span><span class="sxs-lookup"><span data-stu-id="de473-133">Before porting, make sure to take a look at the [Porting Process](index.md).</span></span>

2. <span data-ttu-id="de473-134">將現有的程式碼移植到 .NET Core 或 .NET Standard 時，請安裝 NuGet 套件 [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility)。</span><span class="sxs-lookup"><span data-stu-id="de473-134">When porting existing code to .NET Core or .NET Standard, install the NuGet package [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span>

3. <span data-ttu-id="de473-135">如果您想要留在 Windows，即已完成所有準備。</span><span class="sxs-lookup"><span data-stu-id="de473-135">If you want to stay on Windows, you're all set.</span></span>

4. <span data-ttu-id="de473-136">如果您想要在 Linux 或 macOS 上執行 .NET Core 應用程式或 .NET Standard 程式庫，請使用 [API 分析器](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/)尋找無法跨平台運作的 API 使用方式。</span><span class="sxs-lookup"><span data-stu-id="de473-136">If you want to run the .NET Core application or .NET Standard library on Linux or macOS, use the [API Analyzer](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) to find usage of APIs that won't work cross-platform.</span></span>

5. <span data-ttu-id="de473-137">移除這些 API 的使用方式，以跨平台的替代方案取代，或使用平台檢查保護它們，例如：</span><span class="sxs-lookup"><span data-stu-id="de473-137">Either remove the usages of those APIs, replace them with cross-platform alternatives, or guard them using a platform check, like:</span></span>

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

<span data-ttu-id="de473-138">如需示範，請查看 [Channel 9 的 Windows 相容性套件影片](https://channel9.msdn.com/Events/Connect/2017/T123)。</span><span class="sxs-lookup"><span data-stu-id="de473-138">For a demo, check out the [Channel 9 video of the Windows Compatibility Pack](https://channel9.msdn.com/Events/Connect/2017/T123).</span></span>

