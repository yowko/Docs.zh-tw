---
ms.openlocfilehash: c462c7b4ec8423ce8fd331d3cd31154283cf1f1d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619988"
---
### <a name="marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a><span data-ttu-id="ccd41-101">Marshal.SizeOf 和 Marshal.PtrToStructure 多載會中斷動態程式碼</span><span class="sxs-lookup"><span data-stu-id="ccd41-101">Marshal.SizeOf and Marshal.PtrToStructure overloads break dynamic code</span></span>

#### <a name="details"></a><span data-ttu-id="ccd41-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ccd41-102">Details</span></span>

<span data-ttu-id="ccd41-103">在 .NET Framework 4.5.1 中，動態繫結至方法 <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601>、<xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)>、<xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)>、<xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)> 或 <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)> (例如透過 Windows PowerShell、IronPython 或 C# 動態關鍵字) 可能會造成 <code>MethodInvocationExceptions</code>，因為新增了可能對指令碼引擎模稜兩可的方法多載。</span><span class="sxs-lookup"><span data-stu-id="ccd41-103">Beginning in the .NET Framework 4.5.1, dynamically binding to the methods <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601>, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)>, or <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)>, (via Windows PowerShell, IronPython, or the C# dynamic keyword, for example) can result in <code>MethodInvocationExceptions</code> because new overloads of these methods have been added that may be ambiguous to the scripting engines.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ccd41-104">建議</span><span class="sxs-lookup"><span data-stu-id="ccd41-104">Suggestion</span></span>

<span data-ttu-id="ccd41-105">請更新指令碼，以清楚指出應使用哪個多載。</span><span class="sxs-lookup"><span data-stu-id="ccd41-105">Update scripts to clearly indicate which overload should be used.</span></span> <span data-ttu-id="ccd41-106">一般而言，將方法的型別參數明確轉換成 <xref:System.Type>，即可完成此作業。</span><span class="sxs-lookup"><span data-stu-id="ccd41-106">This can typically done by explicitly casting the methods' type parameters as <xref:System.Type>.</span></span> <span data-ttu-id="ccd41-107">如需如何解決問題的詳細資訊和範例，請參閱[這個連結](https://support.microsoft.com/kb/2909958/)。</span><span class="sxs-lookup"><span data-stu-id="ccd41-107">See [this link](https://support.microsoft.com/kb/2909958/) for more detail and examples of how to workaround the issue.</span></span>

| <span data-ttu-id="ccd41-108">名稱</span><span class="sxs-lookup"><span data-stu-id="ccd41-108">Name</span></span>    | <span data-ttu-id="ccd41-109">值</span><span class="sxs-lookup"><span data-stu-id="ccd41-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ccd41-110">影響範圍</span><span class="sxs-lookup"><span data-stu-id="ccd41-110">Scope</span></span>   |<span data-ttu-id="ccd41-111">Minor</span><span class="sxs-lookup"><span data-stu-id="ccd41-111">Minor</span></span>|
|<span data-ttu-id="ccd41-112">版本</span><span class="sxs-lookup"><span data-stu-id="ccd41-112">Version</span></span>|<span data-ttu-id="ccd41-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="ccd41-113">4.5.1</span></span>|
|<span data-ttu-id="ccd41-114">類型</span><span class="sxs-lookup"><span data-stu-id="ccd41-114">Type</span></span>|<span data-ttu-id="ccd41-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="ccd41-115">Runtime</span></span>|
