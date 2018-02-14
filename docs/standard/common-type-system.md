---
title: "一般類型系統和 Common Language Specification"
description: "了解一般型別系統 (CTS) 和 Common Language Specification (CLS) 如何讓 .NET 能夠支援多種語言。"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 3b1f5725-ac94-4f17-8e5f-244442438a4d
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d7626b0a6a902465416187b2c09d624dfe9a9773
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="common-type-system--common-language-specification"></a><span data-ttu-id="872e9-104">一般類型系統和 Common Language Specification</span><span class="sxs-lookup"><span data-stu-id="872e9-104">Common Type System & Common Language Specification</span></span>

<span data-ttu-id="872e9-105">同樣地，這是在 .NET 世界內自由使用的兩個詞彙，它們實際上對了解 .NET 實作如何啟用多語言開發和其運作方式十分重要。</span><span class="sxs-lookup"><span data-stu-id="872e9-105">Again, two terms that are freely used in the .NET world, they actually are crucial to understand how a .NET implementation enables multi-language development and to understand how it works.</span></span>

## <a name="common-type-system"></a><span data-ttu-id="872e9-106">一般類型系統</span><span class="sxs-lookup"><span data-stu-id="872e9-106">Common Type System</span></span>

<span data-ttu-id="872e9-107">若要從頭開始，請記住，.NET 實作「無從驗證語言」。</span><span class="sxs-lookup"><span data-stu-id="872e9-107">To start from the beginning, remember that a .NET implementation is _language agnostic_.</span></span> <span data-ttu-id="872e9-108">這不只是表示程式設計人員可以使用任何可編譯為 IL 的語言來撰寫自己的程式碼。</span><span class="sxs-lookup"><span data-stu-id="872e9-108">This doesn’t just mean that a programmer can write her code in any language that can be compiled to IL.</span></span> <span data-ttu-id="872e9-109">也表示其必須能夠與使用其他語言所撰寫的程式碼互動，而這些語言可以在 .NET 實作上使用。</span><span class="sxs-lookup"><span data-stu-id="872e9-109">It also means that she needs to be able to interact with code written in other languages that are able to be used on a .NET implementation.</span></span>

<span data-ttu-id="872e9-110">若要透明地執行這項操作，必須要有通用的方式來描述所有支援的類型。</span><span class="sxs-lookup"><span data-stu-id="872e9-110">In order to do this transparently, there has to be a common way to describe all supported types.</span></span> <span data-ttu-id="872e9-111">這是一般類型系統 (CTS) 負責執行的作業。</span><span class="sxs-lookup"><span data-stu-id="872e9-111">This is what the Common Type System (CTS) is in charge of doing.</span></span> <span data-ttu-id="872e9-112">它是用來執行下列事項︰</span><span class="sxs-lookup"><span data-stu-id="872e9-112">It was made to do several things:</span></span>

*   <span data-ttu-id="872e9-113">建立跨語言執行的架構。</span><span class="sxs-lookup"><span data-stu-id="872e9-113">Establish a framework for cross-language execution.</span></span>
*   <span data-ttu-id="872e9-114">提供物件導向模型，以支援在 .NET 實作上實作各種語言。</span><span class="sxs-lookup"><span data-stu-id="872e9-114">Provide an object-oriented model to support implementing various languages on a .NET implementation.</span></span>
*   <span data-ttu-id="872e9-115">定義所有語言在需要處理類型時必須遵循的一組規則。</span><span class="sxs-lookup"><span data-stu-id="872e9-115">Define a set of rules that all languages must follow when it comes to working with types.</span></span>
*   <span data-ttu-id="872e9-116">提供包含基礎基本型別 (例如 `Boolean`、`Byte`、`Char` 等) 的程式庫，以便用於應用程式開發。</span><span class="sxs-lookup"><span data-stu-id="872e9-116">Provide a library that contains the basic primitive types that are used in application development (such as, `Boolean`, `Byte`, `Char` etc.)</span></span>

<span data-ttu-id="872e9-117">CTS 定義應該支援的兩種主要類型︰參考和實值類型。</span><span class="sxs-lookup"><span data-stu-id="872e9-117">CTS defines two main kinds of types that should be supported: reference and value types.</span></span> <span data-ttu-id="872e9-118">它們的名稱會指向其定義。</span><span class="sxs-lookup"><span data-stu-id="872e9-118">Their names point to their definitions.</span></span>

<span data-ttu-id="872e9-119">參考類型的物件是由物件實際值的參考來表示；這裡的參考類似 C/C++ 中的指標。</span><span class="sxs-lookup"><span data-stu-id="872e9-119">Reference types’ objects are represented by a reference to the object’s actual value; a reference here is similar to a pointer in C/C++.</span></span> <span data-ttu-id="872e9-120">它指的就是物件值所在的記憶體位置。</span><span class="sxs-lookup"><span data-stu-id="872e9-120">It simply refers to a memory location where the objects’ values are.</span></span> <span data-ttu-id="872e9-121">這對這些類型的使用方式具有深遠影響。</span><span class="sxs-lookup"><span data-stu-id="872e9-121">This has a profound impact on how these types are used.</span></span> <span data-ttu-id="872e9-122">如果您將參考類型指派給變數，然後將該變數傳遞給方法，例如，物件的任何變更都會反映在主要物件中；未進行複製。</span><span class="sxs-lookup"><span data-stu-id="872e9-122">If you assign a reference type to a variable and then pass that variable into a method, for instance, any changes to the object will be reflected on the main object; there is no copying.</span></span>

