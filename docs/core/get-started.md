---
title: .NET Core 使用者入門
description: 查找資源以瞭解如何在 Windows、Linux 和 macOS 上構建 .NET 核心應用程式。
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 0968d9db1dbfbdc8c586328ee8e02315f17950b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714386"
---
# <a name="get-started-with-net-core"></a>.NET Core 使用者入門

本文提供 .NET Core 使用者入門的相關資訊。 .NET Core 可以安裝在 Windows、Linux 和 macOS 上。 您可以在慣用的文字編輯器中撰寫程式碼，然後產生跨平台的程式庫和應用程式。

如果您不確定 .NET Core 為何，或不確定它與其他 .NET 技術的關聯，請從 [What is .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) (什麼是 .NET) 概觀開始。 簡單來說，.NET Core 是 .NET 的開放原始碼跨平台實作。

## <a name="create-an-application"></a>建立應用程式

首先，在您的電腦上下載並安裝 [.NET Core SDK](https://dotnet.microsoft.com/download)。

接下來，開啟終端機，例如 **PowerShell**、**命令提示字元**或 **bash**。 鍵入以下`dotnet`命令以創建和運行 C# 應用程式：

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

您應該會看見下列輸出：

```console
Hello World!
```

恭喜！ 您已建立簡單的 .NET Core 應用程式。 您也可以使用 [Visual Studio Code](./tutorials/with-visual-studio-code.md)、[Visual Studio](./tutorials/with-visual-studio.md) (僅限 Windows) 或 [Visual Studio for Mac](./tutorials/using-on-mac-vs.md) (僅限 macOS) 建立 .NET Core 應用程式。

## <a name="tutorials"></a>教學課程

通過按照以下分步教程開始開發 .NET Core 應用程式：

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[Windows](#tab/windows)

- [在 Visual Studio 2019 中創建您的第一個 .NET 核心主控台應用程式](./tutorials/with-visual-studio.md)
- [在視覺化工作室中使用 .NET 標準構建類庫](./tutorials/library-with-visual-studio.md)
- [使用 .NET 核心 CLI 開始使用 .NET 核心](./tutorials/cli-create-console-app.md)

|   |   |
|---|---|
| ![影片的電影攝影機圖示](./media/video-icon.png "觀看影片") | 觀看如何在第 9 頻道[上安裝和使用 Visual Studio 代碼和 .NET 核心](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/)視頻。 |
| ![影片的電影攝影機圖示](./media/video-icon.png "觀看影片") | 在 YouTube 上觀看[.NET 核心 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80)視頻。 |

有關受支援的 Windows 版本的清單，請參閱[.NET Core 依賴項和要求](install/dependencies.md?pivots=os-windows)文章。

# <a name="linux"></a>[Linux](#tab/linux)

通過按照以下分步教程開始開發 .NET Core 應用程式：

- [使用 命令列開始使用 .NET 核心](./tutorials/cli-create-console-app.md)

|   |   |
|---|---|
| ![影片的電影攝影機圖示](./media/video-icon.png "觀看影片") | 觀看影片以了解[使用 C# 和 .NET Core 在 Ubuntu 上開始使用 Visual Studio Code](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu)。 |

有關支援的 Linux 發行版本和版本的清單，請參閱[.NET Core 依賴項和要求](install/dependencies.md?pivots=os-linux)文章。

# <a name="macos"></a>[macOS](#tab/macos)

通過按照以下分步教程開始開發 .NET Core 應用程式：

- [使用 Visual Studio Code 在 macOS 上開始使用 .NET Core](./tutorials/using-on-macos.md)
- [使用命令列開始使用 .NET 核心](./tutorials/cli-create-console-app.md)
- [使用 Visual Studio for Mac 在 macOS 上開始使用 .NET Core](./tutorials/using-on-mac-vs.md)
- [使用 Mac 視覺化工作室在 macOS 上構建完整的 .NET 核心解決方案](./tutorials/using-on-mac-vs-full-solution.md)

|   |   |
|---|---|
| ![影片的電影攝影機圖示](media/video-icon.png "觀看影片") | 觀看[macOS 上使用 C# 和 .NET Core 開始使用 Visual Studio 代碼](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac)的視頻。 |

有關支援的 OS X/ macOS 版本的清單，請參閱[.NET Core 依賴項和要求](install/dependencies.md?pivots=os-macos)文章。

---
