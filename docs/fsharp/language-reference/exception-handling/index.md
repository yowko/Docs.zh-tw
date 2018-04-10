---
title: 例外狀況處理 (F#)
description: '了解 F # 中處理的例外狀況的基本概念，並尋找例外狀況處理運算式和函數的連結。'
keywords: Visual F#, F#, 函式程式設計
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: ad475c4a-d94e-47d9-b27b-3ff000b65f8e
ms.openlocfilehash: b61af66e0a70fdf9b86df37418c0284957d1f99e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="exception-handling"></a>例外狀況處理

本節包含 F# 語言例外狀況處理支援的相關資訊。


## <a name="exception-handling-basics"></a>例外狀況處理基本概念
例外狀況處理是 .NET Framework 中處理錯誤狀況的標準方式。 因此，任何 .NET 語言都必須支援此機制，包括 F#。 「例外狀況」是封裝錯誤之相關資訊的物件。 發生錯誤時，即會引發例外狀況並停止一般執行。 而執行階段會針對例外狀況搜尋適合的處理常式。 搜尋會在目前的函式中開始執行，繼續向上搜尋堆疊，遍及呼叫端層級，直到找到相符的處理常式為止。 接著，就會執行這個處理常式。

此外，當堆疊回溯時，執行階段會執行 `finally` 區塊中的所有程式碼，確保在回溯程序期間正確清除物件。


## <a name="related-topics"></a>相關主題

|標題|描述|
|-----|-----------|
|[例外狀況類型](exception-types.md)|描述如何宣告例外狀況類型。|
|[例外狀況：`try...with` 運算式](the-try-with-expression.md)|描述支援例外狀況處理的語言建構。|
|[例外狀況：`try...finally` 運算式](the-try-finally-expression.md)|描述當例外狀況擲回時，可讓您於堆疊回溯時執行清除程式碼的語言建構。|
|[例外狀況：`raise` 函式](the-raise-Function.md)|描述如何擲回例外狀況物件。|
|[例外狀況：`failwith` 函式](the-failwith-function.md)|描述如何產生一般 F# 例外狀況。|
|[例外狀況：`invalidArg` 函式](the-invalidArg-function.md)|描述如何產生無效引數例外狀況。|
