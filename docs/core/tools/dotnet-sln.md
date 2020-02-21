---
title: dotnet sln 命令
description: dotnet-sln 命令提供方便在方案檔中新增、移除及列出專案的選項。
ms.date: 02/14/2020
ms.openlocfilehash: b2455c04a46b2a10b8142d8ddc2d8129f2154b27
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543478"
---
# <a name="dotnet-sln"></a>dotnet sln

**本文適用于：** ✔️ .net CORE 2.x SDK 和更新版本

## <a name="name"></a>名稱

`dotnet sln`-列出或修改 .NET Core 方案檔中的專案。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command] [-h|--help]
```

## <a name="description"></a>描述

`dotnet sln` 命令提供一個便利的方式來列出及修改方案檔中的專案。

若要使用 `dotnet sln` 命令，方案檔必須已經存在。 如果您需要建立一個，請使用[dotnet new](dotnet-new.md)命令，如下列範例所示：

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a>引數

- **`SOLUTION_FILE`**

  要使用的方案檔。 如果省略這個引數，命令會在目前的目錄中搜尋一個。 如果找不到方案檔或多個方案檔，則命令會失敗。

## <a name="options"></a>選項。

- **`-h|--help`**

  印出如何使用命令的說明。

## <a name="commands"></a>命令

### `list`

列出方案檔中的所有專案。

#### <a name="synopsis"></a>概要

```dotnetcli
dotnet sln list [-h|--help]
```

#### <a name="arguments"></a>引數

- **`SOLUTION_FILE`**

  要使用的方案檔。 如果省略這個引數，命令會在目前的目錄中搜尋一個。 如果找不到方案檔或多個方案檔，則命令會失敗。

#### <a name="options"></a>選項。

- **`-h|--help`**

  印出如何使用命令的說明。
  
### `add`

將一個或多個專案加入至方案檔。

#### <a name="synopsis"></a>概要

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder] <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a>引數

- **`SOLUTION_FILE`**

  要使用的方案檔。 如果未指定，命令會在目前的目錄中搜尋一個，如果有多個方案檔，則會失敗。

- **`PROJECT_PATH`**

  要加入至方案之專案的路徑。 Unix/Linux shell[萬用字元模式](https://en.wikipedia.org/wiki/Glob_(programming))擴充會由 `dotnet sln` 命令正確處理。

#### <a name="options"></a>選項。

- **`-h|--help`**

  印出如何使用命令的說明。

- **`--in-root`**

  將專案放在方案的根目錄中，而不是建立方案資料夾。 自 .NET Core 3.0 SDK 起提供使用。

- **`-s|--solution-folder`**

  要加入專案的目的地解決方案資料夾路徑。 自 .NET Core 3.0 SDK 起提供使用。

### `remove`

從方案檔中移除一個專案或多個專案。

#### <a name="synopsis"></a>概要

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a>引數

- **`SOLUTION_FILE`**

  要使用的方案檔。 如果未指定，命令會在目前的目錄中搜尋一個，如果有多個方案檔，則會失敗。

- **`PROJECT_PATH`**

  要加入至方案之專案的路徑。 Unix/Linux shell[萬用字元模式](https://en.wikipedia.org/wiki/Glob_(programming))擴充會由 `dotnet sln` 命令正確處理。

#### <a name="options"></a>選項。

- **`-h|--help`**

  印出如何使用命令的說明。

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

- 將多C#個專案新增至方案的根目錄：

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

- 使用萬用字元C#模式將多個專案新增至解決方案（僅限 Unix/Linux）：

  ```dotnetcli
  dotnet sln todo.sln add **/*.csproj
  ```

- 使用萬用字元C#模式從方案中移除多個專案（僅限 Unix/Linux）：

  ```dotnetcli
  dotnet sln todo.sln remove **/*.csproj
  ```
