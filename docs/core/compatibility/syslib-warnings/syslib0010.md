---
title: SYSLIB0010 警告
description: 瞭解產生編譯時期警告 SYSLIB0010 的 obsoletions。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 289fb3f766a6e1d37bea8faec1896d20442f43f9
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596459"
---
# <a name="syslib0010-unsupported-remoting-apis"></a>SYSLIB0010：不支援的遠端 Api

[.Net 遠端處理](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71)) 是一種舊版技術，基礎結構只存在於 .NET Framework 中。 從 .NET 5.0 開始，下列遠端相關的 Api 會標示為已淘汰。 在程式碼中使用它們會 `SYSLIB0010` 在編譯時期產生警告。

- <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType>
- <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType>

## <a name="workarounds"></a>因應措施

請考慮使用以 WCF 或 HTTP 為基礎的 REST 服務，與其他應用程式或電腦之間的物件進行通訊。 如需詳細資訊，請參閱 [.NET FRAMEWORK .Net Core 上無法使用的技術](../../porting/net-framework-tech-unavailable.md)。

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a>另請參閱

- [.NET 遠端處理](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71))
