---
ms.openlocfilehash: 662c140f019add66ff6605d47ad1f32c3f50d711
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619976"
---
### <a name="eventsourcewriteevent-impls-must-pass-writeevent-the-same-parameters-that-it-received-plus-id"></a><span data-ttu-id="4f3dd-101">EventSource.WriteEvent impl 必須將收到的相同參數傳遞給 WriteEvent (再加上識別碼)</span><span class="sxs-lookup"><span data-stu-id="4f3dd-101">EventSource.WriteEvent impls must pass WriteEvent the same parameters that it received (plus ID)</span></span>

#### <a name="details"></a><span data-ttu-id="4f3dd-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="4f3dd-102">Details</span></span>

<span data-ttu-id="4f3dd-103">執行階段現在會強制執行指定下列作業的合約：定義 ETW 事件方法之衍生自 <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> 的類別在呼叫基底類別 <code>EventSource.WriteEvent</code> 方法時，必須在事件識別碼後面接著傳遞 ETW 事件方法的相同目的地引數。</span><span class="sxs-lookup"><span data-stu-id="4f3dd-103">The runtime now enforces the contract that specifies the following: A class derived from <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> that defines an ETW event method must call the base class <code>EventSource.WriteEvent</code> method with the event ID followed by the same arguments that the ETW event method was passed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4f3dd-104">建議</span><span class="sxs-lookup"><span data-stu-id="4f3dd-104">Suggestion</span></span>

<span data-ttu-id="4f3dd-105">如果 <xref:System.IndexOutOfRangeException?displayProperty=fullName> 讀取來自於違反此合約之事件來源的處理中 <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> 資料，則會擲回 <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4f3dd-105">An <xref:System.IndexOutOfRangeException?displayProperty=fullName> exception is thrown if an <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> reads <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> data in process for an event source that violates this contract.</span></span>

| <span data-ttu-id="4f3dd-106">名稱</span><span class="sxs-lookup"><span data-stu-id="4f3dd-106">Name</span></span>    | <span data-ttu-id="4f3dd-107">值</span><span class="sxs-lookup"><span data-stu-id="4f3dd-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4f3dd-108">影響範圍</span><span class="sxs-lookup"><span data-stu-id="4f3dd-108">Scope</span></span>   |<span data-ttu-id="4f3dd-109">Minor</span><span class="sxs-lookup"><span data-stu-id="4f3dd-109">Minor</span></span>|
|<span data-ttu-id="4f3dd-110">版本</span><span class="sxs-lookup"><span data-stu-id="4f3dd-110">Version</span></span>|<span data-ttu-id="4f3dd-111">4.5.1</span><span class="sxs-lookup"><span data-stu-id="4f3dd-111">4.5.1</span></span>|
|<span data-ttu-id="4f3dd-112">類型</span><span class="sxs-lookup"><span data-stu-id="4f3dd-112">Type</span></span>|<span data-ttu-id="4f3dd-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="4f3dd-113">Runtime</span></span>|
