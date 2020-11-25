---
title: 命名參數
description: 瞭解參數命名的指導方針。 例如，使用描述性參數名稱 & camel 大小寫，& 考慮根據意義而非類型來命名。
ms.date: 10/22/2008
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
ms.openlocfilehash: 9f03eda511c2ef0c9565d270c52fd72bf54692d8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698347"
---
# <a name="naming-parameters"></a>命名參數

除了可讀性的明顯原因之外，請務必遵循參數名稱的指導方針，因為當視覺化設計工具提供 Intellisense 和類別流覽功能時，參數會顯示在檔和設計工具中。

 ✔️在參數名稱中使用 >camelcasing。

 ✔️請使用描述性參數名稱。

 ✔️考慮依據參數的意義（而非參數的類型）來使用名稱。

### <a name="naming-operator-overload-parameters"></a>命名運算子多載參數

 `left`如果沒有任何意義的參數，✔️請使用和 `right` for 二元運算子多載參數名稱。

 `value`如果沒有任何意義的參數，✔️請使用一元運算子多載參數名稱。

 ✔️針對運算子多載參數考慮有意義的名稱，如果這樣做會增加重要的值。

 ❌ 請勿針對運算子多載參數名稱使用縮寫或數位索引。

 *部分©2005、2009 Microsoft Corporation。保留的擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>另請參閱

- [架構設計指導方針](index.md)
- [命名指導方針](naming-guidelines.md)
