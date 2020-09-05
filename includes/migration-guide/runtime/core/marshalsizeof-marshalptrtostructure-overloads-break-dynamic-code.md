---
ms.openlocfilehash: 086dac69d085d070511fcfd5820bd2644ee4598e
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497689"
---
### <a name="marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a><span data-ttu-id="5dd85-101">Marshal.SizeOf 和 Marshal.PtrToStructure 多載會中斷動態程式碼</span><span class="sxs-lookup"><span data-stu-id="5dd85-101">Marshal.SizeOf and Marshal.PtrToStructure overloads break dynamic code</span></span>

#### <a name="details"></a><span data-ttu-id="5dd85-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5dd85-102">Details</span></span>

<span data-ttu-id="5dd85-103">在 .NET Framework 4.5.1 中，動態繫結至方法 <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601>、<xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)>、<xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)>、<xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)> 或 <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)> (例如透過 Windows PowerShell、IronPython 或 C# 動態關鍵字) 可能會造成 <code>MethodInvocationExceptions</code>，因為新增了可能對指令碼引擎模稜兩可的方法多載。</span><span class="sxs-lookup"><span data-stu-id="5dd85-103">Beginning in the .NET Framework 4.5.1, dynamically binding to the methods <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601>, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)>, or <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)>, (via Windows PowerShell, IronPython, or the C# dynamic keyword, for example) can result in <code>MethodInvocationExceptions</code> because new overloads of these methods have been added that may be ambiguous to the scripting engines.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5dd85-104">建議</span><span class="sxs-lookup"><span data-stu-id="5dd85-104">Suggestion</span></span>

<span data-ttu-id="5dd85-105">請更新指令碼，以清楚指出應使用哪個多載。</span><span class="sxs-lookup"><span data-stu-id="5dd85-105">Update scripts to clearly indicate which overload should be used.</span></span> <span data-ttu-id="5dd85-106">一般而言，將方法的型別參數明確轉換成 <xref:System.Type>，即可完成此作業。</span><span class="sxs-lookup"><span data-stu-id="5dd85-106">This can typically done by explicitly casting the methods' type parameters as <xref:System.Type>.</span></span> <span data-ttu-id="5dd85-107">如需如何解決問題的詳細資訊和範例，請參閱[這個連結](https://support.microsoft.com/kb/2909958/)。</span><span class="sxs-lookup"><span data-stu-id="5dd85-107">See [this link](https://support.microsoft.com/kb/2909958/) for more detail and examples of how to workaround the issue.</span></span>

| <span data-ttu-id="5dd85-108">名稱</span><span class="sxs-lookup"><span data-stu-id="5dd85-108">Name</span></span>    | <span data-ttu-id="5dd85-109">值</span><span class="sxs-lookup"><span data-stu-id="5dd85-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5dd85-110">範圍</span><span class="sxs-lookup"><span data-stu-id="5dd85-110">Scope</span></span>   |<span data-ttu-id="5dd85-111">Minor</span><span class="sxs-lookup"><span data-stu-id="5dd85-111">Minor</span></span>|
|<span data-ttu-id="5dd85-112">版本</span><span class="sxs-lookup"><span data-stu-id="5dd85-112">Version</span></span>|<span data-ttu-id="5dd85-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="5dd85-113">4.5.1</span></span>|
|<span data-ttu-id="5dd85-114">類型</span><span class="sxs-lookup"><span data-stu-id="5dd85-114">Type</span></span>|<span data-ttu-id="5dd85-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="5dd85-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="5dd85-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="5dd85-116">Affected APIs</span></span>

<span data-ttu-id="5dd85-117">無法透過 API 分析偵測。</span><span class="sxs-lookup"><span data-stu-id="5dd85-117">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
