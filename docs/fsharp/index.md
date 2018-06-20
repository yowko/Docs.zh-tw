---
title: F# 指南
description: '本指南提供各種學習材料 F #，功能性執行.net 程式語言的概觀。'
author: jackfoxy
ms.date: 03/19/2018
ms.openlocfilehash: cb829e904c006467e1470752b4fe8757ca694b05
ms.sourcegitcommit: 895c7602386a6dfe7ca4facce3d965b27e5c6e87
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2018
ms.locfileid: "34311997"
---
# <a name="f-guide"></a><span data-ttu-id="3266b-103">F# 指南</span><span class="sxs-lookup"><span data-stu-id="3266b-103">F# Guide</span></span>

<span data-ttu-id="3266b-104">F # 是功能性執行.net 程式語言。</span><span class="sxs-lookup"><span data-stu-id="3266b-104">F# is a functional programming language that runs on .NET.</span></span> <span data-ttu-id="3266b-105">它也會有完整的物件，可讓您 blend 功能和物件的任何問題的實用方案的程式設計支援。</span><span class="sxs-lookup"><span data-stu-id="3266b-105">It also has full support for objects, letting you blend functional and object programming for pragmatic solutions to any problem.</span></span>

```fsharp
open System // Get access to functionality in System namespace.

// Function: takes a name and produces a greeting.
let getGreeting name =
    sprintf "Hello, %s! Isn't F# great?" name

// Use the EntryPoint attribute to run the program.
[<EntryPoint>]
let main args =
    // Define a list of names
    let names = [| "Don"; "Julia"; "Xi" |]
    
    // Print a fun greeting for each name!
    names
    |> Array.map getGreeting
    |> Array.iter (fun greeting -> printfn "%s" greeting)

    0
```

<span data-ttu-id="3266b-106">F # 是關於在其核心的產能。</span><span class="sxs-lookup"><span data-stu-id="3266b-106">F# is about productivity at its heart.</span></span> <span data-ttu-id="3266b-107">無所不在和進階功能的完整 F # 工具支援。</span><span class="sxs-lookup"><span data-stu-id="3266b-107">The tooling support for F# is ubiquitous and full of advanced features.</span></span>

## <a name="learning-f"></a><span data-ttu-id="3266b-108">了解 F #</span><span class="sxs-lookup"><span data-stu-id="3266b-108">Learning F#</span></span> #

