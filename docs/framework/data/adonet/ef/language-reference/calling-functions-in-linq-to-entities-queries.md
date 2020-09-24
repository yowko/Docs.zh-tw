---
title: 在 LINQ to Entities 查詢中呼叫函式
description: 使用這些文章來查看 EntityFunctions 和 SqlFunctions 類別如何提供標準和資料庫函式的存取權，做為 Entity Framework 的一部分。
ms.date: 03/30/2017
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
ms.openlocfilehash: 8c771c93e0c3ed82f3ad550613dd855fd06b6f48
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177484"
---
# <a name="calling-functions-in-linq-to-entities-queries"></a>在 LINQ to Entities 查詢中呼叫函式

本章節的主題描述如何使用呼叫 LINQ to Entities 查詢中的函式。  
  
 <xref:System.Data.Objects.EntityFunctions> 與 <xref:System.Data.Objects.SqlClient.SqlFunctions> 類別可讓您存取標準函式與資料庫函式，這些函式是 Entity Framework 的一部分。 如需詳細資訊，請參閱 [如何：呼叫標準](how-to-call-canonical-functions.md) 函式和 [如何：呼叫資料庫](how-to-call-database-functions.md)函式。  
  
 呼叫自訂函式的程序需要三個基本步驟：  
  
1. 定義概念模型中的函式或宣告儲存模型中的函式。  
  
2. 使用 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> 將方法加入至應用程式，並將它對應至模型中的函式。  
  
3. 呼叫 LINQ to Entities 查詢中的函式。  
  
 如需詳細資料，請參閱本節中的主題。  
  
## <a name="in-this-section"></a>本節內容  

 [如何：呼叫標準函式](how-to-call-canonical-functions.md)  
  
 [如何：呼叫資料庫函式](how-to-call-database-functions.md)  
  
 [如何：呼叫自訂資料庫函式](how-to-call-custom-database-functions.md)  
  
 [如何：在查詢中呼叫模型定義函式](how-to-call-model-defined-functions-in-queries.md)  
  
 [如何：將模型定義函式當做物件方法來呼叫](how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a>另請參閱

- [LINQ to Entities 中的查詢](queries-in-linq-to-entities.md)
- [標準函式](canonical-functions.md)
- [.edmx 檔概觀](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [HOW TO：在概念模型中定義自訂函式](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))
