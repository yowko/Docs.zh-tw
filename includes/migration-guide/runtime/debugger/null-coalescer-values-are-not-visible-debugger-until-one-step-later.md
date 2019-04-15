---
ms.openlocfilehash: 22f8e3bb1ba72379b3f5fc87a077e5fe57f89bf8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235119"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a><span data-ttu-id="dff98-101">在稍後的步驟中，偵錯工具才會顯示 Null 聯合器值</span><span class="sxs-lookup"><span data-stu-id="dff98-101">Null coalescer values are not visible in debugger until one step later</span></span>

|   |   |
|---|---|
|<span data-ttu-id="dff98-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="dff98-102">Details</span></span>|<span data-ttu-id="dff98-103">.NET Framework 4.5 中的 Bug) 會導致在 64 位元版本的 Framework 上執行時，透過 Null 聯合運算設定的值不會立即於執行指派作業之後顯示在偵錯工具中。</span><span class="sxs-lookup"><span data-stu-id="dff98-103">A bug in the .NET Framework 4.5 causes values set via a null coalescing operation to not be visible in the debugger immediately after the assignment operation is executed when running on the 64-bit version of the Framework.</span></span>|
|<span data-ttu-id="dff98-104">建議</span><span class="sxs-lookup"><span data-stu-id="dff98-104">Suggestion</span></span>|<span data-ttu-id="dff98-105">在偵錯工具中逐步執行一段額外時間，將使本機/欄位的值正確更新。</span><span class="sxs-lookup"><span data-stu-id="dff98-105">Stepping one additional time in the debugger will cause the local/field's value to be correctly updated.</span></span> <span data-ttu-id="dff98-106">此外，此問題已在 .NET Framework 4.6 中修正；升級至該版 .NET Framework 應可解決此問題。</span><span class="sxs-lookup"><span data-stu-id="dff98-106">Also, this issue has been fixed in the .NET Framework 4.6; upgrading to that version of the Framework should solve the issue.</span></span>|
|<span data-ttu-id="dff98-107">範圍</span><span class="sxs-lookup"><span data-stu-id="dff98-107">Scope</span></span>|<span data-ttu-id="dff98-108">Edge</span><span class="sxs-lookup"><span data-stu-id="dff98-108">Edge</span></span>|
|<span data-ttu-id="dff98-109">版本</span><span class="sxs-lookup"><span data-stu-id="dff98-109">Version</span></span>|<span data-ttu-id="dff98-110">4.5</span><span class="sxs-lookup"><span data-stu-id="dff98-110">4.5</span></span>|
|<span data-ttu-id="dff98-111">類型</span><span class="sxs-lookup"><span data-stu-id="dff98-111">Type</span></span>|<span data-ttu-id="dff98-112">執行階段</span><span class="sxs-lookup"><span data-stu-id="dff98-112">Runtime</span></span>|
