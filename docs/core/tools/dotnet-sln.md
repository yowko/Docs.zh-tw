---
title: dotnet sln 命令
description: dotnet-sln 命令提供方便在方案檔中新增、移除及列出專案的選項。
ms.date: 02/14/2020
ms.openlocfilehash: 898c53772a28b8cc3b65532dfc3d9bd6e73d467c
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634366"
---
# <a name="dotnet-sln"></a>dotnet sln

本文 **適用于：** ✔️ .net CORE 2.x SDK 和更新版本

## <a name="name"></a>名稱

`dotnet sln` -列出或修改 .NET 方案檔中的專案。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command]

dotnet sln [command] -h|--help
```

## <a name="description"></a>描述

此 `dotnet sln` 命令提供一個便利的方式來列出和修改方案檔中的專案。

若要使用 `dotnet sln` 命令，方案檔必須已經存在。 如果您需要建立一個，請使用 [dotnet new](dotnet-new.md) 命令，如下列範例所示：

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a>引數

- **`SOLUTION_FILE`**

  要使用的方案檔。 如果省略這個引數，則命令會在目前的目錄中搜尋一個。 如果找不到解決方案檔或多個方案檔，則命令會失敗。

## <a name="options"></a>選項

- **`-h|--help`**

  印出如何使用命令的描述。

## <a name="commands"></a>命令

### `list`

列出方案檔中的所有專案。

#### <a name="synopsis"></a>概要

```dotnetcli
dotnet sln list [-h|--help]
```

#### <a name="arguments"></a>引數

- **`SOLUTION_FILE`**

  要使用的方案檔。 如果省略這個引數，則命令會在目前的目錄中搜尋一個。 如果找不到解決方案檔或多個方案檔，則命令會失敗。

#### <a name="options"></a>選項

- **`-h|--help`**

  印出如何使用命令的描述。
  
### `add`

將一或多個專案加入至方案檔。

#### <a name="synopsis"></a>概要

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder <PATH>] <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a>引數

- **`SOLUTION_FILE`**

  要使用的方案檔。 如果未指定，命令會在目前的目錄中搜尋一個目錄，如果有多個方案檔，則會失敗。

- **`PROJECT_PATH`**

  要加入至方案之專案或專案的路徑。 Unix/Linux shell [萬用字元模式](https://en.wikipedia.org/wiki/Glob_(programming)) 擴充會由命令正確處理 `dotnet sln` 。

#### <a name="options"></a>選項

- **`-h|--help`**

  印出如何使用命令的描述。

- **`--in-root`**

  將專案放在解決方案的根目錄，而不是建立方案資料夾。 自 .NET Core 3.0 SDK 起提供。

- **`-s|--solution-folder <PATH>`**

  要加入專案的目的地方案資料夾路徑。 自 .NET Core 3.0 SDK 起提供。

### `remove`

從方案檔中移除一個專案或多個專案。

#### <a name="synopsis"></a>概要

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a>引數

- **`SOLUTION_FILE`**

  要使用的方案檔。 如果未指定，則命令會在目前的目錄中搜尋一個目錄，如果有多個方案檔，則會失敗。

- **`PROJECT_PATH`**

  要加入至方案之專案或專案的路徑。 Unix/Linux shell [萬用字元模式](https://en.wikipedia.org/wiki/Glob_(programming)) 擴充會由命令正確處理 `dotnet sln` 。

#### <a name="options"></a>選項

- **`-h|--help`**

  印出如何使用命令的描述。

## <a name="examples"></a>範例

- 列出方案中的專案：

  ```dotnetcli
  dotnet sln todo.sln list
  ```

- 將 C# 專案新增至方案：

  ```dotnetcli
  dotnet sln add todo-app/todo-app.csproj
  ```

- 移除方案中的 C# 專案：

  ```dotnetcli
  dotnet sln remove todo-app/todo-app.csproj
  ```

- 將多個 c # 專案新增至方案的根目錄：

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj --in-root
  ```

- 將多個 C# 專案新增至方案：

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- 從方案中移除多個 C# 專案：

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- 使用萬用字元模式將多個 c # 專案新增至方案 (僅限 Unix/Linux) ：

  ```dotnetcli
  dotnet sln todo.sln add **/*.csproj
  ```

- 使用萬用字元模式將多個 c # 專案新增至方案 (只 Windows PowerShell) ：

  ```dotnetcli
  dotnet sln todo.sln add (ls -r **/*.csproj)
  ```

- 使用萬用字元模式從方案中移除多個 c # 專案，只 (Unix/Linux) ：

  ```dotnetcli
  dotnet sln todo.sln remove **/*.csproj
  ```

- 使用萬用字元模式從方案中移除多個 c # 專案 (只 Windows PowerShell) ：

  ```dotnetcli
  dotnet sln todo.sln remove (ls -r **/*.csproj)
  ```
