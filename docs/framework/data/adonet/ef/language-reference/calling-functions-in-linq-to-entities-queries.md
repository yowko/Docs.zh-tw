---
title: "在 LINQ to Entities 查詢中呼叫函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d7199c41f8bcf81340956b17f616bec76e534dcc
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="calling-functions-in-linq-to-entities-queries"></a>在 LINQ to Entities 查詢中呼叫函式
本章節的主題描述如何使用呼叫 LINQ to Entities 查詢中的函式。  
  
 <xref:System.Data.Objects.EntityFunctions> 與 <xref:System.Data.Objects.SqlClient.SqlFunctions> 類別可讓您存取標準函式與資料庫函式，這些函式是 Entity Framework 的一部分。 如需詳細資訊，請參閱[如何： 呼叫標準函式](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md)和[如何： 呼叫資料庫函式](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md)。  
  
 呼叫自訂函式的程序需要三個基本步驟：  
  
1.  定義概念模型中的函式或宣告儲存模型中的函式。  
  
2.  使用 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> 將方法加入至應用程式，並將它對應至模型中的函式。  
  
3.  呼叫 LINQ to Entities 查詢中的函式。  
  
 如需詳細資料，請參閱本節中的主題。  
  
## <a name="in-this-section"></a>本節內容  
 [如何：呼叫標準函式](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md)  
  
 [如何：呼叫資料庫函式](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md)  
  
 [如何：呼叫自訂資料庫函式](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-custom-database-functions.md)  
  
 [如何：在查詢中呼叫模型定義函式](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md)  
  
 [如何：將模型定義函式當作物件方法來呼叫](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a>請參閱  
 [LINQ to Entities 中的查詢](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 [標準函式](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)  
 [.edmx 檔案概觀](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [如何： 定義概念模型中的自訂函式](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f)
