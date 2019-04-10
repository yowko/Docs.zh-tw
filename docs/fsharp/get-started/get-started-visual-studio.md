---
title: 開始使用F#在 Visual Studio 中
description: 了解如何使用F#使用 Visual Studio。
ms.date: 07/03/2018
ms.openlocfilehash: 020e5d32b3aa5d5a2195c19d70d8fe684fbd56ef
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59331906"
---
# <a name="get-started-with-f-in-visual-studio"></a>開始使用F#在 Visual Studio 中

F#和視覺效果F#工具所支援的 Visual Studio IDE。

若要開始，請確定您已[與 Visual Studio 一起安裝F# ](install-fsharp.md#install-f-with-visual-studio)。

## <a name="creating-a-console-application"></a>建立主控台應用程式

Visual Studio 中最基本的專案是主控台應用程式。  以下為作法。  一旦開啟 Visual Studio:

1. 在上**檔案**功能表上，指向**新增**，然後選擇**專案**。

2. 在 [新專案] 對話方塊中，下方**範本**，您應該會看到**視覺化F#** 。  選擇此選項以顯示F#範本。

3. 選取  **.NET Core 主控台應用程式**或是**主控台應用程式**。

3. 選擇**好** 按鈕來建立F#專案 ！  您現在應該會看到F#方案總管 中的專案。

## <a name="writing-your-code"></a>撰寫程式碼

讓我們開始先撰寫一些程式碼。  請確定`Program.fs`檔案開啟，並再將其內容取代為下列：

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

在先前的程式碼範例中，函式`square`它會接受名為的輸入已定義`x`並將它本身乘以。  因為F#會使用[型別推斷](../language-reference/type-inference.md)，類型`x`不需要指定。  F#編譯器了解有效，乘法的類型，並將指派到的類型`x`根據`square`呼叫。  如果您停留`square`，您應該會看到下列：

```
val square: x:int -> int
```

這就是所謂的函式的型別簽章。  它可以讀取像這樣："方形會接受名為整數的函式 x，並產生整數 」。  請注意，編譯器提供給`square``int`類型現在-這是因為乘法不是泛型跨*所有*類型，但而是跨一組封閉型別是泛型。  F#編譯器挑選`int`在這點，但它將會調整的型別簽章如果您呼叫`square`取代成不同輸入類型，例如`float`。

另一個函式， `main`，定義，這以裝飾`EntryPoint`告訴屬性F#應該那里啟動程式執行的編譯器。  它會遵循相同的慣例，因此另[c-style 程式設計語言](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)，其中可以傳遞命令列引數，此函式，而將整數傳回碼 (通常`0`)。

它是我們呼叫此函式內`square`函式使用引數`12`。  F#編譯器然後將指定的型別`square`要`int -> int`(也就是函式採用`int`，並產生`int`)。  若要呼叫`printfn`是格式化的列印函式以使用格式字串，類似 C 樣式程式設計語言，其對應至格式字串中所指定的參數，然後會列印結果和新行。

## <a name="running-your-code"></a>執行您的程式碼

您可以執行程式碼，並查看結果，按下**Ctrl**+**F5**。  這會執行程式，但不偵錯，並可讓您查看結果。  或者，您可以選擇**偵錯**最上層功能表項目在 Visual Studio 中，然後選擇**啟動但不偵錯**。

您現在應該會看到下列列印到主控台視窗的 Visual Studio 快顯出來：

```
12 squared is 144!
```

恭喜您！  您已建立您的第一個F#專案在 Visual Studio 中，寫入F#函式列印的結果呼叫的函式，並執行專案，請參閱某些結果。

## <a name="next-steps"></a>後續步驟

如果您還沒有這麼做，請參閱[概觀F# ](../tour.md)，其中涵蓋了一些核心功能的F#語言。  它會提供您的一些功能的概觀F#，並提供很大的程式碼範例，您可以將複製到 Visual Studio，並執行。  也有一些絕佳的外部資源，您可以使用，以展示[F#指南](../index.md)。

## <a name="see-also"></a>另請參閱

- [F# 的教學課程](../tour.md)
- [F#語言參考](../language-reference/index.md)
- [型別推斷](../language-reference/type-inference.md)
- [符號和運算子參考](../language-reference/symbol-and-operator-reference/index.md)
