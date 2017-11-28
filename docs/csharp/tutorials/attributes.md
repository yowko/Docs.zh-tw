---
title: "屬性 - C#"
description: "了解 C# 中屬性的運作方式。"
keywords: ".NET, .NET Core, C#, 屬性"
author: mgroves
ms.author: wiwagn
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: b152cf36-76e4-43a5-b805-1a1952e53b79
ms.openlocfilehash: dad02c64d22fe0f127057202c082680f13261d7b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="using-attributes-in-c"></a><span data-ttu-id="4be3c-104">在 C# 中使用屬性</span><span class="sxs-lookup"><span data-stu-id="4be3c-104">Using Attributes in C#</span></span> #

<span data-ttu-id="4be3c-105">屬性提供以宣告方式將資訊與程式碼相關聯的方法。</span><span class="sxs-lookup"><span data-stu-id="4be3c-105">Attributes provide a way of associating information with code in a declarative way.</span></span> <span data-ttu-id="4be3c-106">它們也可提供可重複使用的元素，以套用至各種不同的目標。</span><span class="sxs-lookup"><span data-stu-id="4be3c-106">They can also provide a reusable element that can be applied to a variety of targets.</span></span>

<span data-ttu-id="4be3c-107">以 `[Obsolete]` 屬性為例。</span><span class="sxs-lookup"><span data-stu-id="4be3c-107">Consider the `[Obsolete]` attribute.</span></span> <span data-ttu-id="4be3c-108">它可以套用至類別、結構、方法及建構函式等。</span><span class="sxs-lookup"><span data-stu-id="4be3c-108">It can be applied to classes, structs, methods, constructors, and more.</span></span> <span data-ttu-id="4be3c-109">它_宣告_元素已過時。</span><span class="sxs-lookup"><span data-stu-id="4be3c-109">It _declares_ that the element is obsolete.</span></span> <span data-ttu-id="4be3c-110">然後是由 C# 編譯器來尋找此屬性，並執行一些動作做為回應。</span><span class="sxs-lookup"><span data-stu-id="4be3c-110">It's then up to the C# compiler to look for this attribute, and do some action in response.</span></span>

