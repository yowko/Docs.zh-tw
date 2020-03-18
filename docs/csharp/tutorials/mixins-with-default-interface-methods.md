---
title: 使用預設介面方法創建混合類型
description: 使用預設介面成員，您可以擴展具有實現器可選預設實現的介面。
ms.technology: csharp-advanced-concepts
ms.date: 10/04/2019
ms.openlocfilehash: aaf8d34e27c9c56d95560656eb7a7b24b152c053
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240102"
---
# <a name="tutorial-mix-functionality-in-when-creating-classes-using-interfaces-with-default-interface-methods"></a><span data-ttu-id="c8af9-103">教程：使用預設介面方法創建類時，在 中混合功能</span><span class="sxs-lookup"><span data-stu-id="c8af9-103">Tutorial: Mix functionality in when creating classes using interfaces with default interface methods</span></span>

<span data-ttu-id="c8af9-104">從 C# 8.0 開始，您可以在宣告介面成員時，於 .NET Core 3.0 上定義實作。</span><span class="sxs-lookup"><span data-stu-id="c8af9-104">Beginning with C# 8.0 on .NET Core 3.0, you can define an implementation when you declare a member of an interface.</span></span> <span data-ttu-id="c8af9-105">此功能提供了新功能，您可以在其中為介面中聲明的功能定義預設實現。</span><span class="sxs-lookup"><span data-stu-id="c8af9-105">This feature provides new capabilities where you can define default implementations for features declared in interfaces.</span></span> <span data-ttu-id="c8af9-106">類可以選擇何時重寫功能、何時使用預設功能以及何時不聲明對離散功能的支援。</span><span class="sxs-lookup"><span data-stu-id="c8af9-106">Classes can pick when to override functionality, when to use the default functionality, and when not to declare support for discrete features.</span></span>

<span data-ttu-id="c8af9-107">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="c8af9-107">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="c8af9-108">創建具有描述離散功能的實現的介面。</span><span class="sxs-lookup"><span data-stu-id="c8af9-108">Create interfaces with implementations that describe discrete features.</span></span>
> * <span data-ttu-id="c8af9-109">創建使用預設實現的類。</span><span class="sxs-lookup"><span data-stu-id="c8af9-109">Create classes that use the default implementations.</span></span>
> * <span data-ttu-id="c8af9-110">創建覆蓋部分或全部預設實現的類。</span><span class="sxs-lookup"><span data-stu-id="c8af9-110">Create classes that override some or all of the default implementations.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c8af9-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="c8af9-111">Prerequisites</span></span>

<span data-ttu-id="c8af9-112">您需要設置電腦以運行 .NET Core，包括 C# 8.0 編譯器。</span><span class="sxs-lookup"><span data-stu-id="c8af9-112">You’ll need to set up your machine to run .NET Core, including the C# 8.0 compiler.</span></span> <span data-ttu-id="c8af9-113">C# 8.0 編譯器可從[Visual Studio 2019 版本 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)或[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core)或更高版本開始。</span><span class="sxs-lookup"><span data-stu-id="c8af9-113">The C# 8.0 compiler is available starting with [Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), or the [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) or later.</span></span>

## <a name="limitations-of-extension-methods"></a><span data-ttu-id="c8af9-114">擴充方法的限制</span><span class="sxs-lookup"><span data-stu-id="c8af9-114">Limitations of extension methods</span></span>

