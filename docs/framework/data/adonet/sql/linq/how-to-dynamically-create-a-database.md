---
title: HOW TO：動態建立資料庫
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb7f23c4-4572-4c38-9898-a287807d070c
ms.openlocfilehash: a73efb334fddc7e0bbfbaca53f0d5026105dd22c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597030"
---
# <a name="how-to-dynamically-create-a-database"></a>HOW TO：動態建立資料庫
在 LINQ to SQL 中，物件模型 (Object Model) 會對應至關聯式資料庫。 對應的啟用方式是使用以屬性 (Attribute) 為基礎的對應或外部對應檔案來描述關聯式資料庫的結構。 在這兩種情況中，系統會提供足夠的關聯式資料庫相關資訊，可讓您使用 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> 方法來建立新的資料庫執行個體 (Instance)。  
  
 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> 方法只會針對物件模型中所編碼的資訊範圍，建立資料庫的複本。 物件模型中的對應檔案和屬性可能不會編碼現有資料庫結構的所有項目。 對應資訊並不代表使用者定義函式、預存程序 (Stored Procedure)、觸發程序 (Trigger) 或檢查條件約束 (Check Constraint) 的內容。 這個行為對各種資料庫而言就已足夠。  
  
 您可以將 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> 方法用在許多情況下，特別是在已知的資料提供者 (Data Provider) (如 Microsoft SQL Server 2008) 可用時。 典型情況包括：  
  
-   建置應用程式，這個應用程式會自動將它自己安裝在客戶系統上。  
  
-   建置用戶端應用程式，這個用戶端應用程式需要本機資料庫來儲存它的離線狀態。  
  
 根據連接字串，您也可以使用 .mdf 檔案或目錄名稱來搭配使用 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> 方法與 SQL Server。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會使用連接字串來定義要建立的資料庫，以及要在其上建立資料庫的伺服器。  
  
> [!NOTE]
>  請盡可能使用 Windows 整合式安全性來連接至資料庫，如此連接字串就不需要使用密碼。  
  
## <a name="example"></a>範例  
 下列程式碼會提供如何建立名為 MyDVDs.mdf 之新資料庫的範例。  
  
 [!code-csharp[DLinqSubmittingChanges#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#5)]
 [!code-vb[DLinqSubmittingChanges#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#5)]  
  
## <a name="example"></a>範例  
 您可以使用物件模型來建立資料庫，步驟如下所示：  
  
 [!code-csharp[DLinqSubmittingChanges#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#6)]
 [!code-vb[DLinqSubmittingChanges#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#6)]  
  
## <a name="example"></a>範例  
 建置 (Build) 會自動在客戶系統上自行安裝的應用程式時，請查看資料庫是否已經存在，並在建立新的資料庫之前卸除現有的資料庫。 <xref:System.Data.Linq.DataContext> 類別 (Class) 會提供 <xref:System.Data.Linq.DataContext.DatabaseExists%2A> 和 <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> 方法來協助您進行此程序。  
  
 下列範例顯示可以使用這些方法來實作此方法的方式：  
  
 [!code-csharp[DLinqSubmittingChanges#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#7)]
 [!code-vb[DLinqSubmittingChanges#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#7)]  
  
## <a name="see-also"></a>另請參閱
- [以屬性為基礎的對應](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)
- [外部對應](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
- [SQL-CLR 類型對應](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
- [背景資訊](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [變更和提交資料](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
