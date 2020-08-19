---
ms.openlocfilehash: ccd056f23d26e6cce4cc691542784792bffe9fc6
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558167"
---
### <a name="environmentosversion-returns-the-correct-operating-system-version"></a>環境。 OSVersion 傳回正確的作業系統版本

<xref:System.Environment.OSVersion?displayProperty=nameWithType> 傳回作業系統 (OS) 的實際版本，例如針對應用程式相容性選取的作業系統。

#### <a name="change-description"></a>變更描述

在舊版的 .NET 中， <xref:System.Environment.OSVersion?displayProperty=nameWithType> 當應用程式在 Windows 相容性模式下執行時，會傳回不正確的 OS 版本。 如需詳細資訊，請參閱 [GetVersionExA 函數備註](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks)。

從 .NET 5.0 開始，會傳回 <xref:System.Environment.OSVersion?displayProperty=nameWithType> 作業系統的實際版本。

#### <a name="reason-for-change"></a>變更的原因

這個屬性的使用者預期會傳回作業系統的實際版本。 大部分的 .NET 應用程式不會在其應用程式資訊清單中指定其支援的版本，因此會從 dotnet 主機取得預設支援的版本。 因此，相容性填充碼對執行中的應用程式很有意義。 當 Windows 發行新版本，而較舊的 dotnet 主機仍在使用中時，這些應用程式可能會得到不正確的 OS 版本。 傳回實際版本與開發人員對此 API 的期望更具內嵌。

#### <a name="version-introduced"></a>引進的版本

5.0

#### <a name="recommended-action"></a>建議的動作

請檢查並測試任何使用的程式碼， <xref:System.Environment.OSVersion?displayProperty=nameWithType> 以確保它會如預期運作。

#### <a name="category"></a>類別

Core .NET 程式庫

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Environment.OSVersion?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Environment.OSVersion`

-->
