---
title: '開始使用 Visual Studio for Mac 中的 F #'
description: '瞭解如何搭配 Visual Studio for Mac 使用 F #。'
ms.date: 07/03/2018
ms.openlocfilehash: d2ad24ad18bb31419b39508f2cf555c82fbe2e0b
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96437998"
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a>開始使用 Visual Studio for Mac 中的 F #

Visual Studio for Mac IDE 支援 F # 和 Visual F# 工具。 確定您已 [安裝 Visual Studio for Mac](install-fsharp.md#install-f-with-visual-studio-for-mac)。

## <a name="creating-a-console-application"></a>建立主控台應用程式

Visual Studio for Mac 的其中一個最基本的專案是主控台應用程式。  以下說明如何執行這項作業。  Visual Studio for Mac 開啟之後：

1. **在 [檔案**] 功能表上，指向 [**新增方案**]。

2. 在 [新增專案] 對話方塊中，主控台應用程式有2個不同的範本。  在以 .NET Framework 為目標的其他 > .NET 下會有一個。  另一個範本是以 .net core 為目標的 > 應用程式，以 .NET Core 為目標。  這兩個範本都應該適用于本文的目的。

3. 在 [主控台應用程式] 下，視需要將 c # 變更為 F #。  選擇 [ **下一步]** 按鈕繼續進行！  

4. 為您的專案命名，並選擇您想要用於應用程式的選項。  請注意，畫面側邊的 [預覽] 窗格會顯示將根據選取的選項建立的目錄結構。  

5. 按一下 [建立]。  您現在應該會在方案總管中看到 F # 專案。

## <a name="writing-your-code"></a>撰寫程式碼

先撰寫一些程式碼，讓我們開始吧。  請確定檔案 `Program.fs` 已開啟，然後將其內容取代為下列內容：

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

在先前的程式碼範例中，已 `square` 定義函式，該函式會接受名為的輸入 `x` ，並將其本身相乘。  因為 F # 使用 [型別推斷](../language-reference/type-inference.md)，所以 `x` 不需要指定的型別。  F # 編譯器瞭解乘法有效的型別，而且會根據呼叫方式將型別指派給 `x` `square` 。  如果您將滑鼠停留在上方 `square` ，您應該會看到下列內容：

```console
val square: x:int -> int
```

這就是所謂的函式類型簽章。  它可以像這樣讀取：「方形是一個函式，它會採用名為 x 的整數，並產生整數」。  請注意，編譯器 `square` `int` 會提供目前的型別，這是因為在 *所有* 類型中的乘法不是泛型，而是在一組封閉的型別中是泛型。  此時會挑選 F # 編譯器 `int` ，但如果您 `square` 使用不同的輸入類型（例如）來呼叫，則會調整型別簽章 `float` 。

另外也定義了另一個函式， `main` 它是以 `EntryPoint` 屬性裝飾，告訴 F # 編譯器，程式執行應該在此開始。  它會遵循與其他 [C 樣式程式設計語言](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)相同的慣例，其中命令列引數可傳遞給此函式，而整數程式碼則會傳回 (通常 `0`) 。

在這個函式中，我們使用的 `square` 引數來呼叫函式 `12` 。  然後，F # 編譯器會將的型別指派為 `square` `int -> int` (也就是採用 `int` 並產生) 的函式 `int` 。  的呼叫 `printfn` 是格式化的列印函式，它會使用格式字串，類似于 C 樣式的程式設計語言、與格式字串中指定的參數對應的參數，然後列印結果和新的行。

## <a name="running-your-code"></a>執行您的程式碼

您可以從最上層功能表中按一下 [ **執行** ]，然後在不進行偵錯工具的情況 **下啟動**，來執行程式碼並查看結果。  這會執行程式而不進行任何偵測，並可讓您查看結果。

您現在應該會在主控台視窗中看到下列輸出 Visual Studio for Mac 快顯視窗：

```console
12 squared is 144!
```

恭喜！  您已在 Visual Studio for Mac 中建立您的第一個 F # 專案、撰寫 F # 函式以列印呼叫該函式的結果，並執行專案以查看某些結果。

## <a name="using-f-interactive"></a>使用 F# 互動

在 Visual Studio for Mac 中，Visual F# 工具的其中一個最佳功能是 F# 互動視窗。  它可讓您將程式碼傳送至進程，您可以在其中呼叫該程式碼，並以互動方式查看結果。

若要開始使用，請反白顯示 `square` 您程式碼中所定義的函式。  接著，按一下最上層功能表中的 [ **編輯** ]。  接下來選取 [ **傳送選取專案至 F# 互動**]。  這會在 F# 互動視窗中執行程式碼。  或者，您也可以在選取專案上按一下滑鼠右鍵，然後選擇 [ **傳送選取專案] F# 互動**。  您應該會看到 F# 互動視窗顯示如下：

```console
>

val square : x:int -> int

>
```

這會顯示函式的相同函式簽章，您稍早在此函式上方看到該簽章 `square` 。  因為 `square` 現在已在 F# 互動進程中定義，所以您可以使用不同的值來呼叫它：

```console
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

這會執行函數、將結果系結至新的名稱 `it` ，並顯示的類型和值 `it` 。  請注意，您必須使用來終止每一行 `;;` 。  這是在函式呼叫完成時 F# 互動知道的方式。  您也可以在 F# 互動中定義新函數：

```console
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

上述定義了新的函 `isOdd` 式，它會取得 `int` 並檢查是否為奇數！  您可以呼叫此函式，以查看傳回的內容有不同的輸入。  您可以呼叫函式呼叫內的函數：

```console
> isOdd (square 15);;
val it : bool = true
```

您也可以使用 [管道轉寄運算子](../language-reference/symbol-and-operator-reference/index.md) ，將值管線至兩個函數：

```console
> 15 |> square |> isOdd;;
val it : bool = true
```

順向運算子和其他的教學課程將在稍後的教學課程中討論。

這只是您可以運用 F# 互動的內容。  若要深入瞭解，請參閱 [使用 F # 的互動式程式設計](../tools/fsharp-interactive/index.md)。

## <a name="next-steps"></a>後續步驟

如果您尚未這麼做，請查看 [f #](../tour.md)的教學課程，其中包含 f # 語言的一些核心功能。  它將概述 F # 的一些功能，並提供可複製到 Visual Studio for Mac 並執行的豐富程式碼範例。  另外還有一些絕佳的外部資源可供您使用，請展示在 [F # 指南](../index.yml)中。

## <a name="see-also"></a>另請參閱

- [F# 指南](../index.yml)
- [F# 的教學課程](../tour.md)
- [F# 語言參考](../language-reference/index.md)
- [型別推斷](../language-reference/type-inference.md)
- [符號和運算子參考](../language-reference/symbol-and-operator-reference/index.md)