<span data-ttu-id="4be3c-111">在本教學課程中，將介紹如何將屬性加入您的程式碼、如何建立及使用您自己的屬性，以及如何使用一些內建到 .NET Core 的屬性。</span><span class="sxs-lookup"><span data-stu-id="4be3c-111">In this tutorial, you'll be introduced to how to add attributes to your code, how to create and use your own attributes, and how to use some attributes that are built into .NET Core.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4be3c-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="4be3c-112">Prerequisites</span></span>
<span data-ttu-id="4be3c-113">您必須設定電腦以執行 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="4be3c-113">You’ll need to setup your machine to run .NET core.</span></span> <span data-ttu-id="4be3c-114">您可以在 [.NET Core (英文)](https://www.microsoft.com/net/core) 頁面找到安裝指示。</span><span class="sxs-lookup"><span data-stu-id="4be3c-114">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span>
<span data-ttu-id="4be3c-115">您可以在 Windows、Ubuntu Linux、macOS 或是 Docker 容器中執行此應用程式。</span><span class="sxs-lookup"><span data-stu-id="4be3c-115">You can run this application on Windows, Ubuntu Linux, macOS or in a Docker container.</span></span> <span data-ttu-id="4be3c-116">您將必須安裝慣用的程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="4be3c-116">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="4be3c-117">以下說明使用 [Visual Studio Code (英文)](https://code.visualstudio.com/)，這是開放原始碼的跨平台編輯器。</span><span class="sxs-lookup"><span data-stu-id="4be3c-117">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="4be3c-118">不過，您可以使用您熟悉的任何工具。</span><span class="sxs-lookup"><span data-stu-id="4be3c-118">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="4be3c-119">建立應用程式</span><span class="sxs-lookup"><span data-stu-id="4be3c-119">Create the Application</span></span>

<span data-ttu-id="4be3c-120">現在您已安裝完所有工具，請建立新的 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="4be3c-120">Now that you've installed all the tools, create a new .NET Core application.</span></span> <span data-ttu-id="4be3c-121">若要使用命令列產生器，請在您慣用的殼層中執行下列命令︰</span><span class="sxs-lookup"><span data-stu-id="4be3c-121">To use the command line generator, execute the following command in your favorite shell:</span></span>

`dotnet new console`

<span data-ttu-id="4be3c-122">此命令會建立最基本的 .NET Core 專案檔案。</span><span class="sxs-lookup"><span data-stu-id="4be3c-122">This command will create barebones .NET core project files.</span></span> <span data-ttu-id="4be3c-123">您將必須執行 `dotnet restore` 以還原編譯此專案所需的相依性。</span><span class="sxs-lookup"><span data-stu-id="4be3c-123">You will need to execute `dotnet restore` to restore the dependencies needed to compile this project.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="4be3c-124">若要執行這個程式，請使用 `dotnet run`。</span><span class="sxs-lookup"><span data-stu-id="4be3c-124">To execute the program, use `dotnet run`.</span></span> <span data-ttu-id="4be3c-125">您應該會在主控台看到 "Hello, World" 輸出。</span><span class="sxs-lookup"><span data-stu-id="4be3c-125">You should see "Hello, World" output to the console.</span></span>

## <a name="how-to-add-attributes-to-code"></a><span data-ttu-id="4be3c-126">如何將屬性加入至程式碼</span><span class="sxs-lookup"><span data-stu-id="4be3c-126">How to add attributes to code</span></span>

<span data-ttu-id="4be3c-127">在 C# 中，屬性是繼承自 `Attribute` 基底類別的類別。</span><span class="sxs-lookup"><span data-stu-id="4be3c-127">In C#, attributes are classes that inherit from the `Attribute` base class.</span></span> <span data-ttu-id="4be3c-128">繼承自 `Attribute` 的任何類別都能在其他程式碼片段上做為一種「標記」。</span><span class="sxs-lookup"><span data-stu-id="4be3c-128">Any class that inherits from `Attribute` can be used as a sort of "tag" on other pieces of code.</span></span>
<span data-ttu-id="4be3c-129">比方說，有一種稱為 `ObsoleteAttribute` 的屬性。</span><span class="sxs-lookup"><span data-stu-id="4be3c-129">For instance, there is an attribute called `ObsoleteAttribute`.</span></span> <span data-ttu-id="4be3c-130">這用來表示程式碼已經過時，而且不應再使用。</span><span class="sxs-lookup"><span data-stu-id="4be3c-130">This is used to signal that code is obsolete and shouldn't be used anymore.</span></span> <span data-ttu-id="4be3c-131">您可以將此屬性放在類別上，例如透過使用方括弧。</span><span class="sxs-lookup"><span data-stu-id="4be3c-131">You can place this attribute on a class, for instance, by using square brackets.</span></span>

[!code-csharp[Obsolete attribute example](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ObsoleteExample1)]  

<span data-ttu-id="4be3c-132">請注意，此類別雖稱為 `ObsoleteAttribute`，但在程式碼中只需使用 `[Obsolete]`。</span><span class="sxs-lookup"><span data-stu-id="4be3c-132">Note that while the class is called `ObsoleteAttribute`, it's only necessary to use `[Obsolete]` in the code.</span></span> <span data-ttu-id="4be3c-133">這是 C# 遵循的慣例。</span><span class="sxs-lookup"><span data-stu-id="4be3c-133">This is a convention that C# follows.</span></span>
<span data-ttu-id="4be3c-134">您也可以選擇使用完整名稱 `[ObsoleteAttribute]`。</span><span class="sxs-lookup"><span data-stu-id="4be3c-134">You can use the full name `[ObsoleteAttribute]` if you choose.</span></span>

<span data-ttu-id="4be3c-135">將類別標示為過時的時候，最好提供一些像是它*為什麼*過時及/或應改用*什麼*的資訊。</span><span class="sxs-lookup"><span data-stu-id="4be3c-135">When marking a class obsolete, it's a good idea to provide some information as to *why* it's obsolete, and/or *what* to use instead.</span></span> <span data-ttu-id="4be3c-136">要這樣做，請傳遞一個字串參數到 Obsolete 屬性。</span><span class="sxs-lookup"><span data-stu-id="4be3c-136">Do this by passing a string parameter to the Obsolete attribute.</span></span>

[!code-csharp[Obsolete attribute example with parameters](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ObsoleteExample2)]

<span data-ttu-id="4be3c-137">字串以引數的方式傳遞至 `ObsoleteAttribute` 建構函式，如同您撰寫 `var attr = new ObsoleteAttribute("some string")` 一般。</span><span class="sxs-lookup"><span data-stu-id="4be3c-137">The string is being passed as an argument to an `ObsoleteAttribute` constructor, just as if you were writing `var attr = new ObsoleteAttribute("some string")`.</span></span>

<span data-ttu-id="4be3c-138">傳遞到屬性建構函式的參數僅限於簡單型別/常值︰`bool, int, double, string, Type, enums, etc` 和這些型別的陣列。</span><span class="sxs-lookup"><span data-stu-id="4be3c-138">Parameters to an attribute constructor are limited to simple types/literals: `bool, int, double, string, Type, enums, etc` and arrays of those types.</span></span>
<span data-ttu-id="4be3c-139">您不能使用運算式或變數。</span><span class="sxs-lookup"><span data-stu-id="4be3c-139">You can not use an expression or a variable.</span></span> <span data-ttu-id="4be3c-140">您可以自由使用位置或具名參數。</span><span class="sxs-lookup"><span data-stu-id="4be3c-140">You are free to use positional or named parameters.</span></span>

## <a name="how-to-create-your-own-attribute"></a><span data-ttu-id="4be3c-141">如何建立您自己的屬性</span><span class="sxs-lookup"><span data-stu-id="4be3c-141">How to create your own attribute</span></span>

<span data-ttu-id="4be3c-142">建立屬性很簡單，只要繼承自 `Attribute` 基底類別。</span><span class="sxs-lookup"><span data-stu-id="4be3c-142">Creating an attribute is as simple as inheriting from the `Attribute` base class.</span></span>

[!code-csharp[Create your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CreateAttributeExample1)]

<span data-ttu-id="4be3c-143">之後就能在程式碼基底的其他位置使用 `[MySpecial]` (或 `[MySpecialAttribute]`) 做為屬性。</span><span class="sxs-lookup"><span data-stu-id="4be3c-143">With the above, I can now use `[MySpecial]` (or `[MySpecialAttribute]`) as an attribute elsewhere in the code base.</span></span>

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CreateAttributeExample2)]

