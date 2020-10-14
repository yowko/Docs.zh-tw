---
ms.openlocfilehash: 80d13609f1b02ae0ac875b2028e745670bb8f503
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050558"
---
### <a name="frameworkdescriptions-value-is-net-instead-of-net-core"></a>FrameworkDescription 的值是 .NET 而不是 .NET Core

<xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> 現在會傳回 ".NET" 而不是 ".NET Core"。

#### <a name="change-description"></a>變更描述

在先前的 .NET 版本中，會傳回 <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> ".Net Core" 做為描述字串的一部分，例如， `.NET Core 3.1.1` 。

從 .NET 5.0 開始，會傳回 <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> ".net" 做為描述字串的一部分，例如， `.NET 5.0.0` 。

#### <a name="reason-for-change"></a>變更的原因

使用 .NET 5 `netcoreapp` 時，會將取代 `net` 為簡短的目標架構名字。 為了保持一致性，也更新了架構的描述。 這項變更是表面，因為 `FrameworkName` 未編碼于屬性中的任何其他位置 <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> 。

#### <a name="version-introduced"></a>引進的版本

5.0

#### <a name="recommended-action"></a>建議的動作

更新在傳回的字串中搜尋 ".NET Core" 的任何程式碼 <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription> 。

#### <a name="category"></a>類別

Core .NET 程式庫

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
