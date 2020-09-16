---
ms.openlocfilehash: 6ffd4147a99a59d0a2e50d3f88279608e286aed1
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679962"
---
### <a name="cryptostreamdispose-transforms-final-block-only-when-writing"></a><span data-ttu-id="fb2f6-101">CryptoStream 只會在寫入時轉換最終區塊</span><span class="sxs-lookup"><span data-stu-id="fb2f6-101">CryptoStream.Dispose transforms final block only when writing</span></span>

<span data-ttu-id="fb2f6-102"><xref:System.Security.Cryptography.CryptoStream.Dispose%2A?displayProperty=nameWithType>用來完成作業的方法， `CryptoStream` 不會再于讀取時嘗試轉換最終區塊。</span><span class="sxs-lookup"><span data-stu-id="fb2f6-102">The <xref:System.Security.Cryptography.CryptoStream.Dispose%2A?displayProperty=nameWithType> method, which is used to finish `CryptoStream` operations, no longer attempts to transform the final block when reading.</span></span>

#### <a name="change-description"></a><span data-ttu-id="fb2f6-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="fb2f6-103">Change description</span></span>

<span data-ttu-id="fb2f6-104">在舊版的 .NET 中，如果使用者在使用 in 模式時執行了未完成的讀取 <xref:System.Security.Cryptography.CryptoStream> <xref:System.Security.Cryptography.CryptoStreamMode.Read> ，此 <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> 方法可能會擲回例外狀況 (例如，搭配使用 AES 與填補) 。</span><span class="sxs-lookup"><span data-stu-id="fb2f6-104">In previous .NET versions, if a user performed an incomplete read when using <xref:System.Security.Cryptography.CryptoStream> in <xref:System.Security.Cryptography.CryptoStreamMode.Read> mode, the <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> method could throw an exception (for example, when using AES with padding).</span></span> <span data-ttu-id="fb2f6-105">擲回例外狀況是因為嘗試轉換最後一個區塊，但資料未完成。</span><span class="sxs-lookup"><span data-stu-id="fb2f6-105">The exception was thrown because the final block was attempted to be transformed but the data was incomplete.</span></span>

<span data-ttu-id="fb2f6-106">在 .NET Core 3.0 和更新版本中， <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> 讀取時不會再嘗試轉換最後的區塊，這可允許不完整的讀取。</span><span class="sxs-lookup"><span data-stu-id="fb2f6-106">In .NET Core 3.0 and later versions, <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> no longer tries to transform the final block when reading, which allows for incomplete reads.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="fb2f6-107">變更的原因</span><span class="sxs-lookup"><span data-stu-id="fb2f6-107">Reason for change</span></span>

<span data-ttu-id="fb2f6-108">這項變更可在取消網路作業時，從密碼編譯資料流程進行不完整的讀取，而不需要攔截例外狀況。</span><span class="sxs-lookup"><span data-stu-id="fb2f6-108">This change enables incomplete reads from the crypto stream when a network operation is canceled, without the need to catch an exception.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="fb2f6-109">引進的版本</span><span class="sxs-lookup"><span data-stu-id="fb2f6-109">Version introduced</span></span>

<span data-ttu-id="fb2f6-110">3.0</span><span class="sxs-lookup"><span data-stu-id="fb2f6-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="fb2f6-111">建議的動作</span><span class="sxs-lookup"><span data-stu-id="fb2f6-111">Recommended action</span></span>

<span data-ttu-id="fb2f6-112">大部分的應用程式應該不會受到這項變更的影響。</span><span class="sxs-lookup"><span data-stu-id="fb2f6-112">Most apps should not be affected by this change.</span></span>

<span data-ttu-id="fb2f6-113">如果您的應用程式先前在讀取不完整時攔截到例外狀況，您可以刪除該 `catch` 區塊。</span><span class="sxs-lookup"><span data-stu-id="fb2f6-113">If your application previously caught an exception in case of an incomplete read, you can delete that `catch` block.</span></span>
<span data-ttu-id="fb2f6-114">如果您的應用程式在雜湊案例中使用了最後一個區塊的轉換，您可能需要確保整個資料流程在處置之前都已讀取。</span><span class="sxs-lookup"><span data-stu-id="fb2f6-114">If your app used transforming of the final block in hashing scenarios, you might need to ensure that the entire stream is read before it's disposed.</span></span>

#### <a name="category"></a><span data-ttu-id="fb2f6-115">類別</span><span class="sxs-lookup"><span data-stu-id="fb2f6-115">Category</span></span>

<span data-ttu-id="fb2f6-116">密碼編譯</span><span class="sxs-lookup"><span data-stu-id="fb2f6-116">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fb2f6-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="fb2f6-117">Affected APIs</span></span>

- <xref:System.Security.Cryptography.CryptoStream.Dispose%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.CryptoStream.Dispose`

-->
