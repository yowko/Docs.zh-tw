---
ms.openlocfilehash: 92c03328414410d56a2ff5f445639757367b42c7
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420420"
---
### <a name="processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start"></a><span data-ttu-id="7f698-101">StartInfo 會針對您未啟動的進程擲回 InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="7f698-101">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>

<span data-ttu-id="7f698-102">讀取程式 <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> 代碼未啟動之進程的屬性會擲回 <xref:System.InvalidOperationException> 。</span><span class="sxs-lookup"><span data-stu-id="7f698-102">Reading the <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> property for processes that your code didn't start throws an <xref:System.InvalidOperationException>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="7f698-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="7f698-103">Change description</span></span>

<span data-ttu-id="7f698-104">在 .NET Framework 中，存取程式 <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> 代碼未啟動之進程的屬性會傳回虛擬 <xref:System.Diagnostics.ProcessStartInfo> 物件。</span><span class="sxs-lookup"><span data-stu-id="7f698-104">In .NET Framework, accessing the <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> property for processes that your code didn't start returns a dummy <xref:System.Diagnostics.ProcessStartInfo> object.</span></span> <span data-ttu-id="7f698-105">虛擬物件包含其所有屬性的預設值，但除外 <xref:System.Diagnostics.ProcessStartInfo.EnvironmentVariables> 。</span><span class="sxs-lookup"><span data-stu-id="7f698-105">The dummy object contains default values for all of its properties except <xref:System.Diagnostics.ProcessStartInfo.EnvironmentVariables>.</span></span>

<span data-ttu-id="7f698-106">從 .NET Core 1.0 開始，如果您讀取 <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> 未啟動之進程的屬性（也就是藉由呼叫 <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> ）， <xref:System.InvalidOperationException> 則會擲回。</span><span class="sxs-lookup"><span data-stu-id="7f698-106">Starting in .NET Core 1.0, if you read the <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> property for a process that you didn't start (that is, by calling <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>), an <xref:System.InvalidOperationException> is thrown.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7f698-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="7f698-107">Version introduced</span></span>

<span data-ttu-id="7f698-108">1.0</span><span class="sxs-lookup"><span data-stu-id="7f698-108">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7f698-109">建議的動作</span><span class="sxs-lookup"><span data-stu-id="7f698-109">Recommended action</span></span>

<span data-ttu-id="7f698-110">請勿存取 <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> 程式碼未啟動之進程的屬性。</span><span class="sxs-lookup"><span data-stu-id="7f698-110">Do not access the <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> property for processes that your code didn't start.</span></span> <span data-ttu-id="7f698-111">例如，請勿讀取所傳回之進程的這個屬性 <xref:System.Diagnostics.Process.GetProcesses%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="7f698-111">For example, don't read this property for processes returned by <xref:System.Diagnostics.Process.GetProcesses%2A?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="7f698-112">類別</span><span class="sxs-lookup"><span data-stu-id="7f698-112">Category</span></span>

<span data-ttu-id="7f698-113">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="7f698-113">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7f698-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="7f698-114">Affected APIs</span></span>

- <xref:System.Diagnostics.Process.StartInfo?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Diagnostics.Process.StartInfo`

-->
