---
ms.openlocfilehash: dbe96abebdc61fae469f7727673e6fcb93cbc739
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803253"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a><span data-ttu-id="77e50-101">無法再將 EnableViewStateMac 設定為 false</span><span class="sxs-lookup"><span data-stu-id="77e50-101">No longer able to set EnableViewStateMac to false</span></span>

|   |   |
|---|---|
|<span data-ttu-id="77e50-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="77e50-102">Details</span></span>|<span data-ttu-id="77e50-103">ASP.NET 不再允許開發人員指定 <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> 或 <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>。</span><span class="sxs-lookup"><span data-stu-id="77e50-103">ASP.NET no longer allows developers to specify <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> or <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>.</span></span> <span data-ttu-id="77e50-104">檢視狀態訊息驗證碼 (MAC) 現在會強制所有要求內嵌檢視狀態。</span><span class="sxs-lookup"><span data-stu-id="77e50-104">The view state message authentication code (MAC) is now enforced for all requests with embedded view state.</span></span> <span data-ttu-id="77e50-105">只會影響將 EnableViewStateMac 屬性明確設定為 <code>false</code> 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="77e50-105">Only apps that explicitly set the EnableViewStateMac property to <code>false</code> are affected.</span></span>|
|<span data-ttu-id="77e50-106">建議</span><span class="sxs-lookup"><span data-stu-id="77e50-106">Suggestion</span></span>|<span data-ttu-id="77e50-107">啟用ViewStateMac必須假定為 true，並且必須解決任何生成的 MAC 錯誤（如[本指南](https://support.microsoft.com/kb/2915218)中所述，其中包含多個解析度，具體取決於導致 MAC 錯誤的原因）。</span><span class="sxs-lookup"><span data-stu-id="77e50-107">EnableViewStateMac must be assumed to be true, and any resulting MAC errors must be resolved (as explained in [this guidance](https://support.microsoft.com/kb/2915218), which contains multiple resolutions depending on the specifics of what is causing MAC errors).</span></span>|
|<span data-ttu-id="77e50-108">影響範圍</span><span class="sxs-lookup"><span data-stu-id="77e50-108">Scope</span></span>|<span data-ttu-id="77e50-109">主要</span><span class="sxs-lookup"><span data-stu-id="77e50-109">Major</span></span>|
|<span data-ttu-id="77e50-110">版本</span><span class="sxs-lookup"><span data-stu-id="77e50-110">Version</span></span>|<span data-ttu-id="77e50-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="77e50-111">4.5.2</span></span>|
|<span data-ttu-id="77e50-112">類型</span><span class="sxs-lookup"><span data-stu-id="77e50-112">Type</span></span>|<span data-ttu-id="77e50-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="77e50-113">Runtime</span></span>|