<span data-ttu-id="c8af9-115">實現作為介面一部分出現的行為的一種方法是定義提供預設行為的[擴充方法](../programming-guide/classes-and-structs/extension-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="c8af9-115">One way you can implement behavior that appears as part of an interface is to define [extension methods](../programming-guide/classes-and-structs/extension-methods.md) that provide the default behavior.</span></span> <span data-ttu-id="c8af9-116">介面聲明最小成員集，同時為實現該介面的任何類提供更大的表面積。</span><span class="sxs-lookup"><span data-stu-id="c8af9-116">Interfaces declare a minimum set of members while providing a greater surface area for any class that implements that interface.</span></span> <span data-ttu-id="c8af9-117">例如，中的<xref:System.Linq.Enumerable>擴充方法為任何序列提供作為 LINQ 查詢源的實現。</span><span class="sxs-lookup"><span data-stu-id="c8af9-117">For example, the extension methods in <xref:System.Linq.Enumerable> provide the implementation for any sequence to be the source of a LINQ query.</span></span>

<span data-ttu-id="c8af9-118">擴充方法在編譯時使用變數的已聲明類型解析。</span><span class="sxs-lookup"><span data-stu-id="c8af9-118">Extension methods are resolved at compile time, using the declared type of the variable.</span></span> <span data-ttu-id="c8af9-119">實現介面的類可以為任何擴充方法提供更好的實現。</span><span class="sxs-lookup"><span data-stu-id="c8af9-119">Classes that implement the interface can provide a better implementation for any extension method.</span></span> <span data-ttu-id="c8af9-120">變數聲明必須與實現類型匹配，以便編譯器能夠選擇該實現。</span><span class="sxs-lookup"><span data-stu-id="c8af9-120">Variable declarations must match the implementing type to enable the compiler to choose that implementation.</span></span> <span data-ttu-id="c8af9-121">當編譯時間類型與介面匹配時，方法調用解析到擴充方法。</span><span class="sxs-lookup"><span data-stu-id="c8af9-121">When the compile-time type matches the interface, method calls resolve to the extension method.</span></span> <span data-ttu-id="c8af9-122">擴充方法的另一個問題是，無論包含擴充方法的類是可訪問的，都可以訪問這些方法。</span><span class="sxs-lookup"><span data-stu-id="c8af9-122">Another concern with extension methods is that those methods are accessible wherever the class containing the extension methods is accessible.</span></span> <span data-ttu-id="c8af9-123">類不能聲明它們是否應提供在擴充方法中聲明的功能。</span><span class="sxs-lookup"><span data-stu-id="c8af9-123">Classes cannot declare if they should or should not provide features declared in extension methods.</span></span>

<span data-ttu-id="c8af9-124">從 C# 8.0 開始，可以將預設實現聲明為介面方法。</span><span class="sxs-lookup"><span data-stu-id="c8af9-124">Starting with C# 8.0, you can declare the default implementations as interface methods.</span></span> <span data-ttu-id="c8af9-125">然後，每個類自動使用預設實現。</span><span class="sxs-lookup"><span data-stu-id="c8af9-125">Then, every class automatically uses the default implementation.</span></span> <span data-ttu-id="c8af9-126">任何可以提供更好實現的類都可以用更好的演算法覆蓋介面方法定義。</span><span class="sxs-lookup"><span data-stu-id="c8af9-126">Any class that can provide a better implementation can override the interface method definition with a better algorithm.</span></span> <span data-ttu-id="c8af9-127">從某種意義上說，這種技術聽起來類似于如何使用[擴充方法](../programming-guide/classes-and-structs/extension-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="c8af9-127">In one sense, this technique sounds similar to how you could use [extension methods](../programming-guide/classes-and-structs/extension-methods.md).</span></span>

<span data-ttu-id="c8af9-128">在本文中，您將瞭解預設介面實現如何啟用新方案。</span><span class="sxs-lookup"><span data-stu-id="c8af9-128">In this article, you'll learn how default interface implementations enable new scenarios.</span></span>

## <a name="design-the-application"></a><span data-ttu-id="c8af9-129">設計應用程式</span><span class="sxs-lookup"><span data-stu-id="c8af9-129">Design the application</span></span>

<span data-ttu-id="c8af9-130">考慮家庭自動化應用程式。</span><span class="sxs-lookup"><span data-stu-id="c8af9-130">Consider a home automation application.</span></span> <span data-ttu-id="c8af9-131">您可能有許多不同類型的燈光和指示燈，可以在整個房子裡使用。</span><span class="sxs-lookup"><span data-stu-id="c8af9-131">You probably have many different types of lights and indicators that could be used throughout the house.</span></span> <span data-ttu-id="c8af9-132">每個指示燈都必須支援 API 以打開和關閉它們，並報告目前狀態。</span><span class="sxs-lookup"><span data-stu-id="c8af9-132">Every light must support APIs to turn them on and off, and to report the current state.</span></span> <span data-ttu-id="c8af9-133">某些燈光和指示燈可能支援其他功能，例如：</span><span class="sxs-lookup"><span data-stu-id="c8af9-133">Some lights and indicators may support other features, such as:</span></span>

- <span data-ttu-id="c8af9-134">打開燈，然後在計時器後將其關閉。</span><span class="sxs-lookup"><span data-stu-id="c8af9-134">Turn light on, then turn it off after a timer.</span></span>
- <span data-ttu-id="c8af9-135">閃爍一段時間的燈。</span><span class="sxs-lookup"><span data-stu-id="c8af9-135">Blink the light for a period of time.</span></span>

<span data-ttu-id="c8af9-136">其中一些擴展功能可以在支援最小集的設備上類比。</span><span class="sxs-lookup"><span data-stu-id="c8af9-136">Some of these extended capabilities could be emulated in devices that support the minimal set.</span></span> <span data-ttu-id="c8af9-137">指示提供預設實現。</span><span class="sxs-lookup"><span data-stu-id="c8af9-137">That indicates providing a default implementation.</span></span> <span data-ttu-id="c8af9-138">對於內置了更多功能的設備，設備軟體將使用本機功能。</span><span class="sxs-lookup"><span data-stu-id="c8af9-138">For those devices that have more capabilities built in, the device software would use the native capabilities.</span></span> <span data-ttu-id="c8af9-139">對於其他燈光，他們可以選擇實現介面並使用預設實現。</span><span class="sxs-lookup"><span data-stu-id="c8af9-139">For other lights, they could choose to implement the interface and use the default implementation.</span></span>

<span data-ttu-id="c8af9-140">預設介面成員是此方案比擴充方法更好的解決方案。</span><span class="sxs-lookup"><span data-stu-id="c8af9-140">Default interface members is a better solution for this scenario than extension methods.</span></span> <span data-ttu-id="c8af9-141">類作者可以控制他們選擇實現哪些介面。</span><span class="sxs-lookup"><span data-stu-id="c8af9-141">Class authors can control which interfaces they choose to implement.</span></span> <span data-ttu-id="c8af9-142">他們選擇的介面可以作為方法提供。</span><span class="sxs-lookup"><span data-stu-id="c8af9-142">Those interfaces they choose are available as methods.</span></span> <span data-ttu-id="c8af9-143">此外，由於預設介面方法在預設情況下是虛擬的，因此方法調度始終選擇類中的實現。</span><span class="sxs-lookup"><span data-stu-id="c8af9-143">In addition, because default interface methods are virtual by default, the method dispatch always chooses the implementation in the class.</span></span>

<span data-ttu-id="c8af9-144">讓我們創建代碼來演示這些差異。</span><span class="sxs-lookup"><span data-stu-id="c8af9-144">Let's create the code to demonstrate these differences.</span></span>

## <a name="create-interfaces"></a><span data-ttu-id="c8af9-145">創建介面</span><span class="sxs-lookup"><span data-stu-id="c8af9-145">Create interfaces</span></span>

<span data-ttu-id="c8af9-146">首先創建定義所有燈光行為的介面：</span><span class="sxs-lookup"><span data-stu-id="c8af9-146">Start by creating the interface that defines the behavior for all lights:</span></span>

[!code-csharp[Declare base interface](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetILightInterfaceV1)]

<span data-ttu-id="c8af9-147">基本開銷燈具可以實現此介面，如以下代碼所示：</span><span class="sxs-lookup"><span data-stu-id="c8af9-147">A basic overhead light fixture might implement this interface as shown in the following code:</span></span>

[!code-csharp[First overhead light](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetOverheadLightV1)]

<span data-ttu-id="c8af9-148">在本教程中，代碼不會驅動 IoT 設備，而是通過向主控台寫入消息來類比這些活動。</span><span class="sxs-lookup"><span data-stu-id="c8af9-148">In this tutorial, the code doesn't drive IoT devices, but emulates those activities by writing messages to the console.</span></span> <span data-ttu-id="c8af9-149">您可以探索代碼，而無需自動執行您的房子。</span><span class="sxs-lookup"><span data-stu-id="c8af9-149">You can explore the code without automating your house.</span></span>

<span data-ttu-id="c8af9-150">接下來，讓我們為超時後可自動關閉的燈定義介面：</span><span class="sxs-lookup"><span data-stu-id="c8af9-150">Next, let's define the interface for a light that can automatically turn off after a timeout:</span></span>

[!code-csharp[pure Timer interface](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetPureTimerInterface)]

<span data-ttu-id="c8af9-151">您可以將基本實現添加到開銷燈中，但更好的解決方案是修改此介面定義以提供`virtual`預設實現：</span><span class="sxs-lookup"><span data-stu-id="c8af9-151">You could add a basic implementation to the overhead light, but a better solution is to modify this interface definition to provide a `virtual` default implementation:</span></span>

[!code-csharp[Timer interface](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/ITimerLight.cs?name=SnippetTimerLightFinal)]

<span data-ttu-id="c8af9-152">通過添加該更改，`OverheadLight`類可以通過聲明對介面的支援來實現計時器函數：</span><span class="sxs-lookup"><span data-stu-id="c8af9-152">By adding that change, the `OverheadLight` class can implement the timer function by declaring support for the interface:</span></span>

```csharp
public class OverheadLight : ITimerLight { }
```

<span data-ttu-id="c8af9-153">不同的光類型可能支援更複雜的協定。</span><span class="sxs-lookup"><span data-stu-id="c8af9-153">A different light type may support a more sophisticated protocol.</span></span> <span data-ttu-id="c8af9-154">它可以為`TurnOnFor`提供自己的實現，如以下代碼所示：</span><span class="sxs-lookup"><span data-stu-id="c8af9-154">It can provide its own implementation for `TurnOnFor`, as shown in the following code:</span></span>

[!code-csharp[Override the timer function](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/HalogenLight.cs?name=SnippetHalogenLight)]

<span data-ttu-id="c8af9-155">與重寫虛擬類方法不同，`TurnOnFor``HalogenLight`類 中的聲明不使用 關鍵字。 `override`</span><span class="sxs-lookup"><span data-stu-id="c8af9-155">Unlike overriding virtual class methods, the declaration of `TurnOnFor` in the `HalogenLight` class does not use the `override` keyword.</span></span>

## <a name="mix-and-match-capabilities"></a><span data-ttu-id="c8af9-156">混合和匹配功能</span><span class="sxs-lookup"><span data-stu-id="c8af9-156">Mix and match capabilities</span></span>

<span data-ttu-id="c8af9-157">隨著引入更高級的功能，預設介面方法的優點變得更加清晰。</span><span class="sxs-lookup"><span data-stu-id="c8af9-157">The advantages of default interface methods become clearer as you introduce more advanced capabilities.</span></span> <span data-ttu-id="c8af9-158">使用介面使您能夠混合和匹配功能。</span><span class="sxs-lookup"><span data-stu-id="c8af9-158">Using interfaces enables you to mix and match capabilities.</span></span> <span data-ttu-id="c8af9-159">它還允許每個類作者在預設實現和自訂實現之間進行選擇。</span><span class="sxs-lookup"><span data-stu-id="c8af9-159">It also enables each class author to choose between the default implementation and a custom implementation.</span></span> <span data-ttu-id="c8af9-160">讓我們為閃爍的燈光添加具有預設實現的介面：</span><span class="sxs-lookup"><span data-stu-id="c8af9-160">Let's add an interface with a default implementation for a blinking light:</span></span>

[!code-csharp[Define the blinking light interface](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/IBlinkingLight.cs?name=SnippetBlinkingLight)]

<span data-ttu-id="c8af9-161">預設實現允許任何指示燈閃爍。</span><span class="sxs-lookup"><span data-stu-id="c8af9-161">The default implementation enables any light to blink.</span></span> <span data-ttu-id="c8af9-162">使用預設實現，頂置指示燈可以同時添加計時器和閃爍功能：</span><span class="sxs-lookup"><span data-stu-id="c8af9-162">The overhead light can add both timer and blink capabilities using the default implementation:</span></span>

[!code-csharp[Use the default blink function](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/OverheadLight.cs?name=SnippetOverheadLight)]

<span data-ttu-id="c8af9-163">新的光類型，直接`LEDLight`支援計時器功能和閃爍功能。</span><span class="sxs-lookup"><span data-stu-id="c8af9-163">A new light type, the `LEDLight` supports both the timer function and the blink function directly.</span></span> <span data-ttu-id="c8af9-164">此光樣式同時實現`ITimerLight`和`IBlinkingLight`介面，並重寫`Blink`方法：</span><span class="sxs-lookup"><span data-stu-id="c8af9-164">This light style implements both the `ITimerLight` and `IBlinkingLight` interfaces, and overrides the `Blink` method:</span></span>

[!code-csharp[Override the blink function](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/LEDLight.cs?name=SnippetLEDLight)]

<span data-ttu-id="c8af9-165">可能`ExtraFancyLight`直接支援閃爍和計時器功能：</span><span class="sxs-lookup"><span data-stu-id="c8af9-165">An `ExtraFancyLight` might support both blink and timer functions directly:</span></span>

[!code-csharp[Override the blink and timer function](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/ExtraFancyLight.cs?name=SnippetExtraFancyLight)]

<span data-ttu-id="c8af9-166">`HalogenLight`您之前創建的不支援閃爍。</span><span class="sxs-lookup"><span data-stu-id="c8af9-166">The `HalogenLight` you created earlier doesn't support blinking.</span></span> <span data-ttu-id="c8af9-167">因此，不要將 添加到`IBlinkingLight`其支援的介面清單中。</span><span class="sxs-lookup"><span data-stu-id="c8af9-167">So, don't add the `IBlinkingLight` to the list of its supported interfaces.</span></span>

## <a name="detect-the-light-types-using-pattern-matching"></a><span data-ttu-id="c8af9-168">使用模式匹配檢測光類型</span><span class="sxs-lookup"><span data-stu-id="c8af9-168">Detect the light types using pattern matching</span></span>

<span data-ttu-id="c8af9-169">接下來，讓我們編寫一些測試代碼。</span><span class="sxs-lookup"><span data-stu-id="c8af9-169">Next, let's write some test code.</span></span> <span data-ttu-id="c8af9-170">您可以通過檢查其支援的介面來確定 C# 的模式[匹配](../pattern-matching.md)功能來確定燈光的功能。</span><span class="sxs-lookup"><span data-stu-id="c8af9-170">You can make use of C#'s [pattern matching](../pattern-matching.md) feature to determine a light's capabilities by examining which interfaces it supports.</span></span>  <span data-ttu-id="c8af9-171">以下方法執行每個光的支援功能：</span><span class="sxs-lookup"><span data-stu-id="c8af9-171">The following method exercises the supported capabilities of each light:</span></span>

[!code-csharp[Test a light's capabilities](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/Program.cs?name=SnippetTestLightFunctions)]

<span data-ttu-id="c8af9-172">方法`Main`中的以下代碼按順序創建每個光類型，並測試該光：</span><span class="sxs-lookup"><span data-stu-id="c8af9-172">The following code in your `Main` method creates each light type in sequence and tests that light:</span></span>

[!code-csharp[Test a light's capabilities](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/Program.cs?name=SnippetMainMethod)]

## <a name="how-the-compiler-determines-best-implementation"></a><span data-ttu-id="c8af9-173">編譯器如何確定最佳實現</span><span class="sxs-lookup"><span data-stu-id="c8af9-173">How the compiler determines best implementation</span></span>

<span data-ttu-id="c8af9-174">此方案顯示一個基本介面，沒有任何實現。</span><span class="sxs-lookup"><span data-stu-id="c8af9-174">This scenario shows a base interface without any implementations.</span></span> <span data-ttu-id="c8af9-175">將方法添加到介面會`ILight`帶來新的複雜性。</span><span class="sxs-lookup"><span data-stu-id="c8af9-175">Adding a method into the `ILight` interface introduces new complexities.</span></span> <span data-ttu-id="c8af9-176">管理預設介面方法的語言規則將實現多個派生介面的具體類的影響降至最低。</span><span class="sxs-lookup"><span data-stu-id="c8af9-176">The language rules governing default interface methods minimize the effect on the concrete classes that implement multiple derived interfaces.</span></span> <span data-ttu-id="c8af9-177">讓我們用新方法增強原始介面，以顯示如何更改其使用。</span><span class="sxs-lookup"><span data-stu-id="c8af9-177">Let's enhance the original interface with a new method to show how that changes its use.</span></span> <span data-ttu-id="c8af9-178">每個指示燈都可以將其電源狀態報表為枚舉值：</span><span class="sxs-lookup"><span data-stu-id="c8af9-178">Every indicator light can report its power status as an enumerated value:</span></span>

[!code-csharp[Enumeration for power status](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/ILight.cs?name=SnippetPowerStatus)]

<span data-ttu-id="c8af9-179">預設實現假定交流電源：</span><span class="sxs-lookup"><span data-stu-id="c8af9-179">The default implementation assumes AC power:</span></span>

[!code-csharp[Report a default power status](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/ILight.cs?name=SnippetILightInterface)]

<span data-ttu-id="c8af9-180">這些更改`ExtraFancyLight`編譯乾淨，即使 聲明支援`ILight`介面和派生介面和`ITimerLight``IBlinkingLight`。</span><span class="sxs-lookup"><span data-stu-id="c8af9-180">These changes compile cleanly, even though the `ExtraFancyLight` declares support for the `ILight` interface and both derived interfaces, `ITimerLight` and `IBlinkingLight`.</span></span> <span data-ttu-id="c8af9-181">`ILight`介面中只聲明瞭一個"最近"實現。</span><span class="sxs-lookup"><span data-stu-id="c8af9-181">There's only one "closest" implementation declared in the `ILight` interface.</span></span> <span data-ttu-id="c8af9-182">任何聲明重寫的類都將成為"最接近"的實現。</span><span class="sxs-lookup"><span data-stu-id="c8af9-182">Any class that declared an override would become the one "closest" implementation.</span></span> <span data-ttu-id="c8af9-183">您看到前面的類中的示例超過了其他派生介面的成員。</span><span class="sxs-lookup"><span data-stu-id="c8af9-183">You saw examples in the preceding classes that overrode the members of other derived interfaces.</span></span>

<span data-ttu-id="c8af9-184">避免在多個派生介面中重寫相同的方法。</span><span class="sxs-lookup"><span data-stu-id="c8af9-184">Avoid overriding the same method in multiple derived interfaces.</span></span> <span data-ttu-id="c8af9-185">這樣做會在類實現兩個派生介面時創建不明確的方法調用。</span><span class="sxs-lookup"><span data-stu-id="c8af9-185">Doing so creates an ambiguous method call whenever a class implements both derived interfaces.</span></span> <span data-ttu-id="c8af9-186">編譯器無法選擇一種更好的方法，因此會發出錯誤。</span><span class="sxs-lookup"><span data-stu-id="c8af9-186">The compiler can't pick a single better method so it issues an error.</span></span> <span data-ttu-id="c8af9-187">例如，如果`IBlinkingLight`和`ITimerLight`都實現了 對`PowerStatus`的重寫`OverheadLight`，則需要提供更具體的重寫。</span><span class="sxs-lookup"><span data-stu-id="c8af9-187">For example, if both the `IBlinkingLight` and `ITimerLight` implemented an override of `PowerStatus`, the `OverheadLight` would need to provide a more specific override.</span></span> <span data-ttu-id="c8af9-188">否則，編譯器無法在兩個派生介面中的實現之間進行選擇。</span><span class="sxs-lookup"><span data-stu-id="c8af9-188">Otherwise, the compiler can't pick between the implementations in the two derived interfaces.</span></span> <span data-ttu-id="c8af9-189">通常可以通過保持介面定義小而專注于一個功能來避免這種情況。</span><span class="sxs-lookup"><span data-stu-id="c8af9-189">You can usually avoid this situation by keeping interface definitions small and focused on one feature.</span></span> <span data-ttu-id="c8af9-190">在這種情況下，光的每個功能都是它自己的介面;多個介面僅由類繼承。</span><span class="sxs-lookup"><span data-stu-id="c8af9-190">In this scenario, each capability of a light is its own interface; multiple interfaces are only inherited by classes.</span></span>

<span data-ttu-id="c8af9-191">此示例顯示了一個方案，您可以在其中定義可混合到類中的離散要素。</span><span class="sxs-lookup"><span data-stu-id="c8af9-191">This sample shows one scenario where you can define discrete features that can be mixed into classes.</span></span> <span data-ttu-id="c8af9-192">通過聲明類支援的介面來聲明任何受支援的功能集。</span><span class="sxs-lookup"><span data-stu-id="c8af9-192">You declare any set of supported functionality by declaring which interfaces a class supports.</span></span> <span data-ttu-id="c8af9-193">使用虛擬預設介面方法使類能夠為任何或所有介面方法使用或定義不同的實現。</span><span class="sxs-lookup"><span data-stu-id="c8af9-193">The use of virtual default interface methods enables classes to use or define a different implementation for any or all the interface methods.</span></span> <span data-ttu-id="c8af9-194">這種語言功能為構建的真實系統提供了建模的新方法。</span><span class="sxs-lookup"><span data-stu-id="c8af9-194">This language capability provides new ways to model the real-world systems you're building.</span></span> <span data-ttu-id="c8af9-195">預設介面方法提供了一種更清晰的方式來表達使用這些功能的虛擬實現混合和匹配不同功能的相關類。</span><span class="sxs-lookup"><span data-stu-id="c8af9-195">Default interface methods provide a clearer way to express related classes that may mix and match different features using virtual implementations of those capabilities.</span></span>
