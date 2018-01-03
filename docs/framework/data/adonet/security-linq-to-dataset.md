---
title: "安全性 (LINQ to DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6116b2b8-75f4-4d8b-aea6-c13e55cda50b
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 2f67ad1947d421a5221a34ad8392242e4d18039f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="security-linq-to-dataset"></a>安全性 (LINQ to DataSet)
本主題討論 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 中的安全性問題。  
  
## <a name="passing-a-query-to-an-untrusted-component"></a>將查詢傳遞到不受信任的元件  
 A[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]查詢可以在程式的一個點位置編寫，並在另一個執行。 在編寫查詢的位置，查詢可以參考顯示在該位置的任何項目，例如，呼叫方法所屬類別的私用成員，或代表區域變數/引數的符號。 在執行時間，即使呼叫程式碼沒有顯示出來，此查詢還是可以有效地存取查詢在編寫時參考的成員。 執行查詢的程式碼沒有任意增加的可見性，因為它無法選擇要存取的成員。 它將可以精確地存取查詢所存取的成員，而且僅透過查詢本身進行存取。  
  
 這暗示：藉由將查詢的參考傳遞到程式碼的其他片段，收到查詢的元件就會受到信任，可以存取該查詢所參考的所有公用和私用成員。 一般情況下，[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]查詢不會傳遞至不受信任的元件，除非查詢已經仔細建構，因此不會暴露應該保密的資訊。  
  
## <a name="external-input"></a>外部輸入  
 應用程式通常採用外部輸入 (從使用者或其他外部代理程式)，並根據該輸入執行動作。  如果是[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]，應用程式可能會建構以特定方式，根據外部輸入或使用外部查詢中輸入查詢。 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 查詢會在可接受常值 (Literal) 的任何位置接受參數。 應用程式開發人員應該使用參數化的查詢，而非將常值從外部代理程式直接插入到查詢中。  
  
 從使用者或外部代理程式直接或間接衍生的任何輸入都可能具備運用目標語言之語法的內容，藉以執行未經授權的動作。 這是所謂的 SQL 插入式攻擊，這是以目標語言為 Transact-SQL 的攻擊模式來命名的。 直接插入到查詢的使用者輸入用於卸除資料庫資料表、造成阻絕服務，或變更要執行之作業的本質。 雖然可以在 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 中撰寫查詢，不過這項作業實際上是透過物件模型 API 執行的。 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]查詢不是由在 TRANSACT-SQL 中並不容易受到 SQL 插入式攻擊，在傳統意義上，使用字串操作或串連組成。  
  
## <a name="see-also"></a>請參閱  
 [程式設計手冊](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
