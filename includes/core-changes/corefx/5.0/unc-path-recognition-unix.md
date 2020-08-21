---
ms.openlocfilehash: 0246f325a6274082b7fb0d5590cec7c80687ae85
ms.sourcegitcommit: ef86c24c418439b8bb5e3e7d64bbdbe5e11c3e9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2020
ms.locfileid: "88720178"
---
### <a name="uri-recognition-of-unc-paths-on-unix"></a><span data-ttu-id="d5597-101">Unix 上 UNC 路徑的 Uri 識別</span><span class="sxs-lookup"><span data-stu-id="d5597-101">Uri recognition of UNC paths on Unix</span></span>

<span data-ttu-id="d5597-102"><xref:System.Uri>類別現在會辨識開頭為兩個正斜線的字串 (`//`) 為 Unix 作業系統上 (UNC) 路徑的通用命名慣例。</span><span class="sxs-lookup"><span data-stu-id="d5597-102">The <xref:System.Uri> class now recognizes strings that start with two forward slashes (`//`) as universal naming convention (UNC) paths on Unix operating systems.</span></span> <span data-ttu-id="d5597-103">這種變更讓這類字串在所有平臺上都是一致的。</span><span class="sxs-lookup"><span data-stu-id="d5597-103">This change makes the behavior for such strings consistent across all platforms.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d5597-104">變更描述</span><span class="sxs-lookup"><span data-stu-id="d5597-104">Change description</span></span>

<span data-ttu-id="d5597-105">在舊版的 .NET 中， <xref:System.Uri> 類別會辨識開頭為兩個正斜線（例如，）的字串， `//contoso` 做為 Unix 作業系統的絕對檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="d5597-105">In previous versions of .NET, the <xref:System.Uri> class recognizes strings that start with with two forward slashes, for example, `//contoso`, as absolute file paths on Unix operating systems.</span></span> <span data-ttu-id="d5597-106">不過，在 Windows 上，這類字串會被辨識為 UNC 路徑。</span><span class="sxs-lookup"><span data-stu-id="d5597-106">However, on Windows, such strings are recognized as UNC paths.</span></span>

<span data-ttu-id="d5597-107">從 .NET 5.0 開始，此 <xref:System.Uri> 類別會辨識以兩個正斜線作為所有平臺（包括 Unix）上之 UNC 路徑開頭的字串。</span><span class="sxs-lookup"><span data-stu-id="d5597-107">Starting in .NET 5.0,  the <xref:System.Uri> class recognizes strings that start with with two forward slashes as UNC paths on all platforms, including Unix.</span></span> <span data-ttu-id="d5597-108">此外，屬性會根據 UNC 語義而行為：</span><span class="sxs-lookup"><span data-stu-id="d5597-108">In addition, properties behave according to UNC semantics:</span></span>

- <span data-ttu-id="d5597-109"><xref:System.Uri.IsUnc?displayProperty=nameWithType> 會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="d5597-109"><xref:System.Uri.IsUnc?displayProperty=nameWithType> returns `true`.</span></span>
- <span data-ttu-id="d5597-110">路徑中的反斜線會以正斜線取代。</span><span class="sxs-lookup"><span data-stu-id="d5597-110">Backslashes in the path are replaced with forward slashes.</span></span> <span data-ttu-id="d5597-111">例如，`//first\second` 會成為 `//first/second`。</span><span class="sxs-lookup"><span data-stu-id="d5597-111">For example, `//first\second` becomes `//first/second`.</span></span>
- <span data-ttu-id="d5597-112"><xref:System.Uri.LocalPath?displayProperty=nameWithType> 不以百分比編碼的字元。</span><span class="sxs-lookup"><span data-stu-id="d5597-112"><xref:System.Uri.LocalPath?displayProperty=nameWithType> doesn't percent-encode characters.</span></span> <span data-ttu-id="d5597-113">例如， `//first/\uFFF0` *不* 會轉換成 `//first/%EF%BF%B0` 。</span><span class="sxs-lookup"><span data-stu-id="d5597-113">For example, `//first/\uFFF0` is *not* converted to `//first/%EF%BF%B0`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d5597-114">引進的版本</span><span class="sxs-lookup"><span data-stu-id="d5597-114">Version introduced</span></span>

<span data-ttu-id="d5597-115">5.0</span><span class="sxs-lookup"><span data-stu-id="d5597-115">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d5597-116">建議的動作</span><span class="sxs-lookup"><span data-stu-id="d5597-116">Recommended action</span></span>

<span data-ttu-id="d5597-117">開發人員不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="d5597-117">No action is required on the part of the developer.</span></span>

#### <a name="category"></a><span data-ttu-id="d5597-118">類別</span><span class="sxs-lookup"><span data-stu-id="d5597-118">Category</span></span>

<span data-ttu-id="d5597-119">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="d5597-119">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d5597-120">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="d5597-120">Affected APIs</span></span>

- <xref:System.Uri?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Uri`

-->
