---
title: "開始使用 F # Visual Studio 中"
description: "了解如何使用 F # 與 Visual Studio。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 02/13/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 8db75596-19a9-4eda-b20d-a12d517c8cc1
ms.openlocfilehash: 818bf50507a88e1d765da8d0505ed8da4790b71f
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
---
# <a name="get-started-with-f-in-visual-studio"></a><span data-ttu-id="d353a-104">開始使用 F # Visual Studio 中</span><span class="sxs-lookup"><span data-stu-id="d353a-104">Get started with F# in Visual Studio</span></span>

<span data-ttu-id="d353a-105">Visual Studio IDE 支援 F # 和 Visual F # 工具。</span><span class="sxs-lookup"><span data-stu-id="d353a-105">F# and the Visual F# tooling are supported in the Visual Studio IDE.</span></span>  <span data-ttu-id="d353a-106">若要開始，您應該[下載 Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)，如果您還沒有這麼做。</span><span class="sxs-lookup"><span data-stu-id="d353a-106">To begin, you should [download Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs), if you haven't already.</span></span>  <span data-ttu-id="d353a-107">本文使用 Visual Studio 2017 Community Edition，但是您可以使用 F # 與您所選擇的版本。</span><span class="sxs-lookup"><span data-stu-id="d353a-107">This article uses the Visual Studio 2017 Community Edition, but you can use F# with the version of your choice.</span></span>

## <a name="installing-f"></a><span data-ttu-id="d353a-108">正在安裝 F #</span><span class="sxs-lookup"><span data-stu-id="d353a-108">Installing F#</span></span> #

<span data-ttu-id="d353a-109">如果您要下載 Visual Studio 第一次，它會先安裝 Visual Studio 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="d353a-109">If you're downloading Visual Studio for the first time, it will first install the Visual Studio installer.</span></span>  <span data-ttu-id="d353a-110">安裝任何版本的 Visual Studio 2017 從安裝程式。</span><span class="sxs-lookup"><span data-stu-id="d353a-110">Install any version of Visual Studio 2017 from the installer.</span></span> <span data-ttu-id="d353a-111">如果您已經安裝，請按一下**修改**。</span><span class="sxs-lookup"><span data-stu-id="d353a-111">If you already have it installed, click **Modify**.</span></span>

<span data-ttu-id="d353a-112">接下來，您會看到一份工作負載。</span><span class="sxs-lookup"><span data-stu-id="d353a-112">You'll next see a list of Workloads.</span></span> <span data-ttu-id="d353a-113">您可以安裝 F # 透過任何下列的工作負載：</span><span class="sxs-lookup"><span data-stu-id="d353a-113">You can install F# through any of the following workloads:</span></span>

