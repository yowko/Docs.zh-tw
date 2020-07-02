---
ms.openlocfilehash: 4d410811095786b33580d25f6c6eab3ac2f27148
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616036"
---
### <a name="resolveassemblyreference-task-now-warns-of-dependencies-with-the-wrong-architecture"></a><span data-ttu-id="d6df2-101">ResolveAssemblyReference 工作現在會發出警告，指出相依於錯誤的架構</span><span class="sxs-lookup"><span data-stu-id="d6df2-101">ResolveAssemblyReference task now warns of dependencies with the wrong architecture</span></span>

#### <a name="details"></a><span data-ttu-id="d6df2-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d6df2-102">Details</span></span>

<span data-ttu-id="d6df2-103">這項工作會發出警告 MSB3270，指出某個參考或參考的任何一個相依性不符合應用程式的架構。</span><span class="sxs-lookup"><span data-stu-id="d6df2-103">The task emits a warning, MSB3270, which indicates that a reference or any of its dependencies does not match the app's architecture.</span></span> <span data-ttu-id="d6df2-104">例如，如果使用 `AnyCPU` 選項編譯的應用程式包含 x86 參考，則會發生此情況。</span><span class="sxs-lookup"><span data-stu-id="d6df2-104">For example, this occurs if an app that was compiled with the `AnyCPU` option includes an x86 reference.</span></span> <span data-ttu-id="d6df2-105">這類情況會導致應用程式在執行階段失敗 (在本範例中，如果應用程式部署為 x64 處理序)。</span><span class="sxs-lookup"><span data-stu-id="d6df2-105">Such a scenario could result in an app failure at run time (in this case, if the app is deployed as an x64 process).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d6df2-106">建議</span><span class="sxs-lookup"><span data-stu-id="d6df2-106">Suggestion</span></span>

<span data-ttu-id="d6df2-107">影響可分為下列兩方面：</span><span class="sxs-lookup"><span data-stu-id="d6df2-107">There are two areas of impact:</span></span>

- <span data-ttu-id="d6df2-108">重新編譯會產生在舊版 MSBuild 下編譯應用程式時未顯示的警告。</span><span class="sxs-lookup"><span data-stu-id="d6df2-108">Recompilation generates warnings that did not appear when the app was compiled under a previous version of MSBuild.</span></span> <span data-ttu-id="d6df2-109">不過，由於此警告識別執行階段失敗的可能來源，因此應該加以調查和解決。</span><span class="sxs-lookup"><span data-stu-id="d6df2-109">However, because the warning identifies a possible source of runtime failure, it should be investigated and addressed.</span></span>
- <span data-ttu-id="d6df2-110">如果將警告視為錯誤，應用程式將無法編譯。</span><span class="sxs-lookup"><span data-stu-id="d6df2-110">If warnings are treated as errors, the app will fail to compile.</span></span>

| <span data-ttu-id="d6df2-111">名稱</span><span class="sxs-lookup"><span data-stu-id="d6df2-111">Name</span></span>    | <span data-ttu-id="d6df2-112">值</span><span class="sxs-lookup"><span data-stu-id="d6df2-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d6df2-113">影響範圍</span><span class="sxs-lookup"><span data-stu-id="d6df2-113">Scope</span></span>   | <span data-ttu-id="d6df2-114">Minor</span><span class="sxs-lookup"><span data-stu-id="d6df2-114">Minor</span></span>       |
| <span data-ttu-id="d6df2-115">版本</span><span class="sxs-lookup"><span data-stu-id="d6df2-115">Version</span></span> | <span data-ttu-id="d6df2-116">4.5.1</span><span class="sxs-lookup"><span data-stu-id="d6df2-116">4.5.1</span></span>       |
| <span data-ttu-id="d6df2-117">類型</span><span class="sxs-lookup"><span data-stu-id="d6df2-117">Type</span></span>    | <span data-ttu-id="d6df2-118">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="d6df2-118">Retargeting</span></span> |
