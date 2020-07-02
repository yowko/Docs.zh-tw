---
ms.openlocfilehash: cecb7b2abd4f57fdaacb0ea373cc19dc3cd9b24a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619935"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a><span data-ttu-id="c1b57-101">無法再將 EnableViewStateMac 設定為 false</span><span class="sxs-lookup"><span data-stu-id="c1b57-101">No longer able to set EnableViewStateMac to false</span></span>

#### <a name="details"></a><span data-ttu-id="c1b57-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c1b57-102">Details</span></span>

<span data-ttu-id="c1b57-103">ASP.NET 不再允許開發人員指定 <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> 或 <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>。</span><span class="sxs-lookup"><span data-stu-id="c1b57-103">ASP.NET no longer allows developers to specify <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> or <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>.</span></span> <span data-ttu-id="c1b57-104">檢視狀態訊息驗證碼 (MAC) 現在會強制所有要求內嵌檢視狀態。</span><span class="sxs-lookup"><span data-stu-id="c1b57-104">The view state message authentication code (MAC) is now enforced for all requests with embedded view state.</span></span> <span data-ttu-id="c1b57-105">只會影響將 EnableViewStateMac 屬性明確設定為 <code>false</code> 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c1b57-105">Only apps that explicitly set the EnableViewStateMac property to <code>false</code> are affected.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c1b57-106">建議</span><span class="sxs-lookup"><span data-stu-id="c1b57-106">Suggestion</span></span>

<span data-ttu-id="c1b57-107">EnableViewStateMac 必須假設為 true，而且必須解決任何產生的 MAC 錯誤（如[本指南](https://support.microsoft.com/kb/2915218)中所述，其中包含多個解決方法，視造成 MAC 錯誤的細節而定）。</span><span class="sxs-lookup"><span data-stu-id="c1b57-107">EnableViewStateMac must be assumed to be true, and any resulting MAC errors must be resolved (as explained in [this guidance](https://support.microsoft.com/kb/2915218), which contains multiple resolutions depending on the specifics of what is causing MAC errors).</span></span>

| <span data-ttu-id="c1b57-108">名稱</span><span class="sxs-lookup"><span data-stu-id="c1b57-108">Name</span></span>    | <span data-ttu-id="c1b57-109">值</span><span class="sxs-lookup"><span data-stu-id="c1b57-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c1b57-110">影響範圍</span><span class="sxs-lookup"><span data-stu-id="c1b57-110">Scope</span></span>   |<span data-ttu-id="c1b57-111">主要</span><span class="sxs-lookup"><span data-stu-id="c1b57-111">Major</span></span>|
|<span data-ttu-id="c1b57-112">版本</span><span class="sxs-lookup"><span data-stu-id="c1b57-112">Version</span></span>|<span data-ttu-id="c1b57-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="c1b57-113">4.5.2</span></span>|
|<span data-ttu-id="c1b57-114">類型</span><span class="sxs-lookup"><span data-stu-id="c1b57-114">Type</span></span>|<span data-ttu-id="c1b57-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="c1b57-115">Runtime</span></span>|