<span data-ttu-id="3266b-109">[F # 教學課程](tour.md)且大量的程式碼範例的主要語言功能的概觀。</span><span class="sxs-lookup"><span data-stu-id="3266b-109">[Tour of F#](tour.md) gives an overview of major language features with lots of code samples.</span></span> <span data-ttu-id="3266b-110">如果您是新手 F #，而且想要的操作有初步的語言的運作方式，這項建議。</span><span class="sxs-lookup"><span data-stu-id="3266b-110">This is recommended if you are new to F# and want to get a feel for how the language works.</span></span>

<span data-ttu-id="3266b-111">[開始使用 F # Visual Studio 中](get-started/get-started-visual-studio.md)如果您是在 Windows 上，且要完整的 Visual Studio IDE （Integraded 開發環境） 體驗。</span><span class="sxs-lookup"><span data-stu-id="3266b-111">[Get started with F# in Visual Studio](get-started/get-started-visual-studio.md) if you're on Windows and want the full Visual Studio IDE (Integraded Development Environment) experience.</span></span>

<span data-ttu-id="3266b-112">[開始使用 F # 在 Visual Studio for Mac](get-started/get-started-with-visual-studio-for-mac.md)如果您 macOS 而且想要使用 Visual Studio IDE。</span><span class="sxs-lookup"><span data-stu-id="3266b-112">[Get started with F# in Visual Studio for Mac](get-started/get-started-with-visual-studio-for-mac.md) if you're on macOS and want to use a Visual Studio IDE.</span></span>

<span data-ttu-id="3266b-113">[開始使用 F # Visual Studio 程式碼中](get-started/get-started-vscode.md)如果您想要跨平台的輕量型和功能的 IDE 體驗。</span><span class="sxs-lookup"><span data-stu-id="3266b-113">[Get Started with F# in Visual Studio Code](get-started/get-started-vscode.md) if you want a lightweight, cross-platform, and feature-packed IDE experience.</span></span>

<span data-ttu-id="3266b-114">[開始使用 F # 和.NET 核心 CLI](get-started/get-started-command-line.md)如果您想要使用命令列工具。</span><span class="sxs-lookup"><span data-stu-id="3266b-114">[Get started with F# with the .NET Core CLI](get-started/get-started-command-line.md) if you want to use command-line tools.</span></span>

<span data-ttu-id="3266b-115">[開始使用 F # 和 Xamarin](https://docs.microsoft.com/xamarin/cross-platform/platform/fsharp/)行動 F # 的程式設計。</span><span class="sxs-lookup"><span data-stu-id="3266b-115">[Get started with F# and Xamarin](https://docs.microsoft.com/xamarin/cross-platform/platform/fsharp/) for mobile programming with F#.</span></span>

<span data-ttu-id="3266b-116">[F # Azure 筆記本的](https://notebooks.azure.com/Microsoft/libraries/samples/html/FSharp%20for%20Azure%20Notebooks.ipynb)是了解 F # 中可用、 託管 Jupyter 筆記本教學課程。</span><span class="sxs-lookup"><span data-stu-id="3266b-116">[F# for Azure Notebooks](https://notebooks.azure.com/Microsoft/libraries/samples/html/FSharp%20for%20Azure%20Notebooks.ipynb) is a tutorial for learning F# in a free, hosted Jupyter Notebook.</span></span>

## <a name="references"></a><span data-ttu-id="3266b-117">參考</span><span class="sxs-lookup"><span data-stu-id="3266b-117">References</span></span>

<span data-ttu-id="3266b-118">[F # 語言參考](language-reference/index.md)是所有的 F # 語言功能的正式、 完整參考。</span><span class="sxs-lookup"><span data-stu-id="3266b-118">[F# Language Reference](language-reference/index.md) is the official, comprehensive reference for all F# language features.</span></span> <span data-ttu-id="3266b-119">每個發行項說明語法，並顯示程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="3266b-119">Each article explains the syntax and shows code samples.</span></span> <span data-ttu-id="3266b-120">您可以使用篩選器列在目錄中，若要尋找特定的發行項。</span><span class="sxs-lookup"><span data-stu-id="3266b-120">You can use the filter bar in the table of contents to find specific articles.</span></span>

<span data-ttu-id="3266b-121">[F # 核心程式庫參考](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference)為 F # 核心程式庫中的應用程式開發介面參考。</span><span class="sxs-lookup"><span data-stu-id="3266b-121">[F# Core Library Reference](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference) is the API reference for the F# Core Library.</span></span>


## <a name="additional-guides"></a><span data-ttu-id="3266b-122">其他的輔助線</span><span class="sxs-lookup"><span data-stu-id="3266b-122">Additional guides</span></span>

<span data-ttu-id="3266b-123">[F # 樂趣和收益](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/)是學習 F # 完整且非常詳細的書籍。</span><span class="sxs-lookup"><span data-stu-id="3266b-123">[F# for Fun and Profit](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/) is a comprehensive and very detailed book on learning F#.</span></span> <span data-ttu-id="3266b-124">它的內容和作者是心愛 F # 社群。</span><span class="sxs-lookup"><span data-stu-id="3266b-124">Its contents and author are beloved by the F# community.</span></span> <span data-ttu-id="3266b-125">目標對象是主要物件導向程式設計背景的開發人員。</span><span class="sxs-lookup"><span data-stu-id="3266b-125">The target audience is primarily developers with an object oriented programming background.</span></span>

<span data-ttu-id="3266b-126">[F # 程式設計 Wikibook](https://en.wikibooks.org/wiki/F_Sharp_Programming)是有關了解 F # wikibook。</span><span class="sxs-lookup"><span data-stu-id="3266b-126">[F# Programming Wikibook](https://en.wikibooks.org/wiki/F_Sharp_Programming) is a wikibook about learning F#.</span></span> <span data-ttu-id="3266b-127">它也是 F # 社群的產品。</span><span class="sxs-lookup"><span data-stu-id="3266b-127">It is also a product of the F# community.</span></span> <span data-ttu-id="3266b-128">目標對象是剛接觸到 F # 中，利用最少的物件導向程式設計背景的人員。</span><span class="sxs-lookup"><span data-stu-id="3266b-128">The target audience is people who are new to F#, with a little bit of object oriented programming background.</span></span>

## <a name="learn-f-through-videos"></a><span data-ttu-id="3266b-129">深入了解 F # 透過影片</span><span class="sxs-lookup"><span data-stu-id="3266b-129">Learn F# through videos</span></span>

<span data-ttu-id="3266b-130">[YouTube 上的 F # 教學課程](https://www.youtube.com/watch?v=c7eNDJN758U)是不錯的介紹，F # 使用 Visual Studio 中，顯示 1.5 小時期間的許多絕佳範例。</span><span class="sxs-lookup"><span data-stu-id="3266b-130">[F# tutorial on YouTube](https://www.youtube.com/watch?v=c7eNDJN758U) is a great introduction to F# using Visual Studio, showing lots of great examples over the course of 1.5 hours.</span></span> <span data-ttu-id="3266b-131">目標對象是剛接觸到 F # Visual Studio 開發人員。</span><span class="sxs-lookup"><span data-stu-id="3266b-131">The target audience is Visual Studio developers who are new to F#.</span></span>

<span data-ttu-id="3266b-132">[使用 F # 的程式設計簡介](https://www.youtube.com/watch?v=Teak30_pXHk&list=PLEoMzSkcN8oNiJ67Hd7oRGgD1d4YBxYGC)是絕佳的影片系列使用 Visual Studio 程式碼做為主要的編輯器。</span><span class="sxs-lookup"><span data-stu-id="3266b-132">[Introduction to Programming with F#](https://www.youtube.com/watch?v=Teak30_pXHk&list=PLEoMzSkcN8oNiJ67Hd7oRGgD1d4YBxYGC) is a great video series that uses Visual Studio Code as the main editor.</span></span> <span data-ttu-id="3266b-133">影片系列是從執行任何動作，而結束建置以文字為基礎的 RPG 視訊遊戲。</span><span class="sxs-lookup"><span data-stu-id="3266b-133">The video series starts from nothing and ends with building a text-based RPG video game.</span></span> <span data-ttu-id="3266b-134">目標對象是開發人員偏好使用 Visual Studio 程式碼 （或是輕量型 IDE） 和 F # 不熟悉。</span><span class="sxs-lookup"><span data-stu-id="3266b-134">The target audience is developers who prefer Visual Studio Code (or a lightweight IDE) and are new to F#.</span></span>

<span data-ttu-id="3266b-135">[What's New in F # 的開發人員的 Visual Studio 2017](https://www.linkedin.com/learning/what-s-new-in-visual-studio-2017-for-f-sharp-for-developers)是 F # 在 Visual Studio 2017 顯示一些較新功能的視訊課程。</span><span class="sxs-lookup"><span data-stu-id="3266b-135">[What's New in Visual Studio 2017 for F# For Developers](https://www.linkedin.com/learning/what-s-new-in-visual-studio-2017-for-f-sharp-for-developers) is a video course that shows some of the newer features for F# in Visual Studio 2017.</span></span> <span data-ttu-id="3266b-136">目標對象是剛接觸到 F # Visual Studio 開發人員。</span><span class="sxs-lookup"><span data-stu-id="3266b-136">The target audience is Visual Studio developers who are new to F#.</span></span>

## <a name="other-useful-resources"></a><span data-ttu-id="3266b-137">其他實用資源</span><span class="sxs-lookup"><span data-stu-id="3266b-137">Other useful resources</span></span>

<span data-ttu-id="3266b-138">[F # 程式碼片段網站](http://www.fssnip.net)包含一組大量程式碼片段示範如何執行幾乎任何在 F # 中，範圍介於徹底初學者至進階的程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="3266b-138">The [F# Snippets Website](http://www.fssnip.net) contains a massive set of code snippets showing how to do just about anything in F#, ranging from absolute beginner to highly advanced snippets.</span></span>

<span data-ttu-id="3266b-139">[F # 軟體 Foundation Slack](http://fsharp.org/guides/slack/)是一個很好的初學者所設計和專家，相同的這是高作用中，並有某些世界最佳 F # 程式設計人員可用的交談。</span><span class="sxs-lookup"><span data-stu-id="3266b-139">The [F# Software Foundation Slack](http://fsharp.org/guides/slack/) is a great place for beginners and experts alike, is highly active, and has some of world's best F# programmers available for a chat.</span></span> <span data-ttu-id="3266b-140">我們強烈建議您加入。</span><span class="sxs-lookup"><span data-stu-id="3266b-140">We highly recommend joining.</span></span>

## <a name="the-f-software-foundation"></a><span data-ttu-id="3266b-141">F# Software Foundation (F# 軟體基金會)</span><span class="sxs-lookup"><span data-stu-id="3266b-141">The F# Software Foundation</span></span>

<span data-ttu-id="3266b-142">雖然 Microsoft 是主要的 F # 語言和 Visual Studio 中的工具開發人員，但 F # 也支援獨立的 foundation、 F # 軟體基礎 (FSSF)。</span><span class="sxs-lookup"><span data-stu-id="3266b-142">Although Microsoft is the primary developer of the F# language and its tools in Visual Studio, F# is also backed by an independent foundation, the F# Software Foundation (FSSF).</span></span>

<span data-ttu-id="3266b-143">F# Software Foundation 的使命是促進、保護和推展 F# 程式設計語言，並支援和促進 F# 程式設計人員國際社群的多元發展。</span><span class="sxs-lookup"><span data-stu-id="3266b-143">The mission of the F# Software Foundation is to promote, protect, and advance the F# programming language, and to support and facilitate the growth of a diverse and international community of F# programmers.</span></span>

<span data-ttu-id="3266b-144">若要進一步了解並參與，請參閱 [fsharp.org](http://fsharp.org)。若要加入，免費且 foundation 中的 F # 開發人員的網路是您不希望錯過 ！</span><span class="sxs-lookup"><span data-stu-id="3266b-144">To learn more and get involved, check out [fsharp.org](http://fsharp.org). It's free to join, and the network of F# developers in the foundation is something you don't want to miss out on!</span></span>
