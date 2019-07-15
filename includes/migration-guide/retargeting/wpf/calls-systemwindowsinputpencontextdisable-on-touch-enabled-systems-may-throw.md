---
ms.openlocfilehash: 0778285ef1b5702bd79743038a1bd21ba04612d6
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804358"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a><span data-ttu-id="55921-101">在具有觸控功能的系統上呼叫 System.Windows.Input.PenContext.Disable 可能會擲回 ArgumentException</span><span class="sxs-lookup"><span data-stu-id="55921-101">Calls to System.Windows.Input.PenContext.Disable on touch-enabled systems may throw an ArgumentException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="55921-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="55921-102">Details</span></span>|<span data-ttu-id="55921-103">在某些情況下，在具有觸控功能的系統上呼叫內部 <strong>System.Windows.Intput.PenContext.Disable</strong> 方法，可能會擲回由於重新進入而未處理的 <code>T:System.ArgumentException</code>。</span><span class="sxs-lookup"><span data-stu-id="55921-103">Under some circumstances, calls to the internal <strong>System.Windows.Intput.PenContext.Disable</strong> method on touch-enabled systems may throw an unhandled <code>T:System.ArgumentException</code> because of reentrancy.</span></span>|
|<span data-ttu-id="55921-104">建議</span><span class="sxs-lookup"><span data-stu-id="55921-104">Suggestion</span></span>|<span data-ttu-id="55921-105">.NET Framework 4.7 中已解決這個問題。</span><span class="sxs-lookup"><span data-stu-id="55921-105">This issue has been addressed in the .NET Framework 4.7.</span></span> <span data-ttu-id="55921-106">若要避免這個例外狀況，請升級至從 .NET Framework 4.7 開始的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="55921-106">To prevent the exception, upgrade to a version of the .NET Framework starting with the .NET Framework 4.7.</span></span>|
|<span data-ttu-id="55921-107">範圍</span><span class="sxs-lookup"><span data-stu-id="55921-107">Scope</span></span>|<span data-ttu-id="55921-108">Edge</span><span class="sxs-lookup"><span data-stu-id="55921-108">Edge</span></span>|
|<span data-ttu-id="55921-109">版本</span><span class="sxs-lookup"><span data-stu-id="55921-109">Version</span></span>|<span data-ttu-id="55921-110">4.6.1</span><span class="sxs-lookup"><span data-stu-id="55921-110">4.6.1</span></span>|
|<span data-ttu-id="55921-111">類型</span><span class="sxs-lookup"><span data-stu-id="55921-111">Type</span></span>|<span data-ttu-id="55921-112">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="55921-112">Retargeting</span></span>|

