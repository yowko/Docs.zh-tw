---
ms.openlocfilehash: 0e25d5d9b545e5cb400cbf701fb13da572fadf10
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614336"
---
### <a name="etw-event-names-cannot-differ-only-by-a-start-or-stop-suffix"></a><span data-ttu-id="53475-101">ETW 事件名稱不能只有 "Start" 或 "Stop" 尾碼不同</span><span class="sxs-lookup"><span data-stu-id="53475-101">ETW event names cannot differ only by a "Start" or "Stop" suffix</span></span>

#### <a name="details"></a><span data-ttu-id="53475-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="53475-102">Details</span></span>

<span data-ttu-id="53475-103">在 .NET Framework 4.6 和4.6.1 中，執行時間會在 <xref:System.ArgumentException> 兩個 Windows 事件追蹤（ETW）事件名稱不同于 "Start" 或 "Stop" 後置詞時擲回（當一個事件名為 `LogUser` 且另一個名為時 `LogUserStart` ）。</span><span class="sxs-lookup"><span data-stu-id="53475-103">In the .NET Framework 4.6 and 4.6.1, the runtime throws an <xref:System.ArgumentException> when two Event Tracing for Windows (ETW) event names differ only by a "Start" or "Stop" suffix (as when one event is named `LogUser` and another is named `LogUserStart`).</span></span> <span data-ttu-id="53475-104">在此情況下，執行階段無法建構事件來源，因此無法發出任何記錄。</span><span class="sxs-lookup"><span data-stu-id="53475-104">In this case, the runtime cannot construct the event source, which cannot emit any logging.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="53475-105">建議</span><span class="sxs-lookup"><span data-stu-id="53475-105">Suggestion</span></span>

<span data-ttu-id="53475-106">若要避免這個例外狀況，請確定沒有任何兩個事件名稱的差異只在於 "Start" 或 "Stop" 後置詞。從 .NET Framework 4.6.2 開始，會移除這項需求;執行時間可以區分只有 "Start" 和 "Stop" 尾碼不同的事件名稱。</span><span class="sxs-lookup"><span data-stu-id="53475-106">To prevent the exception, ensure that no two event names differ only by a "Start" or "Stop" suffix.This requirement is removed starting with the .NET Framework 4.6.2; the runtime can disambiguate event names that differ only by the "Start" and "Stop" suffix.</span></span>

| <span data-ttu-id="53475-107">名稱</span><span class="sxs-lookup"><span data-stu-id="53475-107">Name</span></span>    | <span data-ttu-id="53475-108">值</span><span class="sxs-lookup"><span data-stu-id="53475-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="53475-109">影響範圍</span><span class="sxs-lookup"><span data-stu-id="53475-109">Scope</span></span>   | <span data-ttu-id="53475-110">Edge</span><span class="sxs-lookup"><span data-stu-id="53475-110">Edge</span></span>        |
| <span data-ttu-id="53475-111">版本</span><span class="sxs-lookup"><span data-stu-id="53475-111">Version</span></span> | <span data-ttu-id="53475-112">4.6</span><span class="sxs-lookup"><span data-stu-id="53475-112">4.6</span></span>         |
| <span data-ttu-id="53475-113">類型</span><span class="sxs-lookup"><span data-stu-id="53475-113">Type</span></span>    | <span data-ttu-id="53475-114">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="53475-114">Retargeting</span></span> |
