---
title: 開始使用F# Visual Studio for Mac
description: 瞭解如何搭配 Visual Studio for Mac F#使用。
ms.date: 07/03/2018
ms.openlocfilehash: cd45ab9c59cef76e4bf85a93f39d8e2ee063d200
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552374"
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a>開始使用F# Visual Studio for Mac

F#Visual Studio for Mac IDE 中F#支援和視覺化檢視。 請確定您已[安裝 Visual Studio for Mac](install-fsharp.md#install-f-with-visual-studio-for-mac)。

## <a name="creating-a-console-application"></a>建立主控台應用程式

Visual Studio for Mac 中最基本的專案之一，就是主控台應用程式。  以下為作法。  開啟 Visual Studio for Mac 之後：

1. **在 [檔案**] 功能表上，指向 [**新增方案**]。

2. 在 [新增專案] 對話方塊中，主控台應用程式有2個不同的範本。  在以 .NET Framework 為目標的其他 > .NET 底下有一個。  另一個範本位於 .NET Core-以 .NET Core 為目標 > 應用程式底下。  其中一個範本應適用于本文的目的。

3. 在 [主控台應用程式C# ] F#下，視需要將變更為。  選擇 [**下一步]** 按鈕繼續進行！  

4. 指定您的專案名稱，然後選擇您想要用於應用程式的選項。  請注意，畫面側邊的預覽窗格會顯示將根據選取的選項建立的目錄結構。  

5. 按一下 [建立]。  您現在應該會在F#方案總管中看到專案。

## <a name="writing-your-code"></a>撰寫程式碼

讓我們先從撰寫一些程式碼開始。  請確定 `Program.fs` 檔案已開啟，然後以下列內容取代其內容：

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

在先前的程式碼範例中，已定義函式 `square`，它會接受名為 `x` 的輸入，並將其與本身相乘。  因為F#使用[型別推斷](../language-reference/type-inference.md)，所以不需要指定 `x` 的類型。  F#編譯器會瞭解乘法的有效值，並根據呼叫 `square` 的方式，將型別指派給 `x`。  如果您將滑鼠停留在 `square`上，您應該會看到下列內容：

```console
val square: x:int -> int
```

這就是所謂的函式型別簽章。  它可以讀取如下：「正方形是一個函式，它會採用名為 x 的整數，並產生一個整數」。  請注意，編譯器現在提供 `square` `int` 類型，這是因為乘法在*所有*類型之間並不是泛型，而是在一組封閉的類型之間是泛型的。  F#編譯器會在此時挑選 `int`，但如果您使用不同的輸入類型（例如 `float`）來呼叫 `square`，它會調整類型簽章。

已定義另一個函式 `main`，它會使用 `EntryPoint` 屬性裝飾，告訴編譯器應該F#在該處啟動程式執行。  其遵循與其他[C 樣式程式語言](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)相同的慣例，其中命令列引數可傳遞給此函式，並傳回整數代碼（通常 `0`）。

在這個函式中，我們使用 `12`的引數來呼叫 `square` 函數。  然後F#編譯器會指派要 `int -> int` 的 `square` 類型（也就是接受 `int` 並產生 `int`的函式）。  `printfn` 的呼叫是格式化的列印函式，它會使用格式字串，類似于 C 樣式的程式語言、對應于格式字串中所指定的參數，然後列印結果和新行。

## <a name="running-your-code"></a>執行您的程式碼

您可以從最上層功能表按一下 [**執行**] 來執行程式碼並查看結果，然後在不進行檢查的情況**下啟動**。  這會執行程式而不進行偵測，並可讓您查看結果。

您現在應該會在主控台視窗中看到下列列印 Visual Studio for Mac：

```console
12 squared is 144!
```

恭喜您！  您已在 Visual Studio for Mac 中F#建立第一個專案，並F#撰寫一個函式來列印呼叫該函數的結果，然後執行專案以查看一些結果。

## <a name="using-f-interactive"></a>使用F#互動式

Visual Studio for Mac 中視覺化F#工具的其中一項最佳功能就是F#互動式視窗。  它可讓您將程式碼傳送至進程，您可以在其中呼叫該程式碼，並以互動方式查看結果。

若要開始使用，請反白顯示程式碼中所定義的 `square` 函式。  接下來，按一下最上層功能表中的 [**編輯**]。  接下來 **，選取 [ F#將選取範圍傳送至互動式**]。  這會在F#互動式視窗中執行程式碼。  或者，您也可以在選取範圍上按一下滑鼠右鍵，然後選擇 [**傳送選取專案F#到互動**]。  您應該會看到F#互動式視窗出現，其中包含下列內容：

```console
>

val square : x:int -> int

>
```

這會顯示 `square` 函式的相同函式簽章，當您在函式上暫留時，您會看到此功能簽章。  由於 `square` 現在是在F#互動式進程中定義，因此您可以使用不同的值來呼叫它：

```console
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

這會執行函式，將結果系結至 `it`的新名稱，並顯示 `it`的類型和值。  請注意，您必須使用 `;;`來終止每一行。  這是互動式F#瞭解函式呼叫完成的方式。  您也可以在互動中定義F#新的函式：

```console
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

上述定義了新的函式 `isOdd`，它會接受 `int` 並檢查其是否為奇數！  您可以呼叫此函式，以查看它以不同的輸入傳回的內容。  您可以在函式呼叫中呼叫函數：

```console
> isOdd (square 15);;
val it : bool = true
```

您也可以使用「順[向」運算子](../language-reference/symbol-and-operator-reference/index.md)，將值管線至這兩個函數：

```console
> 15 |> square |> isOdd;;
val it : bool = true
```

後面的教學課程會涵蓋「管線轉寄」運算子等等。

這只是深入探討您可以使用F#互動式執行的工作。  若要深入瞭解，請參閱[使用的F#互動式程式設計](../tutorials/fsharp-interactive/index.md)。

## <a name="next-steps"></a>後續步驟

如果您還沒有這麼做，請參閱的[導覽F# ](../tour.md)，其中涵蓋了F#語言的一些核心功能。  它可讓您大致瞭解的某些功能F#，並提供您可以複製到 Visual Studio for Mac 並執行的豐富程式碼範例。  還有一些您可以使用的絕佳外部資源，請參閱[ F#指南](../index.yml)中的展示。

## <a name="see-also"></a>請參閱

- [F#輥](../index.yml)
- [F# 的教學課程](../tour.md)
- [F#語言參考](../language-reference/index.md)
- [型別推斷](../language-reference/type-inference.md)
- [符號和運算子參考](../language-reference/symbol-and-operator-reference/index.md)
