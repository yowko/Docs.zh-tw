---
title: 開始使用 .NET
description: 建立 Hello World .NET 應用程式。
author: adegeo
ms.author: adegeo
ms.date: 09/29/2020
ms.custom: vs-dotnet
ms.openlocfilehash: 6ad2b96e668c52ee80b707e31a63eac2433f3c9e
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2020
ms.locfileid: "91756087"
---
# <a name="get-started-with-net"></a><span data-ttu-id="0d4ad-103">開始使用 .NET</span><span class="sxs-lookup"><span data-stu-id="0d4ad-103">Get started with .NET</span></span>

<span data-ttu-id="0d4ad-104">本文會教您如何建立及執行「Hello World！」</span><span class="sxs-lookup"><span data-stu-id="0d4ad-104">This article teaches you how to create and run a "Hello World!"</span></span> <span data-ttu-id="0d4ad-105">.NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="0d4ad-105">.NET app.</span></span>

<span data-ttu-id="0d4ad-106">如果您不確定什麼是 .NET，請從 [.net 簡介](introduction.md)開始著手。</span><span class="sxs-lookup"><span data-stu-id="0d4ad-106">If you're unsure what .NET is, start with the [.NET introduction](introduction.md).</span></span>

## <a name="create-an-application"></a><span data-ttu-id="0d4ad-107">建立應用程式</span><span class="sxs-lookup"><span data-stu-id="0d4ad-107">Create an application</span></span>

<span data-ttu-id="0d4ad-108">首先，請在您的電腦上下載並安裝 [.NET SDK](https://dotnet.microsoft.com/download/dotnet-core) 。</span><span class="sxs-lookup"><span data-stu-id="0d4ad-108">First, download and install the [.NET SDK](https://dotnet.microsoft.com/download/dotnet-core) on your computer.</span></span>

<span data-ttu-id="0d4ad-109">接下來，開啟終端機，例如 **PowerShell**、**命令提示字元**或 **bash**。</span><span class="sxs-lookup"><span data-stu-id="0d4ad-109">Next, open a terminal such as **PowerShell**, **Command Prompt**, or **bash**.</span></span> <span data-ttu-id="0d4ad-110">輸入下列 `dotnet` 命令來建立和執行 c # 應用程式：</span><span class="sxs-lookup"><span data-stu-id="0d4ad-110">Enter the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

<span data-ttu-id="0d4ad-111">您看到下列輸出：</span><span class="sxs-lookup"><span data-stu-id="0d4ad-111">You see the following output:</span></span>

```output
Hello World!
```

<span data-ttu-id="0d4ad-112">恭喜！</span><span class="sxs-lookup"><span data-stu-id="0d4ad-112">Congratulations!</span></span> <span data-ttu-id="0d4ad-113">您已建立簡單的 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="0d4ad-113">You've created a simple .NET application.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0d4ad-114">後續步驟</span><span class="sxs-lookup"><span data-stu-id="0d4ad-114">Next steps</span></span>

<span data-ttu-id="0d4ad-115">遵循 [逐步教學](../standard/get-started.md) 課程或在 YouTube 上觀看 [.net 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) 影片，開始開發 .net 應用程式。</span><span class="sxs-lookup"><span data-stu-id="0d4ad-115">Get started developing .NET applications by following a [step-by-step tutorial](../standard/get-started.md) or by watching [.NET 101 videos](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) on YouTube.</span></span>
