---
title: C# 版本控制 - C# 手冊
description: 了解 C# 和 .NET 的版本控制運作方式
ms.date: 01/08/2017
ms.technology: csharp-advanced-concepts
ms.assetid: aa8732d7-5cd0-46e1-994a-78017f20d861
ms.openlocfilehash: dc192337e4eaa5f9f1d6509ea8c15deeac34a48c
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645461"
---
# <a name="versioning-in-c"></a><span data-ttu-id="9fa0b-103">C\# 中的版本控制</span><span class="sxs-lookup"><span data-stu-id="9fa0b-103">Versioning in C\#</span></span>

<span data-ttu-id="9fa0b-104">在本教學課程中，您會了解版本控制在 .NET 中的意義。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-104">In this tutorial you'll learn what versioning means in .NET.</span></span> <span data-ttu-id="9fa0b-105">您也會了解進行程式庫版本控制以及升級成新版程式庫時要考量的因素。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-105">You'll also learn the factors to consider when versioning your library as well as upgrading to a new version of a library.</span></span>

## <a name="authoring-libraries"></a><span data-ttu-id="9fa0b-106">撰寫程式庫</span><span class="sxs-lookup"><span data-stu-id="9fa0b-106">Authoring Libraries</span></span>

<span data-ttu-id="9fa0b-107">身為已建立公用用途 .NET 程式庫的開發人員，您很可能經歷過必須推出新更新的情況。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-107">As a developer who has created .NET libraries for public use, you've most likely been in situations where you have to roll out new updates.</span></span> <span data-ttu-id="9fa0b-108">如何執行此程序影響重大，因為您需要確保現有程式碼能夠順暢轉換到新版文件庫。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-108">How you go about this process matters a lot as you need to ensure that there's a seamless transition of existing code to the new version of your library.</span></span> <span data-ttu-id="9fa0b-109">以下是建立新版本時要考量的幾件事︰</span><span class="sxs-lookup"><span data-stu-id="9fa0b-109">Here are several things to consider when creating a new release:</span></span>

### <a name="semantic-versioning"></a><span data-ttu-id="9fa0b-110">語意版本控制</span><span class="sxs-lookup"><span data-stu-id="9fa0b-110">Semantic Versioning</span></span>

