---
title: SYSLIB0009 警告
description: 瞭解產生編譯時期警告 SYSLIB0009 的 obsoletions。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 922fcc30b2b1577976e4e88e3f7631e19d4b2cce
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596472"
---
# <a name="syslib0009-the-authenticationmanager-authenticate-and-preauthenticate-methods-are-not-supported"></a>SYSLIB0009：不支援 AuthenticationManager 驗證和預先驗證方法

下列 Api 會標示為已淘汰，從 .NET 5.0 開始。 使用這些 Api `SYSLIB0009` 時，會在編譯時期產生警告。

- <xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType>
- <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType>

## <a name="suppress-the-warning"></a>隱藏警告

如果您無法變更程式碼，您可以透過指示詞 `#pragma` 或專案設定來隱藏警告 `<NoWarn>` 。 如需範例，請參閱 [隱藏警告](../syslib-obsoletions.md#suppress-warnings)。
