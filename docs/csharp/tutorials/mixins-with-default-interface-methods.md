---
title: 使用預設介面方法建立 mixin 類型
description: 使用預設介面成員，您可以使用實作者的選擇性預設實作為擴充介面。
ms.date: 10/04/2019
ms.openlocfilehash: 4dee97226420139d9cd09ad75d7c8caf4967273d
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321621"
---
# <a name="tutorial-mix-in-functionality-when-creating-classes-using-interfaces-with-default-interface-methods"></a><span data-ttu-id="e9a3c-103">教學課程：使用具有預設介面方法的介面建立類別時混用功能</span><span class="sxs-lookup"><span data-stu-id="e9a3c-103">Tutorial: Mix in functionality when creating classes using interfaces with default interface methods</span></span>

<span data-ttu-id="e9a3c-104">從 C# 8.0 開始，您可以在宣告介面成員時，於 .NET Core 3.0 上定義實作。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-104">Beginning with C# 8.0 on .NET Core 3.0, you can define an implementation when you declare a member of an interface.</span></span> <span data-ttu-id="e9a3c-105">這項功能提供新的功能，您可以在其中為介面中宣告的功能定義預設的執行方式。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-105">This feature provides new capabilities where you can define default implementations for features declared in interfaces.</span></span> <span data-ttu-id="e9a3c-106">類別可以挑選何時覆寫功能、何時使用預設功能，以及何時不宣告對離散功能的支援。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-106">Classes can pick when to override functionality, when to use the default functionality, and when not to declare support for discrete features.</span></span>

<span data-ttu-id="e9a3c-107">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="e9a3c-107">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="e9a3c-108">使用可描述離散功能的實作為建立介面。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-108">Create interfaces with implementations that describe discrete features.</span></span>
> * <span data-ttu-id="e9a3c-109">建立使用預設實現的類別。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-109">Create classes that use the default implementations.</span></span>
> * <span data-ttu-id="e9a3c-110">建立會覆寫部分或全部預設實作為的類別。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-110">Create classes that override some or all of the default implementations.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e9a3c-111">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="e9a3c-111">Prerequisites</span></span>

<span data-ttu-id="e9a3c-112">您必須設定電腦以執行 .NET Core，包括C# 8.0 編譯器。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-112">You’ll need to set up your machine to run .NET Core, including the C# 8.0 compiler.</span></span> <span data-ttu-id="e9a3c-113">C# 8.0 編譯器從[Visual Studio 2019、16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)或[.net Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) （含）以後版本開始提供。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-113">The C# 8.0 compiler is available starting with [Visual Studio 2019, 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), or the [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) or later.</span></span>

## <a name="limitations-of-extension-methods"></a><span data-ttu-id="e9a3c-114">擴充方法的限制</span><span class="sxs-lookup"><span data-stu-id="e9a3c-114">Limitations of extension methods</span></span>

