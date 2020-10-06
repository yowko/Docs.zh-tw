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
# <a name="get-started-with-net"></a>開始使用 .NET

本文會教您如何建立及執行「Hello World！」 .NET 應用程式。

如果您不確定什麼是 .NET，請從 [.net 簡介](introduction.md)開始著手。

## <a name="create-an-application"></a>建立應用程式

首先，請在您的電腦上下載並安裝 [.NET SDK](https://dotnet.microsoft.com/download/dotnet-core) 。

接下來，開啟終端機，例如 **PowerShell**、**命令提示字元**或 **bash**。 輸入下列 `dotnet` 命令來建立和執行 c # 應用程式：

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

您看到下列輸出：

```output
Hello World!
```

恭喜！ 您已建立簡單的 .NET 應用程式。

## <a name="next-steps"></a>後續步驟

遵循 [逐步教學](../standard/get-started.md) 課程或在 YouTube 上觀看 [.net 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) 影片，開始開發 .net 應用程式。
