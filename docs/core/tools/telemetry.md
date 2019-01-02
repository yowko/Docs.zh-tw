---
title: .NET Core SDK 遙測
description: 探索收集使用量資訊以進行分析的 .NET Core SDK 遙測功能，它會收集哪些資料以及如何停用。
author: richlander
ms.date: 06/20/2018
ms.custom: seodec18
ms.openlocfilehash: 8b0b546d70eab837c2e075f839990870ae9ea6b1
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53168841"
---
# <a name="net-core-sdk-telemetry"></a><span data-ttu-id="a88ed-103">.NET Core SDK 遙測</span><span class="sxs-lookup"><span data-stu-id="a88ed-103">.NET Core SDK telemetry</span></span>

<span data-ttu-id="a88ed-104">[.NET Core SDK](index.md) 包含收集使用資訊的[遙測功能](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry)。</span><span class="sxs-lookup"><span data-stu-id="a88ed-104">The [.NET Core SDK](index.md) includes a [telemetry feature](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry) that collects usage information.</span></span> <span data-ttu-id="a88ed-105">.NET 小組必須了解使用者如何使用這些工具，以便進行改善。</span><span class="sxs-lookup"><span data-stu-id="a88ed-105">It's important that the .NET Team understands how the tools are used so they can be improved.</span></span> <span data-ttu-id="a88ed-106">如需詳細資訊，請參閱 [What we've learned from .NET Core SDK Telemetry](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/) (我們從 .NET Core SDK 遙測學到什麼)。</span><span class="sxs-lookup"><span data-stu-id="a88ed-106">For more information, see [What we've learned from .NET Core SDK Telemetry](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/).</span></span>

<span data-ttu-id="a88ed-107">所收集的資料是匿名的，而且將會以彙總形式發行，供 Microsoft 和社群工程師根據 [Creative Commons Attribution 授權](https://creativecommons.org/licenses/by/4.0/)使用。</span><span class="sxs-lookup"><span data-stu-id="a88ed-107">The collected data is anonymous and published in an aggregated form for use by both Microsoft and the community under the [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span></span>

## <a name="scope"></a><span data-ttu-id="a88ed-108">範圍</span><span class="sxs-lookup"><span data-stu-id="a88ed-108">Scope</span></span>

<span data-ttu-id="a88ed-109">`dotnet` 命令用來啟動應用程式和 .NET Core CLI。</span><span class="sxs-lookup"><span data-stu-id="a88ed-109">The `dotnet` command is used to launch both apps and the .NET Core CLI.</span></span> <span data-ttu-id="a88ed-110">`dotnet` 命令本身不會收集遙測。</span><span class="sxs-lookup"><span data-stu-id="a88ed-110">The `dotnet` command itself doesn't collect telemetry.</span></span> <span data-ttu-id="a88ed-111">`dotnet` 命令執行的 .NET Core CLI 命令會收集遙測。</span><span class="sxs-lookup"><span data-stu-id="a88ed-111">The .NET Core CLI commands run by the `dotnet` command collect the telemetry.</span></span>

<span data-ttu-id="a88ed-112">使用 `dotnet` 命令本身，沒有任何附加命令時，「不啟用」遙測：</span><span class="sxs-lookup"><span data-stu-id="a88ed-112">Telemetry *isn't enabled* when using the `dotnet` command itself, with no command attached:</span></span>

- `dotnet`
- `dotnet [path-to-app]`

<span data-ttu-id="a88ed-113">使用 [.NET Core CLI 命令](index.md) 時會「啟用」遙測，例如：</span><span class="sxs-lookup"><span data-stu-id="a88ed-113">Telemetry *is enabled* when using the [.NET Core CLI commands](index.md), such as:</span></span>

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`

## <a name="how-to-opt-out"></a><span data-ttu-id="a88ed-114">如何選擇退出</span><span class="sxs-lookup"><span data-stu-id="a88ed-114">How to opt out</span></span>

<span data-ttu-id="a88ed-115">預設會啟用 .NET Core SDK 遙測功能。</span><span class="sxs-lookup"><span data-stu-id="a88ed-115">The .NET Core SDK telemetry feature is enabled by default.</span></span> <span data-ttu-id="a88ed-116">將 `DOTNET_CLI_TELEMETRY_OPTOUT` 環境變數設成 `1` 或 `true`，選擇退出遙測功能。</span><span class="sxs-lookup"><span data-stu-id="a88ed-116">Opt out of the telemetry feature by setting the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span>

## <a name="data-points"></a><span data-ttu-id="a88ed-117">資料點</span><span class="sxs-lookup"><span data-stu-id="a88ed-117">Data points</span></span>

<span data-ttu-id="a88ed-118">這個功能會收集下列資料︰</span><span class="sxs-lookup"><span data-stu-id="a88ed-118">The feature collects the following data:</span></span>

- <span data-ttu-id="a88ed-119">叫用時間戳記&#8224;</span><span class="sxs-lookup"><span data-stu-id="a88ed-119">Timestamp of invocation&#8224;</span></span>
- <span data-ttu-id="a88ed-120">已叫用的命令 (例如 "build")&#8224;</span><span class="sxs-lookup"><span data-stu-id="a88ed-120">Command invoked (for example, "build")&#8224;</span></span>
- <span data-ttu-id="a88ed-121">用來判斷地理位置的三個八位元 IP 位址&#8224;</span><span class="sxs-lookup"><span data-stu-id="a88ed-121">Three octet IP address used to determine geographical location&#8224;</span></span>
- <span data-ttu-id="a88ed-122">命令的 `ExitCode`</span><span class="sxs-lookup"><span data-stu-id="a88ed-122">`ExitCode` of the command</span></span>
- <span data-ttu-id="a88ed-123">測試執行器 (用於測試專案)</span><span class="sxs-lookup"><span data-stu-id="a88ed-123">Test runner (for test projects)</span></span>
- <span data-ttu-id="a88ed-124">作業系統和版本&#8224;</span><span class="sxs-lookup"><span data-stu-id="a88ed-124">Operating system and version&#8224;</span></span>
- <span data-ttu-id="a88ed-125">執行階段識別碼是否存在於 "runtimes" 節點中</span><span class="sxs-lookup"><span data-stu-id="a88ed-125">Whether runtime IDs are present in the runtimes node</span></span>
- <span data-ttu-id="a88ed-126">.NET Core SDK 版本&#8224;</span><span class="sxs-lookup"><span data-stu-id="a88ed-126">.NET Core SDK version&#8224;</span></span>

<span data-ttu-id="a88ed-127">&#8224;此計量已發行。</span><span class="sxs-lookup"><span data-stu-id="a88ed-127">&#8224;This metric is published.</span></span>

<span data-ttu-id="a88ed-128">從 .NET Core 2.0 SDK 開始，會收集新的資料點：</span><span class="sxs-lookup"><span data-stu-id="a88ed-128">Starting with .NET Core 2.0 SDK, new data points are collected:</span></span>

- <span data-ttu-id="a88ed-129">`dotnet` 命令引數和選項：只收集已知的引數和選項 (不是任意字串)。</span><span class="sxs-lookup"><span data-stu-id="a88ed-129">`dotnet` command arguments and options: only known arguments and options are collected (not arbitrary strings).</span></span>
- <span data-ttu-id="a88ed-130">SDK 是否正在容器中執行。</span><span class="sxs-lookup"><span data-stu-id="a88ed-130">Whether the SDK is running in a container.</span></span>
- <span data-ttu-id="a88ed-131">目標 Framework。</span><span class="sxs-lookup"><span data-stu-id="a88ed-131">Target frameworks.</span></span>
- <span data-ttu-id="a88ed-132">雜湊 MAC 位址：機器以密碼編譯 (SHA256) 的匿名和唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="a88ed-132">Hashed MAC address: a cryptographically (SHA256) anonymous and unique ID for a machine.</span></span> <span data-ttu-id="a88ed-133">此計量未發行。</span><span class="sxs-lookup"><span data-stu-id="a88ed-133">This metric isn't published.</span></span>
- <span data-ttu-id="a88ed-134">雜湊的目前工作目錄。</span><span class="sxs-lookup"><span data-stu-id="a88ed-134">Hashed current working directory.</span></span>

<span data-ttu-id="a88ed-135">這個功能不收集個人資料，例如使用者名稱或電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="a88ed-135">The feature doesn't collect personal data, such as usernames or email addresses.</span></span> <span data-ttu-id="a88ed-136">它不會掃描您的程式碼，也不會擷取機密的專案層級資料，例如名稱、存放庫或作者。</span><span class="sxs-lookup"><span data-stu-id="a88ed-136">It doesn't scan your code and doesn't extract sensitive project-level data, such as name, repo, or author.</span></span> <span data-ttu-id="a88ed-137">資料會使用 [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) 技術安全傳送至 Microsoft 伺服器、保留在限制存取權下，以及以安全的 [Azure 儲存體](https://azure.microsoft.com/services/storage/)系統的嚴格安全性控制項發佈。</span><span class="sxs-lookup"><span data-stu-id="a88ed-137">The data is sent securely to Microsoft servers using [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technology, held under restricted access, and published under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

<span data-ttu-id="a88ed-138">.NET 小組想要知道您如何使用工具，以及它們是不是好用，而不是您使用這些工具來建置什麼。</span><span class="sxs-lookup"><span data-stu-id="a88ed-138">The .NET team wants to know how the tools are used and if they're working well, not what you're building with the tools.</span></span> <span data-ttu-id="a88ed-139">如果您懷疑遙測收集敏感性資料或資料處理的方式不安全或不適當，請在 [dotnet/cli](https://github.com/dotnet/cli/issues) 存放庫中提出問題以進行調查。</span><span class="sxs-lookup"><span data-stu-id="a88ed-139">If you suspect that the telemetry is collecting sensitive data or that the data is being insecurely or inappropriately handled, file an issue in the [dotnet/cli](https://github.com/dotnet/cli/issues) repository for investigation.</span></span>

## <a name="published-data"></a><span data-ttu-id="a88ed-140">發行資料</span><span class="sxs-lookup"><span data-stu-id="a88ed-140">Published data</span></span>

<span data-ttu-id="a88ed-141">發行為每季提供，並列於 [.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md) (.NET Core SDK 使用方式資料)。</span><span class="sxs-lookup"><span data-stu-id="a88ed-141">Published data is available quarterly and are listed at [.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md).</span></span> <span data-ttu-id="a88ed-142">資料檔的資料行包括：</span><span class="sxs-lookup"><span data-stu-id="a88ed-142">The columns of a data file are:</span></span>

- <span data-ttu-id="a88ed-143">時間戳記</span><span class="sxs-lookup"><span data-stu-id="a88ed-143">Timestamp</span></span>
- <span data-ttu-id="a88ed-144">發生次數&#8224;</span><span class="sxs-lookup"><span data-stu-id="a88ed-144">Occurrences&#8224;</span></span>
- <span data-ttu-id="a88ed-145">命令</span><span class="sxs-lookup"><span data-stu-id="a88ed-145">Command</span></span>
- <span data-ttu-id="a88ed-146">地理位置&#8225;</span><span class="sxs-lookup"><span data-stu-id="a88ed-146">Geography&#8225;</span></span>
- <span data-ttu-id="a88ed-147">OSFamily</span><span class="sxs-lookup"><span data-stu-id="a88ed-147">OSFamily</span></span>
- <span data-ttu-id="a88ed-148">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="a88ed-148">RuntimeID</span></span>
- <span data-ttu-id="a88ed-149">OSVersion</span><span class="sxs-lookup"><span data-stu-id="a88ed-149">OSVersion</span></span>
- <span data-ttu-id="a88ed-150">SDKVersion</span><span class="sxs-lookup"><span data-stu-id="a88ed-150">SDKVersion</span></span>

<span data-ttu-id="a88ed-151">&#8224;「發生次數」資料行顯示該命令該日用於該資料列計量的彙總計數。</span><span class="sxs-lookup"><span data-stu-id="a88ed-151">&#8224;The *Occurrences* column displays the aggregate count of that command's use for that row's metrics that day.</span></span>

<span data-ttu-id="a88ed-152">&#8225;一般而言，「地理位置」資料行會顯示國家/地區的名稱。</span><span class="sxs-lookup"><span data-stu-id="a88ed-152">&#8225;Typically, the *Geography* column displays the name of a country.</span></span> <span data-ttu-id="a88ed-153">在某些情況下，南極大陸會出現在這個資料行，因為研究人員在南極大陸使用 .NET Core 或不正確的位置資料。</span><span class="sxs-lookup"><span data-stu-id="a88ed-153">In some cases, the continent of Antarctica appears in this column, either due to researchers using .NET Core in Antarctica or incorrect location data.</span></span>

### <a name="example"></a><span data-ttu-id="a88ed-154">範例</span><span class="sxs-lookup"><span data-stu-id="a88ed-154">Example</span></span>

| <span data-ttu-id="a88ed-155">時間戳記</span><span class="sxs-lookup"><span data-stu-id="a88ed-155">Timestamp</span></span>      | <span data-ttu-id="a88ed-156">發生次數</span><span class="sxs-lookup"><span data-stu-id="a88ed-156">Occurrences</span></span> | <span data-ttu-id="a88ed-157">命令</span><span class="sxs-lookup"><span data-stu-id="a88ed-157">Command</span></span> | <span data-ttu-id="a88ed-158">地理位置</span><span class="sxs-lookup"><span data-stu-id="a88ed-158">Geography</span></span> | <span data-ttu-id="a88ed-159">OSFamily</span><span class="sxs-lookup"><span data-stu-id="a88ed-159">OSFamily</span></span> | <span data-ttu-id="a88ed-160">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="a88ed-160">RuntimeID</span></span>     | <span data-ttu-id="a88ed-161">OSVersion</span><span class="sxs-lookup"><span data-stu-id="a88ed-161">OSVersion</span></span> | <span data-ttu-id="a88ed-162">SDKVersion</span><span class="sxs-lookup"><span data-stu-id="a88ed-162">SDKVersion</span></span> |
| -------------- | ----------- | ------- | --------- | -------- | ------------- | --------- | ---------- |
| <span data-ttu-id="a88ed-163">4/16/2017 0:00</span><span class="sxs-lookup"><span data-stu-id="a88ed-163">4/16/2017 0:00</span></span> | <span data-ttu-id="a88ed-164">8</span><span class="sxs-lookup"><span data-stu-id="a88ed-164">8</span></span>           | <span data-ttu-id="a88ed-165">回合</span><span class="sxs-lookup"><span data-stu-id="a88ed-165">run</span></span>     | <span data-ttu-id="a88ed-166">烏干達</span><span class="sxs-lookup"><span data-stu-id="a88ed-166">Uganda</span></span>    | <span data-ttu-id="a88ed-167">達爾文</span><span class="sxs-lookup"><span data-stu-id="a88ed-167">Darwin</span></span>   | <span data-ttu-id="a88ed-168">osx.10.12-x64</span><span class="sxs-lookup"><span data-stu-id="a88ed-168">osx.10.12-x64</span></span> | <span data-ttu-id="a88ed-169">10.12</span><span class="sxs-lookup"><span data-stu-id="a88ed-169">10.12</span></span>     | <span data-ttu-id="a88ed-170">1.0.1</span><span class="sxs-lookup"><span data-stu-id="a88ed-170">1.0.1</span></span>      |

### <a name="datasets"></a><span data-ttu-id="a88ed-171">資料集</span><span class="sxs-lookup"><span data-stu-id="a88ed-171">Datasets</span></span>

[<span data-ttu-id="a88ed-172">2016 - Q3</span><span class="sxs-lookup"><span data-stu-id="a88ed-172">2016 - Q3</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q3.tsv)  
[<span data-ttu-id="a88ed-173">2016 - Q4</span><span class="sxs-lookup"><span data-stu-id="a88ed-173">2016 - Q4</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q4.tsv)  
[<span data-ttu-id="a88ed-174">2017 - Q1</span><span class="sxs-lookup"><span data-stu-id="a88ed-174">2017 - Q1</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q1.tsv)  
[<span data-ttu-id="a88ed-175">2017 - Q2</span><span class="sxs-lookup"><span data-stu-id="a88ed-175">2017 - Q2</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q2.tsv)  
[<span data-ttu-id="a88ed-176">2017 - Q3</span><span class="sxs-lookup"><span data-stu-id="a88ed-176">2017 - Q3</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q3.tsv)  
[<span data-ttu-id="a88ed-177">2017 - Q4</span><span class="sxs-lookup"><span data-stu-id="a88ed-177">2017 - Q4</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q4.tsv)  

<span data-ttu-id="a88ed-178">使用標準的 URL 格式張貼額外的資料集。</span><span class="sxs-lookup"><span data-stu-id="a88ed-178">Additional datasets are posted using a standard URL format.</span></span> <span data-ttu-id="a88ed-179">以年取代 `<YEAR>`，以一年的季取代 `<QUARTER>` (使用 `1`、`2`、`3` 或 `4`)。</span><span class="sxs-lookup"><span data-stu-id="a88ed-179">Replace `<YEAR>` with the year and replace `<QUARTER>` with the quarter of the year (use `1`, `2`, `3`, or `4`).</span></span> <span data-ttu-id="a88ed-180">這些檔案使用定位字元分隔值 (*TSV*) 格式。</span><span class="sxs-lookup"><span data-stu-id="a88ed-180">The files are in tab-separated values (*TSV*) format.</span></span>

`https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-<YEAR>-q<QUARTER>.tsv`

## <a name="license"></a><span data-ttu-id="a88ed-181">使用權</span><span class="sxs-lookup"><span data-stu-id="a88ed-181">License</span></span>

<span data-ttu-id="a88ed-182">Microsoft 的 .NET Core 散發是使用 [MICROSOFT .NET LIBRARY EULA](https://aka.ms/dotnet-core-eula) 所授權。</span><span class="sxs-lookup"><span data-stu-id="a88ed-182">The Microsoft distribution of .NET Core is licensed with the [MICROSOFT .NET LIBRARY EULA](https://aka.ms/dotnet-core-eula).</span></span> <span data-ttu-id="a88ed-183">此授權包含 "DATA" 區段以啟用遙測 (如下所示)。</span><span class="sxs-lookup"><span data-stu-id="a88ed-183">This license includes the "DATA" section to enable telemetry (shown below).</span></span>

<span data-ttu-id="a88ed-184">[.NET NuGet 套件](https://www.nuget.org/profiles/dotnetframework)使用相同的授權，但不啟用遙測 (請參閱[範圍](#scope))。</span><span class="sxs-lookup"><span data-stu-id="a88ed-184">[.NET NuGet packages](https://www.nuget.org/profiles/dotnetframework) use the same license but don't enable telemetry (see [Scope](#scope)).</span></span>

> 2. <span data-ttu-id="a88ed-185">資料。</span><span class="sxs-lookup"><span data-stu-id="a88ed-185">DATA.</span></span> <span data-ttu-id="a88ed-186">軟體可能會收集和您及您使用軟體之方式有關的資訊，並將該資訊傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="a88ed-186">The software may collect information about you and your use of the software, and send that to Microsoft.</span></span> <span data-ttu-id="a88ed-187">Microsoft 可能會使用此資訊以改善產品與服務。</span><span class="sxs-lookup"><span data-stu-id="a88ed-187">Microsoft may use this information to improve our products and services.</span></span> <span data-ttu-id="a88ed-188">您可以前往 <http://go.microsoft.com/fwlink/?LinkId=528096>，以在說明文件及隱私權聲明中深入了解資料收集和使用方式的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a88ed-188">You can learn more about data collection and use in the help documentation and the privacy statement at <http://go.microsoft.com/fwlink/?LinkId=528096>.</span></span> <span data-ttu-id="a88ed-189">使用軟體即代表您同意這些做法。</span><span class="sxs-lookup"><span data-stu-id="a88ed-189">Your use of the software operates as your consent to these practices.</span></span>

## <a name="disclosure"></a><span data-ttu-id="a88ed-190">公開</span><span class="sxs-lookup"><span data-stu-id="a88ed-190">Disclosure</span></span>

<span data-ttu-id="a88ed-191">.NET Core SDK 會在您第一次執行其中一個 [.NET Core CLI 命令](index.md)時 (例如 `dotnet restore`)，顯示下列文字。</span><span class="sxs-lookup"><span data-stu-id="a88ed-191">The .NET Core SDK displays the following text when you first run one of the [.NET Core CLI commands](index.md) (for example, `dotnet restore`).</span></span> <span data-ttu-id="a88ed-192">文字可能略有不同，視執行中的 SDK 版本而定。</span><span class="sxs-lookup"><span data-stu-id="a88ed-192">Text may vary slightly depending on the version of the SDK you're running.</span></span> <span data-ttu-id="a88ed-193">這個「第一次執行」經驗是 Microsoft 如何通知您有關資料收集。</span><span class="sxs-lookup"><span data-stu-id="a88ed-193">This "first run" experience is how Microsoft notifies you about data collection.</span></span>

```console
Welcome to .NET Core!
---------------------
Learn more about .NET Core: https://aka.ms/dotnet-docs
Use 'dotnet --help' to see available commands or visit: https://aka.ms/dotnet-cli-docs

Telemetry
---------
The .NET Core tools collect usage data in order to help us improve your experience.
The data is anonymous and doesn't include command-line arguments.
The data is collected by Microsoft and shared with the community.
You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET Core CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry
```

## <a name="see-also"></a><span data-ttu-id="a88ed-194">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a88ed-194">See also</span></span>

- <span data-ttu-id="a88ed-195">[What we've learned from .NET Core SDK Telemetry](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/) (我們從 .NET Core SDK 遙測學到什麼)</span><span class="sxs-lookup"><span data-stu-id="a88ed-195">[What we've learned from .NET Core SDK Telemetry](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/)</span></span>
- <span data-ttu-id="a88ed-196">[Telemetry reference source (dotnet/cli repo)](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry) (遙測參考來源 (dotnet/cli 存放庫)</span><span class="sxs-lookup"><span data-stu-id="a88ed-196">[Telemetry reference source (dotnet/cli repo)](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry)</span></span>
- <span data-ttu-id="a88ed-197">[.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md) (.NET Core SDK 使用方式資料)</span><span class="sxs-lookup"><span data-stu-id="a88ed-197">[.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md)</span></span>
