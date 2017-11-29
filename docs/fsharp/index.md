---
title: "F# 指南"
description: "深入了解 F # 程式語言，提供函式程式設計中的第一級支援的.NET 開放原始碼語言。"
keywords: .NET, .NET Core
author: jackfoxy
ms.author: phcart
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: ea27fb37-dad1-4bd4-a3cc-4f5c70767ae9
ms.openlocfilehash: 4ddd77cef6cf70a63f1af81359d82eda27a01593
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="f-guide"></a><span data-ttu-id="c3444-104">F# 指南</span><span class="sxs-lookup"><span data-stu-id="c3444-104">F# Guide</span></span>

<span data-ttu-id="c3444-105">F# 是一種適用於 .NET 的跨平台、開放原始碼程式設計語言，可提供一流的函式程式設計支援，同時支援物件導向和命令式程式設計。</span><span class="sxs-lookup"><span data-stu-id="c3444-105">F# is a cross-platform, open source programming language for .NET which provides first-class support for functional programming, along with support of object-oriented and imperative programming.</span></span>  <span data-ttu-id="c3444-106">Visual F# 編譯器和工具是 Microsoft 對 F# 程式設計語言的實作和工具，可讓 F# 成為 .NET 的一流成員。</span><span class="sxs-lookup"><span data-stu-id="c3444-106">The Visual F# compiler and tooling are Microsoft's implementation and tooling for the F# programming language, making F# a first-class member of .NET.</span></span>

## <a name="if-youre-new-to-f"></a><span data-ttu-id="c3444-107">如果您剛接觸到 F #</span><span class="sxs-lookup"><span data-stu-id="c3444-107">If You're New to F#</span></span> #

<span data-ttu-id="c3444-108">如果您剛接觸到 F #，以開始[教學課程的 F #](tour.md)來取得語言的概觀。</span><span class="sxs-lookup"><span data-stu-id="c3444-108">If you're new to F#, begin with the [Tour of F#](tour.md) to get an overview of the language.</span></span>

<span data-ttu-id="c3444-109">也建議您瀏覽[函式做為第一級值](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Progamming](introduction-to-functional-programming/index.md)-->若要了解使用 F # 而言是功能性程式設計概念。</span><span class="sxs-lookup"><span data-stu-id="c3444-109">It's also recommended that you go through the [Functions as First-Class Values](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Progamming](introduction-to-functional-programming/index.md)--> to learn Functional Programming concepts which are essential to working with F#.</span></span>

<span data-ttu-id="c3444-110">[教學課程](tutorials/getting-started/index.md)還提供了各種技能等級和語言功能的逐步指南。</span><span class="sxs-lookup"><span data-stu-id="c3444-110">The [Tutorials](tutorials/getting-started/index.md) also have step-by-step guides for various skill levels and features of the language.</span></span>

## <a name="if-youre-experienced-with-f"></a><span data-ttu-id="c3444-111">如果您是熟悉 F #</span><span class="sxs-lookup"><span data-stu-id="c3444-111">If You're Experienced with F#</span></span> #

<span data-ttu-id="c3444-112">若您熟悉 F#，則可以在[語言參考](language-reference/index.md)中找到許多用法，此文件徹底介紹語言的各個方面，並補充了許多程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="c3444-112">If you know your way around F#, you'll find a lot of use in the [Language Reference](language-reference/index.md), which documents each aspect of the language thoroughly, supplemented by numerous code samples.</span></span>  <span data-ttu-id="c3444-113">您還可以在 [F# 核心程式庫參考](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference)中找到大量用法。</span><span class="sxs-lookup"><span data-stu-id="c3444-113">You'll also find a lot of use in the [F# Core Library Reference](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference).</span></span>  <span data-ttu-id="c3444-114">F # 核心程式庫參考最終將 MSDN 離開並進入這些目前文件。</span><span class="sxs-lookup"><span data-stu-id="c3444-114">The F# Core Library Reference will eventually move away from MSDN and into these current docs.</span></span>

## <a name="the-f-software-foundation"></a><span data-ttu-id="c3444-115">F# Software Foundation (F# 軟體基金會)</span><span class="sxs-lookup"><span data-stu-id="c3444-115">The F# Software Foundation</span></span>

<span data-ttu-id="c3444-116">雖然 Microsoft 是 F# 語言和 Visual F# 工具的主要開發人員，但 F# 也獲得 F# Software Foundation (FSSF) 這個獨立基金會支持。</span><span class="sxs-lookup"><span data-stu-id="c3444-116">Although Microsoft is the primary developer of the F# language and Visual F# Tooling, F# is also backed by an independent foundation, the F# Software Foundation (FSSF).</span></span>

