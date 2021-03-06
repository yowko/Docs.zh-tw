---
title: SYSLIB0005 警告
description: 瞭解產生編譯時期警告 SYSLIB0005 的 obsoletion。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 1263a4d327c735268f77ed56bdcea6a4cbed4bfa
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596475"
---
# <a name="syslib0005-the-global-assembly-cache-gac-is-not-supported"></a>SYSLIB0005：不支援全域組件快取 (GAC) 

.NET Core 和 .NET 5.0 和更新版本消除了 .NET Framework 中存在的全域組件快取 (GAC) 的概念。 為了協助開發人員遠離這些 Api，部分 GAC 相關的 Api 會標示為已淘汰，從 .NET 5.0 開始。 使用這些 Api `SYSLIB0005` 時，會在編譯時期產生警告。

下列與 GAC 相關的 Api 已標示為過時：

- <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=nameWithType>

  程式庫和應用程式不應使用 <xref:System.Reflection.Assembly.GlobalAssemblyCache> API 來判斷執行時間行為，因為它一律會 `false` 在 .net Core 和 .net 5 + 中傳回。

## <a name="workarounds"></a>因應措施

如果您的應用程式會查詢 <xref:System.Reflection.Assembly.GlobalAssemblyCache> 屬性，請考慮移除呼叫。 如果您在 <xref:System.Reflection.Assembly.GlobalAssemblyCache> 執行時間使用值來選擇「gac 中的元件」-flow 與「不在 gac 中的元件」的流程，請重新考慮流程是否仍然適合 .net 5 + 應用程式。

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a>另請參閱

- [全域組件快取](../../../framework/app-domains/gac.md)
