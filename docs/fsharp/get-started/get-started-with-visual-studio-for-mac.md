---
title: 開始使用F# Visual Studio for Mac
description: 瞭解如何搭配 Visual Studio for Mac F#使用。
ms.date: 07/03/2018
ms.openlocfilehash: 679ed1ea28f5d0e0d910dbd407b38d1d2f0314f6
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629761"
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a>開始使用F# Visual Studio for Mac

F#Visual Studio for Mac IDE 中F#支援和視覺化檢視。 請確定您已[安裝 Visual Studio for Mac](install-fsharp.md#install-f-with-visual-studio-for-mac)。

## <a name="creating-a-console-application"></a>建立主控台應用程式

Visual Studio for Mac 中最基本的專案之一, 就是主控台應用程式。  以下為作法。  開啟 Visual Studio for Mac 之後:

1. 在 [檔案] 功能表上, 指向 [**新增方案**]。

2. 在 [新增專案] 對話方塊中, 主控台應用程式有2個不同的範本。  在以 .NET Framework 為目標的其他 > .NET 底下有一個。  另一個範本位於 .NET Core-以 .NET Core 為目標 > 應用程式底下。  其中一個範本應適用于本文的目的。

3. 在 [主控台應用程式C# ] F#下, 視需要將變更為。  選擇 [**下一步]** 按鈕繼續進行!  

4. 指定您的專案名稱, 然後選擇您想要用於應用程式的選項。  請注意, 畫面側邊的預覽窗格會顯示將根據選取的選項建立的目錄結構。  

5. 按一下 [建立]。  您現在應該會在F#方案總管中看到專案。

## <a name="writing-your-code"></a>撰寫程式碼

讓我們先從撰寫一些程式碼開始。  請確定`Program.fs`檔案已開啟, 然後以下列內容取代其內容:

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

在先前的程式碼範例中, `square`已定義函式, 它會接受`x`名為的輸入, 並將其本身相乘。  因為F#使用[類型推斷](../language-reference/type-inference.md), 所以`x`不需要指定的類型。  編譯器會瞭解乘法的有效類型, 並根據呼叫的方式`square`將類型指派`x`給。 F#  如果您將滑鼠`square`停留在上方, 您應該會看到下列內容:

```
val square: x:int -> int
```

這就是所謂的函式型別簽章。  它可以讀取如下:「方形是一個函式, 它會採用名為 x 的整數, 並產生一個整數」。  請注意, 編譯器`square` `int`現在提供類型, 這是因為乘法不是*所有*類型的泛型, 而是在一組封閉的類型之間是泛型的。  此時F#會選取`int`編譯器, 但如果您使用`float`不同的輸入類型 (例如) 呼叫`square` , 它會調整類型簽章。

已定義另一個函式, 該函式會`EntryPoint`使用屬性裝飾, 告訴F#編譯器應該在該處啟動程式執行。 `main`  其遵循與其他[C 樣式程式語言](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)相同的慣例, 其中命令列引數可傳遞給此函式, 並傳回整數代碼 (通常`0`是)。

在這個函式中, 我們使用的`square` `12`引數來呼叫函數。  然後F# , 編譯器會`int -> int`將的類型`square`指派為 ( `int`也就是採用並產生的函式`int`)。  對的呼叫`printfn`是格式化的列印函式, 它會使用格式字串, 類似于 C 樣式的程式語言、對應于格式字串中所指定的參數, 然後列印結果和新行。

## <a name="running-your-code"></a>執行您的程式碼

您可以從最上層功能表按一下 [**執行**] 來執行程式碼並查看結果, 然後在不進行檢查的情況**下啟動**。  這會執行程式而不進行偵測, 並可讓您查看結果。

您現在應該會在主控台視窗中看到下列列印 Visual Studio for Mac:

```
12 squared is 144!
```

恭喜您！  您已在 Visual Studio for Mac 中F#建立第一個專案, 並F#撰寫一個函式來列印呼叫該函數的結果, 然後執行專案以查看一些結果。

## <a name="using-f-interactive"></a>使用F#互動式

Visual Studio for Mac 中視覺化F#工具的其中一項最佳功能就是F#互動式視窗。  它可讓您將程式碼傳送至進程, 您可以在其中呼叫該程式碼, 並以互動方式查看結果。

若要開始使用, 請反`square`白顯示程式碼中定義的函式。  接下來, 按一下最上層功能表中的 [**編輯**]。  接下來 **, 選取 [ F#將選取範圍傳送至互動式**]。  這會在F#互動式視窗中執行程式碼。  或者, 您也可以在選取範圍上按一下滑鼠右鍵, 然後選擇 [**傳送選取專案F#到互動**]。  您應該會看到F#互動式視窗出現, 其中包含下列內容:

```
>

val square : x:int -> int

>
```

這會顯示函式的相同`square`函式簽章, 您稍早在函式上暫留時看到此功能。  因為`square`現在是在F#互動式進程中定義, 所以您可以使用不同的值來呼叫它:

```
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

這會執行函式、將結果系結至新`it`名稱, 並顯示的類型和`it`值。  請注意, 您必須使用`;;`來終止每一行。  這是互動式F#瞭解函式呼叫完成的方式。  您也可以在互動中定義F#新的函式:

```
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

上述會定義新的函式`isOdd` `int` , 它會接受並檢查其是否為奇數!  您可以呼叫此函式, 以查看它以不同的輸入傳回的內容。  您可以在函式呼叫中呼叫函數:

```
> isOdd (square 15);;
val it : bool = true
```

您也可以使用「順[向」運算子](../language-reference/symbol-and-operator-reference/index.md), 將值管線至這兩個函數:

```
> 15 |> square |> isOdd;;
val it : bool = true
```

後面的教學課程會涵蓋「管線轉寄」運算子等等。

這只是深入探討您可以使用F#互動式執行的工作。  若要深入瞭解, 請參閱[使用的F#互動式程式設計](../tutorials/fsharp-interactive/index.md)。

## <a name="next-steps"></a>後續步驟

如果您還沒有這麼做, 請參閱的[導覽F# ](../tour.md), 其中涵蓋了F#語言的一些核心功能。  它可讓您大致瞭解的某些功能F#, 並提供您可以複製到 Visual Studio for Mac 並執行的豐富程式碼範例。  還有一些您可以使用的絕佳外部資源, 請參閱[ F#指南](../index.md)中的展示。

## <a name="see-also"></a>另請參閱

- [Visual F#](../index.md)
- [F# 的教學課程](../tour.md)
- [F#語言參考](../language-reference/index.md)
- [型別推斷](../language-reference/type-inference.md)
- [符號和運算子參考](../language-reference/symbol-and-operator-reference/index.md)
