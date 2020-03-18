---
title: 點網工具運行命令
description: 點網工具運行命令調用本地工具。
ms.date: 02/14/2020
ms.openlocfilehash: a088cd0b7f4bba014234a8189a42a63aa6d88f4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847842"
---
# <a name="dotnet-tool-run"></a>dotnet tool run

**本文適用于：✔️** .NET Core 3.0 SDK 和更高版本

## <a name="name"></a>名稱

`dotnet tool run`- 調用本地工具。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet tool run <COMMAND NAME>

dotnet tool run <-h|--help>
```

## <a name="description"></a>描述

該`dotnet tool run`命令搜索目前的目錄範圍內的工具清單檔。 當它找到對指定工具的引用時，它將運行該工具。 有關詳細資訊，請參閱[調用本地工具](global-tools.md#invoke-a-local-tool)。

## <a name="arguments"></a>引數

- **`COMMAND_NAME`**

  要運行的工具的命令名稱。

## <a name="options"></a>選項。

- **`-h|--help`**

  印出命令的簡短說明。

## <a name="example"></a>範例

- **`dotnet tool run dotnetsay`**

  運行`dotnetsay`本地工具。

## <a name="see-also"></a>另請參閱

- [.NET 核心工具](global-tools.md)
- [教程：使用 .NET 核心 CLI 安裝和使用 .NET 核心本地工具](local-tools-how-to-use.md)
