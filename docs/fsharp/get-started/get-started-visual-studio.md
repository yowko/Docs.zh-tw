---
title: 開始使用F# Visual Studio
description: 瞭解如何搭配 Visual Studio F#使用。
ms.date: 07/03/2018
ms.openlocfilehash: 80b4fc5b7631eace719832fe32003cad578ead27
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552825"
---
# <a name="get-started-with-f-in-visual-studio"></a>開始使用F# Visual Studio

F#Visual Studio IDE 中F#支援和視覺化檢視。

若要開始，請確定您已[ F#使用安裝 Visual Studio ](install-fsharp.md#install-f-with-visual-studio)。

## <a name="creating-a-console-application"></a>建立主控台應用程式

Visual Studio 中最基本的專案之一，就是主控台應用程式。  以下為作法。  開啟 Visual Studio 之後：

1. 在 [**檔案**] 功能表上，指向 [**新增**]，然後選擇 [**專案**]。

2. 在 [新增專案] 對話方塊的 [**範本**] 底下，您應該會看到 [**視覺效果F#** ]。  選擇此以顯示F#範本。

3. 選取 [ **.Net Core 主控台應用程式**] 或 [**主控台應用程式**]。

4. 選擇 [確定 **] 按鈕以**建立F#專案！  您現在應該會在F#方案總管中看到專案。

## <a name="writing-your-code"></a>撰寫程式碼

讓我們先從撰寫一些程式碼開始。  請確定 `Program.fs` 檔案已開啟，然後以下列內容取代其內容：

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

在先前的程式碼範例中，已定義函式 `square`，它會接受名為 `x` 的輸入，並將其與本身相乘。  因為F#使用[型別推斷](../language-reference/type-inference.md)，所以不需要指定 `x` 的類型。  F#編譯器會瞭解乘法的有效值，並根據呼叫 `square` 的方式，將型別指派給 `x`。  如果您將滑鼠停留在 `square`上，您應該會看到下列內容：

```fsharp
val square: x:int -> int
```

這就是所謂的函式型別簽章。  它可以讀取如下：「正方形是一個函式，它會採用名為 x 的整數，並產生一個整數」。  請注意，編譯器現在提供 `square` `int` 類型，這是因為乘法在*所有*類型之間並不是泛型，而是在一組封閉的類型之間是泛型的。  F#編譯器會在此時挑選 `int`，但如果您使用不同的輸入類型（例如 `float`）來呼叫 `square`，它會調整類型簽章。

已定義另一個函式 `main`，它會使用 `EntryPoint` 屬性裝飾，告訴編譯器應該F#在該處啟動程式執行。  其遵循與其他[C 樣式程式語言](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)相同的慣例，其中命令列引數可傳遞給此函式，並傳回整數代碼（通常 `0`）。

在這個函式中，我們使用 `12`的引數來呼叫 `square` 函數。  然後F#編譯器會指派要 `int -> int` 的 `square` 類型（也就是接受 `int` 並產生 `int`的函式）。  `printfn` 的呼叫是格式化的列印函式，它會使用格式字串，類似于 C 樣式的程式語言、對應于格式字串中所指定的參數，然後列印結果和新行。

## <a name="running-your-code"></a>執行您的程式碼

您可以按**Ctrl**+**F5**來執行程式碼並查看結果。  這會執行程式而不進行偵測，並可讓您查看結果。  或者，您可以選擇 Visual Studio 中的 [ **Debug** ] 最上層功能表項目，然後選擇 [**啟動但不進行調試**]。

您現在應該會在主控台視窗中看到下列列印 Visual Studio：

```console
12 squared is 144!
```

恭喜您！  您已在 Visual Studio 中F#建立第一個專案，並F#撰寫一個函式來列印呼叫該函數的結果，然後執行專案以查看一些結果。

## <a name="next-steps"></a>後續步驟

如果您還沒有這麼做，請參閱的[導覽F# ](../tour.md)，其中涵蓋了F#語言的一些核心功能。  它可讓您大致瞭解的某些功能F#，並提供您可以複製到 Visual Studio 並執行的豐富程式碼範例。  您也可以在F#檔[ F#首頁](../index.yml)中深入瞭解檔。

## <a name="see-also"></a>請參閱

- [F# 的教學課程](../tour.md)
- [F#語言參考](../language-reference/index.md)
- [型別推斷](../language-reference/type-inference.md)
- [符號和運算子參考](../language-reference/symbol-and-operator-reference/index.md)
