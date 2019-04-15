---
ms.openlocfilehash: dbe96abebdc61fae469f7727673e6fcb93cbc739
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236626"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a><span data-ttu-id="1e934-101">無法再將 EnableViewStateMac 設定為 false</span><span class="sxs-lookup"><span data-stu-id="1e934-101">No longer able to set EnableViewStateMac to false</span></span>

|   |   |
|---|---|
|<span data-ttu-id="1e934-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1e934-102">Details</span></span>|<span data-ttu-id="1e934-103">ASP.NET 不再允許開發人員指定 <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> 或 <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>。</span><span class="sxs-lookup"><span data-stu-id="1e934-103">ASP.NET no longer allows developers to specify <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> or <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>.</span></span> <span data-ttu-id="1e934-104">檢視狀態訊息驗證碼 (MAC) 現在會強制所有要求內嵌檢視狀態。</span><span class="sxs-lookup"><span data-stu-id="1e934-104">The view state message authentication code (MAC) is now enforced for all requests with embedded view state.</span></span> <span data-ttu-id="1e934-105">只會影響將 EnableViewStateMac 屬性明確設定為 <code>false</code> 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1e934-105">Only apps that explicitly set the EnableViewStateMac property to <code>false</code> are affected.</span></span>|
|<span data-ttu-id="1e934-106">建議</span><span class="sxs-lookup"><span data-stu-id="1e934-106">Suggestion</span></span>|<span data-ttu-id="1e934-107">EnableViewStateMac 必須假設為 true，而且必須解決任何產生的 MAC 錯誤 (如[這個指引](https://support.microsoft.com/kb/2915218)中所述，其中包含多個解決方法，視造成 MAC 錯誤的特定原因而定)。</span><span class="sxs-lookup"><span data-stu-id="1e934-107">EnableViewStateMac must be assumed to be true, and any resulting MAC errors must be resolved (as explained in [this guidance](https://support.microsoft.com/kb/2915218), which contains multiple resolutions depending on the specifics of what is causing MAC errors).</span></span>|
|<span data-ttu-id="1e934-108">範圍</span><span class="sxs-lookup"><span data-stu-id="1e934-108">Scope</span></span>|<span data-ttu-id="1e934-109">主要</span><span class="sxs-lookup"><span data-stu-id="1e934-109">Major</span></span>|
|<span data-ttu-id="1e934-110">版本</span><span class="sxs-lookup"><span data-stu-id="1e934-110">Version</span></span>|<span data-ttu-id="1e934-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="1e934-111">4.5.2</span></span>|
|<span data-ttu-id="1e934-112">類型</span><span class="sxs-lookup"><span data-stu-id="1e934-112">Type</span></span>|<span data-ttu-id="1e934-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="1e934-113">Runtime</span></span>|
