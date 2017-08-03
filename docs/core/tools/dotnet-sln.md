---
title: "dotnet-sln 命令 - .NET Core CLI"
description: "dotnet-sln 命令提供方便在方案檔中新增、移除及列出專案的選項。"
keywords: "dotnet-sln, CLI, CLI 命令, .NET Core"
author: spboyer
ms.author: mairaw
ms.date: 04/11/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: e5a72d3e-c14b-4b0a-a978-c5e54a0988c6
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 606929fbcafddf47abf5da6d3c8ce97d5af06909
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-sln"></a>dotnet-sln

## <a name="name"></a>名稱

`dotnet-sln` - 修改.NET Core 方案檔。

## <a name="synopsis"></a>概要

```
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a>描述

`dotnet sln` 命令提供方便在方案檔中新增、移除及列出專案的方式。

## <a name="commands"></a>命令

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

將一個專案或多個專案加入至方案檔。 以 Unix/Linux 為基礎的終端機上支援 [Globbing 模式 (英文)](https://en.wikipedia.org/wiki/Glob_(programming))。

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

從方案檔中移除一個專案或多個專案。 以 Unix/Linux 為基礎的終端機上支援 [Globbing 模式 (英文)](https://en.wikipedia.org/wiki/Glob_(programming))。

`list`

列出方案檔中的所有專案。

## <a name="arguments"></a>引數

`SOLUTION_NAME`

要使用的方案檔。 如果未指定，命令會在目前的目錄中搜尋一個專案檔。 如果目錄中有多個方案檔，請務必指定一個方案檔。

## <a name="options"></a>選項

`-h|--help`

印出命令的簡短說明。

## <a name="examples"></a>範例

將 C# 專案新增至方案：

`dotnet sln todo.sln add todo-app/todo-app.csproj`

移除方案中的 C# 專案：

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

將多個 C# 專案新增至方案：

`dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj`

從方案中移除多個 C# 專案：

`dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj`

使用 Glob 模式將多個 C# 專案新增至方案：

`dotnet sln todo.sln add **/*.csproj`

使用 Glob 模式從方案中移除多個 C# 專案：

`dotnet sln todo.sln remove **/*.csproj`

