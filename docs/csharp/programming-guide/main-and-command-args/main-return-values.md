---
title: Main() 傳回值 - C# 程式設計指南
description: '瞭解主要 ( # A1 傳回值。 請參閱程式碼範例、編譯器產生的程式碼，並查看其他可用的資源。'
ms.date: 08/02/2017
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: c7521f6aef79825a8cc20d5455588a2d684b9ccb
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609599"
---
# <a name="main-return-values-c-programming-guide"></a><span data-ttu-id="91bde-104">Main() 傳回值 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="91bde-104">Main() return values (C# Programming Guide)</span></span>

<span data-ttu-id="91bde-105">`Main` 方法可以傳回 `void`：</span><span class="sxs-lookup"><span data-stu-id="91bde-105">The `Main` method can return `void`:</span></span>

 [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

<span data-ttu-id="91bde-106">它也可以傳回 `int`：</span><span class="sxs-lookup"><span data-stu-id="91bde-106">It can also return an `int`:</span></span>

 [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

<span data-ttu-id="91bde-107">如果未使用來自 `Main` 的傳回值，則傳回 `void` 可允許使用比較簡單的程式碼。</span><span class="sxs-lookup"><span data-stu-id="91bde-107">If the return value from `Main` is not used, returning `void` allows for slightly simpler code.</span></span> <span data-ttu-id="91bde-108">不過，若是傳回一個整數，可讓程式將狀態資訊傳達給其他會叫用可執行檔的程式或指令碼。</span><span class="sxs-lookup"><span data-stu-id="91bde-108">However, returning an integer enables the program to communicate status information to other programs or scripts that invoke the executable file.</span></span> <span data-ttu-id="91bde-109">從 `Main` 傳回的值會視為處理序的結束代碼。</span><span class="sxs-lookup"><span data-stu-id="91bde-109">The return value from `Main` is treated as the exit code for the process.</span></span> <span data-ttu-id="91bde-110">如果 `void` 從傳回 `Main` ，則結束代碼將會隱含 `0` 。</span><span class="sxs-lookup"><span data-stu-id="91bde-110">If `void` is returned from `Main`, the exit code will be implicitly `0`.</span></span> <span data-ttu-id="91bde-111">下列範例示範如何存取來自 `Main` 的傳回值。</span><span class="sxs-lookup"><span data-stu-id="91bde-111">The following example shows how the return value from `Main` can be accessed.</span></span>

## <a name="example"></a><span data-ttu-id="91bde-112">範例</span><span class="sxs-lookup"><span data-stu-id="91bde-112">Example</span></span>

<span data-ttu-id="91bde-113">此範例使用 [.Net Core](../../../core/introduction.md) 命令列工具。</span><span class="sxs-lookup"><span data-stu-id="91bde-113">This example uses [.NET Core](../../../core/introduction.md) command-line tools.</span></span> <span data-ttu-id="91bde-114">如果您不熟悉 .NET Core 命令列工具，您可以在這 [篇入門文章](../../../core/tutorials/with-visual-studio-code.md)中瞭解這些工具。</span><span class="sxs-lookup"><span data-stu-id="91bde-114">If you are unfamiliar with .NET Core command-line tools, you can learn about them in this [get-started article](../../../core/tutorials/with-visual-studio-code.md).</span></span>

<span data-ttu-id="91bde-115">修改 *program.cs* 中的 `Main` 方法，如下所示：</span><span class="sxs-lookup"><span data-stu-id="91bde-115">Modify the `Main` method in *program.cs* as follows:</span></span>

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

<span data-ttu-id="91bde-116">在 Windows 中執行程式時，任何從 `Main` 函式傳回的值，皆會儲存在環境變數中。</span><span class="sxs-lookup"><span data-stu-id="91bde-116">When a program is executed in Windows, any value returned from the `Main` function is stored in an environment variable.</span></span> <span data-ttu-id="91bde-117">您可以 `ERRORLEVEL` 從批次檔或從 PowerShell 抓取這個環境變數 `$LastExitCode` 。</span><span class="sxs-lookup"><span data-stu-id="91bde-117">This environment variable can be retrieved using `ERRORLEVEL` from a batch file, or `$LastExitCode` from PowerShell.</span></span>

<span data-ttu-id="91bde-118">您可以使用 [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` 命令來建置應用程式。</span><span class="sxs-lookup"><span data-stu-id="91bde-118">You can build the application using the [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` command.</span></span>

<span data-ttu-id="91bde-119">接下來，建立 PowerShell 腳本來執行應用程式並顯示結果。</span><span class="sxs-lookup"><span data-stu-id="91bde-119">Next, create a PowerShell script to run the application and display the result.</span></span> <span data-ttu-id="91bde-120">將下列程式碼貼入文字檔，將它儲存為 `test.ps1`，並放到包含專案的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="91bde-120">Paste the following code into a text file and save it as `test.ps1` in the folder that contains the project.</span></span> <span data-ttu-id="91bde-121">在 PowerShell 提示字元中輸入，以執行 PowerShell 腳本 `test.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="91bde-121">Run the PowerShell script by typing `test.ps1` at the PowerShell prompt.</span></span>

<span data-ttu-id="91bde-122">由於程式碼會傳回零，因為批次檔會報告成功。</span><span class="sxs-lookup"><span data-stu-id="91bde-122">Because the code returns zero, the batch file will report success.</span></span> <span data-ttu-id="91bde-123">但是，如果您將 MainReturnValTest.cs 變更為傳回非零值，然後重新編譯程式，則 PowerShell 腳本的後續執行將會報告失敗。</span><span class="sxs-lookup"><span data-stu-id="91bde-123">However, if you change MainReturnValTest.cs to return a non-zero value and then recompile the program, subsequent execution of the PowerShell script will report failure.</span></span>

```dotnetcli
dotnet run
```

```powershell
if ($LastExitCode -eq 0) {
    Write-Host "Execution succeeded"
} else
{
    Write-Host "Execution Failed"
}
Write-Host "Return value = " $LastExitCode
```

## <a name="sample-output"></a><span data-ttu-id="91bde-124">範例輸出</span><span class="sxs-lookup"><span data-stu-id="91bde-124">Sample output</span></span>

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a><span data-ttu-id="91bde-125">Async Main 傳回值</span><span class="sxs-lookup"><span data-stu-id="91bde-125">Async Main return values</span></span>

<span data-ttu-id="91bde-126">Async Main 傳回值會將呼叫 `Main` 中非同步方法所需的未定案程式碼，移至編譯器所產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="91bde-126">Async Main return values move the boilerplate code necessary for calling asynchronous methods in `Main` to code generated by the compiler.</span></span> <span data-ttu-id="91bde-127">之前，您需要撰寫此建構以呼叫非同步程式碼，並確保您的程式會執行到非同步作業完成為止：</span><span class="sxs-lookup"><span data-stu-id="91bde-127">Previously, you would need to write this construct to call asynchronous code and ensure your program ran until the asynchronous operation completed:</span></span>

```csharp
public static void Main()
{
    AsyncConsoleWork().GetAwaiter().GetResult();
}

private static async Task<int> AsyncConsoleWork()
{
    // Main body here
    return 0;
}
```

<span data-ttu-id="91bde-128">現在，這會取代為：</span><span class="sxs-lookup"><span data-stu-id="91bde-128">Now, this can be replaced by:</span></span>

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

<span data-ttu-id="91bde-129">新語法的優點是編譯器一律會產生正確的程式碼。</span><span class="sxs-lookup"><span data-stu-id="91bde-129">The advantage of the new syntax is that the compiler always generates the correct code.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="91bde-130">編譯器產生的程式碼</span><span class="sxs-lookup"><span data-stu-id="91bde-130">Compiler-generated code</span></span>

<span data-ttu-id="91bde-131">當應用程式進入點傳回 `Task` 或 `Task<int>` 時，編譯器會產生新的進入點，以呼叫應用程式程式碼中宣告的進入點方法。</span><span class="sxs-lookup"><span data-stu-id="91bde-131">When the application entry point returns a `Task` or `Task<int>`, the compiler generates a new entry point that calls the entry point method declared in the application code.</span></span> <span data-ttu-id="91bde-132">假設此進入點稱為 `$GeneratedMain`，編譯器會為這些進入點產生下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="91bde-132">Assuming that this entry point is called `$GeneratedMain`, the compiler generates the following code for these entry points:</span></span>

- <span data-ttu-id="91bde-133">`static Task Main()` 會導致編譯器發出 `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();` 的對等項目</span><span class="sxs-lookup"><span data-stu-id="91bde-133">`static Task Main()` results in the compiler emitting the equivalent of `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="91bde-134">`static Task Main(string[])` 會導致編譯器發出 `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();` 的對等項目</span><span class="sxs-lookup"><span data-stu-id="91bde-134">`static Task Main(string[])` results in the compiler emitting the equivalent of `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="91bde-135">`static Task<int> Main()` 會導致編譯器發出 `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();` 的對等項目</span><span class="sxs-lookup"><span data-stu-id="91bde-135">`static Task<int> Main()` results in the compiler emitting the equivalent of `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="91bde-136">`static Task<int> Main(string[])` 會導致編譯器發出 `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();` 的對等項目</span><span class="sxs-lookup"><span data-stu-id="91bde-136">`static Task<int> Main(string[])` results in the compiler emitting the equivalent of `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>

> [!NOTE]
><span data-ttu-id="91bde-137">如果這些範例在 `Main` 方法上使用 `async` 修飾詞，編譯器會產生相同的程式碼。</span><span class="sxs-lookup"><span data-stu-id="91bde-137">If the examples used `async` modifier on the `Main` method, the compiler would generate the same code.</span></span>

## <a name="see-also"></a><span data-ttu-id="91bde-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91bde-138">See also</span></span>

- [<span data-ttu-id="91bde-139">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="91bde-139">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="91bde-140">C # 參考</span><span class="sxs-lookup"><span data-stu-id="91bde-140">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="91bde-141">主要 ( # A1 和命令列引數</span><span class="sxs-lookup"><span data-stu-id="91bde-141">Main() and Command-Line Arguments</span></span>](index.md)
- [<span data-ttu-id="91bde-142">如何顯示命令列引數</span><span class="sxs-lookup"><span data-stu-id="91bde-142">How to display command line arguments</span></span>](./how-to-display-command-line-arguments.md)