<span data-ttu-id="4be3c-144">.NET 基底類別庫中的屬性 (如 `ObsoleteAttribute`) 會觸發編譯器中的特定行為。</span><span class="sxs-lookup"><span data-stu-id="4be3c-144">Attributes in the .NET base class library like `ObsoleteAttribute` trigger certain behaviors within the compiler.</span></span> <span data-ttu-id="4be3c-145">不過，您所建立的任何屬性僅做為中繼資料，不會在執行的屬性類別內產生任何程式碼。</span><span class="sxs-lookup"><span data-stu-id="4be3c-145">However, any attribute you create acts only as metadata, and doesn't result in any code within the attribute class being executed.</span></span> <span data-ttu-id="4be3c-146">您可以在程式碼中的其他位置對該中繼資料採取行動 (本教學課程稍後有詳細說明)。</span><span class="sxs-lookup"><span data-stu-id="4be3c-146">It's up to you to act on that metadata elsewhere in your code (more on that later in the tutorial).</span></span>

<span data-ttu-id="4be3c-147">這裡要注意的是「陷阱」。</span><span class="sxs-lookup"><span data-stu-id="4be3c-147">There is a 'gotcha' here to watch out for.</span></span> <span data-ttu-id="4be3c-148">如上所述，使用屬性時，只有特定型別可做為引數傳遞。</span><span class="sxs-lookup"><span data-stu-id="4be3c-148">As mentioned above, only certain types are allowed to be passed as arguments when using attributes.</span></span> <span data-ttu-id="4be3c-149">不過，在建立屬性型別時，C# 編譯器不會阻止您建立這些參數。</span><span class="sxs-lookup"><span data-stu-id="4be3c-149">However, when creating an attribute type, the C# compiler won't stop you from creating those parameters.</span></span> <span data-ttu-id="4be3c-150">在下列範例中，我使用編譯良好的建構函式建立了屬性。</span><span class="sxs-lookup"><span data-stu-id="4be3c-150">In the below example, I've created an attribute with a constructor that compiles just fine.</span></span>

