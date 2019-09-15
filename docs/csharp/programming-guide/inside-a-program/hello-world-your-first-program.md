---
title: Hello World--在 Windows 或 Mac 上使用 Visual Studio 的第一個C#程式-程式設計指南
ms.custom: seodec18
ms.date: 09/12/2019
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: 0807e46d36a4cf031bc44ae0dc4efab79dd51d03
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991334"
---
# <a name="hello-world----your-first-program"></a><span data-ttu-id="543ca-102">Hello World--您的第一個程式</span><span class="sxs-lookup"><span data-stu-id="543ca-102">Hello World -- Your first program</span></span>

<span data-ttu-id="543ca-103">在本文中，您將使用 Visual Studio 來建立傳統的「Hello World！」</span><span class="sxs-lookup"><span data-stu-id="543ca-103">In this article, you'll use Visual Studio to create the traditional "Hello World!"</span></span> <span data-ttu-id="543ca-104">程式。</span><span class="sxs-lookup"><span data-stu-id="543ca-104">program.</span></span> <span data-ttu-id="543ca-105">Visual Studio 是一種專業整合式開發環境（IDE），具有專為 .NET 開發所設計的許多功能。</span><span class="sxs-lookup"><span data-stu-id="543ca-105">Visual Studio is a professional Integrated Development Environment (IDE) with many features designed for .NET development.</span></span> <span data-ttu-id="543ca-106">您只會使用 Visual Studio 中的幾項功能來建立此程式。</span><span class="sxs-lookup"><span data-stu-id="543ca-106">You'll use only a few of the features in Visual Studio to create this program.</span></span> <span data-ttu-id="543ca-107">若要深入瞭解 Visual Studio，請參閱[使用 Visual C#和 Visual Basic 消費者入門](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="543ca-107">To learn more about Visual Studio, see [Getting Started with Visual C# and Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="create-a-new-application"></a><span data-ttu-id="543ca-108">建立新的應用程式</span><span class="sxs-lookup"><span data-stu-id="543ca-108">Create a new application</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[<span data-ttu-id="543ca-109">Windows</span><span class="sxs-lookup"><span data-stu-id="543ca-109">Windows</span></span>](#tab/windows)

<span data-ttu-id="543ca-110">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="543ca-110">Start Visual Studio.</span></span> <span data-ttu-id="543ca-111">您會在 Windows 上看到下列影像：</span><span class="sxs-lookup"><span data-stu-id="543ca-111">You'll see the following image on Windows:</span></span>

![Visual Studio Windows 上的歡迎畫面](./media/hello-world-your-first-program/visual-studio-windows-start-screen.png)

<span data-ttu-id="543ca-113">選取影像右下角的 [**建立新專案**]。</span><span class="sxs-lookup"><span data-stu-id="543ca-113">Select **Create a new project** in the lower right corner of the image.</span></span> <span data-ttu-id="543ca-114">Visual Studio 會顯示 [**新增專案**] 對話方塊：</span><span class="sxs-lookup"><span data-stu-id="543ca-114">Visual Studio displays the **New Project** dialog:</span></span>

![在 Windows 上 Visual Studio 新增專案畫面](./media/hello-world-your-first-program/visual-studio-windows-new-project.png)

> [!NOTE]
> <span data-ttu-id="543ca-116">如果這是您第一次啟動 Visual Studio，[**最近使用的專案範本**] 清單會是空的。</span><span class="sxs-lookup"><span data-stu-id="543ca-116">If this is the first time you've started Visual Studio, the **Recent project templates** list is empty.</span></span>

<span data-ttu-id="543ca-117">在 [新增專案] 對話方塊中，選擇 [主控台應用程式（.NET Core）]，然後按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="543ca-117">On the new project dialog, choose "Console App (.NET Core)" and then press **Next**.</span></span> <span data-ttu-id="543ca-118">為您的專案命名，例如 "HelloWorld"，然後按 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="543ca-118">Give your project a name, such as "HelloWorld", then press **Create**.</span></span>

<span data-ttu-id="543ca-119">Visual Studio 會開啟您的專案。</span><span class="sxs-lookup"><span data-stu-id="543ca-119">Visual Studio opens your project.</span></span> <span data-ttu-id="543ca-120">它已經是基本的「Hello World！」</span><span class="sxs-lookup"><span data-stu-id="543ca-120">It's already a basic "Hello World!"</span></span> <span data-ttu-id="543ca-121">為例。</span><span class="sxs-lookup"><span data-stu-id="543ca-121">example.</span></span> <span data-ttu-id="543ca-122">按`Ctrl`  + 以執行您的專案。`F5`</span><span class="sxs-lookup"><span data-stu-id="543ca-122">Press `Ctrl` + `F5` to run your project.</span></span> <span data-ttu-id="543ca-123">Visual Studio 會建立您的專案，並將原始程式碼轉換成可執行檔。</span><span class="sxs-lookup"><span data-stu-id="543ca-123">Visual Studio builds your project, converting the source code into an executable.</span></span> <span data-ttu-id="543ca-124">然後，它會啟動執行新應用程式的命令視窗。</span><span class="sxs-lookup"><span data-stu-id="543ca-124">Then, it launches a command window that runs your new application.</span></span> <span data-ttu-id="543ca-125">您應該會在視窗中看到下列文字：</span><span class="sxs-lookup"><span data-stu-id="543ca-125">You should see the following text in the window:</span></span>

```console
Hello World!

C:\Program Files\dotnet\dotnet.exe (process 11964) exited with code 0.
Press any key to close this window . . .
```

<span data-ttu-id="543ca-126">按下任意鍵即可關閉視窗。</span><span class="sxs-lookup"><span data-stu-id="543ca-126">Press a key to close the window.</span></span>

# <a name="macostabmacos"></a>[<span data-ttu-id="543ca-127">macOS</span><span class="sxs-lookup"><span data-stu-id="543ca-127">macOS</span></span>](#tab/macos)

<span data-ttu-id="543ca-128">啟動 Visual Studio for Mac。</span><span class="sxs-lookup"><span data-stu-id="543ca-128">Start Visual Studio for Mac.</span></span> <span data-ttu-id="543ca-129">您會在 Mac 上看到下列影像：</span><span class="sxs-lookup"><span data-stu-id="543ca-129">You'll see the following image on Mac:</span></span>

![Visual Studio Mac 上的歡迎使用畫面](./media/hello-world-your-first-program/visual-studio-mac-start-screen.png)

> [!NOTE]
> <span data-ttu-id="543ca-131">如果這是您第一次啟動 Visual Studio for Mac，[**最近使用的專案**] 清單會是空的。</span><span class="sxs-lookup"><span data-stu-id="543ca-131">If this is the first time you've started Visual Studio for Mac, the **Recent projects** list is empty.</span></span>

<span data-ttu-id="543ca-132">選取影像右上角的 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="543ca-132">Select **New** in the upper right corner of the image.</span></span> <span data-ttu-id="543ca-133">Visual Studio for Mac 會顯示 [**新增專案**] 對話方塊：</span><span class="sxs-lookup"><span data-stu-id="543ca-133">Visual Studio for Mac displays the **New Project** dialog:</span></span>

![在 Mac 上 Visual Studio 新增專案 畫面](./media/hello-world-your-first-program/visual-studio-mac-new-project.png)

<span data-ttu-id="543ca-135">在 [新增專案] 對話方塊中，選擇 [.NET Core] 和 [主控台應用程式]，然後按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="543ca-135">On the new project dialog, choose ".NET Core", and "Console App" and then press **Next**.</span></span> <span data-ttu-id="543ca-136">您必須選取目標 framework。</span><span class="sxs-lookup"><span data-stu-id="543ca-136">You'll need to select the target framework.</span></span> <span data-ttu-id="543ca-137">預設值是正常的，因此請按 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="543ca-137">The default is fine, so press next.</span></span> <span data-ttu-id="543ca-138">為您的專案命名，例如 "HelloWorld"，然後按 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="543ca-138">Give your project a name, such as "HelloWorld", then press **Create**.</span></span> <span data-ttu-id="543ca-139">您可以使用預設的專案位置。</span><span class="sxs-lookup"><span data-stu-id="543ca-139">You can use the default project location.</span></span> <span data-ttu-id="543ca-140">請勿將這個專案加入至原始檔控制。</span><span class="sxs-lookup"><span data-stu-id="543ca-140">Don't add this project to source control.</span></span>

<span data-ttu-id="543ca-141">Visual Studio for Mac 會開啟您的專案。</span><span class="sxs-lookup"><span data-stu-id="543ca-141">Visual Studio for Mac opens your project.</span></span> <span data-ttu-id="543ca-142">它已經是基本的「Hello World！」</span><span class="sxs-lookup"><span data-stu-id="543ca-142">It's already a basic "Hello World!"</span></span> <span data-ttu-id="543ca-143">為例。</span><span class="sxs-lookup"><span data-stu-id="543ca-143">example.</span></span> <span data-ttu-id="543ca-144">按`Ctrl` 以執行 + 您的專案。 +  `Fn` `F5`</span><span class="sxs-lookup"><span data-stu-id="543ca-144">Press `Ctrl` + `Fn` + `F5` to run your project.</span></span> <span data-ttu-id="543ca-145">Visual Studio for Mac 會建立您的專案，並將原始程式碼轉換成可執行檔。</span><span class="sxs-lookup"><span data-stu-id="543ca-145">Visual Studio for Mac builds your project, converting the source code into an executable.</span></span> <span data-ttu-id="543ca-146">然後，它會啟動執行新應用程式的命令視窗。</span><span class="sxs-lookup"><span data-stu-id="543ca-146">Then, it launches a command window that runs your new application.</span></span> <span data-ttu-id="543ca-147">您應該會在視窗中看到下列文字：</span><span class="sxs-lookup"><span data-stu-id="543ca-147">You should see the following text in the window:</span></span>

```console
Hello World!

Press any key to close this window . . .
```

<span data-ttu-id="543ca-148">按下鍵以結束會話。</span><span class="sxs-lookup"><span data-stu-id="543ca-148">Press a key to end the session.</span></span>

---

## <a name="elements-of-a-c-program"></a><span data-ttu-id="543ca-149">C#程式的元素</span><span class="sxs-lookup"><span data-stu-id="543ca-149">Elements of a C# program</span></span>

<span data-ttu-id="543ca-150">讓我們來檢查這個程式的重要部分。</span><span class="sxs-lookup"><span data-stu-id="543ca-150">Let's examine the important parts of this program.</span></span> <span data-ttu-id="543ca-151">第一行包含註解。</span><span class="sxs-lookup"><span data-stu-id="543ca-151">The first line contains a comment.</span></span> <span data-ttu-id="543ca-152">字元 `//` 會將該行的其餘部分轉換成註解。</span><span class="sxs-lookup"><span data-stu-id="543ca-152">The characters `//` convert the rest of the line to a comment.</span></span>

[!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

<span data-ttu-id="543ca-153">您也可以用 `/*` 和 `*/` 字元括住它，註解文字區塊。</span><span class="sxs-lookup"><span data-stu-id="543ca-153">You can also comment out a block of text by enclosing it between the `/*` and `*/` characters.</span></span> <span data-ttu-id="543ca-154">這在下列範例中顯示。</span><span class="sxs-lookup"><span data-stu-id="543ca-154">This is shown in the following example.</span></span>

[!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

<span data-ttu-id="543ca-155">C# 主控台應用程式必須包含 `Main` 方法，控制項在此開始和結束。</span><span class="sxs-lookup"><span data-stu-id="543ca-155">A C# console application must contain a `Main` method, in which control starts and ends.</span></span> <span data-ttu-id="543ca-156">`Main` 方法是您建立物件和執行其他方法的所在。</span><span class="sxs-lookup"><span data-stu-id="543ca-156">The `Main` method is where you create objects and execute other methods.</span></span>

<span data-ttu-id="543ca-157">`Main` 方法是位於類別或結構內的[靜態](../../language-reference/keywords/static.md)方法。</span><span class="sxs-lookup"><span data-stu-id="543ca-157">The `Main` method is a [static](../../language-reference/keywords/static.md) method that resides inside a class or a struct.</span></span> <span data-ttu-id="543ca-158">在上一個 "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="543ca-158">In the previous "Hello World!"</span></span> <span data-ttu-id="543ca-159">範例中，它位於名為 `Hello` 的類別中。</span><span class="sxs-lookup"><span data-stu-id="543ca-159">example, it resides in a class named `Hello`.</span></span> <span data-ttu-id="543ca-160">您可以下列方式之一宣告 `Main` 方法：</span><span class="sxs-lookup"><span data-stu-id="543ca-160">You can declare the `Main` method in one of the following ways:</span></span>

- <span data-ttu-id="543ca-161">它會傳回 `void`。</span><span class="sxs-lookup"><span data-stu-id="543ca-161">It can return `void`.</span></span> <span data-ttu-id="543ca-162">這表示您的程式不會傳回值。</span><span class="sxs-lookup"><span data-stu-id="543ca-162">That means your program doesn't return a value.</span></span>

[!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- <span data-ttu-id="543ca-163">它也可以傳回整數。</span><span class="sxs-lookup"><span data-stu-id="543ca-163">It can also return an integer.</span></span> <span data-ttu-id="543ca-164">整數是應用程式的結束**代碼**。</span><span class="sxs-lookup"><span data-stu-id="543ca-164">The integer is the **exit code** for your application.</span></span>

[!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- <span data-ttu-id="543ca-165">使用任一傳回型別，它可以接受引數。</span><span class="sxs-lookup"><span data-stu-id="543ca-165">With either of the return types, it can take arguments.</span></span>

[!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

<span data-ttu-id="543ca-166">-或-</span><span class="sxs-lookup"><span data-stu-id="543ca-166">-or-</span></span>

[!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

<span data-ttu-id="543ca-167">`Main` 方法的參數 `args`，是包含用來叫用程式的命令列引數的 `string` 陣列。</span><span class="sxs-lookup"><span data-stu-id="543ca-167">The parameter of the `Main` method, `args`, is a `string` array that contains the command-line arguments used to invoke the program.</span></span>

<span data-ttu-id="543ca-168">如需如何使用命令列引數的詳細資訊，請參閱[Main （）和命令列引數](../main-and-command-args/index.md)中的範例。</span><span class="sxs-lookup"><span data-stu-id="543ca-168">For more information about how to use command-line arguments, see the examples in [Main() and Command-Line Arguments](../main-and-command-args/index.md).</span></span>

## <a name="input-and-output"></a><span data-ttu-id="543ca-169">輸入和輸出</span><span class="sxs-lookup"><span data-stu-id="543ca-169">Input and output</span></span>

<span data-ttu-id="543ca-170">C# 程式通常會使用 .NET Framework 執行階段程式庫所提供的輸入/輸出服務。</span><span class="sxs-lookup"><span data-stu-id="543ca-170">C# programs generally use the input/output services provided by the run-time library of the .NET Framework.</span></span> <span data-ttu-id="543ca-171">陳述式 `System.Console.WriteLine("Hello World!");` 使用 <xref:System.Console.WriteLine%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="543ca-171">The statement `System.Console.WriteLine("Hello World!");` uses the <xref:System.Console.WriteLine%2A> method.</span></span> <span data-ttu-id="543ca-172">這是執行階段程式庫中 <xref:System.Console> 類別的其中一個輸出方法。</span><span class="sxs-lookup"><span data-stu-id="543ca-172">This is one of the output methods of the <xref:System.Console> class in the run-time library.</span></span> <span data-ttu-id="543ca-173">它會在標準輸出資料流中顯示其字串參數，後面接著新行。</span><span class="sxs-lookup"><span data-stu-id="543ca-173">It displays its string parameter on the standard output stream followed by a new line.</span></span> <span data-ttu-id="543ca-174">其他 <xref:System.Console> 方法可供不同的輸入和輸出作業使用。</span><span class="sxs-lookup"><span data-stu-id="543ca-174">Other <xref:System.Console> methods are available for different input and output operations.</span></span> <span data-ttu-id="543ca-175">如果您在程式開始處包含 `using System;` 指示詞，就可以直接使用 <xref:System> 類別和方法，而不必完整限定它們。</span><span class="sxs-lookup"><span data-stu-id="543ca-175">If you include the `using System;` directive at the beginning of the program, you can directly use the <xref:System> classes and methods without fully qualifying them.</span></span> <span data-ttu-id="543ca-176">例如，您可以呼叫 `Console.WriteLine` 而不用呼叫 `System.Console.WriteLine`：</span><span class="sxs-lookup"><span data-stu-id="543ca-176">For example, you can call `Console.WriteLine` instead of `System.Console.WriteLine`:</span></span>

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

<span data-ttu-id="543ca-177">如需輸入/輸出方法的詳細資訊，請參閱 <xref:System.IO>。</span><span class="sxs-lookup"><span data-stu-id="543ca-177">For more information about input/output methods, see <xref:System.IO>.</span></span>

## <a name="see-also"></a><span data-ttu-id="543ca-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="543ca-178">See also</span></span>

- [<span data-ttu-id="543ca-179">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="543ca-179">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="543ca-180">範例與教學課程</span><span class="sxs-lookup"><span data-stu-id="543ca-180">Samples and tutorials</span></span>](../../../samples-and-tutorials/index.md)
- [<span data-ttu-id="543ca-181">Main() 和命令列引數</span><span class="sxs-lookup"><span data-stu-id="543ca-181">Main() and Command-Line Arguments</span></span>](../main-and-command-args/index.md)
- [<span data-ttu-id="543ca-182">Visual C# 和 Visual Basic 使用者入門</span><span class="sxs-lookup"><span data-stu-id="543ca-182">Getting Started with Visual C# and Visual Basic</span></span>](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
