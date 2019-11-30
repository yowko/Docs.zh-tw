---
ms.openlocfilehash: 9520f8c6b6671917f5694bc602293a00e2dab82d
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568182"
---
### <a name="ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes"></a><span data-ttu-id="6f780-101">Ziparchiveentry 中不再處理具有不一致專案大小的封存</span><span class="sxs-lookup"><span data-stu-id="6f780-101">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>

<span data-ttu-id="6f780-102">Zip 封存會列出中央目錄和本機標頭中的壓縮大小和未壓縮大小。</span><span class="sxs-lookup"><span data-stu-id="6f780-102">Zip archives list both compressed size and uncompressed size in the central directory and local header.</span></span>  <span data-ttu-id="6f780-103">專案資料本身也會指出其大小。</span><span class="sxs-lookup"><span data-stu-id="6f780-103">The entry data itself also indicates its size.</span></span>  <span data-ttu-id="6f780-104">在 .NET Core 2.2 和更早版本中，永遠不會檢查這些值是否一致。</span><span class="sxs-lookup"><span data-stu-id="6f780-104">In .NET Core 2.2 and earlier versions, these values were never checked for consistency.</span></span> <span data-ttu-id="6f780-105">從 .NET Core 3.0 開始，它們現在是。</span><span class="sxs-lookup"><span data-stu-id="6f780-105">Starting with .NET Core 3.0, they now are.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6f780-106">變更描述</span><span class="sxs-lookup"><span data-stu-id="6f780-106">Change description</span></span>

<span data-ttu-id="6f780-107">在 .NET Core 2.2 和更早版本中，即使本機標頭不同意的是 zip 檔案的中央標頭，<xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> 還是會成功。</span><span class="sxs-lookup"><span data-stu-id="6f780-107">In .NET Core 2.2 and earlier versions, <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> succeeds even if the local header disagrees with the central header of the zip file.</span></span> <span data-ttu-id="6f780-108">資料會解壓縮到已達到壓縮資料流程的結尾，即使其長度超過中央目錄/本機標頭中列出的未壓縮檔案大小也一樣。</span><span class="sxs-lookup"><span data-stu-id="6f780-108">Data is decompressed until the end of the compressed stream is reached, even if its length exceeds the uncompressed file size listed in the central directory/local header.</span></span>

<span data-ttu-id="6f780-109">從 .NET Core 3.0 開始，<xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> 方法會檢查本機標頭和中央標頭是否同意專案的壓縮和未壓縮大小。</span><span class="sxs-lookup"><span data-stu-id="6f780-109">Starting with .NET Core 3.0, the <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> method checks that local header and central header agree on compressed and uncompressed sizes of an entry.</span></span>  <span data-ttu-id="6f780-110">如果沒有，則如果封存的本機標頭和/或資料描述項清單大小與 zip 檔案的中央目錄不一致，方法就會擲回 <xref:System.IO.InvalidDataException>。</span><span class="sxs-lookup"><span data-stu-id="6f780-110">If they do not, the method throws an <xref:System.IO.InvalidDataException> if the archive's local header and/or data descriptor list sizes that disagree with the central directory of the zip file.</span></span> <span data-ttu-id="6f780-111">當讀取專案時，解壓縮的資料會被截斷為標頭中所列的未壓縮檔案大小。</span><span class="sxs-lookup"><span data-stu-id="6f780-111">When reading an entry, decompressed data is truncated to the uncompressed file size listed in the header.</span></span>

<span data-ttu-id="6f780-112">這項變更是為了確保 <xref:System.IO.Compression.ZipArchiveEntry> 正確地代表其資料大小，而且只會讀取該資料量。</span><span class="sxs-lookup"><span data-stu-id="6f780-112">This change was made to ensure that a <xref:System.IO.Compression.ZipArchiveEntry> correctly represents the size of its data and that only that amount of data is read.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6f780-113">引進的版本</span><span class="sxs-lookup"><span data-stu-id="6f780-113">Version introduced</span></span>

<span data-ttu-id="6f780-114">3.0</span><span class="sxs-lookup"><span data-stu-id="6f780-114">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6f780-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="6f780-115">Recommended action</span></span>

<span data-ttu-id="6f780-116">重新封裝任何展示這些問題的 zip 封存。</span><span class="sxs-lookup"><span data-stu-id="6f780-116">Repackage any zip archive that exhibits these problems.</span></span>

#### <a name="category"></a><span data-ttu-id="6f780-117">Category</span><span class="sxs-lookup"><span data-stu-id="6f780-117">Category</span></span>

<span data-ttu-id="6f780-118">CoreFx</span><span class="sxs-lookup"><span data-stu-id="6f780-118">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6f780-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="6f780-119">Affected APIs</span></span>

- <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFileExtensions.ExtractToDirectory%2A?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.ExtractToDirectory%2A?displayProperty=nameWithType>

<!--

### Affected APIs

`M:System.IO.Compression.ZipArchiveEntry.Open`
`Overload:System.IO.Compression.ZipFileExtensions.ExtractToDirectory%2A`
`Overload:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A`
`Overload:System.IO.Compression.ZipFile.ExtractToDirectory%2A`

-->
