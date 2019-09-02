---
title: 中斷性變更與 .NET 程式庫
description: 建立 .NET 程式庫時巡覽中斷性變更的最佳做法建議。
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 6881b8737d9dd3fa7fa71f099fa1dc97b747033d
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70104664"
---
# <a name="breaking-changes"></a><span data-ttu-id="d19db-103">重大變更</span><span class="sxs-lookup"><span data-stu-id="d19db-103">Breaking changes</span></span>

<span data-ttu-id="d19db-104">.NET 程式庫必須在針對現有使用者提供穩定性，以及針對未來取得創新之間取得平衡。</span><span class="sxs-lookup"><span data-stu-id="d19db-104">It's important for a .NET library to find a balance between stability for existing users and innovation for the future.</span></span> <span data-ttu-id="d19db-105">程式庫作者會傾向重構及重新思考程式碼，直到他們的程式庫完美為止，但中斷您現有的使用者可能會帶來負面影響 (尤其是低層級的程式庫)。</span><span class="sxs-lookup"><span data-stu-id="d19db-105">Library authors lean towards refactoring and rethinking code until it's perfect, but breaking your existing users has a negative impact, especially for low-level libraries.</span></span>

## <a name="project-types-and-breaking-changes"></a><span data-ttu-id="d19db-106">專案類型與中斷性變更</span><span class="sxs-lookup"><span data-stu-id="d19db-106">Project types and breaking changes</span></span>

<span data-ttu-id="d19db-107">.NET 社群使用程式庫的方式會改變中斷性變更對終端使用者開發人員的影響。</span><span class="sxs-lookup"><span data-stu-id="d19db-107">How a library is used by the .NET community changes the effect of breaking changes on end-user developers.</span></span>

- <span data-ttu-id="d19db-108">**低層級與中層級程式庫** (例如序列化程式、HTML 剖析器、資料庫物件關聯式對應程式或 Web 架構) 受到中斷性變更的影響程度最大。</span><span class="sxs-lookup"><span data-stu-id="d19db-108">**Low and middle-level libraries** like a serializer, HTML parser, database object-relational mapper, or web framework are the most affected by breaking changes.</span></span>

  <span data-ttu-id="d19db-109">終端使用者開發人員會使用建置組塊套件來建置應用程式，其他程式庫則會將建置組塊套件用來作為 NuGet 相依性。</span><span class="sxs-lookup"><span data-stu-id="d19db-109">Building block packages are used by end-user developers to build applications, and by other libraries as NuGet dependencies.</span></span> <span data-ttu-id="d19db-110">例如，您要建置一個應用程式，且使用開放原始碼用戶端來呼叫 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="d19db-110">For example, you're building an application and are using an open-source client to call a web service.</span></span> <span data-ttu-id="d19db-111">對使用者所使用相依性進行的中斷性變更，便不是您可以修正的項目。</span><span class="sxs-lookup"><span data-stu-id="d19db-111">A breaking update to a dependency the client uses isn't something you can fix.</span></span> <span data-ttu-id="d19db-112">因為需要變更的是開放原始碼用戶端，而您無法控制該用戶端。</span><span class="sxs-lookup"><span data-stu-id="d19db-112">It's the open-source client that needs to be changed and you have no control over it.</span></span> <span data-ttu-id="d19db-113">您必須找出程式庫的相容版本，或是提交用戶端程式庫的修正並等待新版本。</span><span class="sxs-lookup"><span data-stu-id="d19db-113">You have to find compatible versions of the libraries or submit a fix to the client library and wait for a new version.</span></span> <span data-ttu-id="d19db-114">最差的情況便是您想要使用兩個相依於不同版本協力廠商程式庫的程式庫，而這兩個版本彼此互不相容。</span><span class="sxs-lookup"><span data-stu-id="d19db-114">The worst-case situation is if you want to use two libraries that depend on mutually incompatible versions of a third library.</span></span>

- <span data-ttu-id="d19db-115">**高層級程式庫**(例如 UI 控制項套件) 受到中斷性變更影響的程度則較低。</span><span class="sxs-lookup"><span data-stu-id="d19db-115">**High-level libraries** like a suite of UI controls are less sensitive to breaking changes.</span></span>

  <span data-ttu-id="d19db-116">終端使用者應用程式中會直接參考高層級程式庫。</span><span class="sxs-lookup"><span data-stu-id="d19db-116">High-level libraries are directly referenced in an end-user application.</span></span> <span data-ttu-id="d19db-117">若發生中斷性變更，開發人員可以選擇更新到最新版本，或是修改他們的應用程式來配合中斷性變更。</span><span class="sxs-lookup"><span data-stu-id="d19db-117">If breaking changes occur, the developer can choose to update to the latest version, or can modify their application to work with the breaking change.</span></span>

