---
title: 開始使用F# Visual Studio
description: 瞭解如何搭配 Visual Studio F#使用。
ms.date: 12/20/2019
ms.openlocfilehash: 9bf47fb08ea3df0aa0d5064043d94f030d45d568
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337339"
---
# <a name="get-started-with-f-in-visual-studio"></a><span data-ttu-id="17f1f-103">開始使用F# Visual Studio</span><span class="sxs-lookup"><span data-stu-id="17f1f-103">Get started with F# in Visual Studio</span></span>

<span data-ttu-id="17f1f-104">F#Visual Studio 的集成F#開發環境（IDE）支援和視覺化檢視。</span><span class="sxs-lookup"><span data-stu-id="17f1f-104">F# and the Visual F# tooling are supported in the Visual Studio integrated development environment (IDE).</span></span>

<span data-ttu-id="17f1f-105">若要開始，請確定您已[安裝具有F#支援的 Visual Studio](install-fsharp.md#install-f-with-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="17f1f-105">To begin, ensure that you have [Visual Studio installed with F# support](install-fsharp.md#install-f-with-visual-studio).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="17f1f-106">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="17f1f-106">Create a console application</span></span>

<span data-ttu-id="17f1f-107">Visual Studio 中最基本的專案之一，就是主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="17f1f-107">One of the most basic projects in Visual Studio is the console app.</span></span> <span data-ttu-id="17f1f-108">以下是建立伺服器的方式：</span><span class="sxs-lookup"><span data-stu-id="17f1f-108">Here's how to create one:</span></span>

1. <span data-ttu-id="17f1f-109">開啟 Visual Studio 2019。</span><span class="sxs-lookup"><span data-stu-id="17f1f-109">Open Visual Studio 2019.</span></span>

2. <span data-ttu-id="17f1f-110">在開始視窗中，選擇 [建立新專案]。</span><span class="sxs-lookup"><span data-stu-id="17f1f-110">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="17f1f-111">在 [**建立新專案**] 頁面上， **F#** 從 [語言] 清單中選擇。</span><span class="sxs-lookup"><span data-stu-id="17f1f-111">On the **Create a new project** page, choose **F#** from the Language list.</span></span>

4. <span data-ttu-id="17f1f-112">選擇 [**主控台應用程式（.Net Core）** ] 範本，然後選擇 [**下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="17f1f-112">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

5. <span data-ttu-id="17f1f-113">在 [**設定您的新專案**] 頁面的 [**專案名稱**] 方塊中，輸入名稱。</span><span class="sxs-lookup"><span data-stu-id="17f1f-113">On the **Configure your new project** page, enter a name in the **Project name** box.</span></span> <span data-ttu-id="17f1f-114">接著，選擇 [建立]。</span><span class="sxs-lookup"><span data-stu-id="17f1f-114">Then, choose **Create**.</span></span>

   <span data-ttu-id="17f1f-115">Visual Studio 會建立新F#的專案。</span><span class="sxs-lookup"><span data-stu-id="17f1f-115">Visual Studio creates the new F# project.</span></span> <span data-ttu-id="17f1f-116">您可以在 [方案總管] 視窗中看到它。</span><span class="sxs-lookup"><span data-stu-id="17f1f-116">You can see it in the Solution Explorer window.</span></span>

## <a name="write-the-code"></a><span data-ttu-id="17f1f-117">撰寫程式碼</span><span class="sxs-lookup"><span data-stu-id="17f1f-117">Write the code</span></span>

<span data-ttu-id="17f1f-118">讓我們開始撰寫一些程式碼。</span><span class="sxs-lookup"><span data-stu-id="17f1f-118">Let's get started by writing some code.</span></span> <span data-ttu-id="17f1f-119">請確定 `Program.fs` 檔案已開啟，然後以下列內容取代其內容：</span><span class="sxs-lookup"><span data-stu-id="17f1f-119">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="17f1f-120">先前的程式碼範例會定義名為 `square` 的函式，以接受名為 `x` 的輸入，並將其與本身相乘。</span><span class="sxs-lookup"><span data-stu-id="17f1f-120">The previous code sample defines a function called `square` that takes an input named `x` and multiplies it by itself.</span></span> <span data-ttu-id="17f1f-121">因為F#使用[型別推斷](../language-reference/type-inference.md)，所以不需要指定 `x` 的類型。</span><span class="sxs-lookup"><span data-stu-id="17f1f-121">Because F# uses [Type inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span> <span data-ttu-id="17f1f-122">F#編譯器會瞭解乘法的有效類型，並根據呼叫 `square` 的方式，將類型指派給 `x`。</span><span class="sxs-lookup"><span data-stu-id="17f1f-122">The F# compiler understands the types where multiplication is valid and assigns a type to `x` based on how `square` is called.</span></span> <span data-ttu-id="17f1f-123">如果您將滑鼠停留在 `square`上，您應該會看到下列內容：</span><span class="sxs-lookup"><span data-stu-id="17f1f-123">If you hover over `square`, you should see the following:</span></span>

```fsharp
val square: x:int -> int
```

<span data-ttu-id="17f1f-124">這就是所謂的函式型別簽章。</span><span class="sxs-lookup"><span data-stu-id="17f1f-124">This is what is known as the function's type signature.</span></span> <span data-ttu-id="17f1f-125">它可以讀取如下：「方形是一個函式，它會採用名為 x 的整數，並產生一個整數」。</span><span class="sxs-lookup"><span data-stu-id="17f1f-125">It can be read like this: "Square is a function that takes an integer named x and produces an integer".</span></span> <span data-ttu-id="17f1f-126">編譯器現在提供 `square` 的 `int` 類型;這是因為乘法不是*所有*類型的泛型，而是一組封閉的類型。</span><span class="sxs-lookup"><span data-stu-id="17f1f-126">The compiler gave `square` the `int` type for now; this is because multiplication is not generic across *all* types but rather a closed set of types.</span></span> <span data-ttu-id="17f1f-127">如果F#您使用不同的輸入類型（例如 `float`）來呼叫 `square`，編譯器會調整類型簽章。</span><span class="sxs-lookup"><span data-stu-id="17f1f-127">The F# compiler will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="17f1f-128">已定義另一個函式 `main`，該函式會以 `EntryPoint` 屬性裝飾。</span><span class="sxs-lookup"><span data-stu-id="17f1f-128">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute.</span></span> <span data-ttu-id="17f1f-129">這個屬性會告知F#編譯器應該在該處啟動程式執行。</span><span class="sxs-lookup"><span data-stu-id="17f1f-129">This attribute tells the F# compiler that program execution should start there.</span></span> <span data-ttu-id="17f1f-130">其遵循與其他[C 樣式程式語言](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)相同的慣例，其中命令列引數可傳遞給此函式，並傳回整數代碼（通常 `0`）。</span><span class="sxs-lookup"><span data-stu-id="17f1f-130">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="17f1f-131">它位於進入點函式 `main`中，您可以使用 `12`的引數呼叫 `square` 函數。</span><span class="sxs-lookup"><span data-stu-id="17f1f-131">It is in the entry point function, `main`, that you call the `square` function with an argument of `12`.</span></span> <span data-ttu-id="17f1f-132">然後F#編譯器會指派要 `int -> int` 的 `square` 類型（也就是接受 `int` 並產生 `int`的函式）。</span><span class="sxs-lookup"><span data-stu-id="17f1f-132">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function that takes an `int` and produces an `int`).</span></span> <span data-ttu-id="17f1f-133">`printfn` 的呼叫是格式化的列印函式，它會使用格式字串並列印結果（和新的一行）。</span><span class="sxs-lookup"><span data-stu-id="17f1f-133">The call to `printfn` is a formatted printing function that uses a format string and prints the result (and a new line).</span></span> <span data-ttu-id="17f1f-134">格式字串與 C 樣式的程式設計語言類似，其參數（`%d`）會對應至傳遞給它的引數，在此案例中為 `12` 和 `(square 12)`。</span><span class="sxs-lookup"><span data-stu-id="17f1f-134">The format string, similar to C-style programming languages, has parameters (`%d`) that correspond to the arguments that are passed to it, in this case, `12` and `(square 12)`.</span></span>

## <a name="run-the-code"></a><span data-ttu-id="17f1f-135">執行程式碼</span><span class="sxs-lookup"><span data-stu-id="17f1f-135">Run the code</span></span>

<span data-ttu-id="17f1f-136">您可以按**Ctrl**+**F5**來執行程式碼並查看結果。</span><span class="sxs-lookup"><span data-stu-id="17f1f-136">You can run the code and see the results by pressing **Ctrl**+**F5**.</span></span> <span data-ttu-id="17f1f-137">或者，您可以從最上層功能表列選擇 [ **Debug** ] > [**啟動但不進行調試**]。</span><span class="sxs-lookup"><span data-stu-id="17f1f-137">Alternatively, you can choose the **Debug** > **Start Without Debugging** from the top-level menu bar.</span></span> <span data-ttu-id="17f1f-138">這會執行程式而不進行偵測。</span><span class="sxs-lookup"><span data-stu-id="17f1f-138">This runs the program without debugging.</span></span>

<span data-ttu-id="17f1f-139">下列輸出會列印到 Visual Studio 開啟的主控台視窗：</span><span class="sxs-lookup"><span data-stu-id="17f1f-139">The following output prints to the console window that Visual Studio opened:</span></span>

```console
12 squared is: 144!
```

<span data-ttu-id="17f1f-140">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="17f1f-140">Congratulations!</span></span> <span data-ttu-id="17f1f-141">您已在 Visual Studio 中F#建立第一個專案，並F#撰寫一個可計算和列印值的函式，然後執行專案來查看結果。</span><span class="sxs-lookup"><span data-stu-id="17f1f-141">You've created your first F# project in Visual Studio, written an F# function that calculates and prints a value, and run the project to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="17f1f-142">後續步驟</span><span class="sxs-lookup"><span data-stu-id="17f1f-142">Next steps</span></span>

<span data-ttu-id="17f1f-143">如果您還沒有這麼做，請參閱的[導覽F# ](../tour.md)，其中涵蓋了F#語言的一些核心功能。</span><span class="sxs-lookup"><span data-stu-id="17f1f-143">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span> <span data-ttu-id="17f1f-144">其中提供一些功能的F#總覽，以及您可以複製到 Visual Studio 和執行的大量程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="17f1f-144">It provides an overview of some of the capabilities of F# and ample code samples that you can copy into Visual Studio and run.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="17f1f-145">F# 的教學課程</span><span class="sxs-lookup"><span data-stu-id="17f1f-145">Tour of F#</span></span>](../tour.md)

## <a name="see-also"></a><span data-ttu-id="17f1f-146">請參閱</span><span class="sxs-lookup"><span data-stu-id="17f1f-146">See also</span></span>

- [<span data-ttu-id="17f1f-147">F#語言參考</span><span class="sxs-lookup"><span data-stu-id="17f1f-147">F# language reference</span></span>](../language-reference/index.md)
- [<span data-ttu-id="17f1f-148">型別推斷</span><span class="sxs-lookup"><span data-stu-id="17f1f-148">Type inference</span></span>](../language-reference/type-inference.md)
- [<span data-ttu-id="17f1f-149">符號和運算子參考</span><span class="sxs-lookup"><span data-stu-id="17f1f-149">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)
