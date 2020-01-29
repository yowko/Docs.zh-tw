---
title: 中斷性變更的類型-.NET Core
description: 瞭解 .NET Core 如何嘗試維護跨 .NET 版本開發人員的相容性，以及將哪種變更視為重大變更。
ms.date: 06/10/2019
ms.openlocfilehash: 76d04504c4476f0f7517a633cfbf1c0aa9d5797e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738581"
---
# <a name="changes-that-affect-compatibility"></a><span data-ttu-id="f424d-103">影響相容性的變更</span><span class="sxs-lookup"><span data-stu-id="f424d-103">Changes that affect compatibility</span></span>

<span data-ttu-id="f424d-104">縱觀其歷程記錄，.NET 一直嘗試維護 .NET 各版本之間以及各種變體之間的相容性。</span><span class="sxs-lookup"><span data-stu-id="f424d-104">Throughout its history, .NET has attempted to maintain a high level of compatibility from version to version and across flavors of .NET.</span></span> <span data-ttu-id="f424d-105">在 .NET Core 中仍是如此。</span><span class="sxs-lookup"><span data-stu-id="f424d-105">This continues to be true for .NET Core.</span></span> <span data-ttu-id="f424d-106">雖然 .NET Core 可以視為是獨立於 .NET Framework 之外的新技術，但是有兩個主要因素限制了 .NET Core 從 .NET Framework 分離的能力：</span><span class="sxs-lookup"><span data-stu-id="f424d-106">Although .NET Core can be considered as a new technology that is independent of the .NET Framework, two major factors limit the ability of .NET Core to diverge from .NET Framework:</span></span>

- <span data-ttu-id="f424d-107">最初開發或是繼續開發 .NET Framework 應用程式的大量開發人員。</span><span class="sxs-lookup"><span data-stu-id="f424d-107">A large number of developers either originally developed or continue to develop .NET Framework applications.</span></span> <span data-ttu-id="f424d-108">他們預期跨 .NET 實作有一致的行為。</span><span class="sxs-lookup"><span data-stu-id="f424d-108">They expect consistent behavior across .NET implementations.</span></span>

- <span data-ttu-id="f424d-109">.NET Standard 程式庫專案可讓開發人員建立以 .NET Core 和 .NET Framework 所共用之通用 API 為目標的程式庫。</span><span class="sxs-lookup"><span data-stu-id="f424d-109">.NET Standard library projects allow developers to create libraries that target common APIs shared by .NET Core and .NET Framework.</span></span> <span data-ttu-id="f424d-110">開發人員預期 .NET Core 應用程式中使用之程式庫的行為，應與 .NET Framework 應用程式中所使用的程式庫相同。</span><span class="sxs-lookup"><span data-stu-id="f424d-110">Developers expect that a library used in a .NET Core application should behave identically to the same library used in a .NET Framework application.</span></span>

<span data-ttu-id="f424d-111">除了 .NET 實作之間的相容性之外，開發人員還希望 .NET Core 版本之間具有高層級相容性。</span><span class="sxs-lookup"><span data-stu-id="f424d-111">Along with compatibility across .NET implementations, developers expect a high level of compatibility across .NET Core versions.</span></span> <span data-ttu-id="f424d-112">特別是，針對較早版本的 .NET Core 所撰寫的程式碼應該在新版的 .NET Core 上順暢地執行。</span><span class="sxs-lookup"><span data-stu-id="f424d-112">In particular, code written for an earlier version of .NET Core should run seamlessly on a later version of .NET Core.</span></span> <span data-ttu-id="f424d-113">實際上，許多開發人員預期在新發行的 .NET Core 版本中找到的新 API，也應該與引入那些 API 的發行前版本相容。</span><span class="sxs-lookup"><span data-stu-id="f424d-113">In fact, many developers expect that the new APIs found in newly released versions of .NET Core should also be compatible with the pre-release versions in which those APIs were introduced.</span></span>

