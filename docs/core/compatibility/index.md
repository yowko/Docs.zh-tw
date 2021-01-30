---
title: 中斷性變更的類型
description: 瞭解 .NET 如何嘗試為開發人員提供跨 .NET 版本的相容性，以及何種變更視為重大變更。
ms.date: 01/28/2021
ms.openlocfilehash: d539a82b21abc4df8d726673ef728020f36551bf
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216034"
---
# <a name="changes-that-affect-compatibility"></a><span data-ttu-id="e979b-103">影響相容性的變更</span><span class="sxs-lookup"><span data-stu-id="e979b-103">Changes that affect compatibility</span></span>

<span data-ttu-id="e979b-104">在整個歷程記錄中，.NET 已嘗試維持從版本到版本的高階相容性，以及跨 .NET 的各項執行。</span><span class="sxs-lookup"><span data-stu-id="e979b-104">Throughout its history, .NET has attempted to maintain a high level of compatibility from version to version and across implementations of .NET.</span></span> <span data-ttu-id="e979b-105">相較于 .NET Framework，雖然 .NET 5 (和 .NET Core) 和更新版本可視為新的技術，但是有兩個主要因素會限制這項 .NET 的執行能力與 .NET Framework 相互分離：</span><span class="sxs-lookup"><span data-stu-id="e979b-105">Although .NET 5 (and .NET Core) and later versions can be considered as a new technology compared to .NET Framework, two major factors limit the ability of this implementation of .NET to diverge from .NET Framework:</span></span>

- <span data-ttu-id="e979b-106">最初開發或是繼續開發 .NET Framework 應用程式的大量開發人員。</span><span class="sxs-lookup"><span data-stu-id="e979b-106">A large number of developers either originally developed or continue to develop .NET Framework applications.</span></span> <span data-ttu-id="e979b-107">他們預期跨 .NET 實作有一致的行為。</span><span class="sxs-lookup"><span data-stu-id="e979b-107">They expect consistent behavior across .NET implementations.</span></span>

- <span data-ttu-id="e979b-108">.NET Standard 程式庫專案可讓開發人員建立以 .NET Framework 和 .NET 5 (和 .NET Core) 和更新版本所共用的通用 Api 為目標的程式庫。</span><span class="sxs-lookup"><span data-stu-id="e979b-108">.NET Standard library projects allow developers to create libraries that target common APIs shared by .NET Framework and .NET 5 (and .NET Core) and later versions.</span></span> <span data-ttu-id="e979b-109">開發人員預期在 .NET 5 應用程式中使用的程式庫，其行為應該與 .NET Framework 應用程式中使用的相同程式庫相同。</span><span class="sxs-lookup"><span data-stu-id="e979b-109">Developers expect that a library used in a .NET 5 application should behave identically to the same library used in a .NET Framework application.</span></span>

<span data-ttu-id="e979b-110">除了 .NET 執行的相容性之外，開發人員還預期在 .NET 的各版本之間有高階的相容性。</span><span class="sxs-lookup"><span data-stu-id="e979b-110">Along with compatibility across .NET implementations, developers expect a high level of compatibility across versions of a given implementation of .NET.</span></span> <span data-ttu-id="e979b-111">尤其是針對舊版 .NET Core 所撰寫的程式碼應該在 .NET 5 或更新版本上順暢地執行。</span><span class="sxs-lookup"><span data-stu-id="e979b-111">In particular, code written for an earlier version of .NET Core should run seamlessly on .NET 5 or a later version.</span></span> <span data-ttu-id="e979b-112">事實上，許多開發人員預期在新發行的 .NET 版本中找到的新 Api，也應該與引進這些 Api 的發行前版本相容。</span><span class="sxs-lookup"><span data-stu-id="e979b-112">In fact, many developers expect that the new APIs found in newly released versions of .NET should also be compatible with the pre-release versions in which those APIs were introduced.</span></span>

