---
title: dotnet 工具執行命令
description: Dotnet 工具執行命令會叫用本機工具。
ms.date: 02/14/2020
ms.openlocfilehash: 76830b8a8088fbf21f14ab0722b9547eabde7ba4
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156955"
---
# <a name="dotnet-tool-run"></a>dotnet tool run

**本文適用于：** ✔️ .net CORE 3.0 SDK 和更新版本

## <a name="name"></a>名稱

`dotnet tool run`-叫用本機工具。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet tool run <COMMAND NAME>
dotnet tool run <-h|--help>
```

## <a name="description"></a>描述

`dotnet tool run` 命令會搜尋目前目錄範圍內的工具資訊清單檔案。 當它找到指定之工具的參考時，就會執行工具。 如需詳細資訊，請參閱叫[用本機工具](global-tools.md#invoke-a-local-tool)。

## <a name="arguments"></a>引數

- **`COMMAND_NAME`**

  要執行之工具的命令名稱。

## <a name="options"></a>選項。

- **`-h|--help`**

  印出命令的簡短說明。

## <a name="example"></a>範例

- **`dotnet tool run dotnetsay`**

  執行 `dotnetsay` 本機工具。

## <a name="see-also"></a>另請參閱

- [.NET Core 工具](global-tools.md)
