---
title: 開始使用F# Visual Studio
description: 瞭解如何搭配 Visual Studio F#使用。
ms.date: 12/20/2019
ms.openlocfilehash: 9bf47fb08ea3df0aa0d5064043d94f030d45d568
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337339"
---
# <a name="get-started-with-f-in-visual-studio"></a>開始使用F# Visual Studio

F#Visual Studio 的集成F#開發環境（IDE）支援和視覺化檢視。

若要開始，請確定您已[安裝具有F#支援的 Visual Studio](install-fsharp.md#install-f-with-visual-studio)。

## <a name="create-a-console-application"></a>建立主控台應用程式

Visual Studio 中最基本的專案之一，就是主控台應用程式。 以下是建立伺服器的方式：

1. 開啟 Visual Studio 2019。

2. 在開始視窗中，選擇 [建立新專案]。

3. 在 [**建立新專案**] 頁面上， **F#** 從 [語言] 清單中選擇。

4. 選擇 [**主控台應用程式（.Net Core）** ] 範本，然後選擇 [**下一步]** 。

5. 在 [**設定您的新專案**] 頁面的 [**專案名稱**] 方塊中，輸入名稱。 接著，選擇 [建立]。

   Visual Studio 會建立新F#的專案。 您可以在 [方案總管] 視窗中看到它。

## <a name="write-the-code"></a>撰寫程式碼

讓我們開始撰寫一些程式碼。 請確定 `Program.fs` 檔案已開啟，然後以下列內容取代其內容：

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

先前的程式碼範例會定義名為 `square` 的函式，以接受名為 `x` 的輸入，並將其與本身相乘。 因為F#使用[型別推斷](../language-reference/type-inference.md)，所以不需要指定 `x` 的類型。 F#編譯器會瞭解乘法的有效類型，並根據呼叫 `square` 的方式，將類型指派給 `x`。 如果您將滑鼠停留在 `square`上，您應該會看到下列內容：

```fsharp
val square: x:int -> int
```

這就是所謂的函式型別簽章。 它可以讀取如下：「方形是一個函式，它會採用名為 x 的整數，並產生一個整數」。 編譯器現在提供 `square` 的 `int` 類型;這是因為乘法不是*所有*類型的泛型，而是一組封閉的類型。 如果F#您使用不同的輸入類型（例如 `float`）來呼叫 `square`，編譯器會調整類型簽章。

已定義另一個函式 `main`，該函式會以 `EntryPoint` 屬性裝飾。 這個屬性會告知F#編譯器應該在該處啟動程式執行。 其遵循與其他[C 樣式程式語言](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)相同的慣例，其中命令列引數可傳遞給此函式，並傳回整數代碼（通常 `0`）。

它位於進入點函式 `main`中，您可以使用 `12`的引數呼叫 `square` 函數。 然後F#編譯器會指派要 `int -> int` 的 `square` 類型（也就是接受 `int` 並產生 `int`的函式）。 `printfn` 的呼叫是格式化的列印函式，它會使用格式字串並列印結果（和新的一行）。 格式字串與 C 樣式的程式設計語言類似，其參數（`%d`）會對應至傳遞給它的引數，在此案例中為 `12` 和 `(square 12)`。

## <a name="run-the-code"></a>執行程式碼

您可以按**Ctrl**+**F5**來執行程式碼並查看結果。 或者，您可以從最上層功能表列選擇 [ **Debug** ] > [**啟動但不進行調試**]。 這會執行程式而不進行偵測。

下列輸出會列印到 Visual Studio 開啟的主控台視窗：

```console
12 squared is: 144!
```

恭喜您！ 您已在 Visual Studio 中F#建立第一個專案，並F#撰寫一個可計算和列印值的函式，然後執行專案來查看結果。

## <a name="next-steps"></a>後續步驟

如果您還沒有這麼做，請參閱的[導覽F# ](../tour.md)，其中涵蓋了F#語言的一些核心功能。 其中提供一些功能的F#總覽，以及您可以複製到 Visual Studio 和執行的大量程式碼範例。

> [!div class="nextstepaction"]
> [F# 的教學課程](../tour.md)

## <a name="see-also"></a>請參閱

- [F#語言參考](../language-reference/index.md)
- [型別推斷](../language-reference/type-inference.md)
- [符號和運算子參考](../language-reference/symbol-and-operator-reference/index.md)
