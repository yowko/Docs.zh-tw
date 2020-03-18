---
ms.openlocfilehash: 58d1c8cd3aff52703522391c14348bd81c108587
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568214"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a><span data-ttu-id="9ad63-101">自訂編碼器回退緩衝區實例不能遞迴</span><span class="sxs-lookup"><span data-stu-id="9ad63-101">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>

<span data-ttu-id="9ad63-102">自訂<xref:System.Text.EncoderFallbackBuffer>實例不能遞迴。</span><span class="sxs-lookup"><span data-stu-id="9ad63-102">Custom <xref:System.Text.EncoderFallbackBuffer> instances cannot fall back recursively.</span></span> <span data-ttu-id="9ad63-103">的<xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>實現必須產生可轉換為目標編碼的字元序列。</span><span class="sxs-lookup"><span data-stu-id="9ad63-103">The implementation of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must result in a character sequence that is convertible to the destination encoding.</span></span> <span data-ttu-id="9ad63-104">否則，將發生異常。</span><span class="sxs-lookup"><span data-stu-id="9ad63-104">Otherwise, an exception occurs.</span></span>

#### <a name="change-description"></a><span data-ttu-id="9ad63-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="9ad63-105">Change description</span></span>

<span data-ttu-id="9ad63-106">在字元到位元組轉碼操作期間，運行時檢測格式錯誤或不可轉換的 UTF-16 序列，並將這些字元提供<xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>給該方法。</span><span class="sxs-lookup"><span data-stu-id="9ad63-106">During a character-to-byte transcoding operation, the runtime detects ill-formed or nonconvertible UTF-16 sequences and provides those characters to the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="9ad63-107">該方法`Fallback`確定哪些字元應替換為原始不可轉換資料，並且這些字元通過在迴圈中調用<xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType>而耗盡。</span><span class="sxs-lookup"><span data-stu-id="9ad63-107">The `Fallback` method determines which characters should be substituted for the original nonconvertible data, and these characters are drained by calling <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> in a loop.</span></span>

<span data-ttu-id="9ad63-108">然後，運行時嘗試將這些替換字元轉碼到目標編碼。</span><span class="sxs-lookup"><span data-stu-id="9ad63-108">The runtime then attempts to transcode these substitution characters to the target encoding.</span></span> <span data-ttu-id="9ad63-109">如果此操作成功，運行時將繼續從原始輸入字串中保留的位置轉碼。</span><span class="sxs-lookup"><span data-stu-id="9ad63-109">If this operation succeeds, the runtime continues transcoding from where it left off in the original input string.</span></span>

<span data-ttu-id="9ad63-110">在 .NET 核心預覽 7 和早期版本中，<xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>的自訂實現可以返回不可轉換為目標編碼的字元序列。</span><span class="sxs-lookup"><span data-stu-id="9ad63-110">In .NET Core Preview 7 and earlier versions, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> can return character sequences that are not convertible to the destination encoding.</span></span> <span data-ttu-id="9ad63-111">如果替換的字元無法轉碼到目標編碼，運行時將再次使用替換字元調用<xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>該方法，希望<xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>該方法返回新的替換序列。</span><span class="sxs-lookup"><span data-stu-id="9ad63-111">If the substituted characters cannot be transcoded to the target encoding, the runtime invokes the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method once again with the substitution characters, expecting the <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> method to return a new substitution sequence.</span></span> <span data-ttu-id="9ad63-112">此過程將一直持續到運行時最終看到格式良好的可轉換替換，或直到達到最大遞迴計數。</span><span class="sxs-lookup"><span data-stu-id="9ad63-112">This process continues until the runtime eventually sees a well-formed, convertible substitution, or until a maximum recursion count is reached.</span></span>

<span data-ttu-id="9ad63-113">從 .NET Core 3.0 開始，<xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>必須返回可轉換為目標編碼的字元序列的自訂實現。</span><span class="sxs-lookup"><span data-stu-id="9ad63-113">Starting with .NET Core 3.0, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must return character sequences that are convertible to the destination encoding.</span></span> <span data-ttu-id="9ad63-114">如果替換的字元無法轉碼到目標編碼，則引發 。 <xref:System.ArgumentException></span><span class="sxs-lookup"><span data-stu-id="9ad63-114">If the substituted characters cannot be transcoded to the target encoding, an <xref:System.ArgumentException> is thrown.</span></span> <span data-ttu-id="9ad63-115">運行時將不再對<xref:System.Text.EncoderFallbackBuffer>實例進行遞迴呼叫。</span><span class="sxs-lookup"><span data-stu-id="9ad63-115">The runtime will no longer make recursive calls into the <xref:System.Text.EncoderFallbackBuffer> instance.</span></span>

<span data-ttu-id="9ad63-116">此行為僅在滿足以下所有三個條件時才適用：</span><span class="sxs-lookup"><span data-stu-id="9ad63-116">This behavior only applies when all three of the following conditions are met:</span></span>

- <span data-ttu-id="9ad63-117">運行時檢測格式錯誤的 UTF-16 序列或無法轉換為目標編碼的 UTF-16 序列。</span><span class="sxs-lookup"><span data-stu-id="9ad63-117">The runtime detects an ill-formed UTF-16 sequence or a UTF-16 sequence that cannot be converted to the target encoding.</span></span>
- <span data-ttu-id="9ad63-118">已指定<xref:System.Text.EncoderFallback>自訂項。</span><span class="sxs-lookup"><span data-stu-id="9ad63-118">A custom <xref:System.Text.EncoderFallback> has been specified.</span></span>
- <span data-ttu-id="9ad63-119">自訂<xref:System.Text.EncoderFallback>嘗試替換新的格式錯誤或不可轉換的 UTF-16 序列。</span><span class="sxs-lookup"><span data-stu-id="9ad63-119">The custom <xref:System.Text.EncoderFallback> attempts to substitute a new ill-formed or nonconvertible UTF-16 sequence.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9ad63-120">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="9ad63-120">Version introduced</span></span>

<span data-ttu-id="9ad63-121">3.0</span><span class="sxs-lookup"><span data-stu-id="9ad63-121">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9ad63-122">建議的動作</span><span class="sxs-lookup"><span data-stu-id="9ad63-122">Recommended action</span></span>

<span data-ttu-id="9ad63-123">大多數開發人員不需要採取任何操作。</span><span class="sxs-lookup"><span data-stu-id="9ad63-123">Most developers needn't take any action.</span></span>

<span data-ttu-id="9ad63-124">如果應用程式使用<xref:System.Text.EncoderFallback>自訂和<xref:System.Text.EncoderFallbackBuffer>類，請確保使用格式良好的 UTF-16 資料<xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>填充回退緩衝區，這些資料在運行時首次調用<xref:System.Text.EncoderFallbackBuffer.Fallback%2A>該方法時直接轉換為目標編碼。</span><span class="sxs-lookup"><span data-stu-id="9ad63-124">If an application uses a custom <xref:System.Text.EncoderFallback> and <xref:System.Text.EncoderFallbackBuffer> class, ensure the implementation of <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> populates the fallback buffer with well-formed UTF-16 data that is directly convertible to the target encoding when the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> method is first invoked by the runtime.</span></span>

#### <a name="category"></a><span data-ttu-id="9ad63-125">類別</span><span class="sxs-lookup"><span data-stu-id="9ad63-125">Category</span></span>

<span data-ttu-id="9ad63-126">CoreFx</span><span class="sxs-lookup"><span data-stu-id="9ad63-126">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9ad63-127">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="9ad63-127">Affected APIs</span></span>

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->
