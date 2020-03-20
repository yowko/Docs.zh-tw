---
ms.openlocfilehash: 6bb8c87af66e744514fb43e628c6423487342ac2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "72887744"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a><span data-ttu-id="2ffe3-101">在具有觸控功能的系統上呼叫 System.Windows.Input.PenContext.Disable 可能會擲回 ArgumentException</span><span class="sxs-lookup"><span data-stu-id="2ffe3-101">Calls to System.Windows.Input.PenContext.Disable on touch-enabled systems may throw an ArgumentException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="2ffe3-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2ffe3-102">Details</span></span>|<span data-ttu-id="2ffe3-103">在某些情況下，在具有觸控功能的系統上呼叫內部 **System.Windows.Intput.PenContext.Disable** 方法，可能會擲回由於重新進入而未處理的 <code>T:System.ArgumentException</code>。</span><span class="sxs-lookup"><span data-stu-id="2ffe3-103">Under some circumstances, calls to the internal **System.Windows.Intput.PenContext.Disable** method on touch-enabled systems may throw an unhandled <code>T:System.ArgumentException</code> because of reentrancy.</span></span>|
|<span data-ttu-id="2ffe3-104">建議</span><span class="sxs-lookup"><span data-stu-id="2ffe3-104">Suggestion</span></span>|<span data-ttu-id="2ffe3-105">.NET Framework 4.7 中已解決這個問題。</span><span class="sxs-lookup"><span data-stu-id="2ffe3-105">This issue has been addressed in the .NET Framework 4.7.</span></span> <span data-ttu-id="2ffe3-106">若要避免這個例外狀況，請升級至從 .NET Framework 4.7 開始的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="2ffe3-106">To prevent the exception, upgrade to a version of the .NET Framework starting with the .NET Framework 4.7.</span></span>|
|<span data-ttu-id="2ffe3-107">影響範圍</span><span class="sxs-lookup"><span data-stu-id="2ffe3-107">Scope</span></span>|<span data-ttu-id="2ffe3-108">Edge</span><span class="sxs-lookup"><span data-stu-id="2ffe3-108">Edge</span></span>|
|<span data-ttu-id="2ffe3-109">版本</span><span class="sxs-lookup"><span data-stu-id="2ffe3-109">Version</span></span>|<span data-ttu-id="2ffe3-110">4.6.1</span><span class="sxs-lookup"><span data-stu-id="2ffe3-110">4.6.1</span></span>|
|<span data-ttu-id="2ffe3-111">類型</span><span class="sxs-lookup"><span data-stu-id="2ffe3-111">Type</span></span>|<span data-ttu-id="2ffe3-112">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="2ffe3-112">Retargeting</span></span>|
