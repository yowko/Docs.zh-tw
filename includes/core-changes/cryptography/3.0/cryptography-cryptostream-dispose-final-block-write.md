---
ms.openlocfilehash: 6ffd4147a99a59d0a2e50d3f88279608e286aed1
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679962"
---
### <a name="cryptostreamdispose-transforms-final-block-only-when-writing"></a>CryptoStream 只會在寫入時轉換最終區塊

<xref:System.Security.Cryptography.CryptoStream.Dispose%2A?displayProperty=nameWithType>用來完成作業的方法， `CryptoStream` 不會再于讀取時嘗試轉換最終區塊。

#### <a name="change-description"></a>變更描述

在舊版的 .NET 中，如果使用者在使用 in 模式時執行了未完成的讀取 <xref:System.Security.Cryptography.CryptoStream> <xref:System.Security.Cryptography.CryptoStreamMode.Read> ，此 <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> 方法可能會擲回例外狀況 (例如，搭配使用 AES 與填補) 。 擲回例外狀況是因為嘗試轉換最後一個區塊，但資料未完成。

在 .NET Core 3.0 和更新版本中， <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> 讀取時不會再嘗試轉換最後的區塊，這可允許不完整的讀取。

#### <a name="reason-for-change"></a>變更的原因

這項變更可在取消網路作業時，從密碼編譯資料流程進行不完整的讀取，而不需要攔截例外狀況。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

大部分的應用程式應該不會受到這項變更的影響。

如果您的應用程式先前在讀取不完整時攔截到例外狀況，您可以刪除該 `catch` 區塊。
如果您的應用程式在雜湊案例中使用了最後一個區塊的轉換，您可能需要確保整個資料流程在處置之前都已讀取。

#### <a name="category"></a>類別

密碼編譯

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Security.Cryptography.CryptoStream.Dispose%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.CryptoStream.Dispose`

-->
