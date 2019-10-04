---
title: C# 版本控制 - C# 手冊
description: 了解 C# 和 .NET 的版本控制運作方式
ms.date: 01/08/2017
ms.assetid: aa8732d7-5cd0-46e1-994a-78017f20d861
ms.openlocfilehash: dcfe373312b88c8ddd8587e27c566a90b25e3c13
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834050"
---
# <a name="versioning-in-c"></a><span data-ttu-id="94b46-103">C\# 中的版本控制</span><span class="sxs-lookup"><span data-stu-id="94b46-103">Versioning in C\#</span></span>

<span data-ttu-id="94b46-104">在本教學課程中，您會了解版本控制在 .NET 中的意義。</span><span class="sxs-lookup"><span data-stu-id="94b46-104">In this tutorial you'll learn what versioning means in .NET.</span></span> <span data-ttu-id="94b46-105">您也會了解進行程式庫版本控制以及升級成新版程式庫時要考量的因素。</span><span class="sxs-lookup"><span data-stu-id="94b46-105">You'll also learn the factors to consider when versioning your library as well as upgrading to a new version of a library.</span></span>

## <a name="authoring-libraries"></a><span data-ttu-id="94b46-106">撰寫程式庫</span><span class="sxs-lookup"><span data-stu-id="94b46-106">Authoring Libraries</span></span>

<span data-ttu-id="94b46-107">身為已建立公用用途 .NET 程式庫的開發人員，您很可能經歷過必須推出新更新的情況。</span><span class="sxs-lookup"><span data-stu-id="94b46-107">As a developer who has created .NET libraries for public use, you've most likely been in situations where you have to roll out new updates.</span></span> <span data-ttu-id="94b46-108">如何執行此程序影響重大，因為您需要確保現有程式碼能夠順暢轉換到新版文件庫。</span><span class="sxs-lookup"><span data-stu-id="94b46-108">How you go about this process matters a lot as you need to ensure that there's a seamless transition of existing code to the new version of your library.</span></span> <span data-ttu-id="94b46-109">以下是建立新版本時要考量的幾件事︰</span><span class="sxs-lookup"><span data-stu-id="94b46-109">Here are several things to consider when creating a new release:</span></span>

### <a name="semantic-versioning"></a><span data-ttu-id="94b46-110">語意版本控制</span><span class="sxs-lookup"><span data-stu-id="94b46-110">Semantic Versioning</span></span>

