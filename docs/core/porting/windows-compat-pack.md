---
title: 使用 Windows 相容性套件將程式碼移植到 .NET Core
description: 瞭解 Windows 相容性包以及如何使用它將現有的 .NET 框架代碼移植到 .NET Core。
author: terrajobst
ms.date: 12/07/2018
ms.openlocfilehash: 166259ca37a2005d67f6c545e4843a940f05fb71
ms.sourcegitcommit: b75a45f0cfe012b71b45dd9bf723adf32369d40c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80228642"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a><span data-ttu-id="ab9b4-103">使用 Windows 相容性套件將程式碼移植到 .NET Core</span><span class="sxs-lookup"><span data-stu-id="ab9b4-103">Use the Windows Compatibility Pack to port code to .NET Core</span></span>

<span data-ttu-id="ab9b4-104">將現有代碼移植到 .NET Core 時發現的一些最常見問題是依賴于 API 和僅在 .NET 框架中找到的技術。</span><span class="sxs-lookup"><span data-stu-id="ab9b4-104">Some of the most common issues found when porting existing code to .NET Core are dependencies on APIs and technologies that are only found in .NET Framework.</span></span> <span data-ttu-id="ab9b4-105">*Windows 相容性套件*提供許多這些技術，因此建置 .NET Core 應用程式和 .NET Standard 程式庫很容易。</span><span class="sxs-lookup"><span data-stu-id="ab9b4-105">The *Windows Compatibility Pack* provides many of these technologies, so it's much easier to build .NET Core applications and .NET Standard libraries.</span></span>

<span data-ttu-id="ab9b4-106">相容性包是[.NET 標準 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support)的邏輯擴展，可顯著增加 API 集。</span><span class="sxs-lookup"><span data-stu-id="ab9b4-106">The compatibility pack is a logical [extension of .NET Standard 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) that significantly increases the API set.</span></span> <span data-ttu-id="ab9b4-107">現有代碼編譯時幾乎沒有修改。</span><span class="sxs-lookup"><span data-stu-id="ab9b4-107">Existing code compiles with almost no modifications.</span></span> <span data-ttu-id="ab9b4-108">為了信守"所有 .NET 實現提供的 API 集"的承諾，.NET 標準不包括無法在所有平臺（如註冊表、Windows 管理檢測 （WMI） 或反射發出 API）中工作的技術。</span><span class="sxs-lookup"><span data-stu-id="ab9b4-108">To keep its promise of "the set of APIs that all .NET implementations provide", .NET Standard doesn't include technologies that can't work across all platforms, such as registry, Windows Management Instrumentation (WMI), or reflection emit APIs.</span></span> <span data-ttu-id="ab9b4-109">Windows 相容性包位於 .NET 標準之上，提供對這些僅 Windows 技術的訪問。</span><span class="sxs-lookup"><span data-stu-id="ab9b4-109">The Windows Compatibility Pack sits on top of .NET Standard and provides access to these Windows-only technologies.</span></span> <span data-ttu-id="ab9b4-110">對於想要遷移到 .NET Core 但計畫留在 Windows 上的客戶來說，這尤其有用，至少作為第一步。</span><span class="sxs-lookup"><span data-stu-id="ab9b4-110">It's especially useful for customers that want to move to .NET Core but plan to stay on Windows, at least as a first step.</span></span> <span data-ttu-id="ab9b4-111">在這種情況下，能夠使用僅 Windows 技術可消除遷移障礙。</span><span class="sxs-lookup"><span data-stu-id="ab9b4-111">In that scenario, being able to use Windows-only technologies removes the migration hurdle.</span></span>

## <a name="package-contents"></a><span data-ttu-id="ab9b4-112">封裝內容</span><span class="sxs-lookup"><span data-stu-id="ab9b4-112">Package contents</span></span>

