---
title: '開始使用 Visual Studio 中的 F #'
description: '了解如何使用 F # 與 Visual Studio。'
ms.date: 07/03/2018
ms.openlocfilehash: 3dac8466501338873aeb308ceac9274a7934a8a9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43415730"
---
# <a name="get-started-with-f-in-visual-studio"></a><span data-ttu-id="04248-103">開始使用 Visual Studio 中的 F #</span><span class="sxs-lookup"><span data-stu-id="04248-103">Get started with F# in Visual Studio</span></span>

<span data-ttu-id="04248-104">Visual Studio IDE 中支援 F # 和 Visual F # 工具。</span><span class="sxs-lookup"><span data-stu-id="04248-104">F# and the Visual F# tooling are supported in the Visual Studio IDE.</span></span>

<span data-ttu-id="04248-105">若要開始，請確定您已[安裝 F # 與 Visual Studio](install-fsharp.md#install-f-with-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="04248-105">To begin, ensure that you have [Visual Studio installed with F#](install-fsharp.md#install-f-with-visual-studio).</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="04248-106">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="04248-106">Creating a console application</span></span>

<span data-ttu-id="04248-107">Visual Studio 中最基本的專案是主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="04248-107">One of the most basic projects in Visual Studio is the Console Application.</span></span>  <span data-ttu-id="04248-108">以下為作法。</span><span class="sxs-lookup"><span data-stu-id="04248-108">Here's how to do it.</span></span>  <span data-ttu-id="04248-109">一旦開啟 Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="04248-109">Once Visual Studio is open:</span></span>

1. <span data-ttu-id="04248-110">在上**檔案**功能表上，指向**新增**，然後選擇**專案**。</span><span class="sxs-lookup"><span data-stu-id="04248-110">On the **File** menu, point to **New**, and then choose **Project**.</span></span>

2.  <span data-ttu-id="04248-111">在 [新專案] 對話方塊中，下方**範本**，您應該會看到**Visual F #**。</span><span class="sxs-lookup"><span data-stu-id="04248-111">In the New Project dialog, under **Templates**, you should see **Visual F#**.</span></span>  <span data-ttu-id="04248-112">選擇此選項可顯示 F # 範本。</span><span class="sxs-lookup"><span data-stu-id="04248-112">Choose this to show the F# templates.</span></span>

3. <span data-ttu-id="04248-113">選取  **.NET Core 主控台應用程式**或是**主控台應用程式**。</span><span class="sxs-lookup"><span data-stu-id="04248-113">Select either **.NET Core Console app** or **Console app**.</span></span>

3. <span data-ttu-id="04248-114">選擇**好**按鈕，以建立 F # 專案 ！</span><span class="sxs-lookup"><span data-stu-id="04248-114">Choose the **Okay** button to create the F# project!</span></span>  <span data-ttu-id="04248-115">現在，您應該會看到 [方案總管] 中的 F # 專案。</span><span class="sxs-lookup"><span data-stu-id="04248-115">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="04248-116">撰寫程式碼</span><span class="sxs-lookup"><span data-stu-id="04248-116">Writing your code</span></span>

<span data-ttu-id="04248-117">讓我們開始先撰寫一些程式碼。</span><span class="sxs-lookup"><span data-stu-id="04248-117">Let's get started by writing some code first.</span></span>  <span data-ttu-id="04248-118">請確定`Program.fs`檔案開啟，並再將其內容取代為下列：</span><span class="sxs-lookup"><span data-stu-id="04248-118">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="04248-119">在先前的程式碼範例中，函式`square`它會接受名為的輸入已定義`x`並將它本身乘以。</span><span class="sxs-lookup"><span data-stu-id="04248-119">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="04248-120">由於 F # 會使用[型別推斷](../language-reference/type-inference.md)的型別`x`不需要指定。</span><span class="sxs-lookup"><span data-stu-id="04248-120">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="04248-121">F # 編譯器了解有效，乘法的類型，並將指派到的類型`x`根據`square`呼叫。</span><span class="sxs-lookup"><span data-stu-id="04248-121">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="04248-122">如果您停留`square`，您應該會看到下列：</span><span class="sxs-lookup"><span data-stu-id="04248-122">If you hover over `square`, you should see the following:</span></span>

```
val square: x:int -> int
```

<span data-ttu-id="04248-123">這就是所謂的函式的型別簽章。</span><span class="sxs-lookup"><span data-stu-id="04248-123">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="04248-124">它可以讀取像這樣:"方形會接受名為整數的函式 x，並產生整數 」。</span><span class="sxs-lookup"><span data-stu-id="04248-124">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="04248-125">請注意，編譯器提供給`square``int`類型現在-這是因為乘法不是泛型跨*所有*類型，但而是跨一組封閉型別是泛型。</span><span class="sxs-lookup"><span data-stu-id="04248-125">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="04248-126">F # 編譯器挑選`int`在這點，但它將會調整的型別簽章如果您呼叫`square`與不同輸入類型，例如`float`。</span><span class="sxs-lookup"><span data-stu-id="04248-126">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="04248-127">另一個函式， `main`，定義，這以裝飾`EntryPoint`應該那里開始告訴 F # 編譯器執行該程式的屬性。</span><span class="sxs-lookup"><span data-stu-id="04248-127">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="04248-128">它會遵循相同的慣例，因此另[c-style 程式設計語言](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)，其中可以傳遞命令列引數，此函式，而將整數傳回碼 (通常`0`)。</span><span class="sxs-lookup"><span data-stu-id="04248-128">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="04248-129">它是我們呼叫此函式內`square`函式使用引數`12`。</span><span class="sxs-lookup"><span data-stu-id="04248-129">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="04248-130">F # 編譯器然後將指定的型別`square`要`int -> int`(也就是函式會採用`int`，並產生`int`)。</span><span class="sxs-lookup"><span data-stu-id="04248-130">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="04248-131">若要呼叫`printfn`是格式化的列印函式以使用格式字串，類似 C 樣式程式設計語言，其對應至格式字串中所指定的參數，然後會列印結果和新行。</span><span class="sxs-lookup"><span data-stu-id="04248-131">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="04248-132">執行您的程式碼</span><span class="sxs-lookup"><span data-stu-id="04248-132">Running your code</span></span>

<span data-ttu-id="04248-133">您可以執行程式碼，並查看結果，按下**Ctrl**+**F5**。</span><span class="sxs-lookup"><span data-stu-id="04248-133">You can run the code and see results by pressing **Ctrl**+**F5**.</span></span>  <span data-ttu-id="04248-134">這會執行程式，但不偵錯，並可讓您查看結果。</span><span class="sxs-lookup"><span data-stu-id="04248-134">This runs the program without debugging and allows you to see the results.</span></span>  <span data-ttu-id="04248-135">或者，您可以選擇**偵錯**最上層功能表項目在 Visual Studio 中，然後選擇**啟動但不偵錯**。</span><span class="sxs-lookup"><span data-stu-id="04248-135">Alternatively, you can choose the **Debug** top-level menu item in Visual Studio and choose **Start Without Debugging**.</span></span>

<span data-ttu-id="04248-136">您現在應該會看到下列列印到主控台視窗的 Visual Studio 快顯出來：</span><span class="sxs-lookup"><span data-stu-id="04248-136">You should now see the following printed to the console window that Visual Studio popped up:</span></span>

```
12 squared is 144!
```

<span data-ttu-id="04248-137">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="04248-137">Congratulations!</span></span>  <span data-ttu-id="04248-138">您在 Visual Studio 中建立第一個 F # 專案、 撰寫 F # 函式會列印結果呼叫該函式，並執行專案，請參閱某些結果。</span><span class="sxs-lookup"><span data-stu-id="04248-138">You've created your first F# project in Visual Studio, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="04248-139">後續步驟</span><span class="sxs-lookup"><span data-stu-id="04248-139">Next steps</span></span>

<span data-ttu-id="04248-140">如果您還沒有這麼做，請參閱[的 F # 教學課程](../tour.md)，其中涵蓋了一些 F # 語言的核心功能。</span><span class="sxs-lookup"><span data-stu-id="04248-140">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="04248-141">它會提供一些 F # 的功能的概觀，並提供很大的程式碼範例，您可以將複製到 Visual Studio，並執行。</span><span class="sxs-lookup"><span data-stu-id="04248-141">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio and run.</span></span>  <span data-ttu-id="04248-142">也有一些絕佳的外部資源，您可以使用，以展示[F # 指南](../index.md)。</span><span class="sxs-lookup"><span data-stu-id="04248-142">There are also some great external resources you can use, showcased in the [F# Guide](../index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="04248-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04248-143">See also</span></span>

- [<span data-ttu-id="04248-144">F# 的教學課程</span><span class="sxs-lookup"><span data-stu-id="04248-144">Tour of F#</span></span>](../tour.md)
- [<span data-ttu-id="04248-145">F # 語言參考</span><span class="sxs-lookup"><span data-stu-id="04248-145">F# language reference</span></span>](../language-reference/index.md)
- [<span data-ttu-id="04248-146">型別推斷</span><span class="sxs-lookup"><span data-stu-id="04248-146">Type inference</span></span>](../language-reference/type-inference.md)
- [<span data-ttu-id="04248-147">符號和運算子參考</span><span class="sxs-lookup"><span data-stu-id="04248-147">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)
