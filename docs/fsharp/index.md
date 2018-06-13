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
# <a name="f-guide"></a>F# 指南

F # 是功能性執行.net 程式語言。 它也會有完整的物件，可讓您 blend 功能和物件的任何問題的實用方案的程式設計支援。

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

F # 是關於在其核心的產能。 無所不在和進階功能的完整 F # 工具支援。

## <a name="learning-f"></a>了解 F # #

[F # 教學課程](tour.md)且大量的程式碼範例的主要語言功能的概觀。 如果您是新手 F #，而且想要的操作有初步的語言的運作方式，這項建議。

[開始使用 F # Visual Studio 中](get-started/get-started-visual-studio.md)如果您是在 Windows 上，且要完整的 Visual Studio IDE （Integraded 開發環境） 體驗。

[開始使用 F # 在 Visual Studio for Mac](get-started/get-started-with-visual-studio-for-mac.md)如果您 macOS 而且想要使用 Visual Studio IDE。

[開始使用 F # Visual Studio 程式碼中](get-started/get-started-vscode.md)如果您想要跨平台的輕量型和功能的 IDE 體驗。

[開始使用 F # 和.NET 核心 CLI](get-started/get-started-command-line.md)如果您想要使用命令列工具。

[開始使用 F # 和 Xamarin](https://docs.microsoft.com/xamarin/cross-platform/platform/fsharp/)行動 F # 的程式設計。

[F # Azure 筆記本的](https://notebooks.azure.com/Microsoft/libraries/samples/html/FSharp%20for%20Azure%20Notebooks.ipynb)是了解 F # 中可用、 託管 Jupyter 筆記本教學課程。

## <a name="references"></a>參考

[F # 語言參考](language-reference/index.md)是所有的 F # 語言功能的正式、 完整參考。 每個發行項說明語法，並顯示程式碼範例。 您可以使用篩選器列在目錄中，若要尋找特定的發行項。

[F # 核心程式庫參考](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference)為 F # 核心程式庫中的應用程式開發介面參考。


## <a name="additional-guides"></a>其他的輔助線

[F # 樂趣和收益](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/)是學習 F # 完整且非常詳細的書籍。 它的內容和作者是心愛 F # 社群。 目標對象是主要物件導向程式設計背景的開發人員。

[F # 程式設計 Wikibook](https://en.wikibooks.org/wiki/F_Sharp_Programming)是有關了解 F # wikibook。 它也是 F # 社群的產品。 目標對象是剛接觸到 F # 中，利用最少的物件導向程式設計背景的人員。

## <a name="learn-f-through-videos"></a>深入了解 F # 透過影片

[YouTube 上的 F # 教學課程](https://www.youtube.com/watch?v=c7eNDJN758U)是不錯的介紹，F # 使用 Visual Studio 中，顯示 1.5 小時期間的許多絕佳範例。 目標對象是剛接觸到 F # Visual Studio 開發人員。

[使用 F # 的程式設計簡介](https://www.youtube.com/watch?v=Teak30_pXHk&list=PLEoMzSkcN8oNiJ67Hd7oRGgD1d4YBxYGC)是絕佳的影片系列使用 Visual Studio 程式碼做為主要的編輯器。 影片系列是從執行任何動作，而結束建置以文字為基礎的 RPG 視訊遊戲。 目標對象是開發人員偏好使用 Visual Studio 程式碼 （或是輕量型 IDE） 和 F # 不熟悉。

[What's New in F # 的開發人員的 Visual Studio 2017](https://www.linkedin.com/learning/what-s-new-in-visual-studio-2017-for-f-sharp-for-developers)是 F # 在 Visual Studio 2017 顯示一些較新功能的視訊課程。 目標對象是剛接觸到 F # Visual Studio 開發人員。

## <a name="other-useful-resources"></a>其他實用資源

[F # 程式碼片段網站](http://www.fssnip.net)包含一組大量程式碼片段示範如何執行幾乎任何在 F # 中，範圍介於徹底初學者至進階的程式碼片段。

[F # 軟體 Foundation Slack](http://fsharp.org/guides/slack/)是一個很好的初學者所設計和專家，相同的這是高作用中，並有某些世界最佳 F # 程式設計人員可用的交談。 我們強烈建議您加入。

## <a name="the-f-software-foundation"></a>F# Software Foundation (F# 軟體基金會)

雖然 Microsoft 是主要的 F # 語言和 Visual Studio 中的工具開發人員，但 F # 也支援獨立的 foundation、 F # 軟體基礎 (FSSF)。

F# Software Foundation 的使命是促進、保護和推展 F# 程式設計語言，並支援和促進 F# 程式設計人員國際社群的多元發展。

若要進一步了解並參與，請參閱 [fsharp.org](http://fsharp.org)。若要加入，免費且 foundation 中的 F # 開發人員的網路是您不希望錯過 ！
