---
title: 重大變更： Unix 上 UNC 路徑的 Uri 識別
description: 瞭解核心 .NET 程式庫中的 .NET 5.0 重大變更，其中 Uri 類別現在會辨識開頭為兩個正斜線的字串，做為 Unix 上的 UNC 路徑。
ms.date: 11/01/2020
ms.openlocfilehash: 0d5d9cd8dd869f24e94d15724e5e16eaddf6ed47
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760457"
---
# <a name="uri-recognition-of-unc-paths-on-unix"></a><span data-ttu-id="8344e-103">Unix 上 UNC 路徑的 Uri 識別</span><span class="sxs-lookup"><span data-stu-id="8344e-103">Uri recognition of UNC paths on Unix</span></span>

<span data-ttu-id="8344e-104"><xref:System.Uri>類別現在會辨識開頭為兩個正斜線的字串 (`//`) 為 Unix 作業系統上 (UNC) 路徑的通用命名慣例。</span><span class="sxs-lookup"><span data-stu-id="8344e-104">The <xref:System.Uri> class now recognizes strings that start with two forward slashes (`//`) as universal naming convention (UNC) paths on Unix operating systems.</span></span> <span data-ttu-id="8344e-105">這種變更讓這類字串在所有平臺上都是一致的。</span><span class="sxs-lookup"><span data-stu-id="8344e-105">This change makes the behavior for such strings consistent across all platforms.</span></span>

## <a name="change-description"></a><span data-ttu-id="8344e-106">變更描述</span><span class="sxs-lookup"><span data-stu-id="8344e-106">Change description</span></span>

<span data-ttu-id="8344e-107">在舊版的 .NET 中， <xref:System.Uri> 類別會辨識開頭為兩個正斜線（例如，）的字串， `//contoso` 做為 Unix 作業系統的絕對檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="8344e-107">In previous versions of .NET, the <xref:System.Uri> class recognizes strings that start with two forward slashes, for example, `//contoso`, as absolute file paths on Unix operating systems.</span></span> <span data-ttu-id="8344e-108">不過，在 Windows 上，這類字串會被辨識為 UNC 路徑。</span><span class="sxs-lookup"><span data-stu-id="8344e-108">However, on Windows, such strings are recognized as UNC paths.</span></span>

<span data-ttu-id="8344e-109">從 .NET 5.0 開始， <xref:System.Uri> 類別會辨識開頭為兩個正斜線的字串，做為所有平臺（包括 Unix）上的 UNC 路徑。</span><span class="sxs-lookup"><span data-stu-id="8344e-109">Starting in .NET 5.0,  the <xref:System.Uri> class recognizes strings that start with two forward slashes as UNC paths on all platforms, including Unix.</span></span> <span data-ttu-id="8344e-110">此外，屬性會根據 UNC 語義而行為：</span><span class="sxs-lookup"><span data-stu-id="8344e-110">In addition, properties behave according to UNC semantics:</span></span>

- <span data-ttu-id="8344e-111"><xref:System.Uri.IsUnc?displayProperty=nameWithType> 會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="8344e-111"><xref:System.Uri.IsUnc?displayProperty=nameWithType> returns `true`.</span></span>
- <span data-ttu-id="8344e-112">路徑中的反斜線會以正斜線取代。</span><span class="sxs-lookup"><span data-stu-id="8344e-112">Backslashes in the path are replaced with forward slashes.</span></span> <span data-ttu-id="8344e-113">例如，`//first\second` 會成為 `//first/second`。</span><span class="sxs-lookup"><span data-stu-id="8344e-113">For example, `//first\second` becomes `//first/second`.</span></span>
- <span data-ttu-id="8344e-114"><xref:System.Uri.LocalPath?displayProperty=nameWithType> 不以百分比編碼的字元。</span><span class="sxs-lookup"><span data-stu-id="8344e-114"><xref:System.Uri.LocalPath?displayProperty=nameWithType> doesn't percent-encode characters.</span></span> <span data-ttu-id="8344e-115">例如， `//first/\uFFF0` *不* 會轉換成 `//first/%EF%BF%B0` 。</span><span class="sxs-lookup"><span data-stu-id="8344e-115">For example, `//first/\uFFF0` is *not* converted to `//first/%EF%BF%B0`.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="8344e-116">引進的版本</span><span class="sxs-lookup"><span data-stu-id="8344e-116">Version introduced</span></span>

<span data-ttu-id="8344e-117">5.0</span><span class="sxs-lookup"><span data-stu-id="8344e-117">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="8344e-118">建議的動作</span><span class="sxs-lookup"><span data-stu-id="8344e-118">Recommended action</span></span>

<span data-ttu-id="8344e-119">開發人員不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="8344e-119">No action is required on the part of the developer.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="8344e-120">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="8344e-120">Affected APIs</span></span>

- <xref:System.Uri?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `T:System.Uri`

-->
