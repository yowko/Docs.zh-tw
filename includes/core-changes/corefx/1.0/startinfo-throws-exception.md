---
ms.openlocfilehash: 92c03328414410d56a2ff5f445639757367b42c7
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031989"
---
### <a name="processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start"></a><span data-ttu-id="c06a7-101">StartInfo 會針對您未啟動的進程擲回 InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="c06a7-101">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>

<span data-ttu-id="c06a7-102">讀取程式 <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> 代碼未啟動之進程的屬性會擲回 <xref:System.InvalidOperationException> 。</span><span class="sxs-lookup"><span data-stu-id="c06a7-102">Reading the <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> property for processes that your code didn't start throws an <xref:System.InvalidOperationException>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c06a7-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="c06a7-103">Change description</span></span>

<span data-ttu-id="c06a7-104">在 .NET Framework 中，存取程式 <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> 代碼未啟動之進程的屬性會傳回虛擬 <xref:System.Diagnostics.ProcessStartInfo> 物件。</span><span class="sxs-lookup"><span data-stu-id="c06a7-104">In .NET Framework, accessing the <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> property for processes that your code didn't start returns a dummy <xref:System.Diagnostics.ProcessStartInfo> object.</span></span> <span data-ttu-id="c06a7-105">除了以外，虛擬物件會包含其所有屬性的預設值 <xref:System.Diagnostics.ProcessStartInfo.EnvironmentVariables> 。</span><span class="sxs-lookup"><span data-stu-id="c06a7-105">The dummy object contains default values for all of its properties except <xref:System.Diagnostics.ProcessStartInfo.EnvironmentVariables>.</span></span>

<span data-ttu-id="c06a7-106">從 .NET Core 1.0 開始，如果您 <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> 針對未啟動的進程讀取屬性 (也就是呼叫 <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>) ， <xref:System.InvalidOperationException> 則會擲回。</span><span class="sxs-lookup"><span data-stu-id="c06a7-106">Starting in .NET Core 1.0, if you read the <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> property for a process that you didn't start (that is, by calling <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>), an <xref:System.InvalidOperationException> is thrown.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c06a7-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="c06a7-107">Version introduced</span></span>

<span data-ttu-id="c06a7-108">1.0</span><span class="sxs-lookup"><span data-stu-id="c06a7-108">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c06a7-109">建議的動作</span><span class="sxs-lookup"><span data-stu-id="c06a7-109">Recommended action</span></span>

<span data-ttu-id="c06a7-110">請勿存取程式 <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> 代碼未啟動的進程屬性。</span><span class="sxs-lookup"><span data-stu-id="c06a7-110">Do not access the <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> property for processes that your code didn't start.</span></span> <span data-ttu-id="c06a7-111">例如，請勿針對所傳回的進程讀取這個屬性 <xref:System.Diagnostics.Process.GetProcesses%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="c06a7-111">For example, don't read this property for processes returned by <xref:System.Diagnostics.Process.GetProcesses%2A?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="c06a7-112">類別</span><span class="sxs-lookup"><span data-stu-id="c06a7-112">Category</span></span>

<span data-ttu-id="c06a7-113">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="c06a7-113">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c06a7-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="c06a7-114">Affected APIs</span></span>

- <xref:System.Diagnostics.Process.StartInfo?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Diagnostics.Process.StartInfo`

-->
