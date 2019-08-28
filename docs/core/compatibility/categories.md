---
title: 中斷性變更類別 - .NET Core
description: 了解 .NET Core 如何分類中斷性變更。
author: rpetrusha
ms.author: ronpet
ms.date: 06/10/2019
ms.openlocfilehash: 68cd3580e80305e54b41610f05d939a6aff8b54d
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/21/2019
ms.locfileid: "69577150"
---
# <a name="breaking-change-categories"></a><span data-ttu-id="b64b2-103">中斷性變更類別</span><span class="sxs-lookup"><span data-stu-id="b64b2-103">Breaking change categories</span></span>

<span data-ttu-id="b64b2-104">*相容性*是指在實作之 .NET 版本上編譯或執行程式碼的能力，而該版本與原先開發程式碼時所使用的 .NET 版本不同。</span><span class="sxs-lookup"><span data-stu-id="b64b2-104">*Compatibility* refers to the ability to compile or execute code on a version of a .NET implementation other than the one with which the code was originally developed.</span></span> <span data-ttu-id="b64b2-105">特定變更可能會造成六種不同的相容性影響。</span><span class="sxs-lookup"><span data-stu-id="b64b2-105">A particular change can affect compatibility in six different ways.</span></span> <span data-ttu-id="b64b2-106">在[評估相容性時考慮的個別變更種類](index.md)屬於前五類。</span><span class="sxs-lookup"><span data-stu-id="b64b2-106">The [individual kinds of changes that are considered when evaluating compatibility](index.md) fall into the first five categories.</span></span> 

## <a name="behavioral-change"></a><span data-ttu-id="b64b2-107">行為變更</span><span class="sxs-lookup"><span data-stu-id="b64b2-107">Behavioral change</span></span>

<span data-ttu-id="b64b2-108">行為變更表示變更了成員的行為。</span><span class="sxs-lookup"><span data-stu-id="b64b2-108">A behavioral change represents a change to the behavior of a member.</span></span> <span data-ttu-id="b64b2-109">這類變更可能會外顯 (例如方法可能會擲回不同的例外狀況)，也可能表示實作變更 (例如變更了傳回值的計算方式、新增或移除了內部方法呼叫，甚至是巨幅地改進了效能)。</span><span class="sxs-lookup"><span data-stu-id="b64b2-109">The change may be externally visible (for example, a method may throw a different exception), or it may represent a changed implementation (for example, a change in the way a return value is calculated, the addition or removal of internal method calls, or even a significant performance improvement).</span></span>

<span data-ttu-id="b64b2-110">當行為變更外顯，並修改了類型的公開合約之後，因為會影響二進位相容性，所以評估這類變更相當容易。</span><span class="sxs-lookup"><span data-stu-id="b64b2-110">When behavioral changes are externally visible and modify a type's public contract, they are easy to evaluate since they affect binary compatibility.</span></span> <span data-ttu-id="b64b2-111">實作變更在評估上則更為困難；而根據變更的性質及 API 的使用頻率與模式，變更所造成的影響可能從嚴重到無害不等。</span><span class="sxs-lookup"><span data-stu-id="b64b2-111">Implementation changes are much more difficult to evaluate; depending on the nature of the change and the frequency and patterns of use of the API, the impact of a change can range from severe to innocuous.</span></span>  

## <a name="binary-compatibility"></a><span data-ttu-id="b64b2-112">二進位相容性</span><span class="sxs-lookup"><span data-stu-id="b64b2-112">Binary compatibility</span></span>

<span data-ttu-id="b64b2-113">二進位相容性是指 API 消費者無須重新編譯，就能在新版上使用 API 的能力。</span><span class="sxs-lookup"><span data-stu-id="b64b2-113">Binary compatibility refers to the ability of a consumer of an API to use the API on a newer version without recompilation.</span></span> <span data-ttu-id="b64b2-114">諸如新增方法，或為類型新增介面實作一類的變更，都不會影響二進位相容性。</span><span class="sxs-lookup"><span data-stu-id="b64b2-114">Such changes as adding methods or adding a new interface implementation to a type do not affect binary compatibility.</span></span> <span data-ttu-id="b64b2-115">但若是移除或改變組件的公開特徵標記，致使消費者無法再存取組件公開的同一個介面，就會影響二進位相容性。</span><span class="sxs-lookup"><span data-stu-id="b64b2-115">However, removing or altering an assembly's public signatures so that consumers can no longer access the same interface exposed by the assembly does affect binary compatibility.</span></span> <span data-ttu-id="b64b2-116">這類變更稱為*二進位不相容變更*。</span><span class="sxs-lookup"><span data-stu-id="b64b2-116">A change of this kind is termed a *binary incompatible change*.</span></span>

## <a name="source-compatibility"></a><span data-ttu-id="b64b2-117">來源相容性</span><span class="sxs-lookup"><span data-stu-id="b64b2-117">Source compatibility</span></span>

 <span data-ttu-id="b64b2-118">來源相容性是指現有 API 消費者無須變更原始程式碼，就能透過新版進行重新編譯的能力。</span><span class="sxs-lookup"><span data-stu-id="b64b2-118">Source compatibility refers to the ability of existing consumers of an API to recompile against a newer version without any source changes.</span></span> <span data-ttu-id="b64b2-119">當消費者必須修原始程式碼，程式碼才能成功透過新版 API 進行建置時，就會發生*來源不相容變更*。</span><span class="sxs-lookup"><span data-stu-id="b64b2-119">A *source incompatible change* occurs when a consumer needs to modify source code for it to build successfully against a newer version of an API.</span></span>

