---
title: 開始使用F# Visual Studio
description: 瞭解如何搭配 Visual Studio F#使用。
ms.date: 07/03/2018
ms.openlocfilehash: 24c9a81cfa61dc904db9b2213224677696d7eb9b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629763"
---
# <a name="get-started-with-f-in-visual-studio"></a>開始使用F# Visual Studio

F#Visual Studio IDE 中F#支援和視覺化檢視。

若要開始, 請確定您已[ F#使用安裝 Visual Studio ](install-fsharp.md#install-f-with-visual-studio)。

## <a name="creating-a-console-application"></a>建立主控台應用程式

Visual Studio 中最基本的專案之一, 就是主控台應用程式。  以下為作法。  開啟 Visual Studio 之後:

1. 在 [檔案] 功能表上, 指向 [**新增**], 然後選擇 [**專案**]。

2. 在 [新增專案] 對話方塊的 [**範本**] 底下, 您應該會看到 [**視覺效果F#** ]。  選擇此以顯示F#範本。

3. 選取 [ **.Net Core 主控台應用程式**] 或 [**主控台應用程式**]。

4. 選擇 [確定] 按鈕以建立F#專案!  您現在應該會在F#方案總管中看到專案。

## <a name="writing-your-code"></a>撰寫程式碼

讓我們先從撰寫一些程式碼開始。  請確定`Program.fs`檔案已開啟, 然後以下列內容取代其內容:

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

在先前的程式碼範例中, `square`已定義函式, 它會接受`x`名為的輸入, 並將其本身相乘。  因為F#使用[類型推斷](../language-reference/type-inference.md), 所以`x`不需要指定的類型。  編譯器會瞭解乘法的有效類型, 並根據呼叫的方式`square`將類型指派`x`給。 F#  如果您將滑鼠`square`停留在上方, 您應該會看到下列內容:

```fsharp
val square: x:int -> int
```

這就是所謂的函式型別簽章。  它可以讀取如下:「方形是一個函式, 它會採用名為 x 的整數, 並產生一個整數」。  請注意, 編譯器`square` `int`現在提供類型, 這是因為乘法不是*所有*類型的泛型, 而是在一組封閉的類型之間是泛型的。  此時F#會選取`int`編譯器, 但如果您使用`float`不同的輸入類型 (例如) 呼叫`square` , 它會調整類型簽章。

已定義另一個函式, 該函式會`EntryPoint`使用屬性裝飾, 告訴F#編譯器應該在該處啟動程式執行。 `main`  其遵循與其他[C 樣式程式語言](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)相同的慣例, 其中命令列引數可傳遞給此函式, 並傳回整數代碼 (通常`0`是)。

在這個函式中, 我們使用的`square` `12`引數來呼叫函數。  然後F# , 編譯器會`int -> int`將的類型`square`指派為 ( `int`也就是採用並產生的函式`int`)。  對的呼叫`printfn`是格式化的列印函式, 它會使用格式字串, 類似于 C 樣式的程式語言、對應于格式字串中所指定的參數, 然後列印結果和新行。

## <a name="running-your-code"></a>執行您的程式碼

您可以按下**Ctrl** + **F5**來執行程式碼並查看結果。  這會執行程式而不進行偵測, 並可讓您查看結果。  或者, 您可以選擇 Visual Studio 中的 [ **Debug** ] 最上層功能表項目, 然後選擇 [**啟動但不進行調試**]。

您現在應該會在主控台視窗中看到下列列印 Visual Studio:

```
12 squared is 144!
```

恭喜您！  您已在 Visual Studio 中F#建立第一個專案, 並F#撰寫一個函式來列印呼叫該函數的結果, 然後執行專案以查看一些結果。

## <a name="next-steps"></a>後續步驟

如果您還沒有這麼做, 請參閱的[導覽F# ](../tour.md), 其中涵蓋了F#語言的一些核心功能。  它可讓您大致瞭解的某些功能F#, 並提供您可以複製到 Visual Studio 並執行的豐富程式碼範例。  還有一些您可以使用的絕佳外部資源, 請參閱[ F#指南](../index.md)中的展示。

## <a name="see-also"></a>另請參閱

- [F# 的教學課程](../tour.md)
- [F#語言參考](../language-reference/index.md)
- [型別推斷](../language-reference/type-inference.md)
- [符號和運算子參考](../language-reference/symbol-and-operator-reference/index.md)
