---
title: .NET Core SDK 遙測
description: 探索收集使用方式資訊以進行分析的 .NET Core SDK 遙測功能，它會收集哪些資料以及如何停用。
author: KathleenDollard
ms.date: 08/27/2019
ms.openlocfilehash: 0917dae23588ccd1809252aaf484c397e84561c7
ms.sourcegitcommit: 67cf756b033c6173a1bbd1cbd5aef1fccac99e34
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2020
ms.locfileid: "86226565"
---
# <a name="net-core-sdk-telemetry"></a><span data-ttu-id="eae29-103">.NET Core SDK 遙測</span><span class="sxs-lookup"><span data-stu-id="eae29-103">.NET Core SDK telemetry</span></span>

<span data-ttu-id="eae29-104">[.NET Core SDK](index.md) 包含遙測功能，可在 .NET Core CLI 損毀時收集使用方式資料和例外狀況資訊。</span><span class="sxs-lookup"><span data-stu-id="eae29-104">The [.NET Core SDK](index.md) includes a telemetry feature that collects usage data and exception information when the .NET Core CLI crashes.</span></span> <span data-ttu-id="eae29-105">.NET Core CLI 隨附 .NET Core SDK，是可讓您建置、測試及發佈 .NET Core 應用程式的動詞集。</span><span class="sxs-lookup"><span data-stu-id="eae29-105">The .NET Core CLI comes with the .NET Core SDK and is the set of verbs that enable you to build, test, and publish your .NET Core apps.</span></span> <span data-ttu-id="eae29-106">.NET 小組必須了解使用者如何使用這些工具，以便進行改善。</span><span class="sxs-lookup"><span data-stu-id="eae29-106">It's important that the .NET team understands how the tools are used so they can be improved.</span></span> <span data-ttu-id="eae29-107">失敗資訊可協助小組解決問題並修正 Bug。</span><span class="sxs-lookup"><span data-stu-id="eae29-107">Information on failures helps the team resolve problems and fix bugs.</span></span>

