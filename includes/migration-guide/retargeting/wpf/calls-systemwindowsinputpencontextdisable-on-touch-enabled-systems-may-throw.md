---
ms.openlocfilehash: 6bb8c87af66e744514fb43e628c6423487342ac2
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2019
ms.locfileid: "72887744"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a><span data-ttu-id="33b61-101">在具有觸控功能的系統上呼叫 System.Windows.Input.PenContext.Disable 可能會擲回 ArgumentException</span><span class="sxs-lookup"><span data-stu-id="33b61-101">Calls to System.Windows.Input.PenContext.Disable on touch-enabled systems may throw an ArgumentException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="33b61-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="33b61-102">Details</span></span>|<span data-ttu-id="33b61-103">在某些情況下，在具有觸控功能的系統上呼叫內部 **System.Windows.Intput.PenContext.Disable** 方法，可能會擲回由於重新進入而未處理的 <code>T:System.ArgumentException</code>。</span><span class="sxs-lookup"><span data-stu-id="33b61-103">Under some circumstances, calls to the internal **System.Windows.Intput.PenContext.Disable** method on touch-enabled systems may throw an unhandled <code>T:System.ArgumentException</code> because of reentrancy.</span></span>|
|<span data-ttu-id="33b61-104">建議</span><span class="sxs-lookup"><span data-stu-id="33b61-104">Suggestion</span></span>|<span data-ttu-id="33b61-105">.NET Framework 4.7 中已解決這個問題。</span><span class="sxs-lookup"><span data-stu-id="33b61-105">This issue has been addressed in the .NET Framework 4.7.</span></span> <span data-ttu-id="33b61-106">若要避免這個例外狀況，請升級至從 .NET Framework 4.7 開始的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="33b61-106">To prevent the exception, upgrade to a version of the .NET Framework starting with the .NET Framework 4.7.</span></span>|
|<span data-ttu-id="33b61-107">範圍</span><span class="sxs-lookup"><span data-stu-id="33b61-107">Scope</span></span>|<span data-ttu-id="33b61-108">邊緣</span><span class="sxs-lookup"><span data-stu-id="33b61-108">Edge</span></span>|
|<span data-ttu-id="33b61-109">版本</span><span class="sxs-lookup"><span data-stu-id="33b61-109">Version</span></span>|<span data-ttu-id="33b61-110">4.6.1</span><span class="sxs-lookup"><span data-stu-id="33b61-110">4.6.1</span></span>|
|<span data-ttu-id="33b61-111">輸入</span><span class="sxs-lookup"><span data-stu-id="33b61-111">Type</span></span>|<span data-ttu-id="33b61-112">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="33b61-112">Retargeting</span></span>|
