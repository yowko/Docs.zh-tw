---
title: "字串插補 - C#"
description: "了解字串插補在 C# 6 中如何運作"
keywords: ".NET, .NET Core, C#, 字串"
author: mgroves
ms.author: wiwagn
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: f8806f6b-3ac7-4ee6-9b3e-c524d5301ae9
ms.openlocfilehash: b6b3ce53a08cfacfacb19266b0be216a40633352
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="string-interpolation-in-c"></a>C# 中的字串插值 #

「字串插補」是以字串變數的值取代字串中預留位置的方式。 在 C# 6 之前，是透過 `System.String.Format` 來執行這項操作。 這個運作方式還行，但由於它使用已編號的預留位置，因此更難以閱讀也更冗長。

其他程式設計語言已經在語言中內建字串插補有一段時間。 例如，在 PHP 中：

```php
$name = "Jonas";
echo "My name is $name.";
// This will output "My name is Jonas."
```

在 C# 6 中，我們終於也有該樣式的字串插補。 您可以在字串前使用 `$` 來指出它應該以變數/運算式來替代其值。

## <a name="prerequisites"></a>必要條件
您將必須設定電腦以執行 .NET Core。 您可以在 [.NET Core (英文)](https://www.microsoft.com/net/core) 頁面找到安裝指示。
您可以在 Windows、Ubuntu Linux、macOS 或是 Docker 容器中執行此應用程式。 您將必須安裝慣用的程式碼編輯器。 以下說明使用 [Visual Studio Code (英文)](https://code.visualstudio.com/)，這是開放原始碼的跨平台編輯器。 不過，您可以使用您熟悉的任何工具。

## <a name="create-the-application"></a>建立應用程式

現在您已安裝完所有工具，請建立新的 .NET Core 應用程式。 若要使用命令列產生器，請為您的專案建立一個目錄 (例如 `interpolated`)，然後在您慣用的殼層中執行下列命令︰

```
dotnet new console
```

此命令會建立一個含有 *interpolated.csproj* 專案檔和 *Program.cs* 原始程式碼檔案的陽春型 .NET Core 專案。 您將必須執行 `dotnet restore` 以還原編譯此專案所需的相依性。

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

若要執行這個程式，請使用 `dotnet run`。 您應該會在主控台看到 "Hello, World" 輸出。



## <a name="intro-to-string-interpolation"></a>字串插補簡介

使用 `System.String.Format` 時，您需指定要由字串後的參數取代的字串中「預留位置」。 若是執行個體：

[!code-csharp[String.Format example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#StringFormatExample)]  

此範例將會輸出 "My name is Matt Groves"。

在 C# 6 中，您將不使用 `String.Format`，而是藉由在插補字串前加上 `$` 符號，然後直接在該字串中使用變數，來定義插捕字串。 若是執行個體：

[!code-csharp[Interpolation example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationExample)]  

您不必只使用變數。 您可以在括弧內使用任何運算式。 若是執行個體：

[!code-csharp[Interpolation expression example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationExpressionExample)]  

這會輸出：

```
This is line number 1
This is line number 2
This is line number 3
This is line number 4
This is line number 5
```

## <a name="how-string-interpolation-works"></a>字串插補如何運作

在幕後，會由編譯器將這個字串插補轉譯成 String.Format。 因此，您可以執行[之前對 String.Format 所進行的相同型別操作](https://msdn.microsoft.com/library/dwhawy9k(v=vs.110).aspx)。

例如，您可以新增填補和設定數字格式：

[!code-csharp[Interpolation formatting example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationFormattingExample)]  

上述範例會產生類似以下的輸出：

```
998        5,177.67
999        6,719.30
1000       9,910.61
1001       529.34
1002       1,349.86
1003       2,660.82
1004       6,227.77
```

如果找不到變數名稱，則會產生編譯階段錯誤。

若是執行個體：

```csharp
var animal = "fox";
var localizeMe = $"The {adj} brown {animal} jumped over the lazy {otheranimal}";
var adj = "quick";
Console.WriteLine(localizeMe);
```

如果編譯它，您將會收到錯誤：
 
* `Cannot use local variable 'adj' before it is declared` - 在插補字串「之後」才宣告 `adj` 變數。
* `The name 'otheranimal' does not exist in the current context` - 從未宣告名為 `otheranimal` 的變數

## <a name="localization-and-internationalization"></a>當地語系化和國際化

插補字串支援 `IFormattable` 和 `FormattableString`，這對國際化相當有用。

插補字串預設會使用目前的文化特性 (Culture)。 若要使用不同的文化特性，您可以將它轉換為 `IFormattable`

若是執行個體：

[!code-csharp[Interpolation internationalization example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationInternationalizationExample)]  

## <a name="conclusion"></a>結論 

在本教學課程中，您已了解如何使用 C# 6 的字串插補功能。 它基本上是一個撰寫簡單 `String.Format` 陳述式的更簡潔方式，但針對較進階的用法有一些注意事項。
