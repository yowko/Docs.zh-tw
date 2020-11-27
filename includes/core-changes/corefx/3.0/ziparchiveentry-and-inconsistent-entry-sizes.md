---
ms.openlocfilehash: 8c8e87c885c99d28aa9a7a5d5a2b48c80d40d7db
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032039"
---
### <a name="ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes"></a><span data-ttu-id="3e814-101">ZipArchiveEntry 不再以不一致的專案大小處理封存</span><span class="sxs-lookup"><span data-stu-id="3e814-101">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>

<span data-ttu-id="3e814-102">Zip 封存會列出中央目錄和本機標頭中的壓縮大小和未壓縮大小。</span><span class="sxs-lookup"><span data-stu-id="3e814-102">Zip archives list both compressed size and uncompressed size in the central directory and local header.</span></span>  <span data-ttu-id="3e814-103">專案資料本身也會指出其大小。</span><span class="sxs-lookup"><span data-stu-id="3e814-103">The entry data itself also indicates its size.</span></span>  <span data-ttu-id="3e814-104">在 .NET Core 2.2 及更早版本中，這些值絕對不會檢查一致性。</span><span class="sxs-lookup"><span data-stu-id="3e814-104">In .NET Core 2.2 and earlier versions, these values were never checked for consistency.</span></span> <span data-ttu-id="3e814-105">從 .NET Core 3.0 開始，它們現在是。</span><span class="sxs-lookup"><span data-stu-id="3e814-105">Starting with .NET Core 3.0, they now are.</span></span>

#### <a name="change-description"></a><span data-ttu-id="3e814-106">變更描述</span><span class="sxs-lookup"><span data-stu-id="3e814-106">Change description</span></span>

<span data-ttu-id="3e814-107">在 .NET Core 2.2 及更早版本中， <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> 即使本機標頭是以 zip 檔案的中央標頭不同意，也會成功。</span><span class="sxs-lookup"><span data-stu-id="3e814-107">In .NET Core 2.2 and earlier versions, <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> succeeds even if the local header disagrees with the central header of the zip file.</span></span> <span data-ttu-id="3e814-108">除非壓縮資料流程結束，否則資料會進行解壓縮，即使其長度超過中央目錄/本機標頭中所列的未壓縮檔案大小。</span><span class="sxs-lookup"><span data-stu-id="3e814-108">Data is decompressed until the end of the compressed stream is reached, even if its length exceeds the uncompressed file size listed in the central directory/local header.</span></span>

<span data-ttu-id="3e814-109">從 .NET Core 3.0 開始，此 <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> 方法會檢查本機標頭和中央標頭是否同意專案的壓縮和未壓縮大小。</span><span class="sxs-lookup"><span data-stu-id="3e814-109">Starting with .NET Core 3.0, the <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> method checks that local header and central header agree on compressed and uncompressed sizes of an entry.</span></span>  <span data-ttu-id="3e814-110">如果沒有，則方法會在封存 <xref:System.IO.InvalidDataException> 的本機標頭和/或資料描述項清單大小與 zip 檔案的中央目錄不一致時擲回。</span><span class="sxs-lookup"><span data-stu-id="3e814-110">If they do not, the method throws an <xref:System.IO.InvalidDataException> if the archive's local header and/or data descriptor list sizes that disagree with the central directory of the zip file.</span></span> <span data-ttu-id="3e814-111">讀取專案時，解壓縮的資料會截斷為標頭中所列的未壓縮檔案大小。</span><span class="sxs-lookup"><span data-stu-id="3e814-111">When reading an entry, decompressed data is truncated to the uncompressed file size listed in the header.</span></span>

<span data-ttu-id="3e814-112">進行這項變更是為了確保 <xref:System.IO.Compression.ZipArchiveEntry> 正確表示其資料的大小，以及唯讀取該資料量。</span><span class="sxs-lookup"><span data-stu-id="3e814-112">This change was made to ensure that a <xref:System.IO.Compression.ZipArchiveEntry> correctly represents the size of its data and that only that amount of data is read.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3e814-113">引進的版本</span><span class="sxs-lookup"><span data-stu-id="3e814-113">Version introduced</span></span>

<span data-ttu-id="3e814-114">3.0</span><span class="sxs-lookup"><span data-stu-id="3e814-114">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3e814-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="3e814-115">Recommended action</span></span>

<span data-ttu-id="3e814-116">重新封裝任何展示這些問題的 zip 封存。</span><span class="sxs-lookup"><span data-stu-id="3e814-116">Repackage any zip archive that exhibits these problems.</span></span>

#### <a name="category"></a><span data-ttu-id="3e814-117">類別</span><span class="sxs-lookup"><span data-stu-id="3e814-117">Category</span></span>

<span data-ttu-id="3e814-118">CoreFx</span><span class="sxs-lookup"><span data-stu-id="3e814-118">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3e814-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="3e814-119">Affected APIs</span></span>

- <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFileExtensions.ExtractToDirectory%2A?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.ExtractToDirectory%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`M:System.IO.Compression.ZipArchiveEntry.Open`
`Overload:System.IO.Compression.ZipFileExtensions.ExtractToDirectory%2A`
`Overload:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A`
`Overload:System.IO.Compression.ZipFile.ExtractToDirectory%2A`

-->