<span data-ttu-id="d19db-118">**✔️ 請**思考您程式庫的使用方式。</span><span class="sxs-lookup"><span data-stu-id="d19db-118">**✔️ DO** think about how your library will be used.</span></span> <span data-ttu-id="d19db-119">中斷性變更可能會對使用它的應用程式和程式庫帶來什麼影響？</span><span class="sxs-lookup"><span data-stu-id="d19db-119">What effect will breaking changes have on applications and libraries that use it?</span></span>

<span data-ttu-id="d19db-120">**✔️ 請**在開發低層級 .NET 程式庫時，盡量避免中斷性變更。</span><span class="sxs-lookup"><span data-stu-id="d19db-120">**✔️ DO** minimize breaking changes when developing a low-level .NET library.</span></span>

<span data-ttu-id="d19db-121">**✔️ 請考慮**將大幅重寫的程式庫作為新的 NuGet 套件發佈。</span><span class="sxs-lookup"><span data-stu-id="d19db-121">**✔️ CONSIDER** publishing a major rewrite of a library as a new NuGet package.</span></span>

## <a name="types-of-breaking-changes"></a><span data-ttu-id="d19db-122">中斷性變更的類型</span><span class="sxs-lookup"><span data-stu-id="d19db-122">Types of breaking changes</span></span>

<span data-ttu-id="d19db-123">中斷性變更可分成不同類別，其影響的程度各不相同。</span><span class="sxs-lookup"><span data-stu-id="d19db-123">Breaking changes fall into different categories and aren't equally impactful.</span></span>

### <a name="source-breaking-change"></a><span data-ttu-id="d19db-124">原始檔中斷性變更</span><span class="sxs-lookup"><span data-stu-id="d19db-124">Source breaking change</span></span>

<span data-ttu-id="d19db-125">原始檔中斷性變更不會影響程式的執行，但是會在下一次重新編譯應用程式時導致編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="d19db-125">A source breaking change doesn't affect program execution but will cause compilation errors the next time the application is recompiled.</span></span> <span data-ttu-id="d19db-126">例如，新的多載可能會在先前明確的方法呼叫過程中造成模稜兩可的情況；重新命名參數則可能會中斷使用具名參數的呼叫者。</span><span class="sxs-lookup"><span data-stu-id="d19db-126">For example, a new overload can create an ambiguity in method calls that were unambiguous previously, or a renamed parameter will break callers that use named parameters.</span></span>

```csharp
public class Task
{
    // Adding a type called Task could conflict with System.Threading.Tasks.Task at compilation
}
```

<span data-ttu-id="d19db-127">因為原始檔中斷性變更只會在開發人員重新編譯應用程式時造成傷害，因此它是干擾程度最小的中斷性變更。</span><span class="sxs-lookup"><span data-stu-id="d19db-127">Because a source breaking change is only harmful when developers recompile their applications, it's the least disruptive breaking change.</span></span> <span data-ttu-id="d19db-128">開發人員可以輕易地自行修正中斷的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="d19db-128">Developers can fix their own broken source code easily.</span></span>

### <a name="behavior-breaking-change"></a><span data-ttu-id="d19db-129">行為中斷性變更</span><span class="sxs-lookup"><span data-stu-id="d19db-129">Behavior breaking change</span></span>

<span data-ttu-id="d19db-130">行為中斷性變更是最常見的中斷性變更類型：對行為進行的任何變更幾乎都會中斷其他人。</span><span class="sxs-lookup"><span data-stu-id="d19db-130">Behavior changes are the most common type of breaking change: almost any change in behavior could break someone.</span></span> <span data-ttu-id="d19db-131">變更您的程式庫 (例如方法簽章、擲回的例外狀況或是輸入或輸出資料格式) 都可能會對您程式庫的消費者帶來負面影響。</span><span class="sxs-lookup"><span data-stu-id="d19db-131">Changes to your library, such as method signatures, exceptions thrown or input or output data formats, could all negatively impact your library consumers.</span></span> <span data-ttu-id="d19db-132">若使用者依賴先前中斷的行為，即使是修正 Bug 都可能會符合中斷性變更的定義。</span><span class="sxs-lookup"><span data-stu-id="d19db-132">Even a bug fix can qualify as a breaking change if users relied on the previously broken behavior.</span></span>