|<span data-ttu-id="d353a-114">工作負載</span><span class="sxs-lookup"><span data-stu-id="d353a-114">Workload</span></span>|<span data-ttu-id="d353a-115">動作</span><span class="sxs-lookup"><span data-stu-id="d353a-115">Action</span></span>|
|--------|------|
| <span data-ttu-id="d353a-116">.NET Core 跨平台開發</span><span class="sxs-lookup"><span data-stu-id="d353a-116">.NET Core cross-platform development</span></span> | <span data-ttu-id="d353a-117">預設會不安裝任何動作-F #</span><span class="sxs-lookup"><span data-stu-id="d353a-117">No action - F# is installed by default</span></span> |
| <span data-ttu-id="d353a-118">ASP.NET 與網頁程式開發</span><span class="sxs-lookup"><span data-stu-id="d353a-118">ASP.NET and web development</span></span> | <span data-ttu-id="d353a-119">預設會不安裝任何動作-F #</span><span class="sxs-lookup"><span data-stu-id="d353a-119">No action - F# is installed by default</span></span> |
| <span data-ttu-id="d353a-120">Azure 開發</span><span class="sxs-lookup"><span data-stu-id="d353a-120">Azure development</span></span> | <span data-ttu-id="d353a-121">預設會不安裝任何動作-F #</span><span class="sxs-lookup"><span data-stu-id="d353a-121">No action - F# is installed by default</span></span> |
| <span data-ttu-id="d353a-122">使用 .NET 的行動應用程式開發</span><span class="sxs-lookup"><span data-stu-id="d353a-122">Mobile development with .NET</span></span> | <span data-ttu-id="d353a-123">預設會不安裝任何動作-F #</span><span class="sxs-lookup"><span data-stu-id="d353a-123">No action - F# is installed by default</span></span> |
| <span data-ttu-id="d353a-124">資料科學和分析應用程式</span><span class="sxs-lookup"><span data-stu-id="d353a-124">Data science and analytical applications</span></span> | <span data-ttu-id="d353a-125">預設會不安裝任何動作-F #</span><span class="sxs-lookup"><span data-stu-id="d353a-125">No action - F# is installed by default</span></span> |
| <span data-ttu-id="d353a-126">.NET 桌面開發</span><span class="sxs-lookup"><span data-stu-id="d353a-126">.NET desktop development</span></span> | <span data-ttu-id="d353a-127">選取**F # 的桌面版語言支援**右側</span><span class="sxs-lookup"><span data-stu-id="d353a-127">Select **F# desktop language support** from the right-hand side</span></span> |
| <span data-ttu-id="d353a-128">資料儲存體和流程</span><span class="sxs-lookup"><span data-stu-id="d353a-128">Data storage and processing</span></span> | <span data-ttu-id="d353a-129">選取**F # 的桌面版語言支援**右側</span><span class="sxs-lookup"><span data-stu-id="d353a-129">Select **F# desktop language support** from the right-hand side</span></span> |

<span data-ttu-id="d353a-130">接下來，按一下**修改**在右下角。</span><span class="sxs-lookup"><span data-stu-id="d353a-130">Next, click **Modify** in the lower right-hand side.</span></span>  <span data-ttu-id="d353a-131">這會安裝您選取的所有項目。</span><span class="sxs-lookup"><span data-stu-id="d353a-131">This will install everything you have selected.</span></span>  <span data-ttu-id="d353a-132">接著，您可以開啟 Visual Studio 2017 與 F # 語言的支援，即可**啟動**。</span><span class="sxs-lookup"><span data-stu-id="d353a-132">You can then open Visual Studio 2017 with F# language support by clicking **Launch**.</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="d353a-133">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="d353a-133">Creating a console application</span></span>

<span data-ttu-id="d353a-134">其中一個 Visual Studio 中最基本的專案是主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="d353a-134">One of the most basic projects in Visual Studio is the Console Application.</span></span>  <span data-ttu-id="d353a-135">以下為作法。</span><span class="sxs-lookup"><span data-stu-id="d353a-135">Here's how to do it.</span></span>  <span data-ttu-id="d353a-136">一旦開啟 Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="d353a-136">Once Visual Studio is open:</span></span>

1. <span data-ttu-id="d353a-137">在**檔案**功能表上，指向**新增**，然後選擇 **專案**。</span><span class="sxs-lookup"><span data-stu-id="d353a-137">On the **File** menu, point to **New**, and then choose **Project**.</span></span>

2.  <span data-ttu-id="d353a-138">在 [新增專案] 對話方塊中，在**範本**，您應該會看到**Visual F #**。</span><span class="sxs-lookup"><span data-stu-id="d353a-138">In the New Project dialog, under **Templates**, you should see **Visual F#**.</span></span>  <span data-ttu-id="d353a-139">選擇此選項以顯示 F # 範本。</span><span class="sxs-lookup"><span data-stu-id="d353a-139">Choose this to show the F# templates.</span></span>

3. <span data-ttu-id="d353a-140">選取  **.NET Core 主控台應用程式**或**主控台應用程式**。</span><span class="sxs-lookup"><span data-stu-id="d353a-140">Select either **.NET Core Console app** or **Console app**.</span></span>

