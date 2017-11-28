---
title: "空間函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 935708457c3ebc8257b2495da36886468be1c706
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="spatial-functions"></a>空間函式
空間型別沒有任何常值格式。 不過，您可以使用標準 Entity Framework 函式 (使用 Well-Known Text 格式的字串所呼叫)。 例如，下列函式呼叫可建立幾何點：  
  
```  
GeometryFromText('POINT (43 -73)')  
```  
  
 [SpatialEdmFunctions 方法](http://msdn.microsoft.com/library/hh749531.aspx)頁面會列出所有空間標準 Entity Framework 方法。 按一下相關方法，以查看應將哪些參數傳遞至函式。
