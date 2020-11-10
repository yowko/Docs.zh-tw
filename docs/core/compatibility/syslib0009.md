---
title: SYSLIB0009 警告
description: 瞭解產生編譯時期警告 SYSLIB0009 的 obsoletions。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 47b4f595a54800370da90f61d838c665df8b6091
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94439972"
---
# <a name="syslib0009-the-authenticationmanager-authenticate-and-preauthenticate-methods-are-not-supported"></a>SYSLIB0009：不支援 AuthenticationManager 驗證和預先驗證方法

下列 Api 會標示為已淘汰，從 .NET 5.0 開始。 使用這些 Api `SYSLIB0009` 時，會在編譯時期產生警告。

- <xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType>
- <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType>

## <a name="suppress-the-warning"></a>隱藏警告

如果您無法變更程式碼，您可以透過指示詞 `#pragma` 或專案設定來隱藏警告 `<NoWarn>` 。 如需範例，請參閱 [隱藏警告](syslib-obsoletions.md#suppress-warnings)。
