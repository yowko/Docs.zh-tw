---
ms.openlocfilehash: 39a329597ef28e002242103a247515d94761676a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234646"
---
### <a name="resolveassemblyreference-task-now-warns-of-dependencies-with-the-wrong-architecture"></a><span data-ttu-id="5ceae-101">ResolveAssemblyReference 工作現在會發出警告，指出相依於錯誤的架構</span><span class="sxs-lookup"><span data-stu-id="5ceae-101">ResolveAssemblyReference task now warns of dependencies with the wrong architecture</span></span>

|   |   |
|---|---|
|<span data-ttu-id="5ceae-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5ceae-102">Details</span></span>|<span data-ttu-id="5ceae-103">這項工作會發出警告 MSB3270，指出某個參考或參考的任何一個相依性不符合應用程式的架構。</span><span class="sxs-lookup"><span data-stu-id="5ceae-103">The task emits a warning, MSB3270, which indicates that a reference or any of its dependencies does not match the app's architecture.</span></span> <span data-ttu-id="5ceae-104">例如，如果使用 <code>AnyCPU</code> 選項編譯的應用程式包含 x86 參考，則會發生此情況。</span><span class="sxs-lookup"><span data-stu-id="5ceae-104">For example, this occurs if an app that was compiled with the <code>AnyCPU</code> option includes an x86 reference.</span></span> <span data-ttu-id="5ceae-105">這類情況會導致應用程式在執行階段失敗 (在本範例中，如果應用程式部署為 x64 處理序)。</span><span class="sxs-lookup"><span data-stu-id="5ceae-105">Such a scenario could result in an app failure at run time (in this case, if the app is deployed as an x64 process).</span></span>|
|<span data-ttu-id="5ceae-106">建議</span><span class="sxs-lookup"><span data-stu-id="5ceae-106">Suggestion</span></span>|<span data-ttu-id="5ceae-107">影響可分為下列兩方面：</span><span class="sxs-lookup"><span data-stu-id="5ceae-107">There are two areas of impact:</span></span><ul><li><span data-ttu-id="5ceae-108">重新編譯會產生在舊版 MSBuild 下編譯應用程式時未顯示的警告。</span><span class="sxs-lookup"><span data-stu-id="5ceae-108">Recompilation generates warnings that did not appear when the app was compiled under a previous version of MSBuild.</span></span> <span data-ttu-id="5ceae-109">不過，由於此警告識別執行階段失敗的可能來源，因此應該加以調查和解決。</span><span class="sxs-lookup"><span data-stu-id="5ceae-109">However, because the warning identifies a possible source of runtime failure, it should be investigated and addressed.</span></span></li><li><span data-ttu-id="5ceae-110">如果將警告視為錯誤，應用程式將無法編譯。</span><span class="sxs-lookup"><span data-stu-id="5ceae-110">If warnings are treated as errors, the app will fail to compile.</span></span></li></ul>|
|<span data-ttu-id="5ceae-111">範圍</span><span class="sxs-lookup"><span data-stu-id="5ceae-111">Scope</span></span>|<span data-ttu-id="5ceae-112">次要</span><span class="sxs-lookup"><span data-stu-id="5ceae-112">Minor</span></span>|
|<span data-ttu-id="5ceae-113">版本</span><span class="sxs-lookup"><span data-stu-id="5ceae-113">Version</span></span>|<span data-ttu-id="5ceae-114">4.5.1</span><span class="sxs-lookup"><span data-stu-id="5ceae-114">4.5.1</span></span>|
|<span data-ttu-id="5ceae-115">類型</span><span class="sxs-lookup"><span data-stu-id="5ceae-115">Type</span></span>|<span data-ttu-id="5ceae-116">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="5ceae-116">Retargeting</span></span>|
