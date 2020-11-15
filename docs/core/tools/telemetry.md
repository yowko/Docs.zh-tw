---
title: .NET SDK 遙測
description: 探索收集使用量資訊以進行分析的 .NET SDK 遙測功能、收集的資料，以及如何停用。
author: KathleenDollard
ms.date: 08/27/2019
ms.openlocfilehash: 4f137822c61e1a04eccd28ebd0cd56c04f4a85e2
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2020
ms.locfileid: "94633865"
---
# <a name="net-sdk-telemetry"></a><span data-ttu-id="891df-103">.NET SDK 遙測</span><span class="sxs-lookup"><span data-stu-id="891df-103">.NET SDK telemetry</span></span>

<span data-ttu-id="891df-104">[.NET SDK](index.md)包含遙測功能，可在 .net CLI 損毀時，收集使用方式資料和例外狀況資訊。</span><span class="sxs-lookup"><span data-stu-id="891df-104">The [.NET SDK](index.md) includes a telemetry feature that collects usage data and exception information when the .NET CLI crashes.</span></span> <span data-ttu-id="891df-105">.Net CLI 隨附 .NET SDK，是一組可讓您建立、測試和發佈 .NET 應用程式的動詞命令。</span><span class="sxs-lookup"><span data-stu-id="891df-105">The .NET CLI comes with the .NET SDK and is the set of verbs that enable you to build, test, and publish your .NET apps.</span></span> <span data-ttu-id="891df-106">.NET 小組必須了解使用者如何使用這些工具，以便進行改善。</span><span class="sxs-lookup"><span data-stu-id="891df-106">It's important that the .NET team understands how the tools are used so they can be improved.</span></span> <span data-ttu-id="891df-107">失敗資訊可協助小組解決問題並修正 Bug。</span><span class="sxs-lookup"><span data-stu-id="891df-107">Information on failures helps the team resolve problems and fix bugs.</span></span>

