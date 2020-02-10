---
title: 中斷性變更類別
description: 了解 .NET Core 如何分類中斷性變更。
ms.date: 06/10/2019
ms.openlocfilehash: b273ebbb82da803cde66ea34760aa1779c6c1ca5
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093041"
---
# <a name="breaking-change-categories"></a><span data-ttu-id="c6280-103">中斷性變更類別</span><span class="sxs-lookup"><span data-stu-id="c6280-103">Breaking change categories</span></span>

<span data-ttu-id="c6280-104">*相容性*是指在實作之 .NET 版本上編譯或執行程式碼的能力，而該版本與原先開發程式碼時所使用的 .NET 版本不同。</span><span class="sxs-lookup"><span data-stu-id="c6280-104">*Compatibility* refers to the ability to compile or execute code on a version of a .NET implementation other than the one with which the code was originally developed.</span></span> <span data-ttu-id="c6280-105">特定變更可能會造成六種不同的相容性影響。</span><span class="sxs-lookup"><span data-stu-id="c6280-105">A particular change can affect compatibility in six different ways.</span></span> <span data-ttu-id="c6280-106">評估相容性時所考慮的[個別變更種類](index.md)分為下列類別：</span><span class="sxs-lookup"><span data-stu-id="c6280-106">The [individual kinds of changes](index.md) that are considered when evaluating compatibility fall into the following categories:</span></span>