[!code-csharp[Valid constructor used in an attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeGothca1)]

<span data-ttu-id="4be3c-151">不過，您將無法使用這個建構函式搭配屬性語法。</span><span class="sxs-lookup"><span data-stu-id="4be3c-151">However, you will be unable to use this constructor with attribute syntax.</span></span>

[!code-csharp[Invalid attempt to use the attribute constructor](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeGotcha2)]

<span data-ttu-id="4be3c-152">上述程式碼會造成編譯器錯誤，例如：`Attribute constructor parameter 'myClass' has type 'Foo', which is not a valid attribute parameter type`</span><span class="sxs-lookup"><span data-stu-id="4be3c-152">The above will cause a compiler error like `Attribute constructor parameter 'myClass' has type 'Foo', which is not a valid attribute parameter type`</span></span>

## <a name="how-to-restrict-attribute-usage"></a><span data-ttu-id="4be3c-153">如何限制屬性使用方式</span><span class="sxs-lookup"><span data-stu-id="4be3c-153">How to restrict attribute usage</span></span>

<span data-ttu-id="4be3c-154">屬性可用在許多「目標」上。</span><span class="sxs-lookup"><span data-stu-id="4be3c-154">Attributes can be used on a number of "targets".</span></span> <span data-ttu-id="4be3c-155">上述範例顯示它們使用於類別，但也可以用在：</span><span class="sxs-lookup"><span data-stu-id="4be3c-155">The above examples show them on classes, but they can also be used on:</span></span>

* <span data-ttu-id="4be3c-156">Assembly</span><span class="sxs-lookup"><span data-stu-id="4be3c-156">Assembly</span></span>
* <span data-ttu-id="4be3c-157">類別</span><span class="sxs-lookup"><span data-stu-id="4be3c-157">Class</span></span>
* <span data-ttu-id="4be3c-158">建構函式</span><span class="sxs-lookup"><span data-stu-id="4be3c-158">Constructor</span></span>
* <span data-ttu-id="4be3c-159">委派</span><span class="sxs-lookup"><span data-stu-id="4be3c-159">Delegate</span></span>
* <span data-ttu-id="4be3c-160">列舉</span><span class="sxs-lookup"><span data-stu-id="4be3c-160">Enum</span></span>
* <span data-ttu-id="4be3c-161">事件</span><span class="sxs-lookup"><span data-stu-id="4be3c-161">Event</span></span>
* <span data-ttu-id="4be3c-162">欄位</span><span class="sxs-lookup"><span data-stu-id="4be3c-162">Field</span></span>
* <span data-ttu-id="4be3c-163">GenericParameter</span><span class="sxs-lookup"><span data-stu-id="4be3c-163">GenericParameter</span></span>
* <span data-ttu-id="4be3c-164">介面</span><span class="sxs-lookup"><span data-stu-id="4be3c-164">Interface</span></span>
* <span data-ttu-id="4be3c-165">方法</span><span class="sxs-lookup"><span data-stu-id="4be3c-165">Method</span></span>
* <span data-ttu-id="4be3c-166">模組</span><span class="sxs-lookup"><span data-stu-id="4be3c-166">Module</span></span>
* <span data-ttu-id="4be3c-167">參數</span><span class="sxs-lookup"><span data-stu-id="4be3c-167">Parameter</span></span>
* <span data-ttu-id="4be3c-168">屬性</span><span class="sxs-lookup"><span data-stu-id="4be3c-168">Property</span></span>
* <span data-ttu-id="4be3c-169">ReturnValue</span><span class="sxs-lookup"><span data-stu-id="4be3c-169">ReturnValue</span></span>
* <span data-ttu-id="4be3c-170">結構</span><span class="sxs-lookup"><span data-stu-id="4be3c-170">Struct</span></span>

<span data-ttu-id="4be3c-171">當您建立屬性類別時，根據預設，C# 將允許您在任何可能的屬性目標中使用該屬性。</span><span class="sxs-lookup"><span data-stu-id="4be3c-171">When you create an attribute class, by default, C# will allow you to use that attribute on any of the possible attribute targets.</span></span> <span data-ttu-id="4be3c-172">如果您想要將您的屬性限制在特定目標，您可以在屬性類別中使用 `AttributeUsageAttribute` 來完成。</span><span class="sxs-lookup"><span data-stu-id="4be3c-172">If you want to restrict your attribute to certain targets, you can do so by using the `AttributeUsageAttribute` on your attribute class.</span></span> <span data-ttu-id="4be3c-173">沒錯，屬性中的屬性！</span><span class="sxs-lookup"><span data-stu-id="4be3c-173">That's right, an attribute on an attribute!</span></span>

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeUsageExample1)]

