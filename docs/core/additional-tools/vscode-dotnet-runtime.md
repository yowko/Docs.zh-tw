---
title: 適用于 VS Code 擴充功能作者的 .NET 安裝工具
description: 概述擴充功能作者的 .NET 安裝工具，這是安裝 .NET 執行時間的 Visual Studio Code 延伸模組。
author: sfoslund
ms.date: 11/18/2020
ms.openlocfilehash: 37be1b9dcdb9fba99554800fea23f28443efb5fa
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599909"
---
# <a name="net-install-tool-for-extension-authors"></a>延伸模組作者的 .NET 安裝工具

[延伸模組作者的 .net 安裝工具](https://github.com/dotnet/vscode-dotnet-runtime)是 Visual Studio Code 的延伸模組，可讓您專門針對 VS Code 延伸模組作者取得 .net 執行時間。 這項工具的目的是要用於以 .NET 撰寫的延伸模組，並要求使用 .NET 來啟動延伸模組 (例如，語言伺服器) 。 延伸模組不能直接供使用者用來安裝 .NET 進行開發。

## <a name="getting-started-extension-authors"></a>使用者入門：延伸模組作者

若要確保延伸模組作者的 .NET 安裝工具適合您的案例，請先在 GitHub 頁面上查看 [此延伸](https://github.com/dotnet/vscode-dotnet-runtime#goals-acquiring-net-core-for-extensions) 模組的目標。

> [!NOTE]
> 此工具只能用來安裝 .NET 執行時間，但目前並沒有安裝 .NET SDK 的功能。

確認延伸模組作者的 .NET 安裝工具符合您的需求之後，您就可以在 [擴充功能資訊清單](https://code.visualstudio.com/api/references/extension-manifest) 中相依于它，並開始使用我們使用 [VS Code API](https://code.visualstudio.com/api/extension-guides/command#programmatically-executing-a-command)所公開的命令。 您可以在 [GitHub](https://github.com/dotnet/vscode-dotnet-runtime/blob/master/Documentation/commands.md)上找到此延伸模組所公開的命令清單。

請參閱此 [範例延伸](https://github.com/dotnet/vscode-dotnet-runtime/tree/master/sample) 模組，以瞭解這些步驟的運作方式。

如需更多範例，請參閱目前利用此工具的開放原始碼延伸模組：

- [適用于 Visual Studio Code 的 Azure Resource Manager (ARM) 工具](https://github.com/microsoft/vscode-azurearmtools)

- [.NET 互動式筆記本](https://github.com/dotnet/interactive/tree/main/src/dotnet-interactive-vscode)

## <a name="getting-started-end-users"></a>使用者入門：終端使用者

一般情況下，終端使用者應該完全不需要與 .NET 安裝工具互動以進行延伸模組作者。 如果您遇到延伸模組的問題，請查看我們的 [疑難排解頁面](https://github.com/dotnet/vscode-dotnet-runtime/blob/master/Documentation/troubleshooting.md) ，或在 [GitHub](https://github.com/dotnet/vscode-dotnet-runtime/issues)上提出問題。