<span data-ttu-id="eae29-108">根據 [Creative Commons Attribution 授權](https://creativecommons.org/licenses/by/4.0/)，所收集的資料為匿名，且將會以彙總形式發佈。</span><span class="sxs-lookup"><span data-stu-id="eae29-108">The collected data is anonymous and published in aggregate under the [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span></span>

## <a name="scope"></a><span data-ttu-id="eae29-109">範圍</span><span class="sxs-lookup"><span data-stu-id="eae29-109">Scope</span></span>

<span data-ttu-id="eae29-110">`dotnet` 有兩個功能：執行應用程式，以及執行 CLI 命令。</span><span class="sxs-lookup"><span data-stu-id="eae29-110">`dotnet` has two functions: to run apps, and to execute CLI commands.</span></span> <span data-ttu-id="eae29-111">使用 `dotnet` 啟動應用程式時 (格式如下)，「不會收集」\*\* 遙測：</span><span class="sxs-lookup"><span data-stu-id="eae29-111">Telemetry *isn't collected* when using `dotnet` to start an application in the following format:</span></span>

- `dotnet [path-to-app].dll`

<span data-ttu-id="eae29-112">使用以下任何 [.NET Core CLI 命令](index.md) 時，則「會收集」\*\* 遙測：</span><span class="sxs-lookup"><span data-stu-id="eae29-112">Telemetry *is collected* when using any of the [.NET Core CLI commands](index.md), such as:</span></span>

- `dotnet build`
- `dotnet pack`
- `dotnet run`

## <a name="how-to-opt-out"></a><span data-ttu-id="eae29-113">如何選擇退出</span><span class="sxs-lookup"><span data-stu-id="eae29-113">How to opt out</span></span>

<span data-ttu-id="eae29-114">預設會啟用 .NET Core SDK 遙測功能。</span><span class="sxs-lookup"><span data-stu-id="eae29-114">The .NET Core SDK telemetry feature is enabled by default.</span></span> <span data-ttu-id="eae29-115">若要退出遙測功能，請將 `DOTNET_CLI_TELEMETRY_OPTOUT` 環境變數設定為 `1` 或 `true`。</span><span class="sxs-lookup"><span data-stu-id="eae29-115">To opt out of the telemetry feature, set the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span>

<span data-ttu-id="eae29-116">當安裝成功時，.NET Core SDK 安裝程式也會傳送單一遙測項目。</span><span class="sxs-lookup"><span data-stu-id="eae29-116">A single telemetry entry is also sent by the .NET Core SDK installer when a successful installation happens.</span></span> <span data-ttu-id="eae29-117">若要退出，請在安裝 .NET Core SDK 之前，先設定 `DOTNET_CLI_TELEMETRY_OPTOUT` 環境變數。</span><span class="sxs-lookup"><span data-stu-id="eae29-117">To opt out, set the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable before you install the .NET Core SDK.</span></span>

## <a name="disclosure"></a><span data-ttu-id="eae29-118">公開</span><span class="sxs-lookup"><span data-stu-id="eae29-118">Disclosure</span></span>

<span data-ttu-id="eae29-119">.NET Core SDK 會在您第一次執行其中一個 [.NET Core CLI 命令](index.md)時 (例如 `dotnet build`)，顯示類似如下的文字。</span><span class="sxs-lookup"><span data-stu-id="eae29-119">The .NET Core SDK displays text similar to the following when you first run one of the [.NET Core CLI commands](index.md) (for example, `dotnet build`).</span></span> <span data-ttu-id="eae29-120">文字可能略有不同，視執行中的 SDK 版本而定。</span><span class="sxs-lookup"><span data-stu-id="eae29-120">Text may vary slightly depending on the version of the SDK you're running.</span></span> <span data-ttu-id="eae29-121">這個「第一次執行」經驗是 Microsoft 如何通知您有關資料收集。</span><span class="sxs-lookup"><span data-stu-id="eae29-121">This "first run" experience is how Microsoft notifies you about data collection.</span></span>

```console
Telemetry
---------
The .NET Core tools collect usage data in order to help us improve your experience. The data is anonymous. It is collected by Microsoft and shared with the community. You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET Core CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry
```

<span data-ttu-id="eae29-122">若要停用此訊息和 .NET Core 歡迎訊息，請將 `DOTNET_NOLOGO` 環境變數設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="eae29-122">To disable this message and the .NET Core welcome message, set the `DOTNET_NOLOGO` environment variable to `true`.</span></span> <span data-ttu-id="eae29-123">請注意，此變數對遙測選擇不會有任何影響。</span><span class="sxs-lookup"><span data-stu-id="eae29-123">Note that this variable has no effect on telemetry opt out.</span></span>

## <a name="data-points"></a><span data-ttu-id="eae29-124">資料點</span><span class="sxs-lookup"><span data-stu-id="eae29-124">Data points</span></span>

<span data-ttu-id="eae29-125">遙測功能不會收集個人資料，例如使用者名稱或電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="eae29-125">The telemetry feature doesn't collect personal data, such as usernames or email addresses.</span></span> <span data-ttu-id="eae29-126">它不會掃描您的程式碼，也不會擷取專案層級資料，例如名稱、存放庫或作者。</span><span class="sxs-lookup"><span data-stu-id="eae29-126">It doesn't scan your code and doesn't extract project-level data, such as name, repository, or author.</span></span> <span data-ttu-id="eae29-127">資料使用 [Azure 監視器](https://azure.microsoft.com/services/monitor/)技術安全地傳送至 Microsoft 伺服器、在限制存取下保留，並在嚴格安全性控制下從安全的 [Azure 儲存體](https://azure.microsoft.com/services/storage/)系統發佈。</span><span class="sxs-lookup"><span data-stu-id="eae29-127">The data is sent securely to Microsoft servers using [Azure Monitor](https://azure.microsoft.com/services/monitor/) technology, held under restricted access, and published under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

<span data-ttu-id="eae29-128">保護您的隱私權對我們而言很重要。</span><span class="sxs-lookup"><span data-stu-id="eae29-128">Protecting your privacy is important to us.</span></span> <span data-ttu-id="eae29-129">如果您懷疑遙測正在收集敏感性資料，或資料被, 或不當處理，請在[dotnet/sdk](https://github.com/dotnet/sdk/issues)存放庫中提出問題，或傳送電子郵件給 [dotnet@microsoft.com](mailto:dotnet@microsoft.com) 進行調查。</span><span class="sxs-lookup"><span data-stu-id="eae29-129">If you suspect the telemetry is collecting sensitive data or the data is being insecurely or inappropriately handled, file an issue in the [dotnet/sdk](https://github.com/dotnet/sdk/issues) repository or send an email to [dotnet@microsoft.com](mailto:dotnet@microsoft.com) for investigation.</span></span>

<span data-ttu-id="eae29-130">遙測功能會收集下列資料：</span><span class="sxs-lookup"><span data-stu-id="eae29-130">The telemetry feature collects the following data:</span></span>

| <span data-ttu-id="eae29-131">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="eae29-131">SDK versions</span></span> | <span data-ttu-id="eae29-132">資料</span><span class="sxs-lookup"><span data-stu-id="eae29-132">Data</span></span> |
|--------------|------|
| <span data-ttu-id="eae29-133">全部</span><span class="sxs-lookup"><span data-stu-id="eae29-133">All</span></span>          | <span data-ttu-id="eae29-134">叫用的時間戳記。</span><span class="sxs-lookup"><span data-stu-id="eae29-134">Timestamp of invocation.</span></span> |
| <span data-ttu-id="eae29-135">全部</span><span class="sxs-lookup"><span data-stu-id="eae29-135">All</span></span>          | <span data-ttu-id="eae29-136">叫用的命令 (例如 "build")，從 2.1 開始已雜湊。</span><span class="sxs-lookup"><span data-stu-id="eae29-136">Command invoked (for example, "build"), hashed starting in 2.1.</span></span> |
| <span data-ttu-id="eae29-137">全部</span><span class="sxs-lookup"><span data-stu-id="eae29-137">All</span></span>          | <span data-ttu-id="eae29-138">用來判斷地理位置的三個八位元 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="eae29-138">Three octet IP address used to determine the geographical location.</span></span> |
| <span data-ttu-id="eae29-139">全部</span><span class="sxs-lookup"><span data-stu-id="eae29-139">All</span></span>          | <span data-ttu-id="eae29-140">作業系統和版本。</span><span class="sxs-lookup"><span data-stu-id="eae29-140">Operating system and version.</span></span> |
| <span data-ttu-id="eae29-141">全部</span><span class="sxs-lookup"><span data-stu-id="eae29-141">All</span></span>          | <span data-ttu-id="eae29-142">SDK 正在執行的執行階段識別碼 (RID)。</span><span class="sxs-lookup"><span data-stu-id="eae29-142">Runtime ID (RID) the SDK is running on.</span></span> |
| <span data-ttu-id="eae29-143">全部</span><span class="sxs-lookup"><span data-stu-id="eae29-143">All</span></span>          | <span data-ttu-id="eae29-144">.NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="eae29-144">.NET Core SDK version.</span></span> |
| <span data-ttu-id="eae29-145">全部</span><span class="sxs-lookup"><span data-stu-id="eae29-145">All</span></span>          | <span data-ttu-id="eae29-146">遙測設定檔：選擇性值，只能透過明確的使用者加入使用，且只能在 Microsoft 內部使用。</span><span class="sxs-lookup"><span data-stu-id="eae29-146">Telemetry profile: an optional value only used with explicit user opt-in and used internally at Microsoft.</span></span> |
| <span data-ttu-id="eae29-147">>=2.0</span><span class="sxs-lookup"><span data-stu-id="eae29-147">>=2.0</span></span>        | <span data-ttu-id="eae29-148">命令引數和選項：會收集數個引數和選項 (不是任意字串)。</span><span class="sxs-lookup"><span data-stu-id="eae29-148">Command arguments and options: several arguments and options are collected (not arbitrary strings).</span></span> <span data-ttu-id="eae29-149">請參閱[收集的選項](#collected-options)。</span><span class="sxs-lookup"><span data-stu-id="eae29-149">See [collected options](#collected-options).</span></span> <span data-ttu-id="eae29-150">2.1.300 之後已雜湊。</span><span class="sxs-lookup"><span data-stu-id="eae29-150">Hashed after 2.1.300.</span></span> |
| <span data-ttu-id="eae29-151">>=2.0</span><span class="sxs-lookup"><span data-stu-id="eae29-151">>=2.0</span></span>         | <span data-ttu-id="eae29-152">SDK 是否正在容器中執行。</span><span class="sxs-lookup"><span data-stu-id="eae29-152">Whether the SDK is running in a container.</span></span> |
| <span data-ttu-id="eae29-153">>=2.0</span><span class="sxs-lookup"><span data-stu-id="eae29-153">>=2.0</span></span>         | <span data-ttu-id="eae29-154">目標 Framework (來自 `TargetFramework` 事件)，從 2.1 開始已雜湊。</span><span class="sxs-lookup"><span data-stu-id="eae29-154">Target frameworks (from the `TargetFramework` event), hashed starting in 2.1.</span></span> |
| <span data-ttu-id="eae29-155">>=2.0</span><span class="sxs-lookup"><span data-stu-id="eae29-155">>=2.0</span></span>         | <span data-ttu-id="eae29-156">雜湊的媒體存取控制 (MAC) 位址：電腦的密碼編譯 (SHA256) 匿名唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="eae29-156">Hashed Media Access Control (MAC) address: a cryptographically (SHA256) anonymous and unique ID for a machine.</span></span> |
| <span data-ttu-id="eae29-157">>=2.0</span><span class="sxs-lookup"><span data-stu-id="eae29-157">>=2.0</span></span>         | <span data-ttu-id="eae29-158">雜湊的目前工作目錄。</span><span class="sxs-lookup"><span data-stu-id="eae29-158">Hashed current working directory.</span></span> |
| <span data-ttu-id="eae29-159">>=2.0</span><span class="sxs-lookup"><span data-stu-id="eae29-159">>=2.0</span></span>         | <span data-ttu-id="eae29-160">使用雜湊的安裝程式 exe 檔名來安裝成功報告。</span><span class="sxs-lookup"><span data-stu-id="eae29-160">Install success report, with hashed installer exe filename.</span></span> |
| <span data-ttu-id="eae29-161">>=2.1.300</span><span class="sxs-lookup"><span data-stu-id="eae29-161">>=2.1.300</span></span>     | <span data-ttu-id="eae29-162">核心版本。</span><span class="sxs-lookup"><span data-stu-id="eae29-162">Kernel version.</span></span> |
| <span data-ttu-id="eae29-163">>=2.1.300</span><span class="sxs-lookup"><span data-stu-id="eae29-163">>=2.1.300</span></span>     | <span data-ttu-id="eae29-164">Libc 發行/版本。</span><span class="sxs-lookup"><span data-stu-id="eae29-164">Libc release/version.</span></span> |
| <span data-ttu-id="eae29-165">>=3.0.100</span><span class="sxs-lookup"><span data-stu-id="eae29-165">>=3.0.100</span></span>     | <span data-ttu-id="eae29-166">輸出是否已重新導向 (true 或 false)。</span><span class="sxs-lookup"><span data-stu-id="eae29-166">Whether the output was redirected (true or false).</span></span> |
| <span data-ttu-id="eae29-167">>=3.0.100</span><span class="sxs-lookup"><span data-stu-id="eae29-167">>=3.0.100</span></span>     | <span data-ttu-id="eae29-168">CLI/SDK 損毀時的例外狀況類型及其堆疊追蹤 (只有 CLI/SDK 程式碼會包含在傳送的堆疊追蹤中)。</span><span class="sxs-lookup"><span data-stu-id="eae29-168">On a CLI/SDK crash, the exception type and its stack trace (only CLI/SDK code is included in the stack trace sent).</span></span> <span data-ttu-id="eae29-169">如需詳細資訊，請參閱[收集的 .NET Core CLI/SDK 損毀例外狀況遙測](#net-core-clisdk-crash-exception-telemetry-collected)。</span><span class="sxs-lookup"><span data-stu-id="eae29-169">For more information, see [.NET Core CLI/SDK crash exception telemetry collected](#net-core-clisdk-crash-exception-telemetry-collected).</span></span> |

### <a name="collected-options"></a><span data-ttu-id="eae29-170">收集的選項</span><span class="sxs-lookup"><span data-stu-id="eae29-170">Collected options</span></span>

<span data-ttu-id="eae29-171">某些命令會傳送額外的資料。</span><span class="sxs-lookup"><span data-stu-id="eae29-171">Certain commands send additional data.</span></span> <span data-ttu-id="eae29-172">命令的子集會傳送第一個引數：</span><span class="sxs-lookup"><span data-stu-id="eae29-172">A subset of commands sends the first argument:</span></span>

| <span data-ttu-id="eae29-173">命令</span><span class="sxs-lookup"><span data-stu-id="eae29-173">Command</span></span>               | <span data-ttu-id="eae29-174">傳送的第一個引數資料</span><span class="sxs-lookup"><span data-stu-id="eae29-174">First argument data sent</span></span>                |
|-----------------------|-----------------------------------------|
| `dotnet help <arg>`   | <span data-ttu-id="eae29-175">要查詢的命令說明。</span><span class="sxs-lookup"><span data-stu-id="eae29-175">The command help is being queried for.</span></span>  |
| `dotnet new <arg>`    | <span data-ttu-id="eae29-176">範本名稱 (已雜湊)。</span><span class="sxs-lookup"><span data-stu-id="eae29-176">The template name (hashed).</span></span>             |
| `dotnet add <arg>`    | <span data-ttu-id="eae29-177">`package` 或 `reference` 一字。</span><span class="sxs-lookup"><span data-stu-id="eae29-177">The word `package` or `reference`.</span></span>      |
| `dotnet remove <arg>` | <span data-ttu-id="eae29-178">`package` 或 `reference` 一字。</span><span class="sxs-lookup"><span data-stu-id="eae29-178">The word `package` or `reference`.</span></span>      |
| `dotnet list <arg>`   | <span data-ttu-id="eae29-179">`package` 或 `reference` 一字。</span><span class="sxs-lookup"><span data-stu-id="eae29-179">The word `package` or `reference`.</span></span>      |
| `dotnet sln <arg>`    | <span data-ttu-id="eae29-180">`add`、`list` 或 `remove` 一字。</span><span class="sxs-lookup"><span data-stu-id="eae29-180">The word `add`, `list`, or `remove`.</span></span>    |
| `dotnet nuget <arg>`  | <span data-ttu-id="eae29-181">`delete`、`locals` 或 `push` 一字。</span><span class="sxs-lookup"><span data-stu-id="eae29-181">The word `delete`, `locals`, or `push`.</span></span> |

<span data-ttu-id="eae29-182">命令的子集會傳送所選取選項 (如果已使用) 及其值：</span><span class="sxs-lookup"><span data-stu-id="eae29-182">A subset of commands sends selected options if they're used, along with their values:</span></span>

| <span data-ttu-id="eae29-183">選項</span><span class="sxs-lookup"><span data-stu-id="eae29-183">Option</span></span>                  | <span data-ttu-id="eae29-184">命令</span><span class="sxs-lookup"><span data-stu-id="eae29-184">Commands</span></span>                                                                                       |
|-------------------------|------------------------------------------------------------------------------------------------|
| `--verbosity`           | <span data-ttu-id="eae29-185">所有命令</span><span class="sxs-lookup"><span data-stu-id="eae29-185">All commands</span></span>                                                                                   |
| `--language`            | `dotnet new`                                                                                   |
| `--configuration`       | <span data-ttu-id="eae29-186">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`</span><span class="sxs-lookup"><span data-stu-id="eae29-186">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`</span></span>                  |
| `--framework`           | <span data-ttu-id="eae29-187">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`, `dotnet vstest`</span><span class="sxs-lookup"><span data-stu-id="eae29-187">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`, `dotnet vstest`</span></span> |
| `--runtime`             | <span data-ttu-id="eae29-188">`dotnet build`,  `dotnet publish`</span><span class="sxs-lookup"><span data-stu-id="eae29-188">`dotnet build`,  `dotnet publish`</span></span>                                                              |
| `--platform`            | `dotnet vstest`                                                                                |
| `--logger`              | `dotnet vstest`                                                                                |
| `--sdk-package-version` | `dotnet migrate`                                                                               |

<span data-ttu-id="eae29-189">除了 `--verbosity` 和 `--sdk-package-version` 以外，所有其他值都會從 .NET Core 2.1.100 SDK 開始進行雜湊。</span><span class="sxs-lookup"><span data-stu-id="eae29-189">Except for `--verbosity` and `--sdk-package-version`, all the other values are hashed starting with .NET Core 2.1.100 SDK.</span></span>

## <a name="net-core-clisdk-crash-exception-telemetry-collected"></a><span data-ttu-id="eae29-190">收集的 .NET Core CLI/SDK 損毀例外狀況遙測</span><span class="sxs-lookup"><span data-stu-id="eae29-190">.NET Core CLI/SDK crash exception telemetry collected</span></span>

<span data-ttu-id="eae29-191">如果 .NET Core CLI/SDK 損毀，它會收集例外狀況名稱和 CLI/SDK 程式碼的堆疊追蹤。</span><span class="sxs-lookup"><span data-stu-id="eae29-191">If the .NET Core CLI/SDK crashes, it collects the name of the exception and stack trace of the CLI/SDK code.</span></span> <span data-ttu-id="eae29-192">收集這項資訊的目的在於評定問題，並改善 .NET Core SDK 和 CLI 的品質。</span><span class="sxs-lookup"><span data-stu-id="eae29-192">This information is collected to assess problems and improve the quality of the .NET Core SDK and CLI.</span></span> <span data-ttu-id="eae29-193">本文提供我們所收集資料的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="eae29-193">This article provides information about the data we collect.</span></span> <span data-ttu-id="eae29-194">它也提供有關建置自有 .NET Core SDK 版本的使用者如何避免意外洩漏個人或敏感性資訊的祕訣。</span><span class="sxs-lookup"><span data-stu-id="eae29-194">It also provides tips on how users building their own version of the .NET Core SDK can avoid inadvertent disclosure of personal or sensitive information.</span></span>

### <a name="types-of-collected-data"></a><span data-ttu-id="eae29-195">收集的資料類型</span><span class="sxs-lookup"><span data-stu-id="eae29-195">Types of collected data</span></span>

<span data-ttu-id="eae29-196">.NET Core CLI 只會收集 CLI/SDK 例外狀況的資訊，而不會收集您應用程式中的例外狀況資訊。</span><span class="sxs-lookup"><span data-stu-id="eae29-196">.NET Core CLI collects information for CLI/SDK exceptions only, not exceptions in your application.</span></span> <span data-ttu-id="eae29-197">所收集資料包含例外狀況的名稱和堆疊追蹤。</span><span class="sxs-lookup"><span data-stu-id="eae29-197">The collected data contains the name of the exception and the stack trace.</span></span> <span data-ttu-id="eae29-198">此堆疊追蹤是 CLI/SDK 程式碼的堆疊追蹤。</span><span class="sxs-lookup"><span data-stu-id="eae29-198">This stack trace is of CLI/SDK code.</span></span>

<span data-ttu-id="eae29-199">下列範例會顯示所收集的資料類型：</span><span class="sxs-lookup"><span data-stu-id="eae29-199">The following example shows the kind of data that is collected:</span></span>

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

### <a name="avoid-inadvertent-disclosure-of-information"></a><span data-ttu-id="eae29-200">避免意外洩漏資訊</span><span class="sxs-lookup"><span data-stu-id="eae29-200">Avoid inadvertent disclosure of information</span></span>

<span data-ttu-id="eae29-201">.NET Core 參與者及執行其自行建置之 .NET Core SDK 版本的任何其他人，都應該考慮其 SDK 原始程式碼的路徑。</span><span class="sxs-lookup"><span data-stu-id="eae29-201">.NET Core contributors and anyone else running a version of the .NET Core SDK that they built themselves should consider the path to their SDK source code.</span></span> <span data-ttu-id="eae29-202">如果使用 .NET Core SDK 時發生損毀，且該 SDK是自訂偵錯組建或透過自訂組建符號檔所設定，則會在堆疊追蹤過程中從組建電腦收集 SDK 來源檔案路徑，且不會進行雜湊處理。</span><span class="sxs-lookup"><span data-stu-id="eae29-202">If a crash occurs while using a .NET Core SDK that is a custom debug build or configured with custom build symbol files, the SDK source file path from the build machine is collected as part of the stack trace and isn't hashed.</span></span>

<span data-ttu-id="eae29-203">因此，.NET Core SDK 自訂組建不應該位於其路徑名稱會公開個人或敏感性資訊的目錄中。</span><span class="sxs-lookup"><span data-stu-id="eae29-203">Because of this, custom builds of the .NET Core SDK shouldn't be located in directories whose path names expose personal or sensitive information.</span></span>

## <a name="see-also"></a><span data-ttu-id="eae29-204">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eae29-204">See also</span></span>

- <span data-ttu-id="eae29-205">[.NET Core CLI Telemetry - 2019 Q2 Data](https://dotnet.microsoft.com/platform/telemetry/dotnet-core-cli-2019q2) (.NET Core CLI 遙測 - 2019 年第 2 季資料)</span><span class="sxs-lookup"><span data-stu-id="eae29-205">[.NET Core CLI Telemetry - 2019 Q2 Data](https://dotnet.microsoft.com/platform/telemetry/dotnet-core-cli-2019q2)</span></span>
- [<span data-ttu-id="eae29-206">遙測參考來源 (dotnet/sdk 存放庫) </span><span class="sxs-lookup"><span data-stu-id="eae29-206">Telemetry reference source (dotnet/sdk repository)</span></span>](https://github.com/dotnet/sdk/tree/master/src/Cli/dotnet/Telemetry)
