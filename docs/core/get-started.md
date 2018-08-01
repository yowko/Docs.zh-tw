---
title: .NET Core 使用者入門
description: 尋找資源以了解如何在 Windows、Linux 和 macOS 上建置 .NET Core 應用程式。
author: thraka
ms.author: adegeo
ms.date: 06/27/2018
ms.openlocfilehash: fa5deb46b64e1a09c9ad6582486a993a24336b42
ms.sourcegitcommit: 702d5ffc6e733b6c4ded85bf1c92e2293638ee9a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/04/2018
ms.locfileid: "37792396"
---
# <a name="get-started-with-net-core"></a>.NET Core 使用者入門

本文提供 .NET Core 使用者入門的相關資訊。 .NET Core 可以安裝在 Windows、Linux 和 macOS 上。 您可以在慣用的文字編輯器中撰寫程式碼，然後產生跨平台的程式庫和應用程式。 

如果您不確定 .NET Core 為何，或不確定它與其他 .NET 技術的關聯，請從 [What is .NET](https://www.microsoft.com/net/learn/what-is-dotnet) (什麼是 .NET) 概觀開始。 簡單來說，.NET Core 是 .NET 的開放原始碼跨平台實作。

## <a name="create-an-application"></a>建立應用程式

首先，在您的電腦上下載並安裝 [.NET Core SDK](https://www.microsoft.com/net/download/)。

接下來，開啟終端機，例如 **PowerShell**、**命令提示字元**或 **bash**。 鍵入下列 `dotnet` 命令以建立並執行 C# 應用程式。

```console
dotnet new console --output sample1
dotnet run --project sample1
```

您應該會看到下列輸出：

```console
Hello World!
```

恭喜您！ 您已建立簡單的 .NET Core 應用程式。 您也可以使用 [Visual Studio Code](tutorials/with-visual-studio-code.md)、[Visual Studio 2017](tutorials/with-visual-studio.md) (僅限 Windows) 或 [Visual Studio for Mac](tutorials/using-on-mac-vs.md) (僅限 macOS) 來建立 .NET Core 應用程式。

## <a name="tutorials"></a>教學課程

遵循這些逐步教學課程就可以開始開發 .NET Core 應用程式。

# <a name="windowstabwindows"></a>[Windows](#tab/windows)

* [在 Visual Studio 2017 中使用 .NET Core 建置 C# "Hello World" 應用程式。](./tutorials/with-visual-studio.md)

* [在 Visual Studio 2017 中使用 .NET Core 建置 C# 類別庫。](./tutorials/library-with-visual-studio.md)

* [在 Visual Studio 2017 中使用 .NET Core 建置 Visual Basic "Hello World" 應用程式。](./tutorials/vb-with-visual-studio.md)

* [在 Visual Studio 2017 中使用 Visual Basic 和 .NET Core 建置類別庫。](./tutorials/vb-library-with-visual-studio.md)  

* 觀看影片以了解[如何安裝及使用 Visual Studio Code 和 .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/)。

* 觀看影片以了解[如何安裝及使用 Visual Studio 2017 和 .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-Started-NET-Core-Visual-Studio-2017/)。

* [使用命令列開始使用 .NET Core。](tutorials/using-with-xplat-cli.md)

如需支援的 Windows 版本清單，請參閱 [Windows 開發的必要條件](windows-prerequisites.md)一文。

# <a name="linuxtablinux"></a>[Linux](#tab/linux)

遵循這些逐步教學課程就可以開始開發 .NET Core 應用程式。

* [使用命令列開始使用 .NET Core。](tutorials/using-with-xplat-cli.md)

* 觀看影片以了解[使用 C# 和 .NET Core 在 Ubuntu 上開始使用 Visual Studio Code](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu)。

如需支援的 Linux 發行和版本清單，請參閱 [Linux 開發的必要條件](linux-prerequisites.md)一文。

# <a name="macostabmacos"></a>[macOS](#tab/macos)

遵循這些逐步教學課程就可以開始開發 .NET Core 應用程式。

* 觀看影片以了解[使用 C# 和 .NET Core 在 macOS 上開始使用 Visual Studio Code](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac)。

* [使用 Visual Studio Code 在 macOS 上開始使用 .NET Core。](tutorials/using-on-macos.md)

* [使用命令列開始使用 .NET Core。](tutorials/using-with-xplat-cli.md)

* [使用 Visual Studio for Mac 在 macOS 上開始使用 .NET Core。](tutorials/using-on-mac-vs.md)

* [使用 Visual Studio for Mac 在 macOS 上建置完整的 .NET Core 方案。](tutorials/using-on-mac-vs-full-solution.md)

如需支援的 OS X/macOS 版本清單，請參閱 [macOS 開發的必要條件](macos-prerequisites.md)一文。

***