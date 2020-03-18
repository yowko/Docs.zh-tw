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
# <a name="net-core-managed-debuggers"></a><span data-ttu-id="523c3-103">.NET 核心託管調試器</span><span class="sxs-lookup"><span data-stu-id="523c3-103">.NET Core managed debuggers</span></span>

<span data-ttu-id="523c3-104">調試器允許逐步暫停或執行程式。</span><span class="sxs-lookup"><span data-stu-id="523c3-104">Debuggers allow programs to be paused or executed step-by-step.</span></span> <span data-ttu-id="523c3-105">暫停後，可以查看進程的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="523c3-105">When paused, the current state of the process can be viewed.</span></span> <span data-ttu-id="523c3-106">通過單一步驟關鍵區段，您可以瞭解代碼及其產生結果的原因。</span><span class="sxs-lookup"><span data-stu-id="523c3-106">By stepping through key sections, you gain understanding of your code and why it produces the result that it does.</span></span>

<span data-ttu-id="523c3-107">微軟在**視覺化工作室**和**視覺化工作室代碼**中為託管代碼提供調試器。</span><span class="sxs-lookup"><span data-stu-id="523c3-107">Microsoft provides debuggers for managed code in **Visual Studio** and **Visual Studio Code**.</span></span>

## <a name="visual-studio-managed-debugger"></a><span data-ttu-id="523c3-108">視覺化工作室託管調試器</span><span class="sxs-lookup"><span data-stu-id="523c3-108">Visual Studio managed debugger</span></span>

<span data-ttu-id="523c3-109">**Visual Studio**是一個集成的開發環境，具有最全面的調試器。</span><span class="sxs-lookup"><span data-stu-id="523c3-109">**Visual Studio** is an integrated development environment with the most comprehensive debugger available.</span></span> <span data-ttu-id="523c3-110">對於在 Windows 上工作的開發人員來說，視覺化工作室是一個很好的選擇。</span><span class="sxs-lookup"><span data-stu-id="523c3-110">Visual Studio is an excellent choice for developers working on Windows.</span></span>

- [<span data-ttu-id="523c3-111">教程 - 使用視覺化工作室在 Windows 上調試 .NET 核心應用程式</span><span class="sxs-lookup"><span data-stu-id="523c3-111">Tutorial - Debugging a .NET Core application on Windows with Visual Studio</span></span>](../tutorials/debugging-with-visual-studio.md)

<span data-ttu-id="523c3-112">雖然 Visual Studio 是 Windows 應用程式，但它仍可用於遠端偵錯 Linux 和 macOS 應用程式。</span><span class="sxs-lookup"><span data-stu-id="523c3-112">While Visual Studio is a Windows application, it can still be used to debug Linux and macOS apps remotely.</span></span>

- [<span data-ttu-id="523c3-113">使用視覺化工作室在 Linux/OSX 上調試 .NET 核心應用程式</span><span class="sxs-lookup"><span data-stu-id="523c3-113">Debugging a .NET Core application on Linux/OSX with Visual Studio</span></span>](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio)

 <span data-ttu-id="523c3-114">調試ASP.NET核心應用需要略有不同的說明。</span><span class="sxs-lookup"><span data-stu-id="523c3-114">Debugging ASP.NET Core apps require slightly different instructions.</span></span>

- [<span data-ttu-id="523c3-115">在視覺化工作室中調試ASP.NET核心應用</span><span class="sxs-lookup"><span data-stu-id="523c3-115">Debug ASP.NET Core apps in Visual Studio</span></span>](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications#debug-aspnet-core-apps)

## <a name="visual-studio-code-managed-debugger"></a><span data-ttu-id="523c3-116">視覺化工作室代碼託管調試器</span><span class="sxs-lookup"><span data-stu-id="523c3-116">Visual Studio Code managed debugger</span></span>

<span data-ttu-id="523c3-117">**視覺化工作室代碼**是一個羽量級的跨平臺代碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="523c3-117">**Visual Studio Code** is a lightweight cross-platform code editor.</span></span> <span data-ttu-id="523c3-118">它使用與 Visual Studio 相同的 .NET Core 調試器實現，但使用者介面簡化。</span><span class="sxs-lookup"><span data-stu-id="523c3-118">It uses the same .NET Core debugger implementation as Visual Studio, but with a simplified user interface.</span></span>

- [<span data-ttu-id="523c3-119">教程 - 使用視覺化工作室代碼調試 .NET 核心應用程式</span><span class="sxs-lookup"><span data-stu-id="523c3-119">Tutorial - Debugging a .NET Core application with Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md#debug)
- [<span data-ttu-id="523c3-120">在 Visual Studio Code 中偵錯</span><span class="sxs-lookup"><span data-stu-id="523c3-120">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/docs/editor/debugging)
