---
ms.openlocfilehash: 298cb441bf9fe7daddb30c85f9d7366dc972628c
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032030"
---
### <a name="replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines"></a><span data-ttu-id="a86b1-101">取代格式不正確的 UTF-8 位元組序列遵循 Unicode 指導方針</span><span class="sxs-lookup"><span data-stu-id="a86b1-101">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>

<span data-ttu-id="a86b1-102">當 <xref:System.Text.UTF8Encoding> 類別在位元組對字元轉碼作業期間遇到格式不正確的 utf-8 位元組序列時，會以輸出字串中的 ' ' (U + FFFD 取代字元) 字元來取代該序列。</span><span class="sxs-lookup"><span data-stu-id="a86b1-102">When the <xref:System.Text.UTF8Encoding> class encounters an ill-formed UTF-8 byte sequence during a byte-to-character transcoding operation, it replaces that sequence with a '�' (U+FFFD REPLACEMENT CHARACTER) character in the output string.</span></span> <span data-ttu-id="a86b1-103">.NET Core 3.0 與舊版的 .NET Core 和 .NET Framework 有不同之處，就是遵循在轉碼作業期間執行此取代的 Unicode 最佳做法。</span><span class="sxs-lookup"><span data-stu-id="a86b1-103">.NET Core 3.0 differs from previous versions of .NET Core and the .NET Framework by following the Unicode best practice for performing this replacement during the transcoding operation.</span></span>

<span data-ttu-id="a86b1-104">這是改善整個 .NET 的 UTF-8 處理工作的一部分，包括新的 <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> 和 <xref:System.Text.Rune?displayProperty=nameWithType> 類型。</span><span class="sxs-lookup"><span data-stu-id="a86b1-104">This is part of a larger effort to improve UTF-8 handling throughout .NET, including by the new <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> and <xref:System.Text.Rune?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="a86b1-105">此 <xref:System.Text.UTF8Encoding> 類型已獲得改良的錯誤處理機制，因此它會產生與新引進之類型一致的輸出。</span><span class="sxs-lookup"><span data-stu-id="a86b1-105">The <xref:System.Text.UTF8Encoding> type was given improved error handling mechanics so that it produces output consistent with the newly introduced types.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a86b1-106">變更描述</span><span class="sxs-lookup"><span data-stu-id="a86b1-106">Change description</span></span>

<span data-ttu-id="a86b1-107">從 .NET Core 3.0 開始，當轉碼位元組到字元時， <xref:System.Text.UTF8Encoding> 類別會根據 Unicode 最佳作法執行字元替代。</span><span class="sxs-lookup"><span data-stu-id="a86b1-107">Starting with .NET Core 3.0, when transcoding bytes to characters, the <xref:System.Text.UTF8Encoding> class performs character substitution based on Unicode best practices.</span></span> <span data-ttu-id="a86b1-108">使用的替代機制是以 [Unicode 標準12.0、Sec. 3.9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) 的標題標題為 _U + FFFD 的最大子零件替代_。</span><span class="sxs-lookup"><span data-stu-id="a86b1-108">The substitution mechanism used is described by [The Unicode Standard, Version 12.0, Sec. 3.9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) in the heading titled _U+FFFD Substitution of Maximal Subparts_.</span></span>

<span data-ttu-id="a86b1-109">只有當輸入位元組序列包含格式不正確的 UTF-8 資料時， _才_ 會套用此行為。</span><span class="sxs-lookup"><span data-stu-id="a86b1-109">This behavior _only_ applies when the input byte sequence contains ill-formed UTF-8 data.</span></span> <span data-ttu-id="a86b1-110">此外，如果 <xref:System.Text.UTF8Encoding> 已使用來建立實例 `throwOnInvalidBytes: true` ， `UTF8Encoding` 實例會繼續擲回不正確輸入，而不是執行 U + FFFD 取代。</span><span class="sxs-lookup"><span data-stu-id="a86b1-110">Additionally, if the <xref:System.Text.UTF8Encoding> instance has been constructed with `throwOnInvalidBytes: true`, the `UTF8Encoding` instance will continue to throw on invalid input rather than perform U+FFFD replacement.</span></span> <span data-ttu-id="a86b1-111">如需有關此函數的詳細資訊 `UTF8Encoding` ，請參閱 <xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)> 。</span><span class="sxs-lookup"><span data-stu-id="a86b1-111">For more information about the `UTF8Encoding` constructor, see <xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>.</span></span>

<span data-ttu-id="a86b1-112">下表說明這項變更的影響，以及不正確3位元組輸入：</span><span class="sxs-lookup"><span data-stu-id="a86b1-112">The following table illustrates the impact of this change with an invalid 3-byte input:</span></span>

| <span data-ttu-id="a86b1-113">3位元組格式錯誤的輸入</span><span class="sxs-lookup"><span data-stu-id="a86b1-113">Ill-formed 3-byte input</span></span> | <span data-ttu-id="a86b1-114">.NET Core 3.0 之前的輸出</span><span class="sxs-lookup"><span data-stu-id="a86b1-114">Output before .NET Core 3.0</span></span>          | <span data-ttu-id="a86b1-115">從 .NET Core 3.0 開始的輸出</span><span class="sxs-lookup"><span data-stu-id="a86b1-115">Output starting with .NET Core 3.0</span></span>        |
|-------------------------|--------------------------------------|-------------------------------------------|
| `[ ED A0 90 ]`          | <span data-ttu-id="a86b1-116">`[ FFFD FFFD ]` (2-字元輸出) </span><span class="sxs-lookup"><span data-stu-id="a86b1-116">`[ FFFD FFFD ]` (2-character output)</span></span> | <span data-ttu-id="a86b1-117">`[ FFFD FFFD FFFD ]` (3-字元輸出) </span><span class="sxs-lookup"><span data-stu-id="a86b1-117">`[ FFFD FFFD FFFD ]` (3-character output)</span></span> |

<span data-ttu-id="a86b1-118">根據先前連結之 Unicode 標準 PDF 的 _表格 3-9_ ，3-char 輸出是慣用的輸出。</span><span class="sxs-lookup"><span data-stu-id="a86b1-118">The 3-char output is the preferred output, according to _Table 3-9_ of the previously linked Unicode Standard PDF.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a86b1-119">引進的版本</span><span class="sxs-lookup"><span data-stu-id="a86b1-119">Version introduced</span></span>

<span data-ttu-id="a86b1-120">3.0</span><span class="sxs-lookup"><span data-stu-id="a86b1-120">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a86b1-121">建議的動作</span><span class="sxs-lookup"><span data-stu-id="a86b1-121">Recommended action</span></span>

<span data-ttu-id="a86b1-122">開發人員不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="a86b1-122">No action is required on the part of the developer.</span></span>

#### <a name="category"></a><span data-ttu-id="a86b1-123">類別</span><span class="sxs-lookup"><span data-stu-id="a86b1-123">Category</span></span>

<span data-ttu-id="a86b1-124">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="a86b1-124">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a86b1-125">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="a86b1-125">Affected APIs</span></span>

- <xref:System.Text.UTF8Encoding.GetCharCount%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetChars%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.UTF8Encoding.GetCharCount`
- `Overload:System.Text.UTF8Encoding.GetChars`
- `M:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)`

-->
