---
ms.openlocfilehash: 49041ce906ab0bb8b9482b79c44302465c4ca788
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702286"
---
### <a name="globalization-apis-use-icu-libraries-on-windows"></a><span data-ttu-id="24f4c-101">全球化 Api 在 Windows 上使用 ICU 程式庫</span><span class="sxs-lookup"><span data-stu-id="24f4c-101">Globalization APIs use ICU libraries on Windows</span></span>

<span data-ttu-id="24f4c-102">.NET 5.0 和更新版本在 Windows 10 2019 更新或更新版本上執行時，會使用[Unicode （ICU）](http://site.icu-project.org/home)程式庫的國際元件來取得全球化功能。</span><span class="sxs-lookup"><span data-stu-id="24f4c-102">.NET 5.0 and later versions use [International Components for Unicode (ICU)](http://site.icu-project.org/home) libraries for globalization functionality when running on Windows 10 May 2019 Update or later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="24f4c-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="24f4c-103">Change description</span></span>

<span data-ttu-id="24f4c-104">之前，.NET 程式庫使用了全球化功能的[國家語言支援（NLS）](/windows/win32/intl/national-language-support) api。</span><span class="sxs-lookup"><span data-stu-id="24f4c-104">Previously, .NET libraries used [National Language Support (NLS)](/windows/win32/intl/national-language-support) APIs for globalization functionality.</span></span> <span data-ttu-id="24f4c-105">例如，NLS 函數是用來取得文化特性資料，例如日期和時間格式模式、比較字串，以及在適當的文化特性中執行字串大小寫。</span><span class="sxs-lookup"><span data-stu-id="24f4c-105">For example, NLS functions were used to get culture data, such as date and time format patterns, compare strings, and perform string casing in the appropriate culture.</span></span>

<span data-ttu-id="24f4c-106">從 .NET 5.0 開始，如果應用程式在 Windows 10 2019 更新或更新版本上執行，則 .NET 程式庫會使用[ICU](http://site.icu-project.org/home)全球化 api。</span><span class="sxs-lookup"><span data-stu-id="24f4c-106">Starting in .NET 5.0, if an app is running on Windows 10 May 2019 Update or later, .NET libraries use [ICU](http://site.icu-project.org/home) globalization APIs.</span></span> <span data-ttu-id="24f4c-107">Windows 10 5 月2019更新和更新版本隨附于 ICU 原生程式庫。</span><span class="sxs-lookup"><span data-stu-id="24f4c-107">Windows 10 May 2019 Update and later versions ship with the ICU native library.</span></span> <span data-ttu-id="24f4c-108">如果 .NET 執行時間無法載入 ICU，它會改為使用 NLS。</span><span class="sxs-lookup"><span data-stu-id="24f4c-108">If the .NET runtime can't load ICU, it uses NLS instead.</span></span>

<span data-ttu-id="24f4c-109">這是基於兩個原因而引進的變更：</span><span class="sxs-lookup"><span data-stu-id="24f4c-109">This change was introduced for two reasons:</span></span>

- <span data-ttu-id="24f4c-110">應用程式在平臺上具有相同的全球化行為，包括 Linux、macOS 和 Windows。</span><span class="sxs-lookup"><span data-stu-id="24f4c-110">Apps have the same globalization behavior across platforms, including Linux, macOS, and Windows.</span></span>
- <span data-ttu-id="24f4c-111">應用程式可以使用自訂的 ICU 程式庫來控制全球化行為。</span><span class="sxs-lookup"><span data-stu-id="24f4c-111">Apps can control globalization behavior by using custom ICU libraries.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="24f4c-112">引進的版本</span><span class="sxs-lookup"><span data-stu-id="24f4c-112">Version introduced</span></span>

<span data-ttu-id="24f4c-113">.NET 5.0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="24f4c-113">.NET 5.0 Preview 4</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="24f4c-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="24f4c-114">Recommended action</span></span>

<span data-ttu-id="24f4c-115">開發人員不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="24f4c-115">No action is required on the part of the developer.</span></span> <span data-ttu-id="24f4c-116">不過，如果您想要繼續使用 NLS 全球化 Api，您可以設定[執行時間參數](../../../../docs/core/run-time-config/globalization.md#nls)來還原為該行為。</span><span class="sxs-lookup"><span data-stu-id="24f4c-116">However, if you wish to continue using NLS globalization APIs, you can set a [run-time switch](../../../../docs/core/run-time-config/globalization.md#nls) to revert to that behavior.</span></span>

#### <a name="category"></a><span data-ttu-id="24f4c-117">類別</span><span class="sxs-lookup"><span data-stu-id="24f4c-117">Category</span></span>

<span data-ttu-id="24f4c-118">全球化</span><span class="sxs-lookup"><span data-stu-id="24f4c-118">Globalization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="24f4c-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="24f4c-119">Affected APIs</span></span>

- <xref:System.Span%601?displayProperty=fullName>
- <xref:System.String?displayProperty=fullName>
- <span data-ttu-id="24f4c-120">命名空間中的大部分類型 <xref:System.Globalization?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="24f4c-120">Most types in the <xref:System.Globalization?displayProperty=fullName> namespace</span></span>

<!--

#### Affected APIs

- `T:System.Span%601`
- `T:System.String`
- `N:System.Globalization`

-->