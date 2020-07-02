---
ms.openlocfilehash: cef8096c971da8ae245ff974697022f350cb9195
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616032"
---
### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a><span data-ttu-id="14ea6-101">VB.NET 不再支援 System.Windows API 的部分命名空間限定性條件</span><span class="sxs-lookup"><span data-stu-id="14ea6-101">VB.NET no longer supports partial namespace qualification for System.Windows APIs</span></span>

#### <a name="details"></a><span data-ttu-id="14ea6-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="14ea6-102">Details</span></span>

<span data-ttu-id="14ea6-103">從 .NET Framework 4.5.2 開始，VB.NET 專案無法以部分限定的命名空間來指定 System.Windows API。</span><span class="sxs-lookup"><span data-stu-id="14ea6-103">Beginning in .NET Framework 4.5.2, VB.NET projects cannot specify System.Windows APIs with partially-qualified namespaces.</span></span> <span data-ttu-id="14ea6-104">例如，參考 `Windows.Forms.DialogResult` 將會失敗。</span><span class="sxs-lookup"><span data-stu-id="14ea6-104">For example, referring to `Windows.Forms.DialogResult` will fail.</span></span> <span data-ttu-id="14ea6-105">相反地，程式碼必須參考完整名稱 (<xref:System.Windows.Forms.DialogResult>)，或匯入特定命名空間並只參考 <xref:System.Windows.Forms.DialogResult?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="14ea6-105">Instead, code must refer to the fully qualified name (<xref:System.Windows.Forms.DialogResult>) or import the specific namespace and refer simply to <xref:System.Windows.Forms.DialogResult?displayProperty=fullName>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="14ea6-106">建議</span><span class="sxs-lookup"><span data-stu-id="14ea6-106">Suggestion</span></span>

<span data-ttu-id="14ea6-107">您應該更新程式碼，以簡單名稱 (並匯入相關命名空間) 或完整名稱參考 `System.Windows` API。</span><span class="sxs-lookup"><span data-stu-id="14ea6-107">Code should be updated to refer to `System.Windows` APIs either with simple names (and importing the relevant namespace) or with fully qualified names.</span></span>

| <span data-ttu-id="14ea6-108">名稱</span><span class="sxs-lookup"><span data-stu-id="14ea6-108">Name</span></span>    | <span data-ttu-id="14ea6-109">值</span><span class="sxs-lookup"><span data-stu-id="14ea6-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="14ea6-110">影響範圍</span><span class="sxs-lookup"><span data-stu-id="14ea6-110">Scope</span></span>   | <span data-ttu-id="14ea6-111">Minor</span><span class="sxs-lookup"><span data-stu-id="14ea6-111">Minor</span></span>       |
| <span data-ttu-id="14ea6-112">版本</span><span class="sxs-lookup"><span data-stu-id="14ea6-112">Version</span></span> | <span data-ttu-id="14ea6-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="14ea6-113">4.5.2</span></span>       |
| <span data-ttu-id="14ea6-114">類型</span><span class="sxs-lookup"><span data-stu-id="14ea6-114">Type</span></span>    | <span data-ttu-id="14ea6-115">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="14ea6-115">Retargeting</span></span> |
