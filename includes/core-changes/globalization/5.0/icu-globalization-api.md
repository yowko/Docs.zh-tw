---
ms.openlocfilehash: 18718ebc934e0175c20411055b8c0a90ef6b175f
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539448"
---
### <a name="globalization-apis-use-icu-libraries-on-windows"></a><span data-ttu-id="72cc9-101">全球化 Api 在 Windows 上使用 ICU 程式庫</span><span class="sxs-lookup"><span data-stu-id="72cc9-101">Globalization APIs use ICU libraries on Windows</span></span>

<span data-ttu-id="72cc9-102">.NET 5.0 和更新版本會在 Windows 10 2019 年5月更新或更新版本上執行時，使用 [Unicode (ICU) ](http://site.icu-project.org/home) 程式庫的全球化功能。</span><span class="sxs-lookup"><span data-stu-id="72cc9-102">.NET 5.0 and later versions use [International Components for Unicode (ICU)](http://site.icu-project.org/home) libraries for globalization functionality when running on Windows 10 May 2019 Update or later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="72cc9-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="72cc9-103">Change description</span></span>

<span data-ttu-id="72cc9-104">先前，.NET 程式庫使用 [國家語言支援 (NLS) ](/windows/win32/intl/national-language-support) api 來提供全球化功能。</span><span class="sxs-lookup"><span data-stu-id="72cc9-104">Previously, .NET libraries used [National Language Support (NLS)](/windows/win32/intl/national-language-support) APIs for globalization functionality.</span></span> <span data-ttu-id="72cc9-105">例如，使用 NLS 函數來取得文化特性資料，例如日期和時間格式模式、比較字串，以及在適當的文化特性中執行字串大小寫。</span><span class="sxs-lookup"><span data-stu-id="72cc9-105">For example, NLS functions were used to get culture data, such as date and time format patterns, compare strings, and perform string casing in the appropriate culture.</span></span>

<span data-ttu-id="72cc9-106">從 .NET 5.0 開始，如果應用程式在 Windows 10 2019 年5月更新或更新版本上執行，則 .NET 程式庫會使用 [ICU](http://site.icu-project.org/home) 全球化 api。</span><span class="sxs-lookup"><span data-stu-id="72cc9-106">Starting in .NET 5.0, if an app is running on Windows 10 May 2019 Update or later, .NET libraries use [ICU](http://site.icu-project.org/home) globalization APIs.</span></span> <span data-ttu-id="72cc9-107">Windows 10 2019 年5月更新和更新版本隨附于 ICU 原生程式庫。</span><span class="sxs-lookup"><span data-stu-id="72cc9-107">Windows 10 May 2019 Update and later versions ship with the ICU native library.</span></span> <span data-ttu-id="72cc9-108">如果 .NET 執行時間無法載入 ICU，則會改為使用 NLS。</span><span class="sxs-lookup"><span data-stu-id="72cc9-108">If the .NET runtime can't load ICU, it uses NLS instead.</span></span>

<span data-ttu-id="72cc9-109">這種變更的引進原因有兩種：</span><span class="sxs-lookup"><span data-stu-id="72cc9-109">This change was introduced for two reasons:</span></span>

- <span data-ttu-id="72cc9-110">應用程式在各種平臺上都有相同的全球化行為，包括 Linux、macOS 和 Windows。</span><span class="sxs-lookup"><span data-stu-id="72cc9-110">Apps have the same globalization behavior across platforms, including Linux, macOS, and Windows.</span></span>
- <span data-ttu-id="72cc9-111">應用程式可以使用自訂的 ICU 程式庫來控制全球化行為。</span><span class="sxs-lookup"><span data-stu-id="72cc9-111">Apps can control globalization behavior by using custom ICU libraries.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="72cc9-112">引進的版本</span><span class="sxs-lookup"><span data-stu-id="72cc9-112">Version introduced</span></span>

<span data-ttu-id="72cc9-113">.NET 5.0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="72cc9-113">.NET 5.0 Preview 4</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="72cc9-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="72cc9-114">Recommended action</span></span>

<span data-ttu-id="72cc9-115">開發人員不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="72cc9-115">No action is required on the part of the developer.</span></span> <span data-ttu-id="72cc9-116">但是，如果您想要繼續使用 NLS 全球化 Api，您可以將 [執行時間參數](../../../../docs/core/run-time-config/globalization.md#nls) 設定為還原為該行為。</span><span class="sxs-lookup"><span data-stu-id="72cc9-116">However, if you wish to continue using NLS globalization APIs, you can set a [run-time switch](../../../../docs/core/run-time-config/globalization.md#nls) to revert to that behavior.</span></span> <span data-ttu-id="72cc9-117">如需可用參數的詳細資訊，請參閱 [.net 全球化和 ICU](../../../../docs/standard/globalization-localization/globalization-icu.md) 文章。</span><span class="sxs-lookup"><span data-stu-id="72cc9-117">For more information about the available switches, see the [.NET globalization and ICU](../../../../docs/standard/globalization-localization/globalization-icu.md) article.</span></span>

#### <a name="category"></a><span data-ttu-id="72cc9-118">類別</span><span class="sxs-lookup"><span data-stu-id="72cc9-118">Category</span></span>

<span data-ttu-id="72cc9-119">全球化</span><span class="sxs-lookup"><span data-stu-id="72cc9-119">Globalization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="72cc9-120">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="72cc9-120">Affected APIs</span></span>

- <xref:System.Span%601?displayProperty=fullName>
- <xref:System.String?displayProperty=fullName>
- <span data-ttu-id="72cc9-121">命名空間中的大部分類型 <xref:System.Globalization?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="72cc9-121">Most types in the <xref:System.Globalization?displayProperty=fullName> namespace</span></span>

<!--

#### Affected APIs

- ``T:System.Span`1``
- `T:System.String`
- `N:System.Globalization`

-->