3. <span data-ttu-id="d353a-141">選擇**好**按鈕以建立 F # 專案 ！</span><span class="sxs-lookup"><span data-stu-id="d353a-141">Choose the **Okay** button to create the F# project!</span></span>  <span data-ttu-id="d353a-142">您現在應該會看到 [方案總管] 中的 F # 專案。</span><span class="sxs-lookup"><span data-stu-id="d353a-142">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="d353a-143">撰寫程式碼</span><span class="sxs-lookup"><span data-stu-id="d353a-143">Writing your code</span></span>

<span data-ttu-id="d353a-144">讓我們開始吧撰寫一些程式碼第一次。</span><span class="sxs-lookup"><span data-stu-id="d353a-144">Let's get started by writing some code first.</span></span>  <span data-ttu-id="d353a-145">請確定`Program.fs`檔案已開啟，而且然後取代為下列內容：</span><span class="sxs-lookup"><span data-stu-id="d353a-145">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="d353a-146">在先前程式碼範例中，函式`square`其可接受名為輸入已定義`x`再將它本身。</span><span class="sxs-lookup"><span data-stu-id="d353a-146">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="d353a-147">因為 F # 使用[型別推斷](../language-reference/type-inference.md)的型別`x`不需要指定。</span><span class="sxs-lookup"><span data-stu-id="d353a-147">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="d353a-148">F # 編譯器瞭解乘法是有效的其中的型別，並將指派到的類型`x`根據`square`呼叫。</span><span class="sxs-lookup"><span data-stu-id="d353a-148">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="d353a-149">如果您將滑鼠停留在`square`，您應該會看到下列：</span><span class="sxs-lookup"><span data-stu-id="d353a-149">If you hover over `square`, you should see the following:</span></span>

```
val square: x:int -> int
```

<span data-ttu-id="d353a-150">這是所謂的函式的類型簽章。</span><span class="sxs-lookup"><span data-stu-id="d353a-150">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="d353a-151">它可以讀取如下:"方會採用名為整數的函式 x，並產生整數 」。</span><span class="sxs-lookup"><span data-stu-id="d353a-151">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="d353a-152">請注意，編譯器提供`square``int`類型現在-這是因為乘法不是泛型跨*所有*類型、 但而是跨一組已關閉的類型是泛型。</span><span class="sxs-lookup"><span data-stu-id="d353a-152">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="d353a-153">F # 編譯器挑選`int`這點，但它會調整的類型簽章如果您呼叫`square`不同輸入類型，例如`float`。</span><span class="sxs-lookup"><span data-stu-id="d353a-153">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="d353a-154">另一個函式， `main`，定義，這以裝飾`EntryPoint`告訴 F # 編譯器執行該程式的屬性應該從那裡開始。</span><span class="sxs-lookup"><span data-stu-id="d353a-154">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="d353a-155">它會遵循與其他的相同慣例[c-style 程式設計語言](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)，然後從中命令列引數可以傳遞至這個函式，並將整數傳回碼 (通常`0`)。</span><span class="sxs-lookup"><span data-stu-id="d353a-155">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="d353a-156">它是我們會呼叫這個函式中`square`函式的引數`12`。</span><span class="sxs-lookup"><span data-stu-id="d353a-156">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="d353a-157">F # 編譯器然後將指定的型別`square`是`int -> int`(也就是函式會採用`int`並產生`int`)。</span><span class="sxs-lookup"><span data-stu-id="d353a-157">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="d353a-158">若要呼叫`printfn`是格式化的列印函式以使用格式字串，類似 c-style 程式設計語言，其對應至格式字串中指定的參數，然後列印結果和新行。</span><span class="sxs-lookup"><span data-stu-id="d353a-158">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="d353a-159">執行您的程式碼</span><span class="sxs-lookup"><span data-stu-id="d353a-159">Running your code</span></span>

<span data-ttu-id="d353a-160">您可以執行的程式碼，並按下查看結果**ctrl-f5**。</span><span class="sxs-lookup"><span data-stu-id="d353a-160">You can run the code and see results by pressing **ctrl-f5**.</span></span>  <span data-ttu-id="d353a-161">這會執行程式，但不偵錯，並可讓您查看結果。</span><span class="sxs-lookup"><span data-stu-id="d353a-161">This will run the program without debugging and allows you to see the results.</span></span>  <span data-ttu-id="d353a-162">或者，您可以選擇**偵錯**最上層功能表項目在 Visual Studio 中，並選擇**啟動但不偵錯**。</span><span class="sxs-lookup"><span data-stu-id="d353a-162">Alternatively, you can choose the **Debug** top-level menu item in Visual Studio and choose **Start Without Debugging**.</span></span>