<span data-ttu-id="4be3c-174">如果您嘗試將上述屬性放在類別或結構以外的項目中，就會發生如下的編譯器錯誤：`Attribute 'MyAttributeForClassAndStructOnly' is not valid on this declaration type. It is only valid on 'class, struct' declarations`</span><span class="sxs-lookup"><span data-stu-id="4be3c-174">If you attempt to put the above attribute on something that's not a class or a struct, you will get a compiler error like `Attribute 'MyAttributeForClassAndStructOnly' is not valid on this declaration type. It is only valid on 'class, struct' declarations`</span></span>

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeUsageExample2)]

## <a name="how-to-use-attributes-attached-to-a-code-element"></a><span data-ttu-id="4be3c-175">如何使用附加至程式碼元素的屬性</span><span class="sxs-lookup"><span data-stu-id="4be3c-175">How to use attributes attached to a code element</span></span>

<span data-ttu-id="4be3c-176">屬性是做為中繼資料。</span><span class="sxs-lookup"><span data-stu-id="4be3c-176">Attributes act as metadata.</span></span> <span data-ttu-id="4be3c-177">在無外力介入的情況下，它們不會實際執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="4be3c-177">Without some outward force, they won't actually do anything.</span></span>

<span data-ttu-id="4be3c-178">為了尋找屬性並對其採取行動，通常需要[反射](../programming-guide/concepts/reflection.md)。</span><span class="sxs-lookup"><span data-stu-id="4be3c-178">To find and act on attributes, [Reflection](../programming-guide/concepts/reflection.md) is generally needed.</span></span> <span data-ttu-id="4be3c-179">我在本教學課程中不會深入介紹「反射」，但基本概念是「反射」可讓您在 C# 中撰寫檢查其他程式碼的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4be3c-179">I won't cover Reflection in-depth in this tutorial, but the basic idea is that Reflection allows you to write code in C# that examines other code.</span></span>

<span data-ttu-id="4be3c-180">比方說，您可以使用「反射」來取得類別的相關資訊︰</span><span class="sxs-lookup"><span data-stu-id="4be3c-180">For instance, you can use Reflection to get information about a class:</span></span> 

[!code-csharp[Getting type information with Reflection](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ReflectionExample1)]

<span data-ttu-id="4be3c-181">該程式碼會印出類似以下的內容：`The assembly qualified name of MyClass is ConsoleApplication.MyClass, attributes, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null`</span><span class="sxs-lookup"><span data-stu-id="4be3c-181">That will print out something like: `The assembly qualified name of MyClass is ConsoleApplication.MyClass, attributes, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null`</span></span>

<span data-ttu-id="4be3c-182">一旦您擁有 `TypeInfo` 物件 (或 `MemberInfo`、`FieldInfo` 等)，就可以使用 `GetCustomAttributes` 方法。</span><span class="sxs-lookup"><span data-stu-id="4be3c-182">Once you have a `TypeInfo` object (or a `MemberInfo`, `FieldInfo`, etc), you can use the `GetCustomAttributes` method.</span></span> <span data-ttu-id="4be3c-183">這會傳回 `Attribute` 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="4be3c-183">This will return a collection of `Attribute` objects.</span></span>
<span data-ttu-id="4be3c-184">您也可以使用 `GetCustomAttribute` 並指定一個「屬性」型別。</span><span class="sxs-lookup"><span data-stu-id="4be3c-184">You can also use `GetCustomAttribute` and specify an Attribute type.</span></span>

<span data-ttu-id="4be3c-185">以下是在 `MyClass` 的 `MemberInfo` 執行個體上使用 `GetCustomAttributes` 的範例 (我們之前已看到其中有一個 `[Obsolete]` 屬性)。</span><span class="sxs-lookup"><span data-stu-id="4be3c-185">Here's an example of using `GetCustomAttributes` on a `MemberInfo` instance for `MyClass` (which we saw earlier has an `[Obsolete]` attribute on it).</span></span>

