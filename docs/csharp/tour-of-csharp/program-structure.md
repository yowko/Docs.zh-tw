---
title: C# 程式結構 - C# 語言教學課程
description: 了解 C# 程式的基本建置區塊
ms.date: 08/10/2016
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: 5102c72d68108f698a0456b9c14e6713778f4325
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834160"
---
# <a name="program-structure"></a>程式結構

C# 語言的重要組織概念如下：程式、命名空間、型別、成員及組件。 C# 程式包含一個或多個原始程式檔。 程式宣告型別，其中包含成員並可以依據命名空間分組。 類別和介面都是型別的範例。 欄位、方法、屬性及事件都是成員的範例。 在編譯 C# 語言時，會將它們實際封裝為組件。 組件通常具有副檔名 `.exe` 或 `.dll`，其分別在於實作「應用程式」或「程式庫」。

此範例會在名為 `Acme.Collections` 的命名空間中，宣告稱為 `Stack` 的類別：

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

此類別的完整名稱是 `Acme.Collections.Stack`。 該類別包含數個成員︰一個名為 `top` 的欄位、兩個名為 `Push` 和 `Pop` 的方法以及名為 `Entry` 的巢狀類別。 `Entry` 類別更包含三個成員︰一個名為 `next` 的欄位、一個名為 `data` 的欄位以及建構函式。 假設此範例的原始程式碼儲存在檔案 `acme.cs`，命令列

```console
csc /t:library acme.cs
```

會將範例編譯為程式庫 (不需要 `Main` 進入點的程式碼)，並產生名為 `acme.dll` 的組件。

> [!IMPORTANT]
> 上述範例使用 `csc` 做為命令列 C# 編譯器。 此編譯器是 Windows 可執行檔。 若要在其他平台上使用 C#，您應該使用 .NET core 的工具。 .NET Core 生態系統會使用 `dotnet` CLI 管理命令列組建。 這包括管理相依性，以及叫用 C# 編譯器。 如需有關 .NET Core 所支援平台上那些工具的完整說明 ，請參閱[本教學課程](../../core/tutorials/using-with-xplat-cli.md)。

組件包含的可執行程式碼採用中繼語言 (IL) 指令形式，而符號資訊採用中繼資料形式。 執行前，組件中的 IL 程式碼會由 .NET 通用語言執行平台的 Just-In-Time (JIT) 編譯器自動轉換為處理器特定程式碼。

由於組件是包含程式碼和中繼資料的功能自我描述單位，所以不需要提供 C# 中的 `#include` 指示詞和標頭檔。 特定組件中所包含的公用型別和成員只能在編譯程式時，使用 C# 程式來參考該組件。 例如，此程式使用來自 `acme.dll` 組件的 `Acme.Collections.Stack` 類別︰

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

如果程式儲存在檔案 `example.cs` 中，編譯 `example.cs` 時，可以使用編譯器的 /r 選項來參考 acme.dll 組件︰

```console
csc /r:acme.dll example.cs
```

這樣會建立名為 `example.exe` 可執行檔組件，執行時會產生以下輸出︰

```console
100
10
1
```

C# 允許以數個原始程式檔儲存程式的原始程式文字。 編譯有多檔案的 C# 程式時，所有原始程式檔都會一起處理，而原始程式檔可以隨意地互相參考。概念上，就如同將所有原始程式檔都串連成一個大型檔案，然後再進行處理。 C# 中不再需要向前宣告，原因是在極少數的例外狀況中，宣告順序並不重要。 C# 不會限制原始程式檔只能宣告一個公用型別，也不會要求原始程式檔符合原始程式檔中所宣告的型別名稱。

>[!div class="step-by-step"]
>[上一頁](index.md)
>[下一頁](types-and-variables.md)
