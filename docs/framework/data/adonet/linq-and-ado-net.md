---
title: LINQ 和 ADO.NET
ms.date: 03/30/2017
ms.assetid: bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec
ms.openlocfilehash: 16b06549573bc79378539cf7f5ccdcb60c812e81
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504463"
---
# <a name="linq-and-adonet"></a>LINQ 和 ADO.NET
現今許多商務程式開發人員必須使用兩個 （含） 以上的程式設計語言： 商務邏輯和展示層的高階語言 (例如視覺效果C#或 Visual Basic)，以及互動 （例如 Transact SQL) 資料庫的查詢語言. 因此，開發人員必須精通許多語言才能具有效率，而且也會在開發環境中產生語言不符的情況。 例如，使用資料存取 API 針對資料庫執行查詢的應用程式會使用引號，將查詢指定成字串常值 (String Literal)。 編譯器 (Compiler) 無法讀取這個查詢字串而且不會檢查是否有錯誤，例如語法無效或它所參考的資料行或資料列是否實際存在。 此外，系統無法提供查詢參數的型別檢查和 `IntelliSense` 支援。  
  
 [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] 可讓開發人員在其應用程式程式碼中撰寫以集合為基礎的查詢，而不需要使用不同的查詢語言。 您可以針對各種可列舉的資料來源 (亦即，實作 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 介面的資料來源) 撰寫 <xref:System.Collections.IEnumerable> 查詢，而這些資料來源包括記憶體中資料結構、XML 文件、SQL 資料庫和 <xref:System.Data.DataSet> 物件。 雖然這些可列舉的資料來源是以各種不同的方式實作，但是它們全部都會公開 (Expose) 相同的語法和語言建構。 由於您可以用程式語言本身來撰寫查詢，因此不需要使用另一種查詢語言，進而內嵌為編譯器無法了解或驗證的字串常值。 整合的程式設計語言中的查詢也可讓 Visual Studio 程式設計人員可以藉由提供編譯時期型別和語法檢查，可提高生產力和`IntelliSense`。 這些功能會減少查詢偵錯和錯誤修正的需要。  
  
 將資料從 SQL 資料表傳輸至記憶體中物件通常很費時而且容易產生錯誤。 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]實作由 LINQ to DataSet 提供者並[!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]來源將資料轉換成<xref:System.Collections.IEnumerable>為基礎的物件集合。 當您查詢和更新時，程式設計人員永遠會將資料視為 <xref:System.Collections.IEnumerable> 集合。 針對這些集合撰寫查詢可獲得完整的 `IntelliSense` 支援。  
  
 有三個不同的 ADO.NET[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]技術：LINQ to DataSet， [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]，和[!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)]。 LINQ to DataSet 可讓您提供更豐富且最佳化的查詢<xref:System.Data.DataSet>並[!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]可讓您直接查詢 SQL Server 資料庫結構描述，和[!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)]可讓您查詢實體資料模型。  
  
 下圖將提供 ADO.NET LINQ 技術如何與高階程式語言和啟用 LINQ 之資料來源相關聯的概觀。  
  
 ![LINQ to ADO.NET 概觀](../../../../docs/framework/data/adonet/media/dpue-linqtoadonetoverview-bpuedev11.gif "DPUE_LinqToAdoNetOverview_bpuedev11")  
  
 如需有關 LINQ 的詳細資訊，請參閱 < [Language Integrated Query (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md)。
  
 下列各節提供資料集，LINQ 的詳細資訊[!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]，和[!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)]。  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 <xref:System.Data.DataSet>是中斷連接程式設計模型，ADO.NET 為基礎，並廣泛使用的重要項目。 LINQ to DataSet 可讓開發人員建置更豐富的查詢功能<xref:System.Data.DataSet>使用適用於許多其他資料來源的相同查詢編寫機制。 如需詳細資訊，請參閱 [LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md)。  
  
## <a name="linq-to-sql"></a>LINQ to SQL  
 對於不需要對應至概念模型的開發人員而言，[!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] 是很有用的工具。 透過 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]，您就可以直接在現有的資料庫結構描述上使用 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 程式設計模型。 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] 可讓開發人員產生代表資料的.NET Framework 類別。 然後，這些產生的類別會直接對應至資料庫資料表、檢視、預存程序 (Stored Procedure) 和使用者定義函式，而非對應至概念性資料模型。  
  
 透過 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]，開發人員就可以使用與記憶體中集合和 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] (以及 XML 等其他資料來源) 相同的 <xref:System.Data.DataSet> 程式設計模式，直接針對儲存結構描述撰寫程式碼。 如需詳細資訊，請參閱 [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)。  
  
## <a name="linq-to-entities"></a>LINQ to Entities  
 目前大部分應用程式都是根據關聯式資料庫所撰寫而成。 同時，這些應用程式將必須與關聯式格式表示的資料互動。 但是，資料庫結構描述不一定適合建立應用程式，而且應用程式的概念模型與資料庫的邏輯模型有所不同。 實體資料模型是可用來針對特定定義域資料，讓應用程式可以與資料當做物件互動模型的概念資料模型。 請參閱[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)如需詳細資訊。  
  
 實體資料模型中，透過關聯式資料公開為.NET 環境中的物件。 如此一來，物件層就成為理想的 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 支援目標，讓程式開發人員可以根據用於建置商務邏輯的語言，針對資料庫編寫查詢。 這項功能稱為 [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)]。 如需詳細資訊，請參閱 [LINQ to Entities](../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)。  
  
## <a name="see-also"></a>另請參閱

- [LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md)
- [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)
- [LINQ to Entities](../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)
- [Language-Integrated Query (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md)
- [ADO.NET 概觀](ado-net-overview.md)
