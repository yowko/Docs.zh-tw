---
title: 重大變更： FrameworkDescription 的值為 .NET 而非 .NET Core
description: 瞭解核心 .NET 程式庫中的 .NET 5.0 重大變更，其中 >runtimeinformation. FrameworkDescription 現在會傳回 ".NET" 而非 ".NET Core"。
ms.date: 11/01/2020
ms.openlocfilehash: 3925fb092135c26291e1e60b99f359974d21553c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760721"
---
# <a name="frameworkdescriptions-value-is-net-instead-of-net-core"></a>FrameworkDescription 的值是 .NET 而不是 .NET Core

<xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> 現在會傳回 ".NET" 而不是 ".NET Core"。

## <a name="change-description"></a>變更描述

在先前的 .NET 版本中，會傳回 <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> ".Net Core" 做為描述字串的一部分，例如， `.NET Core 3.1.1` 。

從 .NET 5.0 開始，會傳回 <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> ".net" 做為描述字串的一部分，例如， `.NET 5.0.0` 。

## <a name="reason-for-change"></a>變更的原因

使用 .NET 5 `netcoreapp` 時，會將取代 `net` 為簡短的目標架構名字。 為了保持一致性，也更新了架構的描述。 這項變更是表面，因為 `FrameworkName` 未編碼于屬性中的任何其他位置 <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> 。

## <a name="version-introduced"></a>引進的版本

5.0

## <a name="recommended-action"></a>建議的動作

更新在傳回的字串中搜尋 ".NET Core" 的任何程式碼 <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription> 。

## <a name="affected-apis"></a>受影響的 API

- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
