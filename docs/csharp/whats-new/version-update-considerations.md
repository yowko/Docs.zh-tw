---
title: 適用於 C# 開發人員的版本和更新考量
description: 在您的程式庫中引進新的語言功能，會影響使用該程式庫的程式碼。
ms.date: 09/19/2018
ms.openlocfilehash: 3ffe2f6fd64a391fddf28233dccb022c95851884
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634482"
---
# <a name="version-and-update-considerations-for-c-developers"></a><span data-ttu-id="85dd5-103">適用於 C# 開發人員的版本和更新考量</span><span class="sxs-lookup"><span data-stu-id="85dd5-103">Version and update considerations for C# developers</span></span>

<span data-ttu-id="85dd5-104">將新功能新增至 C# 語言時，相容性是非常重要的目標。</span><span class="sxs-lookup"><span data-stu-id="85dd5-104">Compatibility is a very important goal as new features are added to the C# language.</span></span> <span data-ttu-id="85dd5-105">在幾乎所有情況下，現有程式碼可以使用新的編譯器版本重新編譯，不會有任何問題。</span><span class="sxs-lookup"><span data-stu-id="85dd5-105">In almost all cases, existing code can be recompiled with a new compiler version without any issue.</span></span>

<span data-ttu-id="85dd5-106">當您在程式庫中採用新語言功能時，可能需要更加小心。</span><span class="sxs-lookup"><span data-stu-id="85dd5-106">More care may be required when you adopt new language features in a library.</span></span> <span data-ttu-id="85dd5-107">您可能會使用最新版本中的功能來建立新程式庫，並需要確保使用舊版編譯器建置的應用程式可以使用它。</span><span class="sxs-lookup"><span data-stu-id="85dd5-107">You may be creating a new library with features found in the latest version and need to ensure apps built using previous versions of the compiler can use it.</span></span> <span data-ttu-id="85dd5-108">或者您可能升級了現有的程式庫，但是您的許多使用者都還沒有升級的版本。</span><span class="sxs-lookup"><span data-stu-id="85dd5-108">Or you may be upgrading an existing library and many of your users may not have upgraded versions yet.</span></span> <span data-ttu-id="85dd5-109">當您決定採用新功能時，需要考慮兩個相容性變化：來源相容及二進位相容。</span><span class="sxs-lookup"><span data-stu-id="85dd5-109">As you make decisions on adopting new features, you'll need to consider two variations of compatibility: source compatible and binary compatible.</span></span>

## <a name="binary-compatible-changes"></a><span data-ttu-id="85dd5-110">二進位相容變更</span><span class="sxs-lookup"><span data-stu-id="85dd5-110">Binary compatible changes</span></span>

<span data-ttu-id="85dd5-111">如果您更新了程式庫，而且不需要重建使用此程式庫的應用程式和程式庫就能開始使用，則您程式庫上的這些變更屬於**二進位相容**。</span><span class="sxs-lookup"><span data-stu-id="85dd5-111">Changes to your library are **binary compatible** when your updated library can be used without rebuilding applications and libraries that use it.</span></span> <span data-ttu-id="85dd5-112">相依組件並不需要重建，也不需要任何原始程式碼變更。</span><span class="sxs-lookup"><span data-stu-id="85dd5-112">Dependent assemblies are not required to be rebuilt, nor are any source code changes required.</span></span> <span data-ttu-id="85dd5-113">二進位相容變更也是來源相容變更。</span><span class="sxs-lookup"><span data-stu-id="85dd5-113">Binary compatible changes are also source compatible changes.</span></span>

## <a name="source-compatible-changes"></a><span data-ttu-id="85dd5-114">來源相容變更</span><span class="sxs-lookup"><span data-stu-id="85dd5-114">Source compatible changes</span></span>

<span data-ttu-id="85dd5-115">如果使用您程式庫的應用程式和程式庫不需要變更原始程式碼，但來源必須根據新版本重新編譯，才能正常運作，則您程式庫上的這些變更屬於**來源相容**。</span><span class="sxs-lookup"><span data-stu-id="85dd5-115">Changes to your library are **source compatible** when applications and libraries that use your library do not require source code changes, but the source must be recompiled against the new version to work correctly.</span></span>

