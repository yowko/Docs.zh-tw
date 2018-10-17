---
title: 重大變更 」 和 「.NET 程式庫
description: 瀏覽時建立的.NET 程式庫的重大變更的最佳做法建議。
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 83c01fdad7d836877bf692b87eeb0230219ded36
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2018
ms.locfileid: "49369807"
---
# <a name="breaking-changes"></a><span data-ttu-id="34189-103">重大變更</span><span class="sxs-lookup"><span data-stu-id="34189-103">Breaking changes</span></span>

<span data-ttu-id="34189-104">很重要的.NET 程式庫，若要尋找現有使用者的穩定性和未來的創新之間取得平衡。</span><span class="sxs-lookup"><span data-stu-id="34189-104">It's important for a .NET library to find a balance between stability for existing users and innovation for the future.</span></span> <span data-ttu-id="34189-105">程式庫作者借助針對重構和重新思考程式碼，直到它是完美的但是中斷現有的使用者會有負面的影響，特別是針對低層級的程式庫。</span><span class="sxs-lookup"><span data-stu-id="34189-105">Library authors lean towards refactoring and rethinking code until it's perfect, but breaking your existing users has a negative impact, especially for low-level libraries.</span></span>

## <a name="project-types-and-breaking-changes"></a><span data-ttu-id="34189-106">專案類型和重大變更</span><span class="sxs-lookup"><span data-stu-id="34189-106">Project types and breaking changes</span></span>

<span data-ttu-id="34189-107">.NET 社群使用文件庫的方式變更使用者的開發人員的重大變更的影響。</span><span class="sxs-lookup"><span data-stu-id="34189-107">How a library is used by the .NET community changes the effect of breaking changes on end-user developers.</span></span>

* <span data-ttu-id="34189-108">**低和中介層程式庫**等序列化程式、 HTML 剖析器、 資料庫物件關聯式對應程式或 web 架構是最受影響的重大變更。</span><span class="sxs-lookup"><span data-stu-id="34189-108">**Low and middle-level libraries** like a serializer, HTML parser, database object-relational mapper, or web framework are the most affected by breaking changes.</span></span>

  <span data-ttu-id="34189-109">建置組塊套件會使用由使用者來建置應用程式的開發人員和其他程式庫做為 NuGet 相依性。</span><span class="sxs-lookup"><span data-stu-id="34189-109">Building block packages are used by end-user developers to build applications, and by other libraries as NuGet dependencies.</span></span> <span data-ttu-id="34189-110">例如，您要建置的應用程式，並使用開放原始碼用戶端來呼叫 web 服務。</span><span class="sxs-lookup"><span data-stu-id="34189-110">For example, you're building an application and are using an open-source client to call a web service.</span></span> <span data-ttu-id="34189-111">用戶端會使用相依性的重大更新不是您可以修正。</span><span class="sxs-lookup"><span data-stu-id="34189-111">A breaking update to a dependency the client uses isn't something you can fix.</span></span> <span data-ttu-id="34189-112">它是開放原始碼用戶端，需要變更，就無法控制。</span><span class="sxs-lookup"><span data-stu-id="34189-112">It's the open-source client that needs to be changed and you have no control over it.</span></span> <span data-ttu-id="34189-113">您必須尋找相容版本的程式庫或提交修正，以用戶端程式庫，並等候新的版本。</span><span class="sxs-lookup"><span data-stu-id="34189-113">You have to find compatible versions of the libraries or submit a fix to the client library and wait for a new version.</span></span> <span data-ttu-id="34189-114">最糟的情況是如果您想要使用相依於彼此不相容的版本，第三個程式庫的兩個程式庫。</span><span class="sxs-lookup"><span data-stu-id="34189-114">The worst-case situation is if you want to use two libraries that depend on mutually incompatible versions of a third library.</span></span>

