---
title: .NET Core 使用者入門
description: 尋找資源以瞭解如何在 Windows、Linux 和 macOS 上建立 .NET Core 應用程式。
author: adegeo
ms.author: adegeo
ms.date: 12/03/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 56eebc0fc5bad6f57d93358cbbef389d6355d66b
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656686"
---
# <a name="get-started-with-net-core"></a>.NET Core 使用者入門

本文提供 .NET Core 使用者入門的相關資訊。 .NET Core 可以安裝在 Windows、Linux 和 macOS 上。 您可以在慣用的文字編輯器中撰寫程式碼，然後產生跨平台的程式庫和應用程式。

如果您不確定什麼是 .NET Core 或與其他 .NET 技術有何關聯，請從 [什麼是 .net](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) 總覽著手。 簡單來說，.NET Core 是 .NET 的開放原始碼跨平台實作。

## <a name="create-an-application"></a>建立應用程式

首先，在您的電腦上下載並安裝 [.NET Core SDK](https://dotnet.microsoft.com/download)。

接下來，開啟終端機，例如 **PowerShell**、**命令提示字元**或 **bash**。 輸入下列 `dotnet` 命令來建立和執行 c # 應用程式：

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

您應該會看見下列輸出：

```console
Hello World!
```

恭喜！ 您已建立簡單的 .NET Core 應用程式。 您也可以使用 [Visual Studio Code](./tutorials/with-visual-studio-code.md)、[Visual Studio](./tutorials/with-visual-studio.md) (僅限 Windows) 或 [Visual Studio for Mac](tutorials/with-visual-studio-mac.md) (僅限 macOS) 建立 .NET Core 應用程式。

## <a name="tutorials"></a>教學課程

遵循下列逐步教學課程，開始開發 .NET Core 應用程式：

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[Windows](#tab/windows)

- [在 Visual Studio 2019 中建立您的第一個 .NET Core 主控台應用程式](./tutorials/with-visual-studio.md)
- [在 Visual Studio 中建立具有 .NET Standard 的類別庫](./tutorials/library-with-visual-studio.md)
- [教學課程：使用 Visual Studio Code 建立 .NET Core 主控台應用程式](tutorials/with-visual-studio-code.md)

|   |   |
|---|---|
| ![影片的電影攝影機圖示](./media/video-icon.png "觀看影片") | 觀看 Channel 9 上的 [如何安裝和使用 Visual Studio Code 和 .Net Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/) 影片。 |
| ![影片的電影攝影機圖示](./media/video-icon.png "觀看影片") | 觀看 YouTube 上的 [.Net Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) 影片。 |

如需支援的 Windows 版本清單，請參閱 [.Net Core 相依性和需求](install/dependencies.md?pivots=os-windows) 文章。

# <a name="linux"></a>[Linux](#tab/linux)

遵循下列逐步教學課程，開始開發 .NET Core 應用程式：

- [教學課程：使用 Visual Studio Code 建立 .NET Core 主控台應用程式](tutorials/with-visual-studio-code.md)

|   |   |
|---|---|
| ![影片的電影攝影機圖示](./media/video-icon.png "觀看影片") | 觀看影片以了解[使用 C# 和 .NET Core 在 Ubuntu 上開始使用 Visual Studio Code](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu)。 |

如需支援的 Linux 散發版本和版本清單，請參閱 [.Net Core 相依性和需求](install/dependencies.md?pivots=os-linux) 文章。

# <a name="macos"></a>[macOS](#tab/macos)

遵循下列逐步教學課程，開始開發 .NET Core 應用程式：

- [教學課程：使用 Visual Studio Code 建立 .NET Core 主控台應用程式](tutorials/with-visual-studio-code.md)
- [教學課程：使用 Visual Studio for Mac 建立 .NET Core 主控台應用程式](tutorials/with-visual-studio-mac.md)
- [使用 Visual Studio for Mac 在 macOS 上建立 .NET Standard 程式庫](tutorials/library-with-visual-studio-mac.md)

|   |   |
|---|---|
| ![影片的電影攝影機圖示](media/video-icon.png "觀看影片") | 觀看在 macOS 上 [使用 c # 和 .Net Core 開始使用 Visual Studio Code](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac)的影片。 |

請參閱 [.Net Core 相依性和需求](install/dependencies.md?pivots=os-macos) 一文，以取得支援的 OS X/macOS 版本清單。

---
