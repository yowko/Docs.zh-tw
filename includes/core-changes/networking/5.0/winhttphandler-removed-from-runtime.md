---
ms.openlocfilehash: 115cd6be935ae12a1293f948a0f899c6c3ff0d78
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608471"
---
### <a name="winhttphandler-removed-from-net-runtime"></a>WinHttpHandler 已從 .NET 執行時間移除

`WinHttpHandler`類別已從*System.Net.Http.dll*元件中移除。 它現在僅適用于頻外 (OOB) [NuGet 套件](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)。

#### <a name="version-introduced"></a>引進的版本

5.0

#### <a name="change-description"></a>變更描述

在先前的 .NET 版本中， <xref:System.Net.Http.WinHttpHandler> 類別可作為核心 .net 程式庫的一部分。 從 .NET 5.0 開始， <xref:System.Net.Http.WinHttpHandler> 類別僅可作為個別安裝的 [NuGet 套件](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)。

#### <a name="recommended-action"></a>建議的動作

安裝 [WinHttpHandler NuGet 套件](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)。 或者，如果您不需要 WinHTTP 特定功能，請改用 <xref:System.Net.Http.SocketsHttpHandler> 。

#### <a name="category"></a>類別

網路功能

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Net.Http.WinHttpHandler?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Net.Http.WinHttpHandler`

-->
