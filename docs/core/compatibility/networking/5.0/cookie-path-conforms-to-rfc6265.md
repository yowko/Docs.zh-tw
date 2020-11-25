---
title: 重大變更： Cookie 路徑處理現在符合 RFC 6265
description: 瞭解 .NET 5.0 中的重大變更，其中 RFC 6265 中定義的路徑處理演算法是針對 Cookie 和 CookieContainer 類別所執行。
ms.date: 08/18/2020
ms.openlocfilehash: 4aea06f434c4bbbef7d94b4b39ff647dd954745e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760633"
---
# <a name="cookie-path-handling-now-conforms-to-rfc-6265"></a><span data-ttu-id="dd602-103">Cookie 路徑處理現在符合 RFC 6265</span><span class="sxs-lookup"><span data-stu-id="dd602-103">Cookie path handling now conforms to RFC 6265</span></span>

<span data-ttu-id="dd602-104">[RFC 6265](https://tools.ietf.org/html/rfc6265)中定義的路徑處理演算法是針對 <xref:System.Net.Cookie> 和類別所執行 <xref:System.Net.CookieContainer> 。</span><span class="sxs-lookup"><span data-stu-id="dd602-104">Path-handling algorithms defined in [RFC 6265](https://tools.ietf.org/html/rfc6265) were implemented for the <xref:System.Net.Cookie> and <xref:System.Net.CookieContainer> classes.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="dd602-105">引進的版本</span><span class="sxs-lookup"><span data-stu-id="dd602-105">Version introduced</span></span>

<span data-ttu-id="dd602-106">5.0</span><span class="sxs-lookup"><span data-stu-id="dd602-106">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="dd602-107">變更描述</span><span class="sxs-lookup"><span data-stu-id="dd602-107">Change description</span></span>

- <span data-ttu-id="dd602-108"><xref:System.Net.Cookie.Path>屬性不再需要是要求路徑的前置詞。</span><span class="sxs-lookup"><span data-stu-id="dd602-108">The <xref:System.Net.Cookie.Path> property is no longer required to be a prefix of the request path.</span></span>
- <span data-ttu-id="dd602-109">的預設值和路徑比對 <xref:System.Net.Cookie.Path> 演算法的計算是依照 RFC 6265 的 [5.1.4 一節](https://tools.ietf.org/html/rfc6265#section-5.1.4) 中的定義來執行。</span><span class="sxs-lookup"><span data-stu-id="dd602-109">The calculation of the default value of <xref:System.Net.Cookie.Path> and path-matching algorithms were implemented as defined in [section 5.1.4](https://tools.ietf.org/html/rfc6265#section-5.1.4) of RFC 6265.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="dd602-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="dd602-110">Recommended action</span></span>

<span data-ttu-id="dd602-111">在大多數情況下，您不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="dd602-111">In most cases, you won't need to take any action.</span></span> <span data-ttu-id="dd602-112">但是，如果您的程式碼相依于 <xref:System.Net.Cookie.Path> 驗證，則您必須在程式碼中執行必要的驗證。</span><span class="sxs-lookup"><span data-stu-id="dd602-112">However, if your code was dependent on <xref:System.Net.Cookie.Path> validation, you'll need to implement required validation in your code.</span></span> <span data-ttu-id="dd602-113">如果您的程式碼相依于的預設值計算 <xref:System.Net.Cookie.Path> ，請考慮以手動方式提供值， <xref:System.Net.Cookie.Path> 而不是使用預設值。</span><span class="sxs-lookup"><span data-stu-id="dd602-113">If your code was dependent on default value calculation for <xref:System.Net.Cookie.Path>, consider supplying the <xref:System.Net.Cookie.Path> value manually instead of using the default value.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="dd602-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="dd602-114">Affected APIs</span></span>

- <xref:System.Net.Cookie?displayProperty=fullName>
- <xref:System.Net.CookieContainer?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Net.Cookie`
- `T:System.Net.CookieContainer`

### Category

Networking

-->
