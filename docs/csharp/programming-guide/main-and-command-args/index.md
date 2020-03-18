---
title: Main() 和命令列引數 - C# 程式設計指南
ms.date: 08/02/2017
f1_keywords:
- CS5001
- main_CSharpKeyword
- Main
helpviewer_keywords:
- Main method [C#]
- C# language, command-line arguments
- arguments [C#], command-line
- command line [C#], arguments
- command-line arguments [C#], Main method
ms.assetid: 73a17231-cf96-44ea-aa8a-54807c6fb1f4
ms.openlocfilehash: 0571ec6dbc42f103ec922a6b2b13a52510640a78
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "75700597"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a><span data-ttu-id="f80d9-102">Main() 和命令列引數 (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="f80d9-102">Main() and command-line arguments (C# Programming Guide)</span></span>

<span data-ttu-id="f80d9-103">`Main` 方法是 C# 應用程式的進入點。</span><span class="sxs-lookup"><span data-stu-id="f80d9-103">The `Main` method is the entry point of a C# application.</span></span> <span data-ttu-id="f80d9-104">（庫和服務不需要`Main`方法作為進入點。啟動應用程式時，`Main`該方法是調用的第一個方法。</span><span class="sxs-lookup"><span data-stu-id="f80d9-104">(Libraries and services do not require a `Main` method as an entry point.) When the application is started, the `Main` method is the first method that is invoked.</span></span>

 <span data-ttu-id="f80d9-105">C# 程式中只能有一個進入點。</span><span class="sxs-lookup"><span data-stu-id="f80d9-105">There can only be one entry point in a C# program.</span></span> <span data-ttu-id="f80d9-106">如果您具有多個含 `Main` 方法的類別，就必須使用 **/main** 編譯器選項來編譯您的程式，以指定要使用哪一個 `Main` 方法做為進入點。</span><span class="sxs-lookup"><span data-stu-id="f80d9-106">If you have more than one class that has a `Main` method, you must compile your program with the **/main** compiler option to specify which `Main` method to use as the entry point.</span></span> <span data-ttu-id="f80d9-107">有關詳細資訊，請參閱[-main （C# 編譯器選項）](../../language-reference/compiler-options/main-compiler-option.md)。</span><span class="sxs-lookup"><span data-stu-id="f80d9-107">For more information, see [-main (C# Compiler Options)](../../language-reference/compiler-options/main-compiler-option.md).</span></span>

[!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

## <a name="overview"></a><span data-ttu-id="f80d9-108">概觀</span><span class="sxs-lookup"><span data-stu-id="f80d9-108">Overview</span></span>

- <span data-ttu-id="f80d9-109">`Main` 方法是可執行程式的進入點；它是程式控制開始和結束的位置。</span><span class="sxs-lookup"><span data-stu-id="f80d9-109">The `Main` method is the entry point of an executable program; it is where the program control starts and ends.</span></span>
- <span data-ttu-id="f80d9-110">`Main` 會宣告於類別或結構內部。</span><span class="sxs-lookup"><span data-stu-id="f80d9-110">`Main` is declared inside a class or struct.</span></span> <span data-ttu-id="f80d9-111">`Main` 必須是 [static](../../language-reference/keywords/static.md)，但不必是 [public](../../language-reference/keywords/public.md)。</span><span class="sxs-lookup"><span data-stu-id="f80d9-111">`Main` must be [static](../../language-reference/keywords/static.md) and it need not be [public](../../language-reference/keywords/public.md).</span></span> <span data-ttu-id="f80d9-112">（在前面的示例中，它接收[私有](../../language-reference/keywords/private.md)的預設存取權限 。封閉類或結構不一定是靜態的。</span><span class="sxs-lookup"><span data-stu-id="f80d9-112">(In the earlier example, it receives the default access of [private](../../language-reference/keywords/private.md).) The enclosing class or struct is not required to be static.</span></span>
- <span data-ttu-id="f80d9-113">`Main` 的傳回型別可以是 `void`、`int`，或是 `Task`、`Task<int>` (從 C# 7.1 開始)。</span><span class="sxs-lookup"><span data-stu-id="f80d9-113">`Main` can either have a `void`, `int`, or, starting with C# 7.1, `Task`, or `Task<int>` return type.</span></span>
- <span data-ttu-id="f80d9-114">如果 且僅當`Main`返回`Task`或`Task<int>`時，聲明`Main`可以包括[`async`](../../language-reference/keywords/async.md)修飾符。</span><span class="sxs-lookup"><span data-stu-id="f80d9-114">If and only if `Main` returns a `Task` or `Task<int>`, the declaration of `Main` may include the [`async`](../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="f80d9-115">請注意，上列敘述排除了 `async void Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="f80d9-115">Note that this specifically excludes an `async void Main` method.</span></span>
- <span data-ttu-id="f80d9-116">`Main` 方法不一定要使用包含命令列引數的 `string[]` 參數來宣告。</span><span class="sxs-lookup"><span data-stu-id="f80d9-116">The `Main` method can be declared with or without a `string[]` parameter that contains command-line arguments.</span></span> <span data-ttu-id="f80d9-117">使用 Visual Studio 創建 Windows 應用程式時，可以手動添加參數，也可以使用<xref:System.Environment.GetCommandLineArgs>方法獲取[命令列參數](command-line-arguments.md)。</span><span class="sxs-lookup"><span data-stu-id="f80d9-117">When using Visual Studio to create Windows applications, you can add the parameter manually or else use the <xref:System.Environment.GetCommandLineArgs> method to obtain the [command-line arguments](command-line-arguments.md).</span></span> <span data-ttu-id="f80d9-118">參數會讀入來做為以零為基礎的命令列引數。</span><span class="sxs-lookup"><span data-stu-id="f80d9-118">Parameters are read as zero-indexed command-line arguments.</span></span> <span data-ttu-id="f80d9-119">與 C 和 C++不同，程式的名稱不被視為`args`陣列中的第一個命令列參數，但它是<xref:System.Environment.GetCommandLineArgs>方法的第一個元素。</span><span class="sxs-lookup"><span data-stu-id="f80d9-119">Unlike C and C++, the name of the program is not treated as the first command-line argument in the `args` array, but it is the first element of the <xref:System.Environment.GetCommandLineArgs> method.</span></span>

<span data-ttu-id="f80d9-120">以下是有效`Main`簽名的清單：</span><span class="sxs-lookup"><span data-stu-id="f80d9-120">The following is a list of valid `Main` signatures:</span></span>

```csharp
public static void Main() { }
public static int Main() { }
public static void Main(string[] args) { }
public static int Main(string[] args) { }
public static async Task Main() { }
public static async Task<int> Main() { }
public static async Task Main(string[] args) { }
public static async Task<int> Main(string[] args) { }
```

<span data-ttu-id="f80d9-121">當主控台應用程式必須啟動且等待 `Main` 中的 `await` 非同步作業時，新增的 `async` 與 `Task`、`Task<int>` 傳回型別可簡化程式碼。</span><span class="sxs-lookup"><span data-stu-id="f80d9-121">The addition of `async` and `Task`, `Task<int>` return types simplifies program code when console applications need to start and `await` asynchronous operations in `Main`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f80d9-122">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="f80d9-122">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f80d9-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f80d9-123">See also</span></span>

- [<span data-ttu-id="f80d9-124">使用 csc.exe 建置命令列</span><span class="sxs-lookup"><span data-stu-id="f80d9-124">Command-line Building With csc.exe</span></span>](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="f80d9-125">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="f80d9-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f80d9-126">方法</span><span class="sxs-lookup"><span data-stu-id="f80d9-126">Methods</span></span>](../classes-and-structs/methods.md)
- [<span data-ttu-id="f80d9-127">C# 程式內部</span><span class="sxs-lookup"><span data-stu-id="f80d9-127">Inside a C# Program</span></span>](../inside-a-program/index.md)
