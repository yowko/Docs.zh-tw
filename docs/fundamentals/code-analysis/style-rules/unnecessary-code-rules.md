---
title: 不需要的程式碼規則
description: 瞭解程式碼分析不必要的程式碼規則
ms.date: 09/30/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 16c4ba0e4bee2388736bf9813a3e8290d8d4da32
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2020
ms.locfileid: "96586573"
---
# <a name="unnecessary-code-rules"></a>不需要的程式碼規則

不必要的程式碼規則會識別程式碼基底中不必要的不同部分，而且可以重構或移除。 存在不必要的程式碼表示下列其中一個問題：

- 可讀性：不必要地降低可讀性的程式碼。 例如， [IDE0001](ide0001.md) 會將不必要的類型名稱限定標記為旗標。
- 可維護性：重構之後不再使用的程式碼，而且不必要進行維護。 例如， [IDE0051](ide0051.md) 會旗標未使用的私用欄位、屬性、事件和方法。
- 效能：不必要的計算，不具副作用，導致不必要的效能額外負荷。 例如， [IDE0059](ide0059.md) 會旗標未使用的值指派，其中計算值的運算式沒有任何副作用。
- 功能：在程式碼中，會導致必要程式碼重複呈現的功能性問題。 例如， [IDE0060](ide0060.md) 會標記方法不小心忽略輸入參數的未使用參數。

本節中的規則會考慮下列不必要的程式碼規則：

- [簡化名稱 (IDE0001) ](ide0001.md)
- [簡化成員存取 (IDE0002) ](ide0002.md)
- [移除不必要的 cast (IDE0004) ](ide0004.md)
- [移除不必要的匯入 (IDE0005) ](ide0005.md)
- [ (IDE0035) 移除無法連線的程式碼 ](ide0035.md)
- [移除未使用的私用成員 (IDE0051) ](ide0051.md)
- [移除未讀取的私用成員 (IDE0052) ](ide0052.md)
- [移除未使用的運算式值 (IDE0058) ](ide0058.md)
- [移除不必要的值指派 (IDE0059) ](ide0059.md)
- [移除未使用的參數 (IDE0060) ](ide0060.md)
- [移除不必要的隱藏 (IDE0079) ](ide0079.md)
- [移除不必要的隱藏專案運算子 (IDE0080) ](ide0080.md) -僅限 c #。
- [移除 ' ByVal ' (IDE0081) ](ide0081.md) -僅 Visual Basic。
- [移除不必要的等號比較運算子 (IDE0100) ](ide0100.md)
- [移除不必要的捨棄 (IDE0110) ](ide0110.md) -僅限 c #。

其中有些規則具有設定規則行為的選項：

- [csharp_style_unused_value_expression_statement_preference (IDE0058) ](ide0058.md#csharp_style_unused_value_expression_statement_preference)
- [visual_basic_style_unused_value_expression_statement_preference (IDE0058) ](ide0058.md#visual_basic_style_unused_value_expression_statement_preference)
- [csharp_style_unused_value_assignment_preference (IDE0059) ](ide0059.md#csharp_style_unused_value_assignment_preference)
- [visual_basic_style_unused_value_assignment_preference (IDE0059) ](ide0059.md#visual_basic_style_unused_value_assignment_preference)
- [dotnet_code_quality_unused_parameters (IDE0060) ](ide0060.md#dotnet_code_quality_unused_parameters)
- [dotnet_remove_unnecessary_suppression_exclusions (IDE0079) ](ide0079.md#dotnet_remove_unnecessary_suppression_exclusions)

## <a name="see-also"></a>另請參閱

- [程式碼樣式語言規則](language-rules.md)
- [程式碼樣式規則參考](index.md)
