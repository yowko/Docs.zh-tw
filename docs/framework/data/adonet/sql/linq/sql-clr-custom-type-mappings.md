---
title: SQL-CLR 自訂類型對應
ms.date: 03/30/2017
ms.assetid: d916c7fb-4b56-4214-acbe-5e23365047b2
ms.openlocfilehash: bc92d54cad6a977268ef3f000c684d5f195a933d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59140409"
---
# <a name="sql-clr-custom-type-mappings"></a>SQL-CLR 自訂類型對應
當您使用 SQLMetal 命令列工具或物件關聯式設計工具 (O/R 設計工具) 時，系統就會自動指定 SQL Server 與 Common Language Runtime (CLR) 之間的型別對應。  
  
 執行任何自訂的對應時，這些工具指派預設的型別對應中所述[SQL-CLR 類型對應](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)。 如果您想要建立與這些預設值不同的型別對應，就必須進行一些型別對應的自訂作業。  
  
 自訂型別對應時，建議的方法是在中繼 DBML 檔案中進行這些變更。 然後，當您使用 SQLMetal 或 O/R 設計工具來建立程式碼和對應檔案時，就應該使用自訂的 DBML 檔案。  
  
 一旦您從程式碼和對應檔案具現化 <xref:System.Data.Linq.DataContext> 物件之後，<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> 方法就會根據指定的型別對應來建立資料庫。 如果對應中沒有指定任何 CLR `type` 屬性，就會使用預設的型別對應。  
  
## <a name="customization-with-sqlmetal-or-or-designer"></a>使用 SQLMetal 或 O/R 設計工具進行自訂  
 透過 SQLMetal 和 O/R 設計工具，您就可以自動建立在程式碼檔案內部或外部包含型別對應資訊的物件模型 (Object Model)。 由於這些檔案會由 SQLMetal 或 O/R 設計工具所覆寫，所以每次您重新建立對應時，指定自訂型別對應的建議方法是自訂 DBML 檔案。  
  
 若要使用 SQLMetal 或 O/R 設計工具來自訂型別對應，請先產生 DBML 檔案。 然後，在產生程式碼檔案或對應檔案之前，修改 DBML 檔案，以便識別所需的型別對應。 您必須透過 SQLMetal 來手動變更 DBML 檔案中的 `Type` 和 `DbType` 屬性，以便進行型別對應自訂作業。 使用 O/R 設計工具時，您可以在此設計工具內部進行變更。 如需使用 O/R 設計工具的詳細資訊，請參閱[LINQ to SQL 工具，在 Visual Studio 中](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)。  
  
> [!NOTE]
>  在資料庫之間來回轉譯時，某些型別對應可能會造成溢位或資料遺失的例外狀況 (Exception)。 請仔細檢閱 在型別對應的執行階段行為對照表[SQL-CLR 類型對應](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)再進行任何自訂項目。  
  
 為了讓 SQLMetal 或 O/R 設計工具能夠辨識型別對應自訂項目，在產生程式碼檔案或外部對應檔案時，您必須確定這些工具提供在自訂 DBML 檔案的路徑中。 雖然不是型別對應項目所需的作業，不過建議您一定要分隔型別對應資訊與程式碼檔案，並且產生其他外部型別對應檔案。 這樣做將會保留一些彈性，讓您不需要重新編譯程式碼檔案。  
  
## <a name="incorporating-database-changes"></a>合併資料庫變更  
 當資料庫變更時，您必須更新 DBML 檔案來反映這些變更。 其中一種更新方式是自動建立新的 DBML 檔案，然後重新進行型別對應自訂作業。 或者，您可以比較新 DBML 檔案與自訂 DBML 檔案之間的差異，然後手動更新自訂 DBML 檔案來反映資料庫變更。  
  
## <a name="see-also"></a>另請參閱

- [SQL-CLR 類型對應](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
- [LINQ to SQL 中的程式碼產生](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
