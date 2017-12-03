---
title: "F# 指南"
description: "深入了解 F # 執行.net 功能性程式設計語言。"
keywords: .NET, .NET Core
author: jackfoxy
ms.author: phcart
ms.date: 12/01/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: ea27fb37-dad1-4bd4-a3cc-4f5c70767ae9
ms.openlocfilehash: 45f5d2ca794ccea7a35cf6c0bf9d58a3e6500453
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="f-guide"></a><span data-ttu-id="380a3-104">F# 指南</span><span class="sxs-lookup"><span data-stu-id="380a3-104">F# Guide</span></span>

<span data-ttu-id="380a3-105">F # 是一種功能的程式設計語言.NET 上執行。</span><span class="sxs-lookup"><span data-stu-id="380a3-105">F# is a functional programming language which runs on .NET.</span></span>  <span data-ttu-id="380a3-106">除了支援的函式程式設計建構，它也會有物件的程式設計功能。</span><span class="sxs-lookup"><span data-stu-id="380a3-106">In addition to supporting functional programming constructs, it also has object programming capabilities.</span></span>  <span data-ttu-id="380a3-107">此混合式功能性程式設計與物件導向的功能，讓 F # 實用的語言，完成任何工作。</span><span class="sxs-lookup"><span data-stu-id="380a3-107">This hybrid of functional programming with object-oriented capabilities makes F# a pragmatic language for accomplishing any task.</span></span>

## <a name="if-youre-new-to-f"></a><span data-ttu-id="380a3-108">如果您剛接觸到 F #</span><span class="sxs-lookup"><span data-stu-id="380a3-108">If You're New to F#</span></span> #

<span data-ttu-id="380a3-109">如果您剛接觸到 F #，以開始[教學課程的 F #](tour.md)取得語言的概觀，以及其程式設計概念。</span><span class="sxs-lookup"><span data-stu-id="380a3-109">If you're new to F#, begin with the [Tour of F#](tour.md) to get an overview of the language and some of its programming concepts.</span></span>  <span data-ttu-id="380a3-110">如果您使用 Visual Studio，教學課程專案範本也包含相同的內容。</span><span class="sxs-lookup"><span data-stu-id="380a3-110">If you're using Visual Studio, the Tutorial project template contains the same content.</span></span>

## <a name="if-youre-experienced-with-f"></a><span data-ttu-id="380a3-111">如果您是熟悉 F #</span><span class="sxs-lookup"><span data-stu-id="380a3-111">If You're Experienced with F#</span></span> #

<span data-ttu-id="380a3-112">如果您知道您的工作環境 F # 中，或想要深入了解特定語言建構時，請參閱[語言參考](language-reference/index.md)。</span><span class="sxs-lookup"><span data-stu-id="380a3-112">If you know your way around F#, or want to learn more about a specific language construct, see the [Language Reference](language-reference/index.md).</span></span>  <span data-ttu-id="380a3-113">它是所有的 F # 語言功能的完整指南。</span><span class="sxs-lookup"><span data-stu-id="380a3-113">It's a thorough guide of all F# language capabilities.</span></span>

