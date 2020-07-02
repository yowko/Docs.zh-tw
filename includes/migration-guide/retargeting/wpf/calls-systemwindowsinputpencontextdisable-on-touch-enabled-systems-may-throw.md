---
ms.openlocfilehash: a44458484ea09c566defeabc9b604bd55d994e93
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617524"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a><span data-ttu-id="32454-101">在具有觸控功能的系統上呼叫 System.Windows.Input.PenContext.Disable 可能會擲回 ArgumentException</span><span class="sxs-lookup"><span data-stu-id="32454-101">Calls to System.Windows.Input.PenContext.Disable on touch-enabled systems may throw an ArgumentException</span></span>

#### <a name="details"></a><span data-ttu-id="32454-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="32454-102">Details</span></span>

<span data-ttu-id="32454-103">在某些情況下，在具有觸控功能的系統上呼叫內部 **System.Windows.Intput.PenContext.Disable** 方法，可能會擲回由於重新進入而未處理的 `T:System.ArgumentException`。</span><span class="sxs-lookup"><span data-stu-id="32454-103">Under some circumstances, calls to the internal **System.Windows.Intput.PenContext.Disable** method on touch-enabled systems may throw an unhandled `T:System.ArgumentException` because of reentrancy.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="32454-104">建議</span><span class="sxs-lookup"><span data-stu-id="32454-104">Suggestion</span></span>

<span data-ttu-id="32454-105">.NET Framework 4.7 中已解決這個問題。</span><span class="sxs-lookup"><span data-stu-id="32454-105">This issue has been addressed in the .NET Framework 4.7.</span></span> <span data-ttu-id="32454-106">若要避免這個例外狀況，請升級至從 .NET Framework 4.7 開始的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="32454-106">To prevent the exception, upgrade to a version of the .NET Framework starting with the .NET Framework 4.7.</span></span>

| <span data-ttu-id="32454-107">名稱</span><span class="sxs-lookup"><span data-stu-id="32454-107">Name</span></span>    | <span data-ttu-id="32454-108">值</span><span class="sxs-lookup"><span data-stu-id="32454-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="32454-109">影響範圍</span><span class="sxs-lookup"><span data-stu-id="32454-109">Scope</span></span>   | <span data-ttu-id="32454-110">Edge</span><span class="sxs-lookup"><span data-stu-id="32454-110">Edge</span></span>        |
| <span data-ttu-id="32454-111">版本</span><span class="sxs-lookup"><span data-stu-id="32454-111">Version</span></span> | <span data-ttu-id="32454-112">4.6.1</span><span class="sxs-lookup"><span data-stu-id="32454-112">4.6.1</span></span>       |
| <span data-ttu-id="32454-113">類型</span><span class="sxs-lookup"><span data-stu-id="32454-113">Type</span></span>    | <span data-ttu-id="32454-114">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="32454-114">Retargeting</span></span> |
