---
title: '可攜性和互通性規則 (程式碼分析) '
description: 瞭解程式碼分析規則可攜性和互通性規則
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Portablityrules
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis rules, interoperability rules, portability rules
- portability rules
- warnings, portability
- interoperability rules
- warnings, interoperability
author: gewarren
ms.author: gewarren
ms.openlocfilehash: a20cd77e13c4a8b95633d129990667f0a8de3ee8
ms.sourcegitcommit: 2e4adc490c1d2a705a0592b295d606b10b9f51f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2020
ms.locfileid: "96585237"
---
# <a name="portability-and-interoperability-rules"></a><span data-ttu-id="8eda4-103">可攜性與互通性規則</span><span class="sxs-lookup"><span data-stu-id="8eda4-103">Portability and interoperability rules</span></span>

<span data-ttu-id="8eda4-104">可攜性規則支援跨不同平臺的可攜性。</span><span class="sxs-lookup"><span data-stu-id="8eda4-104">Portability rules support portability across different platforms.</span></span> <span data-ttu-id="8eda4-105">互通性規則支援與 COM 用戶端互動。</span><span class="sxs-lookup"><span data-stu-id="8eda4-105">Interoperability rules support interaction with COM clients.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="8eda4-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="8eda4-106">In this section</span></span>

| <span data-ttu-id="8eda4-107">規則</span><span class="sxs-lookup"><span data-stu-id="8eda4-107">Rule</span></span> | <span data-ttu-id="8eda4-108">描述</span><span class="sxs-lookup"><span data-stu-id="8eda4-108">Description</span></span> |
| - | - |
| [<span data-ttu-id="8eda4-109">CA1401： P/Invoke 不應該為可見的</span><span class="sxs-lookup"><span data-stu-id="8eda4-109">CA1401: P/Invokes should not be visible</span></span>](ca1401.md) | <span data-ttu-id="8eda4-110">公用類型中的公用或受保護方法具有 System.Runtime.InteropServices.Dll的 ImportAttribute 屬性 (也會由 Visual Basic) 中的 Declare 關鍵字來執行。</span><span class="sxs-lookup"><span data-stu-id="8eda4-110">A public or protected method in a public type has the System.Runtime.InteropServices.DllImportAttribute attribute (also implemented by the Declare keyword in Visual Basic).</span></span> <span data-ttu-id="8eda4-111">但不得公開 (Expose) 此類方法。</span><span class="sxs-lookup"><span data-stu-id="8eda4-111">Such methods should not be exposed.</span></span> |
| [<span data-ttu-id="8eda4-112">CA1416：驗證平台相容性</span><span class="sxs-lookup"><span data-stu-id="8eda4-112">CA1416: Validate platform compatibility</span></span>](ca1416.md) | <span data-ttu-id="8eda4-113">在元件上使用平臺相依的 Api，可讓程式碼無法在所有平臺上運作。</span><span class="sxs-lookup"><span data-stu-id="8eda4-113">Using platform-dependent APIs on a component makes the code no longer work across all platforms.</span></span> |
| [<span data-ttu-id="8eda4-114">CA1417：不使用 `OutAttribute` P/invoke 的字串參數</span><span class="sxs-lookup"><span data-stu-id="8eda4-114">CA1417: Do not use `OutAttribute` on string parameters for P/Invokes</span></span>](ca1417.md) | <span data-ttu-id="8eda4-115">以傳值方式傳遞的字串參數， `OutAttribute` 會在字串為暫存字串時，使執行時間不穩定。</span><span class="sxs-lookup"><span data-stu-id="8eda4-115">String parameters passed by value with the `OutAttribute` can destabilize the runtime if the string is an interned string.</span></span> |
