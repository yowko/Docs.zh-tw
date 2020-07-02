---
ms.openlocfilehash: 0bd90b3d479a7e0897aaf78b7718ae156a4a239f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619947"
---
### <a name="assemblies-compiled-with-regexcompiletoassembly-breaks-between-40-and-45"></a><span data-ttu-id="e2ff5-101">使用 Regex.CompileToAssembly 編譯的組件在 4.0 與 4.5 之間中斷</span><span class="sxs-lookup"><span data-stu-id="e2ff5-101">Assemblies compiled with Regex.CompileToAssembly breaks between 4.0 and 4.5</span></span>

#### <a name="details"></a><span data-ttu-id="e2ff5-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e2ff5-102">Details</span></span>

<span data-ttu-id="e2ff5-103">如果使用 .NET Framework 4.5 建置編譯之規則運算式的組件，但以 .NET Framework 4 為目標，嘗試在安裝 .NET Framework 4 的系統上使用該組件中的其中一個規則運算式時，會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e2ff5-103">If an assembly of compiled regular expressions is built with the .NET Framework 4.5 but targets the .NET Framework 4, attempting to use one of the regular expressions in that assembly on a system with .NET Framework 4 installed throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e2ff5-104">建議</span><span class="sxs-lookup"><span data-stu-id="e2ff5-104">Suggestion</span></span>

<span data-ttu-id="e2ff5-105">若要解決這個問題，您可以執行下列任何一項操作：</span><span class="sxs-lookup"><span data-stu-id="e2ff5-105">To work around this problem, you can do either of the following:</span></span><ul><li><span data-ttu-id="e2ff5-106">使用 .NET Framework 4 建置包含規則運算式的組件。</span><span class="sxs-lookup"><span data-stu-id="e2ff5-106">Build the assembly that contains the regular expressions with the .NET Framework 4.</span></span></li><li><span data-ttu-id="e2ff5-107">使用解譯的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="e2ff5-107">Use an interpreted regular expression.</span></span></li></ul>

| <span data-ttu-id="e2ff5-108">名稱</span><span class="sxs-lookup"><span data-stu-id="e2ff5-108">Name</span></span>    | <span data-ttu-id="e2ff5-109">值</span><span class="sxs-lookup"><span data-stu-id="e2ff5-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e2ff5-110">影響範圍</span><span class="sxs-lookup"><span data-stu-id="e2ff5-110">Scope</span></span>   |<span data-ttu-id="e2ff5-111">Minor</span><span class="sxs-lookup"><span data-stu-id="e2ff5-111">Minor</span></span>|
|<span data-ttu-id="e2ff5-112">版本</span><span class="sxs-lookup"><span data-stu-id="e2ff5-112">Version</span></span>|<span data-ttu-id="e2ff5-113">4.5</span><span class="sxs-lookup"><span data-stu-id="e2ff5-113">4.5</span></span>|
|<span data-ttu-id="e2ff5-114">類型</span><span class="sxs-lookup"><span data-stu-id="e2ff5-114">Type</span></span>|<span data-ttu-id="e2ff5-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="e2ff5-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e2ff5-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="e2ff5-116">Affected APIs</span></span>

-<xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName)?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[])?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[],System.String)?displayProperty=nameWithType></li></ul>|
