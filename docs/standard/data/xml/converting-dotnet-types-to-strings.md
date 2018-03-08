---
title: "將 .NET Framework 型別轉換成字串"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6ca134e13593fdacd759b0000e0e159f76ea067f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
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
|DateTime|格式為 yyyy-MM-ddTHH:mm:sszzzzzz 及其子集。|  
|Timespan|格式為 PnYnMnTnHnMnS，例如 `P2Y10M15DT10H30M20S` 代表期間為 2 年 10 個月 15 天 10 小時 30 分鐘 20 秒。|  
  
## <a name="see-also"></a>請參閱  
 [XML 資料類型轉換](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 [將字串轉換成 .NET Framework 資料類型](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)
