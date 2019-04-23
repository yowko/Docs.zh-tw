---
title: Main() 傳回值 - C# 程式設計指南
ms.custom: seodec18
ms.date: 08/02/2017
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: f515268af13ef95b8b6d9a79f71c49d5d4a98d05
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59149834"
---
# <a name="main-return-values-c-programming-guide"></a><span data-ttu-id="7051f-102">Main() 傳回值 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="7051f-102">Main() return values (C# Programming Guide)</span></span>

<span data-ttu-id="7051f-103">`Main` 方法可以傳回 `void`：</span><span class="sxs-lookup"><span data-stu-id="7051f-103">The `Main` method can return `void`:</span></span>

 [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

<span data-ttu-id="7051f-104">它也可以傳回 `int`：</span><span class="sxs-lookup"><span data-stu-id="7051f-104">It can also return an `int`:</span></span>

 [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

<span data-ttu-id="7051f-105">如果未使用來自 `Main` 的傳回值，則傳回 `void` 可允許使用比較簡單的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7051f-105">If the return value from `Main` is not used, returning `void` allows for slightly simpler code.</span></span> <span data-ttu-id="7051f-106">不過，若是傳回一個整數，可讓程式將狀態資訊傳達給其他會叫用可執行檔的程式或指令碼。</span><span class="sxs-lookup"><span data-stu-id="7051f-106">However, returning an integer enables the program to communicate status information to other programs or scripts that invoke the executable file.</span></span> <span data-ttu-id="7051f-107">從 `Main` 傳回的值會視為處理序的結束代碼。</span><span class="sxs-lookup"><span data-stu-id="7051f-107">The return value from `Main` is treated as the exit code for the process.</span></span> <span data-ttu-id="7051f-108">下列範例示範如何存取來自 `Main` 的傳回值。</span><span class="sxs-lookup"><span data-stu-id="7051f-108">The following example shows how the return value from `Main` can be accessed.</span></span>

## <a name="example"></a><span data-ttu-id="7051f-109">範例</span><span class="sxs-lookup"><span data-stu-id="7051f-109">Example</span></span>

<span data-ttu-id="7051f-110">此範例使用 [.NET Core](../../../core/index.md) 命令列工具。</span><span class="sxs-lookup"><span data-stu-id="7051f-110">This example uses [.NET Core](../../../core/index.md) command line tools.</span></span> <span data-ttu-id="7051f-111">如果您不熟悉 .NET Core 命令列工具，您可以在此[開始使用主題](../../../core/tutorials/using-with-xplat-cli.md)中了解這些工具。</span><span class="sxs-lookup"><span data-stu-id="7051f-111">If you are unfamiliar with .NET Core command line tools, you can learn about them in this [Get started topic](../../../core/tutorials/using-with-xplat-cli.md).</span></span>

<span data-ttu-id="7051f-112">修改 *program.cs* 中的 `Main` 方法，如下所示：</span><span class="sxs-lookup"><span data-stu-id="7051f-112">Modify the `Main` method in *program.cs* as follows:</span></span>

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

<span data-ttu-id="7051f-113">在 Windows 中執行程式時，任何從 `Main` 函式傳回的值，皆會儲存在環境變數中。</span><span class="sxs-lookup"><span data-stu-id="7051f-113">When a program is executed in Windows, any value returned from the `Main` function is stored in an environment variable.</span></span> <span data-ttu-id="7051f-114">您可以從批次檔使用 `ERRORLEVEL` 或從 PowerShell 使用 `$LastExitCode` 來擷取此環境變數。</span><span class="sxs-lookup"><span data-stu-id="7051f-114">This environment variable can be retrieved using `ERRORLEVEL` from a batch file, or `$LastExitCode` from powershell.</span></span>

<span data-ttu-id="7051f-115">您可以使用 [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` 命令來建置應用程式。</span><span class="sxs-lookup"><span data-stu-id="7051f-115">You can build the application using the [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` command.</span></span>

<span data-ttu-id="7051f-116">接下來，建立 PowerShell 指令碼以執行此應用程式，並顯示結果。</span><span class="sxs-lookup"><span data-stu-id="7051f-116">Next, create a Powershell script to run the application and display the result.</span></span> <span data-ttu-id="7051f-117">將下列程式碼貼入文字檔，將它儲存為 `test.ps1`，並放到包含專案的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="7051f-117">Paste the following code into a text file and save it as `test.ps1` in the folder that contains the project.</span></span> <span data-ttu-id="7051f-118">在 PowerShell 命令提示字元中鍵入 `test.ps1`，以執行 PowerShell 指令碼。</span><span class="sxs-lookup"><span data-stu-id="7051f-118">Run the powershell script by typing `test.ps1` at the powershell prompt.</span></span>

<span data-ttu-id="7051f-119">由於程式碼會傳回零，因為批次檔會報告成功。</span><span class="sxs-lookup"><span data-stu-id="7051f-119">Because the code returns zero, the batch file will report success.</span></span> <span data-ttu-id="7051f-120">不過，如果您將 MainReturnValTest.cs 變更為傳回非零值，並重新編譯程式，則 PowerShell 指令碼的後續執行會報告失敗。</span><span class="sxs-lookup"><span data-stu-id="7051f-120">However, if you change MainReturnValTest.cs to return a non-zero value and then re-compile the program, subsequent execution of the powershell script will report failure.</span></span>

```powershell
dotnet run
if ($LastExitCode -eq 0) {
    Write-Host "Execution succeeded"
} else
{
    Write-Host "Execution Failed"
}
Write-Host "Return value = " $LastExitCode
```

## <a name="sample-output"></a><span data-ttu-id="7051f-121">範例輸出</span><span class="sxs-lookup"><span data-stu-id="7051f-121">Sample output</span></span>

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a><span data-ttu-id="7051f-122">Async Main 傳回值</span><span class="sxs-lookup"><span data-stu-id="7051f-122">Async Main return values</span></span>

<span data-ttu-id="7051f-123">Async Main 傳回值會將呼叫 `Main` 中非同步方法所需的未定案程式碼，移至編譯器所產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7051f-123">Async Main return values move the boilerplate code necessary for calling asynchronous methods in `Main` to code generated by the compiler.</span></span> <span data-ttu-id="7051f-124">之前，您需要撰寫此建構以呼叫非同步程式碼，並確保您的程式會執行到非同步作業完成為止：</span><span class="sxs-lookup"><span data-stu-id="7051f-124">Previously, you would need to write this construct to call asynchronous code and ensure your program ran until the asynchronous operation completed:</span></span>

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

<span data-ttu-id="7051f-125">現在，這會取代為：</span><span class="sxs-lookup"><span data-stu-id="7051f-125">Now, this can be replaced by:</span></span>

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

<span data-ttu-id="7051f-126">新語法的優點是編譯器一律會產生正確的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7051f-126">The advantage of the new syntax is that the compiler always generates the correct code.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="7051f-127">編譯器產生的程式碼</span><span class="sxs-lookup"><span data-stu-id="7051f-127">Compiler generated code</span></span>

<span data-ttu-id="7051f-128">當應用程式進入點傳回 `Task` 或 `Task<int>` 時，編譯器會產生新的進入點，以呼叫應用程式程式碼中宣告的進入點方法。</span><span class="sxs-lookup"><span data-stu-id="7051f-128">When the application entry point returns a `Task` or `Task<int>`, the compiler generates a new entry point that calls the entry point method declared in the application code.</span></span> <span data-ttu-id="7051f-129">假設此進入點稱為 `$GeneratedMain`，編譯器會為這些進入點產生下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="7051f-129">Assuming that this entry point is called `$GeneratedMain`, the compiler generates the following code for these entry points:</span></span>

- `static Task Main()` <span data-ttu-id="7051f-130">會導致編譯器發出下列項目的對等項目：</span><span class="sxs-lookup"><span data-stu-id="7051f-130">results in the compiler emitting the equivalent of</span></span> `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task Main(string[])` <span data-ttu-id="7051f-131">會導致編譯器發出下列項目的對等項目：</span><span class="sxs-lookup"><span data-stu-id="7051f-131">results in the compiler emitting the equivalent of</span></span> `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`
- `static Task<int> Main()` <span data-ttu-id="7051f-132">會導致編譯器發出下列項目的對等項目：</span><span class="sxs-lookup"><span data-stu-id="7051f-132">results in the compiler emitting the equivalent of</span></span> `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task<int> Main(string[])` <span data-ttu-id="7051f-133">會導致編譯器發出下列項目的對等項目：</span><span class="sxs-lookup"><span data-stu-id="7051f-133">results in the compiler emitting the equivalent of</span></span> `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`

> [!NOTE]
><span data-ttu-id="7051f-134">如果這些範例在 `Main` 方法上使用 `async` 修飾詞，編譯器會產生相同的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7051f-134">If the examples used `async` modifier on the `Main` method, the compiler would generate the same code.</span></span>

## <a name="see-also"></a><span data-ttu-id="7051f-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7051f-135">See also</span></span>

- [<span data-ttu-id="7051f-136">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="7051f-136">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7051f-137">C# 參考</span><span class="sxs-lookup"><span data-stu-id="7051f-137">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7051f-138">Main() 和命令列引數</span><span class="sxs-lookup"><span data-stu-id="7051f-138">Main() and Command-Line Arguments</span></span>](index.md)
- [<span data-ttu-id="7051f-139">作法：顯示命令列引數</span><span class="sxs-lookup"><span data-stu-id="7051f-139">How to: Display Command Line Arguments</span></span>](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [<span data-ttu-id="7051f-140">作法：使用 foreach 存取命令列引數</span><span class="sxs-lookup"><span data-stu-id="7051f-140">How to: Access Command-Line Arguments Using foreach</span></span>](../../programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)
