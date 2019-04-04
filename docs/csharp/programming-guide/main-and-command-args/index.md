---
title: Main() 和命令列引數 - C# 程式設計指南
ms.custom: seodec18
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
ms.openlocfilehash: f1cbbc6081c0e2f3e29d49f413e00c7346ea7e60
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968994"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a><span data-ttu-id="2050e-102">Main() 和命令列引數 (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="2050e-102">Main() and command-line arguments (C# Programming Guide)</span></span>

<span data-ttu-id="2050e-103">`Main` 方法是 C# 應用程式的進入點。</span><span class="sxs-lookup"><span data-stu-id="2050e-103">The `Main` method is the entry point of a C# application.</span></span> <span data-ttu-id="2050e-104">(程式庫和服務不需要使用 `Main` 方法做為進入點)。啟動應用程式時，`Main` 方法是第一個叫用的方法。</span><span class="sxs-lookup"><span data-stu-id="2050e-104">(Libraries and services do not require a `Main` method as an entry point.) When the application is started, the `Main` method is the first method that is invoked.</span></span>

 <span data-ttu-id="2050e-105">C# 程式中只能有一個進入點。</span><span class="sxs-lookup"><span data-stu-id="2050e-105">There can only be one entry point in a C# program.</span></span> <span data-ttu-id="2050e-106">如果您具有多個含 `Main` 方法的類別，就必須使用 **/main** 編譯器選項來編譯您的程式，以指定要使用哪一個 `Main` 方法做為進入點。</span><span class="sxs-lookup"><span data-stu-id="2050e-106">If you have more than one class that has a `Main` method, you must compile your program with the **/main** compiler option to specify which `Main` method to use as the entry point.</span></span> <span data-ttu-id="2050e-107">如需詳細資訊，請參閱 [/main (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/main-compiler-option.md)。</span><span class="sxs-lookup"><span data-stu-id="2050e-107">For more information, see [/main (C# Compiler Options)](../../../csharp/language-reference/compiler-options/main-compiler-option.md).</span></span>

 [!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

## <a name="overview"></a><span data-ttu-id="2050e-108">總覽</span><span class="sxs-lookup"><span data-stu-id="2050e-108">Overview</span></span>

- <span data-ttu-id="2050e-109">`Main` 方法是可執行程式的進入點；它是程式控制開始和結束的位置。</span><span class="sxs-lookup"><span data-stu-id="2050e-109">The `Main` method is the entry point of an executable program; it is where the program control starts and ends.</span></span>
- <span data-ttu-id="2050e-110">`Main` 會宣告於類別或結構內部。</span><span class="sxs-lookup"><span data-stu-id="2050e-110">`Main` is declared inside a class or struct.</span></span> <span data-ttu-id="2050e-111">`Main` 必須是 [static](../../../csharp/language-reference/keywords/static.md)，但不必是 [public](../../../csharp/language-reference/keywords/public.md)。</span><span class="sxs-lookup"><span data-stu-id="2050e-111">`Main` must be [static](../../../csharp/language-reference/keywords/static.md) and it need not be [public](../../../csharp/language-reference/keywords/public.md).</span></span> <span data-ttu-id="2050e-112">(在先前範例中，它會接收 [private](../../../csharp/language-reference/keywords/private.md) 的預設存取)。封入類別或結構不需要是 static。</span><span class="sxs-lookup"><span data-stu-id="2050e-112">(In the earlier example, it receives the default access of [private](../../../csharp/language-reference/keywords/private.md).) The enclosing class or struct is not required to be static.</span></span>
- <span data-ttu-id="2050e-113">`Main` 的傳回型別可以是 `void`、`int`，或是 `Task`、`Task<int>` (從 C# 7.1 開始)。</span><span class="sxs-lookup"><span data-stu-id="2050e-113">`Main` can either have a `void`, `int`, or, starting with C# 7.1, `Task`, or `Task<int>` return type.</span></span>
- <span data-ttu-id="2050e-114">只有當 `Main` 傳回 `Task` 或 `Task<int>` 時，`Main` 的宣告才可以包含 [`async`](../../language-reference/keywords/async.md) 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="2050e-114">If and only if `Main` returns a `Task` or `Task<int>`, the declaration of `Main` may include the [`async`](../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="2050e-115">請注意，上列敘述排除了 `async void Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="2050e-115">Note that this specifically excludes an `async void Main` method.</span></span>
- <span data-ttu-id="2050e-116">`Main` 方法不一定要使用包含命令列引數的 `string[]` 參數來宣告。</span><span class="sxs-lookup"><span data-stu-id="2050e-116">The `Main` method can be declared with or without a `string[]` parameter that contains command-line arguments.</span></span> <span data-ttu-id="2050e-117">使用 Visual Studio 來建立 Windows 應用程式時，您可以手動新增參數，或使用 <xref:System.Environment> 類別來取得命令列引數。</span><span class="sxs-lookup"><span data-stu-id="2050e-117">When using Visual Studio to create Windows applications, you can add the parameter manually or else use the <xref:System.Environment> class to obtain the command-line arguments.</span></span> <span data-ttu-id="2050e-118">參數會讀入來做為以零為基礎的命令列引數。</span><span class="sxs-lookup"><span data-stu-id="2050e-118">Parameters are read as zero-indexed command-line arguments.</span></span> <span data-ttu-id="2050e-119">不同於 C 和 C++，程式的名稱不會被視為第一個命令列引數。</span><span class="sxs-lookup"><span data-stu-id="2050e-119">Unlike C and C++, the name of the program is not treated as the first command-line argument.</span></span>

<span data-ttu-id="2050e-120">當主控台應用程式必須啟動且等待 `Main` 中的 `await` 非同步作業時，新增的 `async` 與 `Task`、`Task<int>` 傳回型別可簡化程式碼。</span><span class="sxs-lookup"><span data-stu-id="2050e-120">The addition of `async` and `Task`, `Task<int>` return types simplifies program code when console applications need to start and `await` asynchronous operations in `Main`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2050e-121">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="2050e-121">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="2050e-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2050e-122">See also</span></span>

- [<span data-ttu-id="2050e-123">使用 csc.exe 建置命令列</span><span class="sxs-lookup"><span data-stu-id="2050e-123">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="2050e-124">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="2050e-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="2050e-125">方法</span><span class="sxs-lookup"><span data-stu-id="2050e-125">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
- [<span data-ttu-id="2050e-126">C# 程式內部</span><span class="sxs-lookup"><span data-stu-id="2050e-126">Inside a C# Program</span></span>](../../../csharp/programming-guide/inside-a-program/index.md)
