---
ms.openlocfilehash: c0551fa086644497c631cd9b6d7058398ff9ccfa
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702269"
---
### <a name="c-locale-maps-to-the-invariant-locale"></a><span data-ttu-id="6376c-101">"C" 地區設定對應至不變的地區設定</span><span class="sxs-lookup"><span data-stu-id="6376c-101">"C" locale maps to the invariant locale</span></span>

<span data-ttu-id="6376c-102">.NET Core 2.2 及更早版本相依于預設的 ICU 行為，此行為會將 "C" 地區設定對應至 en_US_POSIX 地區設定。</span><span class="sxs-lookup"><span data-stu-id="6376c-102">.NET Core 2.2 and earlier versions depend on the default ICU behavior, which maps the "C" locale to the en_US_POSIX locale.</span></span> <span data-ttu-id="6376c-103">En_US_POSIX 地區設定有不必要的定序行為，因為它不支援不區分大小寫的字串比較。</span><span class="sxs-lookup"><span data-stu-id="6376c-103">The en_US_POSIX locale has an undesirable collation behavior, because it doesn't support case-insensitive string comparisons.</span></span> <span data-ttu-id="6376c-104">因為某些 Linux 發行版本會將 "C" 地區設定設定為預設地區設定，所以使用者會遇到非預期的行為。</span><span class="sxs-lookup"><span data-stu-id="6376c-104">Because some Linux distributions set the "C" locale as the default locale, users were experiencing unexpected behavior.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6376c-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="6376c-105">Change description</span></span>

<span data-ttu-id="6376c-106">從 .NET Core 3.0 開始，"C" 地區設定對應已變更為使用不變的地區設定，而不是 en_US_POSIX。</span><span class="sxs-lookup"><span data-stu-id="6376c-106">Starting with .NET Core 3.0, the "C" locale mapping has changed to use the Invariant locale instead of en_US_POSIX.</span></span> <span data-ttu-id="6376c-107">「非變異」對應的 "C" 地區設定也適用于 Windows，以保持一致性。</span><span class="sxs-lookup"><span data-stu-id="6376c-107">The "C" locale to Invariant mapping is also applied to Windows for consistency.</span></span>

<span data-ttu-id="6376c-108">將 "C" 對應至 en_US_POSIX 文化特性會造成客戶的混淆，因為 en_US_POSIX 不支援不區分大小寫的排序/搜尋字串作業。</span><span class="sxs-lookup"><span data-stu-id="6376c-108">Mapping "C" to en_US_POSIX culture caused customer confusion, because en_US_POSIX doesn't support case insensitive sorting/searching string operations.</span></span> <span data-ttu-id="6376c-109">因為 "C" 地區設定在某些 Linux 散發版本中是用來做為預設的地區設定，所以客戶在這些作業系統上遇到這類不想要的行為。</span><span class="sxs-lookup"><span data-stu-id="6376c-109">Because the "C" locale is used as a default locale in some of the Linux distros, customers experienced this undesired behavior on these operating systems.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6376c-110">引進的版本</span><span class="sxs-lookup"><span data-stu-id="6376c-110">Version introduced</span></span>

<span data-ttu-id="6376c-111">3.0</span><span class="sxs-lookup"><span data-stu-id="6376c-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6376c-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="6376c-112">Recommended action</span></span>

<span data-ttu-id="6376c-113">這項變更不會有任何特定的功能。</span><span class="sxs-lookup"><span data-stu-id="6376c-113">Nothing specific more than the awareness of this change.</span></span> <span data-ttu-id="6376c-114">這種變更只會影響使用 "C" 地區設定對應的應用程式。</span><span class="sxs-lookup"><span data-stu-id="6376c-114">This change affects only applications that use the "C" locale mapping.</span></span>

#### <a name="category"></a><span data-ttu-id="6376c-115">類別</span><span class="sxs-lookup"><span data-stu-id="6376c-115">Category</span></span>

<span data-ttu-id="6376c-116">全球化</span><span class="sxs-lookup"><span data-stu-id="6376c-116">Globalization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6376c-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="6376c-117">Affected APIs</span></span>

<span data-ttu-id="6376c-118">所有定序和文化特性 Api 都會受到這項變更的影響。</span><span class="sxs-lookup"><span data-stu-id="6376c-118">All collation and culture APIs are affected by this change.</span></span>

<!--

#### Affected APIs

-->
