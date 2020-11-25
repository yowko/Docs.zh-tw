---
title: 重大變更： NegotiateStream 和 SslStream 允許後續的開始作業
description: 瞭解 .NET 5.0 中的重大變更，其中安全性資料流程的錯誤案例會以不同方式處理，而後續對 BeginAuthenticateAsServer 或 BeginAuthenticateAsClient 的呼叫可能不會再失敗。
ms.date: 10/18/2020
ms.openlocfilehash: e0226d0f5586efca050ca3497ca1490fa21fd943
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760621"
---
# <a name="negotiatestream-and-sslstream-allow-successive-begin-operations"></a>NegotiateStream 和 SslStream 允許連續的開始作業

安全性資料流程的錯誤案例會以不同方式處理，而後續對或的呼叫 `BeginAuthenticateAsServer` `BeginAuthenticateAsClient` 可能不會再失敗。

## <a name="version-introduced"></a>引進的版本

5.0

## <a name="change-description"></a>變更描述

在舊版的 .NET 版本中，呼叫 `BeginAuthenticateAsServer` 或 `BeginAuthenticateAsClient` 連續，但不先呼叫 `EndAuthenticateAsServer` 或會 `EndAuthenticateAsClient` 產生 <xref:System.NotSupportedException> 。 從 .NET 5.0 開始，後續的呼叫 `BeginAuthenticateAsServer` 或 `BeginAuthenticateAsClient` 不再產生 <xref:System.NotSupportedException> ，因為這些 api 是由型的執行所支援的 <xref:System.Threading.Tasks.Task> 。

## <a name="reason-for-change"></a>變更的原因

從非同步程式設計模型切換內部實 (APM) 轉換為 <xref:System.Threading.Tasks.Task> 基礎，可改善效能並降低程式碼的複雜度。

## <a name="recommended-action"></a>建議的動作

開發人員不需要採取任何動作。

## <a name="affected-apis"></a>受影響的 API

- <xref:System.Net.Security.SslStream.BeginAuthenticateAsServer%2A?displayProperty=fullName>
- <xref:System.Net.Security.SslStream.BeginAuthenticateAsClient%2A?displayProperty=fullName>
- <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer%2A?displayProperty=fullName>
- <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:M:System.Net.Security.SslStream.BeginAuthenticateAsServer`
- `Overload:M:System.Net.Security.SslStream.BeginAuthenticateAsClient`
- `Overload:M:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer`
- `Overload:M:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient`

### Category

Networking

-->
