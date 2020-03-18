---
title: 中斷性變更的類型
description: 瞭解 .NET Core 如何嘗試維護跨 .NET 版本的開發人員的相容性，以及哪種更改被視為重大更改。
ms.date: 06/10/2019
ms.openlocfilehash: bf0cc35d69e6bb501640455604a99a1f48962c4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "77628588"
---
# <a name="changes-that-affect-compatibility"></a><span data-ttu-id="b4dad-103">影響相容性的更改</span><span class="sxs-lookup"><span data-stu-id="b4dad-103">Changes that affect compatibility</span></span>

<span data-ttu-id="b4dad-104">縱觀其歷程記錄，.NET 一直嘗試維護 .NET 各版本之間以及各種變體之間的相容性。</span><span class="sxs-lookup"><span data-stu-id="b4dad-104">Throughout its history, .NET has attempted to maintain a high level of compatibility from version to version and across flavors of .NET.</span></span> <span data-ttu-id="b4dad-105">在 .NET Core 中仍是如此。</span><span class="sxs-lookup"><span data-stu-id="b4dad-105">This continues to be true for .NET Core.</span></span> <span data-ttu-id="b4dad-106">雖然 .NET Core 可以視為是獨立於 .NET Framework 之外的新技術，但是有兩個主要因素限制了 .NET Core 從 .NET Framework 分離的能力：</span><span class="sxs-lookup"><span data-stu-id="b4dad-106">Although .NET Core can be considered as a new technology that is independent of the .NET Framework, two major factors limit the ability of .NET Core to diverge from .NET Framework:</span></span>

- <span data-ttu-id="b4dad-107">最初開發或是繼續開發 .NET Framework 應用程式的大量開發人員。</span><span class="sxs-lookup"><span data-stu-id="b4dad-107">A large number of developers either originally developed or continue to develop .NET Framework applications.</span></span> <span data-ttu-id="b4dad-108">他們預期跨 .NET 實作有一致的行為。</span><span class="sxs-lookup"><span data-stu-id="b4dad-108">They expect consistent behavior across .NET implementations.</span></span>

- <span data-ttu-id="b4dad-109">.NET Standard 程式庫專案可讓開發人員建立以 .NET Core 和 .NET Framework 所共用之通用 API 為目標的程式庫。</span><span class="sxs-lookup"><span data-stu-id="b4dad-109">.NET Standard library projects allow developers to create libraries that target common APIs shared by .NET Core and .NET Framework.</span></span> <span data-ttu-id="b4dad-110">開發人員預期 .NET Core 應用程式中使用之程式庫的行為，應與 .NET Framework 應用程式中所使用的程式庫相同。</span><span class="sxs-lookup"><span data-stu-id="b4dad-110">Developers expect that a library used in a .NET Core application should behave identically to the same library used in a .NET Framework application.</span></span>

<span data-ttu-id="b4dad-111">除了 .NET 實作之間的相容性之外，開發人員還希望 .NET Core 版本之間具有高層級相容性。</span><span class="sxs-lookup"><span data-stu-id="b4dad-111">Along with compatibility across .NET implementations, developers expect a high level of compatibility across .NET Core versions.</span></span> <span data-ttu-id="b4dad-112">特別是，針對較早版本的 .NET Core 所撰寫的程式碼應該在新版的 .NET Core 上順暢地執行。</span><span class="sxs-lookup"><span data-stu-id="b4dad-112">In particular, code written for an earlier version of .NET Core should run seamlessly on a later version of .NET Core.</span></span> <span data-ttu-id="b4dad-113">實際上，許多開發人員預期在新發行的 .NET Core 版本中找到的新 API，也應該與引入那些 API 的發行前版本相容。</span><span class="sxs-lookup"><span data-stu-id="b4dad-113">In fact, many developers expect that the new APIs found in newly released versions of .NET Core should also be compatible with the pre-release versions in which those APIs were introduced.</span></span>

