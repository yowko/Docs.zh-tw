---
ms.openlocfilehash: db1d09c8c9e606b5327a42977a74a74703282d84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568195"
---
### <a name="net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences"></a><span data-ttu-id="da85c-101">.NET Core 3.0 在替換格式錯誤的 UTF-8 位元組序列時遵循 Unicode 最佳實踐</span><span class="sxs-lookup"><span data-stu-id="da85c-101">.NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences</span></span>

<span data-ttu-id="da85c-102">當類<xref:System.Text.UTF8Encoding>在位元組到字元轉碼操作期間遇到格式錯誤的 UTF-8 位元組序列時，它將在輸出字串中用''（U+FFFD 替換字元）替換該序列。</span><span class="sxs-lookup"><span data-stu-id="da85c-102">When the <xref:System.Text.UTF8Encoding> class encounters an ill-formed UTF-8 byte sequence during a byte-to-character transcoding operation, it will replace that sequence with a '�' (U+FFFD REPLACEMENT CHARACTER) character in the output string.</span></span> <span data-ttu-id="da85c-103">.NET Core 3.0 不同于早期版本的 .NET Core 和 .NET Framework，在轉碼操作期間遵循 Unicode 最佳做法執行此替換。</span><span class="sxs-lookup"><span data-stu-id="da85c-103">.NET Core 3.0 differs from previous versions of .NET Core and the .NET Framework by following the Unicode best practice for performing this replacement during the transcoding operation.</span></span>

<span data-ttu-id="da85c-104">這是改進整個 .NET 的 UTF-8 處理（包括新<xref:System.Text.Unicode.Utf8?displayProperty=nameWithType>類型和<xref:System.Text.Rune?displayProperty=nameWithType>類型）的更大努力的一部分。</span><span class="sxs-lookup"><span data-stu-id="da85c-104">This is part of a larger effort to improve UTF-8 handling throughout .NET, including by the new <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> and <xref:System.Text.Rune?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="da85c-105">該<xref:System.Text.UTF8Encoding>類型得到了改進的錯誤處理機制，以便生成與新引入的類型一致的輸出。</span><span class="sxs-lookup"><span data-stu-id="da85c-105">The <xref:System.Text.UTF8Encoding> type was given improved error handling mechanics so that it produces output consistent with the newly introduced types.</span></span>

#### <a name="change-description"></a><span data-ttu-id="da85c-106">變更描述</span><span class="sxs-lookup"><span data-stu-id="da85c-106">Change description</span></span>

<span data-ttu-id="da85c-107">從 .NET Core 3.0 開始，當將位元組轉碼<xref:System.Text.UTF8Encoding>轉給字元時，類根據 Unicode 最佳實踐執行字元替換。</span><span class="sxs-lookup"><span data-stu-id="da85c-107">Starting with .NET Core 3.0, when transcoding bytes to characters, the <xref:System.Text.UTF8Encoding> class performs character substitution based on Unicode best practices.</span></span> <span data-ttu-id="da85c-108">所使用的替換機制由[Unicode 標準版本 12.0、第 3.9（PDF） 在](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf)標題為_U_FFFD 替換最大子部分_的標題中描述。</span><span class="sxs-lookup"><span data-stu-id="da85c-108">The substitution mechanism used is described by [The Unicode Standard, Version 12.0, Sec. 3.9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) in the heading titled _U+FFFD Substitution of Maximal Subparts_.</span></span>

<span data-ttu-id="da85c-109">僅當輸入位元組序列包含格式錯誤的 UTF-8 資料時，_此行為才_適用。</span><span class="sxs-lookup"><span data-stu-id="da85c-109">This behavior _only_ applies when the input byte sequence contains ill-formed UTF-8 data.</span></span> <span data-ttu-id="da85c-110">此外，<xref:System.Text.UTF8Encoding>如果實例已構造`throwOnInvalidBytes: true`（請參閱 [UTF8編碼建構函式文檔]（，<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>`UTF8Encoding`實例將繼續引發不正確輸入，而不是執行 U_FFFD 替換。</span><span class="sxs-lookup"><span data-stu-id="da85c-110">Additionally, if the <xref:System.Text.UTF8Encoding> instance has been constructed with `throwOnInvalidBytes: true` (see the [UTF8Encoding constructor documentation](<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>, the `UTF8Encoding` instance will continue to throw on invalid input rather than perform U+FFFD replacement.</span></span>

<span data-ttu-id="da85c-111">下面說明了此更改對不正確 3 位元組輸入的影響：</span><span class="sxs-lookup"><span data-stu-id="da85c-111">The following illustrates the impact of this change with an invalid 3-byte input:</span></span>

|<span data-ttu-id="da85c-112">變形的 3 位元組輸入</span><span class="sxs-lookup"><span data-stu-id="da85c-112">Ill-formed 3-byte input</span></span>|<span data-ttu-id="da85c-113">在 .NET 核心 3.0 之前輸出</span><span class="sxs-lookup"><span data-stu-id="da85c-113">Output before .NET Core 3.0</span></span>|<span data-ttu-id="da85c-114">輸出以 .NET 核心 3.0 開頭</span><span class="sxs-lookup"><span data-stu-id="da85c-114">Output starting with .NET Core 3.0</span></span>|
|---|---|---|
| `[ ED A0 90 ]` | <span data-ttu-id="da85c-115">`[ FFFD FFFD ]`（2 個字元輸出）</span><span class="sxs-lookup"><span data-stu-id="da85c-115">`[ FFFD FFFD ]` (2-character output)</span></span>| <span data-ttu-id="da85c-116">`[ FFFD FFFD FFFD ]`（3 個字元輸出）</span><span class="sxs-lookup"><span data-stu-id="da85c-116">`[ FFFD FFFD FFFD ]` (3-character output)</span></span>|

<span data-ttu-id="da85c-117">根據先前連結的 Unicode 標準 PDF_表 3-9，_ 此 3 字元輸出是首選輸出。</span><span class="sxs-lookup"><span data-stu-id="da85c-117">This 3-char output is the preferred output, according to _Table 3-9_ of the previously linked Unicode Standard PDF.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="da85c-118">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="da85c-118">Version introduced</span></span>

<span data-ttu-id="da85c-119">3.0</span><span class="sxs-lookup"><span data-stu-id="da85c-119">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="da85c-120">建議的動作</span><span class="sxs-lookup"><span data-stu-id="da85c-120">Recommended action</span></span>

<span data-ttu-id="da85c-121">開發人員不需要執行任何操作。</span><span class="sxs-lookup"><span data-stu-id="da85c-121">No action is required on the part of the developer.</span></span>

#### <a name="category"></a><span data-ttu-id="da85c-122">類別</span><span class="sxs-lookup"><span data-stu-id="da85c-122">Category</span></span>

<span data-ttu-id="da85c-123">CoreFx</span><span class="sxs-lookup"><span data-stu-id="da85c-123">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="da85c-124">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="da85c-124">Affected APIs</span></span>

- <xref:System.Text.UTF8Encoding.GetCharCount%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetChars%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.UTF8Encoding.GetCharCount`
- `Overload:System.Text.UTF8Encoding.GetChars`
- `M:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)`

-->