<span data-ttu-id="f424d-114">此文章概述相容性變更 (或中斷性變更) 的類別，以及 .NET 小組評估每個類別中的變更的方式。</span><span class="sxs-lookup"><span data-stu-id="f424d-114">This article outlines the categories of compatibility changes (or breaking changes) and the way in which the .NET team evaluates changes in each of these categories.</span></span> <span data-ttu-id="f424d-115">瞭解 .NET 小組如何解決可能的重大變更，對於在修改現有 Api 行為的[dotnet/runtime](https://github.com/dotnet/runtime) GitHub 存放庫中開啟提取要求的開發人員而言特別有用。</span><span class="sxs-lookup"><span data-stu-id="f424d-115">Understanding how the .NET team approaches possible breaking changes is particularly helpful for developers who open pull requests in the [dotnet/runtime](https://github.com/dotnet/runtime) GitHub repository that modify the behavior of existing APIs.</span></span>

> [!NOTE]
> <span data-ttu-id="f424d-116">如需相容性類別的定義，例如二進位檔案相容性和回溯相容性，請參閱[中斷性變更類別](categories.md)。</span><span class="sxs-lookup"><span data-stu-id="f424d-116">For a definition of compatibility categories, such as binary compatibility and backward compatibility, see [Breaking change categories](categories.md).</span></span>

<span data-ttu-id="f424d-117">下列各節說明對 .NET Core Api 所做的變更分類，以及它們對應用程式相容性的影響。</span><span class="sxs-lookup"><span data-stu-id="f424d-117">The following sections describe the categories of changes made to .NET Core APIs and their impact on application compatibility.</span></span> <span data-ttu-id="f424d-118">變更允許✔️、不允許的 ❌，或需要判斷和評估先前的行為如何❓的可預測、明顯和一致。</span><span class="sxs-lookup"><span data-stu-id="f424d-118">Changes are either allowed ✔️, disallowed ❌, or require judgment and an evaluation of how predictable, obvious, and consistent the previous behavior was ❓.</span></span>

> [!NOTE]
> <span data-ttu-id="f424d-119">除了作為如何評估 .NET Core 程式庫變更的指南之外，程式庫開發人員也可以使用這些準則來評估其程式庫 (以多個 .NET 實作和版本為目標) 的變更。</span><span class="sxs-lookup"><span data-stu-id="f424d-119">In addition to serving as a guide to how changes to .NET Core libraries are evaluated, library developers can also use these criteria to evaluate changes to their libraries that target multiple .NET implementations and versions.</span></span>

## <a name="modifications-to-the-public-contract"></a><span data-ttu-id="f424d-120">公用合約的修改</span><span class="sxs-lookup"><span data-stu-id="f424d-120">Modifications to the public contract</span></span>

<span data-ttu-id="f424d-121">此類別目錄中的變更會修改類型的公用介面區。</span><span class="sxs-lookup"><span data-stu-id="f424d-121">Changes in this category modify the public surface area of a type.</span></span> <span data-ttu-id="f424d-122">此類別中的大多數變更都是不允許的，因為它們違反了回溯相容性 (可讓使用舊版 API 開發的應用程式能夠在更新版本上執行而不必重新編譯的能力)。</span><span class="sxs-lookup"><span data-stu-id="f424d-122">Most of the changes in this category are disallowed since they violate *backwards compatibility* (the ability of an application that was developed with a previous version of an API to execute without recompilation on a later version).</span></span>

### <a name="types"></a><span data-ttu-id="f424d-123">型別</span><span class="sxs-lookup"><span data-stu-id="f424d-123">Types</span></span>

- <span data-ttu-id="f424d-124">**允許✔️：當基底類型已經實作為介面時，從類型移除介面實**</span><span class="sxs-lookup"><span data-stu-id="f424d-124">✔️ **ALLOWED: Removing an interface implementation from a type when the interface is already implemented by a base type**</span></span>

- <span data-ttu-id="f424d-125">❓**需要判斷：將新的介面執行加入至類型**</span><span class="sxs-lookup"><span data-stu-id="f424d-125">❓ **REQUIRES JUDGMENT: Adding a new interface implementation to a type**</span></span>

  <span data-ttu-id="f424d-126">這是一個可接受的變更，因為它不會對現有的用戶端產生負面影響。</span><span class="sxs-lookup"><span data-stu-id="f424d-126">This is an acceptable change because it does not adversely affect existing clients.</span></span> <span data-ttu-id="f424d-127">對類型的任何變更都必須在此處定義的可接受變更的界限內運作，以使新實作維持可接受。</span><span class="sxs-lookup"><span data-stu-id="f424d-127">Any changes to the type must work within the boundaries of acceptable changes defined here for the new implementation to remain acceptable.</span></span> <span data-ttu-id="f424d-128">如果您要加入的介面會直接影響設計工具或序列化程式產生無法在低層級取用之程式碼或資料的能力，請格外小心。</span><span class="sxs-lookup"><span data-stu-id="f424d-128">Extreme caution is necessary when adding interfaces that directly affect the ability of a designer or serializer to generate code or data that cannot be consumed down-level.</span></span> <span data-ttu-id="f424d-129">其中一個範例是 <xref:System.Runtime.Serialization.ISerializable> 介面。</span><span class="sxs-lookup"><span data-stu-id="f424d-129">An example is the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

- <span data-ttu-id="f424d-130">❓**需要判斷：引進新的基類**</span><span class="sxs-lookup"><span data-stu-id="f424d-130">❓ **REQUIRES JUDGMENT: Introducing a new base class**</span></span>

  <span data-ttu-id="f424d-131">如果類型未引進任何新的[抽象](../../csharp/language-reference/keywords/abstract.md)成員，或變更現有類型的語義或行為，則可以在兩個現有類型之間引進階層。</span><span class="sxs-lookup"><span data-stu-id="f424d-131">A type can be introduced into a hierarchy between two existing types if it doesn't introduce any new [abstract](../../csharp/language-reference/keywords/abstract.md) members or change the semantics or behavior of existing types.</span></span> <span data-ttu-id="f424d-132">例如，在 .NET Framework 2.0 中，<xref:System.Data.Common.DbConnection> 類別成為 <xref:System.Data.SqlClient.SqlConnection> 的新基底類別，它先前直接衍生自 <xref:System.ComponentModel.Component>。</span><span class="sxs-lookup"><span data-stu-id="f424d-132">For example, in .NET Framework 2.0, the <xref:System.Data.Common.DbConnection> class became a new base class for <xref:System.Data.SqlClient.SqlConnection>, which had previously derived directly from <xref:System.ComponentModel.Component>.</span></span>

- <span data-ttu-id="f424d-133">**允許✔️：將類型從一個元件移至另**一個</span><span class="sxs-lookup"><span data-stu-id="f424d-133">✔️ **ALLOWED: Moving a type from one assembly to another**</span></span>

  <span data-ttu-id="f424d-134">*舊*元件必須以指向新元件的 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> 標記。</span><span class="sxs-lookup"><span data-stu-id="f424d-134">The *old* assembly must be marked with the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> that points to the new assembly.</span></span>

- <span data-ttu-id="f424d-135">**允許✔️：將[結構](../../csharp/language-reference/keywords/struct.md)類型變更為 `readonly struct` 類型**</span><span class="sxs-lookup"><span data-stu-id="f424d-135">✔️ **ALLOWED: Changing a [struct](../../csharp/language-reference/keywords/struct.md) type to a `readonly struct` type**</span></span>

  <span data-ttu-id="f424d-136">不允許將 `readonly struct` 類型變更為 `struct` 類型。</span><span class="sxs-lookup"><span data-stu-id="f424d-136">Changing a `readonly struct` type to a `struct` type is not allowed.</span></span>

- <span data-ttu-id="f424d-137">**允許✔️：當沒有*可存取*（公用或受保護）的函式時，將[Sealed](../../csharp/language-reference/keywords/sealed.md)或[abstract](../../csharp/language-reference/keywords/abstract.md)關鍵字新增至類型**</span><span class="sxs-lookup"><span data-stu-id="f424d-137">✔️ **ALLOWED: Adding the [sealed](../../csharp/language-reference/keywords/sealed.md) or [abstract](../../csharp/language-reference/keywords/abstract.md) keyword to a type when there are no *accessible* (public or protected) constructors**</span></span>

- <span data-ttu-id="f424d-138">**允許✔️：展開類型的可見度**</span><span class="sxs-lookup"><span data-stu-id="f424d-138">✔️ **ALLOWED: Expanding the visibility of a type**</span></span>

- <span data-ttu-id="f424d-139">不**允許 ❌：變更類型的命名空間或名稱**</span><span class="sxs-lookup"><span data-stu-id="f424d-139">❌ **DISALLOWED: Changing the namespace or name of a type**</span></span>

- <span data-ttu-id="f424d-140">不**允許 ❌：重新命名或移除公用類型**</span><span class="sxs-lookup"><span data-stu-id="f424d-140">❌ **DISALLOWED: Renaming or removing a public type**</span></span>

   <span data-ttu-id="f424d-141">這會中斷使用已重新命名或已移除之型別的所有程式碼。</span><span class="sxs-lookup"><span data-stu-id="f424d-141">This breaks all code that uses the renamed or removed type.</span></span>

- <span data-ttu-id="f424d-142">**不允許 ❌：變更列舉的基礎類型**</span><span class="sxs-lookup"><span data-stu-id="f424d-142">❌ **DISALLOWED: Changing the underlying type of an enumeration**</span></span>

   <span data-ttu-id="f424d-143">這是編譯時期和行為的中斷性變更，以及可以使屬性引數無法進行剖析的二進位中斷性變更。</span><span class="sxs-lookup"><span data-stu-id="f424d-143">This is a compile-time and behavioral breaking change as well as a binary breaking change that can make attribute arguments unparsable.</span></span>

- <span data-ttu-id="f424d-144">**不允許 ❌：密封先前未密封的類型**</span><span class="sxs-lookup"><span data-stu-id="f424d-144">❌ **DISALLOWED: Sealing a type that was previously unsealed**</span></span>

- <span data-ttu-id="f424d-145">**不允許 ❌：將介面新增至介面的基底類型集合**</span><span class="sxs-lookup"><span data-stu-id="f424d-145">❌ **DISALLOWED: Adding an interface to the set of base types of an interface**</span></span>

   <span data-ttu-id="f424d-146">如果介面實作先前未實作的介面，則實作介面原始版本的所有型別都會中斷。</span><span class="sxs-lookup"><span data-stu-id="f424d-146">If an interface implements an interface that it previously did not implement, all types that implemented the original version of the interface are broken.</span></span>

- <span data-ttu-id="f424d-147">❓**需要判斷：從一組衍生的介面中移除基類或介面的類別**</span><span class="sxs-lookup"><span data-stu-id="f424d-147">❓ **REQUIRES JUDGMENT: Removing a class from the set of base classes or an interface from the set of implemented interfaces**</span></span>

  <span data-ttu-id="f424d-148">介面移除規則有一個例外：您可以新增衍生自已移除之介面的介面實作。</span><span class="sxs-lookup"><span data-stu-id="f424d-148">There is one exception to the rule for interface removal: you can add the implementation of an interface that derives from the removed interface.</span></span> <span data-ttu-id="f424d-149">例如，如果型別或介面現在實作 <xref:System.ComponentModel.IComponent> (它會實作 <xref:System.IDisposable>)，則可以移除 <xref:System.IDisposable>。</span><span class="sxs-lookup"><span data-stu-id="f424d-149">For example, you can remove <xref:System.IDisposable> if the type or interface now implements <xref:System.ComponentModel.IComponent>, which implements <xref:System.IDisposable>.</span></span>

- <span data-ttu-id="f424d-150">不**允許 ❌：將 `readonly struct` 型別變更為[結構](../../csharp/language-reference/keywords/struct.md)型**別</span><span class="sxs-lookup"><span data-stu-id="f424d-150">❌ **DISALLOWED: Changing a `readonly struct` type to a [struct](../../csharp/language-reference/keywords/struct.md) type**</span></span>

  <span data-ttu-id="f424d-151">不過，允許將 `struct` 類型變更為 `readonly struct` 類型。</span><span class="sxs-lookup"><span data-stu-id="f424d-151">The change of a `struct` type to a `readonly struct` type is allowed, however.</span></span>

- <span data-ttu-id="f424d-152">不**允許 ❌：將[結構](../../csharp/language-reference/keywords/struct.md)型別變更為 `ref struct` 型別，** 反之亦然</span><span class="sxs-lookup"><span data-stu-id="f424d-152">❌ **DISALLOWED: Changing a [struct](../../csharp/language-reference/keywords/struct.md) type to a `ref struct` type, and vice versa**</span></span>

- <span data-ttu-id="f424d-153">不**允許 ❌：減少類型的可見度**</span><span class="sxs-lookup"><span data-stu-id="f424d-153">❌ **DISALLOWED: Reducing the visibility of a type**</span></span>

   <span data-ttu-id="f424d-154">但是，允許增加型別的可見性。</span><span class="sxs-lookup"><span data-stu-id="f424d-154">However, increasing the visibility of a type is allowed.</span></span>

### <a name="members"></a><span data-ttu-id="f424d-155">Members</span><span class="sxs-lookup"><span data-stu-id="f424d-155">Members</span></span>

- <span data-ttu-id="f424d-156">**允許✔️：展開非[虛擬](../../csharp/language-reference/keywords/sealed.md)成員的可見度**</span><span class="sxs-lookup"><span data-stu-id="f424d-156">✔️ **ALLOWED: Expanding the visibility of a member that is not [virtual](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="f424d-157">**允許✔️：將抽象成員加入至沒有*可存取*（公用或受保護）之函式的公用類型，或類型為[sealed](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="f424d-157">✔️ **ALLOWED: Adding an abstract member to a public type that has no *accessible* (public or protected) constructors, or the type is [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

  <span data-ttu-id="f424d-158">但是，不允許將抽象成員新增至具有可存取 (公用或受保護) 建構函式且不是 `sealed` 的型別。</span><span class="sxs-lookup"><span data-stu-id="f424d-158">However, adding an abstract member to a type that has accessible (public or protected) constructors and is not `sealed` is not allowed.</span></span>

- <span data-ttu-id="f424d-159">**允許✔️：當類型沒有可存取（公用或受保護）的函式，或類型已[密封](../../csharp/language-reference/keywords/sealed.md)時，限制[受保護](../../csharp/language-reference/keywords/protected.md)成員的可見度**</span><span class="sxs-lookup"><span data-stu-id="f424d-159">✔️ **ALLOWED: Restricting the visibility of a [protected](../../csharp/language-reference/keywords/protected.md) member when the type has no accessible (public or protected) constructors, or the type is [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="f424d-160">**允許✔️：將成員移至階層中較高的類別，而不是移除它的類型**</span><span class="sxs-lookup"><span data-stu-id="f424d-160">✔️ **ALLOWED: Moving a member into a class higher in the hierarchy than the type from which it was removed**</span></span>

- <span data-ttu-id="f424d-161">**允許✔️：新增或移除覆寫**</span><span class="sxs-lookup"><span data-stu-id="f424d-161">✔️ **ALLOWED: Adding or removing an override**</span></span>

  <span data-ttu-id="f424d-162">覆寫的引進可能會導致先前的取用者在呼叫[base](../../csharp/language-reference/keywords/base.md)時略過覆寫。</span><span class="sxs-lookup"><span data-stu-id="f424d-162">Introducing an override might cause previous consumers to skip over the override when calling [base](../../csharp/language-reference/keywords/base.md).</span></span>

- <span data-ttu-id="f424d-163">**允許✔️：將函式新增至類別，以及如果類別先前沒有任何的函式，則為無參數的**函式</span><span class="sxs-lookup"><span data-stu-id="f424d-163">✔️ **ALLOWED: Adding a constructor to a class, along with a parameterless constructor if the class previously had no constructors**</span></span>

   <span data-ttu-id="f424d-164">但是，不允許將建構函式新增至先前沒有建構函式且沒有新增無參數建構函式的類別。</span><span class="sxs-lookup"><span data-stu-id="f424d-164">However, adding a constructor to a class that previously had no constructors *without* adding the parameterless constructor is not allowed.</span></span>

- <span data-ttu-id="f424d-165">**允許✔️：將成員從[abstract](../../csharp/language-reference/keywords/abstract.md)變更為[virtual](../../csharp/language-reference/keywords/virtual.md)**</span><span class="sxs-lookup"><span data-stu-id="f424d-165">✔️ **ALLOWED: Changing a member from [abstract](../../csharp/language-reference/keywords/abstract.md) to [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

- <span data-ttu-id="f424d-166">**允許✔️：從 `ref readonly` 變更為 `ref` 傳回值（虛擬方法或介面除外）**</span><span class="sxs-lookup"><span data-stu-id="f424d-166">✔️ **ALLOWED: Changing from a `ref readonly` to a `ref` return value (except for virtual methods or interfaces)**</span></span>

- <span data-ttu-id="f424d-167">**允許✔️：除非欄位的靜態類型是可變的實數值型別，否則從欄位移除[readonly](../../csharp/language-reference/keywords/readonly.md)**</span><span class="sxs-lookup"><span data-stu-id="f424d-167">✔️ **ALLOWED: Removing [readonly](../../csharp/language-reference/keywords/readonly.md) from a field, unless the static type of the field is a mutable value type**</span></span>

- <span data-ttu-id="f424d-168">**允許✔️：呼叫先前未定義的新事件**</span><span class="sxs-lookup"><span data-stu-id="f424d-168">✔️ **ALLOWED: Calling a new event that wasn't previously defined**</span></span>

- <span data-ttu-id="f424d-169">❓**需要判斷：將新的實例欄位加入至類型**</span><span class="sxs-lookup"><span data-stu-id="f424d-169">❓ **REQUIRES JUDGMENT: Adding a new instance field to a type**</span></span>

   <span data-ttu-id="f424d-170">此變更會影響序列化。</span><span class="sxs-lookup"><span data-stu-id="f424d-170">This change impacts serialization.</span></span>

- <span data-ttu-id="f424d-171">不**允許 ❌：重新命名或移除公用成員或參數**</span><span class="sxs-lookup"><span data-stu-id="f424d-171">❌ **DISALLOWED: Renaming or removing a public member or parameter**</span></span>

   <span data-ttu-id="f424d-172">這會中斷使用已重新命名或已移除之成員或參數的所有程式碼。</span><span class="sxs-lookup"><span data-stu-id="f424d-172">This breaks all code that uses the renamed or removed member, or parameter.</span></span>

   <span data-ttu-id="f424d-173">這包括從屬性移除或重新命名 getter 或 setter，以及重新命名或移除列舉成員。</span><span class="sxs-lookup"><span data-stu-id="f424d-173">This includes removing or renaming a getter or setter from a property, as well as renaming or removing enumeration members.</span></span>

- <span data-ttu-id="f424d-174">**不允許 ❌：將成員新增至介面**</span><span class="sxs-lookup"><span data-stu-id="f424d-174">❌ **DISALLOWED: Adding a member to an interface**</span></span>

- <span data-ttu-id="f424d-175">不**允許 ❌：變更公用常數或列舉成員的值**</span><span class="sxs-lookup"><span data-stu-id="f424d-175">❌ **DISALLOWED: Changing the value of a public constant or enumeration member**</span></span>

- <span data-ttu-id="f424d-176">不**允許 ❌：變更屬性、欄位、參數或傳回值的類型**</span><span class="sxs-lookup"><span data-stu-id="f424d-176">❌ **DISALLOWED: Changing the type of a property, field, parameter, or return value**</span></span>

- <span data-ttu-id="f424d-177">不**允許的 ❌：新增、移除或變更參數的順序**</span><span class="sxs-lookup"><span data-stu-id="f424d-177">❌ **DISALLOWED: Adding, removing, or changing the order of parameters**</span></span>

- <span data-ttu-id="f424d-178">不**允許 ❌：從參數新增或移除[in](../../csharp/language-reference/keywords/in.md)、 [out](../../csharp/language-reference/keywords/out.md)或[ref](../../csharp/language-reference/keywords/ref.md)關鍵字**</span><span class="sxs-lookup"><span data-stu-id="f424d-178">❌ **DISALLOWED: Adding or removing the [in](../../csharp/language-reference/keywords/in.md), [out](../../csharp/language-reference/keywords/out.md) , or [ref](../../csharp/language-reference/keywords/ref.md) keyword from a parameter**</span></span>

- <span data-ttu-id="f424d-179">不**允許 ❌：重新具名引數（包括變更其大小寫）**</span><span class="sxs-lookup"><span data-stu-id="f424d-179">❌ **DISALLOWED: Renaming a parameter (including changing its case)**</span></span>

  <span data-ttu-id="f424d-180">這會視為中斷的原因有二：</span><span class="sxs-lookup"><span data-stu-id="f424d-180">This is considered breaking for two reasons:</span></span>

  - <span data-ttu-id="f424d-181">它中斷了晚期繫結的案例，例如 Visual Basic 中的晚期繫結功能和 C# 中的 [dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type)。</span><span class="sxs-lookup"><span data-stu-id="f424d-181">It breaks late-bound scenarios such as the late binding feature in Visual Basic and [dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) in C#.</span></span>

  - <span data-ttu-id="f424d-182">當開發人員使用[具名引數](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments)時，它會中斷[來源相容性](categories.md#source-compatibility)。</span><span class="sxs-lookup"><span data-stu-id="f424d-182">It breaks [source compatibility](categories.md#source-compatibility) when developers use [named arguments](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).</span></span>

- <span data-ttu-id="f424d-183">不**允許 ❌：從 `ref` 傳回值變更為 `ref readonly` 傳回值**</span><span class="sxs-lookup"><span data-stu-id="f424d-183">❌ **DISALLOWED: Changing from a `ref` return value to a `ref readonly` return value**</span></span>

- <span data-ttu-id="f424d-184">不**允許 ❌️：從 `ref readonly` 變更為虛擬方法或介面上的 `ref` 傳回值**</span><span class="sxs-lookup"><span data-stu-id="f424d-184">❌️ **DISALLOWED: Changing from a `ref readonly` to a `ref` return value on a virtual method or interface**</span></span>

- <span data-ttu-id="f424d-185">不**允許 ❌：從成員新增或移除[抽象](../../csharp/language-reference/keywords/abstract.md)**</span><span class="sxs-lookup"><span data-stu-id="f424d-185">❌ **DISALLOWED: Adding or removing [abstract](../../csharp/language-reference/keywords/abstract.md) from a member**</span></span>

- <span data-ttu-id="f424d-186">不**允許 ❌：從成員移除[虛擬](../../csharp/language-reference/keywords/virtual.md)關鍵字**</span><span class="sxs-lookup"><span data-stu-id="f424d-186">❌ **DISALLOWED: Removing the [virtual](../../csharp/language-reference/keywords/virtual.md) keyword from a member**</span></span>

  <span data-ttu-id="f424d-187">雖然這通常不是一個中斷性變更，因為 C# 編譯器傾向於發出 [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) 中繼語言 (IL) 指令以呼叫非虛擬方法 (`callvirt` 會執行 Null 檢查，而正常呼叫不會)，由於以下幾個原因，此行為並不是不變的：</span><span class="sxs-lookup"><span data-stu-id="f424d-187">While this often is not a breaking change because the C# compiler tends to emit [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) Intermediate Language (IL) instructions to call non-virtual methods (`callvirt` performs a null check, while a normal call doesn't), this behavior is not invariable for several reasons:</span></span>
  - <span data-ttu-id="f424d-188">C# 不是 .NET 以其為目標的唯一語言。</span><span class="sxs-lookup"><span data-stu-id="f424d-188">C# is not the only language that .NET targets.</span></span>

  - <span data-ttu-id="f424d-189">只要目標方法為非虛擬且可能不是 Null 時 (例如透過 [?. null 傳播運算子](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)存取的方法)，C# 編譯器就會漸漸地嘗試將 `callvirt` 最佳化為正常呼叫。</span><span class="sxs-lookup"><span data-stu-id="f424d-189">The C# compiler increasingly tries to optimize `callvirt` to a normal call whenever the target method is non-virtual and is probably not null (such as a method accessed through the [?. null propagation operator](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).</span></span>

  <span data-ttu-id="f424d-190">使方法成為虛擬表示取用者程式碼通常最後會以非虛擬方式呼叫它。</span><span class="sxs-lookup"><span data-stu-id="f424d-190">Making a method virtual means that the consumer code would often end up calling it non-virtually.</span></span>

- <span data-ttu-id="f424d-191">不**允許 ❌：將[虛擬](../../csharp/language-reference/keywords/virtual.md)關鍵字新增至成員**</span><span class="sxs-lookup"><span data-stu-id="f424d-191">❌ **DISALLOWED: Adding the [virtual](../../csharp/language-reference/keywords/virtual.md) keyword to a member**</span></span>

- <span data-ttu-id="f424d-192">不**允許 ❌：使虛擬成員成為抽象**</span><span class="sxs-lookup"><span data-stu-id="f424d-192">❌ **DISALLOWED: Making a virtual member abstract**</span></span>

  <span data-ttu-id="f424d-193">[虛擬成員](../../csharp/language-reference/keywords/virtual.md)提供了一種方法實作，可以由衍生類別覆寫。</span><span class="sxs-lookup"><span data-stu-id="f424d-193">A [virtual member](../../csharp/language-reference/keywords/virtual.md) provides a method implementation that *can be* overridden by a derived class.</span></span> <span data-ttu-id="f424d-194">[抽象成員](../../csharp/language-reference/keywords/abstract.md)不提供任何實作，且必須被覆寫。</span><span class="sxs-lookup"><span data-stu-id="f424d-194">An [abstract member](../../csharp/language-reference/keywords/abstract.md) provides no implementation and *must be* overridden.</span></span>

- <span data-ttu-id="f424d-195">❌ 不**允許：將抽象成員加入具有可存取（公用或受保護）之函式且未[密封](../../csharp/language-reference/keywords/sealed.md)的公用類型**</span><span class="sxs-lookup"><span data-stu-id="f424d-195">❌ **DISALLOWED: Adding an abstract member to a public type that has accessible (public or protected) constructors and that is not [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="f424d-196">不**允許 ❌：從成員新增或移除[靜態](../../csharp/language-reference/keywords/static.md)關鍵字**</span><span class="sxs-lookup"><span data-stu-id="f424d-196">❌ **DISALLOWED: Adding or removing the [static](../../csharp/language-reference/keywords/static.md) keyword from a member**</span></span>

- <span data-ttu-id="f424d-197">❌ 不**允許：新增可排除現有多載並定義不同行為**的多載</span><span class="sxs-lookup"><span data-stu-id="f424d-197">❌ **DISALLOWED: Adding an overload that precludes an existing overload and defines a different behavior**</span></span>

  <span data-ttu-id="f424d-198">這會中斷繫結到先前多載的現有用戶端。</span><span class="sxs-lookup"><span data-stu-id="f424d-198">This breaks existing clients that were bound to the previous overload.</span></span> <span data-ttu-id="f424d-199">例如，如果某個類別具有接受 <xref:System.UInt32> 的方法的單一版本，則現有的取用者在傳遞 <xref:System.Int32> 值時將成功繫結至該多載。</span><span class="sxs-lookup"><span data-stu-id="f424d-199">For example, if a class has a single version of a method that accepts a <xref:System.UInt32>, an existing consumer will successfully bind to that overload when passing a <xref:System.Int32> value.</span></span> <span data-ttu-id="f424d-200">但是，如果新增接受 <xref:System.Int32> 的多載，則在重新編譯或使用晚期繫結時，編譯器現在會繫結至新的多載。</span><span class="sxs-lookup"><span data-stu-id="f424d-200">However, if you add an overload that accepts an <xref:System.Int32>, when recompiling or using late-binding, the compiler now binds to the new overload.</span></span> <span data-ttu-id="f424d-201">如果產生不同的行為，這是一個中斷性變更。</span><span class="sxs-lookup"><span data-stu-id="f424d-201">If different behavior results, this is a breaking change.</span></span>

- <span data-ttu-id="f424d-202">**不允許 ❌：將函式新增至先前沒有任何函式的類別，而不加入無參數的**函式</span><span class="sxs-lookup"><span data-stu-id="f424d-202">❌ **DISALLOWED: Adding a constructor to a class that previously had no constructor without adding the parameterless constructor**</span></span>

- <span data-ttu-id="f424d-203">不**允許 ❌️：將[readonly](../../csharp/language-reference/keywords/readonly.md)加入至欄位**</span><span class="sxs-lookup"><span data-stu-id="f424d-203">❌️ **DISALLOWED: Adding [readonly](../../csharp/language-reference/keywords/readonly.md) to a field**</span></span>

- <span data-ttu-id="f424d-204">不**允許 ❌：減少成員的可見度**</span><span class="sxs-lookup"><span data-stu-id="f424d-204">❌ **DISALLOWED: Reducing the visibility of a member**</span></span>

   <span data-ttu-id="f424d-205">這包括減少[受保護](../../csharp/language-reference/keywords/protected.md)成員的可見度（當有*可存取*的（`public` 或 `protected`）的函式，且該類型*不*是[密封](../../csharp/language-reference/keywords/sealed.md)的。</span><span class="sxs-lookup"><span data-stu-id="f424d-205">This includes reducing the visibility of a [protected](../../csharp/language-reference/keywords/protected.md) member when there are *accessible* (`public` or `protected`) constructors and the type is *not* [sealed](../../csharp/language-reference/keywords/sealed.md).</span></span> <span data-ttu-id="f424d-206">如果不是這種情況，則允許降低受保護成員的可見性。</span><span class="sxs-lookup"><span data-stu-id="f424d-206">If this is not the case, reducing the visibility of a protected member is allowed.</span></span>

   <span data-ttu-id="f424d-207">允許增加成員的可見度。</span><span class="sxs-lookup"><span data-stu-id="f424d-207">Increasing the visibility of a member is allowed.</span></span>

- <span data-ttu-id="f424d-208">不**允許 ❌：變更成員的類型**</span><span class="sxs-lookup"><span data-stu-id="f424d-208">❌ **DISALLOWED: Changing the type of a member**</span></span>

   <span data-ttu-id="f424d-209">無法修改方法的傳回值，或屬性或欄位的型別。</span><span class="sxs-lookup"><span data-stu-id="f424d-209">The return value of a method or the type of a property or field cannot be modified.</span></span> <span data-ttu-id="f424d-210">例如，傳回 <xref:System.Object> 之方法的簽章不能變更為傳回 <xref:System.String>，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="f424d-210">For example, the signature of a method that returns an <xref:System.Object> cannot be changed to return a <xref:System.String>, or vice versa.</span></span>

- <span data-ttu-id="f424d-211">**不允許 ❌：將欄位新增至先前沒有狀態的結構**</span><span class="sxs-lookup"><span data-stu-id="f424d-211">❌ **DISALLOWED: Adding a field to a struct that previously had no state**</span></span>

  <span data-ttu-id="f424d-212">只要變數型別是無狀態結構，明確指派規則就允許使用未初始化的變數。</span><span class="sxs-lookup"><span data-stu-id="f424d-212">Definite assignment rules allow the use of uninitialized variables so long as the variable type is a stateless struct.</span></span> <span data-ttu-id="f424d-213">如果將結構設定為具狀態，程式碼最後可能會遇到未初始化的資料。</span><span class="sxs-lookup"><span data-stu-id="f424d-213">If the struct is made stateful, code could end up with uninitialized data.</span></span> <span data-ttu-id="f424d-214">這可能是一個來源中斷和二進位中斷性變更。</span><span class="sxs-lookup"><span data-stu-id="f424d-214">This is both potentially a source breaking and a binary breaking change.</span></span>

- <span data-ttu-id="f424d-215">**不允許的 ❌：引發從未引發的現有事件**</span><span class="sxs-lookup"><span data-stu-id="f424d-215">❌ **DISALLOWED: Firing an existing event when it was never fired before**</span></span>

## <a name="behavioral-changes"></a><span data-ttu-id="f424d-216">行為變更</span><span class="sxs-lookup"><span data-stu-id="f424d-216">Behavioral changes</span></span>

### <a name="assemblies"></a><span data-ttu-id="f424d-217">組件</span><span class="sxs-lookup"><span data-stu-id="f424d-217">Assemblies</span></span>

- <span data-ttu-id="f424d-218">**允許✔️：當仍然支援相同的平臺時，讓元件可**攜</span><span class="sxs-lookup"><span data-stu-id="f424d-218">✔️ **ALLOWED: Making an assembly portable when the same platforms are still supported**</span></span>

- <span data-ttu-id="f424d-219">不**允許 ❌：變更元件的名稱**</span><span class="sxs-lookup"><span data-stu-id="f424d-219">❌ **DISALLOWED: Changing the name of an assembly**</span></span>
- <span data-ttu-id="f424d-220">**不允許 ❌：變更元件的公開金鑰**</span><span class="sxs-lookup"><span data-stu-id="f424d-220">❌ **DISALLOWED: Changing the public key of an assembly**</span></span>

### <a name="properties-fields-parameters-and-return-values"></a><span data-ttu-id="f424d-221">屬性、欄位、參數與傳回值</span><span class="sxs-lookup"><span data-stu-id="f424d-221">Properties, fields, parameters, and return values</span></span>

- <span data-ttu-id="f424d-222">**允許✔️：將屬性、欄位、傳回值或[輸出](../../csharp/language-reference/keywords/out-parameter-modifier.md)參數的值變更為更衍生的類型**</span><span class="sxs-lookup"><span data-stu-id="f424d-222">✔️ **ALLOWED: Changing the value of a property, field, return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter to a more derived type**</span></span>

  <span data-ttu-id="f424d-223">例如，傳回 <xref:System.Object> 型別的方法可以傳回 <xref:System.String> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="f424d-223">For example, a method that returns a type of <xref:System.Object> can return a <xref:System.String> instance.</span></span> <span data-ttu-id="f424d-224">(但是，無法變更方法簽章。)</span><span class="sxs-lookup"><span data-stu-id="f424d-224">(However, the method signature cannot change.)</span></span>

- <span data-ttu-id="f424d-225">**允許✔️：如果成員不是[虛擬](../../csharp/language-reference/keywords/virtual.md)，則增加屬性或參數的接受值範圍**</span><span class="sxs-lookup"><span data-stu-id="f424d-225">✔️ **ALLOWED: Increasing the range of accepted values for a property or parameter if the member is not [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

  <span data-ttu-id="f424d-226">雖然可以傳遞給方法的值範圍或成員所傳回的可以展開，但參數或成員類型不能。</span><span class="sxs-lookup"><span data-stu-id="f424d-226">While the range of values that can be passed to the method or are returned by the member can expand, the parameter or member type cannot.</span></span> <span data-ttu-id="f424d-227">例如，雖然傳遞至方法的值可以從 0-124 擴充至 0-255，但參數類型無法從 <xref:System.Byte> 變更為 <xref:System.Int32>。</span><span class="sxs-lookup"><span data-stu-id="f424d-227">For example, while the values passed to a method can expand from 0-124 to 0-255, the parameter type cannot change from <xref:System.Byte> to <xref:System.Int32>.</span></span>

- <span data-ttu-id="f424d-228">**不允許 ❌：如果成員是[虛擬](../../csharp/language-reference/keywords/virtual.md)的，則增加屬性或參數的接受值範圍**</span><span class="sxs-lookup"><span data-stu-id="f424d-228">❌ **DISALLOWED: Increasing the range of accepted values for a property or parameter if the member is [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

   <span data-ttu-id="f424d-229">此變更會中斷現有的覆寫成員，這些成員將無法在擴充的值範圍內正常執行。</span><span class="sxs-lookup"><span data-stu-id="f424d-229">This change breaks existing overridden members, which will not function correctly for the extended range of values.</span></span>

- <span data-ttu-id="f424d-230">不**允許 ❌：減少屬性或參數的接受值範圍**</span><span class="sxs-lookup"><span data-stu-id="f424d-230">❌ **DISALLOWED: Decreasing the range of accepted values for a property or parameter**</span></span>

- <span data-ttu-id="f424d-231">不**允許 ❌：增加屬性、欄位、傳回值或[輸出](../../csharp/language-reference/keywords/out-parameter-modifier.md)參數的傳回值範圍**</span><span class="sxs-lookup"><span data-stu-id="f424d-231">❌ **DISALLOWED: Increasing the range of returned values for a property, field, return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter**</span></span>

- <span data-ttu-id="f424d-232">不**允許 ❌：變更屬性、欄位、方法傳回值或[out](../../csharp/language-reference/keywords/out-parameter-modifier.md)參數的傳回值**</span><span class="sxs-lookup"><span data-stu-id="f424d-232">❌ **DISALLOWED: Changing the returned values for a property, field, method return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter**</span></span>

- <span data-ttu-id="f424d-233">不**允許 ❌：變更屬性、欄位或參數的預設值**</span><span class="sxs-lookup"><span data-stu-id="f424d-233">❌ **DISALLOWED: Changing the default value of a property, field, or parameter**</span></span>

- <span data-ttu-id="f424d-234">不**允許 ❌：變更數值傳回值**的有效位數</span><span class="sxs-lookup"><span data-stu-id="f424d-234">❌ **DISALLOWED: Changing the precision of a numeric return value**</span></span>

- <span data-ttu-id="f424d-235">❓**需要判斷：剖析輸入和擲回新例外狀況的變更（即使檔中未指定剖析行為也一樣**）</span><span class="sxs-lookup"><span data-stu-id="f424d-235">❓ **REQUIRES JUDGMENT: A change in the parsing of input and throwing new exceptions (even if parsing behavior is not specified in the documentation**</span></span>

### <a name="exceptions"></a><span data-ttu-id="f424d-236">例外狀況</span><span class="sxs-lookup"><span data-stu-id="f424d-236">Exceptions</span></span>

- <span data-ttu-id="f424d-237">允許✔️：擲回**比現有例外狀況更多的衍生例外**狀況</span><span class="sxs-lookup"><span data-stu-id="f424d-237">✔️ **ALLOWED: Throwing a more derived exception than an existing exception**</span></span>

  <span data-ttu-id="f424d-238">因為新的例外狀況是現有例外狀況的子類別，所以先前的例外狀況處理程式碼會繼續處理例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f424d-238">Because the new exception is a subclass of an existing exception, previous exception handling code continues to handle the exception.</span></span> <span data-ttu-id="f424d-239">例如，在 .NET Framework 4 中，文化特性建立和擷取方法已開始擲回 <xref:System.Globalization.CultureNotFoundException> 而不是 <xref:System.ArgumentException> (如果找不到文化特性)。</span><span class="sxs-lookup"><span data-stu-id="f424d-239">For example, in .NET Framework 4, culture creation and retrieval methods began to throw a <xref:System.Globalization.CultureNotFoundException> instead of an <xref:System.ArgumentException> if the culture could not be found.</span></span> <span data-ttu-id="f424d-240">因為 <xref:System.Globalization.CultureNotFoundException> 衍生自 <xref:System.ArgumentException>，所以這是一個可接受的變更。</span><span class="sxs-lookup"><span data-stu-id="f424d-240">Because <xref:System.Globalization.CultureNotFoundException> derives from <xref:System.ArgumentException>, this is an acceptable change.</span></span>

- <span data-ttu-id="f424d-241">允許✔️：擲回**比 <xref:System.NotSupportedException>、<xref:System.NotImplementedException>、更特定的例外狀況 <xref:System.NullReferenceException>**</span><span class="sxs-lookup"><span data-stu-id="f424d-241">✔️ **ALLOWED: Throwing a more specific exception than <xref:System.NotSupportedException>, <xref:System.NotImplementedException>, <xref:System.NullReferenceException>**</span></span>

- <span data-ttu-id="f424d-242">允許✔️：擲回**被視為無法**復原的例外狀況</span><span class="sxs-lookup"><span data-stu-id="f424d-242">✔️ **ALLOWED: Throwing an exception that is considered unrecoverable**</span></span>

  <span data-ttu-id="f424d-243">無法復原的例外狀況不應該攔截，而應該由高層級追補處理常式處理。</span><span class="sxs-lookup"><span data-stu-id="f424d-243">Unrecoverable exceptions should not be caught but instead should be handled by a high-level catch-all handler.</span></span> <span data-ttu-id="f424d-244">因此，使用者不應該擁有攔截這些明確例外狀況的程式碼。</span><span class="sxs-lookup"><span data-stu-id="f424d-244">Therefore, users are not expected to have code that catches these explicit exceptions.</span></span> <span data-ttu-id="f424d-245">無法復原的例外狀況有：</span><span class="sxs-lookup"><span data-stu-id="f424d-245">The unrecoverable exceptions are:</span></span>

  - <xref:System.AccessViolationException>
  - <xref:System.ExecutionEngineException>
  - <xref:System.Runtime.InteropServices.SEHException>
  - <xref:System.StackOverflowException>

- <span data-ttu-id="f424d-246">**允許✔️：在新的程式碼路徑中擲回新的例外**狀況</span><span class="sxs-lookup"><span data-stu-id="f424d-246">✔️ **ALLOWED: Throwing a new exception in a new code path**</span></span>

  <span data-ttu-id="f424d-247">例外狀況必須只套用至以新的參數值或狀態執行，而且不能由目標為舊版的現有程式碼執行的新程式碼路徑。</span><span class="sxs-lookup"><span data-stu-id="f424d-247">The exception must apply only to a new code-path that's executed with new parameter values or state and that can't be executed by existing code that targets the previous version.</span></span>

- <span data-ttu-id="f424d-248">**允許✔️：移除例外狀況以啟用更健全的行為或新案例**</span><span class="sxs-lookup"><span data-stu-id="f424d-248">✔️ **ALLOWED: Removing an exception to enable more robust behavior or new scenarios**</span></span>

  <span data-ttu-id="f424d-249">例如，之前只處理正值並擲回 <xref:System.ArgumentOutOfRangeException> 的 `Divide` 方法可以變更為支援負值和正值，而不擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f424d-249">For example, a `Divide` method that previously only handled positive values and threw an <xref:System.ArgumentOutOfRangeException> otherwise can be changed to support both negative and positive values without throwing an exception.</span></span>

- <span data-ttu-id="f424d-250">**允許✔️：變更錯誤訊息的文字**</span><span class="sxs-lookup"><span data-stu-id="f424d-250">✔️ **ALLOWED: Changing the text of an error message**</span></span>

  <span data-ttu-id="f424d-251">開發人員不應該依賴錯誤訊息的文字，這也會根據使用者的文化特性而變更。</span><span class="sxs-lookup"><span data-stu-id="f424d-251">Developers should not rely on the text of error messages, which also change based on the user's culture.</span></span>

- <span data-ttu-id="f424d-252">**不允許 ❌：在上述未列出的任何其他情況下擲回例外狀況**</span><span class="sxs-lookup"><span data-stu-id="f424d-252">❌ **DISALLOWED: Throwing an exception in any other case not listed above**</span></span>

- <span data-ttu-id="f424d-253">**不允許 ❌：移除以上未列出的任何其他案例中的例外狀況**</span><span class="sxs-lookup"><span data-stu-id="f424d-253">❌ **DISALLOWED: Removing an exception in any other case not listed above**</span></span>

### <a name="attributes"></a><span data-ttu-id="f424d-254">屬性</span><span class="sxs-lookup"><span data-stu-id="f424d-254">Attributes</span></span>

- <span data-ttu-id="f424d-255">**允許✔️：變更*無法*觀察的屬性值**</span><span class="sxs-lookup"><span data-stu-id="f424d-255">✔️ **ALLOWED: Changing the value of an attribute that is *not* observable**</span></span>

- <span data-ttu-id="f424d-256">\***不\*允許 ❌：變更可觀察的屬性值**</span><span class="sxs-lookup"><span data-stu-id="f424d-256">❌ **DISALLOWED: Changing the value of an attribute that *is* observable**</span></span>

- <span data-ttu-id="f424d-257">❓**需要判斷：移除屬性**</span><span class="sxs-lookup"><span data-stu-id="f424d-257">❓ **REQUIRES JUDGMENT: Removing an attribute**</span></span>

  <span data-ttu-id="f424d-258">在大部分情況下，移除屬性 (例如<xref:System.NonSerializedAttribute>) 是一個中斷性變更。</span><span class="sxs-lookup"><span data-stu-id="f424d-258">In most cases, removing an attribute (such as <xref:System.NonSerializedAttribute>) is a breaking change.</span></span>

## <a name="platform-support"></a><span data-ttu-id="f424d-259">平台支援</span><span class="sxs-lookup"><span data-stu-id="f424d-259">Platform support</span></span>

- <span data-ttu-id="f424d-260">**允許✔️：在先前不支援的平臺上支援**作業</span><span class="sxs-lookup"><span data-stu-id="f424d-260">✔️ **ALLOWED: Supporting an operation on a platform that was previously not supported**</span></span>

- <span data-ttu-id="f424d-261">❌**不允許：不支援或現在需要平臺上先前支援**之作業的特定 Service Pack</span><span class="sxs-lookup"><span data-stu-id="f424d-261">❌ **DISALLOWED: Not supporting or now requiring a specific service pack for an operation that was previously supported on a platform**</span></span>

## <a name="internal-implementation-changes"></a><span data-ttu-id="f424d-262">內部實作的變更</span><span class="sxs-lookup"><span data-stu-id="f424d-262">Internal implementation changes</span></span>

- <span data-ttu-id="f424d-263">❓**需要判斷：變更內部類型的介面區**</span><span class="sxs-lookup"><span data-stu-id="f424d-263">❓ **REQUIRES JUDGMENT: Changing the surface area of an internal type**</span></span>

   <span data-ttu-id="f424d-264">通常允許此類變更，儘管它們可能會中斷私人反映。</span><span class="sxs-lookup"><span data-stu-id="f424d-264">Such changes are generally allowed, although they break private reflection.</span></span> <span data-ttu-id="f424d-265">在一些熱門的協力廠商程式庫或大量開發人員依賴內部 API 的案例中，可能不允許此類變更。</span><span class="sxs-lookup"><span data-stu-id="f424d-265">In some cases, where popular third-party libraries or a large number of developers depend on the internal APIs, such changes may not be allowed.</span></span>

- <span data-ttu-id="f424d-266">❓**需要判斷：變更成員的內部執行**</span><span class="sxs-lookup"><span data-stu-id="f424d-266">❓ **REQUIRES JUDGMENT: Changing the internal implementation of a member**</span></span>

  <span data-ttu-id="f424d-267">通常允許這些變更，儘管它們可能會中斷私人反映。</span><span class="sxs-lookup"><span data-stu-id="f424d-267">These changes are generally allowed, although they break private reflection.</span></span> <span data-ttu-id="f424d-268">在一些客戶程式碼經常依賴私人反映或變更引進非預期之副作用的情況下，可能不允許這些變更。</span><span class="sxs-lookup"><span data-stu-id="f424d-268">In some cases, where customer code frequently depends on private reflection or where the change introduces unintended side effects, these changes may not be allowed.</span></span>

- <span data-ttu-id="f424d-269">**允許✔️：改善作業的效能**</span><span class="sxs-lookup"><span data-stu-id="f424d-269">✔️ **ALLOWED: Improving the performance of an operation**</span></span>

   <span data-ttu-id="f424d-270">修改作業效能的能力是很重要的，但此類變更可能會中斷仰賴目前作業速度的程式碼。</span><span class="sxs-lookup"><span data-stu-id="f424d-270">The ability to modify the performance of an operation is essential, but such changes can break code that relies upon the current speed of an operation.</span></span> <span data-ttu-id="f424d-271">對於仰賴非同步作業時間的程式碼尤其如此。</span><span class="sxs-lookup"><span data-stu-id="f424d-271">This is particularly true of code that depends on the timing of asynchronous operations.</span></span> <span data-ttu-id="f424d-272">效能變更應該不會影響其他有問題的 API 行為;否則，變更將會中斷。</span><span class="sxs-lookup"><span data-stu-id="f424d-272">The performance change should have no effect on other behavior of the API in question; otherwise, the change will be breaking.</span></span>

- <span data-ttu-id="f424d-273">**允許✔️：間接（而且通常會有負面）變更作業的效能**</span><span class="sxs-lookup"><span data-stu-id="f424d-273">✔️ **ALLOWED: Indirectly (and often adversely) changing the performance of an operation**</span></span>

  <span data-ttu-id="f424d-274">如果由於某些其他原因而未將相關變更歸類為中斷，則這是可以接受的。</span><span class="sxs-lookup"><span data-stu-id="f424d-274">If the change in question is not categorized as breaking for some other reason, this is acceptable.</span></span> <span data-ttu-id="f424d-275">通常，需要採取可能包括額外的作業或新增新功能的動作。</span><span class="sxs-lookup"><span data-stu-id="f424d-275">Often, actions need to be taken that may include extra operations or that add new functionality.</span></span> <span data-ttu-id="f424d-276">這幾乎一律會影響效能，但對於使相關 API 如預期般運作至關重要。</span><span class="sxs-lookup"><span data-stu-id="f424d-276">This will almost always affect performance but may be essential to make the API in question function as expected.</span></span>

- <span data-ttu-id="f424d-277">不**允許 ❌：將同步 API 變更為非同步（反之亦然）**</span><span class="sxs-lookup"><span data-stu-id="f424d-277">❌ **DISALLOWED: Changing a synchronous API to asynchronous (and vice versa)**</span></span>

## <a name="code-changes"></a><span data-ttu-id="f424d-278">程式碼變更</span><span class="sxs-lookup"><span data-stu-id="f424d-278">Code changes</span></span>

- <span data-ttu-id="f424d-279">**允許✔️：將[params](../../csharp/language-reference/keywords/params.md)新增至參數**</span><span class="sxs-lookup"><span data-stu-id="f424d-279">✔️ **ALLOWED: Adding [params](../../csharp/language-reference/keywords/params.md) to a parameter**</span></span>

- <span data-ttu-id="f424d-280">不**允許 ❌：將[結構](../../csharp/language-reference/keywords/struct.md)變更為[類別](../../csharp/language-reference/keywords/class.md)，反之亦然**</span><span class="sxs-lookup"><span data-stu-id="f424d-280">❌ **DISALLOWED: Changing a [struct](../../csharp/language-reference/keywords/struct.md) to a [class](../../csharp/language-reference/keywords/class.md) and vice versa**</span></span>

- <span data-ttu-id="f424d-281">不**允許 ❌：將[Checked](../../csharp/language-reference/keywords/virtual.md)關鍵字新增至程式碼區塊**</span><span class="sxs-lookup"><span data-stu-id="f424d-281">❌ **DISALLOWED: Adding the [checked](../../csharp/language-reference/keywords/virtual.md) keyword to a code block**</span></span>

   <span data-ttu-id="f424d-282">此變更可能會導致先前執行的程式碼擲回 <xref:System.OverflowException> 且無法接受。</span><span class="sxs-lookup"><span data-stu-id="f424d-282">This change may cause code that previously executed to throw an <xref:System.OverflowException> and is unacceptable.</span></span>

- <span data-ttu-id="f424d-283">不**允許 ❌：從參數移除[params](../../csharp/language-reference/keywords/params.md)**</span><span class="sxs-lookup"><span data-stu-id="f424d-283">❌ **DISALLOWED: Removing [params](../../csharp/language-reference/keywords/params.md) from a parameter**</span></span>

- <span data-ttu-id="f424d-284">不**允許 ❌：變更引發事件的順序**</span><span class="sxs-lookup"><span data-stu-id="f424d-284">❌ **DISALLOWED: Changing the order in which events are fired**</span></span>

  <span data-ttu-id="f424d-285">開發人員可以合理地預期事件以相同的順序引發，而開發人員程式碼經常會取決於事件的引發順序。</span><span class="sxs-lookup"><span data-stu-id="f424d-285">Developers can reasonably expect events to fire in the same order, and developer code frequently depends on the order in which events are fired.</span></span>

- <span data-ttu-id="f424d-286">不**允許 ❌：移除指定動作上引發的事件**</span><span class="sxs-lookup"><span data-stu-id="f424d-286">❌ **DISALLOWED: Removing the raising of an event on a given action**</span></span>

- <span data-ttu-id="f424d-287">**不允許 ❌：變更給定事件的呼叫**次數</span><span class="sxs-lookup"><span data-stu-id="f424d-287">❌ **DISALLOWED: Changing the number of times given events are called**</span></span>

- <span data-ttu-id="f424d-288">**不允許 ❌：將 <xref:System.FlagsAttribute> 新增至列舉類型**</span><span class="sxs-lookup"><span data-stu-id="f424d-288">❌ **DISALLOWED: Adding the <xref:System.FlagsAttribute> to an enumeration type**</span></span>
