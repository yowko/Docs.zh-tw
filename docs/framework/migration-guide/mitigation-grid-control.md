---
title: "風險降低：方格控制項對 Star-columns 的空間配置 | Microsoft Docs"
ms.custom: 
ms.date: 04/07/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- Grid control retargeting changes
ms.assetid: 707c064d-85e9-4ea1-aefb-e42b60b88679
caps.latest.revision: 4
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9460c8b6ca8db927af4064e3567eca34c1bf5c91
ms.openlocfilehash: c7acce9d41af7e72b04b89751a7b186c9581dfea
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-grid-control39s-space-allocation-to-star-columns"></a>風險降低：方格控制項對 Star-columns 的空間配置

從以 .NET Framework 4.7 為目標的應用程式開始，WPF 取代了 <xref:System.Windows.Controls.Grid> 控制項用來配置 \*-columns 空間的演算法。 

## <a name="whats-changed"></a>已變更的內容

新的演算法修正了舊演算法中的數個錯誤：

1. 資料行的總配置可能會超過方格的寬度。 資料行的按比例共用若低於其大小下限，配置空間時就可能發生這個狀況。 此演算法會配置大小下限，因此，其他資料行的可用空間會減少。 如果沒有要配置的 \*-columns，總配置將會過大。

1. 總配置的方格寬度可能會不足。 這是第 1 點的雙重問題，在為資料行配置空間時，若其按比例共用超過大小上限，但缺少可使用剩餘空間的 \*-columns 時，就會發生這個狀況。

1. 兩個 \*-columns 的配置可能不是依其 -weights 按比例分配。 相較於第 1 點/第 2 點，這是程度較輕的錯誤，在為 *-columns A、B 和 C (依此順序) 配置空間時，若 B 的按比例共用違反其下限 (或上限) 條件約束，就會發生這個狀況。 如上所述，這會使資料行 C 的可用的空間產生變化，可能會獲得較 A 更少 (或更多) 的比例配置，

1. 權數極大 (> 10 ^298) 的資料行一律會視為擁有 10 ^298 的權數。 它們之間 (及權數較小的資料行之間) 的比例差異則可忽略。

1. 無法正確處理擁有無限權數的資料行。 [事實上，您無法將權數設為無限大，但這是人為限制。 配置程式碼會嘗試處理它，但成效不彰。]

1. 避免溢位、反向溢位時的幾個小問題、精確度失準及類似的浮點數問題。

1. 版面配置進位的調整在 DPI 足夠高的情況下不正確。

新的演算法會產生符合下列準則的結果︰

答： 指派給 *-column 的實際寬度永遠不會低於其寬度下限或高於其寬度上限。

B. 對於尚未指派寬度下限或上限的每個 -column，會依其 -weight 按比例指派寬度。 確切而言，若有兩個資料行分別使用寬度 x 和 y 宣告，而任一資料行均未配置其寬度下限和上限，則指派給資料行的實際寬度 v 和 w 所使用的比例相同：v / w == x / y。

C. 配置給 「按比例」\*-columns 的總寬度，等於配置給條件約束的資料行 (固定、自動及已配置寬度下限或上限的 \*-columns) 後的可用空間。 這可能是零，例如，若寬度下限的總和超過方格可用的寬度。

D. 以上所述是就「理想」的版面配置而言。 當版面配置進位作用中時，實際寬度與理想寬度最多會相差一個像素。

舊的演算法能實現 (A) 準則，卻無法實現上述狀況中的其他準則。

本主題中關於資料行與寬度的論述也適用於資料列與高度。

## <a name="impact"></a>影響

在以下幾種狀況下，新的演算法會使指派給 \*-columns 的實際寬度產生變化︰

- 當一或多個 \*-columns 也具有寬度下限或上限，因而會覆寫該資料行的按比例配置時。 (寬度下限可能衍生自明確的 <xref:System.Windows.FrameworkElement.MinWidth%2A> 宣告，或衍生自從資料行的內容取得的隱含下限。 寬度上限只能透過 <xref:System.Windows.FrameworkElement.MaxWidth%2A> 宣告明確地定義。)

- 當一或多個 \*-columns 宣告極大的 \*-weight 時 (大於 10^298)。

- 當 \*-weights 的差異足以發生浮點不穩定 (溢位、反向溢位、精確度失準) 時。

- 當版面配置進位已啟用，且有效顯示 DPI 夠高時。

在前兩個狀況中，新演算法產生的寬度可能明顯不同於舊演算法產生的寬度；在最後一個狀況中，差異最多會是一或兩個像素。

## <a name="mitigation"></a>緩和

根據預設，以 .NET Framework 4.7 開始的 .NET Framework 版本為目標的應用程式將使用新演算法，以 .NET Framework 4.6.2 或更舊版本為目標的應用程式將使用舊演算法。

若要覆寫預設值，請使用下列組態設定︰

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true" /> 
</runtime>
```

值 'true' 會選取舊的演算法，'false' 會選取新的演算法。

## <a name="see-also"></a>請參閱
[.NET Framework 4.7 中的重定目標變更](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)

