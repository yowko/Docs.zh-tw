---
title: '開始使用 F # 在 Visual Studio for Mac'
description: '了解如何使用 F # 與 Visual Studio for mac。'
ms.date: 02/13/2017
ms.openlocfilehash: 58e65e703b092f2ee5d74386051b158c932013b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a>開始使用 F # 在 Visual Studio for Mac

F # 和 Visual F # 工具支援 Visual Studio for Mac IDE。  若要開始，您應該[下載 Visual Studio for Mac](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)，如果您還沒有這麼做。  本文使用 Visual Studio 社群 2017 for Mac，但是您可以使用 F # 與您所選擇的版本。

## <a name="installing-f"></a>正在安裝 F # #

下載 Visual Studio for Mac 之後, 就會提示您選擇您想要安裝。  基於本文的目的，我們會離開預設值。  相較於 Visual Studio for Windows，您不需要特別安裝 F # 支援。  請按 [安裝] 以繼續。

安裝完成後，選擇 [啟動 Visual Studio]。  您也可以啟動它透過搜尋 macOS 上。

## <a name="creating-a-console-application"></a>建立主控台應用程式

在 Visual Studio for Mac 最基本的專案是主控台應用程式。  以下為作法。  一旦開啟 Visual Studio for Mac:

1. 在**檔案**功能表上，指向**新方案**。

2.  在 [新增專案] 對話方塊中，有 2 不同的範本，為主控台應用程式。  有一個在 其他-> 以.NET Framework 為目標的.NET。  .NET core 是其他範本]-> [應用程式為目標的.NET Core。  其中一個範本應該針對本文的目的工作。

3. 在主控台應用程式中，視需要變更 C# F #。  選擇**下一步**向前移動的按鈕 ！  

4. 為您的專案命名，並選擇您想要的應用程式的選項。  請注意，螢幕將會顯示將建立的目錄結構的側邊的 [預覽] 窗格會根據選取的選項。  

5. 按一下 [建立] 。  您現在應該會看到 [方案總管] 中的 F # 專案。

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

您可以執行的程式碼，並查看結果上的 **執行**從最上層功能表，然後**啟動但不偵錯**。  這會執行程式，但不偵錯，並可讓您查看結果。

您現在應該會看到下列列印到主控台視窗上的 Visual Studio for Mac:

```
12 squared is 144!
```

恭喜您！  您在 Visual Studio 中建立第一個 F # 專案，適用於 Mac、 撰寫 F # 函式列印呼叫此函式的結果並執行專案，以查看一些結果。

## <a name="using-f-interactive"></a>使用 F # Interactive

其中一個最佳功能的 Visual F # 工具在 Visual Studio for Mac 是 F # Interactive 視窗。  它可讓您透過的程式碼傳送至處理序，您可以在此呼叫該程式碼，並以互動方式查看結果。

若要開始使用它，反白顯示`square`程式碼中定義的函式。  接下來，按一下**編輯**從最上層功能表。  接下來選取**將選取範圍傳送至 F # Interactive**。  這是 F # Interactive 視窗中執行程式碼。  或者，您可以在 選取項目上按一下滑鼠右鍵，然後選擇**將選取範圍傳送至 F # Interactive**。  您應該會看到 F # 互動式視窗會出現在它為下列：

```
>

val square : x:int -> int

>
```

這會顯示為相同的函式簽章`square`函式，當您暫留在進入函式之前看到。  因為`square`是定義在 F # 互動式處理序中，現在可以呼叫具有不同值：

```
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

這會執行函式，請將結果繫結至新的名稱`it`，並顯示類型和值`it`。  請注意，您必須終止與每一行`;;`。  這是如何 F # Interactive 知道函式呼叫完成時。  您也可以定義新的函式 F # Interactive 中：

```
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

上述定義新的函式， `isOdd`，這個方法會接受`int`和檢查，以查看是否為奇數 ！  您可以呼叫此函式，以查看它傳回以不同的輸入。  您可以呼叫函式呼叫中的函式：

```
> isOdd (square 15);;
val it : bool = true
```

您也可以使用[管道正運算子](../language-reference/symbol-and-operator-reference/index.md)值導入兩個函式：

```
> 15 |> square |> isOdd;;
val it : bool = true
```

管道正運算子和詳細資訊，之後的教學課程所述。

這是一窺成您可以使用 F # Interactive 執行。  若要進一步了解，請參閱[使用 F # 互動式程式設計](../tutorials/fsharp-interactive/index.md)。

## <a name="next-steps"></a>後續步驟

如果您還沒有這麼做，請參閱[教學課程的 F #](../tour.md)，其中涵蓋了某些 F # 語言的核心功能。  它會提供 F # 的功能概觀，並提供豐富的程式碼範例，您可以將複製到 Visual Studio for Mac 並執行。  也有一些絕佳的外部資源，您可以使用，在其中顯示[F # 指南](../index.md)。

## <a name="see-also"></a>另請參閱
 [Visual F#](../index.md)  
 [F# 的教學課程](../tour.md)  
 [F # 語言參考](../language-reference/index.md)  
 [類型推斷](../language-reference/type-inference.md)  
 [符號和運算子參考](../language-reference/symbol-and-operator-reference/index.md)  
