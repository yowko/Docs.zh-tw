---
ms.openlocfilehash: ec6724ab378dd614c55a024ede18d997d27be3a3
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032437"
---
### <a name="target-framework-net-framework-support-dropped"></a>目標 framework：已卸載 .NET Framework 支援

從 ASP.NET Core 3.0 開始，.NET Framework 是不受支援的目標 Framework。

#### <a name="change-description"></a>變更描述

.NET Framework 4.8 是 .NET Framework 的最後一個主要版本。 新的 ASP.NET Core 應用程式應該以 .NET Core 為基礎。 從 .NET Core 3.0 版本開始，您可以將 ASP.NET Core 3.0 視為 .NET Core 的一部分。

使用 ASP.NET Core 搭配 .NET Framework 的客戶可以使用 [2.1 LTS 版本](https://dotnet.microsoft.com/download/dotnet-core/2.1)，以完全支援的方式繼續進行。 2.1 的支援和服務會繼續進行，直到至少2021年8月21日為止。 此日期是每個 [.Net 支援原則](https://dotnet.microsoft.com/platform/support-policy)的 LTS 發行宣告後三年。 **.NET Framework 上** ASP.NET Core 2.1 套件的支援將會無限期地延伸，類似于 [其他以套件為基礎的 ASP.NET 架構的服務原則](https://dotnet.microsoft.com/platform/support/policy/aspnet)。

如需從 .NET Framework 移植到 .NET Core 的詳細資訊，請參閱 [移植到 .Net core](~/docs/core/porting/index.md)。

`Microsoft.Extensions` 封裝 (例如記錄、相依性插入及設定) ，而且 Entity Framework Core 不受影響。 他們將繼續支援 .NET Standard。

如需此變更動機的詳細資訊，請參閱 [原始的 blog 文章](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/)。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

ASP.NET Core 的應用程式可以在 .NET Core 或 .NET Framework 上執行。

#### <a name="new-behavior"></a>新的行為

ASP.NET Core 的應用程式只能在 .NET Core 上執行。

#### <a name="recommended-action"></a>建議的動作

請採取下列其中一個動作：

- 將您的應用程式保留在 ASP.NET Core 2.1。
- 將您的應用程式和相依性遷移至 .NET Core。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