<span data-ttu-id="ab9b4-113">Windows 相容性包通過[Microsoft.Windows.相容性 NuGet 包](https://www.nuget.org/packages/Microsoft.Windows.Compatibility)提供，可以從針對 .NET Core 或 .NET 標準的專案引用。</span><span class="sxs-lookup"><span data-stu-id="ab9b4-113">The Windows Compatibility Pack is provided via the [Microsoft.Windows.Compatibility NuGet package](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) and can be referenced from projects that target .NET Core or .NET Standard.</span></span>

<span data-ttu-id="ab9b4-114">它提供約 20,000 個 API，包括僅限 Windows 以及來自下列技術領域的跨平台 API：</span><span class="sxs-lookup"><span data-stu-id="ab9b4-114">It provides about 20,000 APIs, including Windows-only as well as cross-platform APIs from the following technology areas:</span></span>

- <span data-ttu-id="ab9b4-115">字碼頁</span><span class="sxs-lookup"><span data-stu-id="ab9b4-115">Code Pages</span></span>
- <span data-ttu-id="ab9b4-116">CodeDom</span><span class="sxs-lookup"><span data-stu-id="ab9b4-116">CodeDom</span></span>
- <span data-ttu-id="ab9b4-117">組態</span><span class="sxs-lookup"><span data-stu-id="ab9b4-117">Configuration</span></span>
- <span data-ttu-id="ab9b4-118">目錄服務</span><span class="sxs-lookup"><span data-stu-id="ab9b4-118">Directory Services</span></span>
- <span data-ttu-id="ab9b4-119">繪圖</span><span class="sxs-lookup"><span data-stu-id="ab9b4-119">Drawing</span></span>
- <span data-ttu-id="ab9b4-120">ODBC</span><span class="sxs-lookup"><span data-stu-id="ab9b4-120">ODBC</span></span>
- <span data-ttu-id="ab9b4-121">權限</span><span class="sxs-lookup"><span data-stu-id="ab9b4-121">Permissions</span></span>
- <span data-ttu-id="ab9b4-122">連接埠</span><span class="sxs-lookup"><span data-stu-id="ab9b4-122">Ports</span></span>
- <span data-ttu-id="ab9b4-123">Windows 存取控制清單 (ACL)</span><span class="sxs-lookup"><span data-stu-id="ab9b4-123">Windows Access Control Lists (ACL)</span></span>
- <span data-ttu-id="ab9b4-124">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="ab9b4-124">Windows Communication Foundation (WCF)</span></span>
- <span data-ttu-id="ab9b4-125">Windows 加密</span><span class="sxs-lookup"><span data-stu-id="ab9b4-125">Windows Cryptography</span></span>
- <span data-ttu-id="ab9b4-126">Windows EventLog</span><span class="sxs-lookup"><span data-stu-id="ab9b4-126">Windows EventLog</span></span>
- <span data-ttu-id="ab9b4-127">Windows Management Instrumentation (WMI)</span><span class="sxs-lookup"><span data-stu-id="ab9b4-127">Windows Management Instrumentation (WMI)</span></span>
- <span data-ttu-id="ab9b4-128">Windows 效能計數器</span><span class="sxs-lookup"><span data-stu-id="ab9b4-128">Windows Performance Counters</span></span>
- <span data-ttu-id="ab9b4-129">Windows 登錄</span><span class="sxs-lookup"><span data-stu-id="ab9b4-129">Windows Registry</span></span>
- <span data-ttu-id="ab9b4-130">Windows 執行階段快取</span><span class="sxs-lookup"><span data-stu-id="ab9b4-130">Windows Runtime Caching</span></span>
- <span data-ttu-id="ab9b4-131">Windows 服務</span><span class="sxs-lookup"><span data-stu-id="ab9b4-131">Windows Services</span></span>

<span data-ttu-id="ab9b4-132">如需詳細資訊，請參閱[相容性套件規格](https://github.com/dotnet/designs/blob/master/accepted/2018/compat-pack/compat-pack.md)。</span><span class="sxs-lookup"><span data-stu-id="ab9b4-132">For more information, see the [specification of the compatibility pack](https://github.com/dotnet/designs/blob/master/accepted/2018/compat-pack/compat-pack.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="ab9b4-133">開始使用</span><span class="sxs-lookup"><span data-stu-id="ab9b4-133">Get started</span></span>

1. <span data-ttu-id="ab9b4-134">在移植之前，請務必查看[移植過程](index.md)。</span><span class="sxs-lookup"><span data-stu-id="ab9b4-134">Before porting, make sure to take a look at the [Porting process](index.md).</span></span>

2. <span data-ttu-id="ab9b4-135">將現有代碼移植到 .NET Core 或 .NET 標準時，請安裝[Microsoft.Windows.相容性 NuGet 包](https://www.nuget.org/packages/Microsoft.Windows.Compatibility)。</span><span class="sxs-lookup"><span data-stu-id="ab9b4-135">When porting existing code to .NET Core or .NET Standard, install the [Microsoft.Windows.Compatibility NuGet package](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span>

   <span data-ttu-id="ab9b4-136">如果您想要留在 Windows，即已完成所有準備。</span><span class="sxs-lookup"><span data-stu-id="ab9b4-136">If you want to stay on Windows, you're all set.</span></span>

3. <span data-ttu-id="ab9b4-137">如果您想要在 Linux 或 macOS 上執行 .NET Core 應用程式或 .NET Standard 程式庫，請使用 [API 分析器](../../standard/analyzers/api-analyzer.md)尋找無法跨平台運作的 API 使用方式。</span><span class="sxs-lookup"><span data-stu-id="ab9b4-137">If you want to run the .NET Core application or .NET Standard library on Linux or macOS, use the [API Analyzer](../../standard/analyzers/api-analyzer.md) to find usage of APIs that won't work cross-platform.</span></span>

4. <span data-ttu-id="ab9b4-138">移除這些 API 的使用方式，以跨平台的替代方案取代，或使用平台檢查保護它們，例如：</span><span class="sxs-lookup"><span data-stu-id="ab9b4-138">Either remove the usages of those APIs, replace them with cross-platform alternatives, or guard them using a platform check, like:</span></span>

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

<span data-ttu-id="ab9b4-139">如需示範，請查看 [Channel 9 的 Windows 相容性套件影片](https://channel9.msdn.com/Events/Connect/2017/T123)。</span><span class="sxs-lookup"><span data-stu-id="ab9b4-139">For a demo, check out the [Channel 9 video of the Windows Compatibility Pack](https://channel9.msdn.com/Events/Connect/2017/T123).</span></span>
