---
title: 將 .NET 類型轉換成字串
ms.date: 03/30/2017
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
ms.openlocfilehash: 9744224b4346b865a112b0eb6957f12553e1ec5f
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830983"
---
# <a name="convert-net-types-to-strings"></a>將 .NET 類型轉換成字串

如果您想要將 .NET 型別轉換成字串，請使用 **ToString** 方法。 **ToString** 方法會傳回所傳入之型別的字串表示。 下表列出的 .NET 型別會以對應至 XML 架構 (XSD) 規格的格式傳回字串。  
  
|.NET 類型|傳回的字串型別|  
|-------------------------|--------------------------|  
|布林值|"true"、"false"|  
|Single.PositiveInfinity|"INF"|  
|Single.NegativeInfinity|"-INF"|  
|Double.PositiveInfinity|"INF"|  
|Double.NegativeInfinity|"-INF"|  
|Datetime|格式為 yyyy-MM-ddTHH:mm:sszzzzzz 及其子集。|  
|Timespan|格式為 PnYnMnTnHnMnS，例如 `P2Y10M15DT10H30M20S` 代表期間為 2 年 10 個月 15 天 10 小時 30 分鐘 20 秒。|  
  
## <a name="see-also"></a>請參閱

- [XML 資料型別轉換](conversion-of-xml-data-types.md)
- [將字串轉換成 .NET 資料類型](converting-strings-to-dotnet-data-types.md)