<span data-ttu-id="d353a-163">您現在應該會看到下列列印到主控台視窗上的 Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="d353a-163">You should now see the following printed to the console window that Visual Studio popped up:</span></span>

```
12 squared is 144!
```

<span data-ttu-id="d353a-164">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="d353a-164">Congratulations!</span></span>  <span data-ttu-id="d353a-165">您在 Visual Studio 中建立第一個 F # 專案、 撰寫 F # 函式列印呼叫此函式的結果並執行專案，以查看一些結果。</span><span class="sxs-lookup"><span data-stu-id="d353a-165">You've created your first F# project in Visual Studio, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="using-f-interactive"></a><span data-ttu-id="d353a-166">使用 F # Interactive</span><span class="sxs-lookup"><span data-stu-id="d353a-166">Using F# Interactive</span></span>

<span data-ttu-id="d353a-167">F # Interactive 視窗的最佳功能的 Visual F # 工具在 Visual Studio 中的其中一個。</span><span class="sxs-lookup"><span data-stu-id="d353a-167">One of the best features of the Visual F# tooling in Visual Studio is the F# Interactive Window.</span></span>  <span data-ttu-id="d353a-168">它可讓您透過的程式碼傳送至處理序，您可以在此呼叫該程式碼，並以互動方式查看結果。</span><span class="sxs-lookup"><span data-stu-id="d353a-168">It allows you to send code over to a process where you can call that code and see the result interactively.</span></span>

<span data-ttu-id="d353a-169">若要開始使用它，反白顯示`square`程式碼中定義的函式。</span><span class="sxs-lookup"><span data-stu-id="d353a-169">To begin using it, highlight the `square` function defined in your code.</span></span>  <span data-ttu-id="d353a-170">接下來，保存**Alt**鍵並按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="d353a-170">Next, hold the **Alt** key and press **Enter**.</span></span>  <span data-ttu-id="d353a-171">這是 F # Interactive 視窗中執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="d353a-171">This executes the code in the F# Interactive Window.</span></span>  <span data-ttu-id="d353a-172">您應該會看到 F # 互動式視窗會出現在它為下列：</span><span class="sxs-lookup"><span data-stu-id="d353a-172">You should see the F# Interactive Window appear with the following in it:</span></span>

```
>

val square : x:int -> int

>
```

<span data-ttu-id="d353a-173">這會顯示為相同的函式簽章`square`函式，當您暫留在進入函式之前看到。</span><span class="sxs-lookup"><span data-stu-id="d353a-173">This shows the same function signature for the `square` function, which you saw earlier when you hovered over the function.</span></span>  <span data-ttu-id="d353a-174">因為`square`是定義在 F # 互動式處理序中，現在可以呼叫具有不同值：</span><span class="sxs-lookup"><span data-stu-id="d353a-174">Because `square` is now defined in the F# Interactive process, you can call it with different values:</span></span>

```
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

<span data-ttu-id="d353a-175">這會執行函式，請將結果繫結至新的名稱`it`，並顯示類型和值`it`。</span><span class="sxs-lookup"><span data-stu-id="d353a-175">This executes the function, binds the result to a new name `it`, and displays the type and value of `it`.</span></span>  <span data-ttu-id="d353a-176">請注意，您必須終止與每一行`;;`。</span><span class="sxs-lookup"><span data-stu-id="d353a-176">Note that you must terminate each line with `;;`.</span></span>  <span data-ttu-id="d353a-177">這是如何 F # Interactive 知道函式呼叫完成時。</span><span class="sxs-lookup"><span data-stu-id="d353a-177">This is how F# Interactive knows when your function call is finished.</span></span>  <span data-ttu-id="d353a-178">您也可以定義新的函式 F # Interactive 中：</span><span class="sxs-lookup"><span data-stu-id="d353a-178">You can also define new functions in F# Interactive:</span></span>

```
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

