---
ms.openlocfilehash: 47d0aa554d88726caca35fa6bebe4d863fdc0695
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235123"
---
### <a name="eventsourcewriteevent-impls-must-pass-writeevent-the-same-parameters-that-it-received-plus-id"></a><span data-ttu-id="8b388-101">EventSource.WriteEvent impl 必須將收到的相同參數傳遞給 WriteEvent (再加上識別碼)</span><span class="sxs-lookup"><span data-stu-id="8b388-101">EventSource.WriteEvent impls must pass WriteEvent the same parameters that it received (plus ID)</span></span>

|   |   |
|---|---|
|<span data-ttu-id="8b388-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8b388-102">Details</span></span>|<span data-ttu-id="8b388-103">執行階段現在會強制執行指定下列作業的合約：定義 ETW 事件方法之衍生自 <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> 的類別在呼叫基底類別 <code>EventSource.WriteEvent</code> 方法時，必須在事件識別碼後面接著傳遞 ETW 事件方法的相同目的地引數。</span><span class="sxs-lookup"><span data-stu-id="8b388-103">The runtime now enforces the contract that specifies the following: A class derived from <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> that defines an ETW event method must call the base class <code>EventSource.WriteEvent</code> method with the event ID followed by the same arguments that the ETW event method was passed.</span></span>|
|<span data-ttu-id="8b388-104">建議</span><span class="sxs-lookup"><span data-stu-id="8b388-104">Suggestion</span></span>|<span data-ttu-id="8b388-105">如果 <xref:System.IndexOutOfRangeException?displayProperty=name> 讀取來自於違反此合約之事件來源的處理中 <xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> 資料，則會擲回 <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8b388-105">An <xref:System.IndexOutOfRangeException?displayProperty=name> exception is thrown if an <xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> reads <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> data in process for an event source that violates this contract.</span></span>|
|<span data-ttu-id="8b388-106">範圍</span><span class="sxs-lookup"><span data-stu-id="8b388-106">Scope</span></span>|<span data-ttu-id="8b388-107">次要</span><span class="sxs-lookup"><span data-stu-id="8b388-107">Minor</span></span>|
|<span data-ttu-id="8b388-108">版本</span><span class="sxs-lookup"><span data-stu-id="8b388-108">Version</span></span>|<span data-ttu-id="8b388-109">4.5.1</span><span class="sxs-lookup"><span data-stu-id="8b388-109">4.5.1</span></span>|
|<span data-ttu-id="8b388-110">類型</span><span class="sxs-lookup"><span data-stu-id="8b388-110">Type</span></span>|<span data-ttu-id="8b388-111">執行階段</span><span class="sxs-lookup"><span data-stu-id="8b388-111">Runtime</span></span>|
