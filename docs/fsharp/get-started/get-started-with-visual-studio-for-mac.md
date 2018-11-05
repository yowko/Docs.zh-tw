---
title: '開始使用 F # 在 Visual Studio for Mac'
description: '了解如何使用 F # 與 Visual Studio for mac。'
ms.date: 07/03/2018
ms.openlocfilehash: 6aceec299c29e04aecd7999cd1dda6a56dd2779a
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "44042319"
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a><span data-ttu-id="cee96-103">開始使用 F # 在 Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="cee96-103">Get started with F# in Visual Studio for Mac</span></span>

<span data-ttu-id="cee96-104">F # 和 Visual F # 工具支援 Visual Studio for Mac IDE。</span><span class="sxs-lookup"><span data-stu-id="cee96-104">F# and the Visual F# tooling are supported in the Visual Studio for Mac IDE.</span></span> <span data-ttu-id="cee96-105">請確定您已[Visual Studio for Mac 安裝](install-fsharp.md#install-f-with-visual-studio-for-mac)。</span><span class="sxs-lookup"><span data-stu-id="cee96-105">Ensure that you have [Visual Studio for Mac installed](install-fsharp.md#install-f-with-visual-studio-for-mac).</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="cee96-106">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="cee96-106">Creating a console application</span></span>

<span data-ttu-id="cee96-107">其中一個 Visual Studio for Mac 中最基本的專案是主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="cee96-107">One of the most basic projects in Visual Studio for Mac is the Console Application.</span></span>  <span data-ttu-id="cee96-108">以下為作法。</span><span class="sxs-lookup"><span data-stu-id="cee96-108">Here's how to do it.</span></span>  <span data-ttu-id="cee96-109">一旦開啟 Visual Studio for Mac:</span><span class="sxs-lookup"><span data-stu-id="cee96-109">Once Visual Studio for Mac is open:</span></span>

1. <span data-ttu-id="cee96-110">在 **檔案**功能表上，指向**新的方案**。</span><span class="sxs-lookup"><span data-stu-id="cee96-110">On the **File** menu, point to **New Solution**.</span></span>

