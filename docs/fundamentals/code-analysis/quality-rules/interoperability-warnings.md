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
# <a name="portability-and-interoperability-rules"></a>可攜性與互通性規則

可攜性規則支援跨不同平臺的可攜性。 互通性規則支援與 COM 用戶端互動。

## <a name="in-this-section"></a>本節內容

| 規則 | 描述 |
| - | - |
| [CA1401： P/Invoke 不應該為可見的](ca1401.md) | 公用類型中的公用或受保護方法具有 System.Runtime.InteropServices.Dll的 ImportAttribute 屬性 (也會由 Visual Basic) 中的 Declare 關鍵字來執行。 但不得公開 (Expose) 此類方法。 |
| [CA1416：驗證平台相容性](ca1416.md) | 在元件上使用平臺相依的 Api，可讓程式碼無法在所有平臺上運作。 |
| [CA1417：不使用 `OutAttribute` P/invoke 的字串參數](ca1417.md) | 以傳值方式傳遞的字串參數， `OutAttribute` 會在字串為暫存字串時，使執行時間不穩定。 |