* <span data-ttu-id="34189-115">**高層級的程式庫**像一套的 UI 控制項是較不容易的重大變更。</span><span class="sxs-lookup"><span data-stu-id="34189-115">**High-level libraries** like a suite of UI controls are less sensitive to breaking changes.</span></span>

  <span data-ttu-id="34189-116">高層級的程式庫會直接參考使用者應用程式中。</span><span class="sxs-lookup"><span data-stu-id="34189-116">High-level libraries are directly referenced in an end-user application.</span></span> <span data-ttu-id="34189-117">如果發生重大變更，開發人員可以選擇更新為最新版本，或可以修改其應用程式使用的重大變更。</span><span class="sxs-lookup"><span data-stu-id="34189-117">If breaking changes occur, the developer can choose to update to the latest version, or can modify their application to work with the breaking change.</span></span>

<span data-ttu-id="34189-118">**請勿 ✔️**思考您的程式庫的使用方式。</span><span class="sxs-lookup"><span data-stu-id="34189-118">**✔️ DO** think about how your library will be used.</span></span> <span data-ttu-id="34189-119">重大變更會有何種影響的應用程式和程式庫，使用它呢？</span><span class="sxs-lookup"><span data-stu-id="34189-119">What effect will breaking changes have on applications and libraries that use it?</span></span>

<span data-ttu-id="34189-120">**請勿 ✔️**開發的低層級的.NET 程式庫時，將重大變更降至最低。</span><span class="sxs-lookup"><span data-stu-id="34189-120">**✔️ DO** minimize breaking changes when developing a low-level .NET library.</span></span>

<span data-ttu-id="34189-121">**請考慮 ✔️**發行主要重寫為新的 NuGet 套件程式庫。</span><span class="sxs-lookup"><span data-stu-id="34189-121">**✔️ CONSIDER** publishing a major rewrite of a library as a new NuGet package.</span></span>

## <a name="types-of-breaking-changes"></a><span data-ttu-id="34189-122">類型的重大變更</span><span class="sxs-lookup"><span data-stu-id="34189-122">Types of breaking changes</span></span>

<span data-ttu-id="34189-123">重大變更會分成不同類別，並不是同樣有影響力。</span><span class="sxs-lookup"><span data-stu-id="34189-123">Breaking changes fall into different categories and aren't equally impactful.</span></span>

### <a name="source-breaking-change"></a><span data-ttu-id="34189-124">來源重大變更</span><span class="sxs-lookup"><span data-stu-id="34189-124">Source breaking change</span></span>

<span data-ttu-id="34189-125">重大變更的來源並不會影響程式執行，但會導致重新編譯應用程式在下一次編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="34189-125">A source breaking change doesn't affect program execution but will cause compilation errors the next time the application is recompiled.</span></span> <span data-ttu-id="34189-126">比方說，新的多載可以在先前模稜兩可，方法呼叫的模稜兩可，或已重新命名的參數將會中斷的呼叫端使用具名參數。</span><span class="sxs-lookup"><span data-stu-id="34189-126">For example, a new overload can create an ambiguity in method calls that were unambiguous previously, or a renamed parameter will break callers that use named parameters.</span></span>

```csharp
public class Task
{
    // Adding a type called Task could conflict with System.Threading.Tasks.Task at compilation
}
```

<span data-ttu-id="34189-127">開發人員重新編譯其應用程式時，才會造成損害的重大變更的來源，因為它會是最少干擾的重大變更。</span><span class="sxs-lookup"><span data-stu-id="34189-127">Because a source breaking change is only harmful when developers recompile their applications, it's the least disruptive breaking change.</span></span> <span data-ttu-id="34189-128">開發人員可以輕鬆地修正自己中斷的來源的程式碼。</span><span class="sxs-lookup"><span data-stu-id="34189-128">Developers can fix their own broken source code easily.</span></span>

### <a name="behavior-breaking-change"></a><span data-ttu-id="34189-129">行為重大變更</span><span class="sxs-lookup"><span data-stu-id="34189-129">Behavior breaking change</span></span>