<span data-ttu-id="94b46-111">[語意版本控制](https://semver.org/) (簡稱為 SemVer) 是文件庫各版本套用的命名慣例，表示特定的重大事件。</span><span class="sxs-lookup"><span data-stu-id="94b46-111">[Semantic versioning](https://semver.org/) (SemVer for short) is a naming convention applied to versions of your library to signify specific milestone events.</span></span>
<span data-ttu-id="94b46-112">理想情況是，您提供給文件庫的版本資訊應該能幫助開發人員判斷其與使用同一文件庫舊版本的專案是否相容。</span><span class="sxs-lookup"><span data-stu-id="94b46-112">Ideally, the version information you give your library should help developers determine the compatibility with their projects that make use of older versions of that same library.</span></span>

<span data-ttu-id="94b46-113">SemVer 最基本的方法是 3 元件格式 `MAJOR.MINOR.PATCH`，其中：</span><span class="sxs-lookup"><span data-stu-id="94b46-113">The most basic approach to SemVer is the 3 component format `MAJOR.MINOR.PATCH`, where:</span></span>

- <span data-ttu-id="94b46-114">當您進行不相容的 API 變更時會遞增 `MAJOR`</span><span class="sxs-lookup"><span data-stu-id="94b46-114">`MAJOR` is incremented when you make incompatible API changes</span></span>
- <span data-ttu-id="94b46-115">當您以回溯相容方式新增功能時會遞增 `MINOR`</span><span class="sxs-lookup"><span data-stu-id="94b46-115">`MINOR` is incremented when you add functionality in a backwards-compatible manner</span></span>
- <span data-ttu-id="94b46-116">當您進行回溯相容的 Bug 修正時會遞增 `PATCH`</span><span class="sxs-lookup"><span data-stu-id="94b46-116">`PATCH` is incremented when you make backwards-compatible bug fixes</span></span>

<span data-ttu-id="94b46-117">將版本資訊套用至您的 .NET 文件庫時，還有其他方式可以指定其他狀況，例如發行前版本等等。</span><span class="sxs-lookup"><span data-stu-id="94b46-117">There are also ways to specify other scenarios like pre-release versions etc. when applying version information to your .NET library.</span></span>

### <a name="backwards-compatibility"></a><span data-ttu-id="94b46-118">回溯相容性</span><span class="sxs-lookup"><span data-stu-id="94b46-118">Backwards Compatibility</span></span>

<span data-ttu-id="94b46-119">當您發行新版文件庫時，與舊版相容會是您的主要考量之一。</span><span class="sxs-lookup"><span data-stu-id="94b46-119">As you release new versions of your library, backwards compatibility with previous versions will most likely be one of your major concerns.</span></span>
<span data-ttu-id="94b46-120">如果相依於前一版的程式碼在重新編譯時，能在新版正常運作，新舊兩版的文件庫就是來源相容。</span><span class="sxs-lookup"><span data-stu-id="94b46-120">A new version of your library is source compatible with a previous version if code that depends on the previous version can, when recompiled, work with the new version.</span></span> <span data-ttu-id="94b46-121">如果相依於舊版的應用程式在未重新編譯的情況下，能在新版正常運作，新舊兩版的文件庫就是二進位相容。</span><span class="sxs-lookup"><span data-stu-id="94b46-121">A new version of your library is binary compatible if an application that depended on the old version can, without recompilation, work with the new version.</span></span>

<span data-ttu-id="94b46-122">以下是嘗試維持與舊版文件庫的相容性時要考慮的一些事項︰</span><span class="sxs-lookup"><span data-stu-id="94b46-122">Here are some things to consider when trying to maintain backwards compatibility with older versions of your library:</span></span>

- <span data-ttu-id="94b46-123">虛擬方法：當您在新版本中將虛擬方法變成非虛擬，表示必須更新覆寫該方法的專案。</span><span class="sxs-lookup"><span data-stu-id="94b46-123">Virtual methods: When you make a virtual method non-virtual in your new version it means that projects that override that method will have to be updated.</span></span> <span data-ttu-id="94b46-124">這是一項極重大的變更，強烈建議您不要這麼做。</span><span class="sxs-lookup"><span data-stu-id="94b46-124">This is a huge breaking change and is strongly discouraged.</span></span>
- <span data-ttu-id="94b46-125">方法簽章：更新方法行為時，如果您也需要變更其簽章，您應該改為建立多載，讓呼叫該方法的程式碼仍然可以運作。</span><span class="sxs-lookup"><span data-stu-id="94b46-125">Method signatures: When updating a method behavior requires you to change its signature as well, you should instead create an overload so that code calling into that method will still work.</span></span>
<span data-ttu-id="94b46-126">您可以一直使用舊的方法簽章呼叫新方法簽章，讓實作保持一致。</span><span class="sxs-lookup"><span data-stu-id="94b46-126">You can always manipulate the old method signature to call into the new method signature so that implementation remains consistent.</span></span>
- <span data-ttu-id="94b46-127">[Obsolete 屬性](programming-guide/concepts/attributes/common-attributes.md#Obsolete)：您可以在程式碼中使用這個屬性，指定未來版本中要淘汰及可能移除的類別或類別成員。</span><span class="sxs-lookup"><span data-stu-id="94b46-127">[Obsolete attribute](programming-guide/concepts/attributes/common-attributes.md#Obsolete): You can use this attribute in your code to specify classes or class members that are deprecated and likely to be removed in future versions.</span></span> <span data-ttu-id="94b46-128">這可確保使用您文件庫的開發人員在面對重大變更時有更完善的準備。</span><span class="sxs-lookup"><span data-stu-id="94b46-128">This ensures developers utilizing your library are better prepared for breaking changes.</span></span>
- <span data-ttu-id="94b46-129">選擇性方法引數：當您將先前的選擇性方法引數變為強制，或是變更其預設值後，所有不提供這些引數的程式碼都需要更新。</span><span class="sxs-lookup"><span data-stu-id="94b46-129">Optional Method Arguments: When you make previously optional method arguments compulsory or change their default value then all code that does not supply those arguments will need to be updated.</span></span>

> [!NOTE]
> <span data-ttu-id="94b46-130">將強制引數設為選擇性的效果，特別是當它不會變更方法的行為時。</span><span class="sxs-lookup"><span data-stu-id="94b46-130">Making compulsory arguments optional should have very little effect especially if it doesn't change the method's behavior.</span></span>

<span data-ttu-id="94b46-131">使用者升級至新版文件庫的過程愈簡單，他們就愈可能快速升級。</span><span class="sxs-lookup"><span data-stu-id="94b46-131">The easier you make it for your users to upgrade to the new version of your library, the more likely that they will upgrade sooner.</span></span>

### <a name="application-configuration-file"></a><span data-ttu-id="94b46-132">應用程式組態檔</span><span class="sxs-lookup"><span data-stu-id="94b46-132">Application Configuration File</span></span>

<span data-ttu-id="94b46-133">身為 .NET 開發人員，您在大多數的專案類型中，有很大的機會遇到[`app.config` 檔案](../framework/configure-apps/file-schema/index.md)。</span><span class="sxs-lookup"><span data-stu-id="94b46-133">As a .NET developer there's a very high chance you've encountered [the `app.config` file](../framework/configure-apps/file-schema/index.md) present in most project types.</span></span>
<span data-ttu-id="94b46-134">這個簡單的組態檔要很長時間才能改善推出新的更新。</span><span class="sxs-lookup"><span data-stu-id="94b46-134">This simple configuration file can go a long way into improving the rollout of new updates.</span></span> <span data-ttu-id="94b46-135">一般來說，您應該以這種方式設計程式庫，讓可能定期變更的資訊儲存在 @no__t 0 檔案中，如此一來，當更新這類資訊時，較舊版本的設定檔就必須以新的檔案取代，而不需要需要重新編譯程式庫。</span><span class="sxs-lookup"><span data-stu-id="94b46-135">You should generally design your libraries in such a way that information that is likely to change regularly is stored in the `app.config` file, this way when such information is updated, the config file of older versions just needs to be replaced with the new one without the need for recompilation of the library.</span></span>

## <a name="consuming-libraries"></a><span data-ttu-id="94b46-136">使用文件庫</span><span class="sxs-lookup"><span data-stu-id="94b46-136">Consuming Libraries</span></span>

<span data-ttu-id="94b46-137">身為使用其他開發人員所組建的 .NET 文件庫的開發人員，您很清楚新版文件庫可能無法與您的專案完全相容，而您可能必須經常更新自己的程式碼，才能使用這些變更。</span><span class="sxs-lookup"><span data-stu-id="94b46-137">As a developer that consumes .NET libraries built by other developers you're most likely aware that a new version of a library might not be fully compatible with your project and you might often find yourself having to update your code to work with those changes.</span></span>

<span data-ttu-id="94b46-138">幸運的是， C# .net 生態系統提供了一些功能和技術，可讓我們輕鬆更新應用程式，以使用可能會造成重大變更的新程式庫版本。</span><span class="sxs-lookup"><span data-stu-id="94b46-138">Lucky for you, C# and the .NET ecosystem comes with features and techniques that allow us to easily update our app to work with new versions of libraries that might introduce breaking changes.</span></span>

### <a name="assembly-binding-redirection"></a><span data-ttu-id="94b46-139">組件繫結重新導向</span><span class="sxs-lookup"><span data-stu-id="94b46-139">Assembly Binding Redirection</span></span>

<span data-ttu-id="94b46-140">您可以*使用 app.config 檔案*來更新應用程式使用的程式庫版本。</span><span class="sxs-lookup"><span data-stu-id="94b46-140">You can use the *app.config* file to update the version of a library your app uses.</span></span> <span data-ttu-id="94b46-141">藉由新增所謂的系結重新[*導向*](../framework/configure-apps/redirect-assembly-versions.md)，您可以使用新的程式庫版本，而不需要重新編譯應用程式。</span><span class="sxs-lookup"><span data-stu-id="94b46-141">By adding what is called a [*binding redirect*](../framework/configure-apps/redirect-assembly-versions.md), you can use the new library version without having to recompile your app.</span></span> <span data-ttu-id="94b46-142">下列範例會示範如何更新應用*程式的 app.config*檔案，以使用 `ReferencedLibrary` 的 @no__t 1 修補程式版本，而不是原本用來編譯的 `1.0.0` 版。</span><span class="sxs-lookup"><span data-stu-id="94b46-142">The following example shows how you would update your app's *app.config* file to use the `1.0.1` patch version of `ReferencedLibrary` instead of the `1.0.0` version it was originally compiled with.</span></span>

```xml
<dependentAssembly>
    <assemblyIdentity name="ReferencedLibrary" publicKeyToken="32ab4ba45e0a69a1" culture="en-us" />
    <bindingRedirect oldVersion="1.0.0" newVersion="1.0.1" />
</dependentAssembly>
```

> [!NOTE]
> <span data-ttu-id="94b46-143">新版 `ReferencedLibrary` 與您的應用程式必須是二進位相容，才能使用這個方法。</span><span class="sxs-lookup"><span data-stu-id="94b46-143">This approach will only work if the new version of `ReferencedLibrary` is binary compatible with your app.</span></span>
> <span data-ttu-id="94b46-144">如需決定相容性時需要留意的變更，請參閱前文的[回溯相容性](#backwards-compatibility)一節。</span><span class="sxs-lookup"><span data-stu-id="94b46-144">See the [Backwards Compatibility](#backwards-compatibility) section above for changes to look out for when determining compatibility.</span></span>

### <a name="new"></a><span data-ttu-id="94b46-145">new</span><span class="sxs-lookup"><span data-stu-id="94b46-145">new</span></span>

<span data-ttu-id="94b46-146">您使用 `new` 修飾詞隱藏繼承的基底類別成員。</span><span class="sxs-lookup"><span data-stu-id="94b46-146">You use the `new` modifier to hide inherited members of a base class.</span></span> <span data-ttu-id="94b46-147">這是衍生類別可以回應基底類別更新的一種方式。</span><span class="sxs-lookup"><span data-stu-id="94b46-147">This is one way derived classes can respond to updates in base classes.</span></span>

<span data-ttu-id="94b46-148">請使用以下範例：</span><span class="sxs-lookup"><span data-stu-id="94b46-148">Take the following example:</span></span>

[!code-csharp[Sample usage of the 'new' modifier](~/samples/csharp/versioning/new/Program.cs#sample)]

<span data-ttu-id="94b46-149">**輸出**</span><span class="sxs-lookup"><span data-stu-id="94b46-149">**Output**</span></span>

```console
A base method
A derived method
```

<span data-ttu-id="94b46-150">您在上例中可以看到 `DerivedClass` 如何隱藏出現在 `BaseClass` 中的 `MyMethod` 方法。</span><span class="sxs-lookup"><span data-stu-id="94b46-150">From the example above you can see how `DerivedClass` hides the `MyMethod` method present in `BaseClass`.</span></span>
<span data-ttu-id="94b46-151">這表示，當新版文件庫中的基底類別新增您衍生類別中已有的成員時，您只要對衍生類別成員使用 `new` 修飾詞，就可以隱藏基底類別成員。</span><span class="sxs-lookup"><span data-stu-id="94b46-151">This means that when a base class in the new version of a library adds a member that already exists in your derived class, you can simply use the `new` modifier on your derived class member to hide the base class member.</span></span>

<span data-ttu-id="94b46-152">未指定任何 `new` 修飾詞時，衍生類別預設會隱藏基底類別中發生衝突的成員，雖然會產生編譯器警告，但程式碼仍會編譯。</span><span class="sxs-lookup"><span data-stu-id="94b46-152">When no `new` modifier is specified, a derived class will by default hide conflicting members in a base class, although a compiler warning will be generated the code will still compile.</span></span> <span data-ttu-id="94b46-153">這表示，只要將新成員新增至現有的類別，即可讓新版文件庫與與相依於它的程式碼為來源和二進位相容。</span><span class="sxs-lookup"><span data-stu-id="94b46-153">This means that simply adding new members to an existing class makes that new version of your library both source and binary compatible with code that depends on it.</span></span>

### <a name="override"></a><span data-ttu-id="94b46-154">override</span><span class="sxs-lookup"><span data-stu-id="94b46-154">override</span></span>

<span data-ttu-id="94b46-155">`override` 修飾詞表示衍生的實作會擴充基底類別成員的實作，而非隱藏它。</span><span class="sxs-lookup"><span data-stu-id="94b46-155">The `override` modifier means a derived implementation extends the implementation of a base class member rather than hides it.</span></span> <span data-ttu-id="94b46-156">基底類別成員需要套用 `virtual` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="94b46-156">The base class member needs to have the `virtual` modifier applied to it.</span></span>

[!code-csharp[Sample usage of the 'override' modifier](../../samples/csharp/versioning/override/Program.cs#sample)]

<span data-ttu-id="94b46-157">**輸出**</span><span class="sxs-lookup"><span data-stu-id="94b46-157">**Output**</span></span>

```console
Base Method One: Method One
Derived Method One: Derived Method One
```

<span data-ttu-id="94b46-158">`override` 修飾詞會在編譯期間評估，如果編譯器找不到要覆寫的虛擬成員，它會擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="94b46-158">The `override` modifier is evaluated at compile time and the compiler will throw an error if it doesn't find a virtual member to override.</span></span>

<span data-ttu-id="94b46-159">您對所討論之技術的瞭解，以及您對其使用方式的瞭解，將會很長的方式可簡化程式庫版本之間的轉換。</span><span class="sxs-lookup"><span data-stu-id="94b46-159">Your knowledge of the discussed techniques and your understanding of the situations in which to use them, will go a long way towards easing the transition between versions of a library.</span></span>
