---
title: 重大變更：環境。 OSVersion 傳回正確的作業系統版本
description: 瞭解核心 .NET 程式庫中的 .NET 5.0 重大變更，其中的環境會傳回作業系統的實際版本，而不是（例如，針對應用程式相容性所選取的作業系統）。
ms.date: 11/01/2020
ms.openlocfilehash: c810d9a7a028a0c60c30d69e78a9b9c695d933ef
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009517"
---
# <a name="environmentosversion-returns-the-correct-operating-system-version"></a>環境。 OSVersion 傳回正確的作業系統版本

<xref:System.Environment.OSVersion?displayProperty=nameWithType> 傳回作業系統 (OS) 的實際版本，例如針對應用程式相容性選取的作業系統。

## <a name="change-description"></a>變更描述

在舊版的 .NET 中， <xref:System.Environment.OSVersion?displayProperty=nameWithType> 當應用程式在 Windows 相容性模式下執行時，會傳回不正確的 OS 版本。 如需詳細資訊，請參閱 [GetVersionExA 函數備註](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks)。 在 macOS 上，傳回 <xref:System.Environment.OSVersion?displayProperty=nameWithType> 基礎 Darwin 核心版本。

從 .NET 5.0 開始，會傳回 <xref:System.Environment.OSVersion?displayProperty=nameWithType> Windows 和 macOS 作業系統的實際版本。

下表顯示行為差異。

|  | 先前的 .NET 版本 | .NET 5 + |
|--|------------------------|---------|
| Windows | 6.2.9200.0 | 10.0.19042.0 |
| macOS | 19.6.0.0 | 10.15.7 |

## <a name="reason-for-change"></a>變更的原因

這個屬性的使用者預期會傳回作業系統的實際版本。 大部分的 .NET 應用程式不會在其應用程式資訊清單中指定其支援的版本，因此會從 dotnet 主機取得預設支援的版本。 因此，相容性填充碼對執行中的應用程式很有意義。 當 Windows 發行新版本，而較舊的 dotnet 主機仍在使用中時，這些應用程式可能會得到不正確的 OS 版本。 傳回實際版本與開發人員對此 API 的期望更具內嵌。

隨著在 <xref:System.OperatingSystem.IsWindowsVersionAtLeast%2A?displayProperty=nameWithType> .net 5.0 中引進、 <xref:System.OperatingSystem.IsMacOSVersionAtLeast%2A?displayProperty=nameWithType> 和， <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute?displayProperty=nameWithType> <xref:System.Environment.OSVersion?displayProperty=nameWithType> 已針對 Windows 和 macOS 變更為一致。

## <a name="version-introduced"></a>引進的版本

5.0

## <a name="recommended-action"></a>建議的動作

請檢查並測試任何使用的程式碼， <xref:System.Environment.OSVersion?displayProperty=nameWithType> 以確保它會如預期運作。

## <a name="affected-apis"></a>受影響的 API

- <xref:System.Environment.OSVersion?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Environment.OSVersion`

-->
