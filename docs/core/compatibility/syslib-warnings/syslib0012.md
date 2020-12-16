---
title: SYSLIB0012 警告
description: 瞭解產生編譯時期警告 SYSLIB0012 的 obsoletions。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 9b3fa94029efb2343e6dbbeb3ae36195f0956523
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596440"
---
# <a name="syslib0012-assemblycodebase-and-assemblyescapedcodebase-are-obsolete"></a>SYSLIB0012： Assembly。程式碼基底和 Assembly. EscapedCodeBase 已淘汰

下列 Api 會標示為已淘汰，從 .NET 5.0 開始。 在程式碼中使用它們會 `SYSLIB0012` 在編譯時期產生警告。

- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType>

## <a name="workarounds"></a>因應措施

請改用 <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType>。

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]