## <a name="incompatible-changes"></a><span data-ttu-id="85dd5-116">不相容變更</span><span class="sxs-lookup"><span data-stu-id="85dd5-116">Incompatible changes</span></span>

<span data-ttu-id="85dd5-117">如果變更既不是**來源相容**也不是**二進位相容**，則相依程式庫和應用程式需要變更原始程式碼與重新編譯。</span><span class="sxs-lookup"><span data-stu-id="85dd5-117">If a change is neither **source compatible** nor **binary compatible**, source code changes along with recompilation are required in dependent libraries and applications.</span></span>

## <a name="evaluate-your-library"></a><span data-ttu-id="85dd5-118">評估您的程式庫</span><span class="sxs-lookup"><span data-stu-id="85dd5-118">Evaluate your library</span></span>

<span data-ttu-id="85dd5-119">這些相容性概念會影響您程式庫中的公用和受保護宣告，但不會影響其內部實作。</span><span class="sxs-lookup"><span data-stu-id="85dd5-119">These compatibility concepts affect the public and protected declarations for your library, not its internal implementation.</span></span> <span data-ttu-id="85dd5-120">在內部採用任何新的功能都是**二進位相容**。</span><span class="sxs-lookup"><span data-stu-id="85dd5-120">Adopting any new features internally are always **binary compatible**.</span></span>  

<span data-ttu-id="85dd5-121">**二進位相容**變更會提供新語法，該語法會針對公用宣告產生與舊語法相同的編譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="85dd5-121">**Binary compatible** changes provide new syntax that generates the same compiled code for public declarations as the older syntax.</span></span> <span data-ttu-id="85dd5-122">例如，將方法變更為運算式主體成員是**二進位相容**變更：</span><span class="sxs-lookup"><span data-stu-id="85dd5-122">For example, changing a method to an expression-bodied member is a **binary compatible** change:</span></span>

<span data-ttu-id="85dd5-123">原始程式碼：</span><span class="sxs-lookup"><span data-stu-id="85dd5-123">Original code:</span></span>

```csharp
public double CalculateSquare(double value)
{
    return value * value;
}
```

<span data-ttu-id="85dd5-124">新程式碼：</span><span class="sxs-lookup"><span data-stu-id="85dd5-124">New code:</span></span>

```csharp
public double CalculateSquare(double value) => value * value;
```

<span data-ttu-id="85dd5-125">**來源相容**變更會引進語法，該語法會變更公用成員的已編譯程式碼，但是會使用與現有呼叫網站相容的方式。</span><span class="sxs-lookup"><span data-stu-id="85dd5-125">**Source compatible** changes introduce syntax that changes the compiled code for a public member, but in a way that is compatible with existing call sites.</span></span> <span data-ttu-id="85dd5-126">例如，將方法簽章從「依值 (by value)」參數變更為 `in`「依參考 (by reference)」參數是來源相容，而不是二進位相容：</span><span class="sxs-lookup"><span data-stu-id="85dd5-126">For example, changing a method signature from a by value parameter to an `in` by reference parameter is source compatible, but not binary compatible:</span></span>

<span data-ttu-id="85dd5-127">原始程式碼：</span><span class="sxs-lookup"><span data-stu-id="85dd5-127">Original code:</span></span>

```csharp
public double CalculateSquare(double value) => value * value;
```

<span data-ttu-id="85dd5-128">新程式碼：</span><span class="sxs-lookup"><span data-stu-id="85dd5-128">New code:</span></span>

```csharp
public double CalculateSquare(in double value) => value * value;
```

<span data-ttu-id="85dd5-129">[最新功能](index.md)文章中會註明影響公用宣告的引進功能是來源相容或二進位相容。</span><span class="sxs-lookup"><span data-stu-id="85dd5-129">The [What's new](index.md) articles note if introducing a feature that affects public declarations is source compatible or binary compatible.</span></span>