<span data-ttu-id="e9a3c-115">有一種方式可以實作為介面的一部分來執行行為，即定義提供預設行為的[擴充方法](../programming-guide/classes-and-structs/extension-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-115">One way you can implement behavior that appears as part of an interface is to define [extension methods](../programming-guide/classes-and-structs/extension-methods.md) that provide the default behavior.</span></span> <span data-ttu-id="e9a3c-116">介面會宣告一組最小成員，同時為任何可實作為介面的類別提供更大的表面區域。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-116">Interfaces declare a minimum set of members while providing a greater surface area for any class that implements that interface.</span></span> <span data-ttu-id="e9a3c-117">例如，<xref:System.Linq.Enumerable> 中的擴充方法會提供任何序列的執行，做為 LINQ 查詢的來源。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-117">For example, the extension methods in <xref:System.Linq.Enumerable> provide the implementation for any sequence to be the source of a LINQ query.</span></span>

<span data-ttu-id="e9a3c-118">擴充方法會在編譯時期解析，並使用變數的宣告型別。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-118">Extension methods are resolved at compile time, using the declared type of the variable.</span></span> <span data-ttu-id="e9a3c-119">執行介面的類別可以為任何擴充方法提供更好的執行方式。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-119">Classes that implement the interface can provide a better implementation for any extension method.</span></span> <span data-ttu-id="e9a3c-120">變數宣告必須符合實類型，才能讓編譯器選擇該執行。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-120">Variable declarations must match the implementing type to enable the compiler to choose that implementation.</span></span> <span data-ttu-id="e9a3c-121">當編譯時間型別符合介面時，方法呼叫會解析成擴充方法。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-121">When the compile-time type matches the interface, method calls resolve to the extension method.</span></span> <span data-ttu-id="e9a3c-122">擴充方法還有另一個考慮，就是可存取包含擴充方法之類別的任何地方都可以存取這些方法。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-122">Another concern with extension methods is that those methods are accessible wherever the class containing the extension methods is accessible.</span></span> <span data-ttu-id="e9a3c-123">如果類別不應該或不應該提供在擴充方法中宣告的功能，就無法宣告。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-123">Classes cannot declare if they should or should not provide features declared in extension methods.</span></span>

<span data-ttu-id="e9a3c-124">從C# 8.0 開始，您可以將預設的實作為介面方法來宣告。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-124">Starting with C# 8.0, you can declare the default implementations as interface methods.</span></span> <span data-ttu-id="e9a3c-125">然後，每個類別都會自動使用預設的實值。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-125">Then, every class automatically uses the default implementation.</span></span> <span data-ttu-id="e9a3c-126">可以提供更好的執行方式的任何類別，都可以使用更好的演算法來覆寫介面方法定義。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-126">Any class that can provide a better implementation can override the interface method definition with a better algorithm.</span></span> <span data-ttu-id="e9a3c-127">就這一點而言，這項技術與您可以使用[擴充方法](../programming-guide/classes-and-structs/extension-methods.md)的方式非常類似。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-127">In one sense, this technique sounds similar to how you could use [extension methods](../programming-guide/classes-and-structs/extension-methods.md).</span></span>

<span data-ttu-id="e9a3c-128">在本文中，您將瞭解預設介面的實現如何啟用新的案例。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-128">In this article, you'll learn how default interface implementations enable new scenarios.</span></span>

## <a name="design-the-application"></a><span data-ttu-id="e9a3c-129">設計應用程式</span><span class="sxs-lookup"><span data-stu-id="e9a3c-129">Design the application</span></span>

<span data-ttu-id="e9a3c-130">請考慮使用「家庭自動化」應用程式。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-130">Consider a home automation application.</span></span> <span data-ttu-id="e9a3c-131">您可能會有許多不同類型的光源和指示器，可以在整個房屋中使用。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-131">You probably have many different types of lights and indicators that could be used throughout the house.</span></span> <span data-ttu-id="e9a3c-132">每個光線都必須支援 Api，才能開啟和關閉這些應用程式，以及報告目前的狀態。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-132">Every light must support APIs to turn them on and off, and to report the current state.</span></span> <span data-ttu-id="e9a3c-133">有些光源和指示器可能支援其他功能，例如：</span><span class="sxs-lookup"><span data-stu-id="e9a3c-133">Some lights and indicators may support other features, such as:</span></span>

- <span data-ttu-id="e9a3c-134">開啟 [亮]，然後在計時器之後關閉它。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-134">Turn light on, then turn it off after a timer.</span></span>
- <span data-ttu-id="e9a3c-135">將燈閃爍一段時間。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-135">Blink the light for a period of time.</span></span>

<span data-ttu-id="e9a3c-136">其中一些擴充功能可以在支援最小設定的裝置上進行模擬。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-136">Some of these extended capabilities could be emulated in devices that support the minimal set.</span></span> <span data-ttu-id="e9a3c-137">，表示提供預設的執行。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-137">That indicates providing a default implementation.</span></span> <span data-ttu-id="e9a3c-138">對於內建更多功能的裝置，裝置軟體會使用原生功能。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-138">For those devices that have more capabilities built in, the device software would use the native capabilities.</span></span> <span data-ttu-id="e9a3c-139">針對其他光源，他們可以選擇執行介面，並使用預設的實作為。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-139">For other lights, they could choose to implement the interface and use the default implementation.</span></span>

<span data-ttu-id="e9a3c-140">在此案例中，預設介面成員是比擴充方法更好的解決方案。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-140">Default interface members is a better solution for this scenario than extension methods.</span></span> <span data-ttu-id="e9a3c-141">類別作者可以控制他們選擇要執行的介面。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-141">Class authors can control which interfaces they choose to implement.</span></span> <span data-ttu-id="e9a3c-142">它們所選擇的介面可以做為方法。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-142">Those interfaces they choose are available as methods.</span></span> <span data-ttu-id="e9a3c-143">此外，因為預設介面方法是虛擬的，所以方法分派一律會選擇類別中的實值。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-143">In addition, because default interface methods are virtual by default, the method dispatch always chooses the implementation in the class.</span></span> 

<span data-ttu-id="e9a3c-144">讓我們建立程式碼來示範這些差異。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-144">Let's create the code to demonstrate these differences.</span></span>

## <a name="create-interfaces"></a><span data-ttu-id="e9a3c-145">建立介面</span><span class="sxs-lookup"><span data-stu-id="e9a3c-145">Create interfaces</span></span>

<span data-ttu-id="e9a3c-146">首先建立介面來定義所有光源的行為：</span><span class="sxs-lookup"><span data-stu-id="e9a3c-146">Start by creating the interface that defines the behavior for all lights:</span></span>

[!code-csharp[Declare base interface](~/samples/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetILightInterfaceV1)]

<span data-ttu-id="e9a3c-147">基本的額外負荷輕量裝置可能會實作為下列程式碼所示的介面：</span><span class="sxs-lookup"><span data-stu-id="e9a3c-147">A basic overhead light fixture might implement this interface as shown in the following code:</span></span>

[!code-csharp[First overhead light](~/samples/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetOverheadLightV1)]

<span data-ttu-id="e9a3c-148">在本教學課程中，程式碼不會驅動 IoT 裝置，而是會藉由將訊息寫入主控台來模擬這些活動。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-148">In this tutorial, the code doesn't drive IoT devices, but emulates those activities by writing messages to the console.</span></span> <span data-ttu-id="e9a3c-149">您可以流覽程式碼，而不需要自動化您的公司。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-149">You can explore the code without automating your house.</span></span>

<span data-ttu-id="e9a3c-150">接下來，我們將定義可在超時時間之後自動關閉的光線介面：</span><span class="sxs-lookup"><span data-stu-id="e9a3c-150">Next, let's define the interface for a light that can automatically turn off after a timeout:</span></span>

[!code-csharp[pure Timer interface](~/samples/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetPureTimerInterface)]

<span data-ttu-id="e9a3c-151">您可以將基本的執行方式新增至額外負荷，但更好的解決方案是修改此介面定義，以提供 `virtual` 的預設實作為方式：</span><span class="sxs-lookup"><span data-stu-id="e9a3c-151">You could add a basic implementation to the overhead light, but a better solution is to modify this interface definition to provide a `virtual` default implementation:</span></span>

[!code-csharp[Timer interface](~/samples/csharp/tutorials/mixins-with-interfaces/ITimerLight.cs?name=SnippetTimerLightFinal)]

<span data-ttu-id="e9a3c-152">藉由加入該變更，`OverheadLight` 類別可以藉由宣告介面的支援，來實作用計時器函式：</span><span class="sxs-lookup"><span data-stu-id="e9a3c-152">By adding that change, the `OverheadLight` class can implement the timer function by declaring support for the interface:</span></span>

```csharp
public class OverheadLight : ITimerLight { }
```

<span data-ttu-id="e9a3c-153">不同的光源類型可能會支援更複雜的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-153">A different light type may support a more sophisticated protocol.</span></span> <span data-ttu-id="e9a3c-154">它可以為 `TurnOnFor` 提供自己的執行，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="e9a3c-154">It can provide its own implementation for `TurnOnFor`, as shown in the following code:</span></span>

[!code-csharp[Override the timer function](~/samples/csharp/tutorials/mixins-with-interfaces/HalogenLight.cs?name=SnippetHalogenLight)]

<span data-ttu-id="e9a3c-155">不同于覆寫虛擬類別方法，`HalogenLight` 類別中的 `TurnOnFor` 宣告不會使用 `override` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-155">Unlike overriding virtual class methods, the declaration of `TurnOnFor` in the `HalogenLight` class does not use the `override` keyword.</span></span> 

## <a name="mix-and-match-capabilities"></a><span data-ttu-id="e9a3c-156">混合和比對功能</span><span class="sxs-lookup"><span data-stu-id="e9a3c-156">Mix and match capabilities</span></span>

<span data-ttu-id="e9a3c-157">當您引進更先進的功能時，預設介面方法的優點會變得更清楚。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-157">The advantages of default interface methods become clearer as you introduce more advanced capabilities.</span></span> <span data-ttu-id="e9a3c-158">使用介面可讓您混合和比對功能。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-158">Using interfaces enables you to mix and match capabilities.</span></span> <span data-ttu-id="e9a3c-159">它也可以讓每個類別作者在預設的執行和自訂執行之間做選擇。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-159">It also enables each class author to choose between the default implementation and a custom implementation.</span></span> <span data-ttu-id="e9a3c-160">讓我們使用閃爍燈的預設實來新增介面：</span><span class="sxs-lookup"><span data-stu-id="e9a3c-160">Let's add an interface with a default implementation for a blinking light:</span></span>

[!code-csharp[Define the blinking light interface](~/samples/csharp/tutorials/mixins-with-interfaces/IBlinkingLight.cs?name=SnippetBlinkingLight)]

<span data-ttu-id="e9a3c-161">預設的實值可讓任何光線閃爍。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-161">The default implementation enables any light to blink.</span></span> <span data-ttu-id="e9a3c-162">額外負荷可能會使用預設的實作為新增計時器和閃爍功能：</span><span class="sxs-lookup"><span data-stu-id="e9a3c-162">The overhead light can add both timer and blink capabilities using the default implementation:</span></span>

[!code-csharp[Use the default blink function](~/samples/csharp/tutorials/mixins-with-interfaces/OverheadLight.cs?name=SnippetOverheadLight)]

<span data-ttu-id="e9a3c-163">新的光源類型，`LEDLight` 同時支援計時器函式和閃爍函式。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-163">A new light type, the `LEDLight` supports both the timer function and the blink function directly.</span></span> <span data-ttu-id="e9a3c-164">這個淺色樣式會同時執行 `ITimerLight` 和 `IBlinkingLight` 介面，並覆寫 `Blink` 方法：</span><span class="sxs-lookup"><span data-stu-id="e9a3c-164">This light style implements both the `ITimerLight` and `IBlinkingLight` interfaces, and overrides the `Blink` method:</span></span>

[!code-csharp[Override the blink function](~/samples/csharp/tutorials/mixins-with-interfaces/LEDLight.cs?name=SnippetLEDLight)]

<span data-ttu-id="e9a3c-165">@No__t_0 可能會直接支援閃爍和計時器函式：</span><span class="sxs-lookup"><span data-stu-id="e9a3c-165">An `ExtraFancyLight` might support both blink and timer functions directly:</span></span>

[!code-csharp[Override the blink and timer function](~/samples/csharp/tutorials/mixins-with-interfaces/ExtraFancyLight.cs?name=SnippetExtraFancyLight)]

<span data-ttu-id="e9a3c-166">您稍早建立的 `HalogenLight` 不支援閃爍。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-166">The `HalogenLight` you created earlier doesn't support blinking.</span></span> <span data-ttu-id="e9a3c-167">因此，請勿將 `IBlinkingLight` 新增至其支援的介面清單。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-167">So, don't add the `IBlinkingLight` to the list of its supported interfaces.</span></span>

## <a name="detect-the-light-types-using-pattern-matching"></a><span data-ttu-id="e9a3c-168">使用模式比對來偵測光源類型</span><span class="sxs-lookup"><span data-stu-id="e9a3c-168">Detect the light types using pattern matching</span></span>

<span data-ttu-id="e9a3c-169">接下來，讓我們撰寫一些測試程式碼。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-169">Next, let's write some test code.</span></span> <span data-ttu-id="e9a3c-170">您可以藉由檢查C#支援的介面，來利用的[模式](../pattern-matching.md)比對功能來判斷光線的功能。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-170">You can make use of C#'s [pattern matching](../pattern-matching.md) feature to determine a light's capabilities by examining which interfaces it supports.</span></span>  <span data-ttu-id="e9a3c-171">下列方法會練習每個光線支援的功能：</span><span class="sxs-lookup"><span data-stu-id="e9a3c-171">The following method exercises the supported capabilities of each light:</span></span>

[!code-csharp[Test a light's capabilities](~/samples/csharp/tutorials/mixins-with-interfaces/Program.cs?name=SnippetTestLightFunctions)]

<span data-ttu-id="e9a3c-172">@No__t_0 方法中的下列程式碼會依序建立每個光源類型，並測試該光線：</span><span class="sxs-lookup"><span data-stu-id="e9a3c-172">The following code in your `Main` method creates each light type in sequence and tests that light:</span></span>

[!code-csharp[Test a light's capabilities](~/samples/csharp/tutorials/mixins-with-interfaces/Program.cs?name=SnippetMainMethod)]

## <a name="how-the-compiler-determines-best-implementation"></a><span data-ttu-id="e9a3c-173">編譯器如何判斷最佳的執行方式</span><span class="sxs-lookup"><span data-stu-id="e9a3c-173">How the compiler determines best implementation</span></span>

<span data-ttu-id="e9a3c-174">此案例顯示不含任何執行的基底介面。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-174">This scenario shows a base interface without any implementations.</span></span> <span data-ttu-id="e9a3c-175">將方法新增至 `ILight` 介面會帶來新的複雜性。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-175">Adding a method into the `ILight` interface introduces new complexities.</span></span> <span data-ttu-id="e9a3c-176">管理預設介面方法的語言規則會將對執行多個衍生介面之實體類別的影響降至最低。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-176">The language rules governing default interface methods minimize the effect on the concrete classes that implement multiple derived interfaces.</span></span> <span data-ttu-id="e9a3c-177">讓我們使用新的方法來增強原始介面，以顯示如何變更其使用方式。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-177">Let's enhance the original interface with a new method to show how that changes its use.</span></span> <span data-ttu-id="e9a3c-178">每個指示器光線都可以將其電源狀態報表為列舉值：</span><span class="sxs-lookup"><span data-stu-id="e9a3c-178">Every indicator light can report its power status as an enumerated value:</span></span>

[!code-csharp[Enumeration for power status](~/samples/csharp/tutorials/mixins-with-interfaces/ILight.cs?name=SnippetPowerStatus)]

<span data-ttu-id="e9a3c-179">預設的執行是採用 AC 電源：</span><span class="sxs-lookup"><span data-stu-id="e9a3c-179">The default implementation assumes AC power:</span></span>

[!code-csharp[Report a default power status](~/samples/csharp/tutorials/mixins-with-interfaces/ILight.cs?name=SnippetILightInterface)]

<span data-ttu-id="e9a3c-180">這些變更會完全編譯，即使 `ExtraFancyLight` 宣告 `ILight` 介面和衍生介面的支援，`ITimerLight` 和 `IBlinkingLight`。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-180">These changes compile cleanly, even though the `ExtraFancyLight` declares support for the `ILight` interface and both derived interfaces, `ITimerLight` and `IBlinkingLight`.</span></span> <span data-ttu-id="e9a3c-181">在 `ILight` 介面中，只會宣告一個「最接近」的實作為。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-181">There's only one "closest" implementation declared in the `ILight` interface.</span></span> <span data-ttu-id="e9a3c-182">任何宣告覆寫的類別都會變成一個「最接近」的執行。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-182">Any class that declared an override would become the one "closest" implementation.</span></span> <span data-ttu-id="e9a3c-183">您在上述類別中看到的範例會已覆寫其他衍生介面的成員。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-183">You saw examples in the preceding classes that overrode the members of other derived interfaces.</span></span>

<span data-ttu-id="e9a3c-184">避免在多個衍生介面中覆寫相同的方法。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-184">Avoid overriding the same method in multiple derived interfaces.</span></span> <span data-ttu-id="e9a3c-185">如此一來，每當類別同時執行兩個衍生介面時，就會建立不明確的方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-185">Doing so creates an ambiguous method call whenever a class implements both derived interfaces.</span></span> <span data-ttu-id="e9a3c-186">編譯器無法挑選一個更好的方法，因此它會發出錯誤。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-186">The compiler can't pick a single better method so it issues an error.</span></span> <span data-ttu-id="e9a3c-187">例如，如果 `IBlinkingLight` 和 `ITimerLight` 都實作為 `PowerStatus` 的覆寫，`OverheadLight` 就必須提供更明確的覆寫。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-187">For example, if both the `IBlinkingLight` and `ITimerLight` implemented an override of `PowerStatus`, the `OverheadLight` would need to provide a more specific override.</span></span> <span data-ttu-id="e9a3c-188">否則，編譯器就無法在兩個衍生介面中的執行之間進行選擇。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-188">Otherwise, the compiler can't pick between the implementations in the two derived interfaces.</span></span> <span data-ttu-id="e9a3c-189">您通常可以藉由讓介面定義更小且專注于一項功能，來避免這種情況。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-189">You can usually avoid this situation by keeping interface definitions small and focused on one feature.</span></span> <span data-ttu-id="e9a3c-190">在此案例中，每個光線的功能都是它自己的介面;只有類別會繼承多個介面。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-190">In this scenario, each capability of a light is its own interface; multiple interfaces are only inherited by classes.</span></span>

<span data-ttu-id="e9a3c-191">這個範例會示範一個案例，您可以在其中定義可以混合成類別的離散功能。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-191">This sample shows one scenario where you can define discrete features that can be mixed into classes.</span></span> <span data-ttu-id="e9a3c-192">您可以宣告類別支援的介面，以宣告任何一組支援的功能。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-192">You declare any set of supported functionality by declaring which interfaces a class supports.</span></span> <span data-ttu-id="e9a3c-193">使用虛擬預設介面方法，可讓類別針對任何或所有介面方法使用或定義不同的執行。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-193">The use of virtual default interface methods enables classes to use or define a different implementation for any or all the interface methods.</span></span> <span data-ttu-id="e9a3c-194">此語言功能提供新的方法，讓您建立您所打造的真實世界系統模型。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-194">This language capability provides new ways to model the real-world systems you're building.</span></span> <span data-ttu-id="e9a3c-195">預設介面方法提供更清楚的方式來表達相關的類別，這些類別可能會使用這些功能的虛擬實現來混合和比對不同的功能。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-195">Default interface methods provide a clearer way to express related classes that may mix and match different features using virtual implementations of those capabilities.</span></span>
