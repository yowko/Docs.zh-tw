---
title: 開始使用F#在 Visual Studio 中
description: 了解如何使用F#使用 Visual Studio。
ms.date: 07/03/2018
ms.openlocfilehash: 9b02a5d295f982b1911dab567213fa9a2b6c4304
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754872"
---
# <a name="get-started-with-f-in-visual-studio"></a><span data-ttu-id="dc707-103">開始使用F#在 Visual Studio 中</span><span class="sxs-lookup"><span data-stu-id="dc707-103">Get started with F# in Visual Studio</span></span>

<span data-ttu-id="dc707-104">F#和視覺效果F#工具所支援的 Visual Studio IDE。</span><span class="sxs-lookup"><span data-stu-id="dc707-104">F# and the Visual F# tooling are supported in the Visual Studio IDE.</span></span>

<span data-ttu-id="dc707-105">若要開始，請確定您已[與 Visual Studio 一起安裝F# ](install-fsharp.md#install-f-with-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="dc707-105">To begin, ensure that you have [Visual Studio installed with F#](install-fsharp.md#install-f-with-visual-studio).</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="dc707-106">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="dc707-106">Creating a console application</span></span>

<span data-ttu-id="dc707-107">Visual Studio 中最基本的專案是主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="dc707-107">One of the most basic projects in Visual Studio is the Console Application.</span></span>  <span data-ttu-id="dc707-108">以下為作法。</span><span class="sxs-lookup"><span data-stu-id="dc707-108">Here's how to do it.</span></span>  <span data-ttu-id="dc707-109">一旦開啟 Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="dc707-109">Once Visual Studio is open:</span></span>

1. <span data-ttu-id="dc707-110">在上**檔案**功能表上，指向**新增**，然後選擇**專案**。</span><span class="sxs-lookup"><span data-stu-id="dc707-110">On the **File** menu, point to **New**, and then choose **Project**.</span></span>

2. <span data-ttu-id="dc707-111">在 [新專案] 對話方塊中，下方**範本**，您應該會看到**視覺化F#** 。</span><span class="sxs-lookup"><span data-stu-id="dc707-111">In the New Project dialog, under **Templates**, you should see **Visual F#**.</span></span>  <span data-ttu-id="dc707-112">選擇此選項以顯示F#範本。</span><span class="sxs-lookup"><span data-stu-id="dc707-112">Choose this to show the F# templates.</span></span>

3. <span data-ttu-id="dc707-113">選取  **.NET Core 主控台應用程式**或是**主控台應用程式**。</span><span class="sxs-lookup"><span data-stu-id="dc707-113">Select either **.NET Core Console app** or **Console app**.</span></span>

4. <span data-ttu-id="dc707-114">選擇**好** 按鈕來建立F#專案 ！</span><span class="sxs-lookup"><span data-stu-id="dc707-114">Choose the **Okay** button to create the F# project!</span></span>  <span data-ttu-id="dc707-115">您現在應該會看到F#方案總管 中的專案。</span><span class="sxs-lookup"><span data-stu-id="dc707-115">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="dc707-116">撰寫程式碼</span><span class="sxs-lookup"><span data-stu-id="dc707-116">Writing your code</span></span>

<span data-ttu-id="dc707-117">讓我們開始先撰寫一些程式碼。</span><span class="sxs-lookup"><span data-stu-id="dc707-117">Let's get started by writing some code first.</span></span>  <span data-ttu-id="dc707-118">請確定`Program.fs`檔案開啟，並再將其內容取代為下列：</span><span class="sxs-lookup"><span data-stu-id="dc707-118">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="dc707-119">在先前的程式碼範例中，函式`square`它會接受名為的輸入已定義`x`並將它本身乘以。</span><span class="sxs-lookup"><span data-stu-id="dc707-119">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="dc707-120">因為F#會使用[型別推斷](../language-reference/type-inference.md)，類型`x`不需要指定。</span><span class="sxs-lookup"><span data-stu-id="dc707-120">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="dc707-121">F#編譯器了解有效，乘法的類型，並將指派到的類型`x`根據`square`呼叫。</span><span class="sxs-lookup"><span data-stu-id="dc707-121">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="dc707-122">如果您停留`square`，您應該會看到下列：</span><span class="sxs-lookup"><span data-stu-id="dc707-122">If you hover over `square`, you should see the following:</span></span>

```fsharp
val square: x:int -> int
```

<span data-ttu-id="dc707-123">這就是所謂的函式的型別簽章。</span><span class="sxs-lookup"><span data-stu-id="dc707-123">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="dc707-124">它可以讀取像這樣："方形會接受名為整數的函式 x，並產生整數 」。</span><span class="sxs-lookup"><span data-stu-id="dc707-124">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="dc707-125">請注意，編譯器提供給`square``int`類型現在-這是因為乘法不是泛型跨*所有*類型，但而是跨一組封閉型別是泛型。</span><span class="sxs-lookup"><span data-stu-id="dc707-125">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="dc707-126">F#編譯器挑選`int`在這點，但它將會調整的型別簽章如果您呼叫`square`取代成不同輸入類型，例如`float`。</span><span class="sxs-lookup"><span data-stu-id="dc707-126">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="dc707-127">另一個函式， `main`，定義，這以裝飾`EntryPoint`告訴屬性F#應該那里啟動程式執行的編譯器。</span><span class="sxs-lookup"><span data-stu-id="dc707-127">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="dc707-128">它會遵循相同的慣例，因此另[c-style 程式設計語言](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)，其中可以傳遞命令列引數，此函式，而將整數傳回碼 (通常`0`)。</span><span class="sxs-lookup"><span data-stu-id="dc707-128">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="dc707-129">它是我們呼叫此函式內`square`函式使用引數`12`。</span><span class="sxs-lookup"><span data-stu-id="dc707-129">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="dc707-130">F#編譯器然後將指定的型別`square`要`int -> int`(也就是函式採用`int`，並產生`int`)。</span><span class="sxs-lookup"><span data-stu-id="dc707-130">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="dc707-131">若要呼叫`printfn`是格式化的列印函式以使用格式字串，類似 C 樣式程式設計語言，其對應至格式字串中所指定的參數，然後會列印結果和新行。</span><span class="sxs-lookup"><span data-stu-id="dc707-131">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="dc707-132">執行您的程式碼</span><span class="sxs-lookup"><span data-stu-id="dc707-132">Running your code</span></span>

<span data-ttu-id="dc707-133">您可以執行程式碼，並查看結果，按下**Ctrl**+**F5**。</span><span class="sxs-lookup"><span data-stu-id="dc707-133">You can run the code and see results by pressing **Ctrl**+**F5**.</span></span>  <span data-ttu-id="dc707-134">這會執行程式，但不偵錯，並可讓您查看結果。</span><span class="sxs-lookup"><span data-stu-id="dc707-134">This runs the program without debugging and allows you to see the results.</span></span>  <span data-ttu-id="dc707-135">或者，您可以選擇**偵錯**最上層功能表項目在 Visual Studio 中，然後選擇**啟動但不偵錯**。</span><span class="sxs-lookup"><span data-stu-id="dc707-135">Alternatively, you can choose the **Debug** top-level menu item in Visual Studio and choose **Start Without Debugging**.</span></span>

<span data-ttu-id="dc707-136">您現在應該會看到下列列印到主控台視窗的 Visual Studio 快顯出來：</span><span class="sxs-lookup"><span data-stu-id="dc707-136">You should now see the following printed to the console window that Visual Studio popped up:</span></span>

```
12 squared is 144!
```

<span data-ttu-id="dc707-137">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="dc707-137">Congratulations!</span></span>  <span data-ttu-id="dc707-138">您已建立您的第一個F#專案在 Visual Studio 中，寫入F#函式列印的結果呼叫的函式，並執行專案，請參閱某些結果。</span><span class="sxs-lookup"><span data-stu-id="dc707-138">You've created your first F# project in Visual Studio, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="dc707-139">後續步驟</span><span class="sxs-lookup"><span data-stu-id="dc707-139">Next steps</span></span>

<span data-ttu-id="dc707-140">如果您還沒有這麼做，請參閱[概觀F# ](../tour.md)，其中涵蓋了一些核心功能的F#語言。</span><span class="sxs-lookup"><span data-stu-id="dc707-140">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="dc707-141">它會提供您的一些功能的概觀F#，並提供很大的程式碼範例，您可以將複製到 Visual Studio，並執行。</span><span class="sxs-lookup"><span data-stu-id="dc707-141">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio and run.</span></span>  <span data-ttu-id="dc707-142">也有一些絕佳的外部資源，您可以使用，以展示[F#指南](../index.md)。</span><span class="sxs-lookup"><span data-stu-id="dc707-142">There are also some great external resources you can use, showcased in the [F# Guide](../index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dc707-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc707-143">See also</span></span>

- [<span data-ttu-id="dc707-144">F# 的教學課程</span><span class="sxs-lookup"><span data-stu-id="dc707-144">Tour of F#</span></span>](../tour.md)
- [<span data-ttu-id="dc707-145">F#語言參考</span><span class="sxs-lookup"><span data-stu-id="dc707-145">F# language reference</span></span>](../language-reference/index.md)
- [<span data-ttu-id="dc707-146">型別推斷</span><span class="sxs-lookup"><span data-stu-id="dc707-146">Type inference</span></span>](../language-reference/type-inference.md)
- [<span data-ttu-id="dc707-147">符號和運算子參考</span><span class="sxs-lookup"><span data-stu-id="dc707-147">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)
