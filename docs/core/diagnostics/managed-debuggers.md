---
title: 受控偵錯工具-.NET Core
description: 概述 Visual Studio 和 Visual Studio Code 受控偵錯工具。
ms.date: 08/05/2019
ms.openlocfilehash: 28cc21980bc78234f7af3b4668e2fa77fbf8ce5b
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2020
ms.locfileid: "84200866"
---
# <a name="net-core-managed-debuggers"></a>.NET Core 受控偵錯工具

偵錯工具可以逐步暫停或執行程式。 暫停時，可以查看進程的目前狀態。 藉由逐步執行主要章節，您可以瞭解您的程式碼及其產生結果的原因。

Microsoft 會在**Visual Studio**和**Visual Studio Code**中提供受控碼的偵錯工具。

## <a name="visual-studio-managed-debugger"></a>Visual Studio managed 偵錯工具

**Visual Studio**是一個整合式開發環境，其中提供最完整的偵錯工具。 對於在 Windows 上工作的開發人員而言，Visual Studio 是絕佳的選擇。

- [教學課程-使用 Visual Studio 在 Windows 上調試 .NET Core 應用程式](../tutorials/debugging-with-visual-studio.md)

雖然 Visual Studio 是 Windows 應用程式，但仍可用於從遠端對 Linux 和 macOS 應用程式進行偵錯工具。

- [在 Linux/OSX 上使用 Visual Studio 來進行 .NET Core 應用程式的偵錯工具](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio)

 ASP.NET Core 應用程式的偵錯工具需要稍微不同的指示。

- [Visual Studio 中的 Debug ASP.NET Core 應用程式](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications#debug-aspnet-core-apps)

## <a name="visual-studio-code-managed-debugger"></a>Visual Studio Code managed 偵錯工具

**Visual Studio Code**是輕量的跨平臺程式碼編輯器。 它使用與 Visual Studio 相同的 .NET Core 偵錯工具實作為，但使用簡化的使用者介面。

- [教學課程-使用 Visual Studio Code 來調試 .NET Core 應用程式](../tutorials/debugging-with-visual-studio-code.md)
- [在 Visual Studio Code 中偵錯](https://code.visualstudio.com/docs/editor/debugging)
