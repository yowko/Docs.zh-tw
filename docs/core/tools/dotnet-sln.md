---
title: dotnet sln 命令
description: dotnet-sln 命令提供方便在方案檔中新增、移除及列出專案的選項。
ms.date: 06/13/2018
ms.openlocfilehash: a88e22c68f639f2a42e59f9a271e431f04e24a2b
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169140"
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

## <a name="description"></a>說明

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

> [!NOTE]
> 萬用字元不是 CLI 功能，而是命令殼層的功能。 若要成功擴充檔案，您必須使用支援萬用字元的殼層。 如需萬用字元的詳細資訊，請參閱[維基百科](https://en.wikipedia.org/wiki/Glob_(programming)) \(英文\)。