<span data-ttu-id="872e9-123">如果物件是由物件的值來表示，則實值類型就是相反值。</span><span class="sxs-lookup"><span data-stu-id="872e9-123">Value types are the opposite, where the objects are represented by their values.</span></span> <span data-ttu-id="872e9-124">如果您將實值類型指派給變數，則基本上會複製物件的值。</span><span class="sxs-lookup"><span data-stu-id="872e9-124">If you assign a value type to a variable, you are essentially copying a value of the object.</span></span>

<span data-ttu-id="872e9-125">CTS 定義數種分類的類型，各有其特定語意和用法︰</span><span class="sxs-lookup"><span data-stu-id="872e9-125">CTS defines several categories of types, each with their specific semantics and usage:</span></span>

*   <span data-ttu-id="872e9-126">類別</span><span class="sxs-lookup"><span data-stu-id="872e9-126">Classes</span></span>
*   <span data-ttu-id="872e9-127">結構</span><span class="sxs-lookup"><span data-stu-id="872e9-127">Structures</span></span>
*   <span data-ttu-id="872e9-128">列舉</span><span class="sxs-lookup"><span data-stu-id="872e9-128">Enums</span></span>
*   <span data-ttu-id="872e9-129">介面</span><span class="sxs-lookup"><span data-stu-id="872e9-129">Interfaces</span></span>
*   <span data-ttu-id="872e9-130">委派</span><span class="sxs-lookup"><span data-stu-id="872e9-130">Delegates</span></span>

<span data-ttu-id="872e9-131">CTS 也會定義類型的所有其他屬性 (例如存取修飾詞)、什麼是有效類型成員、繼承和多載的運作方式等。</span><span class="sxs-lookup"><span data-stu-id="872e9-131">CTS also defines all other properties of the types, such as access modifiers, what are valid type members, how inheritance and overloading works and so on.</span></span> <span data-ttu-id="872e9-132">不幸的是，深入探討其中任何項目不在簡介文章的範圍 (例如這項)，但您可以查閱涵蓋這些主題之更深入內容連結結尾的[更多資源](#more-resources)一節。</span><span class="sxs-lookup"><span data-stu-id="872e9-132">Unfortunately, going deep into any of those is beyond the scope of an introductory article such as this, but you can consult [More resources](#more-resources) section at the end for links to more in-depth content that covers these topics.</span></span>

## <a name="common-language-specification"></a><span data-ttu-id="872e9-133">Common Language Specification</span><span class="sxs-lookup"><span data-stu-id="872e9-133">Common Language Specification</span></span>

<span data-ttu-id="872e9-134">若要啟用完整互通性案例，則透過程式碼建立的所有物件都必須依賴使用它們之語言的一些共通性 (即其_呼叫端_)。</span><span class="sxs-lookup"><span data-stu-id="872e9-134">To enable full interoperability scenarios, all objects that are created in code must rely on some commonality in the languages that are consuming them (are their _callers_).</span></span> <span data-ttu-id="872e9-135">因為有多種不同的語言，所以 .NET 已透過 **Common Language Specification** (CLS) 指定這些共通性。</span><span class="sxs-lookup"><span data-stu-id="872e9-135">Since there are numerous different languages, .NET has specified those commonalities in something called the **Common Language Specification** (CLS).</span></span> <span data-ttu-id="872e9-136">CLS 定義許多常見應用程式所需的一組功能。</span><span class="sxs-lookup"><span data-stu-id="872e9-136">CLS defines a set of features that are needed by many common applications.</span></span> <span data-ttu-id="872e9-137">它也提供一種方法，以在需要支援的 .NET 上實作任何語言。</span><span class="sxs-lookup"><span data-stu-id="872e9-137">It also provides a sort of recipe for any language that is implemented on top of .NET on what it needs to support.</span></span>

<span data-ttu-id="872e9-138">CLS 是 CTS 的子集。</span><span class="sxs-lookup"><span data-stu-id="872e9-138">CLS is a subset of the CTS.</span></span> <span data-ttu-id="872e9-139">除非 CLS 規則更嚴格，否則這表示 CTS 中的所有規則也適用於 CLS。</span><span class="sxs-lookup"><span data-stu-id="872e9-139">This means that all of the rules in the CTS also apply to the CLS, unless the CLS rules are more strict.</span></span> <span data-ttu-id="872e9-140">如果元件只是使用 CLS 中的規則所建置 (亦即，它只會在其 API 中公開 CLS 功能)，表示**符合 CLS 標準**。</span><span class="sxs-lookup"><span data-stu-id="872e9-140">If a component is built using only the rules in the CLS, that is, it exposes only the CLS features in its API, it is said to be **CLS-compliant**.</span></span> <span data-ttu-id="872e9-141">例如，`<framework-librares>` 完全符合 CLS 標準，原因是它們需要作用於 .NET 上支援的所有語言。</span><span class="sxs-lookup"><span data-stu-id="872e9-141">For instance, the `<framework-librares>` are CLS-compliant precisely because they need to work across all of the languages that are supported on .NET.</span></span>

<span data-ttu-id="872e9-142">您可以查閱下面[更多資源](#more-resources)一節中的文件，以取得 CLS 中所有功能的概觀。</span><span class="sxs-lookup"><span data-stu-id="872e9-142">You can consult the documents in the [More Resources](#more-resources) section below to get an overview of all the features in the CLS.</span></span>

## <a name="more-resources"></a><span data-ttu-id="872e9-143">更多資源</span><span class="sxs-lookup"><span data-stu-id="872e9-143">More resources</span></span>

*   [<span data-ttu-id="872e9-144">一般類型系統</span><span class="sxs-lookup"><span data-stu-id="872e9-144">Common Type System</span></span>](./base-types/common-type-system.md)
*   [<span data-ttu-id="872e9-145">Common Language Specification</span><span class="sxs-lookup"><span data-stu-id="872e9-145">Common Language Specification</span></span>](language-independence-and-language-independent-components.md)
