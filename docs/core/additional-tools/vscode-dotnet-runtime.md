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
# <a name="net-install-tool-for-extension-authors"></a><span data-ttu-id="6f2c4-103">延伸模組作者的 .NET 安裝工具</span><span class="sxs-lookup"><span data-stu-id="6f2c4-103">.NET install tool for extension authors</span></span>

<span data-ttu-id="6f2c4-104">[延伸模組作者的 .net 安裝工具](https://github.com/dotnet/vscode-dotnet-runtime)是 Visual Studio Code 的延伸模組，可讓您專門針對 VS Code 延伸模組作者取得 .net 執行時間。</span><span class="sxs-lookup"><span data-stu-id="6f2c4-104">The [.NET install tool for extension authors](https://github.com/dotnet/vscode-dotnet-runtime) is a Visual Studio Code extension that allows acquisition of the .NET runtime specifically for VS Code extension authors.</span></span> <span data-ttu-id="6f2c4-105">這項工具的目的是要用於以 .NET 撰寫的延伸模組，並要求使用 .NET 來啟動延伸模組 (例如，語言伺服器) 。</span><span class="sxs-lookup"><span data-stu-id="6f2c4-105">This tool is intended to be leveraged in extensions that are written in .NET and require .NET to boot pieces of the extension (for example, a language server).</span></span> <span data-ttu-id="6f2c4-106">延伸模組不能直接供使用者用來安裝 .NET 進行開發。</span><span class="sxs-lookup"><span data-stu-id="6f2c4-106">The extension is not intended to be used directly by users to install .NET for development.</span></span>

## <a name="getting-started-extension-authors"></a><span data-ttu-id="6f2c4-107">使用者入門：延伸模組作者</span><span class="sxs-lookup"><span data-stu-id="6f2c4-107">Getting started: extension authors</span></span>

<span data-ttu-id="6f2c4-108">若要確保延伸模組作者的 .NET 安裝工具適合您的案例，請先在 GitHub 頁面上查看 [此延伸](https://github.com/dotnet/vscode-dotnet-runtime#goals-acquiring-net-core-for-extensions) 模組的目標。</span><span class="sxs-lookup"><span data-stu-id="6f2c4-108">To ensure that the .NET install tool for extension authors is the right fit for your scenario, start by reviewing the [goals of this extension](https://github.com/dotnet/vscode-dotnet-runtime#goals-acquiring-net-core-for-extensions) on our GitHub page.</span></span>

> [!NOTE]
> <span data-ttu-id="6f2c4-109">此工具只能用來安裝 .NET 執行時間，但目前並沒有安裝 .NET SDK 的功能。</span><span class="sxs-lookup"><span data-stu-id="6f2c4-109">This tool can be used to install the .NET runtime only, it currently does not have the capability to install the .NET SDK.</span></span>

<span data-ttu-id="6f2c4-110">確認延伸模組作者的 .NET 安裝工具符合您的需求之後，您就可以在 [擴充功能資訊清單](https://code.visualstudio.com/api/references/extension-manifest) 中相依于它，並開始使用我們使用 [VS Code API](https://code.visualstudio.com/api/extension-guides/command#programmatically-executing-a-command)所公開的命令。</span><span class="sxs-lookup"><span data-stu-id="6f2c4-110">Once you have verified that the .NET install tool for extension authors fits your needs, you can take a dependency on it in your [extension manifest](https://code.visualstudio.com/api/references/extension-manifest) and begin using the commands we expose with the [VS Code API](https://code.visualstudio.com/api/extension-guides/command#programmatically-executing-a-command).</span></span> <span data-ttu-id="6f2c4-111">您可以在 [GitHub](https://github.com/dotnet/vscode-dotnet-runtime/blob/master/Documentation/commands.md)上找到此延伸模組所公開的命令清單。</span><span class="sxs-lookup"><span data-stu-id="6f2c4-111">You can find the list of commands this extension exposes on our [GitHub](https://github.com/dotnet/vscode-dotnet-runtime/blob/master/Documentation/commands.md).</span></span>

<span data-ttu-id="6f2c4-112">請參閱此 [範例延伸](https://github.com/dotnet/vscode-dotnet-runtime/tree/master/sample) 模組，以瞭解這些步驟的運作方式。</span><span class="sxs-lookup"><span data-stu-id="6f2c4-112">Check out this [sample extension](https://github.com/dotnet/vscode-dotnet-runtime/tree/master/sample) to see these steps in action.</span></span>

<span data-ttu-id="6f2c4-113">如需更多範例，請參閱目前利用此工具的開放原始碼延伸模組：</span><span class="sxs-lookup"><span data-stu-id="6f2c4-113">For more examples, check out these open source extensions that currently leverage this tool:</span></span>

- [<span data-ttu-id="6f2c4-114">適用于 Visual Studio Code 的 Azure Resource Manager (ARM) 工具</span><span class="sxs-lookup"><span data-stu-id="6f2c4-114">Azure Resource Manager (ARM) Tools for Visual Studio Code</span></span>](https://github.com/microsoft/vscode-azurearmtools)

- [<span data-ttu-id="6f2c4-115">.NET 互動式筆記本</span><span class="sxs-lookup"><span data-stu-id="6f2c4-115">.NET Interactive Notebooks</span></span>](https://github.com/dotnet/interactive/tree/main/src/dotnet-interactive-vscode)

## <a name="getting-started-end-users"></a><span data-ttu-id="6f2c4-116">使用者入門：終端使用者</span><span class="sxs-lookup"><span data-stu-id="6f2c4-116">Getting started: end users</span></span>

<span data-ttu-id="6f2c4-117">一般情況下，終端使用者應該完全不需要與 .NET 安裝工具互動以進行延伸模組作者。</span><span class="sxs-lookup"><span data-stu-id="6f2c4-117">In general, the end user should not need to interact with the .NET install tool for extension authors at all.</span></span> <span data-ttu-id="6f2c4-118">如果您遇到延伸模組的問題，請查看我們的 [疑難排解頁面](https://github.com/dotnet/vscode-dotnet-runtime/blob/master/Documentation/troubleshooting.md) ，或在 [GitHub](https://github.com/dotnet/vscode-dotnet-runtime/issues)上提出問題。</span><span class="sxs-lookup"><span data-stu-id="6f2c4-118">If you are having problems with the extension, check out our [troubleshooting page](https://github.com/dotnet/vscode-dotnet-runtime/blob/master/Documentation/troubleshooting.md) or file an issue on our [GitHub](https://github.com/dotnet/vscode-dotnet-runtime/issues).</span></span>
