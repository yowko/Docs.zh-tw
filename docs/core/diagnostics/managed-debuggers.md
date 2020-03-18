---
title: 託管調試器 - .NET 核心
description: 視覺化工作室和視覺化工作室代碼託管調試器的概述。
ms.date: 08/05/2019
ms.openlocfilehash: 065b1b0fc32eb76b398cb3821c8592a1955c9359
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715559"
---
# <a name="net-core-managed-debuggers"></a>.NET 核心託管調試器

調試器允許逐步暫停或執行程式。 暫停後，可以查看進程的目前狀態。 通過單一步驟關鍵區段，您可以瞭解代碼及其產生結果的原因。

微軟在**視覺化工作室**和**視覺化工作室代碼**中為託管代碼提供調試器。

## <a name="visual-studio-managed-debugger"></a>視覺化工作室託管調試器

**Visual Studio**是一個集成的開發環境，具有最全面的調試器。 對於在 Windows 上工作的開發人員來說，視覺化工作室是一個很好的選擇。

- [教程 - 使用視覺化工作室在 Windows 上調試 .NET 核心應用程式](../tutorials/debugging-with-visual-studio.md)

雖然 Visual Studio 是 Windows 應用程式，但它仍可用於遠端偵錯 Linux 和 macOS 應用程式。

- [使用視覺化工作室在 Linux/OSX 上調試 .NET 核心應用程式](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio)

 調試ASP.NET核心應用需要略有不同的說明。

- [在視覺化工作室中調試ASP.NET核心應用](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications#debug-aspnet-core-apps)

## <a name="visual-studio-code-managed-debugger"></a>視覺化工作室代碼託管調試器

**視覺化工作室代碼**是一個羽量級的跨平臺代碼編輯器。 它使用與 Visual Studio 相同的 .NET Core 調試器實現，但使用者介面簡化。

- [教程 - 使用視覺化工作室代碼調試 .NET 核心應用程式](../tutorials/with-visual-studio-code.md#debug)
- [在 Visual Studio Code 中偵錯](https://code.visualstudio.com/docs/editor/debugging)