<span data-ttu-id="34189-130">行為變更是最常見的重大變更的類型： 幾乎任何行為變更可能會中斷其他人。</span><span class="sxs-lookup"><span data-stu-id="34189-130">Behavior changes are the most common type of breaking change: almost any change in behavior could break someone.</span></span> <span data-ttu-id="34189-131">變更為您的程式庫，例如方法簽章，例外狀況擲回或輸入或輸出資料格式，所有設定而嚴重影響您的程式庫取用者。</span><span class="sxs-lookup"><span data-stu-id="34189-131">Changes to your library, such as method signatures, exceptions thrown or input or output data formats, could all negatively impact your library consumers.</span></span> <span data-ttu-id="34189-132">如果使用者依賴先前中斷的行為，甚至修正可以限定為一項重大變更。</span><span class="sxs-lookup"><span data-stu-id="34189-132">Even a bug fix can qualify as a breaking change if users relied on the previously broken behavior.</span></span>

<span data-ttu-id="34189-133">新增功能和改善不正確的行為是件好事，但是不小心會變得更難升級現有的使用者。</span><span class="sxs-lookup"><span data-stu-id="34189-133">Adding features and improving bad behaviors is a good thing, but without care it can make it very hard for existing users to upgrade.</span></span> <span data-ttu-id="34189-134">若要協助開發人員在面對重大變更的行為的其中一個方法是設定背後隱藏起來。</span><span class="sxs-lookup"><span data-stu-id="34189-134">One approach to helping developers deal with behavior breaking changes is to hide them behind settings.</span></span> <span data-ttu-id="34189-135">設定可讓開發人員更新您的程式庫，而同時選擇參加或退出的重大變更最新版本。</span><span class="sxs-lookup"><span data-stu-id="34189-135">Settings let developers update to the latest version of your library while at the same time choosing to opt in or opt out of breaking changes.</span></span> <span data-ttu-id="34189-136">這項策略可讓開發人員同時可讓其使用的程式碼，採用經過一段時間保持最新狀態。</span><span class="sxs-lookup"><span data-stu-id="34189-136">This strategy lets developers stay up to date while letting their consuming code adapt over time.</span></span>

<span data-ttu-id="34189-137">例如，ASP.NET Core MVC 具有概念[相容性版本](/aspnet/core/mvc/compatibility-version)修改的功能已啟用和停用`MvcOptions`。</span><span class="sxs-lookup"><span data-stu-id="34189-137">For example, ASP.NET Core MVC has the concept of a [compatibility version](/aspnet/core/mvc/compatibility-version) that modifies the features enabled and disabled on `MvcOptions`.</span></span>

<span data-ttu-id="34189-138">**請考慮 ✔️**離開的新功能，根據預設，如果它們會影響現有的使用者，讓開發人員選擇加入設定的功能。</span><span class="sxs-lookup"><span data-stu-id="34189-138">**✔️ CONSIDER** leaving new features off by default, if they affect existing users, and let developers opt in to the feature with a setting.</span></span>

### <a name="binary-breaking-change"></a><span data-ttu-id="34189-139">二進位的重大變更</span><span class="sxs-lookup"><span data-stu-id="34189-139">Binary breaking change</span></span>

<span data-ttu-id="34189-140">當您變更您的程式庫的公用 API 時，會發生重大變更的二進位檔，因此對編譯的組件較舊版本的程式庫已不再能夠呼叫 API。</span><span class="sxs-lookup"><span data-stu-id="34189-140">A binary breaking change happens when you change the public API of your library, so assemblies compiled against older versions of your library are no longer able to call the API.</span></span> <span data-ttu-id="34189-141">例如，藉由新增新的參數變更方法簽章會對程式庫的較舊版本所編譯的組件會擲回<xref:System.MissingMethodException>。</span><span class="sxs-lookup"><span data-stu-id="34189-141">For example, changing a method's signature by adding a new parameter will cause assemblies compiled against the older version of the library to throw a <xref:System.MissingMethodException>.</span></span>

<span data-ttu-id="34189-142">重大變更的二進位檔可能會破壞**整個組件**。</span><span class="sxs-lookup"><span data-stu-id="34189-142">A binary breaking change can also break an **entire assembly**.</span></span> <span data-ttu-id="34189-143">重新命名的組件`AssemblyName`，將組件的身分識別，也會新增、 移除或變更組件的強式命名金鑰。</span><span class="sxs-lookup"><span data-stu-id="34189-143">Renaming an assembly with `AssemblyName` will change the assembly's identity, as will adding, removing, or changing the assembly's strong naming key.</span></span> <span data-ttu-id="34189-144">組件的身分識別的變更會中斷所有使用它的已編譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="34189-144">A change of an assembly's identity will break all compiled code that uses it.</span></span>