2.  <span data-ttu-id="cee96-111">在 [新增專案] 對話方塊中，有 2 個不同的範本，為主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="cee96-111">In the New Project dialog, there are 2 different templates for Console Application.</span></span>  <span data-ttu-id="cee96-112">有一個 其他-> .NET Framework 為目標的.NET。</span><span class="sxs-lookup"><span data-stu-id="cee96-112">There is one under Other -> .NET which targets the .NET Framework.</span></span>  <span data-ttu-id="cee96-113">其他範本是在.NET Core]-> [以.NET Core 為目標的應用程式。</span><span class="sxs-lookup"><span data-stu-id="cee96-113">The other template is under .NET Core -> App which targets .NET Core.</span></span>  <span data-ttu-id="cee96-114">其中一個範本應可基於本文的目的。</span><span class="sxs-lookup"><span data-stu-id="cee96-114">Either template should work for the purpose of this article.</span></span>

3. <span data-ttu-id="cee96-115">在主控台應用程式，視需要變更 C# F #。</span><span class="sxs-lookup"><span data-stu-id="cee96-115">Under console app, change C# to F# if needed.</span></span>  <span data-ttu-id="cee96-116">選擇**下一步**按鈕以向前移動 ！</span><span class="sxs-lookup"><span data-stu-id="cee96-116">Choose the **Next** button to move forward!</span></span>  

4. <span data-ttu-id="cee96-117">為您的專案命名，並選擇您想要的應用程式的選項。</span><span class="sxs-lookup"><span data-stu-id="cee96-117">Give your project a name, and choose the options you want for the app.</span></span>  <span data-ttu-id="cee96-118">請注意，畫面會顯示將建立的目錄結構的側邊的 [預覽] 窗格會根據選取的選項。</span><span class="sxs-lookup"><span data-stu-id="cee96-118">Notice, the preview pane to the side of the screen that will show the directory structure that will be created based on the options selected.</span></span>  

5. <span data-ttu-id="cee96-119">按一下 [建立] 。</span><span class="sxs-lookup"><span data-stu-id="cee96-119">Click **Create**.</span></span>  <span data-ttu-id="cee96-120">現在，您應該會看到 [方案總管] 中的 F # 專案。</span><span class="sxs-lookup"><span data-stu-id="cee96-120">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="cee96-121">撰寫程式碼</span><span class="sxs-lookup"><span data-stu-id="cee96-121">Writing your code</span></span>

<span data-ttu-id="cee96-122">讓我們開始先撰寫一些程式碼。</span><span class="sxs-lookup"><span data-stu-id="cee96-122">Let's get started by writing some code first.</span></span>  <span data-ttu-id="cee96-123">請確定`Program.fs`檔案開啟，並再將其內容取代為下列：</span><span class="sxs-lookup"><span data-stu-id="cee96-123">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="cee96-124">在先前的程式碼範例中，函式`square`它會接受名為的輸入已定義`x`並將它本身乘以。</span><span class="sxs-lookup"><span data-stu-id="cee96-124">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="cee96-125">由於 F # 會使用[型別推斷](../language-reference/type-inference.md)的型別`x`不需要指定。</span><span class="sxs-lookup"><span data-stu-id="cee96-125">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="cee96-126">F # 編譯器了解有效，乘法的類型，並將指派到的類型`x`根據`square`呼叫。</span><span class="sxs-lookup"><span data-stu-id="cee96-126">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="cee96-127">如果您停留`square`，您應該會看到下列：</span><span class="sxs-lookup"><span data-stu-id="cee96-127">If you hover over `square`, you should see the following:</span></span>

```
val square: x:int -> int
```

<span data-ttu-id="cee96-128">這就是所謂的函式的型別簽章。</span><span class="sxs-lookup"><span data-stu-id="cee96-128">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="cee96-129">它可以讀取像這樣:"方形會接受名為整數的函式 x，並產生整數 」。</span><span class="sxs-lookup"><span data-stu-id="cee96-129">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="cee96-130">請注意，編譯器提供給`square``int`類型現在-這是因為乘法不是泛型跨*所有*類型，但而是跨一組封閉型別是泛型。</span><span class="sxs-lookup"><span data-stu-id="cee96-130">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="cee96-131">F # 編譯器挑選`int`在這點，但它將會調整的型別簽章如果您呼叫`square`與不同輸入類型，例如`float`。</span><span class="sxs-lookup"><span data-stu-id="cee96-131">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="cee96-132">另一個函式， `main`，定義，這以裝飾`EntryPoint`應該那里開始告訴 F # 編譯器執行該程式的屬性。</span><span class="sxs-lookup"><span data-stu-id="cee96-132">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="cee96-133">它會遵循相同的慣例，因此另[c-style 程式設計語言](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)，其中可以傳遞命令列引數，此函式，而將整數傳回碼 (通常`0`)。</span><span class="sxs-lookup"><span data-stu-id="cee96-133">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="cee96-134">它是我們呼叫此函式內`square`函式使用引數`12`。</span><span class="sxs-lookup"><span data-stu-id="cee96-134">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="cee96-135">F # 編譯器然後將指定的型別`square`要`int -> int`(也就是函式會採用`int`，並產生`int`)。</span><span class="sxs-lookup"><span data-stu-id="cee96-135">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="cee96-136">若要呼叫`printfn`是格式化的列印函式以使用格式字串，類似 C 樣式程式設計語言，其對應至格式字串中所指定的參數，然後會列印結果和新行。</span><span class="sxs-lookup"><span data-stu-id="cee96-136">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="cee96-137">執行您的程式碼</span><span class="sxs-lookup"><span data-stu-id="cee96-137">Running your code</span></span>

<span data-ttu-id="cee96-138">您可以執行程式碼，並按一下以查看結果**執行**從最上層功能表，然後**啟動但不偵錯**。</span><span class="sxs-lookup"><span data-stu-id="cee96-138">You can run the code and see results by clicking on **Run** from the top level menu and then **Start Without Debugging**.</span></span>  <span data-ttu-id="cee96-139">這會執行程式，但不偵錯，並可讓您查看結果。</span><span class="sxs-lookup"><span data-stu-id="cee96-139">This will run the program without debugging and allows you to see the results.</span></span>

<span data-ttu-id="cee96-140">現在，您應該會看到下列列印到主控台視窗的 Visual Studio for Mac 的快顯出來：</span><span class="sxs-lookup"><span data-stu-id="cee96-140">You should now see the following printed to the console window that Visual Studio for Mac popped up:</span></span>

```
12 squared is 144!
```

<span data-ttu-id="cee96-141">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="cee96-141">Congratulations!</span></span>  <span data-ttu-id="cee96-142">您 for Mac，然後在 Visual Studio 中建立第一個 F # 專案、 撰寫 F # 函式會列印結果呼叫該函式，並執行專案，請參閱某些結果。</span><span class="sxs-lookup"><span data-stu-id="cee96-142">You've created your first F# project in Visual Studio for Mac, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="using-f-interactive"></a><span data-ttu-id="cee96-143">使用 F # Interactive</span><span class="sxs-lookup"><span data-stu-id="cee96-143">Using F# Interactive</span></span>

<span data-ttu-id="cee96-144">其中一個最佳功能中的 Visual F # 工具在 Visual Studio for Mac 是 F # Interactive 視窗。</span><span class="sxs-lookup"><span data-stu-id="cee96-144">One of the best features of the Visual F# tooling in Visual Studio for Mac is the F# Interactive Window.</span></span>  <span data-ttu-id="cee96-145">它可讓您透過的程式碼傳送至處理序，您可以在此呼叫該程式碼，並以互動方式查看結果。</span><span class="sxs-lookup"><span data-stu-id="cee96-145">It allows you to send code over to a process where you can call that code and see the result interactively.</span></span>

<span data-ttu-id="cee96-146">若要開始使用它，反白顯示`square`在您的程式碼中定義的函式。</span><span class="sxs-lookup"><span data-stu-id="cee96-146">To begin using it, highlight the `square` function defined in your code.</span></span>  <span data-ttu-id="cee96-147">接下來，按一下**編輯**從最上層功能表。</span><span class="sxs-lookup"><span data-stu-id="cee96-147">Next, click on **Edit** from the top level menu.</span></span>  <span data-ttu-id="cee96-148">接下來，選取**將選取範圍傳送至 F # Interactive**。</span><span class="sxs-lookup"><span data-stu-id="cee96-148">Next select **Send selection to F# Interactive**.</span></span>  <span data-ttu-id="cee96-149">這在 F # Interactive 視窗中執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="cee96-149">This executes the code in the F# Interactive Window.</span></span>  <span data-ttu-id="cee96-150">或者，您可以在選取範圍上按一下滑鼠右鍵，然後選擇**將選取範圍傳送至 F # Interactive**。</span><span class="sxs-lookup"><span data-stu-id="cee96-150">Alternatively, you can right click on the selection and choose **Send selection to F# Interactive**.</span></span>  <span data-ttu-id="cee96-151">您應該會看到 F # 互動式視窗會出現在它為下列：</span><span class="sxs-lookup"><span data-stu-id="cee96-151">You should see the F# Interactive Window appear with the following in it:</span></span>

```
>

val square : x:int -> int

>
```

<span data-ttu-id="cee96-152">這會顯示相同的函式簽章，如`square`函式，這您稍早您停留在函式上時。</span><span class="sxs-lookup"><span data-stu-id="cee96-152">This shows the same function signature for the `square` function, which you saw earlier when you hovered over the function.</span></span>  <span data-ttu-id="cee96-153">因為`square`是定義在 F # 互動式處理序中，現在可以呼叫具有不同值：</span><span class="sxs-lookup"><span data-stu-id="cee96-153">Because `square` is now defined in the F# Interactive process, you can call it with different values:</span></span>

```
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

<span data-ttu-id="cee96-154">這會執行函式，將結果繫結至新的名稱`it`，並顯示類型和值`it`。</span><span class="sxs-lookup"><span data-stu-id="cee96-154">This executes the function, binds the result to a new name `it`, and displays the type and value of `it`.</span></span>  <span data-ttu-id="cee96-155">請注意，您必須終止使用的每一行`;;`。</span><span class="sxs-lookup"><span data-stu-id="cee96-155">Note that you must terminate each line with `;;`.</span></span>  <span data-ttu-id="cee96-156">這是如何 F # Interactive 知道您的函式呼叫完成時。</span><span class="sxs-lookup"><span data-stu-id="cee96-156">This is how F# Interactive knows when your function call is finished.</span></span>  <span data-ttu-id="cee96-157">您也可以定義新的函式 F # Interactive 中：</span><span class="sxs-lookup"><span data-stu-id="cee96-157">You can also define new functions in F# Interactive:</span></span>

```
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

<span data-ttu-id="cee96-158">上述的定義新的函式中， `isOdd`，這個方法會接受`int`和檢查，以查看是否為奇數 ！</span><span class="sxs-lookup"><span data-stu-id="cee96-158">The above defines a new function, `isOdd`, which takes an `int` and checks to see if it's odd!</span></span>  <span data-ttu-id="cee96-159">您可以呼叫此函式，以查看它以不同的輸入會傳回。</span><span class="sxs-lookup"><span data-stu-id="cee96-159">You can call this function to see what it returns with different inputs.</span></span>  <span data-ttu-id="cee96-160">您可以呼叫內函式呼叫的函式：</span><span class="sxs-lookup"><span data-stu-id="cee96-160">You can call functions within function calls:</span></span>

```
> isOdd (square 15);;
val it : bool = true
```

<span data-ttu-id="cee96-161">您也可以使用[順向的管道運算子](../language-reference/symbol-and-operator-reference/index.md)到管線進入兩個函式的值：</span><span class="sxs-lookup"><span data-stu-id="cee96-161">You can also use the [pipe-forward operator](../language-reference/symbol-and-operator-reference/index.md) to pipeline the value into the two functions:</span></span>

```
> 15 |> square |> isOdd;;
val it : bool = true
```

<span data-ttu-id="cee96-162">順向的管道運算子和詳細資訊，稍後的教學課程所述。</span><span class="sxs-lookup"><span data-stu-id="cee96-162">The pipe-forward operator, and more, are covered in later tutorials.</span></span>

<span data-ttu-id="cee96-163">這是一窺到您可以使用 F # Interactive 執行。</span><span class="sxs-lookup"><span data-stu-id="cee96-163">This is only a glimpse into what you can do with F# Interactive.</span></span>  <span data-ttu-id="cee96-164">若要進一步了解，請參閱[使用 F # 互動式程式設計](../tutorials/fsharp-interactive/index.md)。</span><span class="sxs-lookup"><span data-stu-id="cee96-164">To learn more, check out [Interactive Programming with F#](../tutorials/fsharp-interactive/index.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="cee96-165">後續步驟</span><span class="sxs-lookup"><span data-stu-id="cee96-165">Next steps</span></span>

<span data-ttu-id="cee96-166">如果您還沒有這麼做，請參閱[的 F # 教學課程](../tour.md)，其中涵蓋了一些 F # 語言的核心功能。</span><span class="sxs-lookup"><span data-stu-id="cee96-166">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="cee96-167">它會提供一些 F # 的功能的概觀，並提供很大的程式碼範例，您可以複製到 Visual Studio for Mac，並執行。</span><span class="sxs-lookup"><span data-stu-id="cee96-167">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio for Mac and run.</span></span>  <span data-ttu-id="cee96-168">也有一些絕佳的外部資源，您可以使用，以展示[F # 指南](../index.md)。</span><span class="sxs-lookup"><span data-stu-id="cee96-168">There are also some great external resources you can use, showcased in the [F# Guide](../index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cee96-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cee96-169">See also</span></span>

- [<span data-ttu-id="cee96-170">Visual F#</span><span class="sxs-lookup"><span data-stu-id="cee96-170">Visual F#</span></span>](../index.md)  
- [<span data-ttu-id="cee96-171">F# 的教學課程</span><span class="sxs-lookup"><span data-stu-id="cee96-171">Tour of F#</span></span>](../tour.md)  
- [<span data-ttu-id="cee96-172">F # 語言參考</span><span class="sxs-lookup"><span data-stu-id="cee96-172">F# language reference</span></span>](../language-reference/index.md)  
- [<span data-ttu-id="cee96-173">型別推斷</span><span class="sxs-lookup"><span data-stu-id="cee96-173">Type inference</span></span>](../language-reference/type-inference.md)  
- [<span data-ttu-id="cee96-174">符號和運算子參考</span><span class="sxs-lookup"><span data-stu-id="cee96-174">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)  
