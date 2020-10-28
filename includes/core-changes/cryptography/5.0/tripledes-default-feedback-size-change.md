---
ms.openlocfilehash: 2599e1f65720c25695f1fb5cfa39cabb842efc1d
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888606"
---
### <a name="default-feedbacksize-value-for-instances-created-by-tripledescreate-changed"></a><span data-ttu-id="b7839-101">TripleDES 建立之實例的預設 FeedbackSize 值。建立變更</span><span class="sxs-lookup"><span data-stu-id="b7839-101">Default FeedbackSize value for instances created by TripleDES.Create changed</span></span>

<span data-ttu-id="b7839-102"><xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize?displayProperty=nameWithType>從傳回的實例上，屬性的預設值 <xref:System.Security.Cryptography.TripleDES> <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> 已從64變更為8，以簡化 .NET Framework 的遷移。</span><span class="sxs-lookup"><span data-stu-id="b7839-102">The default value for the <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize?displayProperty=nameWithType> property on the <xref:System.Security.Cryptography.TripleDES> instance returned from <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> has changed from 64 to 8 to make migration from .NET Framework easier.</span></span> <span data-ttu-id="b7839-103">除非直接在呼叫端程式碼中使用這個屬性，否則此屬性只會在 <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode> 屬性為時使用 <xref:System.Security.Cryptography.CipherMode.CFB?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="b7839-103">This property, unless used directly in caller code, is used only when the <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode> property is <xref:System.Security.Cryptography.CipherMode.CFB?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="b7839-104">針對 <xref:System.Security.Cryptography.CipherMode.CFB> 5.0 RC1 版本，第一次將模式的支援新增至 .net，因此只有 .net 5.0 RC1 和 .net 5.0 RC2 應用程式才會受到這項變更的影響。</span><span class="sxs-lookup"><span data-stu-id="b7839-104">Support for the <xref:System.Security.Cryptography.CipherMode.CFB> mode was first added to .NET for the 5.0 RC1 release, so only .NET 5.0 RC1 and .NET 5.0 RC2 applications should be impacted by this change.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b7839-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="b7839-105">Change description</span></span>

<span data-ttu-id="b7839-106">在 .NET Core 和舊版的 .NET 5.0 發行前版本中， `TripleDES.Create().FeedbackSize` 預設值是64。</span><span class="sxs-lookup"><span data-stu-id="b7839-106">In .NET Core and previous pre-release versions of .NET 5.0, `TripleDES.Create().FeedbackSize` has a default value of 64.</span></span> <span data-ttu-id="b7839-107">從 .NET 5.0 的 RTM 版本開始， `TripleDES.Create().FeedbackSize` 預設值為8。</span><span class="sxs-lookup"><span data-stu-id="b7839-107">Starting in the RTM version of .NET 5.0, `TripleDES.Create().FeedbackSize` has a default value of 8.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b7839-108">變更的原因</span><span class="sxs-lookup"><span data-stu-id="b7839-108">Reason for change</span></span>

<span data-ttu-id="b7839-109">在 .NET Framework 中， <xref:System.Security.Cryptography.TripleDES> 基類會將的值預設為 <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> 64，但類別會將 <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> 預設值覆寫為8。</span><span class="sxs-lookup"><span data-stu-id="b7839-109">In .NET Framework, the <xref:System.Security.Cryptography.TripleDES> base class defaults the value of <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> to 64, but the <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> class overwrites the default to 8.</span></span> <span data-ttu-id="b7839-110">當 <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> 屬性在2.0 版中引進 .Net Core 時，會保留相同的行為。</span><span class="sxs-lookup"><span data-stu-id="b7839-110">When the <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> property was introduced to .NET Core in version 2.0, this same behavior was preserved.</span></span> <span data-ttu-id="b7839-111">不過，在 .NET Framework 中，會傳回的 <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> 實例 <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> ，因此演算法 factory 的預設值為8。</span><span class="sxs-lookup"><span data-stu-id="b7839-111">However, in .NET Framework, <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> returns an instance of <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider>, so the default value from the algorithm factory is 8.</span></span> <span data-ttu-id="b7839-112">若是 .NET Core 和 .NET 5 +，演算法處理站會傳回非公用的執行，而在目前為止，預設值為64。</span><span class="sxs-lookup"><span data-stu-id="b7839-112">For .NET Core and .NET 5+, the algorithm factory returns a non-public implementation, which, until now, had a default value of 64.</span></span>

