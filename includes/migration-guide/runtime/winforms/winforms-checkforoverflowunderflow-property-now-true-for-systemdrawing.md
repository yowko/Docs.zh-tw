---
ms.openlocfilehash: 8b2a01eb6dfdd5bd2bcbef6014d4edeb3ec82ac1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235158"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a><span data-ttu-id="6c345-101">WinForm 的 CheckForOverflowUnderflow 屬性對於 System.Drawing 現在是 true</span><span class="sxs-lookup"><span data-stu-id="6c345-101">WinForm's CheckForOverflowUnderflow property is now true for System.Drawing</span></span>

|   |   |
|---|---|
|<span data-ttu-id="6c345-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="6c345-102">Details</span></span>|<span data-ttu-id="6c345-103">System.Drawing.dll 組件的 CheckForOverflowUnderflow 屬性設定為 true。</span><span class="sxs-lookup"><span data-stu-id="6c345-103">The CheckForOverflowUnderflow property for the System.Drawing.dll assembly is set to true.</span></span>|
|<span data-ttu-id="6c345-104">建議</span><span class="sxs-lookup"><span data-stu-id="6c345-104">Suggestion</span></span>|<span data-ttu-id="6c345-105">以往發生溢位時，結果會以無訊息模式截斷。</span><span class="sxs-lookup"><span data-stu-id="6c345-105">Previously when overflows occurred, the result would be silently truncated.</span></span> <span data-ttu-id="6c345-106">現在則會擲回 <xref:System.OverflowException?displayProperty=name> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6c345-106">Now an <xref:System.OverflowException?displayProperty=name> exception is thrown.</span></span>|
|<span data-ttu-id="6c345-107">範圍</span><span class="sxs-lookup"><span data-stu-id="6c345-107">Scope</span></span>|<span data-ttu-id="6c345-108">Edge</span><span class="sxs-lookup"><span data-stu-id="6c345-108">Edge</span></span>|
|<span data-ttu-id="6c345-109">版本</span><span class="sxs-lookup"><span data-stu-id="6c345-109">Version</span></span>|<span data-ttu-id="6c345-110">4.5</span><span class="sxs-lookup"><span data-stu-id="6c345-110">4.5</span></span>|
|<span data-ttu-id="6c345-111">類型</span><span class="sxs-lookup"><span data-stu-id="6c345-111">Type</span></span>|<span data-ttu-id="6c345-112">執行階段</span><span class="sxs-lookup"><span data-stu-id="6c345-112">Runtime</span></span>|
