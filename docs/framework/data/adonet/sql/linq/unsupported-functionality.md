---
title: "不支援的功能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6dd8ccebd278fdc36c536c49f7f1d4262b2de8c1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="unsupported-functionality"></a>不支援的功能
在 LINQ to SQL 中，下列 SQL 功能無法透過轉譯現有 Common Language Runtime (CLR) 和 .NET Framework 建構來公開 (Expose)：  
  
-   `STDDEV`  
  
-   `LIKE`  
  
     雖然 `LIKE` 並非透過直接轉譯提供支援，但是類似的功能存在 <xref:System.Data.Linq.SqlClient.SqlMethods> 類別 (Class) 中。 如需詳細資訊，請參閱<xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>。  
  
-   `DATEDIFF`  
  
     LINQ to SQL 對於 `DATEDIFF` 的支援有限。 類似的功能存在 <xref:System.Data.Linq.SqlClient.SqlMethods> 類別中。  
  
-   `ROUND`  
  
     LINQ to SQL 對於 `ROUND` 的支援有限。 如需詳細資訊，請參閱[System.Math 方法](system-math-methods.md)。  
  
## <a name="see-also"></a>另請參閱  
 [資料型別和函式](data-types-and-functions.md)