<span data-ttu-id="d19db-133">新增功能和改善不良行為是件好事，但若不小心，便可能會讓現有使用者難以進行升級。</span><span class="sxs-lookup"><span data-stu-id="d19db-133">Adding features and improving bad behaviors is a good thing, but without care it can make it very hard for existing users to upgrade.</span></span> <span data-ttu-id="d19db-134">協助開發人員處理行為中斷性變更的其中一種方法，便是將它們隱藏在設定後方。</span><span class="sxs-lookup"><span data-stu-id="d19db-134">One approach to helping developers deal with behavior breaking changes is to hide them behind settings.</span></span> <span data-ttu-id="d19db-135">設定可以讓開發人員更新到程式庫的最新版本，同時也能讓他們選擇加入或退出中斷性變更。</span><span class="sxs-lookup"><span data-stu-id="d19db-135">Settings let developers update to the latest version of your library while at the same time choosing to opt in or opt out of breaking changes.</span></span> <span data-ttu-id="d19db-136">這項策略可讓開發人員維持在最新狀態，同時也能讓他們取用的程式碼隨時間適應變更。</span><span class="sxs-lookup"><span data-stu-id="d19db-136">This strategy lets developers stay up to date while letting their consuming code adapt over time.</span></span>

<span data-ttu-id="d19db-137">例如，ASP.NET Core MVC 具有[相容性版本](/aspnet/core/mvc/compatibility-version)的概念，可修改在 `MvcOptions` 上啟用或停用的功能。</span><span class="sxs-lookup"><span data-stu-id="d19db-137">For example, ASP.NET Core MVC has the concept of a [compatibility version](/aspnet/core/mvc/compatibility-version) that modifies the features enabled and disabled on `MvcOptions`.</span></span>

<span data-ttu-id="d19db-138">**✔️ 請考慮**在新功能可能影響現有使用者的情況下，根據預設將其維持在關閉狀態，並讓開發人員透過設定加入功能。</span><span class="sxs-lookup"><span data-stu-id="d19db-138">**✔️ CONSIDER** leaving new features off by default, if they affect existing users, and let developers opt in to the feature with a setting.</span></span>

### <a name="binary-breaking-change"></a><span data-ttu-id="d19db-139">二進位中斷性變更</span><span class="sxs-lookup"><span data-stu-id="d19db-139">Binary breaking change</span></span>

<span data-ttu-id="d19db-140">二進位中斷性變更會在您變更程式庫的公用 API 時發生，導致針對您舊版程式庫進行編譯的組件無法繼續呼叫 API。</span><span class="sxs-lookup"><span data-stu-id="d19db-140">A binary breaking change happens when you change the public API of your library, so assemblies compiled against older versions of your library are no longer able to call the API.</span></span> <span data-ttu-id="d19db-141">例如，新增新參數來變更方法的簽章會導致針對舊版程式庫進行編譯的組件擲回 <xref:System.MissingMethodException>。</span><span class="sxs-lookup"><span data-stu-id="d19db-141">For example, changing a method's signature by adding a new parameter will cause assemblies compiled against the older version of the library to throw a <xref:System.MissingMethodException>.</span></span>

<span data-ttu-id="d19db-142">二進位中斷性變更也可能會中斷**整個組件**。</span><span class="sxs-lookup"><span data-stu-id="d19db-142">A binary breaking change can also break an **entire assembly**.</span></span> <span data-ttu-id="d19db-143">使用 `AssemblyName` 重新命名組件，或是新增、移除或變更組件的強式命名金鑰，則會變更組件的身分識別。</span><span class="sxs-lookup"><span data-stu-id="d19db-143">Renaming an assembly with `AssemblyName` will change the assembly's identity, as will adding, removing, or changing the assembly's strong naming key.</span></span> <span data-ttu-id="d19db-144">變更組件的身分識別會中斷所有使用它的編譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="d19db-144">A change of an assembly's identity will break all compiled code that uses it.</span></span>

<span data-ttu-id="d19db-145">**❌ 請不要**變更組件名稱。</span><span class="sxs-lookup"><span data-stu-id="d19db-145">**❌ DO NOT** change an assembly name.</span></span>

<span data-ttu-id="d19db-146">**❌ 請不要**新增、移除或變更強式命名金鑰。</span><span class="sxs-lookup"><span data-stu-id="d19db-146">**❌ DO NOT** add, remove, or change the strong naming key.</span></span>

<span data-ttu-id="d19db-147">**✔️ 請考慮**使用抽象基底類別，而非介面。</span><span class="sxs-lookup"><span data-stu-id="d19db-147">**✔️ CONSIDER** using abstract base classes instead of interfaces.</span></span>

