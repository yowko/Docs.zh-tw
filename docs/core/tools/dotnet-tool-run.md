---
title: dotnet 工具執行命令
description: Dotnet 工具執行命令會叫用本機工具。
ms.date: 02/14/2020
ms.openlocfilehash: 05b21c0f5ea86f4b99b220f556c61bf83f464114
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543877"
---
# <a name="dotnet-tool-run"></a>dotnet 工具執行

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
