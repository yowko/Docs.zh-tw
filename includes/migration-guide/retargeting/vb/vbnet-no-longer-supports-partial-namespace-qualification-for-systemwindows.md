---
ms.openlocfilehash: 8db115a46df3fcea103e8fa6896542d0116aa256
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236723"
---
### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a><span data-ttu-id="2639c-101">VB.NET 不再支援 System.Windows API 的部分命名空間限定性條件</span><span class="sxs-lookup"><span data-stu-id="2639c-101">VB.NET no longer supports partial namespace qualification for System.Windows APIs</span></span>

|   |   |
|---|---|
|<span data-ttu-id="2639c-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2639c-102">Details</span></span>|<span data-ttu-id="2639c-103">從 .NET Framework 4.5.2 開始，VB.NET 專案無法以部分限定的命名空間來指定 System.Windows API。</span><span class="sxs-lookup"><span data-stu-id="2639c-103">Beginning in .NET Framework 4.5.2, VB.NET projects cannot specify System.Windows APIs with partially-qualified namespaces.</span></span> <span data-ttu-id="2639c-104">例如，參考 <code>Windows.Forms.DialogResult</code> 將會失敗。</span><span class="sxs-lookup"><span data-stu-id="2639c-104">For example, referring to <code>Windows.Forms.DialogResult</code> will fail.</span></span> <span data-ttu-id="2639c-105">相反地，程式碼必須參考完整名稱 (<xref:System.Windows.Forms.DialogResult>)，或匯入特定命名空間並只參考 <xref:System.Windows.Forms.DialogResult?displayProperty=name>。</span><span class="sxs-lookup"><span data-stu-id="2639c-105">Instead, code must refer to the fully qualified name (<xref:System.Windows.Forms.DialogResult>) or import the specific namespace and refer simply to <xref:System.Windows.Forms.DialogResult?displayProperty=name>.</span></span>|
|<span data-ttu-id="2639c-106">建議</span><span class="sxs-lookup"><span data-stu-id="2639c-106">Suggestion</span></span>|<span data-ttu-id="2639c-107">您應該更新程式碼，以簡單名稱 (並匯入相關命名空間) 或完整名稱參考 <code>System.Windows</code> API。</span><span class="sxs-lookup"><span data-stu-id="2639c-107">Code should be updated to refer to <code>System.Windows</code> APIs either with simple names (and importing the relevant namespace) or with fully qualified names.</span></span>|
|<span data-ttu-id="2639c-108">範圍</span><span class="sxs-lookup"><span data-stu-id="2639c-108">Scope</span></span>|<span data-ttu-id="2639c-109">次要</span><span class="sxs-lookup"><span data-stu-id="2639c-109">Minor</span></span>|
|<span data-ttu-id="2639c-110">版本</span><span class="sxs-lookup"><span data-stu-id="2639c-110">Version</span></span>|<span data-ttu-id="2639c-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="2639c-111">4.5.2</span></span>|
|<span data-ttu-id="2639c-112">類型</span><span class="sxs-lookup"><span data-stu-id="2639c-112">Type</span></span>|<span data-ttu-id="2639c-113">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="2639c-113">Retargeting</span></span>|