> <span data-ttu-id="d19db-148">將任何項目新增到介面都會造成實作它的現有類型失敗。</span><span class="sxs-lookup"><span data-stu-id="d19db-148">Adding anything to an interface will cause existing types that implement it to fail.</span></span> <span data-ttu-id="d19db-149">基底類別則允許您新增預設虛擬實作。</span><span class="sxs-lookup"><span data-stu-id="d19db-149">An abstract base class allows you to add a default virtual implementation.</span></span>

<span data-ttu-id="d19db-150">**✔️ 請考慮**將 <xref:System.ObsoleteAttribute> 放置在您打算移除的類型和成員上。</span><span class="sxs-lookup"><span data-stu-id="d19db-150">**✔️ CONSIDER** placing the <xref:System.ObsoleteAttribute> on types and members that you intend to remove.</span></span> <span data-ttu-id="d19db-151">屬性應具備指示，說明如何更新程式碼以避免使用已淘汰的 API。</span><span class="sxs-lookup"><span data-stu-id="d19db-151">The attribute should have instructions for updating code to no longer use the obsolete API.</span></span>

> <span data-ttu-id="d19db-152">呼叫具有 <xref:System.ObsoleteAttribute> 類型和方法的程式碼會產生建置警告，並附帶提供給該屬性的訊息。</span><span class="sxs-lookup"><span data-stu-id="d19db-152">Code that calls types and methods with the <xref:System.ObsoleteAttribute> will generate a build warning with the message supplied to the attribute.</span></span> <span data-ttu-id="d19db-153">警告可讓使用已淘汰 API 的人員進行遷移，以在移除已淘汰的 API 時，大多數的人員已不再使用它。</span><span class="sxs-lookup"><span data-stu-id="d19db-153">The warnings give people who use the obsolete API surface time to migrate so that when the obsolete API is removed, most are no longer using it.</span></span>

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

<span data-ttu-id="d19db-154">**✔️ 請考慮**在低層級與中層級程式庫中無限期維持具有 <xref:System.ObsoleteAttribute> 的類型和方法。</span><span class="sxs-lookup"><span data-stu-id="d19db-154">**✔️ CONSIDER** keeping types and methods with the <xref:System.ObsoleteAttribute> indefinitely in low and middle-level libraries.</span></span>

> <span data-ttu-id="d19db-155">移除 API 是一項二進位中斷性變更。</span><span class="sxs-lookup"><span data-stu-id="d19db-155">Removing APIs is a binary breaking change.</span></span> <span data-ttu-id="d19db-156">若維持已淘汰類型和方法的成本低廉，也不會為您的程式庫增加技術債務，則請考慮維持已淘汰的類型和方法。</span><span class="sxs-lookup"><span data-stu-id="d19db-156">Considering keeping obsolete types and methods if maintaining them is low cost and doesn't add lot of technical debt to your library.</span></span> <span data-ttu-id="d19db-157">避免移除類型和方法，可協助避免上述提到的最差情況。</span><span class="sxs-lookup"><span data-stu-id="d19db-157">Not removing types and methods can help avoid the worst-case scenarios mentioned above.</span></span>

## <a name="see-also"></a><span data-ttu-id="d19db-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d19db-158">See also</span></span>

- [<span data-ttu-id="d19db-159">適用於 C# 開發人員的版本和更新考量</span><span class="sxs-lookup"><span data-stu-id="d19db-159">Version and update considerations for C# developers</span></span>](../../csharp/whats-new/version-update-considerations.md)
- <span data-ttu-id="d19db-160">[A definitive guide to API-breaking changes in .NET](https://stackoverflow.com/questions/1456785/a-definitive-guide-to-api-breaking-changes-in-net) (.NET 中 API 中斷性變更的完整指南)</span><span class="sxs-lookup"><span data-stu-id="d19db-160">[A definitive guide to API-breaking changes in .NET](https://stackoverflow.com/questions/1456785/a-definitive-guide-to-api-breaking-changes-in-net)</span></span>
- <span data-ttu-id="d19db-161">[CoreFX Breaking Change Rules](https://github.com/dotnet/corefx/blob/master/Documentation/coding-guidelines/breaking-change-rules.md) (CoreFX 中斷性變更規則)</span><span class="sxs-lookup"><span data-stu-id="d19db-161">[CoreFX Breaking Change Rules](https://github.com/dotnet/corefx/blob/master/Documentation/coding-guidelines/breaking-change-rules.md)</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="d19db-162">上一步</span><span class="sxs-lookup"><span data-stu-id="d19db-162">Previous</span></span>](versioning.md)
