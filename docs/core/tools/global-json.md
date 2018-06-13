---
title: global.json 參考
description: 請參閱 global.json 檔案的結構描述，它允許設定 .NET Core 工具的版本。
author: blackdwarf
ms.author: mairaw
ms.date: 04/05/2017
ms.openlocfilehash: 7479774c7b9cdda233cf32d791c16e7fc6d733a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33209966"
---
# <a name="globaljson-reference"></a>global.json 參考

*global.json* 檔案允許透過 `sdk` 屬性使用選取的 .NET Core 工具版本。

.NET Core CLI 工具會在目前工作目錄 (這不一定與專案目錄相同) 或它的其中一個上層目錄中尋找此檔案。

## <a name="sdk"></a>SDK
類型：Object

指定 SDK 相關資訊。

### <a name="version"></a>版本
類型：String

要使用的 SDK 版本。

例如: 

```json
{
  "sdk": {
    "version": "1.0.0-preview2-003121"
  }
}
```
