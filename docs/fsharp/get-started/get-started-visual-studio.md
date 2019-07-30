---
title: 開始使用F# Visual Studio
description: 瞭解如何搭配 Visual Studio F#使用。
ms.date: 07/03/2018
ms.openlocfilehash: 24c9a81cfa61dc904db9b2213224677696d7eb9b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629763"
---
# <a name="get-started-with-f-in-visual-studio"></a><span data-ttu-id="90b63-103">開始使用F# Visual Studio</span><span class="sxs-lookup"><span data-stu-id="90b63-103">Get started with F# in Visual Studio</span></span>

<span data-ttu-id="90b63-104">F#Visual Studio IDE 中F#支援和視覺化檢視。</span><span class="sxs-lookup"><span data-stu-id="90b63-104">F# and the Visual F# tooling are supported in the Visual Studio IDE.</span></span>

<span data-ttu-id="90b63-105">若要開始, 請確定您已[ F#使用安裝 Visual Studio ](install-fsharp.md#install-f-with-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="90b63-105">To begin, ensure that you have [Visual Studio installed with F#](install-fsharp.md#install-f-with-visual-studio).</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="90b63-106">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="90b63-106">Creating a console application</span></span>

<span data-ttu-id="90b63-107">Visual Studio 中最基本的專案之一, 就是主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="90b63-107">One of the most basic projects in Visual Studio is the Console Application.</span></span>  <span data-ttu-id="90b63-108">以下為作法。</span><span class="sxs-lookup"><span data-stu-id="90b63-108">Here's how to do it.</span></span>  <span data-ttu-id="90b63-109">開啟 Visual Studio 之後:</span><span class="sxs-lookup"><span data-stu-id="90b63-109">Once Visual Studio is open:</span></span>

1. <span data-ttu-id="90b63-110">在 [檔案] 功能表上, 指向 [**新增**], 然後選擇 [**專案**]。</span><span class="sxs-lookup"><span data-stu-id="90b63-110">On the **File** menu, point to **New**, and then choose **Project**.</span></span>

2. <span data-ttu-id="90b63-111">在 [新增專案] 對話方塊的 [**範本**] 底下, 您應該會看到 [**視覺效果F#** ]。</span><span class="sxs-lookup"><span data-stu-id="90b63-111">In the New Project dialog, under **Templates**, you should see **Visual F#**.</span></span>  <span data-ttu-id="90b63-112">選擇此以顯示F#範本。</span><span class="sxs-lookup"><span data-stu-id="90b63-112">Choose this to show the F# templates.</span></span>

3. <span data-ttu-id="90b63-113">選取 [ **.Net Core 主控台應用程式**] 或 [**主控台應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="90b63-113">Select either **.NET Core Console app** or **Console app**.</span></span>

4. <span data-ttu-id="90b63-114">選擇 [確定] 按鈕以建立F#專案!</span><span class="sxs-lookup"><span data-stu-id="90b63-114">Choose the **Okay** button to create the F# project!</span></span>  <span data-ttu-id="90b63-115">您現在應該會在F#方案總管中看到專案。</span><span class="sxs-lookup"><span data-stu-id="90b63-115">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="90b63-116">撰寫程式碼</span><span class="sxs-lookup"><span data-stu-id="90b63-116">Writing your code</span></span>

<span data-ttu-id="90b63-117">讓我們先從撰寫一些程式碼開始。</span><span class="sxs-lookup"><span data-stu-id="90b63-117">Let's get started by writing some code first.</span></span>  <span data-ttu-id="90b63-118">請確定`Program.fs`檔案已開啟, 然後以下列內容取代其內容:</span><span class="sxs-lookup"><span data-stu-id="90b63-118">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="90b63-119">在先前的程式碼範例中, `square`已定義函式, 它會接受`x`名為的輸入, 並將其本身相乘。</span><span class="sxs-lookup"><span data-stu-id="90b63-119">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="90b63-120">因為F#使用[類型推斷](../language-reference/type-inference.md), 所以`x`不需要指定的類型。</span><span class="sxs-lookup"><span data-stu-id="90b63-120">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="90b63-121">編譯器會瞭解乘法的有效類型, 並根據呼叫的方式`square`將類型指派`x`給。 F#</span><span class="sxs-lookup"><span data-stu-id="90b63-121">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="90b63-122">如果您將滑鼠`square`停留在上方, 您應該會看到下列內容:</span><span class="sxs-lookup"><span data-stu-id="90b63-122">If you hover over `square`, you should see the following:</span></span>

```fsharp
val square: x:int -> int
```

<span data-ttu-id="90b63-123">這就是所謂的函式型別簽章。</span><span class="sxs-lookup"><span data-stu-id="90b63-123">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="90b63-124">它可以讀取如下:「方形是一個函式, 它會採用名為 x 的整數, 並產生一個整數」。</span><span class="sxs-lookup"><span data-stu-id="90b63-124">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="90b63-125">請注意, 編譯器`square` `int`現在提供類型, 這是因為乘法不是*所有*類型的泛型, 而是在一組封閉的類型之間是泛型的。</span><span class="sxs-lookup"><span data-stu-id="90b63-125">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="90b63-126">此時F#會選取`int`編譯器, 但如果您使用`float`不同的輸入類型 (例如) 呼叫`square` , 它會調整類型簽章。</span><span class="sxs-lookup"><span data-stu-id="90b63-126">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="90b63-127">已定義另一個函式, 該函式會`EntryPoint`使用屬性裝飾, 告訴F#編譯器應該在該處啟動程式執行。 `main`</span><span class="sxs-lookup"><span data-stu-id="90b63-127">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="90b63-128">其遵循與其他[C 樣式程式語言](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)相同的慣例, 其中命令列引數可傳遞給此函式, 並傳回整數代碼 (通常`0`是)。</span><span class="sxs-lookup"><span data-stu-id="90b63-128">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="90b63-129">在這個函式中, 我們使用的`square` `12`引數來呼叫函數。</span><span class="sxs-lookup"><span data-stu-id="90b63-129">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="90b63-130">然後F# , 編譯器會`int -> int`將的類型`square`指派為 ( `int`也就是採用並產生的函式`int`)。</span><span class="sxs-lookup"><span data-stu-id="90b63-130">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="90b63-131">對的呼叫`printfn`是格式化的列印函式, 它會使用格式字串, 類似于 C 樣式的程式語言、對應于格式字串中所指定的參數, 然後列印結果和新行。</span><span class="sxs-lookup"><span data-stu-id="90b63-131">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="90b63-132">執行您的程式碼</span><span class="sxs-lookup"><span data-stu-id="90b63-132">Running your code</span></span>

<span data-ttu-id="90b63-133">您可以按下**Ctrl** + **F5**來執行程式碼並查看結果。</span><span class="sxs-lookup"><span data-stu-id="90b63-133">You can run the code and see results by pressing **Ctrl**+**F5**.</span></span>  <span data-ttu-id="90b63-134">這會執行程式而不進行偵測, 並可讓您查看結果。</span><span class="sxs-lookup"><span data-stu-id="90b63-134">This runs the program without debugging and allows you to see the results.</span></span>  <span data-ttu-id="90b63-135">或者, 您可以選擇 Visual Studio 中的 [ **Debug** ] 最上層功能表項目, 然後選擇 [**啟動但不進行調試**]。</span><span class="sxs-lookup"><span data-stu-id="90b63-135">Alternatively, you can choose the **Debug** top-level menu item in Visual Studio and choose **Start Without Debugging**.</span></span>

<span data-ttu-id="90b63-136">您現在應該會在主控台視窗中看到下列列印 Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="90b63-136">You should now see the following printed to the console window that Visual Studio popped up:</span></span>

```
12 squared is 144!
```

<span data-ttu-id="90b63-137">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="90b63-137">Congratulations!</span></span>  <span data-ttu-id="90b63-138">您已在 Visual Studio 中F#建立第一個專案, 並F#撰寫一個函式來列印呼叫該函數的結果, 然後執行專案以查看一些結果。</span><span class="sxs-lookup"><span data-stu-id="90b63-138">You've created your first F# project in Visual Studio, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="90b63-139">後續步驟</span><span class="sxs-lookup"><span data-stu-id="90b63-139">Next steps</span></span>

<span data-ttu-id="90b63-140">如果您還沒有這麼做, 請參閱的[導覽F# ](../tour.md), 其中涵蓋了F#語言的一些核心功能。</span><span class="sxs-lookup"><span data-stu-id="90b63-140">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="90b63-141">它可讓您大致瞭解的某些功能F#, 並提供您可以複製到 Visual Studio 並執行的豐富程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="90b63-141">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio and run.</span></span>  <span data-ttu-id="90b63-142">還有一些您可以使用的絕佳外部資源, 請參閱[ F#指南](../index.md)中的展示。</span><span class="sxs-lookup"><span data-stu-id="90b63-142">There are also some great external resources you can use, showcased in the [F# Guide](../index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="90b63-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90b63-143">See also</span></span>

- [<span data-ttu-id="90b63-144">F# 的教學課程</span><span class="sxs-lookup"><span data-stu-id="90b63-144">Tour of F#</span></span>](../tour.md)
- [<span data-ttu-id="90b63-145">F#語言參考</span><span class="sxs-lookup"><span data-stu-id="90b63-145">F# language reference</span></span>](../language-reference/index.md)
- [<span data-ttu-id="90b63-146">型別推斷</span><span class="sxs-lookup"><span data-stu-id="90b63-146">Type inference</span></span>](../language-reference/type-inference.md)
- [<span data-ttu-id="90b63-147">符號和運算子參考</span><span class="sxs-lookup"><span data-stu-id="90b63-147">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)
