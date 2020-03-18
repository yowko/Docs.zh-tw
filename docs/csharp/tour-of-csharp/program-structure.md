---
title: C# 程式結構 - C# 語言教學課程
description: 了解 C# 程式的基本建置區塊
ms.date: 02/25/2020
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: c09c11a4dd957b29b2adb7aaa8d68a50f30620b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156827"
---
# <a name="program-structure"></a>程式結構

C# 語言的重要組織概念如下：程式******、命名空間******、型別******、成員****** 及組件******。 C# 程式包含一個或多個原始程式檔。 程式宣告型別，其中包含成員並可以依據命名空間分組。 類別和介面都是型別的範例。 欄位、方法、屬性及事件都是成員的範例。 編譯 C# 程式時，它們將物理打包到程式集中。 組件通常具有副檔名 `.exe` 或 `.dll`，其分別在於實作「應用程式」****** 或「程式庫」******。

可以使用 以下命令創建名為*acme*的`dotnet new`庫專案：

```console
dotnet new classlib -o acme
```

在該專案中，聲明命名空間中`Stack`名為 的類： `Acme.Collections`

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

此類別的完整名稱是 `Acme.Collections.Stack`。 該類別包含數個成員︰一個名為 `top` 的欄位、兩個名為 `Push` 和 `Pop` 的方法以及名為 `Entry` 的巢狀類別。 `Entry` 類別更包含三個成員︰一個名為 `next` 的欄位、一個名為 `data` 的欄位以及建構函式。 命令：

```console
dotnet build
```

會將範例編譯為程式庫 (不需要 `Main` 進入點的程式碼)，並產生名為 `acme.dll` 的組件。

組件包含的可執行程式碼採用中繼語言 (IL) 指令形式，而符號資訊採用中繼資料形式。 在執行之前，.NET 通用語言運行時的及時 （JIT） 編譯器將程式集中的 IL 代碼轉換為特定于處理器的代碼。

由於程式集是包含代碼和中繼資料的自描述功能單元，因此不需要 C# 中的`#include`指令和標標頭檔。 特定組件中所包含的公用型別和成員只能在編譯程式時，使用 C# 程式來參考該組件。 例如，此程式使用來自 `acme.dll` 組件的 `Acme.Collections.Stack` 類別︰

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

前一個程式專案的*csproj*檔必須包含 C# 編譯器的引用節點，以解決對程式集中的類的`acme.dll`引用：

```xml
  <ItemGroup>
    <ProjectReference Include="..\acme\acme.csproj" />
  </ItemGroup>
```

添加後，`dotnet build`創建名為 的`example.exe`可執行程式集，該程式集在運行時生成輸出：

```console
100
10
1
```

C# 允許以數個原始程式檔儲存程式的原始程式文字。 編譯有多檔案的 C# 程式時，所有原始程式檔都會一起處理，而原始程式檔可以隨意地互相參考。概念上，就如同將所有原始程式檔都串連成一個大型檔案，然後再進行處理。 C# 中從來不需要轉發聲明，因為除了少數例外情況外，聲明順序微不足道。 C# 不會限制原始程式檔只能宣告一個公用型別，也不會要求原始程式檔符合原始程式檔中所宣告的型別名稱。

>[!div class="step-by-step"]
>[上一個](index.md)
>[下一個](types-and-variables.md)