- [<span data-ttu-id="c6280-107">行為變更</span><span class="sxs-lookup"><span data-stu-id="c6280-107">behavioral change</span></span>](#behavioral-change)
- [<span data-ttu-id="c6280-108">二進位相容性</span><span class="sxs-lookup"><span data-stu-id="c6280-108">binary compatibility</span></span>](#binary-compatibility)
- [<span data-ttu-id="c6280-109">來源相容性</span><span class="sxs-lookup"><span data-stu-id="c6280-109">source compatibility</span></span>](#source-compatibility)
- [<span data-ttu-id="c6280-110">設計階段相容性</span><span class="sxs-lookup"><span data-stu-id="c6280-110">design-time compatibility</span></span>](#design-time-compatibility)
- [<span data-ttu-id="c6280-111">回溯相容性</span><span class="sxs-lookup"><span data-stu-id="c6280-111">backwards compatibility</span></span>](#backwards-compatibility)
- <span data-ttu-id="c6280-112">[向前相容性](#forward-compatibility)（不是 .net Core 的目標）</span><span class="sxs-lookup"><span data-stu-id="c6280-112">[forward compatibility](#forward-compatibility) (not a goal of .NET Core)</span></span>

## <a name="behavioral-change"></a><span data-ttu-id="c6280-113">行為變更</span><span class="sxs-lookup"><span data-stu-id="c6280-113">Behavioral change</span></span>

<span data-ttu-id="c6280-114">行為變更表示變更了成員的行為。</span><span class="sxs-lookup"><span data-stu-id="c6280-114">A behavioral change represents a change to the behavior of a member.</span></span> <span data-ttu-id="c6280-115">這類變更可能會外顯 (例如方法可能會擲回不同的例外狀況)，也可能表示實作變更 (例如變更了傳回值的計算方式、新增或移除了內部方法呼叫，甚至是巨幅地改進了效能)。</span><span class="sxs-lookup"><span data-stu-id="c6280-115">The change may be externally visible (for example, a method may throw a different exception), or it may represent a changed implementation (for example, a change in the way a return value is calculated, the addition or removal of internal method calls, or even a significant performance improvement).</span></span>

<span data-ttu-id="c6280-116">當行為變更外顯，並修改了類型的公開合約之後，因為會影響二進位相容性，所以評估這類變更相當容易。</span><span class="sxs-lookup"><span data-stu-id="c6280-116">When behavioral changes are externally visible and modify a type's public contract, they are easy to evaluate since they affect binary compatibility.</span></span> <span data-ttu-id="c6280-117">實作變更在評估上則更為困難；而根據變更的性質及 API 的使用頻率與模式，變更所造成的影響可能從嚴重到無害不等。</span><span class="sxs-lookup"><span data-stu-id="c6280-117">Implementation changes are much more difficult to evaluate; depending on the nature of the change and the frequency and patterns of use of the API, the impact of a change can range from severe to innocuous.</span></span>

## <a name="binary-compatibility"></a><span data-ttu-id="c6280-118">二進位相容性</span><span class="sxs-lookup"><span data-stu-id="c6280-118">Binary compatibility</span></span>

<span data-ttu-id="c6280-119">二進位相容性是指 API 消費者無須重新編譯，就能在新版上使用 API 的能力。</span><span class="sxs-lookup"><span data-stu-id="c6280-119">Binary compatibility refers to the ability of a consumer of an API to use the API on a newer version without recompilation.</span></span> <span data-ttu-id="c6280-120">諸如新增方法，或為類型新增介面實作一類的變更，都不會影響二進位相容性。</span><span class="sxs-lookup"><span data-stu-id="c6280-120">Such changes as adding methods or adding a new interface implementation to a type do not affect binary compatibility.</span></span> <span data-ttu-id="c6280-121">但若是移除或改變組件的公開特徵標記，致使消費者無法再存取組件公開的同一個介面，就會影響二進位相容性。</span><span class="sxs-lookup"><span data-stu-id="c6280-121">However, removing or altering an assembly's public signatures so that consumers can no longer access the same interface exposed by the assembly does affect binary compatibility.</span></span> <span data-ttu-id="c6280-122">這類變更稱為*二進位不相容變更*。</span><span class="sxs-lookup"><span data-stu-id="c6280-122">A change of this kind is termed a *binary incompatible change*.</span></span>

## <a name="source-compatibility"></a><span data-ttu-id="c6280-123">來源相容性</span><span class="sxs-lookup"><span data-stu-id="c6280-123">Source compatibility</span></span>

<span data-ttu-id="c6280-124">來源相容性是指現有 API 消費者無須變更原始程式碼，就能透過新版進行重新編譯的能力。</span><span class="sxs-lookup"><span data-stu-id="c6280-124">Source compatibility refers to the ability of existing consumers of an API to recompile against a newer version without any source changes.</span></span> <span data-ttu-id="c6280-125">當消費者必須修原始程式碼，程式碼才能成功透過新版 API 進行建置時，就會發生*來源不相容變更*。</span><span class="sxs-lookup"><span data-stu-id="c6280-125">A *source incompatible change* occurs when a consumer needs to modify source code for it to build successfully against a newer version of an API.</span></span>

## <a name="design-time-compatibility"></a><span data-ttu-id="c6280-126">設計階段相容性</span><span class="sxs-lookup"><span data-stu-id="c6280-126">Design-time compatibility</span></span>

<span data-ttu-id="c6280-127">設計階段相容性是指保留在不同版本 Visual Studio 及其他設計階段環境上之設計階段體驗的能力。</span><span class="sxs-lookup"><span data-stu-id="c6280-127">Design-time compatibility refers to preserving the design-time experience across versions of Visual Studio and other design-time environments.</span></span> <span data-ttu-id="c6280-128">雖然這有可能會涉及設計工具的行為或 UI，但最攸關設計階段相容性的層面，則是專案相容性。</span><span class="sxs-lookup"><span data-stu-id="c6280-128">While this can involve the behavior or the UI of designers, the most important aspect of design-time compatibility concerns project compatibility.</span></span> <span data-ttu-id="c6280-129">專案或解決方案必須能夠在新版的設計階段環境上開啟及使用。</span><span class="sxs-lookup"><span data-stu-id="c6280-129">A project or solution must be able to be opened and used on a newer version of the design-time environment.</span></span>

## <a name="backwards-compatibility"></a><span data-ttu-id="c6280-130">回溯相容性</span><span class="sxs-lookup"><span data-stu-id="c6280-130">Backwards compatibility</span></span>

<span data-ttu-id="c6280-131">回溯相容性是指現有 API 消費者對新版執行時，仍能保有相同行為的能力。</span><span class="sxs-lookup"><span data-stu-id="c6280-131">Backwards compatibility refers to the ability of an existing consumer of an API to run against a new version while behaving in the same way.</span></span> <span data-ttu-id="c6280-132">行為變更與二進位相容性變更都會影響回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="c6280-132">Both behavioral changes and changes in binary compatibility affect backwards compatibility.</span></span> <span data-ttu-id="c6280-133">若消費者無法對新版執行，或對新版執行時，無法保有相同的行為，此 API 便是*回溯不相容*。</span><span class="sxs-lookup"><span data-stu-id="c6280-133">If a consumer is not able to run or behaves differently when running against the newer version of the API, the API is *backwards incompatible*.</span></span>

<span data-ttu-id="c6280-134">不鼓勵影響回溯相容性的變更，因為開發人員希望在較新版本的 API 中提供回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="c6280-134">Changes that affect backwards compatibility are discouraged, since developers expect backwards compatibility in newer versions of an API.</span></span>

## <a name="forward-compatibility"></a><span data-ttu-id="c6280-135">往後相容性</span><span class="sxs-lookup"><span data-stu-id="c6280-135">Forward compatibility</span></span>

<span data-ttu-id="c6280-136">往後相容性是指現有 API 消費者對舊版執行時，仍能保有相同行為的能力。</span><span class="sxs-lookup"><span data-stu-id="c6280-136">Forward compatibility refers to the ability of an existing consumer of an API to run against an older version while exhibiting the same behavior.</span></span> <span data-ttu-id="c6280-137">若消費者無法對舊版執行，或對舊版執行時，無法保有相同的行為，此 API 便是*往後不相容*。</span><span class="sxs-lookup"><span data-stu-id="c6280-137">If a consumer is not able to run or behaves differently when run against an older version of the API, the API is *forward incompatible*.</span></span>

<span data-ttu-id="c6280-138">實際上，維護往後相容性可防止版本更迭時變更或新增，因為這些變更會造成使用新版的消費者無法在舊版中執行。</span><span class="sxs-lookup"><span data-stu-id="c6280-138">Maintaining forward compatibility virtually precludes any changes or additions from version to version, since those changes prevent a consumer that targets a later version from running under an earlier version.</span></span> <span data-ttu-id="c6280-139">開發人員會預期使用新版 API 的消費者，在對舊版 API 執行時無法正常運作。</span><span class="sxs-lookup"><span data-stu-id="c6280-139">Developers expect that a consumer that relies on a newer API may not function correctly against the older API.</span></span>

<span data-ttu-id="c6280-140">.NET Core 不會維護往後相容性。</span><span class="sxs-lookup"><span data-stu-id="c6280-140">Maintaining forward compatibility is not a goal of .NET Core.</span></span>

## <a name="see-also"></a><span data-ttu-id="c6280-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6280-141">See also</span></span>

- [<span data-ttu-id="c6280-142">評估 .NET Core 中的中斷性變更</span><span class="sxs-lookup"><span data-stu-id="c6280-142">Evaluate breaking changes in .NET Core</span></span>](index.md)
