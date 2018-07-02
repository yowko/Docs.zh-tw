---
title: dotnet sln 命令 - .NET Core CLI
description: dotnet-sln 命令提供方便在方案檔中新增、移除及列出專案的選項。
author: mairaw
ms.author: mairaw
ms.date: 06/13/2018
ms.openlocfilehash: 65ae402ef5519863886c8cf833598f5314b4bdad
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207772"
---
# <a name="dotnet-sln"></a>dotnet sln

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>名稱

`dotnet sln` - 修改.NET Core 方案檔。

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

若要使用 `dotnet sln` 命令，方案檔必須已經存在。 如果您需要建立一個，請使用 [dotnet new](dotnet-new.md) 命令，如下列範例：

```
dotnet new sln
```

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