<span data-ttu-id="b7839-113">將 <xref:System.Security.Cryptography.TripleDES> 實數值型別的 <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> 值變更為8可讓針對指定加密模式的 .NET Framework 寫入的應用程式， <xref:System.Security.Cryptography.CipherMode.CFB> 但未明確指派 <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> 屬性，以便在 .net 5 上繼續運作。</span><span class="sxs-lookup"><span data-stu-id="b7839-113">Changing the <xref:System.Security.Cryptography.TripleDES> implementation class' <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> value to 8 allows for applications written for .NET Framework that specified the cipher mode as <xref:System.Security.Cryptography.CipherMode.CFB> but didn't explicitly assign the <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> property, to continue to function on .NET 5.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b7839-114">引進的版本</span><span class="sxs-lookup"><span data-stu-id="b7839-114">Version introduced</span></span>

<span data-ttu-id="b7839-115">5.0 RTM</span><span class="sxs-lookup"><span data-stu-id="b7839-115">5.0 RTM</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b7839-116">建議的動作</span><span class="sxs-lookup"><span data-stu-id="b7839-116">Recommended action</span></span>

<span data-ttu-id="b7839-117">當符合下列條件時，在 .NET 5.0 的 RC1 或 RC2 版本中加密或解密資料的應用程式會使用 CFB64 來執行此作業：</span><span class="sxs-lookup"><span data-stu-id="b7839-117">Applications that encrypt or decrypt data in the RC1 or RC2 versions of .NET 5.0 do so with CFB64, when the following conditions are met:</span></span>

- <span data-ttu-id="b7839-118">的 <xref:System.Security.Cryptography.TripleDES> 實例 <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="b7839-118">With a <xref:System.Security.Cryptography.TripleDES> instance from <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="b7839-119">使用的預設值 <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> 。</span><span class="sxs-lookup"><span data-stu-id="b7839-119">Using the default value for <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize>.</span></span>
- <span data-ttu-id="b7839-120"><xref:System.Security.Cryptography.SymmetricAlgorithm.Mode>屬性設定為 <xref:System.Security.Cryptography.CipherMode.CFB?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="b7839-120">With the <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode> property set to <xref:System.Security.Cryptography.CipherMode.CFB?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="b7839-121">若要維護這種行為，請將 <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> 屬性指派給 `64` 。</span><span class="sxs-lookup"><span data-stu-id="b7839-121">To maintain this behavior, assign the <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> property to `64`.</span></span>

<span data-ttu-id="b7839-122">並非所有 `TripleDES` 的實施都使用相同的預設值 <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> 。</span><span class="sxs-lookup"><span data-stu-id="b7839-122">Not all `TripleDES` implementations use the same default for <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize>.</span></span> <span data-ttu-id="b7839-123">如果您 <xref:System.Security.Cryptography.CipherMode.CFB> 在實例上使用加密模式，建議 <xref:System.Security.Cryptography.TripleDES> 您一律明確指派 <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> 屬性值。</span><span class="sxs-lookup"><span data-stu-id="b7839-123">We recommend that if you use the <xref:System.Security.Cryptography.CipherMode.CFB> cipher mode on <xref:System.Security.Cryptography.TripleDES> instances, you should always explicitly assign the <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> property value.</span></span>

```csharp
TripleDES cipher = TripleDES.Create();
cipher.Mode = CipherMode.CFB;
// Explicitly set the FeedbackSize for CFB to control between CFB8 and CFB64.
cipher.FeedbackSize = 8;
```

#### <a name="category"></a><span data-ttu-id="b7839-124">類別</span><span class="sxs-lookup"><span data-stu-id="b7839-124">Category</span></span>

- <span data-ttu-id="b7839-125">密碼編譯</span><span class="sxs-lookup"><span data-stu-id="b7839-125">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b7839-126">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="b7839-126">Affected APIs</span></span>

- <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.TripleDES.Create`
- `P:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize`

-->
