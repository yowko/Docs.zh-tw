---
ms.openlocfilehash: b60f74947a537c602c7bd1a89587b76bd847c82a
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937256"
---
### <a name="target-framework-net-framework-support-dropped"></a>目標 framework： .NET Framework 支援捨棄

從 ASP.NET Core 3.0 開始，.NET Framework 是不支援的目標架構。

#### <a name="change-description"></a>變更描述

.NET Framework 4.8 是 .NET Framework 的最後一個主要版本。 新的 ASP.NET Core 應用程式應該以 .NET Core 為基礎。 從 .NET Core 3.0 版本開始，您可以將 ASP.NET Core 3.0 視為 .NET Core 的一部分。

使用 ASP.NET Core 搭配 .NET Framework 的客戶可以使用[2.1 LTS 版本](https://www.microsoft.com/net/download/dotnet-core/2.1)，以完全支援的方式繼續進行。 2\.1 的支援和服務會持續到至少2021年8月21日為止。 此日期是每個[.Net 支援原則](https://www.microsoft.com/net/platform/support-policy)宣告 LTS 版本後的三年。 **.NET Framework 上**的 ASP.NET Core 2.1 套件支援將會無限期延伸，類似于[其他以套件為基礎的 ASP.NET 架構的服務原則](https://dotnet.microsoft.com/platform/support/policy/aspnet)。

如需從 .NET Framework 移植至 .NET Core 的詳細資訊，請參閱[移植至 .Net core](~/docs/core/porting/index.md)。

`Microsoft.Extensions` 套件（例如記錄、相依性插入和設定）和 Entity Framework Core 不會受到影響。 它們會繼續支援 .NET Standard。

如需這種變更動機的詳細資訊，請參閱[原始的 blog 文章](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/)。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

ASP.NET Core 的應用程式可以在 .NET Core 或 .NET Framework 上執行。

#### <a name="new-behavior"></a>新的行為

ASP.NET Core 應用程式只能在 .NET Core 上執行。

#### <a name="recommended-action"></a>建議的動作

採取下列其中一個動作：

- 將您的應用程式保留在 ASP.NET Core 2.1。
- 將您的應用程式和相依性遷移至 .NET Core。

#### <a name="category"></a>分類

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