<span data-ttu-id="9fa0b-111">[語意版本控制](https://semver.org/) (簡稱為 SemVer) 是文件庫各版本套用的命名慣例，表示特定的重大事件。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-111">[Semantic versioning](https://semver.org/) (SemVer for short) is a naming convention applied to versions of your library to signify specific milestone events.</span></span>
<span data-ttu-id="9fa0b-112">理想情況是，您提供給文件庫的版本資訊應該能幫助開發人員判斷其與使用同一文件庫舊版本的專案是否相容。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-112">Ideally, the version information you give your library should help developers determine the compatibility with their projects that make use of older versions of that same library.</span></span>

<span data-ttu-id="9fa0b-113">SemVer 最基本的方法是 3 元件格式 `MAJOR.MINOR.PATCH`，其中：</span><span class="sxs-lookup"><span data-stu-id="9fa0b-113">The most basic approach to SemVer is the 3 component format `MAJOR.MINOR.PATCH`, where:</span></span>

- <span data-ttu-id="9fa0b-114">當您進行不相容的 API 變更時會遞增 `MAJOR`</span><span class="sxs-lookup"><span data-stu-id="9fa0b-114">`MAJOR` is incremented when you make incompatible API changes</span></span>
- <span data-ttu-id="9fa0b-115">當您以回溯相容方式新增功能時會遞增 `MINOR`</span><span class="sxs-lookup"><span data-stu-id="9fa0b-115">`MINOR` is incremented when you add functionality in a backwards-compatible manner</span></span>
- <span data-ttu-id="9fa0b-116">當您進行回溯相容的 Bug 修正時會遞增 `PATCH`</span><span class="sxs-lookup"><span data-stu-id="9fa0b-116">`PATCH` is incremented when you make backwards-compatible bug fixes</span></span>

<span data-ttu-id="9fa0b-117">將版本資訊套用至您的 .NET 文件庫時，還有其他方式可以指定其他狀況，例如發行前版本等等。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-117">There are also ways to specify other scenarios like pre-release versions etc. when applying version information to your .NET library.</span></span>

### <a name="backwards-compatibility"></a><span data-ttu-id="9fa0b-118">回溯相容性</span><span class="sxs-lookup"><span data-stu-id="9fa0b-118">Backwards Compatibility</span></span>

<span data-ttu-id="9fa0b-119">當您發行新版文件庫時，與舊版相容會是您的主要考量之一。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-119">As you release new versions of your library, backwards compatibility with previous versions will most likely be one of your major concerns.</span></span>
<span data-ttu-id="9fa0b-120">如果相依於前一版的程式碼在重新編譯時，能在新版正常運作，新舊兩版的文件庫就是來源相容。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-120">A new version of your library is source compatible with a previous version if code that depends on the previous version can, when recompiled, work with the new version.</span></span>
<span data-ttu-id="9fa0b-121">如果相依於舊版的應用程式在未重新編譯的情況下，能在新版正常運作，新舊兩版的文件庫就是二進位相容。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-121">A new version of your library is binary compatible if an application that depended on the old version can, without recompilation, work with the new version.</span></span>

<span data-ttu-id="9fa0b-122">以下是嘗試維持與舊版文件庫的相容性時要考慮的一些事項︰</span><span class="sxs-lookup"><span data-stu-id="9fa0b-122">Here are some things to consider when trying to maintain backwards compatibility with older versions of your library:</span></span>

- <span data-ttu-id="9fa0b-123">虛擬方法︰當您在新版本中將虛擬方法變成非虛擬，表示必須更新覆寫該方法的專案。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-123">Virtual methods: When you make a virtual method non-virtual in your new version it means that projects that override that method will have to be updated.</span></span> <span data-ttu-id="9fa0b-124">這是一項極重大的變更，強烈建議您不要這麼做。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-124">This is a huge breaking change and is strongly discouraged.</span></span>
- <span data-ttu-id="9fa0b-125">方法簽名:當更新方法行為要求您更改其簽名時,應改為創建重載,以便調用該方法的代碼仍然有效。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-125">Method signatures: When updating a method behavior requires you to change its signature as well, you should instead create an overload so that code calling into that method will still work.</span></span>
<span data-ttu-id="9fa0b-126">您可以一直使用舊的方法簽章呼叫新方法簽章，讓實作保持一致。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-126">You can always manipulate the old method signature to call into the new method signature so that implementation remains consistent.</span></span>
- <span data-ttu-id="9fa0b-127">[Obsolete 屬性](language-reference/attributes/general.md#obsolete-attribute)︰您可以在程式碼中使用這個屬性，指定未來版本中要取代及可能移除的類別或類別成員。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-127">[Obsolete attribute](language-reference/attributes/general.md#obsolete-attribute): You can use this attribute in your code to specify classes or class members that are deprecated and likely to be removed in future versions.</span></span> <span data-ttu-id="9fa0b-128">這可確保使用您文件庫的開發人員在面對重大變更時有更完善的準備。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-128">This ensures developers utilizing your library are better prepared for breaking changes.</span></span>
- <span data-ttu-id="9fa0b-129">選擇性的方法引數︰當您將先前的選擇性方法引數變為強制，或是變更其預設值後，所有不提供這些引數的程式碼都需要更新。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-129">Optional Method Arguments: When you make previously optional method arguments compulsory or change their default value then all code that does not supply those arguments will need to be updated.</span></span>

> [!NOTE]
> <span data-ttu-id="9fa0b-130">使強制參數可選應該沒有什麼效果,特別是如果它不改變方法的行為。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-130">Making compulsory arguments optional should have very little effect especially if it doesn't change the method's behavior.</span></span>

<span data-ttu-id="9fa0b-131">使用者升級至新版文件庫的過程愈簡單，他們就愈可能快速升級。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-131">The easier you make it for your users to upgrade to the new version of your library, the more likely that they will upgrade sooner.</span></span>

### <a name="application-configuration-file"></a><span data-ttu-id="9fa0b-132">應用程式組態檔</span><span class="sxs-lookup"><span data-stu-id="9fa0b-132">Application Configuration File</span></span>

<span data-ttu-id="9fa0b-133">身為 .NET 開發人員，您在大多數的專案類型中，有很大的機會遇到[`app.config` 檔案](../framework/configure-apps/file-schema/index.md)。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-133">As a .NET developer there's a very high chance you've encountered [the `app.config` file](../framework/configure-apps/file-schema/index.md) present in most project types.</span></span>
<span data-ttu-id="9fa0b-134">這個簡單的組態檔要很長時間才能改善推出新的更新。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-134">This simple configuration file can go a long way into improving the rollout of new updates.</span></span> <span data-ttu-id="9fa0b-135">通常,您應該以可能定期更改的資訊存儲`app.config`在 檔中的方式設計庫,這樣,當此類資訊更新時,舊版本的配置檔只需替換為新版本的配置檔,而無需重新編譯庫。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-135">You should generally design your libraries in such a way that information that is likely to change regularly is stored in the `app.config` file, this way when such information is updated, the config file of older versions just needs to be replaced with the new one without the need for recompilation of the library.</span></span>

## <a name="consuming-libraries"></a><span data-ttu-id="9fa0b-136">使用文件庫</span><span class="sxs-lookup"><span data-stu-id="9fa0b-136">Consuming Libraries</span></span>

<span data-ttu-id="9fa0b-137">身為使用其他開發人員所組建的 .NET 文件庫的開發人員，您很清楚新版文件庫可能無法與您的專案完全相容，而您可能必須經常更新自己的程式碼，才能使用這些變更。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-137">As a developer that consumes .NET libraries built by other developers you're most likely aware that a new version of a library might not be fully compatible with your project and you might often find yourself having to update your code to work with those changes.</span></span>

<span data-ttu-id="9fa0b-138">幸運的是,C# 和 .NET 生態系統附帶了一些功能和技術,使我們能夠輕鬆更新應用,以便使用新版本的庫,這些庫可能會帶來重大更改。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-138">Lucky for you, C# and the .NET ecosystem comes with features and techniques that allow us to easily update our app to work with new versions of libraries that might introduce breaking changes.</span></span>

### <a name="assembly-binding-redirection"></a><span data-ttu-id="9fa0b-139">組件繫結重新導向</span><span class="sxs-lookup"><span data-stu-id="9fa0b-139">Assembly Binding Redirection</span></span>

<span data-ttu-id="9fa0b-140">您可以使用*app.config*檔案更新應用使用的庫版本。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-140">You can use the *app.config* file to update the version of a library your app uses.</span></span> <span data-ttu-id="9fa0b-141">通過添加所謂的[*綁定重定向*](../framework/configure-apps/redirect-assembly-versions.md),可以使用新的庫版本,而無需重新編譯你的應用。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-141">By adding what is called a [*binding redirect*](../framework/configure-apps/redirect-assembly-versions.md), you can use the new library version without having to recompile your app.</span></span> <span data-ttu-id="9fa0b-142">下面的範例展示如何更新應用的應用 *.config*檔,`1.0.1`以使用修`ReferencedLibrary`補程式 版本,而不是`1.0.0`最初編譯 的版本。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-142">The following example shows how you would update your app's *app.config* file to use the `1.0.1` patch version of `ReferencedLibrary` instead of the `1.0.0` version it was originally compiled with.</span></span>

```xml
<dependentAssembly>
    <assemblyIdentity name="ReferencedLibrary" publicKeyToken="32ab4ba45e0a69a1" culture="en-us" />
    <bindingRedirect oldVersion="1.0.0" newVersion="1.0.1" />
</dependentAssembly>
```

> [!NOTE]
> <span data-ttu-id="9fa0b-143">新版 `ReferencedLibrary` 與您的應用程式必須是二進位相容，才能使用這個方法。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-143">This approach will only work if the new version of `ReferencedLibrary` is binary compatible with your app.</span></span>
> <span data-ttu-id="9fa0b-144">如需決定相容性時需要留意的變更，請參閱前文的[回溯相容性](#backwards-compatibility)一節。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-144">See the [Backwards Compatibility](#backwards-compatibility) section above for changes to look out for when determining compatibility.</span></span>

### <a name="new"></a><span data-ttu-id="9fa0b-145">new</span><span class="sxs-lookup"><span data-stu-id="9fa0b-145">new</span></span>

<span data-ttu-id="9fa0b-146">您使用 `new` 修飾詞隱藏繼承的基底類別成員。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-146">You use the `new` modifier to hide inherited members of a base class.</span></span> <span data-ttu-id="9fa0b-147">這是衍生類別可以回應基底類別更新的一種方式。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-147">This is one way derived classes can respond to updates in base classes.</span></span>

<span data-ttu-id="9fa0b-148">請使用以下範例：</span><span class="sxs-lookup"><span data-stu-id="9fa0b-148">Take the following example:</span></span>

[!code-csharp[Sample usage of the 'new' modifier](~/samples/snippets/csharp/versioning/new/Program.cs#sample)]

<span data-ttu-id="9fa0b-149">**輸出**</span><span class="sxs-lookup"><span data-stu-id="9fa0b-149">**Output**</span></span>

```console
A base method
A derived method
```

<span data-ttu-id="9fa0b-150">您在上例中可以看到 `DerivedClass` 如何隱藏出現在 `BaseClass` 中的 `MyMethod` 方法。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-150">From the example above you can see how `DerivedClass` hides the `MyMethod` method present in `BaseClass`.</span></span>
<span data-ttu-id="9fa0b-151">這表示，當新版文件庫中的基底類別新增您衍生類別中已有的成員時，您只要對衍生類別成員使用 `new` 修飾詞，就可以隱藏基底類別成員。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-151">This means that when a base class in the new version of a library adds a member that already exists in your derived class, you can simply use the `new` modifier on your derived class member to hide the base class member.</span></span>

<span data-ttu-id="9fa0b-152">未指定任何 `new` 修飾詞時，衍生類別預設會隱藏基底類別中發生衝突的成員，雖然會產生編譯器警告，但程式碼仍會編譯。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-152">When no `new` modifier is specified, a derived class will by default hide conflicting members in a base class, although a compiler warning will be generated the code will still compile.</span></span> <span data-ttu-id="9fa0b-153">這表示，只要將新成員新增至現有的類別，即可讓新版文件庫與與相依於它的程式碼為來源和二進位相容。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-153">This means that simply adding new members to an existing class makes that new version of your library both source and binary compatible with code that depends on it.</span></span>

### <a name="override"></a><span data-ttu-id="9fa0b-154">override</span><span class="sxs-lookup"><span data-stu-id="9fa0b-154">override</span></span>

<span data-ttu-id="9fa0b-155">`override` 修飾詞表示衍生的實作會擴充基底類別成員的實作，而非隱藏它。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-155">The `override` modifier means a derived implementation extends the implementation of a base class member rather than hides it.</span></span> <span data-ttu-id="9fa0b-156">基底類別成員需要套用 `virtual` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-156">The base class member needs to have the `virtual` modifier applied to it.</span></span>

[!code-csharp[Sample usage of the 'override' modifier](../../samples/snippets/csharp/versioning/override/Program.cs#sample)]

<span data-ttu-id="9fa0b-157">**輸出**</span><span class="sxs-lookup"><span data-stu-id="9fa0b-157">**Output**</span></span>

```console
Base Method One: Method One
Derived Method One: Derived Method One
```

<span data-ttu-id="9fa0b-158">`override` 修飾詞會在編譯期間評估，如果編譯器找不到要覆寫的虛擬成員，它會擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-158">The `override` modifier is evaluated at compile time and the compiler will throw an error if it doesn't find a virtual member to override.</span></span>

<span data-ttu-id="9fa0b-159">您對所討論技術的瞭解以及您對使用它們的情況的理解,將大有作為,從而有助於緩解庫版本之間的過渡。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-159">Your knowledge of the discussed techniques and your understanding of the situations in which to use them, will go a long way towards easing the transition between versions of a library.</span></span>
