---
ms.openlocfilehash: 0bd90b3d479a7e0897aaf78b7718ae156a4a239f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619947"
---
### <a name="assemblies-compiled-with-regexcompiletoassembly-breaks-between-40-and-45"></a>使用 Regex.CompileToAssembly 編譯的組件在 4.0 與 4.5 之間中斷

#### <a name="details"></a>詳細資料

如果使用 .NET Framework 4.5 建置編譯之規則運算式的組件，但以 .NET Framework 4 為目標，嘗試在安裝 .NET Framework 4 的系統上使用該組件中的其中一個規則運算式時，會擲回例外狀況。

#### <a name="suggestion"></a>建議

若要解決這個問題，您可以執行下列任何一項操作：<ul><li>使用 .NET Framework 4 建置包含規則運算式的組件。</li><li>使用解譯的規則運算式。</li></ul>

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Minor|
|版本|4.5|
|類型|執行階段

#### <a name="affected-apis"></a>受影響的 API

-<xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName)?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[])?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[],System.String)?displayProperty=nameWithType></li></ul>|