<span data-ttu-id="d353a-179">上述定義新的函式， `isOdd`，這個方法會接受`int`和檢查，以查看是否為奇數 ！</span><span class="sxs-lookup"><span data-stu-id="d353a-179">The above defines a new function, `isOdd`, which takes an `int` and checks to see if it's odd!</span></span> <span data-ttu-id="d353a-180">您可以呼叫此函式，以查看它傳回以不同的輸入。</span><span class="sxs-lookup"><span data-stu-id="d353a-180">You can call this function to see what it returns with different inputs.</span></span>  <span data-ttu-id="d353a-181">您可以呼叫函式呼叫中的函式：</span><span class="sxs-lookup"><span data-stu-id="d353a-181">You can call functions within function calls:</span></span>

```
> isOdd (square 15);;
val it : bool = true
```

<span data-ttu-id="d353a-182">您也可以使用[管道正運算子](../language-reference/symbol-and-operator-reference/index.md)值導入兩個函式：</span><span class="sxs-lookup"><span data-stu-id="d353a-182">You can also use the [pipe-forward operator](../language-reference/symbol-and-operator-reference/index.md) to pipeline the value into the two functions:</span></span>

```
> 15 |> square |> isOdd;;
val it : bool = true
```

<span data-ttu-id="d353a-183">管道正運算子和詳細資訊，之後的教學課程所述。</span><span class="sxs-lookup"><span data-stu-id="d353a-183">The pipe-forward operator, and more, are covered in later tutorials.</span></span>

<span data-ttu-id="d353a-184">這是一窺成您可以使用 F # Interactive 執行。</span><span class="sxs-lookup"><span data-stu-id="d353a-184">This is only a glimpse into what you can do with F# Interactive.</span></span> <span data-ttu-id="d353a-185">若要進一步了解，請參閱[使用 F # 互動式程式設計](../tutorials/fsharp-interactive/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d353a-185">To learn more, check out [Interactive Programming with F#](../tutorials/fsharp-interactive/index.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="d353a-186">後續步驟</span><span class="sxs-lookup"><span data-stu-id="d353a-186">Next steps</span></span>

<span data-ttu-id="d353a-187">如果您還沒有這麼做，請參閱[教學課程的 F #](../tour.md)，其中涵蓋了某些 F # 語言的核心功能。</span><span class="sxs-lookup"><span data-stu-id="d353a-187">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="d353a-188">它會提供 F # 的功能概觀，並提供豐富的程式碼範例，您可以將複製到 Visual Studio，並執行。</span><span class="sxs-lookup"><span data-stu-id="d353a-188">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio and run.</span></span>  <span data-ttu-id="d353a-189">也有一些絕佳的外部資源，您可以使用，在其中顯示[F # 指南](../index.md)。</span><span class="sxs-lookup"><span data-stu-id="d353a-189">There are also some great external resources you can use, showcased in the [F# Guide](../index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d353a-190">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d353a-190">See also</span></span>
 [<span data-ttu-id="d353a-191">Visual F#</span><span class="sxs-lookup"><span data-stu-id="d353a-191">Visual F#</span></span>](index.md)  
 [<span data-ttu-id="d353a-192">F# 的教學課程</span><span class="sxs-lookup"><span data-stu-id="d353a-192">Tour of F#</span></span>](../tour.md)  
 [<span data-ttu-id="d353a-193">F # 語言參考</span><span class="sxs-lookup"><span data-stu-id="d353a-193">F# language reference</span></span>](../language-reference/index.md)  
 [<span data-ttu-id="d353a-194">類型推斷</span><span class="sxs-lookup"><span data-stu-id="d353a-194">Type inference</span></span>](../language-reference/type-inference.md)  
 [<span data-ttu-id="d353a-195">符號和運算子參考</span><span class="sxs-lookup"><span data-stu-id="d353a-195">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)  
