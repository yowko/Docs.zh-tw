---
ms.openlocfilehash: f9ae32c44e5648eb74d7eab9fa5aa6cc2f17b9a1
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237317"
---
### <a name="c-locale-maps-to-the-invariant-locale"></a><span data-ttu-id="62226-101">"C" 地區設定對應到不變的地區設定</span><span class="sxs-lookup"><span data-stu-id="62226-101">"C" locale maps to the invariant locale</span></span>

<span data-ttu-id="62226-102">.NET Core 2.2 和更早版本取決於預設的 ICU 行為，這會將 "C" 地區設定對應至 en_US_POSIX 地區設定。</span><span class="sxs-lookup"><span data-stu-id="62226-102">.NET Core 2.2 and earlier versions depend on the default ICU behavior, which maps the "C" locale to the en_US_POSIX locale.</span></span> <span data-ttu-id="62226-103">En_US_POSIX 地區設定有不想要的定序行為，因為它不支援不區分大小寫的字串比較。</span><span class="sxs-lookup"><span data-stu-id="62226-103">The en_US_POSIX locale has an undesirable collation behavior, because it doesn't support case-insensitive string comparisons.</span></span> <span data-ttu-id="62226-104">由於某些 Linux 散發套件會將 "C" 地區設定設為預設地區設定，因此使用者會遇到非預期的行為。</span><span class="sxs-lookup"><span data-stu-id="62226-104">Because some Linux distributions set the "C" locale as the default locale, users were experiencing unexpected behavior.</span></span> 

#### <a name="change-description"></a><span data-ttu-id="62226-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="62226-105">Change description</span></span>

<span data-ttu-id="62226-106">從 .NET Core 3.0 開始，"C" 地區設定對應已變更為使用不變的地區設定，而不是 en_US_POSIX。</span><span class="sxs-lookup"><span data-stu-id="62226-106">Starting with .NET Core 3.0, the "C" locale mapping has changed to use the Invariant locale instead of en_US_POSIX.</span></span> <span data-ttu-id="62226-107">非變異對應的 "C" 地區設定也會套用至 Windows 以保持一致性。</span><span class="sxs-lookup"><span data-stu-id="62226-107">The "C" locale to Invariant mapping is also applied to Windows for consistency.</span></span>

<span data-ttu-id="62226-108">將 "C" 對應至 en_US_POSIX 文化特性會造成客戶混淆，因為 en_US_POSIX 不支援不區分大小寫的排序/搜尋字串作業。</span><span class="sxs-lookup"><span data-stu-id="62226-108">Mapping "C" to en_US_POSIX culture caused customer confusion, because en_US_POSIX doesn't support case insensitive sorting/searching string operations.</span></span> <span data-ttu-id="62226-109">因為在某些 Linux 散發版本中，會使用 "C" 地區設定做為預設地區設定，所以客戶會在這些作業系統上遇到此不想要的行為。</span><span class="sxs-lookup"><span data-stu-id="62226-109">Because the "C" locale is used as a default locale in some of the Linux distros, customers experienced this undesired behavior on these operating systems.</span></span> 

#### <a name="version-introduced"></a><span data-ttu-id="62226-110">引進的版本</span><span class="sxs-lookup"><span data-stu-id="62226-110">Version introduced</span></span>

<span data-ttu-id="62226-111">3.0</span><span class="sxs-lookup"><span data-stu-id="62226-111">3.0</span></span>

### <a name="recommended-action"></a><span data-ttu-id="62226-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="62226-112">Recommended action</span></span>

<span data-ttu-id="62226-113">除了這項變更的認知以外，沒有任何特定的內容。</span><span class="sxs-lookup"><span data-stu-id="62226-113">Nothing specific more than the awareness of this change.</span></span> <span data-ttu-id="62226-114">這種變更只會影響使用 "C" 地區設定對應的應用程式。</span><span class="sxs-lookup"><span data-stu-id="62226-114">This change affects only applications that use the "C" locale mapping.</span></span>

### <a name="category"></a><span data-ttu-id="62226-115">Category</span><span class="sxs-lookup"><span data-stu-id="62226-115">Category</span></span>

<span data-ttu-id="62226-116">全球化</span><span class="sxs-lookup"><span data-stu-id="62226-116">Globalization</span></span> 

### <a name="affected-apis"></a><span data-ttu-id="62226-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="62226-117">Affected APIs</span></span>

<span data-ttu-id="62226-118">所有定序和文化特性 Api 都會受到這項變更的影響。</span><span class="sxs-lookup"><span data-stu-id="62226-118">All collation and culture APIs are affected by this change.</span></span>

<!--

-->
