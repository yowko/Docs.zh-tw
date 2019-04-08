---
ms.openlocfilehash: 0778285ef1b5702bd79743038a1bd21ba04612d6
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760972"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a><span data-ttu-id="f4a96-101">在具有觸控功能的系統上呼叫 System.Windows.Input.PenContext.Disable 可能會擲回 ArgumentException</span><span class="sxs-lookup"><span data-stu-id="f4a96-101">Calls to System.Windows.Input.PenContext.Disable on touch-enabled systems may throw an ArgumentException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="f4a96-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f4a96-102">Details</span></span>|<span data-ttu-id="f4a96-103">在某些情況下，在具有觸控功能的系統上呼叫內部 <strong>System.Windows.Intput.PenContext.Disable</strong> 方法，可能會擲回由於重新進入而未處理的 <code>T:System.ArgumentException</code>。</span><span class="sxs-lookup"><span data-stu-id="f4a96-103">Under some circumstances, calls to the internal <strong>System.Windows.Intput.PenContext.Disable</strong> method on touch-enabled systems may throw an unhandled <code>T:System.ArgumentException</code> because of reentrancy.</span></span>|
|<span data-ttu-id="f4a96-104">建議</span><span class="sxs-lookup"><span data-stu-id="f4a96-104">Suggestion</span></span>|<span data-ttu-id="f4a96-105">.NET Framework 4.7 中已解決這個問題。</span><span class="sxs-lookup"><span data-stu-id="f4a96-105">This issue has been addressed in the .NET Framework 4.7.</span></span> <span data-ttu-id="f4a96-106">若要避免這個例外狀況，請升級至從 .NET Framework 4.7 開始的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="f4a96-106">To prevent the exception, upgrade to a version of the .NET Framework starting with the .NET Framework 4.7.</span></span>|
|<span data-ttu-id="f4a96-107">範圍</span><span class="sxs-lookup"><span data-stu-id="f4a96-107">Scope</span></span>|<span data-ttu-id="f4a96-108">Edge</span><span class="sxs-lookup"><span data-stu-id="f4a96-108">Edge</span></span>|
|<span data-ttu-id="f4a96-109">版本</span><span class="sxs-lookup"><span data-stu-id="f4a96-109">Version</span></span>|<span data-ttu-id="f4a96-110">4.6.1</span><span class="sxs-lookup"><span data-stu-id="f4a96-110">4.6.1</span></span>|
|<span data-ttu-id="f4a96-111">類型</span><span class="sxs-lookup"><span data-stu-id="f4a96-111">Type</span></span>|<span data-ttu-id="f4a96-112">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="f4a96-112">Retargeting</span></span>|

