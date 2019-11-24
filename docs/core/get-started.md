---
title: .NET Core 使用者入門
description: 尋找資源以了解如何在 Windows、Linux 和 macOS 上建置 .NET Core 應用程式。
author: thraka
ms.author: adegeo
ms.date: 09/19/2019
ms.openlocfilehash: 78066f2904f6a874b71165e4fe1769b6b778ae41
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428877"
---
# <a name="get-started-with-net-core"></a>.NET Core 使用者入門

本文提供 .NET Core 使用者入門的相關資訊。 .NET Core 可以安裝在 Windows、Linux 和 macOS 上。 您可以在慣用的文字編輯器中撰寫程式碼，然後產生跨平台的程式庫和應用程式。 

如果您不確定 .NET Core 為何，或不確定它與其他 .NET 技術的關聯，請從 [What is .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) (什麼是 .NET) 概觀開始。 簡單來說，.NET Core 是 .NET 的開放原始碼跨平台實作。

## <a name="create-an-application"></a>建立應用程式

首先，在您的電腦上下載並安裝 [.NET Core SDK](https://dotnet.microsoft.com/download)。

接下來，開啟終端機，例如 **PowerShell**、**命令提示字元**或 **bash**。 Type the following `dotnet` commands to create and run a C# application:

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

您應該會看到下列輸出：

```console
Hello World!
```

恭喜您！ 您已建立簡單的 .NET Core 應用程式。 您也可以使用 [Visual Studio Code](tutorials/with-visual-studio-code.md)、[Visual Studio](tutorials/with-visual-studio.md) (僅限 Windows) 或 [Visual Studio for Mac](tutorials/using-on-mac-vs.md) (僅限 macOS) 建立 .NET Core 應用程式。

## <a name="tutorials"></a>教學課程

遵循這些逐步教學課程就可以開始開發 .NET Core 應用程式。

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[Windows](#tab/windows)

- [在 Visual Studio 2017 中使用 .NET Core 建置 C# "Hello World" 應用程式。](./tutorials/with-visual-studio.md)
- [在 Visual Studio 2017 中使用 .NET Core 建置 C# 類別庫。](./tutorials/library-with-visual-studio.md)
- [在 Visual Studio 2017 中使用 .NET Core 建置 Visual Basic "Hello World" 應用程式。](./tutorials/vb-with-visual-studio.md)
- [在 Visual Studio 2017 中使用 Visual Basic 和 .NET Core 建置類別庫。](./tutorials/vb-library-with-visual-studio.md)  
- 觀看影片以了解[如何安裝及使用 Visual Studio Code 和 .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/)。
- 觀看影片以了解[如何安裝及使用 Visual Studio 2017 和 .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-Started-NET-Core-Visual-Studio-2017/)。
- [使用命令列開始使用 .NET Core。](tutorials/using-with-xplat-cli.md)

See the [.NET Core dependencies and requirements](install/dependencies.md?tabs=netcore30&pivots=os-windows) article for a list of the supported Windows versions.

# <a name="linuxtablinux"></a>[Linux](#tab/linux)

You can get started developing .NET Core application by following these step-by-step tutorials:

- [使用命令列開始使用 .NET Core。](tutorials/using-with-xplat-cli.md)
- 觀看影片以了解[使用 C# 和 .NET Core 在 Ubuntu 上開始使用 Visual Studio Code](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu)。

See the [.NET Core dependencies and requirements](install/dependencies.md?tabs=netcore30&pivots=os-linux) article for a list of the supported Linux distros and versions.

# <a name="macostabmacos"></a>[macOS](#tab/macos)

You can get started developing .NET Core application by following these step-by-step tutorials:

- 觀看影片以了解[使用 C# 和 .NET Core 在 macOS 上開始使用 Visual Studio Code](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac)。
- [使用 Visual Studio Code 在 macOS 上開始使用 .NET Core。](tutorials/using-on-macos.md)
- [使用命令列開始使用 .NET Core。](tutorials/using-with-xplat-cli.md)
- [使用 Visual Studio for Mac 在 macOS 上開始使用 .NET Core。](tutorials/using-on-mac-vs.md)
- [使用 Visual Studio for Mac 在 macOS 上建置完整的 .NET Core 方案。](tutorials/using-on-mac-vs-full-solution.md)

See the [.NET Core dependencies and requirements](install/dependencies.md?tabs=netcore30&pivots=os-macos) article for a list of the supported OS X / macOS versions.

---