<span data-ttu-id="c3444-117">F# Software Foundation 的使命是促進、保護和推展 F# 程式設計語言，並支援和促進 F# 程式設計人員國際社群的多元發展。</span><span class="sxs-lookup"><span data-stu-id="c3444-117">The mission of the F# Software Foundation is to promote, protect, and advance the F# programming language, and to support and facilitate the growth of a diverse and international community of F# programmers.</span></span>

<span data-ttu-id="c3444-118">若要進一步了解並參與，請參閱 [fsharp.org](http://fsharp.org)。</span><span class="sxs-lookup"><span data-stu-id="c3444-118">To learn more and get involved, check out [fsharp.org](http://fsharp.org).</span></span>

## <a name="documentation"></a><span data-ttu-id="c3444-119">文件</span><span class="sxs-lookup"><span data-stu-id="c3444-119">Documentation</span></span>

* [<span data-ttu-id="c3444-120">教學課程</span><span class="sxs-lookup"><span data-stu-id="c3444-120">Tutorials</span></span>](tutorials/getting-started/index.md)
* <span data-ttu-id="c3444-121">[當做第一級值的函式](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Programming](introduction-to-functional-programming/index.md)--></span><span class="sxs-lookup"><span data-stu-id="c3444-121">[Functions as First-Class Values](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Programming](introduction-to-functional-programming/index.md)--></span></span>
* [<span data-ttu-id="c3444-122">語言參考</span><span class="sxs-lookup"><span data-stu-id="c3444-122">Language Reference</span></span>](language-reference/index.md)
* [<span data-ttu-id="c3444-123">F# 核心程式庫參考</span><span class="sxs-lookup"><span data-stu-id="c3444-123">F# Core Library Reference</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference)

## <a name="online-reading-resources"></a><span data-ttu-id="c3444-124">線上閱讀資源</span><span class="sxs-lookup"><span data-stu-id="c3444-124">Online Reading Resources</span></span>

* <span data-ttu-id="c3444-125">[F# for Fun and Profit Gitbook](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/) (有趣且可獲益的 F# Gitbook)</span><span class="sxs-lookup"><span data-stu-id="c3444-125">[F# for Fun and Profit Gitbook](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/)</span></span> 
* <span data-ttu-id="c3444-126">[F# Programming Wikibook](https://en.wikibooks.org/wiki/F_Sharp_Programming) (F# 程式設計 Wikibook)</span><span class="sxs-lookup"><span data-stu-id="c3444-126">[F# Programming Wikibook](https://en.wikibooks.org/wiki/F_Sharp_Programming)</span></span>

## <a name="video-learning-resources"></a><span data-ttu-id="c3444-127">視訊學習資源</span><span class="sxs-lookup"><span data-stu-id="c3444-127">Video Learning Resources</span></span>

* <span data-ttu-id="c3444-128">[Introduction to Programming with F# series on YouTube](https://www.youtube.com/watch?v=Teak30_pXHk&list=PLEoMzSkcN8oNiJ67Hd7oRGgD1d4YBxYGC) (YouTube 上的 F# 系列程式設計簡介)</span><span class="sxs-lookup"><span data-stu-id="c3444-128">[Introduction to Programming with F# series on YouTube](https://www.youtube.com/watch?v=Teak30_pXHk&list=PLEoMzSkcN8oNiJ67Hd7oRGgD1d4YBxYGC)</span></span>
* <span data-ttu-id="c3444-129">[Introduction to F# series on FSharpTV](https://fsharp.tv/courses/fsharp-programming-intro/) (FSharpTV 上的 F# 系列簡介)</span><span class="sxs-lookup"><span data-stu-id="c3444-129">[Introduction to F# series on FSharpTV](https://fsharp.tv/courses/fsharp-programming-intro/)</span></span>

## <a name="further-resources"></a><span data-ttu-id="c3444-130">其他資源</span><span class="sxs-lookup"><span data-stu-id="c3444-130">Further Resources</span></span>

* <span data-ttu-id="c3444-131">[F# Learning Resources on fsharp.org](http://fsharp.org/learn.html) (fsharp.org 上的 F# 學習資源)</span><span class="sxs-lookup"><span data-stu-id="c3444-131">[F# Learning Resources on fsharp.org](http://fsharp.org/learn.html)</span></span>
* <span data-ttu-id="c3444-132">[F# Snippets Website](http://www.fssnip.net) (F# 程式碼片段網站)</span><span class="sxs-lookup"><span data-stu-id="c3444-132">[F# Snippets Website](http://www.fssnip.net)</span></span>
* <span data-ttu-id="c3444-133">[F# Software Foundation](http://fsharp.org) (F# 軟體基金會)</span><span class="sxs-lookup"><span data-stu-id="c3444-133">[F# Software Foundation](http://fsharp.org)</span></span>
