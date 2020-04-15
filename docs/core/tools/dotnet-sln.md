---
title: dotnet sln 命令
description: dotnet-sln 命令提供方便在方案檔中新增、移除及列出專案的選項。
ms.date: 02/14/2020
ms.openlocfilehash: 615e25e30a63b6ca36d9898cfcde565053830572
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389643"
---
# <a name="dotnet-sln"></a>dotnet sln

**本文適用於:✔️** .NET Core 2.x SDK 和更高版本

## <a name="name"></a>名稱

`dotnet sln`- 列出或修改 .NET Core 解決方案檔中的專案。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command] [-h|--help]
```

## <a name="description"></a>描述

該`dotnet sln`命令提供了一種在解決方案檔中列出和修改專案的便捷方法。

若要使用 `dotnet sln` 命令，方案檔必須已經存在。 如果需要建立指令,請使用[dotnet 新](dotnet-new.md)指令,如以下範例所示:

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a>引數

- **`SOLUTION_FILE`**

  要使用的解決方案檔。 如果省略此參數,該命令將搜索當前目錄。 如果找不到解決方案檔或多個解決方案檔,則命令將失敗。

## <a name="options"></a>選項。

- **`-h|--help`**

  列印出如何使用命令的說明。

## <a name="commands"></a>命令

### `list`

列出方案檔中的所有專案。

#### <a name="synopsis"></a>概要

```dotnetcli
dotnet sln list [-h|--help]
```

#### <a name="arguments"></a>引數

- **`SOLUTION_FILE`**

  要使用的解決方案檔。 如果省略此參數,該命令將搜索當前目錄。 如果找不到解決方案檔或多個解決方案檔,則命令將失敗。

#### <a name="options"></a>選項。

- **`-h|--help`**

  列印出如何使用命令的說明。
  
### `add`

將一個或多個專案添加到解決方案檔中。

#### <a name="synopsis"></a>概要

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder] <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a>引數

- **`SOLUTION_FILE`**

  要使用的解決方案檔。 如果未指定,該命令將搜索當前目錄,如果有多個解決方案檔,則該命令將失敗。

- **`PROJECT_PATH`**

  要添加到解決方案的專案或專案的路徑。 命令正確處理`dotnet sln`Unix/Linux 外殼[globing 模式](https://en.wikipedia.org/wiki/Glob_(programming))擴展。

#### <a name="options"></a>選項。

- **`-h|--help`**

  列印出如何使用命令的說明。

- **`--in-root`**

  將專案放在解決方案的根目錄中,而不是創建解決方案資料夾。 自 .NET Core 3.0 SDK 起提供。

- **`-s|--solution-folder`**

  要將專案添加到的目標解決方案資料夾路徑。 自 .NET Core 3.0 SDK 起提供。

### `remove`

從方案檔中移除一個專案或多個專案。

#### <a name="synopsis"></a>概要

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a>引數

- **`SOLUTION_FILE`**

  要使用的解決方案檔。 如果未指定,該命令將搜索當前目錄,如果有多個解決方案檔,則該目錄將失敗。

- **`PROJECT_PATH`**

  要添加到解決方案的專案或專案的路徑。 命令正確處理`dotnet sln`Unix/Linux 外殼[globing 模式](https://en.wikipedia.org/wiki/Glob_(programming))擴展。

#### <a name="options"></a>選項。

- **`-h|--help`**

  列印出如何使用命令的說明。

## <a name="examples"></a>範例

- 在解決方案中列出專案:

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

- 新增 C# 專案到解決方案的根目錄:

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

- 使用 globing 模式(僅限 Unix/Linux)將多個 C# 專案新增到解決方案中:

  ```dotnetcli
  dotnet sln todo.sln add **/*.csproj
  ```

- 使用 globing 模式(僅限 Windows PowerShell)將多個 C# 專案新增到解決方案中:

  ```dotnetcli
  dotnet sln todo.sln add (ls **/*.csproj)
  ```

- 使用 globing 模式從解決方案中移除多個 C# 專案(僅限 Unix/Linux):

  ```dotnetcli
  dotnet sln todo.sln remove **/*.csproj
  ```

- 使用 globing 模式從解決方案中移除多個 C# 專案(只有限制 Windows PowerShell):

  ```dotnetcli
  dotnet sln todo.sln remove (ls **/*.csproj)
  ```
