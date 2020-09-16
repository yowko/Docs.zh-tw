---
ms.openlocfilehash: 7140f6d4cac063088b3663ab98d292104218b542
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465505"
---
### <a name="cookie-path-handling-now-conforms-to-rfc-6265"></a><span data-ttu-id="027bf-101">Cookie 路徑處理現在符合 RFC 6265</span><span class="sxs-lookup"><span data-stu-id="027bf-101">Cookie Path handling now conforms to RFC 6265</span></span>

<span data-ttu-id="027bf-102">[RFC 6265](https://tools.ietf.org/html/rfc6265)中定義的路徑處理演算法是針對 <xref:System.Net.Cookie> 和類別所執行 <xref:System.Net.CookieContainer> 。</span><span class="sxs-lookup"><span data-stu-id="027bf-102">Path-handling algorithms defined in [RFC 6265](https://tools.ietf.org/html/rfc6265) were implemented for the <xref:System.Net.Cookie> and <xref:System.Net.CookieContainer> classes.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="027bf-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="027bf-103">Version introduced</span></span>

<span data-ttu-id="027bf-104">5.0</span><span class="sxs-lookup"><span data-stu-id="027bf-104">5.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="027bf-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="027bf-105">Change description</span></span>

- <span data-ttu-id="027bf-106"><xref:System.Net.Cookie.Path>屬性不再需要是要求路徑的前置詞。</span><span class="sxs-lookup"><span data-stu-id="027bf-106">The <xref:System.Net.Cookie.Path> property is no longer required to be a prefix of the request path.</span></span>
- <span data-ttu-id="027bf-107">的預設值和路徑比對 <xref:System.Net.Cookie.Path> 演算法的計算是依照 RFC 6265 的 [5.1.4 一節](https://tools.ietf.org/html/rfc6265#section-5.1.4) 中的定義來執行。</span><span class="sxs-lookup"><span data-stu-id="027bf-107">The calculation of the default value of <xref:System.Net.Cookie.Path> and path-matching algorithms were implemented as defined in [section 5.1.4](https://tools.ietf.org/html/rfc6265#section-5.1.4) of RFC 6265.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="027bf-108">建議的動作</span><span class="sxs-lookup"><span data-stu-id="027bf-108">Recommended action</span></span>

<span data-ttu-id="027bf-109">在大多數情況下，您不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="027bf-109">In most cases, you won't need to take any action.</span></span> <span data-ttu-id="027bf-110">但是，如果您的程式碼相依于 <xref:System.Net.Cookie.Path> 驗證，則您必須在程式碼中執行必要的驗證。</span><span class="sxs-lookup"><span data-stu-id="027bf-110">However, if your code was dependent on <xref:System.Net.Cookie.Path> validation, you'll need to implement required validation in your code.</span></span> <span data-ttu-id="027bf-111">如果您的程式碼相依于的預設值計算 <xref:System.Net.Cookie.Path> ，請考慮以手動方式提供值， <xref:System.Net.Cookie.Path> 而不是使用預設值。</span><span class="sxs-lookup"><span data-stu-id="027bf-111">If your code was dependent on default value calculation for <xref:System.Net.Cookie.Path>, consider supplying the <xref:System.Net.Cookie.Path> value manually instead of using the default value.</span></span>

#### <a name="category"></a><span data-ttu-id="027bf-112">類別</span><span class="sxs-lookup"><span data-stu-id="027bf-112">Category</span></span>

<span data-ttu-id="027bf-113">網路功能</span><span class="sxs-lookup"><span data-stu-id="027bf-113">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="027bf-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="027bf-114">Affected APIs</span></span>

- <xref:System.Net.Cookie?displayProperty=fullName>
- <xref:System.Net.CookieContainer?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Net.Cookie`
- `T:System.Net.CookieContainer`

-->
