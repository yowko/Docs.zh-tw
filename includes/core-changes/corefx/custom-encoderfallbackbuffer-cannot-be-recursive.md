---
ms.openlocfilehash: 58d1c8cd3aff52703522391c14348bd81c108587
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237313"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a><span data-ttu-id="d1c9e-101">自訂 EncoderFallbackBuffer 實例無法遞迴切換</span><span class="sxs-lookup"><span data-stu-id="d1c9e-101">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>

<span data-ttu-id="d1c9e-102">自訂 <xref:System.Text.EncoderFallbackBuffer> 實例無法以遞迴方式回復。</span><span class="sxs-lookup"><span data-stu-id="d1c9e-102">Custom <xref:System.Text.EncoderFallbackBuffer> instances cannot fall back recursively.</span></span> <span data-ttu-id="d1c9e-103">@No__t-0 的執行必須產生可轉換成目的地編碼的字元序列。</span><span class="sxs-lookup"><span data-stu-id="d1c9e-103">The implementation of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must result in a character sequence that is convertible to the destination encoding.</span></span> <span data-ttu-id="d1c9e-104">否則，就會發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d1c9e-104">Otherwise, an exception occurs.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d1c9e-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="d1c9e-105">Change description</span></span>

<span data-ttu-id="d1c9e-106">在字元對位元組轉碼作業期間，執行時間會偵測格式不正確或 nonconvertible 的 UTF-16 序列，並將這些字元提供給 <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="d1c9e-106">During a character-to-byte transcoding operation, the runtime detects ill-formed or nonconvertible UTF-16 sequences and provides those characters to the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d1c9e-107">@No__t-0 方法會決定哪些字元應取代為原始的 nonconvertible 資料，而這些字元會藉由在迴圈中呼叫 <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> 而耗盡。</span><span class="sxs-lookup"><span data-stu-id="d1c9e-107">The `Fallback` method determines which characters should be substituted for the original nonconvertible data, and these characters are drained by calling <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> in a loop.</span></span>

<span data-ttu-id="d1c9e-108">然後執行時間會嘗試將這些替代字元轉碼到目標編碼。</span><span class="sxs-lookup"><span data-stu-id="d1c9e-108">The runtime then attempts to transcode these substitution characters to the target encoding.</span></span> <span data-ttu-id="d1c9e-109">如果這項作業成功，執行時間會從原始輸入字串中停止的位置繼續轉碼。</span><span class="sxs-lookup"><span data-stu-id="d1c9e-109">If this operation succeeds, the runtime continues transcoding from where it left off in the original input string.</span></span>

<span data-ttu-id="d1c9e-110">在 .NET Core Preview 7 和更早版本中，<xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> 的自訂執行可能會傳回無法轉換成目的地編碼的字元序列。</span><span class="sxs-lookup"><span data-stu-id="d1c9e-110">In .NET Core Preview 7 and earlier versions, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> can return character sequences that are not convertible to the destination encoding.</span></span> <span data-ttu-id="d1c9e-111">如果替代字元無法轉碼到目標編碼，執行時間就會再次使用替代字元叫用 <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> 方法一次，並預期 <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> 方法傳回新的替代序列。</span><span class="sxs-lookup"><span data-stu-id="d1c9e-111">If the substituted characters cannot be transcoded to the target encoding, the runtime invokes the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method once again with the substitution characters, expecting the <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> method to return a new substitution sequence.</span></span> <span data-ttu-id="d1c9e-112">此程式會繼續進行，直到執行時間最終看到格式正確、可轉換的替代，或直到達到最大遞迴計數為止。</span><span class="sxs-lookup"><span data-stu-id="d1c9e-112">This process continues until the runtime eventually sees a well-formed, convertible substitution, or until a maximum recursion count is reached.</span></span>

<span data-ttu-id="d1c9e-113">從 .NET Core 3.0 開始，<xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> 的自訂執行必須傳回可轉換成目的地編碼的字元序列。</span><span class="sxs-lookup"><span data-stu-id="d1c9e-113">Starting with .NET Core 3.0, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must return character sequences that are convertible to the destination encoding.</span></span> <span data-ttu-id="d1c9e-114">如果替代字元無法轉碼到目標編碼，則會擲回 @no__t 0。</span><span class="sxs-lookup"><span data-stu-id="d1c9e-114">If the substituted characters cannot be transcoded to the target encoding, an <xref:System.ArgumentException> is thrown.</span></span> <span data-ttu-id="d1c9e-115">執行時間不會再對 <xref:System.Text.EncoderFallbackBuffer> 實例進行遞迴呼叫。</span><span class="sxs-lookup"><span data-stu-id="d1c9e-115">The runtime will no longer make recursive calls into the <xref:System.Text.EncoderFallbackBuffer> instance.</span></span>

<span data-ttu-id="d1c9e-116">只有在符合下列三個條件時，才會套用此行為：</span><span class="sxs-lookup"><span data-stu-id="d1c9e-116">This behavior only applies when all three of the following conditions are met:</span></span>

- <span data-ttu-id="d1c9e-117">執行時間會偵測格式不正確的 UTF-16 序列或 UTF-16 序列，而無法轉換成目標編碼。</span><span class="sxs-lookup"><span data-stu-id="d1c9e-117">The runtime detects an ill-formed UTF-16 sequence or a UTF-16 sequence that cannot be converted to the target encoding.</span></span>
- <span data-ttu-id="d1c9e-118">已指定自訂 <xref:System.Text.EncoderFallback>。</span><span class="sxs-lookup"><span data-stu-id="d1c9e-118">A custom <xref:System.Text.EncoderFallback> has been specified.</span></span>
- <span data-ttu-id="d1c9e-119">自訂 <xref:System.Text.EncoderFallback> 會嘗試取代新格式不正確或 nonconvertible 的 UTF-16 序列。</span><span class="sxs-lookup"><span data-stu-id="d1c9e-119">The custom <xref:System.Text.EncoderFallback> attempts to substitute a new ill-formed or nonconvertible UTF-16 sequence.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d1c9e-120">引進的版本</span><span class="sxs-lookup"><span data-stu-id="d1c9e-120">Version introduced</span></span>

<span data-ttu-id="d1c9e-121">3.0</span><span class="sxs-lookup"><span data-stu-id="d1c9e-121">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d1c9e-122">建議的動作</span><span class="sxs-lookup"><span data-stu-id="d1c9e-122">Recommended action</span></span>

<span data-ttu-id="d1c9e-123">大部分的開發人員都不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="d1c9e-123">Most developers needn't take any action.</span></span>

<span data-ttu-id="d1c9e-124">如果應用程式使用自訂的 <xref:System.Text.EncoderFallback> 和 @no__t 1 類別，請確定 <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> 會將正確格式的 UTF-16 資料填入回溯緩衝區，而當第一次叫用 <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> 方法時，會直接轉換成目標編碼運行.</span><span class="sxs-lookup"><span data-stu-id="d1c9e-124">If an application uses a custom <xref:System.Text.EncoderFallback> and <xref:System.Text.EncoderFallbackBuffer> class, ensure the implementation of <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> populates the fallback buffer with well-formed UTF-16 data that is directly convertible to the target encoding when the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> method is first invoked by the runtime.</span></span>

#### <a name="category"></a><span data-ttu-id="d1c9e-125">Category</span><span class="sxs-lookup"><span data-stu-id="d1c9e-125">Category</span></span>

<span data-ttu-id="d1c9e-126">CoreFx</span><span class="sxs-lookup"><span data-stu-id="d1c9e-126">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d1c9e-127">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="d1c9e-127">Affected APIs</span></span>

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->
