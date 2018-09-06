---
title: '開始使用 F # 在 Visual Studio for Mac'
description: '了解如何使用 F # 與 Visual Studio for mac。'
ms.date: 07/03/2018
ms.openlocfilehash: 6aceec299c29e04aecd7999cd1dda6a56dd2779a
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43785527"
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a>開始使用 F # 在 Visual Studio for Mac

F # 和 Visual F # 工具支援 Visual Studio for Mac IDE。 請確定您已[Visual Studio for Mac 安裝](install-fsharp.md#install-f-with-visual-studio-for-mac)。

## <a name="creating-a-console-application"></a>建立主控台應用程式

其中一個 Visual Studio for Mac 中最基本的專案是主控台應用程式。  以下為作法。  一旦開啟 Visual Studio for Mac:

1. 在 **檔案**功能表上，指向**新的方案**。

2.  在 [新增專案] 對話方塊中，有 2 個不同的範本，為主控台應用程式。  有一個 其他-> .NET Framework 為目標的.NET。  其他範本是在.NET Core]-> [以.NET Core 為目標的應用程式。  其中一個範本應可基於本文的目的。

3. 在主控台應用程式，視需要變更 C# F #。  選擇**下一步**按鈕以向前移動 ！  

4. 為您的專案命名，並選擇您想要的應用程式的選項。  請注意，畫面會顯示將建立的目錄結構的側邊的 [預覽] 窗格會根據選取的選項。  

5. 按一下 [建立] 。  現在，您應該會看到 [方案總管] 中的 F # 專案。

## <a name="writing-your-code"></a>撰寫程式碼

讓我們開始先撰寫一些程式碼。  請確定`Program.fs`檔案開啟，並再將其內容取代為下列：

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

在先前的程式碼範例中，函式`square`它會接受名為的輸入已定義`x`並將它本身乘以。  由於 F # 會使用[型別推斷](../language-reference/type-inference.md)的型別`x`不需要指定。  F # 編譯器了解有效，乘法的類型，並將指派到的類型`x`根據`square`呼叫。  如果您停留`square`，您應該會看到下列：

```
val square: x:int -> int
```

這就是所謂的函式的型別簽章。  它可以讀取像這樣:"方形會接受名為整數的函式 x，並產生整數 」。  請注意，編譯器提供給`square``int`類型現在-這是因為乘法不是泛型跨*所有*類型，但而是跨一組封閉型別是泛型。  F # 編譯器挑選`int`在這點，但它將會調整的型別簽章如果您呼叫`square`與不同輸入類型，例如`float`。

另一個函式， `main`，定義，這以裝飾`EntryPoint`應該那里開始告訴 F # 編譯器執行該程式的屬性。  它會遵循相同的慣例，因此另[c-style 程式設計語言](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)，其中可以傳遞命令列引數，此函式，而將整數傳回碼 (通常`0`)。

它是我們呼叫此函式內`square`函式使用引數`12`。  F # 編譯器然後將指定的型別`square`要`int -> int`(也就是函式會採用`int`，並產生`int`)。  若要呼叫`printfn`是格式化的列印函式以使用格式字串，類似 C 樣式程式設計語言，其對應至格式字串中所指定的參數，然後會列印結果和新行。

## <a name="running-your-code"></a>執行您的程式碼

您可以執行程式碼，並按一下以查看結果**執行**從最上層功能表，然後**啟動但不偵錯**。  這會執行程式，但不偵錯，並可讓您查看結果。

現在，您應該會看到下列列印到主控台視窗的 Visual Studio for Mac 的快顯出來：

```
12 squared is 144!
```

恭喜您！  您 for Mac，然後在 Visual Studio 中建立第一個 F # 專案、 撰寫 F # 函式會列印結果呼叫該函式，並執行專案，請參閱某些結果。

## <a name="using-f-interactive"></a>使用 F # Interactive

其中一個最佳功能中的 Visual F # 工具在 Visual Studio for Mac 是 F # Interactive 視窗。  它可讓您透過的程式碼傳送至處理序，您可以在此呼叫該程式碼，並以互動方式查看結果。

若要開始使用它，反白顯示`square`在您的程式碼中定義的函式。  接下來，按一下**編輯**從最上層功能表。  接下來，選取**將選取範圍傳送至 F # Interactive**。  這在 F # Interactive 視窗中執行程式碼。  或者，您可以在選取範圍上按一下滑鼠右鍵，然後選擇**將選取範圍傳送至 F # Interactive**。  您應該會看到 F # 互動式視窗會出現在它為下列：

```
>

val square : x:int -> int

>
```

這會顯示相同的函式簽章，如`square`函式，這您稍早您停留在函式上時。  因為`square`是定義在 F # 互動式處理序中，現在可以呼叫具有不同值：

```
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

這會執行函式，將結果繫結至新的名稱`it`，並顯示類型和值`it`。  請注意，您必須終止使用的每一行`;;`。  這是如何 F # Interactive 知道您的函式呼叫完成時。  您也可以定義新的函式 F # Interactive 中：

```
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

上述的定義新的函式中， `isOdd`，這個方法會接受`int`和檢查，以查看是否為奇數 ！  您可以呼叫此函式，以查看它以不同的輸入會傳回。  您可以呼叫內函式呼叫的函式：

```
> isOdd (square 15);;
val it : bool = true
```

您也可以使用[順向的管道運算子](../language-reference/symbol-and-operator-reference/index.md)到管線進入兩個函式的值：

```
> 15 |> square |> isOdd;;
val it : bool = true
```

順向的管道運算子和詳細資訊，稍後的教學課程所述。

這是一窺到您可以使用 F # Interactive 執行。  若要進一步了解，請參閱[使用 F # 互動式程式設計](../tutorials/fsharp-interactive/index.md)。

## <a name="next-steps"></a>後續步驟

如果您還沒有這麼做，請參閱[的 F # 教學課程](../tour.md)，其中涵蓋了一些 F # 語言的核心功能。  它會提供一些 F # 的功能的概觀，並提供很大的程式碼範例，您可以複製到 Visual Studio for Mac，並執行。  也有一些絕佳的外部資源，您可以使用，以展示[F # 指南](../index.md)。

## <a name="see-also"></a>另請參閱

- [Visual F#](../index.md)  
- [F# 的教學課程](../tour.md)  
- [F # 語言參考](../language-reference/index.md)  
- [型別推斷](../language-reference/type-inference.md)  
- [符號和運算子參考](../language-reference/symbol-and-operator-reference/index.md)  
