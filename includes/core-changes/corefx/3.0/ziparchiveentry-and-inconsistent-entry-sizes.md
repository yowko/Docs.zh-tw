---
ms.openlocfilehash: 9520f8c6b6671917f5694bc602293a00e2dab82d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568182"
---
### <a name="ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes"></a><span data-ttu-id="32451-101">ZipArchiveEntry 不再處理條目大小不一致的存檔</span><span class="sxs-lookup"><span data-stu-id="32451-101">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>

<span data-ttu-id="32451-102">Zip 存檔在中央目錄和本地標頭中列出了壓縮大小和未壓縮大小。</span><span class="sxs-lookup"><span data-stu-id="32451-102">Zip archives list both compressed size and uncompressed size in the central directory and local header.</span></span>  <span data-ttu-id="32451-103">條目資料本身也指示其大小。</span><span class="sxs-lookup"><span data-stu-id="32451-103">The entry data itself also indicates its size.</span></span>  <span data-ttu-id="32451-104">在 .NET Core 2.2 和早期版本中，從未檢查過這些值的一致性。</span><span class="sxs-lookup"><span data-stu-id="32451-104">In .NET Core 2.2 and earlier versions, these values were never checked for consistency.</span></span> <span data-ttu-id="32451-105">從 .NET 核心 3.0 開始，它們現在就是.</span><span class="sxs-lookup"><span data-stu-id="32451-105">Starting with .NET Core 3.0, they now are.</span></span>

#### <a name="change-description"></a><span data-ttu-id="32451-106">變更描述</span><span class="sxs-lookup"><span data-stu-id="32451-106">Change description</span></span>

<span data-ttu-id="32451-107">在 .NET Core 2.2<xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType>和早期版本中，即使本地標頭與 ZIP 檔案的中央標頭不同，也會成功。</span><span class="sxs-lookup"><span data-stu-id="32451-107">In .NET Core 2.2 and earlier versions, <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> succeeds even if the local header disagrees with the central header of the zip file.</span></span> <span data-ttu-id="32451-108">資料將解壓縮，直到達到壓縮流的末尾，即使資料的長度超過中央目錄/本地標頭中列出的未壓縮檔案大小。</span><span class="sxs-lookup"><span data-stu-id="32451-108">Data is decompressed until the end of the compressed stream is reached, even if its length exceeds the uncompressed file size listed in the central directory/local header.</span></span>

<span data-ttu-id="32451-109">從 .NET Core 3.0<xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType>開始，該方法檢查本地標頭和中央標頭同意條目的壓縮和未壓縮大小。</span><span class="sxs-lookup"><span data-stu-id="32451-109">Starting with .NET Core 3.0, the <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> method checks that local header and central header agree on compressed and uncompressed sizes of an entry.</span></span>  <span data-ttu-id="32451-110">否則，如果存檔的本地標頭和/<xref:System.IO.InvalidDataException>或資料描述項清單大小與 ZIP 檔案的中央目錄不同，則該方法將引發 。</span><span class="sxs-lookup"><span data-stu-id="32451-110">If they do not, the method throws an <xref:System.IO.InvalidDataException> if the archive's local header and/or data descriptor list sizes that disagree with the central directory of the zip file.</span></span> <span data-ttu-id="32451-111">讀取條目時，解壓縮資料將被截斷到標頭中列出的未壓縮檔案大小。</span><span class="sxs-lookup"><span data-stu-id="32451-111">When reading an entry, decompressed data is truncated to the uncompressed file size listed in the header.</span></span>

<span data-ttu-id="32451-112">進行此更改是為了確保正確<xref:System.IO.Compression.ZipArchiveEntry>表示其資料的大小，並且僅讀取該資料量。</span><span class="sxs-lookup"><span data-stu-id="32451-112">This change was made to ensure that a <xref:System.IO.Compression.ZipArchiveEntry> correctly represents the size of its data and that only that amount of data is read.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="32451-113">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="32451-113">Version introduced</span></span>

<span data-ttu-id="32451-114">3.0</span><span class="sxs-lookup"><span data-stu-id="32451-114">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="32451-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="32451-115">Recommended action</span></span>

<span data-ttu-id="32451-116">重新封包出現這些問題的任何 zip 存檔。</span><span class="sxs-lookup"><span data-stu-id="32451-116">Repackage any zip archive that exhibits these problems.</span></span>

#### <a name="category"></a><span data-ttu-id="32451-117">類別</span><span class="sxs-lookup"><span data-stu-id="32451-117">Category</span></span>

<span data-ttu-id="32451-118">CoreFx</span><span class="sxs-lookup"><span data-stu-id="32451-118">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="32451-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="32451-119">Affected APIs</span></span>

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
