---
title: 將 .NET Framework 型別轉換成字串
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
ms.openlocfilehash: d232fb0e3ea4cf3189294d6e6f43ae9270417407
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287814"
---
# <a name="converting-net-framework-types-to-strings"></a>將 .NET Framework 型別轉換成字串
若要將 .NET Framework 型別轉換成字串，請使用 **ToString** 方法。 **ToString** 方法會傳回所傳入之型別的字串表示。 下表將列出 .NET Framework 型別，其所傳回的字串格式會對應至 XML 結構描述 (XSD) 規格。  
  
|.NET Framework 類型|傳回的字串型別|  
|-------------------------|--------------------------|  
|Boolean|"true"、"false"|  
|Single.PositiveInfinity|"INF"|  
|Single.NegativeInfinity|"-INF"|  
|Double.PositiveInfinity|"INF"|  
|Double.NegativeInfinity|"-INF"|  
|Datetime|格式為 yyyy-MM-ddTHH:mm:sszzzzzz 及其子集。|  
|Timespan|格式為 PnYnMnTnHnMnS，例如 `P2Y10M15DT10H30M20S` 代表期間為 2 年 10 個月 15 天 10 小時 30 分鐘 20 秒。|  
  
## <a name="see-also"></a>另請參閱

- [XML 資料型別轉換](conversion-of-xml-data-types.md)
- [將字串轉換成 .NET Framework 資料型別](converting-strings-to-dotnet-data-types.md)