<span data-ttu-id="891df-108">收集的資料會在「 [創意 Commons](https://creativecommons.org/licenses/by/4.0/)屬性」授權下的匯總中發行。</span><span class="sxs-lookup"><span data-stu-id="891df-108">The collected data is published in aggregate under the [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span></span>

## <a name="scope"></a><span data-ttu-id="891df-109">範圍</span><span class="sxs-lookup"><span data-stu-id="891df-109">Scope</span></span>

<span data-ttu-id="891df-110">`dotnet` 有兩個功能：執行應用程式，以及執行 CLI 命令。</span><span class="sxs-lookup"><span data-stu-id="891df-110">`dotnet` has two functions: to run apps, and to execute CLI commands.</span></span> <span data-ttu-id="891df-111">使用 `dotnet` 啟動應用程式時 (格式如下)，「不會收集」遙測：</span><span class="sxs-lookup"><span data-stu-id="891df-111">Telemetry *isn't collected* when using `dotnet` to start an application in the following format:</span></span>

- `dotnet [path-to-app].dll`

<span data-ttu-id="891df-112">使用任何 [.NET CLI 命令](index.md)時， *會收集* 遙測，例如：</span><span class="sxs-lookup"><span data-stu-id="891df-112">Telemetry *is collected* when using any of the [.NET CLI commands](index.md), such as:</span></span>

- `dotnet build`
- `dotnet pack`
- `dotnet run`

## <a name="how-to-opt-out"></a><span data-ttu-id="891df-113">如何選擇退出</span><span class="sxs-lookup"><span data-stu-id="891df-113">How to opt out</span></span>

<span data-ttu-id="891df-114">預設會啟用 .NET SDK 遙測功能。</span><span class="sxs-lookup"><span data-stu-id="891df-114">The .NET SDK telemetry feature is enabled by default.</span></span> <span data-ttu-id="891df-115">若要退出遙測功能，請將 `DOTNET_CLI_TELEMETRY_OPTOUT` 環境變數設定為 `1` 或 `true`。</span><span class="sxs-lookup"><span data-stu-id="891df-115">To opt out of the telemetry feature, set the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span>

<span data-ttu-id="891df-116">當安裝成功時，.NET SDK 安裝程式也會傳送單一遙測專案。</span><span class="sxs-lookup"><span data-stu-id="891df-116">A single telemetry entry is also sent by the .NET SDK installer when a successful installation happens.</span></span> <span data-ttu-id="891df-117">若要退出，請在 `DOTNET_CLI_TELEMETRY_OPTOUT` 安裝 .NET SDK 之前先設定環境變數。</span><span class="sxs-lookup"><span data-stu-id="891df-117">To opt out, set the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable before you install the .NET SDK.</span></span>

## <a name="disclosure"></a><span data-ttu-id="891df-118">公開</span><span class="sxs-lookup"><span data-stu-id="891df-118">Disclosure</span></span>

<span data-ttu-id="891df-119">當您第一次執行其中一個 [.NET CLI 命令](index.md) 時，.net SDK 會顯示與下列類似的文字 (例如 `dotnet build`) 。</span><span class="sxs-lookup"><span data-stu-id="891df-119">The .NET SDK displays text similar to the following when you first run one of the [.NET CLI commands](index.md) (for example, `dotnet build`).</span></span> <span data-ttu-id="891df-120">文字可能略有不同，視執行中的 SDK 版本而定。</span><span class="sxs-lookup"><span data-stu-id="891df-120">Text may vary slightly depending on the version of the SDK you're running.</span></span> <span data-ttu-id="891df-121">這個「第一次執行」經驗是 Microsoft 如何通知您有關資料收集。</span><span class="sxs-lookup"><span data-stu-id="891df-121">This "first run" experience is how Microsoft notifies you about data collection.</span></span>

```console
Telemetry
---------
The .NET tools collect usage data in order to help us improve your experience. The data is collected by Microsoft and shared with the community. You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry
```

<span data-ttu-id="891df-122">若要停用此訊息和 .NET 歡迎使用訊息，請將 `DOTNET_NOLOGO` 環境變數設為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="891df-122">To disable this message and the .NET welcome message, set the `DOTNET_NOLOGO` environment variable to `true`.</span></span> <span data-ttu-id="891df-123">請注意，此變數不會影響已退出的遙測。</span><span class="sxs-lookup"><span data-stu-id="891df-123">Note that this variable has no effect on telemetry opt out.</span></span>

## <a name="data-points"></a><span data-ttu-id="891df-124">資料點</span><span class="sxs-lookup"><span data-stu-id="891df-124">Data points</span></span>

<span data-ttu-id="891df-125">遙測功能不會收集個人資料，例如使用者名稱或電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="891df-125">The telemetry feature doesn't collect personal data, such as usernames or email addresses.</span></span> <span data-ttu-id="891df-126">它不會掃描您的程式碼，也不會擷取專案層級資料，例如名稱、存放庫或作者。</span><span class="sxs-lookup"><span data-stu-id="891df-126">It doesn't scan your code and doesn't extract project-level data, such as name, repository, or author.</span></span> <span data-ttu-id="891df-127">資料使用 [Azure 監視器](https://azure.microsoft.com/services/monitor/)技術安全地傳送至 Microsoft 伺服器、在限制存取下保留，並在嚴格安全性控制下從安全的 [Azure 儲存體](https://azure.microsoft.com/services/storage/)系統發佈。</span><span class="sxs-lookup"><span data-stu-id="891df-127">The data is sent securely to Microsoft servers using [Azure Monitor](https://azure.microsoft.com/services/monitor/) technology, held under restricted access, and published under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

<span data-ttu-id="891df-128">保護您的隱私權對我們而言很重要。</span><span class="sxs-lookup"><span data-stu-id="891df-128">Protecting your privacy is important to us.</span></span> <span data-ttu-id="891df-129">如果您懷疑遙測收集敏感性資料或資料正在, 或不當處理，請在 [dotnet/sdk](https://github.com/dotnet/sdk/issues) 存放庫中提出問題，或傳送電子郵件以 [dotnet@microsoft.com](mailto:dotnet@microsoft.com) 供調查。</span><span class="sxs-lookup"><span data-stu-id="891df-129">If you suspect the telemetry is collecting sensitive data or the data is being insecurely or inappropriately handled, file an issue in the [dotnet/sdk](https://github.com/dotnet/sdk/issues) repository or send an email to [dotnet@microsoft.com](mailto:dotnet@microsoft.com) for investigation.</span></span>

<span data-ttu-id="891df-130">遙測功能會收集下列資料：</span><span class="sxs-lookup"><span data-stu-id="891df-130">The telemetry feature collects the following data:</span></span>

| <span data-ttu-id="891df-131">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="891df-131">SDK versions</span></span> | <span data-ttu-id="891df-132">資料</span><span class="sxs-lookup"><span data-stu-id="891df-132">Data</span></span> |
|--------------|------|
| <span data-ttu-id="891df-133">全部</span><span class="sxs-lookup"><span data-stu-id="891df-133">All</span></span>          | <span data-ttu-id="891df-134">叫用的時間戳記。</span><span class="sxs-lookup"><span data-stu-id="891df-134">Timestamp of invocation.</span></span> |
| <span data-ttu-id="891df-135">全部</span><span class="sxs-lookup"><span data-stu-id="891df-135">All</span></span>          | <span data-ttu-id="891df-136">叫用的命令 (例如 "build")，從 2.1 開始已雜湊。</span><span class="sxs-lookup"><span data-stu-id="891df-136">Command invoked (for example, "build"), hashed starting in 2.1.</span></span> |
| <span data-ttu-id="891df-137">全部</span><span class="sxs-lookup"><span data-stu-id="891df-137">All</span></span>          | <span data-ttu-id="891df-138">用來判斷地理位置的三個八位元 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="891df-138">Three octet IP address used to determine the geographical location.</span></span> |
| <span data-ttu-id="891df-139">全部</span><span class="sxs-lookup"><span data-stu-id="891df-139">All</span></span>          | <span data-ttu-id="891df-140">作業系統和版本。</span><span class="sxs-lookup"><span data-stu-id="891df-140">Operating system and version.</span></span> |
| <span data-ttu-id="891df-141">全部</span><span class="sxs-lookup"><span data-stu-id="891df-141">All</span></span>          | <span data-ttu-id="891df-142">SDK 正在執行的執行階段識別碼 (RID)。</span><span class="sxs-lookup"><span data-stu-id="891df-142">Runtime ID (RID) the SDK is running on.</span></span> |
| <span data-ttu-id="891df-143">全部</span><span class="sxs-lookup"><span data-stu-id="891df-143">All</span></span>          | <span data-ttu-id="891df-144">.NET SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="891df-144">.NET SDK version.</span></span> |
| <span data-ttu-id="891df-145">全部</span><span class="sxs-lookup"><span data-stu-id="891df-145">All</span></span>          | <span data-ttu-id="891df-146">遙測設定檔：選擇性值，只能透過明確的使用者加入使用，且只能在 Microsoft 內部使用。</span><span class="sxs-lookup"><span data-stu-id="891df-146">Telemetry profile: an optional value only used with explicit user opt-in and used internally at Microsoft.</span></span> |
| <span data-ttu-id="891df-147">>=2.0</span><span class="sxs-lookup"><span data-stu-id="891df-147">>=2.0</span></span>        | <span data-ttu-id="891df-148">命令引數和選項：會收集數個引數和選項 (不是任意字串)。</span><span class="sxs-lookup"><span data-stu-id="891df-148">Command arguments and options: several arguments and options are collected (not arbitrary strings).</span></span> <span data-ttu-id="891df-149">請參閱[收集的選項](#collected-options)。</span><span class="sxs-lookup"><span data-stu-id="891df-149">See [collected options](#collected-options).</span></span> <span data-ttu-id="891df-150">2.1.300 之後已雜湊。</span><span class="sxs-lookup"><span data-stu-id="891df-150">Hashed after 2.1.300.</span></span> |
| <span data-ttu-id="891df-151">>=2.0</span><span class="sxs-lookup"><span data-stu-id="891df-151">>=2.0</span></span>         | <span data-ttu-id="891df-152">SDK 是否正在容器中執行。</span><span class="sxs-lookup"><span data-stu-id="891df-152">Whether the SDK is running in a container.</span></span> |
| <span data-ttu-id="891df-153">>=2.0</span><span class="sxs-lookup"><span data-stu-id="891df-153">>=2.0</span></span>         | <span data-ttu-id="891df-154">目標 Framework (來自 `TargetFramework` 事件)，從 2.1 開始已雜湊。</span><span class="sxs-lookup"><span data-stu-id="891df-154">Target frameworks (from the `TargetFramework` event), hashed starting in 2.1.</span></span> |
| <span data-ttu-id="891df-155">>=2.0</span><span class="sxs-lookup"><span data-stu-id="891df-155">>=2.0</span></span>         | <span data-ttu-id="891df-156">雜湊媒體存取控制 (MAC) 位址 (SHA256) 。</span><span class="sxs-lookup"><span data-stu-id="891df-156">Hashed Media Access Control (MAC) address (SHA256).</span></span> |
| <span data-ttu-id="891df-157">>=2.0</span><span class="sxs-lookup"><span data-stu-id="891df-157">>=2.0</span></span>         | <span data-ttu-id="891df-158">雜湊的目前工作目錄。</span><span class="sxs-lookup"><span data-stu-id="891df-158">Hashed current working directory.</span></span> |
| <span data-ttu-id="891df-159">>=2.0</span><span class="sxs-lookup"><span data-stu-id="891df-159">>=2.0</span></span>         | <span data-ttu-id="891df-160">使用雜湊的安裝程式 exe 檔名來安裝成功報告。</span><span class="sxs-lookup"><span data-stu-id="891df-160">Install success report, with hashed installer exe filename.</span></span> |
| <span data-ttu-id="891df-161">>=2.1.300</span><span class="sxs-lookup"><span data-stu-id="891df-161">>=2.1.300</span></span>     | <span data-ttu-id="891df-162">核心版本。</span><span class="sxs-lookup"><span data-stu-id="891df-162">Kernel version.</span></span> |
| <span data-ttu-id="891df-163">>=2.1.300</span><span class="sxs-lookup"><span data-stu-id="891df-163">>=2.1.300</span></span>     | <span data-ttu-id="891df-164">Libc 發行/版本。</span><span class="sxs-lookup"><span data-stu-id="891df-164">Libc release/version.</span></span> |
| <span data-ttu-id="891df-165">>=3.0.100</span><span class="sxs-lookup"><span data-stu-id="891df-165">>=3.0.100</span></span>     | <span data-ttu-id="891df-166">輸出是否已重新導向 (true 或 false)。</span><span class="sxs-lookup"><span data-stu-id="891df-166">Whether the output was redirected (true or false).</span></span> |
| <span data-ttu-id="891df-167">>=3.0.100</span><span class="sxs-lookup"><span data-stu-id="891df-167">>=3.0.100</span></span>     | <span data-ttu-id="891df-168">CLI/SDK 損毀時的例外狀況類型及其堆疊追蹤 (只有 CLI/SDK 程式碼會包含在傳送的堆疊追蹤中)。</span><span class="sxs-lookup"><span data-stu-id="891df-168">On a CLI/SDK crash, the exception type and its stack trace (only CLI/SDK code is included in the stack trace sent).</span></span> <span data-ttu-id="891df-169">如需詳細資訊，請參閱 [收集的 .NET CLI/SDK 損毀例外狀況遙測](#net-clisdk-crash-exception-telemetry-collected)。</span><span class="sxs-lookup"><span data-stu-id="891df-169">For more information, see [.NET CLI/SDK crash exception telemetry collected](#net-clisdk-crash-exception-telemetry-collected).</span></span> |

### <a name="collected-options"></a><span data-ttu-id="891df-170">收集的選項</span><span class="sxs-lookup"><span data-stu-id="891df-170">Collected options</span></span>

<span data-ttu-id="891df-171">某些命令會傳送額外的資料。</span><span class="sxs-lookup"><span data-stu-id="891df-171">Certain commands send additional data.</span></span> <span data-ttu-id="891df-172">命令的子集會傳送第一個引數：</span><span class="sxs-lookup"><span data-stu-id="891df-172">A subset of commands sends the first argument:</span></span>

| <span data-ttu-id="891df-173">命令</span><span class="sxs-lookup"><span data-stu-id="891df-173">Command</span></span>               | <span data-ttu-id="891df-174">傳送的第一個引數資料</span><span class="sxs-lookup"><span data-stu-id="891df-174">First argument data sent</span></span>                |
|-----------------------|-----------------------------------------|
| `dotnet help <arg>`   | <span data-ttu-id="891df-175">要查詢的命令說明。</span><span class="sxs-lookup"><span data-stu-id="891df-175">The command help is being queried for.</span></span>  |
| `dotnet new <arg>`    | <span data-ttu-id="891df-176">範本名稱 (已雜湊)。</span><span class="sxs-lookup"><span data-stu-id="891df-176">The template name (hashed).</span></span>             |
| `dotnet add <arg>`    | <span data-ttu-id="891df-177">`package` 或 `reference` 一字。</span><span class="sxs-lookup"><span data-stu-id="891df-177">The word `package` or `reference`.</span></span>      |
| `dotnet remove <arg>` | <span data-ttu-id="891df-178">`package` 或 `reference` 一字。</span><span class="sxs-lookup"><span data-stu-id="891df-178">The word `package` or `reference`.</span></span>      |
| `dotnet list <arg>`   | <span data-ttu-id="891df-179">`package` 或 `reference` 一字。</span><span class="sxs-lookup"><span data-stu-id="891df-179">The word `package` or `reference`.</span></span>      |
| `dotnet sln <arg>`    | <span data-ttu-id="891df-180">`add`、`list` 或 `remove` 一字。</span><span class="sxs-lookup"><span data-stu-id="891df-180">The word `add`, `list`, or `remove`.</span></span>    |
| `dotnet nuget <arg>`  | <span data-ttu-id="891df-181">`delete`、`locals` 或 `push` 一字。</span><span class="sxs-lookup"><span data-stu-id="891df-181">The word `delete`, `locals`, or `push`.</span></span> |

<span data-ttu-id="891df-182">命令的子集會傳送所選取選項 (如果已使用) 及其值：</span><span class="sxs-lookup"><span data-stu-id="891df-182">A subset of commands sends selected options if they're used, along with their values:</span></span>

| <span data-ttu-id="891df-183">選項</span><span class="sxs-lookup"><span data-stu-id="891df-183">Option</span></span>                  | <span data-ttu-id="891df-184">命令</span><span class="sxs-lookup"><span data-stu-id="891df-184">Commands</span></span>                                                                                       |
|-------------------------|------------------------------------------------------------------------------------------------|
| `--verbosity`           | <span data-ttu-id="891df-185">所有命令</span><span class="sxs-lookup"><span data-stu-id="891df-185">All commands</span></span>                                                                                   |
| `--language`            | `dotnet new`                                                                                   |
| `--configuration`       | <span data-ttu-id="891df-186">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`</span><span class="sxs-lookup"><span data-stu-id="891df-186">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`</span></span>                  |
| `--framework`           | <span data-ttu-id="891df-187">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`, `dotnet vstest`</span><span class="sxs-lookup"><span data-stu-id="891df-187">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`, `dotnet vstest`</span></span> |
| `--runtime`             | <span data-ttu-id="891df-188">`dotnet build`,  `dotnet publish`</span><span class="sxs-lookup"><span data-stu-id="891df-188">`dotnet build`,  `dotnet publish`</span></span>                                                              |
| `--platform`            | `dotnet vstest`                                                                                |
| `--logger`              | `dotnet vstest`                                                                                |
| `--sdk-package-version` | `dotnet migrate`                                                                               |

<span data-ttu-id="891df-189">除了 `--verbosity` 和 `--sdk-package-version` 以外，所有其他值都會從 .NET Core 2.1.100 SDK 開始進行雜湊。</span><span class="sxs-lookup"><span data-stu-id="891df-189">Except for `--verbosity` and `--sdk-package-version`, all the other values are hashed starting with .NET Core 2.1.100 SDK.</span></span>

## <a name="net-clisdk-crash-exception-telemetry-collected"></a><span data-ttu-id="891df-190">收集的 .NET CLI/SDK 損毀例外狀況遙測</span><span class="sxs-lookup"><span data-stu-id="891df-190">.NET CLI/SDK crash exception telemetry collected</span></span>

<span data-ttu-id="891df-191">如果 .NET CLI/SDK 損毀，它會收集例外狀況的名稱和 CLI/SDK 程式碼的堆疊追蹤。</span><span class="sxs-lookup"><span data-stu-id="891df-191">If the .NET CLI/SDK crashes, it collects the name of the exception and stack trace of the CLI/SDK code.</span></span> <span data-ttu-id="891df-192">收集這項資訊是為了評估問題，並改善 .NET SDK 和 CLI 的品質。</span><span class="sxs-lookup"><span data-stu-id="891df-192">This information is collected to assess problems and improve the quality of the .NET SDK and CLI.</span></span> <span data-ttu-id="891df-193">本文提供我們所收集資料的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="891df-193">This article provides information about the data we collect.</span></span> <span data-ttu-id="891df-194">它也提供使用者如何建立自己的 .NET SDK 版本的秘訣，以避免意外洩漏個人或機密資訊。</span><span class="sxs-lookup"><span data-stu-id="891df-194">It also provides tips on how users building their own version of the .NET SDK can avoid inadvertent disclosure of personal or sensitive information.</span></span>

### <a name="types-of-collected-data"></a><span data-ttu-id="891df-195">收集的資料類型</span><span class="sxs-lookup"><span data-stu-id="891df-195">Types of collected data</span></span>

<span data-ttu-id="891df-196">.NET CLI 只會收集 CLI/SDK 例外狀況的資訊，而不會收集您應用程式中的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="891df-196">.NET CLI collects information for CLI/SDK exceptions only, not exceptions in your application.</span></span> <span data-ttu-id="891df-197">所收集資料包含例外狀況的名稱和堆疊追蹤。</span><span class="sxs-lookup"><span data-stu-id="891df-197">The collected data contains the name of the exception and the stack trace.</span></span> <span data-ttu-id="891df-198">此堆疊追蹤是 CLI/SDK 程式碼的堆疊追蹤。</span><span class="sxs-lookup"><span data-stu-id="891df-198">This stack trace is of CLI/SDK code.</span></span>

<span data-ttu-id="891df-199">下列範例會顯示所收集的資料類型：</span><span class="sxs-lookup"><span data-stu-id="891df-199">The following example shows the kind of data that is collected:</span></span>

```console
System.IO.IOException
at System.ConsolePal.WindowsConsoleStream.Write(Byte[] buffer, Int32 offset, Int32 count)
at System.IO.StreamWriter.Flush(Boolean flushStream, Boolean flushEncoder)
at System.IO.StreamWriter.Write(Char[] buffer)
at System.IO.TextWriter.WriteLine()
at System.IO.TextWriter.SyncTextWriter.WriteLine()
at Microsoft.DotNet.Cli.Utils.Reporter.WriteLine()
at Microsoft.DotNet.Tools.Run.RunCommand.EnsureProjectIsBuilt()
at Microsoft.DotNet.Tools.Run.RunCommand.Execute()
at Microsoft.DotNet.Tools.Run.RunCommand.Run(String[] args)
at Microsoft.DotNet.Cli.Program.ProcessArgs(String[] args, ITelemetry telemetryClient)
at Microsoft.DotNet.Cli.Program.Main(String[] args)
```

### <a name="avoid-inadvertent-disclosure-of-information"></a><span data-ttu-id="891df-200">避免意外洩漏資訊</span><span class="sxs-lookup"><span data-stu-id="891df-200">Avoid inadvertent disclosure of information</span></span>

<span data-ttu-id="891df-201">.NET 參與者和任何其他執行自己所建立之 .NET SDK 版本的人，都應該考慮其 SDK 原始程式碼的路徑。</span><span class="sxs-lookup"><span data-stu-id="891df-201">.NET contributors and anyone else running a version of the .NET SDK that they built themselves should consider the path to their SDK source code.</span></span> <span data-ttu-id="891df-202">如果當您使用的 .NET SDK 是自訂的偵錯工具，或使用自訂群組建符號檔進行設定時發生當機，則會在堆疊追蹤中收集來自組建電腦的 SDK 來源檔案路徑，而不會進行雜湊處理。</span><span class="sxs-lookup"><span data-stu-id="891df-202">If a crash occurs while using a .NET SDK that is a custom debug build or configured with custom build symbol files, the SDK source file path from the build machine is collected as part of the stack trace and isn't hashed.</span></span>

<span data-ttu-id="891df-203">因此，.NET SDK 的自訂群組建不應位於路徑名稱公開個人或機密資訊的目錄中。</span><span class="sxs-lookup"><span data-stu-id="891df-203">Because of this, custom builds of the .NET SDK shouldn't be located in directories whose path names expose personal or sensitive information.</span></span>

## <a name="see-also"></a><span data-ttu-id="891df-204">另請參閱</span><span class="sxs-lookup"><span data-stu-id="891df-204">See also</span></span>

- [<span data-ttu-id="891df-205">.NET CLI 遙測資料</span><span class="sxs-lookup"><span data-stu-id="891df-205">.NET CLI Telemetry Data</span></span>](https://dotnet.microsoft.com/platform/telemetry)
- [<span data-ttu-id="891df-206">遙測參考來源 (dotnet/sdk 存放庫) </span><span class="sxs-lookup"><span data-stu-id="891df-206">Telemetry reference source (dotnet/sdk repository)</span></span>](https://github.com/dotnet/sdk/tree/master/src/Cli/dotnet/Telemetry)