[!code-csharp[Getting type information with Reflection](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ReflectionExample2)]

<span data-ttu-id="4be3c-186">該命令將列印至主控台︰`Attribute on MyClass: ObsoleteAttribute`。</span><span class="sxs-lookup"><span data-stu-id="4be3c-186">That will print to console: `Attribute on MyClass: ObsoleteAttribute`.</span></span> <span data-ttu-id="4be3c-187">嘗試將其他屬性加入 `MyClass`。</span><span class="sxs-lookup"><span data-stu-id="4be3c-187">Try adding other attributes to `MyClass`.</span></span>

<span data-ttu-id="4be3c-188">務必注意的是，這些 `Attribute` 物件會延遲具現化。</span><span class="sxs-lookup"><span data-stu-id="4be3c-188">It's important to note that these `Attribute` objects are instantiated lazily.</span></span> <span data-ttu-id="4be3c-189">也就是說，在您使用 `GetCustomAttribute` 或 `GetCustomAttributes` 之前，它們將不會具現化。</span><span class="sxs-lookup"><span data-stu-id="4be3c-189">That is, they won't be instantiated until you use `GetCustomAttribute` or `GetCustomAttributes`.</span></span>
<span data-ttu-id="4be3c-190">它們也會每次具現化。</span><span class="sxs-lookup"><span data-stu-id="4be3c-190">They are also instantiated each time.</span></span> <span data-ttu-id="4be3c-191">在一個資料列中呼叫 `GetCustomAttributes` 兩次，將會傳回兩個不同的 `ObsoleteAttribute` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="4be3c-191">Calling `GetCustomAttributes` twice in a row will return two different instances of `ObsoleteAttribute`.</span></span>

## <a name="common-attributes-in-the-base-class-library-bcl"></a><span data-ttu-id="4be3c-192">基底類別庫 (BCL) 中的通用屬性</span><span class="sxs-lookup"><span data-stu-id="4be3c-192">Common attributes in the base class library (BCL)</span></span>