## <a name="design-time-compatibility"></a><span data-ttu-id="b64b2-120">設計階段相容性</span><span class="sxs-lookup"><span data-stu-id="b64b2-120">Design-time compatibility</span></span>

<span data-ttu-id="b64b2-121">設計階段相容性是指保留在不同版本 Visual Studio 及其他設計階段環境上之設計階段體驗的能力。</span><span class="sxs-lookup"><span data-stu-id="b64b2-121">Design-time compatibility refers to preserving the design-time experience across versions of Visual Studio and other design-time environments.</span></span> <span data-ttu-id="b64b2-122">雖然這有可能會涉及設計工具的行為或 UI，但最攸關設計階段相容性的層面，則是專案相容性。</span><span class="sxs-lookup"><span data-stu-id="b64b2-122">While this can involve the behavior or the UI of designers, the most important aspect of design-time compatibility concerns project compatibility.</span></span> <span data-ttu-id="b64b2-123">專案或解決方案必須能夠在新版的設計階段環境上開啟及使用。</span><span class="sxs-lookup"><span data-stu-id="b64b2-123">A project or solution must be able to be opened and used on a newer version of the design-time environment.</span></span>

## <a name="backwards-compatibility"></a><span data-ttu-id="b64b2-124">回溯相容性</span><span class="sxs-lookup"><span data-stu-id="b64b2-124">Backwards compatibility</span></span>

<span data-ttu-id="b64b2-125">回溯相容性是指現有 API 消費者對新版執行時，仍能保有相同行為的能力。</span><span class="sxs-lookup"><span data-stu-id="b64b2-125">Backwards compatibility refers to the ability of an existing consumer of an API to run against a new version while behaving in the same way.</span></span> <span data-ttu-id="b64b2-126">行為變更與二進位相容性變更都會影響回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="b64b2-126">Both behavioral changes and changes in binary compatibility affect backwards compatibility.</span></span> <span data-ttu-id="b64b2-127">若消費者無法對新版執行，或對新版執行時，無法保有相同的行為，此 API 便是*回溯不相容*。</span><span class="sxs-lookup"><span data-stu-id="b64b2-127">If a consumer is not able to run or behaves differently when running against the newer version of the API, the API is *backwards incompatible*.</span></span>

<span data-ttu-id="b64b2-128">強烈建議不要進行會對回溯相容性造成影響的變更，因為開發人員一般預期新版 API 具備回溯相容性的能力。</span><span class="sxs-lookup"><span data-stu-id="b64b2-128">Changes that affect backwards compatibility are strongly discouraged since developers by default expect backwards compatibility in newer versions of an API.</span></span>

## <a name="forward-compatibility"></a><span data-ttu-id="b64b2-129">往後相容性</span><span class="sxs-lookup"><span data-stu-id="b64b2-129">Forward compatibility</span></span>

<span data-ttu-id="b64b2-130">往後相容性是指現有 API 消費者對舊版執行時，仍能保有相同行為的能力。</span><span class="sxs-lookup"><span data-stu-id="b64b2-130">Forward compatibility refers to the ability of an existing consumer of an API to run against an older version while exhibiting the same behavior.</span></span> <span data-ttu-id="b64b2-131">若消費者無法對舊版執行，或對舊版執行時，無法保有相同的行為，此 API 便是*往後不相容*。</span><span class="sxs-lookup"><span data-stu-id="b64b2-131">If a consumer is not able to run or behaves differently when run against an older version of the API, the API is *forward incompatible*.</span></span> 

<span data-ttu-id="b64b2-132">實際上，維護往後相容性可防止版本更迭時變更或新增，因為這些變更會造成使用新版的消費者無法在舊版中執行。</span><span class="sxs-lookup"><span data-stu-id="b64b2-132">Maintaining forward compatibility virtually precludes any changes or additions from version to version, since those changes prevent a consumer that targets a later version from running under an earlier version.</span></span> <span data-ttu-id="b64b2-133">開發人員會預期使用新版 API 的消費者，在對舊版 API 執行時無法正常運作。</span><span class="sxs-lookup"><span data-stu-id="b64b2-133">Developers expect that a consumer that relies on a newer API may not function correctly against the older API.</span></span> 

<span data-ttu-id="b64b2-134">.NET Core 不會維護往後相容性。</span><span class="sxs-lookup"><span data-stu-id="b64b2-134">Maintaining forward compatibility is not a goal of .NET Core.</span></span>

## <a name="see-also"></a><span data-ttu-id="b64b2-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b64b2-135">See also</span></span>

[<span data-ttu-id="b64b2-136">評估 .NET Core 中的中斷性變更</span><span class="sxs-lookup"><span data-stu-id="b64b2-136">Evaluate breaking changes in .NET Core</span></span>](index.md)