<span data-ttu-id="b4dad-114">此文章概述相容性變更 (或中斷性變更) 的類別，以及 .NET 小組評估每個類別中的變更的方式。</span><span class="sxs-lookup"><span data-stu-id="b4dad-114">This article outlines the categories of compatibility changes (or breaking changes) and the way in which the .NET team evaluates changes in each of these categories.</span></span> <span data-ttu-id="b4dad-115">瞭解 .NET 團隊如何處理可能的突發更改對於在[dotnet/運行時](https://github.com/dotnet/runtime)GitHub 存儲庫中打開拉取請求的開發人員來說尤其有用，這些開發人員修改了現有 API 的行為。</span><span class="sxs-lookup"><span data-stu-id="b4dad-115">Understanding how the .NET team approaches possible breaking changes is particularly helpful for developers who open pull requests in the [dotnet/runtime](https://github.com/dotnet/runtime) GitHub repository that modify the behavior of existing APIs.</span></span>

> [!NOTE]
> <span data-ttu-id="b4dad-116">如需相容性類別的定義，例如二進位檔案相容性和回溯相容性，請參閱[中斷性變更類別](categories.md)。</span><span class="sxs-lookup"><span data-stu-id="b4dad-116">For a definition of compatibility categories, such as binary compatibility and backward compatibility, see [Breaking change categories](categories.md).</span></span>

<span data-ttu-id="b4dad-117">以下各節介紹對 .NET 核心 API 所做的更改類別及其對應用程式相容性的影響。</span><span class="sxs-lookup"><span data-stu-id="b4dad-117">The following sections describe the categories of changes made to .NET Core APIs and their impact on application compatibility.</span></span> <span data-ttu-id="b4dad-118">更改要麼允許✔️，要麼不允許❌，要麼需要判斷和評估，以及評估以前的行為❓的可預測性、明顯性和一致性。</span><span class="sxs-lookup"><span data-stu-id="b4dad-118">Changes are either allowed ✔️, disallowed ❌, or require judgment and an evaluation of how predictable, obvious, and consistent the previous behavior was ❓.</span></span>

> [!NOTE]
> <span data-ttu-id="b4dad-119">除了作為如何評估 .NET Core 程式庫變更的指南之外，程式庫開發人員也可以使用這些準則來評估其程式庫 (以多個 .NET 實作和版本為目標) 的變更。</span><span class="sxs-lookup"><span data-stu-id="b4dad-119">In addition to serving as a guide to how changes to .NET Core libraries are evaluated, library developers can also use these criteria to evaluate changes to their libraries that target multiple .NET implementations and versions.</span></span>

## <a name="modifications-to-the-public-contract"></a><span data-ttu-id="b4dad-120">公用合約的修改</span><span class="sxs-lookup"><span data-stu-id="b4dad-120">Modifications to the public contract</span></span>

<span data-ttu-id="b4dad-121">此類別中的變更會修改某個類型的公用介面區。</span><span class="sxs-lookup"><span data-stu-id="b4dad-121">Changes in this category modify the public surface area of a type.</span></span> <span data-ttu-id="b4dad-122">此類別中的大多數變更都是不允許的，因為它們違反了回溯相容性\*\* (可讓使用舊版 API 開發的應用程式能夠在更新版本上執行而不必重新編譯的能力)。</span><span class="sxs-lookup"><span data-stu-id="b4dad-122">Most of the changes in this category are disallowed since they violate *backwards compatibility* (the ability of an application that was developed with a previous version of an API to execute without recompilation on a later version).</span></span>

### <a name="types"></a><span data-ttu-id="b4dad-123">類型</span><span class="sxs-lookup"><span data-stu-id="b4dad-123">Types</span></span>

- <span data-ttu-id="b4dad-124">✔️**允許：當介面已由基類型實現時，從類型中刪除介面實現**</span><span class="sxs-lookup"><span data-stu-id="b4dad-124">✔️ **ALLOWED: Removing an interface implementation from a type when the interface is already implemented by a base type**</span></span>

- <span data-ttu-id="b4dad-125">❓**要求：向類型添加新的介面實現**</span><span class="sxs-lookup"><span data-stu-id="b4dad-125">❓ **REQUIRES JUDGMENT: Adding a new interface implementation to a type**</span></span>

  <span data-ttu-id="b4dad-126">這是一個可接受的變更，因為它不會對現有的用戶端產生負面影響。</span><span class="sxs-lookup"><span data-stu-id="b4dad-126">This is an acceptable change because it does not adversely affect existing clients.</span></span> <span data-ttu-id="b4dad-127">對類型的任何變更都必須在此處定義的可接受變更的界限內運作，以使新實作維持可接受。</span><span class="sxs-lookup"><span data-stu-id="b4dad-127">Any changes to the type must work within the boundaries of acceptable changes defined here for the new implementation to remain acceptable.</span></span> <span data-ttu-id="b4dad-128">如果您要加入的介面會直接影響設計工具或序列化程式產生無法在低層級取用之程式碼或資料的能力，請格外小心。</span><span class="sxs-lookup"><span data-stu-id="b4dad-128">Extreme caution is necessary when adding interfaces that directly affect the ability of a designer or serializer to generate code or data that cannot be consumed down-level.</span></span> <span data-ttu-id="b4dad-129">其中一個範例是 <xref:System.Runtime.Serialization.ISerializable> 介面。</span><span class="sxs-lookup"><span data-stu-id="b4dad-129">An example is the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

- <span data-ttu-id="b4dad-130">❓**要求：引入新的基類**</span><span class="sxs-lookup"><span data-stu-id="b4dad-130">❓ **REQUIRES JUDGMENT: Introducing a new base class**</span></span>

  <span data-ttu-id="b4dad-131">如果類型不引入任何新的[抽象](../../csharp/language-reference/keywords/abstract.md)成員或更改現有類型的語義或行為，則可以將其引入到兩種現有類型的層次結構中。</span><span class="sxs-lookup"><span data-stu-id="b4dad-131">A type can be introduced into a hierarchy between two existing types if it doesn't introduce any new [abstract](../../csharp/language-reference/keywords/abstract.md) members or change the semantics or behavior of existing types.</span></span> <span data-ttu-id="b4dad-132">例如，在 .NET Framework 2.0 中，<xref:System.Data.Common.DbConnection> 類別成為 <xref:System.Data.SqlClient.SqlConnection> 的新基底類別，它先前直接衍生自 <xref:System.ComponentModel.Component>。</span><span class="sxs-lookup"><span data-stu-id="b4dad-132">For example, in .NET Framework 2.0, the <xref:System.Data.Common.DbConnection> class became a new base class for <xref:System.Data.SqlClient.SqlConnection>, which had previously derived directly from <xref:System.ComponentModel.Component>.</span></span>

- <span data-ttu-id="b4dad-133">✔️**允許：將類型從一個程式集移動到另一個程式集**</span><span class="sxs-lookup"><span data-stu-id="b4dad-133">✔️ **ALLOWED: Moving a type from one assembly to another**</span></span>

  <span data-ttu-id="b4dad-134">*舊*程式集必須用<xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>指向新程式集的 標記。</span><span class="sxs-lookup"><span data-stu-id="b4dad-134">The *old* assembly must be marked with the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> that points to the new assembly.</span></span>

- <span data-ttu-id="b4dad-135">✔️**允許：將[結構](../../csharp/language-reference/builtin-types/struct.md)類型`readonly struct`更改為類型**</span><span class="sxs-lookup"><span data-stu-id="b4dad-135">✔️ **ALLOWED: Changing a [struct](../../csharp/language-reference/builtin-types/struct.md) type to a `readonly struct` type**</span></span>

  <span data-ttu-id="b4dad-136">不允許將`readonly struct`類型更改為`struct`類型。</span><span class="sxs-lookup"><span data-stu-id="b4dad-136">Changing a `readonly struct` type to a `struct` type is not allowed.</span></span>

- <span data-ttu-id="b4dad-137">✔️**允許：在沒有*可訪問*（公共或受保護）建構函式時，將[密封](../../csharp/language-reference/keywords/sealed.md)或[抽象](../../csharp/language-reference/keywords/abstract.md)關鍵字添加到類型中**</span><span class="sxs-lookup"><span data-stu-id="b4dad-137">✔️ **ALLOWED: Adding the [sealed](../../csharp/language-reference/keywords/sealed.md) or [abstract](../../csharp/language-reference/keywords/abstract.md) keyword to a type when there are no *accessible* (public or protected) constructors**</span></span>

- <span data-ttu-id="b4dad-138">✔️**允許：擴大某種類型的可見度**</span><span class="sxs-lookup"><span data-stu-id="b4dad-138">✔️ **ALLOWED: Expanding the visibility of a type**</span></span>

- <span data-ttu-id="b4dad-139">❌**取消：更改類型的命名空間或名稱**</span><span class="sxs-lookup"><span data-stu-id="b4dad-139">❌ **DISALLOWED: Changing the namespace or name of a type**</span></span>

- <span data-ttu-id="b4dad-140">❌**取消：重命名或刪除公共類型**</span><span class="sxs-lookup"><span data-stu-id="b4dad-140">❌ **DISALLOWED: Renaming or removing a public type**</span></span>

   <span data-ttu-id="b4dad-141">這會中斷使用已重新命名或已移除之型別的所有程式碼。</span><span class="sxs-lookup"><span data-stu-id="b4dad-141">This breaks all code that uses the renamed or removed type.</span></span>

- <span data-ttu-id="b4dad-142">❌**取消：更改枚舉的基礎類型**</span><span class="sxs-lookup"><span data-stu-id="b4dad-142">❌ **DISALLOWED: Changing the underlying type of an enumeration**</span></span>

   <span data-ttu-id="b4dad-143">這是編譯時期和行為的中斷性變更，以及可以使屬性引數無法進行剖析的二進位中斷性變更。</span><span class="sxs-lookup"><span data-stu-id="b4dad-143">This is a compile-time and behavioral breaking change as well as a binary breaking change that can make attribute arguments unparsable.</span></span>

- <span data-ttu-id="b4dad-144">❌**非封閉：密封以前未密封的類型**</span><span class="sxs-lookup"><span data-stu-id="b4dad-144">❌ **DISALLOWED: Sealing a type that was previously unsealed**</span></span>

- <span data-ttu-id="b4dad-145">❌**拒絕：將介面添加到介面的基類型集**</span><span class="sxs-lookup"><span data-stu-id="b4dad-145">❌ **DISALLOWED: Adding an interface to the set of base types of an interface**</span></span>

   <span data-ttu-id="b4dad-146">如果介面實作先前未實作的介面，則實作介面原始版本的所有型別都會中斷。</span><span class="sxs-lookup"><span data-stu-id="b4dad-146">If an interface implements an interface that it previously did not implement, all types that implemented the original version of the interface are broken.</span></span>

- <span data-ttu-id="b4dad-147">❓**要求：從基類集或介面從已實現的介面集中刪除類**</span><span class="sxs-lookup"><span data-stu-id="b4dad-147">❓ **REQUIRES JUDGMENT: Removing a class from the set of base classes or an interface from the set of implemented interfaces**</span></span>

  <span data-ttu-id="b4dad-148">介面移除規則有一個例外：您可以新增衍生自已移除之介面的介面實作。</span><span class="sxs-lookup"><span data-stu-id="b4dad-148">There is one exception to the rule for interface removal: you can add the implementation of an interface that derives from the removed interface.</span></span> <span data-ttu-id="b4dad-149">例如，如果型別或介面現在實作 <xref:System.ComponentModel.IComponent> (它會實作 <xref:System.IDisposable>)，則可以移除 <xref:System.IDisposable>。</span><span class="sxs-lookup"><span data-stu-id="b4dad-149">For example, you can remove <xref:System.IDisposable> if the type or interface now implements <xref:System.ComponentModel.IComponent>, which implements <xref:System.IDisposable>.</span></span>

- <span data-ttu-id="b4dad-150">❌**拒絕：將`readonly struct`類型更改為[結構](../../csharp/language-reference/builtin-types/struct.md)類型**</span><span class="sxs-lookup"><span data-stu-id="b4dad-150">❌ **DISALLOWED: Changing a `readonly struct` type to a [struct](../../csharp/language-reference/builtin-types/struct.md) type**</span></span>

  <span data-ttu-id="b4dad-151">但是，`struct`允許將類型更改為`readonly struct`類型。</span><span class="sxs-lookup"><span data-stu-id="b4dad-151">The change of a `struct` type to a `readonly struct` type is allowed, however.</span></span>

- <span data-ttu-id="b4dad-152">❌**拒絕：將[結構](../../csharp/language-reference/builtin-types/struct.md)類型更改為`ref struct`類型，反之亦然**</span><span class="sxs-lookup"><span data-stu-id="b4dad-152">❌ **DISALLOWED: Changing a [struct](../../csharp/language-reference/builtin-types/struct.md) type to a `ref struct` type, and vice versa**</span></span>

- <span data-ttu-id="b4dad-153">❌**禁止：降低類型的可見度**</span><span class="sxs-lookup"><span data-stu-id="b4dad-153">❌ **DISALLOWED: Reducing the visibility of a type**</span></span>

   <span data-ttu-id="b4dad-154">但是，允許增加型別的可見性。</span><span class="sxs-lookup"><span data-stu-id="b4dad-154">However, increasing the visibility of a type is allowed.</span></span>

### <a name="members"></a><span data-ttu-id="b4dad-155">成員</span><span class="sxs-lookup"><span data-stu-id="b4dad-155">Members</span></span>

- <span data-ttu-id="b4dad-156">✔️**允許：擴展不是[虛擬](../../csharp/language-reference/keywords/sealed.md)成員的可見度**</span><span class="sxs-lookup"><span data-stu-id="b4dad-156">✔️ **ALLOWED: Expanding the visibility of a member that is not [virtual](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="b4dad-157">✔️**允許：將抽象成員添加到沒有*可訪問*（公共或受保護）建構函式或該類型[已密封](../../csharp/language-reference/keywords/sealed.md)的公共類型**</span><span class="sxs-lookup"><span data-stu-id="b4dad-157">✔️ **ALLOWED: Adding an abstract member to a public type that has no *accessible* (public or protected) constructors, or the type is [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

  <span data-ttu-id="b4dad-158">但是，不允許將抽象成員新增至具有可存取 (公用或受保護) 建構函式且不是 `sealed` 的型別。</span><span class="sxs-lookup"><span data-stu-id="b4dad-158">However, adding an abstract member to a type that has accessible (public or protected) constructors and is not `sealed` is not allowed.</span></span>

- <span data-ttu-id="b4dad-159">✔️**允許：當類型沒有可訪問（公共或受保護）建構函式或類型[密封](../../csharp/language-reference/keywords/sealed.md)時，限制[受保護](../../csharp/language-reference/keywords/protected.md)成員的可見度**</span><span class="sxs-lookup"><span data-stu-id="b4dad-159">✔️ **ALLOWED: Restricting the visibility of a [protected](../../csharp/language-reference/keywords/protected.md) member when the type has no accessible (public or protected) constructors, or the type is [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="b4dad-160">✔️**允許：將成員移動到層次結構中比從中刪除該成員的類型更高的類中**</span><span class="sxs-lookup"><span data-stu-id="b4dad-160">✔️ **ALLOWED: Moving a member into a class higher in the hierarchy than the type from which it was removed**</span></span>

- <span data-ttu-id="b4dad-161">✔️**允許：添加或刪除覆蓋**</span><span class="sxs-lookup"><span data-stu-id="b4dad-161">✔️ **ALLOWED: Adding or removing an override**</span></span>

  <span data-ttu-id="b4dad-162">引入重寫可能會導致以前的消費者在調用[base](../../csharp/language-reference/keywords/base.md)時跳過重寫。</span><span class="sxs-lookup"><span data-stu-id="b4dad-162">Introducing an override might cause previous consumers to skip over the override when calling [base](../../csharp/language-reference/keywords/base.md).</span></span>

- <span data-ttu-id="b4dad-163">✔️**允許：如果類以前沒有建構函式，則將建構函式添加到類和無參數建構函式**</span><span class="sxs-lookup"><span data-stu-id="b4dad-163">✔️ **ALLOWED: Adding a constructor to a class, along with a parameterless constructor if the class previously had no constructors**</span></span>

   <span data-ttu-id="b4dad-164">但是，不允許將建構函式新增至先前沒有建構函式且沒有\*\* 新增無參數建構函式的類別。</span><span class="sxs-lookup"><span data-stu-id="b4dad-164">However, adding a constructor to a class that previously had no constructors *without* adding the parameterless constructor is not allowed.</span></span>

- <span data-ttu-id="b4dad-165">✔️**允許：將成員從[抽象](../../csharp/language-reference/keywords/abstract.md)更改為[虛擬](../../csharp/language-reference/keywords/virtual.md)**</span><span class="sxs-lookup"><span data-stu-id="b4dad-165">✔️ **ALLOWED: Changing a member from [abstract](../../csharp/language-reference/keywords/abstract.md) to [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

- <span data-ttu-id="b4dad-166">✔️**允許：從`ref readonly`更改為`ref`傳回值（虛擬方法或介面除外）**</span><span class="sxs-lookup"><span data-stu-id="b4dad-166">✔️ **ALLOWED: Changing from a `ref readonly` to a `ref` return value (except for virtual methods or interfaces)**</span></span>

- <span data-ttu-id="b4dad-167">✔️**允許：從欄位中刪除[唯讀](../../csharp/language-reference/keywords/readonly.md)，除非欄位的靜態類型是可變數值型別**</span><span class="sxs-lookup"><span data-stu-id="b4dad-167">✔️ **ALLOWED: Removing [readonly](../../csharp/language-reference/keywords/readonly.md) from a field, unless the static type of the field is a mutable value type**</span></span>

- <span data-ttu-id="b4dad-168">✔️**允許：調用以前未定義的新事件**</span><span class="sxs-lookup"><span data-stu-id="b4dad-168">✔️ **ALLOWED: Calling a new event that wasn't previously defined**</span></span>

- <span data-ttu-id="b4dad-169">❓**要求：向類型添加新實例欄位**</span><span class="sxs-lookup"><span data-stu-id="b4dad-169">❓ **REQUIRES JUDGMENT: Adding a new instance field to a type**</span></span>

   <span data-ttu-id="b4dad-170">此變更會影響序列化。</span><span class="sxs-lookup"><span data-stu-id="b4dad-170">This change impacts serialization.</span></span>

- <span data-ttu-id="b4dad-171">❌**取消：重命名或刪除公共成員或參數**</span><span class="sxs-lookup"><span data-stu-id="b4dad-171">❌ **DISALLOWED: Renaming or removing a public member or parameter**</span></span>

   <span data-ttu-id="b4dad-172">這會中斷使用已重新命名或已移除之成員或參數的所有程式碼。</span><span class="sxs-lookup"><span data-stu-id="b4dad-172">This breaks all code that uses the renamed or removed member, or parameter.</span></span>

   <span data-ttu-id="b4dad-173">這包括從屬性中刪除或重命名 getter 或 setter，以及重命名或刪除枚舉成員。</span><span class="sxs-lookup"><span data-stu-id="b4dad-173">This includes removing or renaming a getter or setter from a property, as well as renaming or removing enumeration members.</span></span>

- <span data-ttu-id="b4dad-174">❌**拒絕：將成員添加到介面**</span><span class="sxs-lookup"><span data-stu-id="b4dad-174">❌ **DISALLOWED: Adding a member to an interface**</span></span>

- <span data-ttu-id="b4dad-175">❌**取消：更改公共常量或枚舉成員的值**</span><span class="sxs-lookup"><span data-stu-id="b4dad-175">❌ **DISALLOWED: Changing the value of a public constant or enumeration member**</span></span>

- <span data-ttu-id="b4dad-176">❌**取消：更改屬性、欄位、參數或傳回值的類型**</span><span class="sxs-lookup"><span data-stu-id="b4dad-176">❌ **DISALLOWED: Changing the type of a property, field, parameter, or return value**</span></span>

- <span data-ttu-id="b4dad-177">❌**取消：添加、刪除或更改參數的順序**</span><span class="sxs-lookup"><span data-stu-id="b4dad-177">❌ **DISALLOWED: Adding, removing, or changing the order of parameters**</span></span>

- <span data-ttu-id="b4dad-178">❌**拒絕：從參數[中](../../csharp/language-reference/keywords/in.md)添加或刪除 中[、out](../../csharp/language-reference/keywords/out.md)或[ref](../../csharp/language-reference/keywords/ref.md)關鍵字**</span><span class="sxs-lookup"><span data-stu-id="b4dad-178">❌ **DISALLOWED: Adding or removing the [in](../../csharp/language-reference/keywords/in.md), [out](../../csharp/language-reference/keywords/out.md) , or [ref](../../csharp/language-reference/keywords/ref.md) keyword from a parameter**</span></span>

- <span data-ttu-id="b4dad-179">❌**取消：重具名引數（包括更改其大小寫）**</span><span class="sxs-lookup"><span data-stu-id="b4dad-179">❌ **DISALLOWED: Renaming a parameter (including changing its case)**</span></span>

  <span data-ttu-id="b4dad-180">這會視為中斷的原因有二：</span><span class="sxs-lookup"><span data-stu-id="b4dad-180">This is considered breaking for two reasons:</span></span>

  - <span data-ttu-id="b4dad-181">它中斷了晚期繫結的案例，例如 Visual Basic 中的晚期繫結功能和 C# 中的 [dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type)。</span><span class="sxs-lookup"><span data-stu-id="b4dad-181">It breaks late-bound scenarios such as the late binding feature in Visual Basic and [dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) in C#.</span></span>

  - <span data-ttu-id="b4dad-182">當開發人員使用[具名引數](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments)時，它會中斷[來源相容性](categories.md#source-compatibility)。</span><span class="sxs-lookup"><span data-stu-id="b4dad-182">It breaks [source compatibility](categories.md#source-compatibility) when developers use [named arguments](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).</span></span>

- <span data-ttu-id="b4dad-183">❌**拒絕：從`ref`傳回值更改為`ref readonly`傳回值**</span><span class="sxs-lookup"><span data-stu-id="b4dad-183">❌ **DISALLOWED: Changing from a `ref` return value to a `ref readonly` return value**</span></span>

- <span data-ttu-id="b4dad-184">❌️**拒絕：在虛擬方法或`ref readonly`介面上`ref`從 更改為傳回值**</span><span class="sxs-lookup"><span data-stu-id="b4dad-184">❌️ **DISALLOWED: Changing from a `ref readonly` to a `ref` return value on a virtual method or interface**</span></span>

- <span data-ttu-id="b4dad-185">❌**禁止：從成員添加或刪除[摘要](../../csharp/language-reference/keywords/abstract.md)**</span><span class="sxs-lookup"><span data-stu-id="b4dad-185">❌ **DISALLOWED: Adding or removing [abstract](../../csharp/language-reference/keywords/abstract.md) from a member**</span></span>

- <span data-ttu-id="b4dad-186">❌**取消：從成員中刪除[虛擬](../../csharp/language-reference/keywords/virtual.md)關鍵字**</span><span class="sxs-lookup"><span data-stu-id="b4dad-186">❌ **DISALLOWED: Removing the [virtual](../../csharp/language-reference/keywords/virtual.md) keyword from a member**</span></span>

  <span data-ttu-id="b4dad-187">雖然這通常不是一個中斷性變更，因為 C# 編譯器傾向於發出 [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) 中繼語言 (IL) 指令以呼叫非虛擬方法 (`callvirt` 會執行 Null 檢查，而正常呼叫不會)，由於以下幾個原因，此行為並不是不變的：</span><span class="sxs-lookup"><span data-stu-id="b4dad-187">While this often is not a breaking change because the C# compiler tends to emit [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) Intermediate Language (IL) instructions to call non-virtual methods (`callvirt` performs a null check, while a normal call doesn't), this behavior is not invariable for several reasons:</span></span>
  - <span data-ttu-id="b4dad-188">C# 不是 .NET 以其為目標的唯一語言。</span><span class="sxs-lookup"><span data-stu-id="b4dad-188">C# is not the only language that .NET targets.</span></span>

  - <span data-ttu-id="b4dad-189">只要目標方法為非虛擬且可能不是 Null 時 (例如透過 [?. null 傳播運算子](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)存取的方法)，C# 編譯器就會漸漸地嘗試將 `callvirt` 最佳化為正常呼叫。</span><span class="sxs-lookup"><span data-stu-id="b4dad-189">The C# compiler increasingly tries to optimize `callvirt` to a normal call whenever the target method is non-virtual and is probably not null (such as a method accessed through the [?. null propagation operator](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).</span></span>

  <span data-ttu-id="b4dad-190">使方法成為虛擬表示取用者程式碼通常最後會以非虛擬方式呼叫它。</span><span class="sxs-lookup"><span data-stu-id="b4dad-190">Making a method virtual means that the consumer code would often end up calling it non-virtually.</span></span>

- <span data-ttu-id="b4dad-191">❌**拒絕：將[虛擬](../../csharp/language-reference/keywords/virtual.md)關鍵字添加到成員**</span><span class="sxs-lookup"><span data-stu-id="b4dad-191">❌ **DISALLOWED: Adding the [virtual](../../csharp/language-reference/keywords/virtual.md) keyword to a member**</span></span>

- <span data-ttu-id="b4dad-192">❌**內容：使虛擬成員抽象**</span><span class="sxs-lookup"><span data-stu-id="b4dad-192">❌ **DISALLOWED: Making a virtual member abstract**</span></span>

  <span data-ttu-id="b4dad-193">[虛擬成員](../../csharp/language-reference/keywords/virtual.md)提供了一種方法實作，可以\*\* 由衍生類別覆寫。</span><span class="sxs-lookup"><span data-stu-id="b4dad-193">A [virtual member](../../csharp/language-reference/keywords/virtual.md) provides a method implementation that *can be* overridden by a derived class.</span></span> <span data-ttu-id="b4dad-194">[抽象成員](../../csharp/language-reference/keywords/abstract.md)不提供任何實作，且必須\*\* 被覆寫。</span><span class="sxs-lookup"><span data-stu-id="b4dad-194">An [abstract member](../../csharp/language-reference/keywords/abstract.md) provides no implementation and *must be* overridden.</span></span>

- <span data-ttu-id="b4dad-195">❌**拒絕：將抽象成員添加到具有可訪問（公共或受保護）建構函式且未[密封](../../csharp/language-reference/keywords/sealed.md)的公共類型**</span><span class="sxs-lookup"><span data-stu-id="b4dad-195">❌ **DISALLOWED: Adding an abstract member to a public type that has accessible (public or protected) constructors and that is not [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="b4dad-196">❌**取消：從成員添加或刪除[靜態](../../csharp/language-reference/keywords/static.md)關鍵字**</span><span class="sxs-lookup"><span data-stu-id="b4dad-196">❌ **DISALLOWED: Adding or removing the [static](../../csharp/language-reference/keywords/static.md) keyword from a member**</span></span>

- <span data-ttu-id="b4dad-197">❌**取消：添加排除現有重載並定義其他行為的重載**</span><span class="sxs-lookup"><span data-stu-id="b4dad-197">❌ **DISALLOWED: Adding an overload that precludes an existing overload and defines a different behavior**</span></span>

  <span data-ttu-id="b4dad-198">這會中斷繫結到先前多載的現有用戶端。</span><span class="sxs-lookup"><span data-stu-id="b4dad-198">This breaks existing clients that were bound to the previous overload.</span></span> <span data-ttu-id="b4dad-199">例如，如果某個類別具有接受 <xref:System.UInt32> 的方法的單一版本，則現有的取用者在傳遞 <xref:System.Int32> 值時將成功繫結至該多載。</span><span class="sxs-lookup"><span data-stu-id="b4dad-199">For example, if a class has a single version of a method that accepts a <xref:System.UInt32>, an existing consumer will successfully bind to that overload when passing a <xref:System.Int32> value.</span></span> <span data-ttu-id="b4dad-200">但是，如果新增接受 <xref:System.Int32> 的多載，則在重新編譯或使用晚期繫結時，編譯器現在會繫結至新的多載。</span><span class="sxs-lookup"><span data-stu-id="b4dad-200">However, if you add an overload that accepts an <xref:System.Int32>, when recompiling or using late-binding, the compiler now binds to the new overload.</span></span> <span data-ttu-id="b4dad-201">如果產生不同的行為，這是一個中斷性變更。</span><span class="sxs-lookup"><span data-stu-id="b4dad-201">If different behavior results, this is a breaking change.</span></span>

- <span data-ttu-id="b4dad-202">❌**拒絕：將建構函式添加到以前沒有建構函式的類，而不添加無參數建構函式**</span><span class="sxs-lookup"><span data-stu-id="b4dad-202">❌ **DISALLOWED: Adding a constructor to a class that previously had no constructor without adding the parameterless constructor**</span></span>

- <span data-ttu-id="b4dad-203">❌️**拒絕：將[可讀添加到](../../csharp/language-reference/keywords/readonly.md)欄位**</span><span class="sxs-lookup"><span data-stu-id="b4dad-203">❌️ **DISALLOWED: Adding [readonly](../../csharp/language-reference/keywords/readonly.md) to a field**</span></span>

- <span data-ttu-id="b4dad-204">❌**禁止：降低成員的可見度**</span><span class="sxs-lookup"><span data-stu-id="b4dad-204">❌ **DISALLOWED: Reducing the visibility of a member**</span></span>

   <span data-ttu-id="b4dad-205">這包括在*存在可訪問*（`public``protected`或 ） 建構函式且類型*未*[密封](../../csharp/language-reference/keywords/sealed.md)時降低[受保護](../../csharp/language-reference/keywords/protected.md)成員的可見度。</span><span class="sxs-lookup"><span data-stu-id="b4dad-205">This includes reducing the visibility of a [protected](../../csharp/language-reference/keywords/protected.md) member when there are *accessible* (`public` or `protected`) constructors and the type is *not* [sealed](../../csharp/language-reference/keywords/sealed.md).</span></span> <span data-ttu-id="b4dad-206">如果不是這種情況，則允許降低受保護成員的可見性。</span><span class="sxs-lookup"><span data-stu-id="b4dad-206">If this is not the case, reducing the visibility of a protected member is allowed.</span></span>

   <span data-ttu-id="b4dad-207">允許增加成員的可見度。</span><span class="sxs-lookup"><span data-stu-id="b4dad-207">Increasing the visibility of a member is allowed.</span></span>

- <span data-ttu-id="b4dad-208">❌**取消：更改成員的類型**</span><span class="sxs-lookup"><span data-stu-id="b4dad-208">❌ **DISALLOWED: Changing the type of a member**</span></span>

   <span data-ttu-id="b4dad-209">無法修改方法的傳回值，或屬性或欄位的型別。</span><span class="sxs-lookup"><span data-stu-id="b4dad-209">The return value of a method or the type of a property or field cannot be modified.</span></span> <span data-ttu-id="b4dad-210">例如，傳回 <xref:System.Object> 之方法的簽章不能變更為傳回 <xref:System.String>，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="b4dad-210">For example, the signature of a method that returns an <xref:System.Object> cannot be changed to return a <xref:System.String>, or vice versa.</span></span>

- <span data-ttu-id="b4dad-211">❌**拒絕：將欄位添加到以前沒有狀態的結構**</span><span class="sxs-lookup"><span data-stu-id="b4dad-211">❌ **DISALLOWED: Adding a field to a struct that previously had no state**</span></span>

  <span data-ttu-id="b4dad-212">只要變數型別是無狀態結構，明確指派規則就允許使用未初始化的變數。</span><span class="sxs-lookup"><span data-stu-id="b4dad-212">Definite assignment rules allow the use of uninitialized variables so long as the variable type is a stateless struct.</span></span> <span data-ttu-id="b4dad-213">如果將結構設定為具狀態，程式碼最後可能會遇到未初始化的資料。</span><span class="sxs-lookup"><span data-stu-id="b4dad-213">If the struct is made stateful, code could end up with uninitialized data.</span></span> <span data-ttu-id="b4dad-214">這可能是一個來源中斷和二進位中斷性變更。</span><span class="sxs-lookup"><span data-stu-id="b4dad-214">This is both potentially a source breaking and a binary breaking change.</span></span>

- <span data-ttu-id="b4dad-215">❌**未通過：在以前從未觸發現有事件時觸發它**</span><span class="sxs-lookup"><span data-stu-id="b4dad-215">❌ **DISALLOWED: Firing an existing event when it was never fired before**</span></span>

## <a name="behavioral-changes"></a><span data-ttu-id="b4dad-216">行為變更</span><span class="sxs-lookup"><span data-stu-id="b4dad-216">Behavioral changes</span></span>

### <a name="assemblies"></a><span data-ttu-id="b4dad-217">組件</span><span class="sxs-lookup"><span data-stu-id="b4dad-217">Assemblies</span></span>

- <span data-ttu-id="b4dad-218">✔️**允許：在仍支援相同平臺時使元件便於使用**</span><span class="sxs-lookup"><span data-stu-id="b4dad-218">✔️ **ALLOWED: Making an assembly portable when the same platforms are still supported**</span></span>

- <span data-ttu-id="b4dad-219">❌**取消：更改程式集的名稱**</span><span class="sxs-lookup"><span data-stu-id="b4dad-219">❌ **DISALLOWED: Changing the name of an assembly**</span></span>
- <span data-ttu-id="b4dad-220">❌**取消：更改程式集的公開金鑰**</span><span class="sxs-lookup"><span data-stu-id="b4dad-220">❌ **DISALLOWED: Changing the public key of an assembly**</span></span>

### <a name="properties-fields-parameters-and-return-values"></a><span data-ttu-id="b4dad-221">屬性、欄位、參數與傳回值</span><span class="sxs-lookup"><span data-stu-id="b4dad-221">Properties, fields, parameters, and return values</span></span>

- <span data-ttu-id="b4dad-222">✔️**允許：將屬性、欄位、傳回值或[出](../../csharp/language-reference/keywords/out-parameter-modifier.md)參數的值更改為更派生的類型**</span><span class="sxs-lookup"><span data-stu-id="b4dad-222">✔️ **ALLOWED: Changing the value of a property, field, return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter to a more derived type**</span></span>

  <span data-ttu-id="b4dad-223">例如，傳回 <xref:System.Object> 型別的方法可以傳回 <xref:System.String> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="b4dad-223">For example, a method that returns a type of <xref:System.Object> can return a <xref:System.String> instance.</span></span> <span data-ttu-id="b4dad-224">(但是，無法變更方法簽章。)</span><span class="sxs-lookup"><span data-stu-id="b4dad-224">(However, the method signature cannot change.)</span></span>

- <span data-ttu-id="b4dad-225">✔️**允許：如果成員不是[虛擬](../../csharp/language-reference/keywords/virtual.md)的，則增加屬性或參數的已接受值範圍**</span><span class="sxs-lookup"><span data-stu-id="b4dad-225">✔️ **ALLOWED: Increasing the range of accepted values for a property or parameter if the member is not [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

  <span data-ttu-id="b4dad-226">雖然可以傳遞給方法或由成員返回的值範圍可以展開，但參數或成員類型不能。</span><span class="sxs-lookup"><span data-stu-id="b4dad-226">While the range of values that can be passed to the method or are returned by the member can expand, the parameter or member type cannot.</span></span> <span data-ttu-id="b4dad-227">例如，雖然傳遞至方法的值可以從 0-124 擴充至 0-255，但參數類型無法從 <xref:System.Byte> 變更為 <xref:System.Int32>。</span><span class="sxs-lookup"><span data-stu-id="b4dad-227">For example, while the values passed to a method can expand from 0-124 to 0-255, the parameter type cannot change from <xref:System.Byte> to <xref:System.Int32>.</span></span>

- <span data-ttu-id="b4dad-228">❌**禁止：如果成員為[虛擬](../../csharp/language-reference/keywords/virtual.md)，則增加屬性或參數的已接受值範圍**</span><span class="sxs-lookup"><span data-stu-id="b4dad-228">❌ **DISALLOWED: Increasing the range of accepted values for a property or parameter if the member is [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

   <span data-ttu-id="b4dad-229">此變更會中斷現有的覆寫成員，這些成員將無法在擴充的值範圍內正常執行。</span><span class="sxs-lookup"><span data-stu-id="b4dad-229">This change breaks existing overridden members, which will not function correctly for the extended range of values.</span></span>

- <span data-ttu-id="b4dad-230">❌**取消：減小屬性或參數的已接受值範圍**</span><span class="sxs-lookup"><span data-stu-id="b4dad-230">❌ **DISALLOWED: Decreasing the range of accepted values for a property or parameter**</span></span>

- <span data-ttu-id="b4dad-231">❌**取消：增加屬性、欄位、傳回值或[出參數](../../csharp/language-reference/keywords/out-parameter-modifier.md)的傳回值範圍**</span><span class="sxs-lookup"><span data-stu-id="b4dad-231">❌ **DISALLOWED: Increasing the range of returned values for a property, field, return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter**</span></span>

- <span data-ttu-id="b4dad-232">❌**取消：更改屬性、欄位、方法傳回值或[out](../../csharp/language-reference/keywords/out-parameter-modifier.md)參數的傳回值**</span><span class="sxs-lookup"><span data-stu-id="b4dad-232">❌ **DISALLOWED: Changing the returned values for a property, field, method return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter**</span></span>

- <span data-ttu-id="b4dad-233">❌**拒絕：更改屬性、欄位或參數的預設值**</span><span class="sxs-lookup"><span data-stu-id="b4dad-233">❌ **DISALLOWED: Changing the default value of a property, field, or parameter**</span></span>

- <span data-ttu-id="b4dad-234">❌**非分配：更改數值傳回值的精度**</span><span class="sxs-lookup"><span data-stu-id="b4dad-234">❌ **DISALLOWED: Changing the precision of a numeric return value**</span></span>

- <span data-ttu-id="b4dad-235">❓**要求判斷：在分析輸入和引發新異常時發生更改（即使文檔中未指定分析行為**）</span><span class="sxs-lookup"><span data-stu-id="b4dad-235">❓ **REQUIRES JUDGMENT: A change in the parsing of input and throwing new exceptions (even if parsing behavior is not specified in the documentation**</span></span>

### <a name="exceptions"></a><span data-ttu-id="b4dad-236">例外狀況</span><span class="sxs-lookup"><span data-stu-id="b4dad-236">Exceptions</span></span>

- <span data-ttu-id="b4dad-237">✔️**允許：引發比現有異常更派生的異常**</span><span class="sxs-lookup"><span data-stu-id="b4dad-237">✔️ **ALLOWED: Throwing a more derived exception than an existing exception**</span></span>

  <span data-ttu-id="b4dad-238">因為新的例外狀況是現有例外狀況的子類別，所以先前的例外狀況處理程式碼會繼續處理例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b4dad-238">Because the new exception is a subclass of an existing exception, previous exception handling code continues to handle the exception.</span></span> <span data-ttu-id="b4dad-239">例如，在 .NET Framework 4 中，文化特性建立和擷取方法已開始擲回 <xref:System.Globalization.CultureNotFoundException> 而不是 <xref:System.ArgumentException> (如果找不到文化特性)。</span><span class="sxs-lookup"><span data-stu-id="b4dad-239">For example, in .NET Framework 4, culture creation and retrieval methods began to throw a <xref:System.Globalization.CultureNotFoundException> instead of an <xref:System.ArgumentException> if the culture could not be found.</span></span> <span data-ttu-id="b4dad-240">因為 <xref:System.Globalization.CultureNotFoundException> 衍生自 <xref:System.ArgumentException>，所以這是一個可接受的變更。</span><span class="sxs-lookup"><span data-stu-id="b4dad-240">Because <xref:System.Globalization.CultureNotFoundException> derives from <xref:System.ArgumentException>, this is an acceptable change.</span></span>

- <span data-ttu-id="b4dad-241">✔️\*\*允許：引發比<xref:System.NotSupportedException>更具體的異常， <xref:System.NullReferenceException> <xref:System.NotImplementedException> \*\*</span><span class="sxs-lookup"><span data-stu-id="b4dad-241">✔️ **ALLOWED: Throwing a more specific exception than <xref:System.NotSupportedException>, <xref:System.NotImplementedException>, <xref:System.NullReferenceException>**</span></span>

- <span data-ttu-id="b4dad-242">✔️**允許：引發被視為不可恢復的異常**</span><span class="sxs-lookup"><span data-stu-id="b4dad-242">✔️ **ALLOWED: Throwing an exception that is considered unrecoverable**</span></span>

  <span data-ttu-id="b4dad-243">無法復原的例外狀況不應該攔截，而應該由高層級追補處理常式處理。</span><span class="sxs-lookup"><span data-stu-id="b4dad-243">Unrecoverable exceptions should not be caught but instead should be handled by a high-level catch-all handler.</span></span> <span data-ttu-id="b4dad-244">因此，使用者不應該擁有攔截這些明確例外狀況的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b4dad-244">Therefore, users are not expected to have code that catches these explicit exceptions.</span></span> <span data-ttu-id="b4dad-245">無法復原的例外狀況有：</span><span class="sxs-lookup"><span data-stu-id="b4dad-245">The unrecoverable exceptions are:</span></span>

  - <xref:System.AccessViolationException>
  - <xref:System.ExecutionEngineException>
  - <xref:System.Runtime.InteropServices.SEHException>
  - <xref:System.StackOverflowException>

- <span data-ttu-id="b4dad-246">✔️**允許：在新的代碼路徑中引發新的異常**</span><span class="sxs-lookup"><span data-stu-id="b4dad-246">✔️ **ALLOWED: Throwing a new exception in a new code path**</span></span>

  <span data-ttu-id="b4dad-247">該異常必須僅適用于使用新參數值或狀態執行且無法由面向早期版本的現有代碼執行的新代碼路徑。</span><span class="sxs-lookup"><span data-stu-id="b4dad-247">The exception must apply only to a new code-path that's executed with new parameter values or state and that can't be executed by existing code that targets the previous version.</span></span>

- <span data-ttu-id="b4dad-248">✔️**允許：刪除異常以啟用更健壯的行為或新方案**</span><span class="sxs-lookup"><span data-stu-id="b4dad-248">✔️ **ALLOWED: Removing an exception to enable more robust behavior or new scenarios**</span></span>

  <span data-ttu-id="b4dad-249">例如，之前只處理正值並擲回 <xref:System.ArgumentOutOfRangeException> 的 `Divide` 方法可以變更為支援負值和正值，而不擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b4dad-249">For example, a `Divide` method that previously only handled positive values and threw an <xref:System.ArgumentOutOfRangeException> otherwise can be changed to support both negative and positive values without throwing an exception.</span></span>

- <span data-ttu-id="b4dad-250">✔️**允許：更改錯誤訊息的文本**</span><span class="sxs-lookup"><span data-stu-id="b4dad-250">✔️ **ALLOWED: Changing the text of an error message**</span></span>

  <span data-ttu-id="b4dad-251">開發人員不應該依賴錯誤訊息的文字，這也會根據使用者的文化特性而變更。</span><span class="sxs-lookup"><span data-stu-id="b4dad-251">Developers should not rely on the text of error messages, which also change based on the user's culture.</span></span>

- <span data-ttu-id="b4dad-252">❌**非保留：在上述未列出的任何其他情況下引發異常**</span><span class="sxs-lookup"><span data-stu-id="b4dad-252">❌ **DISALLOWED: Throwing an exception in any other case not listed above**</span></span>

- <span data-ttu-id="b4dad-253">❌**非保留：刪除上述未列出的任何其他情況下的異常**</span><span class="sxs-lookup"><span data-stu-id="b4dad-253">❌ **DISALLOWED: Removing an exception in any other case not listed above**</span></span>

### <a name="attributes"></a><span data-ttu-id="b4dad-254">屬性</span><span class="sxs-lookup"><span data-stu-id="b4dad-254">Attributes</span></span>

- <span data-ttu-id="b4dad-255">✔️**允許：更改*無法*觀察到的屬性的值**</span><span class="sxs-lookup"><span data-stu-id="b4dad-255">✔️ **ALLOWED: Changing the value of an attribute that is *not* observable**</span></span>

- <span data-ttu-id="b4dad-256">❌\**不可否認：更改可觀察屬性的值*is\* \*\*</span><span class="sxs-lookup"><span data-stu-id="b4dad-256">❌ **DISALLOWED: Changing the value of an attribute that *is* observable**</span></span>

- <span data-ttu-id="b4dad-257">❓**要求：刪除屬性**</span><span class="sxs-lookup"><span data-stu-id="b4dad-257">❓ **REQUIRES JUDGMENT: Removing an attribute**</span></span>

  <span data-ttu-id="b4dad-258">在大部分情況下，移除屬性 (例如<xref:System.NonSerializedAttribute>) 是一個中斷性變更。</span><span class="sxs-lookup"><span data-stu-id="b4dad-258">In most cases, removing an attribute (such as <xref:System.NonSerializedAttribute>) is a breaking change.</span></span>

## <a name="platform-support"></a><span data-ttu-id="b4dad-259">平台支援</span><span class="sxs-lookup"><span data-stu-id="b4dad-259">Platform support</span></span>

- <span data-ttu-id="b4dad-260">✔️**允許：支援以前不支援的平臺上的操作**</span><span class="sxs-lookup"><span data-stu-id="b4dad-260">✔️ **ALLOWED: Supporting an operation on a platform that was previously not supported**</span></span>

- <span data-ttu-id="b4dad-261">❌**取消：不支援或現在需要特定服務包，用於以前在平臺上支援的操作**</span><span class="sxs-lookup"><span data-stu-id="b4dad-261">❌ **DISALLOWED: Not supporting or now requiring a specific service pack for an operation that was previously supported on a platform**</span></span>

## <a name="internal-implementation-changes"></a><span data-ttu-id="b4dad-262">內部實作的變更</span><span class="sxs-lookup"><span data-stu-id="b4dad-262">Internal implementation changes</span></span>

- <span data-ttu-id="b4dad-263">❓**要求：更改內部類型的表面積**</span><span class="sxs-lookup"><span data-stu-id="b4dad-263">❓ **REQUIRES JUDGMENT: Changing the surface area of an internal type**</span></span>

   <span data-ttu-id="b4dad-264">通常允許此類變更，儘管它們可能會中斷私人反映。</span><span class="sxs-lookup"><span data-stu-id="b4dad-264">Such changes are generally allowed, although they break private reflection.</span></span> <span data-ttu-id="b4dad-265">在一些熱門的協力廠商程式庫或大量開發人員依賴內部 API 的案例中，可能不允許此類變更。</span><span class="sxs-lookup"><span data-stu-id="b4dad-265">In some cases, where popular third-party libraries or a large number of developers depend on the internal APIs, such changes may not be allowed.</span></span>

- <span data-ttu-id="b4dad-266">❓**要求：更改成員的內部實現**</span><span class="sxs-lookup"><span data-stu-id="b4dad-266">❓ **REQUIRES JUDGMENT: Changing the internal implementation of a member**</span></span>

  <span data-ttu-id="b4dad-267">通常允許這些變更，儘管它們可能會中斷私人反映。</span><span class="sxs-lookup"><span data-stu-id="b4dad-267">These changes are generally allowed, although they break private reflection.</span></span> <span data-ttu-id="b4dad-268">在一些客戶程式碼經常依賴私人反映或變更引進非預期之副作用的情況下，可能不允許這些變更。</span><span class="sxs-lookup"><span data-stu-id="b4dad-268">In some cases, where customer code frequently depends on private reflection or where the change introduces unintended side effects, these changes may not be allowed.</span></span>

- <span data-ttu-id="b4dad-269">**✔️：提高操作性能**</span><span class="sxs-lookup"><span data-stu-id="b4dad-269">✔️ **ALLOWED: Improving the performance of an operation**</span></span>

   <span data-ttu-id="b4dad-270">修改作業效能的能力是很重要的，但此類變更可能會中斷仰賴目前作業速度的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b4dad-270">The ability to modify the performance of an operation is essential, but such changes can break code that relies upon the current speed of an operation.</span></span> <span data-ttu-id="b4dad-271">對於仰賴非同步作業時間的程式碼尤其如此。</span><span class="sxs-lookup"><span data-stu-id="b4dad-271">This is particularly true of code that depends on the timing of asynchronous operations.</span></span> <span data-ttu-id="b4dad-272">性能更改不應對相關 API 的其他行為產生影響;否則，更改將中斷。</span><span class="sxs-lookup"><span data-stu-id="b4dad-272">The performance change should have no effect on other behavior of the API in question; otherwise, the change will be breaking.</span></span>

- <span data-ttu-id="b4dad-273">✔️**允許：間接（而且經常不利）改變操作性能**</span><span class="sxs-lookup"><span data-stu-id="b4dad-273">✔️ **ALLOWED: Indirectly (and often adversely) changing the performance of an operation**</span></span>

  <span data-ttu-id="b4dad-274">如果由於某些其他原因而未將相關變更歸類為中斷，則這是可以接受的。</span><span class="sxs-lookup"><span data-stu-id="b4dad-274">If the change in question is not categorized as breaking for some other reason, this is acceptable.</span></span> <span data-ttu-id="b4dad-275">通常，需要採取可能包括額外的作業或新增新功能的動作。</span><span class="sxs-lookup"><span data-stu-id="b4dad-275">Often, actions need to be taken that may include extra operations or that add new functionality.</span></span> <span data-ttu-id="b4dad-276">這幾乎一律會影響效能，但對於使相關 API 如預期般運作至關重要。</span><span class="sxs-lookup"><span data-stu-id="b4dad-276">This will almost always affect performance but may be essential to make the API in question function as expected.</span></span>

- <span data-ttu-id="b4dad-277">❌**非同步：將同步 API 更改為非同步（反之亦然）**</span><span class="sxs-lookup"><span data-stu-id="b4dad-277">❌ **DISALLOWED: Changing a synchronous API to asynchronous (and vice versa)**</span></span>

## <a name="code-changes"></a><span data-ttu-id="b4dad-278">程式碼變更</span><span class="sxs-lookup"><span data-stu-id="b4dad-278">Code changes</span></span>

- <span data-ttu-id="b4dad-279">✔️**允許：向參數添加[參數](../../csharp/language-reference/keywords/params.md)**</span><span class="sxs-lookup"><span data-stu-id="b4dad-279">✔️ **ALLOWED: Adding [params](../../csharp/language-reference/keywords/params.md) to a parameter**</span></span>

- <span data-ttu-id="b4dad-280">❌**拒絕：將[結構](../../csharp/language-reference/builtin-types/struct.md)更改為[類](../../csharp/language-reference/keywords/class.md)，反之亦然**</span><span class="sxs-lookup"><span data-stu-id="b4dad-280">❌ **DISALLOWED: Changing a [struct](../../csharp/language-reference/builtin-types/struct.md) to a [class](../../csharp/language-reference/keywords/class.md) and vice versa**</span></span>

- <span data-ttu-id="b4dad-281">❌**拒絕：將[選中](../../csharp/language-reference/keywords/virtual.md)的關鍵字添加到代碼塊**</span><span class="sxs-lookup"><span data-stu-id="b4dad-281">❌ **DISALLOWED: Adding the [checked](../../csharp/language-reference/keywords/virtual.md) keyword to a code block**</span></span>

   <span data-ttu-id="b4dad-282">此變更可能會導致先前執行的程式碼擲回 <xref:System.OverflowException> 且無法接受。</span><span class="sxs-lookup"><span data-stu-id="b4dad-282">This change may cause code that previously executed to throw an <xref:System.OverflowException> and is unacceptable.</span></span>

- <span data-ttu-id="b4dad-283">❌**取消：從參數中刪除[參數](../../csharp/language-reference/keywords/params.md)**</span><span class="sxs-lookup"><span data-stu-id="b4dad-283">❌ **DISALLOWED: Removing [params](../../csharp/language-reference/keywords/params.md) from a parameter**</span></span>

- <span data-ttu-id="b4dad-284">❌**取消：變更事件觸發順序**</span><span class="sxs-lookup"><span data-stu-id="b4dad-284">❌ **DISALLOWED: Changing the order in which events are fired**</span></span>

  <span data-ttu-id="b4dad-285">開發人員可以合理地預期事件以相同的順序引發，而開發人員程式碼經常會取決於事件的引發順序。</span><span class="sxs-lookup"><span data-stu-id="b4dad-285">Developers can reasonably expect events to fire in the same order, and developer code frequently depends on the order in which events are fired.</span></span>

- <span data-ttu-id="b4dad-286">❌**取消：刪除對給定操作引發事件**</span><span class="sxs-lookup"><span data-stu-id="b4dad-286">❌ **DISALLOWED: Removing the raising of an event on a given action**</span></span>

- <span data-ttu-id="b4dad-287">❌**取消：更改調用給定事件的次數**</span><span class="sxs-lookup"><span data-stu-id="b4dad-287">❌ **DISALLOWED: Changing the number of times given events are called**</span></span>

- <span data-ttu-id="b4dad-288">❌**拒絕：將 添加到<xref:System.FlagsAttribute>枚舉類型**</span><span class="sxs-lookup"><span data-stu-id="b4dad-288">❌ **DISALLOWED: Adding the <xref:System.FlagsAttribute> to an enumeration type**</span></span>
