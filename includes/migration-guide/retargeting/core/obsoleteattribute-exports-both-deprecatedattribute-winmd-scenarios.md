---
ms.openlocfilehash: e8c48c4b1031813ce62f576e5bf1f94c082dfe4b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234641"
---
### <a name="obsoleteattribute-exports-as-both-obsoleteattribute-and-deprecatedattribute-in-winmd-scenarios"></a><span data-ttu-id="d4b12-101">ObsoleteAttribute 會在 WinMD 案例中匯出為 ObsoleteAttribute 和 DeprecatedAttribute</span><span class="sxs-lookup"><span data-stu-id="d4b12-101">ObsoleteAttribute exports as both ObsoleteAttribute and DeprecatedAttribute in WinMD scenarios</span></span>

|   |   |
|---|---|
|<span data-ttu-id="d4b12-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d4b12-102">Details</span></span>|<span data-ttu-id="d4b12-103">當您建立 Windows 中繼資料庫 (.winmd 檔案) 時，<xref:System.ObsoleteAttribute?displayProperty=name> 屬性會匯出為 <xref:System.ObsoleteAttribute?displayProperty=name> 和 [Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute)。</span><span class="sxs-lookup"><span data-stu-id="d4b12-103">When you create a Windows Metadata library (.winmd file), the <xref:System.ObsoleteAttribute?displayProperty=name> attribute is exported as both <xref:System.ObsoleteAttribute?displayProperty=name> and [Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute).</span></span>|
|<span data-ttu-id="d4b12-104">建議</span><span class="sxs-lookup"><span data-stu-id="d4b12-104">Suggestion</span></span>|<span data-ttu-id="d4b12-105">重新編譯使用 <xref:System.ObsoleteAttribute?displayProperty=name> 屬性的現有來源程式碼，可能會在從 C++/CX 或 JavaScript 使用該程式碼時產生警告。我們不建議您在受控組件中同時套用 <xref:System.ObsoleteAttribute?displayProperty=name> 和 [Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute)，這樣可能會導致建置警告。</span><span class="sxs-lookup"><span data-stu-id="d4b12-105">Recompilation of existing source code that uses the <xref:System.ObsoleteAttribute?displayProperty=name> attribute may generate warnings when consuming that code from C++/CX or JavaScript.We do not recommend applying both <xref:System.ObsoleteAttribute?displayProperty=name> and [Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute) to code in managed assemblies; it may result in build warnings.</span></span>|
|<span data-ttu-id="d4b12-106">範圍</span><span class="sxs-lookup"><span data-stu-id="d4b12-106">Scope</span></span>|<span data-ttu-id="d4b12-107">Edge</span><span class="sxs-lookup"><span data-stu-id="d4b12-107">Edge</span></span>|
|<span data-ttu-id="d4b12-108">版本</span><span class="sxs-lookup"><span data-stu-id="d4b12-108">Version</span></span>|<span data-ttu-id="d4b12-109">4.5.1</span><span class="sxs-lookup"><span data-stu-id="d4b12-109">4.5.1</span></span>|
|<span data-ttu-id="d4b12-110">類型</span><span class="sxs-lookup"><span data-stu-id="d4b12-110">Type</span></span>|<span data-ttu-id="d4b12-111">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="d4b12-111">Retargeting</span></span>|
