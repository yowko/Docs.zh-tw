---
title: "物件識別"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c788f2f9-65cc-4455-9907-e8388a268e00
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 97c07ce351de5b7939bdcaf441bc46dac50a8c23
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="object-identity"></a>物件識別
執行階段中的物件具有唯一的識別 (Identity)。 兩個參考相同物件的變數實際上是參考相同的物件執行個體。 因此，透過經過其中一個變數的路徑進行的變更，可以透過另一個變數立即看到。  
  
 關聯式資料庫資料表中的資料列並沒有唯一的識別。 因為每個資料列都會有唯一的主索引鍵，所以兩個資料列不會共用相同的索引鍵值。 不過，這只限於資料庫資料表的內容。  
  
 實際上，最常發生的狀況是從資料庫取出資料，接著將資料放入不同層級，而應用程式會在這些層級中處理資料。 這是 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 支援的模型。 從資料庫中取出資料並放入資料列時，代表相同資料的兩個資料列實際上並不會對應至相同的資料列執行個體。 如果查詢特定客戶兩次，便會有兩列資料。 而每個資料列會包含相同的資訊。  
  
 利用物件時，所進行的方式則相當不同。 如果重複向 <xref:System.Data.Linq.DataContext> 要求相同資訊，則實際上提供給您的會是相同的物件執行個體。 因為物件對您的應用程式有特殊意義，而您預期它們會像物件一樣作業，所以您預期會發生上述行為。 您已將它們設計為階層架構或圖形。 因為您多次要求相同的事項，所以希望以這類方式擷取它們，而不要接收已複寫執行個體的各個部分。  
  
 在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，<xref:System.Data.Linq.DataContext> 會管理物件識別。 只要從資料庫擷取新的資料列，就會根據該資料列的主索引鍵將該資料列記錄到識別表中，而且會建立新的物件。 每次擷取那個相同的資料列時，就會將原始物件執行個體交還給應用程式。 利用這種方式，<xref:System.Data.Linq.DataContext> 會將資料庫看到的識別概念 (即主索引鍵) 轉譯為語言看到的識別概念 (即執行個體)。 而應用程式只會看到物件在它第一次擷取物件時的狀態。 如果新資料的狀態不同則會予以捨棄。 如需詳細資訊，請參閱[擷取物件從識別快取](../../../../../../docs/framework/data/adonet/sql/linq/retrieving-objects-from-the-identity-cache.md)。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]您可以使用此方式來管理本機物件的完整性，以便支援開放式的更新。 因為只有在第一次建立物件之後發生的變更才是應用程式進行的變更，所以應用程式的意圖十分清楚。 如果外部群體在其間也進行了變更，則會在呼叫 `SubmitChanges()` 時識別這些變更。  
  
> [!NOTE]
>  如果查詢要求的物件可以輕易識別為已擷取的物件，則不會執行查詢。 識別表是當成所有先前擷取過物件的快取。  
  
## <a name="examples"></a>範例  
  
### <a name="object-caching-example-1"></a>物件快取範例 1  
 在這個範例中，如果執行相同的查詢兩次，則每次都會接收到記憶體中相同物件的參考。  
  
 [!code-csharp[DLinqObjectIdentity#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectIdentity/cs/Program.cs#1)]
 [!code-vb[DLinqObjectIdentity#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectIdentity/vb/Module1.vb#1)]  
  
### <a name="object-caching-example-2"></a>物件快取範例 2  
 在這個範例中，如果執行不同的查詢從資料庫中傳回相同的資料列，則每次都會接收到記憶體中相同物件的參考。  
  
 [!code-csharp[DLinqObjectIdentity#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectIdentity/cs/Program.cs#2)]
 [!code-vb[DLinqObjectIdentity#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectIdentity/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>另請參閱  
 [背景資訊](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
