---
ms.openlocfilehash: fdbe8ca9b6dbf24c08a2d041c5c7f2e869995f69
ms.sourcegitcommit: b1f4756120deaecb8b554477bb040620f69a4209
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2020
ms.locfileid: "89414446"
---
### <a name="cookie-path-handling-now-conforms-to-rfc-6265"></a><span data-ttu-id="c96df-101">Cookie 路徑處理現在符合 RFC 6265</span><span class="sxs-lookup"><span data-stu-id="c96df-101">Cookie Path handling now conforms to RFC 6265</span></span>

<span data-ttu-id="c96df-102">[RFC 6265](https://tools.ietf.org/html/rfc6265)中定義的路徑處理演算法已針對 `Cookie` 和 `CookieContainer` 類別實作為。</span><span class="sxs-lookup"><span data-stu-id="c96df-102">Path handling algorithms defined in [RFC 6265](https://tools.ietf.org/html/rfc6265) were implemented for `Cookie` and `CookieContainer` classes.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c96df-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="c96df-103">Version introduced</span></span>

<span data-ttu-id="c96df-104">5.0</span><span class="sxs-lookup"><span data-stu-id="c96df-104">5.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="c96df-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="c96df-105">Change description</span></span>

- <span data-ttu-id="c96df-106">將 `Path` 會移除此屬性的限制， (不會再是要求路徑) 的前置詞。</span><span class="sxs-lookup"><span data-stu-id="c96df-106">Restriction for the `Path` attribute is removed (it's no longer expected to be a prefix of the request path).</span></span>
- <span data-ttu-id="c96df-107">的預設值和路徑比對演算法的計算 `Path` 是依照 RFC 6265 的 [5.1.4 一節](https://tools.ietf.org/html/rfc6265#section-5.1.4) 中的定義來執行。</span><span class="sxs-lookup"><span data-stu-id="c96df-107">Calculation of the default value of `Path` and path matching algorithms were implemented as defined in [section 5.1.4](https://tools.ietf.org/html/rfc6265#section-5.1.4) of RFC 6265.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c96df-108">建議的動作</span><span class="sxs-lookup"><span data-stu-id="c96df-108">Recommended action</span></span>

<span data-ttu-id="c96df-109">在大多數情況下，您不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="c96df-109">In most cases, you won't need to take any action.</span></span> <span data-ttu-id="c96df-110">但是，如果您的程式碼相依于 `Path` 驗證，則您必須在程式碼中執行必要的驗證; 或者，如果您的程式碼相依于 `Path` 的預設值計算，您可能會想要 `Path` 手動提供值，而不是使用預設值。</span><span class="sxs-lookup"><span data-stu-id="c96df-110">However, if your code was dependent on `Path` validation you would need to implement required validation in your code; or if your code was dependent on `Path`'s default value calculation, you might want to supply the `Path` value manually instead of using the default value.</span></span>

#### <a name="category"></a><span data-ttu-id="c96df-111">類別</span><span class="sxs-lookup"><span data-stu-id="c96df-111">Category</span></span>

<span data-ttu-id="c96df-112">網路功能</span><span class="sxs-lookup"><span data-stu-id="c96df-112">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c96df-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="c96df-113">Affected APIs</span></span>

- <xref:System.Net.Cookie?displayProperty=fullName>
- <xref:System.Net.CookieContainer?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Net.Cookie`
- `T:System.Net.CookieContainer`

-->
