---
ms.openlocfilehash: 3cd5052dffcb059c240a310e0b89384f28409264
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234397"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a><span data-ttu-id="0c733-101">在具有觸控功能的系統上呼叫 System.Windows.Input.PenContext.Disable 可能會擲回 ArgumentException</span><span class="sxs-lookup"><span data-stu-id="0c733-101">Calls to System.Windows.Input.PenContext.Disable on touch-enabled systems may throw an ArgumentException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="0c733-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0c733-102">Details</span></span>|<span data-ttu-id="0c733-103">在某些情況下，在具有觸控功能的系統上呼叫內部 <strong>System.Windows.Intput.PenContext.Disable</strong> 方法，可能會擲回由於重新進入而未處理的 <code>T:System.ArgumentException</code>。</span><span class="sxs-lookup"><span data-stu-id="0c733-103">Under some circumstances, calls to the internal <strong>System.Windows.Intput.PenContext.Disable</strong> method on touch-enabled systems may throw an unhandled <code>T:System.ArgumentException</code> because of reentrancy.</span></span>|
|<span data-ttu-id="0c733-104">建議</span><span class="sxs-lookup"><span data-stu-id="0c733-104">Suggestion</span></span>|<span data-ttu-id="0c733-105">.NET Framework 4.7 中已解決這個問題。</span><span class="sxs-lookup"><span data-stu-id="0c733-105">This issue has been addressed in the .NET Framework 4.7.</span></span> <span data-ttu-id="0c733-106">若要避免這個例外狀況，請升級至從 .NET Framework 4.7 開始的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="0c733-106">To prevent the exception, upgrade to a version of the .NET Framework starting with the .NET Framework 4.7.</span></span>|
|<span data-ttu-id="0c733-107">範圍</span><span class="sxs-lookup"><span data-stu-id="0c733-107">Scope</span></span>|<span data-ttu-id="0c733-108">Edge</span><span class="sxs-lookup"><span data-stu-id="0c733-108">Edge</span></span>|
|<span data-ttu-id="0c733-109">版本</span><span class="sxs-lookup"><span data-stu-id="0c733-109">Version</span></span>|<span data-ttu-id="0c733-110">4.6.1</span><span class="sxs-lookup"><span data-stu-id="0c733-110">4.6.1</span></span>|
|<span data-ttu-id="0c733-111">類型</span><span class="sxs-lookup"><span data-stu-id="0c733-111">Type</span></span>|<span data-ttu-id="0c733-112">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="0c733-112">Retargeting</span></span>|