<span data-ttu-id="4be3c-193">許多工具和架構都會使用屬性。</span><span class="sxs-lookup"><span data-stu-id="4be3c-193">Attributes are used by many tools and frameworks.</span></span> <span data-ttu-id="4be3c-194">NUnit 使用 NUnit 測試執行器使用的屬性 (例如 `[Test]` 和 `[TestFixture]`)。</span><span class="sxs-lookup"><span data-stu-id="4be3c-194">NUnit uses attributes like `[Test]` and `[TestFixture]` that are used by the NUnit test runner.</span></span> <span data-ttu-id="4be3c-195">ASP.NET MVC 使用 `[Authorize]` 之類的屬性，並提供動作篩選架構來執行關於 MVC 動作的交叉關注。</span><span class="sxs-lookup"><span data-stu-id="4be3c-195">ASP.NET MVC uses attributes like `[Authorize]` and provides an action filter framework to perform cross-cutting concerns on MVC actions.</span></span> <span data-ttu-id="4be3c-196">[PostSharp](https://www.postsharp.net) 使用屬性語法以允許 C# 中的層面導向程式設計。</span><span class="sxs-lookup"><span data-stu-id="4be3c-196">[PostSharp](https://www.postsharp.net) uses the attribute syntax to allow aspect-oriented programming in C#.</span></span>

<span data-ttu-id="4be3c-197">以下是幾個值得注意的屬性，內建於 .NET Core 基底類別庫中︰</span><span class="sxs-lookup"><span data-stu-id="4be3c-197">Here are a few notable attributes built into the .NET Core base class libraries:</span></span>

* <span data-ttu-id="4be3c-198">`[Obsolete]`.</span><span class="sxs-lookup"><span data-stu-id="4be3c-198">`[Obsolete]`.</span></span> <span data-ttu-id="4be3c-199">此屬性使用於上述範例中，且存在於 `System` 命名空間。</span><span class="sxs-lookup"><span data-stu-id="4be3c-199">This one was used in the above examples, and it lives in the `System` namespace.</span></span> <span data-ttu-id="4be3c-200">提供有關變更的程式碼基底的宣告式文件會很有用。</span><span class="sxs-lookup"><span data-stu-id="4be3c-200">It is useful to provide declarative documentation about a changing code base.</span></span> <span data-ttu-id="4be3c-201">訊息可以字串的形式提供，使用另一個布林值參數可以從編譯器警告提升至編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="4be3c-201">A message can be provided in the form of a string, and another boolean parameter can be used to escalate from a compiler warning to a compiler error.</span></span>

* <span data-ttu-id="4be3c-202">`[Conditional]`.</span><span class="sxs-lookup"><span data-stu-id="4be3c-202">`[Conditional]`.</span></span> <span data-ttu-id="4be3c-203">此屬性位於 `System.Diagnostics` 命名空間。</span><span class="sxs-lookup"><span data-stu-id="4be3c-203">This attribute is in the `System.Diagnostics` namespace.</span></span> <span data-ttu-id="4be3c-204">這個屬性可以套用至方法 (或屬性類別)。</span><span class="sxs-lookup"><span data-stu-id="4be3c-204">This attribute can be applied to methods (or attribute classes).</span></span> <span data-ttu-id="4be3c-205">您必須傳遞字串給建構函式。</span><span class="sxs-lookup"><span data-stu-id="4be3c-205">You must pass a string to the constructor.</span></span>
<span data-ttu-id="4be3c-206">如果該字串符合 `#define` 指示詞，C# 編譯器會移除對該方法的任何呼叫 (但非方法本身)。</span><span class="sxs-lookup"><span data-stu-id="4be3c-206">If that string matches a `#define` directive, then any calls to that method (but not the method itself) will be removed by the C# compiler.</span></span> <span data-ttu-id="4be3c-207">這通常用於偵錯 (診斷) 用途。</span><span class="sxs-lookup"><span data-stu-id="4be3c-207">Typically this is used for debugging (diagnostics) purposes.</span></span>

* <span data-ttu-id="4be3c-208">`[CallerMemberName]`.</span><span class="sxs-lookup"><span data-stu-id="4be3c-208">`[CallerMemberName]`.</span></span> <span data-ttu-id="4be3c-209">這個屬性可以用於參數，並存在 `System.Runtime.CompilerServices` 命名空間中。</span><span class="sxs-lookup"><span data-stu-id="4be3c-209">This attribute can be used on parameters, and lives in the `System.Runtime.CompilerServices` namespace.</span></span> <span data-ttu-id="4be3c-210">這個屬性可用來插入呼叫另一個方法之方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="4be3c-210">This is an attribute that is used to inject the name of the method that is calling another method.</span></span> <span data-ttu-id="4be3c-211">在各種 UI 架構中實作 INotifyPropertyChanged 時，這通常做為消除 'magic strings' 的方法。</span><span class="sxs-lookup"><span data-stu-id="4be3c-211">This is typically used as a way to eliminate 'magic strings' when implementing INotifyPropertyChanged in various UI frameworks.</span></span> <span data-ttu-id="4be3c-212">範例如下：</span><span class="sxs-lookup"><span data-stu-id="4be3c-212">As an example:</span></span>

[!code-csharp[Using CallerMemberName when implementing INotifyPropertyChanged](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CallerMemberName1)]

<span data-ttu-id="4be3c-213">在上述程式碼中，您不必使用常值 `"Name"` 字串。</span><span class="sxs-lookup"><span data-stu-id="4be3c-213">In the above code, you don't have to have a literal `"Name"` string.</span></span> <span data-ttu-id="4be3c-214">這有助於避免打字錯誤相關的問題，也可使重構/重新命名更順暢。</span><span class="sxs-lookup"><span data-stu-id="4be3c-214">This can help prevent typo-related bugs and also makes for smoother refactoring/renaming.</span></span>

## <a name="summary"></a><span data-ttu-id="4be3c-215">總結</span><span class="sxs-lookup"><span data-stu-id="4be3c-215">Summary</span></span>

<span data-ttu-id="4be3c-216">屬性能為 C# 提供宣告式能力。</span><span class="sxs-lookup"><span data-stu-id="4be3c-216">Attributes bring declarative power to C#.</span></span> <span data-ttu-id="4be3c-217">但它們是做為中繼資料的一種程式碼，無法自行運作。</span><span class="sxs-lookup"><span data-stu-id="4be3c-217">But they are a form of code as meta-data, and don't act by themselves.</span></span>
