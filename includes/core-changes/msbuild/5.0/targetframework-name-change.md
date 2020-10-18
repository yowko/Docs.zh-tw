---
ms.openlocfilehash: 1ddc2cea19872b44ff9659bcebd76117587ea89a
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159481"
---
### <a name="targetframework-change-from-netcoreapp-to-net"></a>TargetFramework 從 netcoreapp 變更為 net

MSBuild 屬性的值 `TargetFramework` 已從變更 `netcoreapp3.1` 為 `net5.0` 。 這可能會中斷依賴剖析值的程式碼 `TargetFramework` 。

#### <a name="version-introduced"></a>引進的版本

5.0

#### <a name="change-description"></a>變更描述

在 .NET Core 1.0-3.1 中，MSBuild 屬性的值是以 `TargetFramework` `netcoreapp` `netcoreapp3.1` .net core 3.1 的應用程式為開頭，例如。 從 .NET 5.0 開始，此值已簡化為只從 `net` .net 5.0 開始（例如） `net5.0` 。

如需詳細資訊，請參閱 .NET 5 的 .NET Standard 和[目標 framework 名稱](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md)[的未來](https://devblogs.microsoft.com/dotnet/the-future-of-net-standard/)。

#### <a name="reason-for-change"></a>變更的原因

- 簡化 `TargetFramework` 值。
- 讓專案 `TargetPlatform` 在屬性中包含 `TargetFramework` 。

#### <a name="recommended-action"></a>建議的動作

如果您有剖析值的邏輯 `TargetFramework` ，您必須更新它。 例如，下列 MSBuild 條件依賴的值 `TargetFramework` 。

```xml
<PropertyGroup Condition="$(TargetFramework.StartsWith('netcoreapp'))">
```

針對此需求，您可以更新程式碼來比較目標 framework 識別碼。

```xml
<PropertyGroup Condition="'$([MSBuild]::GetTargetFrameworkIdentifier('$(TargetFramework)'))' == '.NETCoreApp'">
```

#### <a name="category"></a>類別

MSBuild

#### <a name="affected-apis"></a>受影響的 API

N/A

<!--

#### Affected APIs

Not detectable via API analysis.

-->