<span data-ttu-id="34189-145">**不這麼做 ❌**變更組件名稱。</span><span class="sxs-lookup"><span data-stu-id="34189-145">**❌ DO NOT** change an assembly name.</span></span>

<span data-ttu-id="34189-146">**不這麼做 ❌**新增、 移除或變更的強式命名的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="34189-146">**❌ DO NOT** add, remove, or change the strong naming key.</span></span>

<span data-ttu-id="34189-147">**請考慮 ✔️**使用抽象的基底類別，而不介面。</span><span class="sxs-lookup"><span data-stu-id="34189-147">**✔️ CONSIDER** using abstract base classes instead of interfaces.</span></span>

> <span data-ttu-id="34189-148">將任何項目新增至介面，會導致現有的型別實作失敗。</span><span class="sxs-lookup"><span data-stu-id="34189-148">Adding anything to an interface will cause existing types that implement it to fail.</span></span> <span data-ttu-id="34189-149">抽象基底類別可讓您新增的預設虛擬實作。</span><span class="sxs-lookup"><span data-stu-id="34189-149">An abstract base class allows you to add a default virtual implementation.</span></span>

<span data-ttu-id="34189-150">**請考慮 ✔️**放置<xref:System.ObsoleteAttribute>類型和您想要移除的成員。</span><span class="sxs-lookup"><span data-stu-id="34189-150">**✔️ CONSIDER** placing the <xref:System.ObsoleteAttribute> on types and members that you intend to remove.</span></span> <span data-ttu-id="34189-151">屬性應該更新程式碼的指示進行，不能再使用過時的 API。</span><span class="sxs-lookup"><span data-stu-id="34189-151">The attribute should have instructions for updating code to no longer use the obsolete API.</span></span>

> <span data-ttu-id="34189-152">呼叫類型和方法的程式碼<xref:System.ObsoleteAttribute>會產生建置警告並提供給屬性的訊息。</span><span class="sxs-lookup"><span data-stu-id="34189-152">Code that calls types and methods with the <xref:System.ObsoleteAttribute> will generate a build warning with the message supplied to the attribute.</span></span> <span data-ttu-id="34189-153">警告讓人使用過時的 API 介面的時間來移轉，如此當移除過時的 API 時，大部分都不會再使用它。</span><span class="sxs-lookup"><span data-stu-id="34189-153">The warnings give people who use the obsolete API surface time to migrate so that when the obsolete API is removed, most are no longer using it.</span></span>

```csharp
public class Document
{
    [Obsolete("LoadDocument(string) is obsolete. Use LoadDocument(Uri) instead.")]
    public static Document LoadDocument(string uri)
    {
        return LoadDocument(new Uri(uri));
    }

    public static Document LoadDocument(Uri uri)
    {
        // Load the document
    }
}
```

## <a name="see-also"></a><span data-ttu-id="34189-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34189-154">See also</span></span>

* [<span data-ttu-id="34189-155">適用於 C# 開發人員版和更新的考量</span><span class="sxs-lookup"><span data-stu-id="34189-155">Version and update considerations for C# developers</span></span>](../../csharp/whats-new/version-update-considerations.md)
* [<span data-ttu-id="34189-156">在.NET 中的 API-重大變更指南</span><span class="sxs-lookup"><span data-stu-id="34189-156">A definitive guide to API-breaking changes in .NET</span></span>](https://stackoverflow.com/questions/1456785/a-definitive-guide-to-api-breaking-changes-in-net)
* [<span data-ttu-id="34189-157">CoreFX 重大變更規則</span><span class="sxs-lookup"><span data-stu-id="34189-157">CoreFX Breaking Change Rules</span></span>](https://github.com/dotnet/corefx/blob/master/Documentation/coding-guidelines/breaking-change-rules.md)

>[!div class="step-by-step"]
[<span data-ttu-id="34189-158">上一步</span><span class="sxs-lookup"><span data-stu-id="34189-158">Previous</span></span>](./versioning.md)
