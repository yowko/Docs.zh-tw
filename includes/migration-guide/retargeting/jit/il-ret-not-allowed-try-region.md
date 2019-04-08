---
ms.openlocfilehash: 060da3ebc60057554fd572bd2569652afee6bd0f
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58761001"
---
### <a name="il-ret-not-allowed-in-a-try-region"></a><span data-ttu-id="fd5c1-101">try 區域中不允許 IL ret</span><span class="sxs-lookup"><span data-stu-id="fd5c1-101">IL ret not allowed in a try region</span></span>

|   |   |
|---|---|
|<span data-ttu-id="fd5c1-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="fd5c1-102">Details</span></span>|<span data-ttu-id="fd5c1-103">不同於 JIT64 Just-In-Time 編譯器，RyuJIT (用於 .NET Framework 4.6) 不允許在 try 區域中使用 IL ret 指令。</span><span class="sxs-lookup"><span data-stu-id="fd5c1-103">Unlike the JIT64 just-in-time compiler, RyuJIT (used in .NET Framework 4.6) does not allow an IL ret instruction in a try region.</span></span> <span data-ttu-id="fd5c1-104">ECMA-335 規格不允許從 try 區域傳回，而且不會有已知的受控編譯器產生這類 IL。</span><span class="sxs-lookup"><span data-stu-id="fd5c1-104">Returning from a try region is disallowed by the ECMA-335 specification, and no known managed compiler generates such IL.</span></span> <span data-ttu-id="fd5c1-105">不過，如果這類 IL 是由反映發出所產生，則 JIT64 編譯器將會執行這類 IL。</span><span class="sxs-lookup"><span data-stu-id="fd5c1-105">However, the JIT64 compiler will execute such IL if it is generated using reflection emit.</span></span>|
|<span data-ttu-id="fd5c1-106">建議</span><span class="sxs-lookup"><span data-stu-id="fd5c1-106">Suggestion</span></span>|<span data-ttu-id="fd5c1-107">如果應用程式產生在 try 區域中包含 ret opcode 的 IL，應用程式可以 .NET Framework 4.5 為目標，即可使用舊的 JIT，以避免這項中斷。</span><span class="sxs-lookup"><span data-stu-id="fd5c1-107">If an app is generating IL that includes a ret opcode in a try region, the app may target .NET Framework 4.5 to use the old JIT and avoid this break.</span></span> <span data-ttu-id="fd5c1-108">或者，可以將產生的 IL 更新為在 try 區域之後傳回。</span><span class="sxs-lookup"><span data-stu-id="fd5c1-108">Alternatively, the generated IL may be updated to return after the try region.</span></span>|
|<span data-ttu-id="fd5c1-109">範圍</span><span class="sxs-lookup"><span data-stu-id="fd5c1-109">Scope</span></span>|<span data-ttu-id="fd5c1-110">Edge</span><span class="sxs-lookup"><span data-stu-id="fd5c1-110">Edge</span></span>|
|<span data-ttu-id="fd5c1-111">版本</span><span class="sxs-lookup"><span data-stu-id="fd5c1-111">Version</span></span>|<span data-ttu-id="fd5c1-112">4.6</span><span class="sxs-lookup"><span data-stu-id="fd5c1-112">4.6</span></span>|
|<span data-ttu-id="fd5c1-113">類型</span><span class="sxs-lookup"><span data-stu-id="fd5c1-113">Type</span></span>|<span data-ttu-id="fd5c1-114">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="fd5c1-114">Retargeting</span></span>|