<span data-ttu-id="380a3-114">此外， [F # 核心程式庫參考](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference)是了解相關的 FSharp.Core，屬於的 F # 核心程式庫的絕佳資源。</span><span class="sxs-lookup"><span data-stu-id="380a3-114">Additionally, the [F# Core Library Reference](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference) is a great resource for learning about FSharp.Core, the core library which is a part of F#.</span></span>

## <a name="the-f-software-foundation"></a><span data-ttu-id="380a3-115">F# Software Foundation (F# 軟體基金會)</span><span class="sxs-lookup"><span data-stu-id="380a3-115">The F# Software Foundation</span></span>

<span data-ttu-id="380a3-116">雖然 Microsoft 是主要的 F # 語言和其工具開發人員，但 F # 也支援獨立的 foundation、 F # 軟體基礎 (FSSF)。</span><span class="sxs-lookup"><span data-stu-id="380a3-116">Although Microsoft is the primary developer of the F# language and its tooling, F# is also backed by an independent foundation, the F# Software Foundation (FSSF).</span></span>

<span data-ttu-id="380a3-117">F# Software Foundation 的使命是促進、保護和推展 F# 程式設計語言，並支援和促進 F# 程式設計人員國際社群的多元發展。</span><span class="sxs-lookup"><span data-stu-id="380a3-117">The mission of the F# Software Foundation is to promote, protect, and advance the F# programming language, and to support and facilitate the growth of a diverse and international community of F# programmers.</span></span>

<span data-ttu-id="380a3-118">若要進一步了解並參與，請參閱 [fsharp.org](http://fsharp.org)。</span><span class="sxs-lookup"><span data-stu-id="380a3-118">To learn more and get involved, check out [fsharp.org](http://fsharp.org).</span></span>

## <a name="documentation"></a><span data-ttu-id="380a3-119">文件</span><span class="sxs-lookup"><span data-stu-id="380a3-119">Documentation</span></span>

* [<span data-ttu-id="380a3-120">教學課程</span><span class="sxs-lookup"><span data-stu-id="380a3-120">Tutorials</span></span>](tutorials/getting-started/index.md)
* <span data-ttu-id="380a3-121">[當做第一級值的函式](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Programming](introduction-to-functional-programming/index.md)--></span><span class="sxs-lookup"><span data-stu-id="380a3-121">[Functions as First-Class Values](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Programming](introduction-to-functional-programming/index.md)--></span></span>
* [<span data-ttu-id="380a3-122">語言參考</span><span class="sxs-lookup"><span data-stu-id="380a3-122">Language Reference</span></span>](language-reference/index.md)
* [<span data-ttu-id="380a3-123">F# 核心程式庫參考</span><span class="sxs-lookup"><span data-stu-id="380a3-123">F# Core Library Reference</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference)

## <a name="online-reading-resources"></a><span data-ttu-id="380a3-124">線上閱讀資源</span><span class="sxs-lookup"><span data-stu-id="380a3-124">Online Reading Resources</span></span>

* <span data-ttu-id="380a3-125">[F# for Fun and Profit Gitbook](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/) (有趣且可獲益的 F# Gitbook)</span><span class="sxs-lookup"><span data-stu-id="380a3-125">[F# for Fun and Profit Gitbook](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/)</span></span> 
* <span data-ttu-id="380a3-126">[F# Programming Wikibook](https://en.wikibooks.org/wiki/F_Sharp_Programming) (F# 程式設計 Wikibook)</span><span class="sxs-lookup"><span data-stu-id="380a3-126">[F# Programming Wikibook](https://en.wikibooks.org/wiki/F_Sharp_Programming)</span></span>

## <a name="video-learning-resources"></a><span data-ttu-id="380a3-127">視訊學習資源</span><span class="sxs-lookup"><span data-stu-id="380a3-127">Video Learning Resources</span></span>

* <span data-ttu-id="380a3-128">[Introduction to Programming with F# series on YouTube](https://www.youtube.com/watch?v=Teak30_pXHk&list=PLEoMzSkcN8oNiJ67Hd7oRGgD1d4YBxYGC) (YouTube 上的 F# 系列程式設計簡介)</span><span class="sxs-lookup"><span data-stu-id="380a3-128">[Introduction to Programming with F# series on YouTube](https://www.youtube.com/watch?v=Teak30_pXHk&list=PLEoMzSkcN8oNiJ67Hd7oRGgD1d4YBxYGC)</span></span>
* <span data-ttu-id="380a3-129">[Introduction to F# series on FSharpTV](https://fsharp.tv/courses/fsharp-programming-intro/) (FSharpTV 上的 F# 系列簡介)</span><span class="sxs-lookup"><span data-stu-id="380a3-129">[Introduction to F# series on FSharpTV](https://fsharp.tv/courses/fsharp-programming-intro/)</span></span>

## <a name="further-resources"></a><span data-ttu-id="380a3-130">其他資源</span><span class="sxs-lookup"><span data-stu-id="380a3-130">Further Resources</span></span>

* <span data-ttu-id="380a3-131">[F# Learning Resources on fsharp.org](http://fsharp.org/learn.html) (fsharp.org 上的 F# 學習資源)</span><span class="sxs-lookup"><span data-stu-id="380a3-131">[F# Learning Resources on fsharp.org](http://fsharp.org/learn.html)</span></span>
* <span data-ttu-id="380a3-132">[F# Snippets Website](http://www.fssnip.net) (F# 程式碼片段網站)</span><span class="sxs-lookup"><span data-stu-id="380a3-132">[F# Snippets Website](http://www.fssnip.net)</span></span>
* <span data-ttu-id="380a3-133">[F# Software Foundation](http://fsharp.org) (F# 軟體基金會)</span><span class="sxs-lookup"><span data-stu-id="380a3-133">[F# Software Foundation](http://fsharp.org)</span></span>