<span data-ttu-id="e979b-113">本文概述會影響相容性的變更，以及 .NET 小組評估各種變更類型的方式。</span><span class="sxs-lookup"><span data-stu-id="e979b-113">This article outlines changes that affect compatibility and the way in which the .NET team evaluates each type of change.</span></span> <span data-ttu-id="e979b-114">瞭解 .NET 團隊如何進行可能的重大變更，對於開啟可修改 [現有 .Net api](https://github.com/dotnet/runtime)行為的提取要求的開發人員而言特別有用。</span><span class="sxs-lookup"><span data-stu-id="e979b-114">Understanding how the .NET team approaches possible breaking changes is particularly helpful for developers who open pull requests that modify the behavior of [existing .NET APIs](https://github.com/dotnet/runtime).</span></span>

<span data-ttu-id="e979b-115">下列各節說明對 .NET Api 所做的變更分類，以及其對應用程式相容性的影響。</span><span class="sxs-lookup"><span data-stu-id="e979b-115">The following sections describe the categories of changes made to .NET APIs and their impact on application compatibility.</span></span> <span data-ttu-id="e979b-116">您可以✔️、不允許 ❌ 或需要判斷變更，以及如何❓上一個行為的可預測、明顯和一致的評估。</span><span class="sxs-lookup"><span data-stu-id="e979b-116">Changes are either allowed ✔️, disallowed ❌, or require judgment and an evaluation of how predictable, obvious, and consistent the previous behavior was ❓.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="e979b-117">除了提供 .NET 程式庫變更的指南之外，程式庫開發人員也可以使用這些準則來評估其以多個 .NET 執行和版本為目標的程式庫變更。</span><span class="sxs-lookup"><span data-stu-id="e979b-117">In addition to serving as a guide to how changes to .NET libraries are evaluated, library developers can also use these criteria to evaluate changes to their libraries that target multiple .NET implementations and versions.</span></span>
> - <span data-ttu-id="e979b-118">如需相容性類別的詳細資訊（例如，向前和回溯相容性），請參閱 [相容性](categories.md)。</span><span class="sxs-lookup"><span data-stu-id="e979b-118">For information about the compatibility categories, for example, forward and backwards compatibility, see [Compatibility](categories.md).</span></span>

## <a name="modifications-to-the-public-contract"></a><span data-ttu-id="e979b-119">公用合約的修改</span><span class="sxs-lookup"><span data-stu-id="e979b-119">Modifications to the public contract</span></span>

<span data-ttu-id="e979b-120">此類別中的變更會修改某個類型的公用介面區。</span><span class="sxs-lookup"><span data-stu-id="e979b-120">Changes in this category modify the public surface area of a type.</span></span> <span data-ttu-id="e979b-121">此類別中的大多數變更都是不允許的，因為它們違反了回溯相容性 (可讓使用舊版 API 開發的應用程式能夠在更新版本上執行而不必重新編譯的能力)。</span><span class="sxs-lookup"><span data-stu-id="e979b-121">Most of the changes in this category are disallowed since they violate *backwards compatibility* (the ability of an application that was developed with a previous version of an API to execute without recompilation on a later version).</span></span>

### <a name="types"></a><span data-ttu-id="e979b-122">類型</span><span class="sxs-lookup"><span data-stu-id="e979b-122">Types</span></span>

- <span data-ttu-id="e979b-123">✔️ **允許：當介面已由基底類型執行時，從類型中移除介面實** 作為</span><span class="sxs-lookup"><span data-stu-id="e979b-123">✔️ **ALLOWED: Removing an interface implementation from a type when the interface is already implemented by a base type**</span></span>

- <span data-ttu-id="e979b-124">❓**需要判斷：將新的介面實作為型** 別</span><span class="sxs-lookup"><span data-stu-id="e979b-124">❓ **REQUIRES JUDGMENT: Adding a new interface implementation to a type**</span></span>

  <span data-ttu-id="e979b-125">這是一個可接受的變更，因為它不會對現有的用戶端產生負面影響。</span><span class="sxs-lookup"><span data-stu-id="e979b-125">This is an acceptable change because it does not adversely affect existing clients.</span></span> <span data-ttu-id="e979b-126">對類型的任何變更都必須在此處定義的可接受變更的界限內運作，以使新實作維持可接受。</span><span class="sxs-lookup"><span data-stu-id="e979b-126">Any changes to the type must work within the boundaries of acceptable changes defined here for the new implementation to remain acceptable.</span></span> <span data-ttu-id="e979b-127">如果您要加入的介面會直接影響設計工具或序列化程式產生無法在低層級取用之程式碼或資料的能力，請格外小心。</span><span class="sxs-lookup"><span data-stu-id="e979b-127">Extreme caution is necessary when adding interfaces that directly affect the ability of a designer or serializer to generate code or data that cannot be consumed down-level.</span></span> <span data-ttu-id="e979b-128">其中一個範例是 <xref:System.Runtime.Serialization.ISerializable> 介面。</span><span class="sxs-lookup"><span data-stu-id="e979b-128">An example is the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

- <span data-ttu-id="e979b-129">❓ **需要判斷：引進新的基類**</span><span class="sxs-lookup"><span data-stu-id="e979b-129">❓ **REQUIRES JUDGMENT: Introducing a new base class**</span></span>

  <span data-ttu-id="e979b-130">如果型別不會引進任何新的 [抽象](../../csharp/language-reference/keywords/abstract.md) 成員，或變更現有型別的語義或行為，則可以將型別引進兩個現有的型別。</span><span class="sxs-lookup"><span data-stu-id="e979b-130">A type can be introduced into a hierarchy between two existing types if it doesn't introduce any new [abstract](../../csharp/language-reference/keywords/abstract.md) members or change the semantics or behavior of existing types.</span></span> <span data-ttu-id="e979b-131">例如，在 .NET Framework 2.0 中，<xref:System.Data.Common.DbConnection> 類別成為 <xref:System.Data.SqlClient.SqlConnection> 的新基底類別，它先前直接衍生自 <xref:System.ComponentModel.Component>。</span><span class="sxs-lookup"><span data-stu-id="e979b-131">For example, in .NET Framework 2.0, the <xref:System.Data.Common.DbConnection> class became a new base class for <xref:System.Data.SqlClient.SqlConnection>, which had previously derived directly from <xref:System.ComponentModel.Component>.</span></span>

- <span data-ttu-id="e979b-132">**允許✔️：將類型從某個元件移至另一個元件**</span><span class="sxs-lookup"><span data-stu-id="e979b-132">✔️ **ALLOWED: Moving a type from one assembly to another**</span></span>

  <span data-ttu-id="e979b-133">*舊* 的元件必須以 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> 指向新元件的來標記。</span><span class="sxs-lookup"><span data-stu-id="e979b-133">The *old* assembly must be marked with the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> that points to the new assembly.</span></span>

- <span data-ttu-id="e979b-134">**允許✔️：將 [結構](../../csharp/language-reference/builtin-types/struct.md)類型變更為 `readonly struct` 類型**</span><span class="sxs-lookup"><span data-stu-id="e979b-134">✔️ **ALLOWED: Changing a [struct](../../csharp/language-reference/builtin-types/struct.md) type to a `readonly struct` type**</span></span>

  <span data-ttu-id="e979b-135">`readonly struct`不允許將類型變更為 `struct` 類型。</span><span class="sxs-lookup"><span data-stu-id="e979b-135">Changing a `readonly struct` type to a `struct` type is not allowed.</span></span>

- <span data-ttu-id="e979b-136">✔️ **允許：當沒有 *可存取* 的 (公用或受保護) 函式時，將 [Sealed](../../csharp/language-reference/keywords/sealed.md)或 [abstract](../../csharp/language-reference/keywords/abstract.md)關鍵字加入至類型**</span><span class="sxs-lookup"><span data-stu-id="e979b-136">✔️ **ALLOWED: Adding the [sealed](../../csharp/language-reference/keywords/sealed.md) or [abstract](../../csharp/language-reference/keywords/abstract.md) keyword to a type when there are no *accessible* (public or protected) constructors**</span></span>

- <span data-ttu-id="e979b-137">**允許✔️：擴充類型的可見度**</span><span class="sxs-lookup"><span data-stu-id="e979b-137">✔️ **ALLOWED: Expanding the visibility of a type**</span></span>

- <span data-ttu-id="e979b-138">❌不 **允許：變更型別的命名空間或名稱**</span><span class="sxs-lookup"><span data-stu-id="e979b-138">❌ **DISALLOWED: Changing the namespace or name of a type**</span></span>

- <span data-ttu-id="e979b-139">❌不 **允許：重新命名或移除公用類型**</span><span class="sxs-lookup"><span data-stu-id="e979b-139">❌ **DISALLOWED: Renaming or removing a public type**</span></span>

   <span data-ttu-id="e979b-140">這會中斷使用已重新命名或已移除之型別的所有程式碼。</span><span class="sxs-lookup"><span data-stu-id="e979b-140">This breaks all code that uses the renamed or removed type.</span></span>

- <span data-ttu-id="e979b-141">❌**不允許：變更列舉的基礎類型**</span><span class="sxs-lookup"><span data-stu-id="e979b-141">❌ **DISALLOWED: Changing the underlying type of an enumeration**</span></span>

   <span data-ttu-id="e979b-142">這是編譯時期和行為的中斷性變更，以及可以使屬性引數無法進行剖析的二進位中斷性變更。</span><span class="sxs-lookup"><span data-stu-id="e979b-142">This is a compile-time and behavioral breaking change as well as a binary breaking change that can make attribute arguments unparsable.</span></span>

- <span data-ttu-id="e979b-143">❌**不允許：密封先前未密封的型** 別</span><span class="sxs-lookup"><span data-stu-id="e979b-143">❌ **DISALLOWED: Sealing a type that was previously unsealed**</span></span>

- <span data-ttu-id="e979b-144">❌**不允許：將介面加入至介面的基底類型集合**</span><span class="sxs-lookup"><span data-stu-id="e979b-144">❌ **DISALLOWED: Adding an interface to the set of base types of an interface**</span></span>

   <span data-ttu-id="e979b-145">如果介面實作先前未實作的介面，則實作介面原始版本的所有型別都會中斷。</span><span class="sxs-lookup"><span data-stu-id="e979b-145">If an interface implements an interface that it previously did not implement, all types that implemented the original version of the interface are broken.</span></span>

- <span data-ttu-id="e979b-146">❓ **需要判斷：從基類集合或從實介面集的介面中移除類別**</span><span class="sxs-lookup"><span data-stu-id="e979b-146">❓ **REQUIRES JUDGMENT: Removing a class from the set of base classes or an interface from the set of implemented interfaces**</span></span>

  <span data-ttu-id="e979b-147">介面移除規則有一個例外：您可以新增衍生自已移除之介面的介面實作。</span><span class="sxs-lookup"><span data-stu-id="e979b-147">There is one exception to the rule for interface removal: you can add the implementation of an interface that derives from the removed interface.</span></span> <span data-ttu-id="e979b-148">例如，如果型別或介面現在實作 <xref:System.ComponentModel.IComponent> (它會實作 <xref:System.IDisposable>)，則可以移除 <xref:System.IDisposable>。</span><span class="sxs-lookup"><span data-stu-id="e979b-148">For example, you can remove <xref:System.IDisposable> if the type or interface now implements <xref:System.ComponentModel.IComponent>, which implements <xref:System.IDisposable>.</span></span>

- <span data-ttu-id="e979b-149">❌不 **允許：將 `readonly struct` 類型變更為 [結構](../../csharp/language-reference/builtin-types/struct.md) 類型**</span><span class="sxs-lookup"><span data-stu-id="e979b-149">❌ **DISALLOWED: Changing a `readonly struct` type to a [struct](../../csharp/language-reference/builtin-types/struct.md) type**</span></span>

  <span data-ttu-id="e979b-150">`struct`不過，您可以將類型變更為 `readonly struct` 類型。</span><span class="sxs-lookup"><span data-stu-id="e979b-150">The change of a `struct` type to a `readonly struct` type is allowed, however.</span></span>

- <span data-ttu-id="e979b-151">❌不 **允許：將 [結構](../../csharp/language-reference/builtin-types/struct.md)類型變更為 `ref struct` 類型，** 反之亦然</span><span class="sxs-lookup"><span data-stu-id="e979b-151">❌ **DISALLOWED: Changing a [struct](../../csharp/language-reference/builtin-types/struct.md) type to a `ref struct` type, and vice versa**</span></span>

- <span data-ttu-id="e979b-152">❌不 **允許：減少類型的可見度**</span><span class="sxs-lookup"><span data-stu-id="e979b-152">❌ **DISALLOWED: Reducing the visibility of a type**</span></span>

   <span data-ttu-id="e979b-153">但是，允許增加型別的可見性。</span><span class="sxs-lookup"><span data-stu-id="e979b-153">However, increasing the visibility of a type is allowed.</span></span>

### <a name="members"></a><span data-ttu-id="e979b-154">成員</span><span class="sxs-lookup"><span data-stu-id="e979b-154">Members</span></span>

- <span data-ttu-id="e979b-155">**允許✔️：展開非 [虛擬](../../csharp/language-reference/keywords/sealed.md)成員的可見度**</span><span class="sxs-lookup"><span data-stu-id="e979b-155">✔️ **ALLOWED: Expanding the visibility of a member that is not [virtual](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="e979b-156">**允許✔️：將抽象成員新增至無法 *存取* (公用或受保護) 的函式，或類型為 [密封](../../csharp/language-reference/keywords/sealed.md)的公用類型**</span><span class="sxs-lookup"><span data-stu-id="e979b-156">✔️ **ALLOWED: Adding an abstract member to a public type that has no *accessible* (public or protected) constructors, or the type is [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

  <span data-ttu-id="e979b-157">但是，不允許將抽象成員新增至具有可存取 (公用或受保護) 建構函式且不是 `sealed` 的型別。</span><span class="sxs-lookup"><span data-stu-id="e979b-157">However, adding an abstract member to a type that has accessible (public or protected) constructors and is not `sealed` is not allowed.</span></span>

- <span data-ttu-id="e979b-158">✔️ **允許：當類型無法存取 (公用或受保護) 的函式，或類型為 [密封](../../csharp/language-reference/keywords/sealed.md)時，限制 [受保護](../../csharp/language-reference/keywords/protected.md)成員的可見度**</span><span class="sxs-lookup"><span data-stu-id="e979b-158">✔️ **ALLOWED: Restricting the visibility of a [protected](../../csharp/language-reference/keywords/protected.md) member when the type has no accessible (public or protected) constructors, or the type is [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="e979b-159">**允許✔️：將成員移至階層中較高層級的類別，而不是移除它的類型**</span><span class="sxs-lookup"><span data-stu-id="e979b-159">✔️ **ALLOWED: Moving a member into a class higher in the hierarchy than the type from which it was removed**</span></span>

- <span data-ttu-id="e979b-160">**允許✔️：新增或移除覆寫**</span><span class="sxs-lookup"><span data-stu-id="e979b-160">✔️ **ALLOWED: Adding or removing an override**</span></span>

  <span data-ttu-id="e979b-161">引進覆寫可能會導致先前的取用者在呼叫 [base](../../csharp/language-reference/keywords/base.md)時略過覆寫。</span><span class="sxs-lookup"><span data-stu-id="e979b-161">Introducing an override might cause previous consumers to skip over the override when calling [base](../../csharp/language-reference/keywords/base.md).</span></span>

- <span data-ttu-id="e979b-162">✔️ **允許：如果類別先前沒有任何函式，將函式新增至類別，以及無參數的** 函式</span><span class="sxs-lookup"><span data-stu-id="e979b-162">✔️ **ALLOWED: Adding a constructor to a class, along with a parameterless constructor if the class previously had no constructors**</span></span>

   <span data-ttu-id="e979b-163">但是，不允許將建構函式新增至先前沒有建構函式且沒有新增無參數建構函式的類別。</span><span class="sxs-lookup"><span data-stu-id="e979b-163">However, adding a constructor to a class that previously had no constructors *without* adding the parameterless constructor is not allowed.</span></span>

- <span data-ttu-id="e979b-164">**允許✔️：將成員從 [abstract](../../csharp/language-reference/keywords/abstract.md)變更為 [virtual](../../csharp/language-reference/keywords/virtual.md)**</span><span class="sxs-lookup"><span data-stu-id="e979b-164">✔️ **ALLOWED: Changing a member from [abstract](../../csharp/language-reference/keywords/abstract.md) to [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

- <span data-ttu-id="e979b-165">**允許✔️：從 `ref readonly` `ref` 虛擬方法或介面變更為傳回值 ()**</span><span class="sxs-lookup"><span data-stu-id="e979b-165">✔️ **ALLOWED: Changing from a `ref readonly` to a `ref` return value (except for virtual methods or interfaces)**</span></span>

- <span data-ttu-id="e979b-166">✔️ **允許：從欄位移除 [readonly](../../csharp/language-reference/keywords/readonly.md) ，除非欄位的靜態類型是可** 變動的實數值型別</span><span class="sxs-lookup"><span data-stu-id="e979b-166">✔️ **ALLOWED: Removing [readonly](../../csharp/language-reference/keywords/readonly.md) from a field, unless the static type of the field is a mutable value type**</span></span>

- <span data-ttu-id="e979b-167">**允許✔️：呼叫先前未定義的新事件**</span><span class="sxs-lookup"><span data-stu-id="e979b-167">✔️ **ALLOWED: Calling a new event that wasn't previously defined**</span></span>

- <span data-ttu-id="e979b-168">❓**需要判斷：將新的實例欄位新增至型** 別</span><span class="sxs-lookup"><span data-stu-id="e979b-168">❓ **REQUIRES JUDGMENT: Adding a new instance field to a type**</span></span>

   <span data-ttu-id="e979b-169">此變更會影響序列化。</span><span class="sxs-lookup"><span data-stu-id="e979b-169">This change impacts serialization.</span></span>

- <span data-ttu-id="e979b-170">❌不 **允許：重新命名或移除公用成員或參數**</span><span class="sxs-lookup"><span data-stu-id="e979b-170">❌ **DISALLOWED: Renaming or removing a public member or parameter**</span></span>

   <span data-ttu-id="e979b-171">這會中斷使用已重新命名或已移除之成員或參數的所有程式碼。</span><span class="sxs-lookup"><span data-stu-id="e979b-171">This breaks all code that uses the renamed or removed member, or parameter.</span></span>

   <span data-ttu-id="e979b-172">這包括從屬性中移除或重新命名 getter 或 setter，以及重新命名或移除列舉成員。</span><span class="sxs-lookup"><span data-stu-id="e979b-172">This includes removing or renaming a getter or setter from a property, as well as renaming or removing enumeration members.</span></span>

- <span data-ttu-id="e979b-173">❌**不允許：將成員新增至介面**</span><span class="sxs-lookup"><span data-stu-id="e979b-173">❌ **DISALLOWED: Adding a member to an interface**</span></span>

- <span data-ttu-id="e979b-174">❌不 **允許：變更公用常數或列舉成員的值**</span><span class="sxs-lookup"><span data-stu-id="e979b-174">❌ **DISALLOWED: Changing the value of a public constant or enumeration member**</span></span>

- <span data-ttu-id="e979b-175">❌不 **允許：變更屬性、欄位、參數或傳回值的類型**</span><span class="sxs-lookup"><span data-stu-id="e979b-175">❌ **DISALLOWED: Changing the type of a property, field, parameter, or return value**</span></span>

- <span data-ttu-id="e979b-176">❌不 **允許：新增、移除或變更參數的順序**</span><span class="sxs-lookup"><span data-stu-id="e979b-176">❌ **DISALLOWED: Adding, removing, or changing the order of parameters**</span></span>

- <span data-ttu-id="e979b-177">❌不 **允許：從參數新增或移除 [in](../../csharp/language-reference/keywords/in.md)、 [out](../../csharp/language-reference/keywords/out.md) 或 [ref](../../csharp/language-reference/keywords/ref.md) 關鍵字**</span><span class="sxs-lookup"><span data-stu-id="e979b-177">❌ **DISALLOWED: Adding or removing the [in](../../csharp/language-reference/keywords/in.md), [out](../../csharp/language-reference/keywords/out.md) , or [ref](../../csharp/language-reference/keywords/ref.md) keyword from a parameter**</span></span>

- <span data-ttu-id="e979b-178">❌不 **允許：重新具名引數 (包括變更其大小寫)**</span><span class="sxs-lookup"><span data-stu-id="e979b-178">❌ **DISALLOWED: Renaming a parameter (including changing its case)**</span></span>

  <span data-ttu-id="e979b-179">這會視為中斷的原因有二：</span><span class="sxs-lookup"><span data-stu-id="e979b-179">This is considered breaking for two reasons:</span></span>

  - <span data-ttu-id="e979b-180">它中斷了晚期繫結的案例，例如 Visual Basic 中的晚期繫結功能和 C# 中的 [dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type)。</span><span class="sxs-lookup"><span data-stu-id="e979b-180">It breaks late-bound scenarios such as the late binding feature in Visual Basic and [dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) in C#.</span></span>

  - <span data-ttu-id="e979b-181">當開發人員使用[具名引數](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments)時，它會中斷[來源相容性](categories.md#source-compatibility)。</span><span class="sxs-lookup"><span data-stu-id="e979b-181">It breaks [source compatibility](categories.md#source-compatibility) when developers use [named arguments](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).</span></span>

- <span data-ttu-id="e979b-182">❌不 **允許：從傳回 `ref` 值變更為傳回 `ref readonly` 值**</span><span class="sxs-lookup"><span data-stu-id="e979b-182">❌ **DISALLOWED: Changing from a `ref` return value to a `ref readonly` return value**</span></span>

- <span data-ttu-id="e979b-183">❌️不 **允許： `ref readonly` `ref` 在虛擬方法或介面上從變更為傳回值**</span><span class="sxs-lookup"><span data-stu-id="e979b-183">❌️ **DISALLOWED: Changing from a `ref readonly` to a `ref` return value on a virtual method or interface**</span></span>

- <span data-ttu-id="e979b-184">❌不 **允許：新增或移除成員的 [抽象](../../csharp/language-reference/keywords/abstract.md)**</span><span class="sxs-lookup"><span data-stu-id="e979b-184">❌ **DISALLOWED: Adding or removing [abstract](../../csharp/language-reference/keywords/abstract.md) from a member**</span></span>

- <span data-ttu-id="e979b-185">❌不 **允許：從成員中移除 [虛擬](../../csharp/language-reference/keywords/virtual.md) 關鍵字**</span><span class="sxs-lookup"><span data-stu-id="e979b-185">❌ **DISALLOWED: Removing the [virtual](../../csharp/language-reference/keywords/virtual.md) keyword from a member**</span></span>

  <span data-ttu-id="e979b-186">雖然這通常不是一個中斷性變更，因為 C# 編譯器傾向於發出 [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) 中繼語言 (IL) 指令以呼叫非虛擬方法 (`callvirt` 會執行 Null 檢查，而正常呼叫不會)，由於以下幾個原因，此行為並不是不變的：</span><span class="sxs-lookup"><span data-stu-id="e979b-186">While this often is not a breaking change because the C# compiler tends to emit [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) Intermediate Language (IL) instructions to call non-virtual methods (`callvirt` performs a null check, while a normal call doesn't), this behavior is not invariable for several reasons:</span></span>
  - <span data-ttu-id="e979b-187">C# 不是 .NET 以其為目標的唯一語言。</span><span class="sxs-lookup"><span data-stu-id="e979b-187">C# is not the only language that .NET targets.</span></span>

  - <span data-ttu-id="e979b-188">只要目標方法為非虛擬且可能不是 Null 時 (例如透過 [?. null 傳播運算子](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)存取的方法)，C# 編譯器就會漸漸地嘗試將 `callvirt` 最佳化為正常呼叫。</span><span class="sxs-lookup"><span data-stu-id="e979b-188">The C# compiler increasingly tries to optimize `callvirt` to a normal call whenever the target method is non-virtual and is probably not null (such as a method accessed through the [?. null propagation operator](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).</span></span>

  <span data-ttu-id="e979b-189">使方法成為虛擬表示取用者程式碼通常最後會以非虛擬方式呼叫它。</span><span class="sxs-lookup"><span data-stu-id="e979b-189">Making a method virtual means that the consumer code would often end up calling it non-virtually.</span></span>

- <span data-ttu-id="e979b-190">❌不 **允許：將 [虛擬](../../csharp/language-reference/keywords/virtual.md) 關鍵字新增至成員**</span><span class="sxs-lookup"><span data-stu-id="e979b-190">❌ **DISALLOWED: Adding the [virtual](../../csharp/language-reference/keywords/virtual.md) keyword to a member**</span></span>

- <span data-ttu-id="e979b-191">❌不 **允許：讓虛擬成員成為抽象**</span><span class="sxs-lookup"><span data-stu-id="e979b-191">❌ **DISALLOWED: Making a virtual member abstract**</span></span>

  <span data-ttu-id="e979b-192">[虛擬成員](../../csharp/language-reference/keywords/virtual.md)提供了一種方法實作，可以由衍生類別覆寫。</span><span class="sxs-lookup"><span data-stu-id="e979b-192">A [virtual member](../../csharp/language-reference/keywords/virtual.md) provides a method implementation that *can be* overridden by a derived class.</span></span> <span data-ttu-id="e979b-193">[抽象成員](../../csharp/language-reference/keywords/abstract.md)不提供任何實作，且必須被覆寫。</span><span class="sxs-lookup"><span data-stu-id="e979b-193">An [abstract member](../../csharp/language-reference/keywords/abstract.md) provides no implementation and *must be* overridden.</span></span>

- <span data-ttu-id="e979b-194">❌**不允許：將抽象成員新增至可存取 (公用或受保護) 的函式，且未 [密封](../../csharp/language-reference/keywords/sealed.md)的公用類型**</span><span class="sxs-lookup"><span data-stu-id="e979b-194">❌ **DISALLOWED: Adding an abstract member to a public type that has accessible (public or protected) constructors and that is not [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="e979b-195">❌不 **允許：從成員新增或移除 [靜態](../../csharp/language-reference/keywords/static.md) 關鍵字**</span><span class="sxs-lookup"><span data-stu-id="e979b-195">❌ **DISALLOWED: Adding or removing the [static](../../csharp/language-reference/keywords/static.md) keyword from a member**</span></span>

- <span data-ttu-id="e979b-196">❌不 **允許：加入可防止現有多載的多載，並定義不同的行為**</span><span class="sxs-lookup"><span data-stu-id="e979b-196">❌ **DISALLOWED: Adding an overload that precludes an existing overload and defines a different behavior**</span></span>

  <span data-ttu-id="e979b-197">這會中斷繫結到先前多載的現有用戶端。</span><span class="sxs-lookup"><span data-stu-id="e979b-197">This breaks existing clients that were bound to the previous overload.</span></span> <span data-ttu-id="e979b-198">例如，如果某個類別具有接受 <xref:System.UInt32> 的方法的單一版本，則現有的取用者在傳遞 <xref:System.Int32> 值時將成功繫結至該多載。</span><span class="sxs-lookup"><span data-stu-id="e979b-198">For example, if a class has a single version of a method that accepts a <xref:System.UInt32>, an existing consumer will successfully bind to that overload when passing a <xref:System.Int32> value.</span></span> <span data-ttu-id="e979b-199">但是，如果新增接受 <xref:System.Int32> 的多載，則在重新編譯或使用晚期繫結時，編譯器現在會繫結至新的多載。</span><span class="sxs-lookup"><span data-stu-id="e979b-199">However, if you add an overload that accepts an <xref:System.Int32>, when recompiling or using late-binding, the compiler now binds to the new overload.</span></span> <span data-ttu-id="e979b-200">如果產生不同的行為，這是一個中斷性變更。</span><span class="sxs-lookup"><span data-stu-id="e979b-200">If different behavior results, this is a breaking change.</span></span>

- <span data-ttu-id="e979b-201">❌**不允許：將函式新增至先前沒有任何函式的類別，而不新增無參數的** 函式</span><span class="sxs-lookup"><span data-stu-id="e979b-201">❌ **DISALLOWED: Adding a constructor to a class that previously had no constructor without adding the parameterless constructor**</span></span>

- <span data-ttu-id="e979b-202">❌️不 **允許：將 [readonly](../../csharp/language-reference/keywords/readonly.md) 加入至欄位**</span><span class="sxs-lookup"><span data-stu-id="e979b-202">❌️ **DISALLOWED: Adding [readonly](../../csharp/language-reference/keywords/readonly.md) to a field**</span></span>

- <span data-ttu-id="e979b-203">❌不 **允許：減少成員的可見度**</span><span class="sxs-lookup"><span data-stu-id="e979b-203">❌ **DISALLOWED: Reducing the visibility of a member**</span></span>

   <span data-ttu-id="e979b-204">這包括減少 [受保護](../../csharp/language-reference/keywords/protected.md)成員的可見度（當有 *可存取* 的 (`public` 或 `protected`) 的函式，且類型 *未*[密封](../../csharp/language-reference/keywords/sealed.md)時）。</span><span class="sxs-lookup"><span data-stu-id="e979b-204">This includes reducing the visibility of a [protected](../../csharp/language-reference/keywords/protected.md) member when there are *accessible* (`public` or `protected`) constructors and the type is *not* [sealed](../../csharp/language-reference/keywords/sealed.md).</span></span> <span data-ttu-id="e979b-205">如果不是這種情況，則允許降低受保護成員的可見性。</span><span class="sxs-lookup"><span data-stu-id="e979b-205">If this is not the case, reducing the visibility of a protected member is allowed.</span></span>

   <span data-ttu-id="e979b-206">允許提高成員的可見度。</span><span class="sxs-lookup"><span data-stu-id="e979b-206">Increasing the visibility of a member is allowed.</span></span>

- <span data-ttu-id="e979b-207">❌不 **允許：變更成員的類型**</span><span class="sxs-lookup"><span data-stu-id="e979b-207">❌ **DISALLOWED: Changing the type of a member**</span></span>

   <span data-ttu-id="e979b-208">無法修改方法的傳回值，或屬性或欄位的型別。</span><span class="sxs-lookup"><span data-stu-id="e979b-208">The return value of a method or the type of a property or field cannot be modified.</span></span> <span data-ttu-id="e979b-209">例如，傳回 <xref:System.Object> 之方法的簽章不能變更為傳回 <xref:System.String>，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="e979b-209">For example, the signature of a method that returns an <xref:System.Object> cannot be changed to return a <xref:System.String>, or vice versa.</span></span>

- <span data-ttu-id="e979b-210">❌**不允許：將欄位新增至先前沒有狀態的結構**</span><span class="sxs-lookup"><span data-stu-id="e979b-210">❌ **DISALLOWED: Adding a field to a struct that previously had no state**</span></span>

  <span data-ttu-id="e979b-211">只要變數型別是無狀態結構，明確指派規則就允許使用未初始化的變數。</span><span class="sxs-lookup"><span data-stu-id="e979b-211">Definite assignment rules allow the use of uninitialized variables so long as the variable type is a stateless struct.</span></span> <span data-ttu-id="e979b-212">如果將結構設定為具狀態，程式碼最後可能會遇到未初始化的資料。</span><span class="sxs-lookup"><span data-stu-id="e979b-212">If the struct is made stateful, code could end up with uninitialized data.</span></span> <span data-ttu-id="e979b-213">這可能是一個來源中斷和二進位中斷性變更。</span><span class="sxs-lookup"><span data-stu-id="e979b-213">This is both potentially a source breaking and a binary breaking change.</span></span>

- <span data-ttu-id="e979b-214">❌**不允許：引發先前從未引發的現有事件**</span><span class="sxs-lookup"><span data-stu-id="e979b-214">❌ **DISALLOWED: Firing an existing event when it was never fired before**</span></span>

## <a name="behavioral-changes"></a><span data-ttu-id="e979b-215">行為變更</span><span class="sxs-lookup"><span data-stu-id="e979b-215">Behavioral changes</span></span>

### <a name="assemblies"></a><span data-ttu-id="e979b-216">組件</span><span class="sxs-lookup"><span data-stu-id="e979b-216">Assemblies</span></span>

- <span data-ttu-id="e979b-217">**允許✔️：仍支援相同平臺時，讓元件可** 攜</span><span class="sxs-lookup"><span data-stu-id="e979b-217">✔️ **ALLOWED: Making an assembly portable when the same platforms are still supported**</span></span>

- <span data-ttu-id="e979b-218">❌**不允許：變更元件的名稱**</span><span class="sxs-lookup"><span data-stu-id="e979b-218">❌ **DISALLOWED: Changing the name of an assembly**</span></span>
- <span data-ttu-id="e979b-219">❌**不允許：變更元件的公開金鑰**</span><span class="sxs-lookup"><span data-stu-id="e979b-219">❌ **DISALLOWED: Changing the public key of an assembly**</span></span>

### <a name="properties-fields-parameters-and-return-values"></a><span data-ttu-id="e979b-220">屬性、欄位、參數與傳回值</span><span class="sxs-lookup"><span data-stu-id="e979b-220">Properties, fields, parameters, and return values</span></span>

- <span data-ttu-id="e979b-221">**允許✔️：將屬性、欄位、傳回值或 [out](../../csharp/language-reference/keywords/out-parameter-modifier.md)參數的值變更為更衍生的類型**</span><span class="sxs-lookup"><span data-stu-id="e979b-221">✔️ **ALLOWED: Changing the value of a property, field, return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter to a more derived type**</span></span>

  <span data-ttu-id="e979b-222">例如，傳回 <xref:System.Object> 型別的方法可以傳回 <xref:System.String> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="e979b-222">For example, a method that returns a type of <xref:System.Object> can return a <xref:System.String> instance.</span></span> <span data-ttu-id="e979b-223">(但是，無法變更方法簽章。)</span><span class="sxs-lookup"><span data-stu-id="e979b-223">(However, the method signature cannot change.)</span></span>

- <span data-ttu-id="e979b-224">**允許✔️：如果成員不是 [虛擬](../../csharp/language-reference/keywords/virtual.md)的，則增加屬性或參數的可接受值範圍**</span><span class="sxs-lookup"><span data-stu-id="e979b-224">✔️ **ALLOWED: Increasing the range of accepted values for a property or parameter if the member is not [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

  <span data-ttu-id="e979b-225">雖然可以傳遞給方法或由成員傳回的值範圍可以展開，但參數或成員類型則不能。</span><span class="sxs-lookup"><span data-stu-id="e979b-225">While the range of values that can be passed to the method or are returned by the member can expand, the parameter or member type cannot.</span></span> <span data-ttu-id="e979b-226">例如，雖然傳遞至方法的值可以從 0-124 擴充至 0-255，但參數類型無法從 <xref:System.Byte> 變更為 <xref:System.Int32>。</span><span class="sxs-lookup"><span data-stu-id="e979b-226">For example, while the values passed to a method can expand from 0-124 to 0-255, the parameter type cannot change from <xref:System.Byte> to <xref:System.Int32>.</span></span>

- <span data-ttu-id="e979b-227">❌**不允許：如果成員為 [虛擬](../../csharp/language-reference/keywords/virtual.md)，則增加屬性或參數的可接受值範圍**</span><span class="sxs-lookup"><span data-stu-id="e979b-227">❌ **DISALLOWED: Increasing the range of accepted values for a property or parameter if the member is [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

   <span data-ttu-id="e979b-228">此變更會中斷現有的覆寫成員，這些成員將無法在擴充的值範圍內正常執行。</span><span class="sxs-lookup"><span data-stu-id="e979b-228">This change breaks existing overridden members, which will not function correctly for the extended range of values.</span></span>

- <span data-ttu-id="e979b-229">❌不 **允許：減少屬性或參數的可接受值範圍**</span><span class="sxs-lookup"><span data-stu-id="e979b-229">❌ **DISALLOWED: Decreasing the range of accepted values for a property or parameter**</span></span>

- <span data-ttu-id="e979b-230">❌不 **允許：增加屬性、欄位、傳回值或 [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) 參數的傳回值範圍**</span><span class="sxs-lookup"><span data-stu-id="e979b-230">❌ **DISALLOWED: Increasing the range of returned values for a property, field, return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter**</span></span>

- <span data-ttu-id="e979b-231">❌不 **允許：變更屬性、欄位、方法傳回值或 [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) 參數的傳回值**</span><span class="sxs-lookup"><span data-stu-id="e979b-231">❌ **DISALLOWED: Changing the returned values for a property, field, method return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter**</span></span>

- <span data-ttu-id="e979b-232">❌不 **允許：變更屬性、欄位或參數的預設值**</span><span class="sxs-lookup"><span data-stu-id="e979b-232">❌ **DISALLOWED: Changing the default value of a property, field, or parameter**</span></span>

- <span data-ttu-id="e979b-233">❌不 **允許：變更數值傳回值的有效位數**</span><span class="sxs-lookup"><span data-stu-id="e979b-233">❌ **DISALLOWED: Changing the precision of a numeric return value**</span></span>

- <span data-ttu-id="e979b-234">❓ **需要判斷：剖析輸入和擲回新的例外狀況的變更， (即使檔中未指定剖析行為**</span><span class="sxs-lookup"><span data-stu-id="e979b-234">❓ **REQUIRES JUDGMENT: A change in the parsing of input and throwing new exceptions (even if parsing behavior is not specified in the documentation**</span></span>

### <a name="exceptions"></a><span data-ttu-id="e979b-235">例外狀況</span><span class="sxs-lookup"><span data-stu-id="e979b-235">Exceptions</span></span>

- <span data-ttu-id="e979b-236">允許✔️：擲回 **比現有例外狀況更多的衍生例外** 狀況</span><span class="sxs-lookup"><span data-stu-id="e979b-236">✔️ **ALLOWED: Throwing a more derived exception than an existing exception**</span></span>

  <span data-ttu-id="e979b-237">因為新的例外狀況是現有例外狀況的子類別，所以先前的例外狀況處理程式碼會繼續處理例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e979b-237">Because the new exception is a subclass of an existing exception, previous exception handling code continues to handle the exception.</span></span> <span data-ttu-id="e979b-238">例如，在 .NET Framework 4 中，文化特性建立和擷取方法已開始擲回 <xref:System.Globalization.CultureNotFoundException> 而不是 <xref:System.ArgumentException> (如果找不到文化特性)。</span><span class="sxs-lookup"><span data-stu-id="e979b-238">For example, in .NET Framework 4, culture creation and retrieval methods began to throw a <xref:System.Globalization.CultureNotFoundException> instead of an <xref:System.ArgumentException> if the culture could not be found.</span></span> <span data-ttu-id="e979b-239">因為 <xref:System.Globalization.CultureNotFoundException> 衍生自 <xref:System.ArgumentException>，所以這是一個可接受的變更。</span><span class="sxs-lookup"><span data-stu-id="e979b-239">Because <xref:System.Globalization.CultureNotFoundException> derives from <xref:System.ArgumentException>, this is an acceptable change.</span></span>

- <span data-ttu-id="e979b-240">允許✔️：擲回 **比 <xref:System.NotSupportedException> 、 <xref:System.NotImplementedException> 、、 <xref:System.NullReferenceException> 更明確的例外** 狀況</span><span class="sxs-lookup"><span data-stu-id="e979b-240">✔️ **ALLOWED: Throwing a more specific exception than <xref:System.NotSupportedException>, <xref:System.NotImplementedException>, <xref:System.NullReferenceException>**</span></span>

- <span data-ttu-id="e979b-241">允許✔️：擲回 **被視為無法** 復原的例外狀況</span><span class="sxs-lookup"><span data-stu-id="e979b-241">✔️ **ALLOWED: Throwing an exception that is considered unrecoverable**</span></span>

  <span data-ttu-id="e979b-242">無法復原的例外狀況不應該攔截，而應該由高層級追補處理常式處理。</span><span class="sxs-lookup"><span data-stu-id="e979b-242">Unrecoverable exceptions should not be caught but instead should be handled by a high-level catch-all handler.</span></span> <span data-ttu-id="e979b-243">因此，使用者不應該擁有攔截這些明確例外狀況的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e979b-243">Therefore, users are not expected to have code that catches these explicit exceptions.</span></span> <span data-ttu-id="e979b-244">無法復原的例外狀況有：</span><span class="sxs-lookup"><span data-stu-id="e979b-244">The unrecoverable exceptions are:</span></span>

  - <xref:System.AccessViolationException>
  - <xref:System.ExecutionEngineException>
  - <xref:System.Runtime.InteropServices.SEHException>
  - <xref:System.StackOverflowException>

- <span data-ttu-id="e979b-245">**允許✔️：在新的程式碼路徑中擲回新的例外** 狀況</span><span class="sxs-lookup"><span data-stu-id="e979b-245">✔️ **ALLOWED: Throwing a new exception in a new code path**</span></span>

  <span data-ttu-id="e979b-246">例外狀況必須只套用至新的程式碼路徑，該路徑會以新的參數值或狀態執行，而且無法由以舊版為目標的現有程式碼執行。</span><span class="sxs-lookup"><span data-stu-id="e979b-246">The exception must apply only to a new code-path that's executed with new parameter values or state and that can't be executed by existing code that targets the previous version.</span></span>

- <span data-ttu-id="e979b-247">**允許✔️：移除例外狀況以啟用更健全的行為或新案例**</span><span class="sxs-lookup"><span data-stu-id="e979b-247">✔️ **ALLOWED: Removing an exception to enable more robust behavior or new scenarios**</span></span>

  <span data-ttu-id="e979b-248">例如，之前只處理正值並擲回 <xref:System.ArgumentOutOfRangeException> 的 `Divide` 方法可以變更為支援負值和正值，而不擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e979b-248">For example, a `Divide` method that previously only handled positive values and threw an <xref:System.ArgumentOutOfRangeException> otherwise can be changed to support both negative and positive values without throwing an exception.</span></span>

- <span data-ttu-id="e979b-249">**允許✔️：變更錯誤訊息的文字**</span><span class="sxs-lookup"><span data-stu-id="e979b-249">✔️ **ALLOWED: Changing the text of an error message**</span></span>

  <span data-ttu-id="e979b-250">開發人員不應該依賴錯誤訊息的文字，這也會根據使用者的文化特性而變更。</span><span class="sxs-lookup"><span data-stu-id="e979b-250">Developers should not rely on the text of error messages, which also change based on the user's culture.</span></span>

- <span data-ttu-id="e979b-251">❌**不允許：擲回例外狀況的其他任何情況下未列出**</span><span class="sxs-lookup"><span data-stu-id="e979b-251">❌ **DISALLOWED: Throwing an exception in any other case not listed above**</span></span>

- <span data-ttu-id="e979b-252">❌**不允許：移除上方未列出的任何其他案例中的例外狀況**</span><span class="sxs-lookup"><span data-stu-id="e979b-252">❌ **DISALLOWED: Removing an exception in any other case not listed above**</span></span>

### <a name="attributes"></a><span data-ttu-id="e979b-253">屬性</span><span class="sxs-lookup"><span data-stu-id="e979b-253">Attributes</span></span>

- <span data-ttu-id="e979b-254">**允許✔️：變更 *不可* 觀察的屬性值**</span><span class="sxs-lookup"><span data-stu-id="e979b-254">✔️ **ALLOWED: Changing the value of an attribute that is *not* observable**</span></span>

- <span data-ttu-id="e979b-255">❌***不* 允許：變更可觀察的屬性值**</span><span class="sxs-lookup"><span data-stu-id="e979b-255">❌ **DISALLOWED: Changing the value of an attribute that *is* observable**</span></span>

- <span data-ttu-id="e979b-256">❓ **需要判斷：移除屬性**</span><span class="sxs-lookup"><span data-stu-id="e979b-256">❓ **REQUIRES JUDGMENT: Removing an attribute**</span></span>

  <span data-ttu-id="e979b-257">在大部分情況下，移除屬性 (例如<xref:System.NonSerializedAttribute>) 是一個中斷性變更。</span><span class="sxs-lookup"><span data-stu-id="e979b-257">In most cases, removing an attribute (such as <xref:System.NonSerializedAttribute>) is a breaking change.</span></span>

## <a name="platform-support"></a><span data-ttu-id="e979b-258">平台支援</span><span class="sxs-lookup"><span data-stu-id="e979b-258">Platform support</span></span>

- <span data-ttu-id="e979b-259">**允許✔️：在先前不支援的平臺上支援操作**</span><span class="sxs-lookup"><span data-stu-id="e979b-259">✔️ **ALLOWED: Supporting an operation on a platform that was previously not supported**</span></span>

- <span data-ttu-id="e979b-260">❌**不允許：不支援或現在針對平臺上先前支援的作業要求特定的 service pack**</span><span class="sxs-lookup"><span data-stu-id="e979b-260">❌ **DISALLOWED: Not supporting or now requiring a specific service pack for an operation that was previously supported on a platform**</span></span>

## <a name="internal-implementation-changes"></a><span data-ttu-id="e979b-261">內部實作的變更</span><span class="sxs-lookup"><span data-stu-id="e979b-261">Internal implementation changes</span></span>

- <span data-ttu-id="e979b-262">❓ **需要判斷：變更內部型別的介面區**</span><span class="sxs-lookup"><span data-stu-id="e979b-262">❓ **REQUIRES JUDGMENT: Changing the surface area of an internal type**</span></span>

   <span data-ttu-id="e979b-263">通常允許此類變更，儘管它們可能會中斷私人反映。</span><span class="sxs-lookup"><span data-stu-id="e979b-263">Such changes are generally allowed, although they break private reflection.</span></span> <span data-ttu-id="e979b-264">在一些熱門的協力廠商程式庫或大量開發人員依賴內部 API 的案例中，可能不允許此類變更。</span><span class="sxs-lookup"><span data-stu-id="e979b-264">In some cases, where popular third-party libraries or a large number of developers depend on the internal APIs, such changes may not be allowed.</span></span>

- <span data-ttu-id="e979b-265">❓**需要判斷：變更成員的內部實** 作為</span><span class="sxs-lookup"><span data-stu-id="e979b-265">❓ **REQUIRES JUDGMENT: Changing the internal implementation of a member**</span></span>

  <span data-ttu-id="e979b-266">通常允許這些變更，儘管它們可能會中斷私人反映。</span><span class="sxs-lookup"><span data-stu-id="e979b-266">These changes are generally allowed, although they break private reflection.</span></span> <span data-ttu-id="e979b-267">在一些客戶程式碼經常依賴私人反映或變更引進非預期之副作用的情況下，可能不允許這些變更。</span><span class="sxs-lookup"><span data-stu-id="e979b-267">In some cases, where customer code frequently depends on private reflection or where the change introduces unintended side effects, these changes may not be allowed.</span></span>

- <span data-ttu-id="e979b-268">**允許✔️：改善作業的效能**</span><span class="sxs-lookup"><span data-stu-id="e979b-268">✔️ **ALLOWED: Improving the performance of an operation**</span></span>

   <span data-ttu-id="e979b-269">修改作業效能的能力是很重要的，但此類變更可能會中斷仰賴目前作業速度的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e979b-269">The ability to modify the performance of an operation is essential, but such changes can break code that relies upon the current speed of an operation.</span></span> <span data-ttu-id="e979b-270">對於仰賴非同步作業時間的程式碼尤其如此。</span><span class="sxs-lookup"><span data-stu-id="e979b-270">This is particularly true of code that depends on the timing of asynchronous operations.</span></span> <span data-ttu-id="e979b-271">效能變更應該不會影響 API 的其他行為，否則，變更將會中斷。</span><span class="sxs-lookup"><span data-stu-id="e979b-271">The performance change should have no effect on other behavior of the API in question; otherwise, the change will be breaking.</span></span>

- <span data-ttu-id="e979b-272">**允許✔️：間接 (，而且通常會) 變更作業的效能**</span><span class="sxs-lookup"><span data-stu-id="e979b-272">✔️ **ALLOWED: Indirectly (and often adversely) changing the performance of an operation**</span></span>

  <span data-ttu-id="e979b-273">如果由於某些其他原因而未將相關變更歸類為中斷，則這是可以接受的。</span><span class="sxs-lookup"><span data-stu-id="e979b-273">If the change in question is not categorized as breaking for some other reason, this is acceptable.</span></span> <span data-ttu-id="e979b-274">通常，需要採取可能包括額外的作業或新增新功能的動作。</span><span class="sxs-lookup"><span data-stu-id="e979b-274">Often, actions need to be taken that may include extra operations or that add new functionality.</span></span> <span data-ttu-id="e979b-275">這幾乎一律會影響效能，但對於使相關 API 如預期般運作至關重要。</span><span class="sxs-lookup"><span data-stu-id="e979b-275">This will almost always affect performance but may be essential to make the API in question function as expected.</span></span>

- <span data-ttu-id="e979b-276">❌不 **允許：將同步 API 變更為非同步 (，反之亦然)**</span><span class="sxs-lookup"><span data-stu-id="e979b-276">❌ **DISALLOWED: Changing a synchronous API to asynchronous (and vice versa)**</span></span>

## <a name="code-changes"></a><span data-ttu-id="e979b-277">程式碼變更</span><span class="sxs-lookup"><span data-stu-id="e979b-277">Code changes</span></span>

- <span data-ttu-id="e979b-278">**允許✔️：將 [](../../csharp/language-reference/keywords/params.md)參數加入至參數**</span><span class="sxs-lookup"><span data-stu-id="e979b-278">✔️ **ALLOWED: Adding [params](../../csharp/language-reference/keywords/params.md) to a parameter**</span></span>

- <span data-ttu-id="e979b-279">❌不 **允許：將 [結構](../../csharp/language-reference/builtin-types/struct.md)變更為 [類別](../../csharp/language-reference/keywords/class.md)，** 反之亦然</span><span class="sxs-lookup"><span data-stu-id="e979b-279">❌ **DISALLOWED: Changing a [struct](../../csharp/language-reference/builtin-types/struct.md) to a [class](../../csharp/language-reference/keywords/class.md) and vice versa**</span></span>

- <span data-ttu-id="e979b-280">❌不 **允許：將 [Checked](../../csharp/language-reference/keywords/virtual.md) 關鍵字加入至程式碼區塊**</span><span class="sxs-lookup"><span data-stu-id="e979b-280">❌ **DISALLOWED: Adding the [checked](../../csharp/language-reference/keywords/virtual.md) keyword to a code block**</span></span>

   <span data-ttu-id="e979b-281">此變更可能會導致先前執行的程式碼擲回 <xref:System.OverflowException> 且無法接受。</span><span class="sxs-lookup"><span data-stu-id="e979b-281">This change may cause code that previously executed to throw an <xref:System.OverflowException> and is unacceptable.</span></span>

- <span data-ttu-id="e979b-282">❌不 **允許： [](../../csharp/language-reference/keywords/params.md)從參數中移除參數**</span><span class="sxs-lookup"><span data-stu-id="e979b-282">❌ **DISALLOWED: Removing [params](../../csharp/language-reference/keywords/params.md) from a parameter**</span></span>

- <span data-ttu-id="e979b-283">❌不 **允許：變更引發事件的順序**</span><span class="sxs-lookup"><span data-stu-id="e979b-283">❌ **DISALLOWED: Changing the order in which events are fired**</span></span>

  <span data-ttu-id="e979b-284">開發人員可以合理地預期事件以相同的順序引發，而開發人員程式碼經常會取決於事件的引發順序。</span><span class="sxs-lookup"><span data-stu-id="e979b-284">Developers can reasonably expect events to fire in the same order, and developer code frequently depends on the order in which events are fired.</span></span>

- <span data-ttu-id="e979b-285">❌**不允許：移除指定動作上引發的事件**</span><span class="sxs-lookup"><span data-stu-id="e979b-285">❌ **DISALLOWED: Removing the raising of an event on a given action**</span></span>

- <span data-ttu-id="e979b-286">❌**不允許：變更指定事件的呼叫次數**</span><span class="sxs-lookup"><span data-stu-id="e979b-286">❌ **DISALLOWED: Changing the number of times given events are called**</span></span>

- <span data-ttu-id="e979b-287">❌**不允許：將加入 <xref:System.FlagsAttribute> 至列舉型** 別</span><span class="sxs-lookup"><span data-stu-id="e979b-287">❌ **DISALLOWED: Adding the <xref:System.FlagsAttribute> to an enumeration type**</span></span>
