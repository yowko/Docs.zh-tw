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
# <a name="negotiatestream-and-sslstream-allow-successive-begin-operations"></a><span data-ttu-id="a4f96-103">NegotiateStream 和 SslStream 允許連續的開始作業</span><span class="sxs-lookup"><span data-stu-id="a4f96-103">NegotiateStream and SslStream allow successive Begin operations</span></span>

<span data-ttu-id="a4f96-104">安全性資料流程的錯誤案例會以不同方式處理，而後續對或的呼叫 `BeginAuthenticateAsServer` `BeginAuthenticateAsClient` 可能不會再失敗。</span><span class="sxs-lookup"><span data-stu-id="a4f96-104">Error cases on security streams are handled differently, and successive calls to `BeginAuthenticateAsServer` or `BeginAuthenticateAsClient` may no longer fail.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="a4f96-105">引進的版本</span><span class="sxs-lookup"><span data-stu-id="a4f96-105">Version introduced</span></span>

<span data-ttu-id="a4f96-106">5.0</span><span class="sxs-lookup"><span data-stu-id="a4f96-106">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="a4f96-107">變更描述</span><span class="sxs-lookup"><span data-stu-id="a4f96-107">Change description</span></span>

<span data-ttu-id="a4f96-108">在舊版的 .NET 版本中，呼叫 `BeginAuthenticateAsServer` 或 `BeginAuthenticateAsClient` 連續，但不先呼叫 `EndAuthenticateAsServer` 或會 `EndAuthenticateAsClient` 產生 <xref:System.NotSupportedException> 。</span><span class="sxs-lookup"><span data-stu-id="a4f96-108">In previous .NET versions, calling `BeginAuthenticateAsServer` or `BeginAuthenticateAsClient` successively without first calling `EndAuthenticateAsServer` or `EndAuthenticateAsClient` results in a <xref:System.NotSupportedException>.</span></span> <span data-ttu-id="a4f96-109">從 .NET 5.0 開始，後續的呼叫 `BeginAuthenticateAsServer` 或 `BeginAuthenticateAsClient` 不再產生 <xref:System.NotSupportedException> ，因為這些 api 是由型的執行所支援的 <xref:System.Threading.Tasks.Task> 。</span><span class="sxs-lookup"><span data-stu-id="a4f96-109">Starting in .NET 5.0, successive calls to `BeginAuthenticateAsServer` or `BeginAuthenticateAsClient` no longer result in a <xref:System.NotSupportedException>, because these APIs are backed by a <xref:System.Threading.Tasks.Task>-based implementation.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="a4f96-110">變更的原因</span><span class="sxs-lookup"><span data-stu-id="a4f96-110">Reason for change</span></span>

<span data-ttu-id="a4f96-111">從非同步程式設計模型切換內部實 (APM) 轉換為 <xref:System.Threading.Tasks.Task> 基礎，可改善效能並降低程式碼的複雜度。</span><span class="sxs-lookup"><span data-stu-id="a4f96-111">Switching the internal implementation from asynchronous programming model (APM) to <xref:System.Threading.Tasks.Task>-based improves performance and decreases code complexity.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="a4f96-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="a4f96-112">Recommended action</span></span>

<span data-ttu-id="a4f96-113">開發人員不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="a4f96-113">No action is required on the part of the developer.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="a4f96-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="a4f96-114">Affected APIs</span></span>

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
