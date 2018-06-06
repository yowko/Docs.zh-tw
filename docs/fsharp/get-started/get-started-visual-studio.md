---
title: '開始使用 F # Visual Studio 中'
description: '了解如何使用 F # 與 Visual Studio。'
ms.date: 02/13/2017
ms.openlocfilehash: 22fbe8086ec133605e1d9b4b28e524fe2ed8ac28
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34728530"
---
# <a name="get-started-with-f-in-visual-studio"></a>開始使用 F # Visual Studio 中

Visual Studio IDE 支援 F # 和 Visual F # 工具。  若要開始，您應該[下載 Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)，如果您還沒有這麼做。  本文使用 Visual Studio 2017 Community Edition，但是您可以使用 F # 與您所選擇的版本。

## <a name="installing-f"></a>正在安裝 F # #

如果您要下載 Visual Studio 第一次，它會先安裝 Visual Studio 安裝程式。  安裝任何版本的 Visual Studio 2017 從安裝程式。 如果您已經安裝，請按一下**修改**。

接下來，您會看到一份工作負載。 您可以安裝 F # 透過任何下列的工作負載：

|工作負載|動作|
|--------|------|
| .NET Core 跨平台開發 | 預設會不安裝任何動作-F # |
| ASP.NET 與網頁程式開發 | 預設會不安裝任何動作-F # |
| Azure 開發 | 預設會不安裝任何動作-F # |
| 使用 .NET 的行動應用程式開發 | 預設會不安裝任何動作-F # |
| 資料科學和分析應用程式 | 預設會不安裝任何動作-F # |
| .NET 桌面開發 | 選取**F # 的桌面版語言支援**右側 |
| 資料儲存體和流程 | 選取**F # 的桌面版語言支援**右側 |

接下來，按一下**修改**在右下角。  這會安裝您選取的所有項目。  接著，您可以開啟 Visual Studio 2017 與 F # 語言的支援，即可**啟動**。

## <a name="creating-a-console-application"></a>建立主控台應用程式

其中一個 Visual Studio 中最基本的專案是主控台應用程式。  以下為作法。  一旦開啟 Visual Studio:

1. 在**檔案**功能表上，指向**新增**，然後選擇 **專案**。

2.  在 [新增專案] 對話方塊中，在**範本**，您應該會看到**Visual F #**。  選擇此選項以顯示 F # 範本。

3. 選取  **.NET Core 主控台應用程式**或**主控台應用程式**。

3. 選擇**好**按鈕以建立 F # 專案 ！  您現在應該會看到 [方案總管] 中的 F # 專案。

## <a name="writing-your-code"></a>撰寫程式碼

讓我們開始吧撰寫一些程式碼第一次。  請確定`Program.fs`檔案已開啟，而且然後取代為下列內容：

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

在先前程式碼範例中，函式`square`其可接受名為輸入已定義`x`再將它本身。  因為 F # 使用[型別推斷](../language-reference/type-inference.md)的型別`x`不需要指定。  F # 編譯器瞭解乘法是有效的其中的型別，並將指派到的類型`x`根據`square`呼叫。  如果您將滑鼠停留在`square`，您應該會看到下列：

```
val square: x:int -> int
```

這是所謂的函式的類型簽章。  它可以讀取如下:"方會採用名為整數的函式 x，並產生整數 」。  請注意，編譯器提供`square``int`類型現在-這是因為乘法不是泛型跨*所有*類型、 但而是跨一組已關閉的類型是泛型。  F # 編譯器挑選`int`這點，但它會調整的類型簽章如果您呼叫`square`不同輸入類型，例如`float`。

另一個函式， `main`，定義，這以裝飾`EntryPoint`告訴 F # 編譯器執行該程式的屬性應該從那裡開始。  它會遵循與其他的相同慣例[c-style 程式設計語言](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)，然後從中命令列引數可以傳遞至這個函式，並將整數傳回碼 (通常`0`)。

它是我們會呼叫這個函式中`square`函式的引數`12`。  F # 編譯器然後將指定的型別`square`是`int -> int`(也就是函式會採用`int`並產生`int`)。  若要呼叫`printfn`是格式化的列印函式以使用格式字串，類似 c-style 程式設計語言，其對應至格式字串中指定的參數，然後列印結果和新行。

## <a name="running-your-code"></a>執行您的程式碼

您可以執行的程式碼，並按下查看結果**ctrl-f5**。  這會執行程式，但不偵錯，並可讓您查看結果。  或者，您可以選擇**偵錯**最上層功能表項目在 Visual Studio 中，並選擇**啟動但不偵錯**。

您現在應該會看到下列列印到主控台視窗上的 Visual Studio:

```
12 squared is 144!
```

恭喜您！  您在 Visual Studio 中建立第一個 F # 專案、 撰寫 F # 函式列印呼叫此函式的結果並執行專案，以查看一些結果。

## <a name="next-steps"></a>後續步驟

如果您還沒有這麼做，請參閱[教學課程的 F #](../tour.md)，其中涵蓋了某些 F # 語言的核心功能。  它會提供 F # 的功能概觀，並提供豐富的程式碼範例，您可以將複製到 Visual Studio，並執行。  也有一些絕佳的外部資源，您可以使用，在其中顯示[F # 指南](../index.md)。

## <a name="see-also"></a>另請參閱
 [Visual F#](index.md)  
 [F# 的教學課程](../tour.md)  
 [F # 語言參考](../language-reference/index.md)  
 [類型推斷](../language-reference/type-inference.md)  
 [符號和運算子參考](../language-reference/symbol-and-operator-reference/index.md)  
