---
ms.openlocfilehash: d35de48dd22003c851cf5dba9e8517ec48b9217b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567768"
---
### <a name="c-locale-maps-to-the-invariant-locale"></a><span data-ttu-id="116ed-101">"C"地區設定映射到不變地區設定</span><span class="sxs-lookup"><span data-stu-id="116ed-101">"C" locale maps to the invariant locale</span></span>

<span data-ttu-id="116ed-102">.NET Core 2.2 和早期版本取決於預設 ICU 行為，該行為將"C"地區設定映射到en_US_POSIX地區設定。</span><span class="sxs-lookup"><span data-stu-id="116ed-102">.NET Core 2.2 and earlier versions depend on the default ICU behavior, which maps the "C" locale to the en_US_POSIX locale.</span></span> <span data-ttu-id="116ed-103">en_US_POSIX地區設定具有不可取的整理行為，因為它不支援不區分大小寫的字串比較。</span><span class="sxs-lookup"><span data-stu-id="116ed-103">The en_US_POSIX locale has an undesirable collation behavior, because it doesn't support case-insensitive string comparisons.</span></span> <span data-ttu-id="116ed-104">由於某些 Linux 發行版本將"C"地區設定設置為預設區域設置，因此使用者遇到意外行為。</span><span class="sxs-lookup"><span data-stu-id="116ed-104">Because some Linux distributions set the "C" locale as the default locale, users were experiencing unexpected behavior.</span></span>

#### <a name="change-description"></a><span data-ttu-id="116ed-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="116ed-105">Change description</span></span>

<span data-ttu-id="116ed-106">從 .NET Core 3.0 開始，"C"地區設定映射已更改為使用不變數地區設定，而不是en_US_POSIX。</span><span class="sxs-lookup"><span data-stu-id="116ed-106">Starting with .NET Core 3.0, the "C" locale mapping has changed to use the Invariant locale instead of en_US_POSIX.</span></span> <span data-ttu-id="116ed-107">"C"地區設定到不變數映射也應用於 Windows 以保持一致性。</span><span class="sxs-lookup"><span data-stu-id="116ed-107">The "C" locale to Invariant mapping is also applied to Windows for consistency.</span></span>

<span data-ttu-id="116ed-108">將"C"映射到en_US_POSIX區域性會導致客戶混淆，因為en_US_POSIX不支援不區分大小寫的排序/搜索字串操作。</span><span class="sxs-lookup"><span data-stu-id="116ed-108">Mapping "C" to en_US_POSIX culture caused customer confusion, because en_US_POSIX doesn't support case insensitive sorting/searching string operations.</span></span> <span data-ttu-id="116ed-109">由於"C"地區設定在某些 Linux 發行版本中用作預設區域設置，因此客戶在這些作業系統上遇到這種不希望的行為。</span><span class="sxs-lookup"><span data-stu-id="116ed-109">Because the "C" locale is used as a default locale in some of the Linux distros, customers experienced this undesired behavior on these operating systems.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="116ed-110">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="116ed-110">Version introduced</span></span>

<span data-ttu-id="116ed-111">3.0</span><span class="sxs-lookup"><span data-stu-id="116ed-111">3.0</span></span>

### <a name="recommended-action"></a><span data-ttu-id="116ed-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="116ed-112">Recommended action</span></span>

<span data-ttu-id="116ed-113">沒有什麼比對這種變化的認識更具體了。</span><span class="sxs-lookup"><span data-stu-id="116ed-113">Nothing specific more than the awareness of this change.</span></span> <span data-ttu-id="116ed-114">此更改僅影響使用"C"地區設定映射的應用程式。</span><span class="sxs-lookup"><span data-stu-id="116ed-114">This change affects only applications that use the "C" locale mapping.</span></span>

### <a name="category"></a><span data-ttu-id="116ed-115">類別</span><span class="sxs-lookup"><span data-stu-id="116ed-115">Category</span></span>

<span data-ttu-id="116ed-116">全球化</span><span class="sxs-lookup"><span data-stu-id="116ed-116">Globalization</span></span>

### <a name="affected-apis"></a><span data-ttu-id="116ed-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="116ed-117">Affected APIs</span></span>

<span data-ttu-id="116ed-118">所有排序規則和文化 API 都受此更改的影響。</span><span class="sxs-lookup"><span data-stu-id="116ed-118">All collation and culture APIs are affected by this change.</span></span>

<!--

-->
