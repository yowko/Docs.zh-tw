---
ms.openlocfilehash: c1a2d76b4e596acc395da6cefed008078e57a336
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858510"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a><span data-ttu-id="b0819-101">在稍後的步驟中，偵錯工具才會顯示 Null 聯合器值</span><span class="sxs-lookup"><span data-stu-id="b0819-101">Null coalescer values are not visible in debugger until one step later</span></span>

|   |   |
|---|---|
|<span data-ttu-id="b0819-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b0819-102">Details</span></span>|<span data-ttu-id="b0819-103">.NET Framework 4.5 中的 Bug) 會導致在 64 位元版本的 Framework 上執行時，透過 Null 聯合運算設定的值不會立即於執行指派作業之後顯示在偵錯工具中。</span><span class="sxs-lookup"><span data-stu-id="b0819-103">A bug in the .NET Framework 4.5 causes values set via a null coalescing operation to not be visible in the debugger immediately after the assignment operation is executed when running on the 64-bit version of the Framework.</span></span>|
|<span data-ttu-id="b0819-104">建議</span><span class="sxs-lookup"><span data-stu-id="b0819-104">Suggestion</span></span>|<span data-ttu-id="b0819-105">在偵錯工具中逐步執行一段額外時間，將使本機/欄位的值正確更新。</span><span class="sxs-lookup"><span data-stu-id="b0819-105">Stepping one additional time in the debugger will cause the local/field's value to be correctly updated.</span></span> <span data-ttu-id="b0819-106">此外，此問題已在 .NET Framework 4.6 中修正；升級至該版 .NET Framework 應可解決此問題。</span><span class="sxs-lookup"><span data-stu-id="b0819-106">Also, this issue has been fixed in the .NET Framework 4.6; upgrading to that version of the Framework should solve the issue.</span></span>|
|<span data-ttu-id="b0819-107">範圍</span><span class="sxs-lookup"><span data-stu-id="b0819-107">Scope</span></span>|<span data-ttu-id="b0819-108">Edge</span><span class="sxs-lookup"><span data-stu-id="b0819-108">Edge</span></span>|
|<span data-ttu-id="b0819-109">版本</span><span class="sxs-lookup"><span data-stu-id="b0819-109">Version</span></span>|<span data-ttu-id="b0819-110">4.5</span><span class="sxs-lookup"><span data-stu-id="b0819-110">4.5</span></span>|
|<span data-ttu-id="b0819-111">類型</span><span class="sxs-lookup"><span data-stu-id="b0819-111">Type</span></span>|<span data-ttu-id="b0819-112">執行階段</span><span class="sxs-lookup"><span data-stu-id="b0819-112">Runtime</span></span>|

