---
title: C# 程式結構 - C# 語言教學課程
description: 了解 C# 程式的基本建置區塊
ms.date: 02/25/2020
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: c0a4dcaed7b53a7da7008d6000b3bec2ffe3ee7b
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141017"
---
# <a name="program-structure"></a>程式結構

C# 語言的重要組織概念如下：程式******、命名空間******、型別******、成員****** 及組件******。 C# 程式包含一個或多個原始程式檔。 程式宣告型別，其中包含成員並可以依據命名空間分組。 類別和介面都是型別的範例。 欄位、方法、屬性及事件都是成員的範例。 編譯 c # 程式時，它們會實際封裝到元件中。 組件通常具有副檔名 `.exe` 或 `.dll`，其分別在於實作「應用程式」****** 或「程式庫」******。

您可以使用`dotnet new`命令來建立名為*acme*的程式庫專案：

```dotnetcli
dotnet new classlib -o acme
```

在該專案中，在名`Stack` `Acme.Collections`為的命名空間中宣告名為的類別：

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

此類別的完整名稱是 `Acme.Collections.Stack`。 該類別包含數個成員︰一個名為 `top` 的欄位、兩個名為 `Push` 和 `Pop` 的方法以及名為 `Entry` 的巢狀類別。 `Entry` 類別更包含三個成員︰一個名為 `next` 的欄位、一個名為 `data` 的欄位以及建構函式。 命令：

```dotnetcli
dotnet build
```

會將範例編譯為程式庫 (不需要 `Main` 進入點的程式碼)，並產生名為 `acme.dll` 的組件。

組件包含的可執行程式碼採用中繼語言 (IL) 指令形式，而符號資訊採用中繼資料形式。 在執行之前，.NET 通用語言執行平臺的即時（JIT）編譯器會將元件中的 IL 程式碼轉換成處理器特定程式碼。

由於元件是包含程式碼和中繼資料的自我描述功能單位，因此 c # 中不需要`#include`指示詞和標頭檔。 特定組件中所包含的公用型別和成員只能在編譯程式時，使用 C# 程式來參考該組件。 例如，此程式使用來自 `acme.dll` 組件的 `Acme.Collections.Stack` 類別︰

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

前述程式專案的 *.csproj*檔案必須包含 c # 編譯器的參考節點，才能解析`acme.dll`元件中類別的參考：

```xml
  <ItemGroup>
    <ProjectReference Include="..\acme\acme.csproj" />
  </ItemGroup>
```

在該新增之後`dotnet build` ，會建立名為`example.exe`的可執行元件，在執行時，會產生輸出：

```dotnetcli
100
10
1
```

C# 允許以數個原始程式檔儲存程式的原始程式文字。 編譯有多檔案的 C# 程式時，所有原始程式檔都會一起處理，而原始程式檔可以隨意地互相參考。概念上，就如同將所有原始程式檔都串連成一個大型檔案，然後再進行處理。 C # 中永遠不需要向前宣告，因為只有少數例外狀況，宣告順序並不重要。 C# 不會限制原始程式檔只能宣告一個公用型別，也不會要求原始程式檔符合原始程式檔中所宣告的型別名稱。

>[!div class="step-by-step"]
>[上一頁](index.md)
>[下一頁](types-and-variables.md)
