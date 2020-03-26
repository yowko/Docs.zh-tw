---
ms.openlocfilehash: ec6724ab378dd614c55a024ede18d997d27be3a3
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2020
ms.locfileid: "79549605"
---
### <a name="target-framework-net-framework-support-dropped"></a>目標框架： .NET 框架支援已放棄

從ASP.NET核心 3.0 開始，.NET 框架是一個不受支援的目標框架。

#### <a name="change-description"></a>變更描述

.NET 框架 4.8 是 .NET 框架的最後一個主要版本。 新的ASP.NET核心應用應建立在 .NET Core 上。 從 .NET Core 3.0 版本開始，可以將 ASP.NET核心 3.0 視為 .NET Core 的一部分。

使用帶有 .NET 框架ASP.NET核心的客戶可以使用[2.1 LTS 版本](https://dotnet.microsoft.com/download/dotnet-core/2.1)以完全支援的方式繼續。 2.1 的支援和服務至少持續到 2021 年 8 月 21 日。 此日期是根據[.NET 支援政策](https://dotnet.microsoft.com/platform/support-policy)聲明 LTS 發佈後三年。 **對 .NET Framework 上的**ASP.NET Core 2.1 包的支援將無限期擴展，類似于[其他基於包ASP.NET框架的服務策略](https://dotnet.microsoft.com/platform/support/policy/aspnet)。

有關從 .NET 框架移植到 .NET 核心的詳細資訊，請參閱[移植到 .NET 核心](~/docs/core/porting/index.md)。

`Microsoft.Extensions`包（如日誌記錄、依賴項注入和配置）和實體框架核心不受影響。 他們將繼續支援 .NET 標準。

有關此更改的動機的詳細資訊，請參閱[原始博客文章](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/)。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="old-behavior"></a>舊的行為

ASP.NET核心應用可以在 .NET 核心或 .NET 框架上運行。

#### <a name="new-behavior"></a>新的行為

ASP.NET核心應用只能在 .NET Core 上運行。

#### <a name="recommended-action"></a>建議的動作

請採取下列其中一個動作：

- 將應用保持在 ASP.NET 核心 2.1 上。
- 將應用和依賴項遷移到 .NET Core。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
