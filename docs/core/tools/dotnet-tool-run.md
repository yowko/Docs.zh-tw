---
title: dotnet tool run 命令
description: Dotnet tool run 命令會叫用本機工具。
ms.date: 02/14/2020
ms.openlocfilehash: 116ecb61748a0ca70ed385b279b11b939748f4a8
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634151"
---
# <a name="dotnet-tool-run"></a>dotnet tool run

本文 **適用于：** ✔️ .net CORE 3.0 SDK 和更新版本

## <a name="name"></a>名稱

`dotnet tool run` -叫用本機工具。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet tool run <COMMAND NAME>

dotnet tool run -h|--help
```

## <a name="description"></a>描述

此 `dotnet tool run` 命令會搜尋目前目錄範圍內的工具資訊清單檔案。 當它找到指定之工具的參考時，就會執行工具。 如需詳細資訊，請參閱叫 [用本機工具](global-tools.md#invoke-a-local-tool)。

## <a name="arguments"></a>引數

- **`COMMAND_NAME`**

  要執行之工具的命令名稱。

## <a name="options"></a>選項

- **`-h|--help`**

  印出命令的簡短說明。

## <a name="example"></a>範例

- **`dotnet tool run dotnetsay`**

  執行 `dotnetsay` 本機工具。

## <a name="see-also"></a>另請參閱

- [.NET 工具](global-tools.md)
- [教學課程：使用 .NET CLI 安裝和使用 .NET 本機工具](local-tools-how-to-use.md)
