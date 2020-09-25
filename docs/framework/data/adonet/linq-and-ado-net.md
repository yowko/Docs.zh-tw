---
title: LINQ 和 ADO.NET
description: 瞭解如何在 ADO.NET 中使用語言整合式查詢 (LINQ) ，以在應用程式程式碼中形成以集合為基礎的查詢，而不需要使用不同的查詢語言。
titleSuffix: ''
ms.date: 03/30/2017
ms.assetid: bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec
ms.openlocfilehash: 50e048a67d4a9bf62b2224664acb654b96da0cb7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194683"
---
# <a name="linq-and-adonet"></a>LINQ 和 ADO.NET

現今許多商務開發人員都必須使用兩個 (或更) 的程式設計語言：適用于商務邏輯和展示層的高階語言 (例如 Visual c # 或 Visual Basic) ，以及用來與資料庫 (互動的查詢語言，例如 Transact-sql) 。 因此，開發人員必須精通許多語言才能具有效率，而且也會在開發環境中產生語言不符的情況。 例如，使用資料存取 API 針對資料庫執行查詢的應用程式會使用引號，將查詢指定成字串常值 (String Literal)。 編譯器無法讀取此查詢字串，因此不會檢查是否有錯誤，例如語法無效或它所參考的資料行或資料列是否實際存在。 此外，系統無法提供查詢參數的型別檢查和 `IntelliSense` 支援。  
  
  (LINQ) 的語言整合式查詢可讓開發人員在其應用程式程式碼中形成以集合為基礎的查詢，而不需要使用不同的查詢語言。 您可以針對各種可列舉的資料來源撰寫 LINQ 查詢 (也就是可執行介面) 的資料來源 <xref:System.Collections.IEnumerable> ，例如記憶體內部資料結構、XML 檔、SQL 資料庫和 <xref:System.Data.DataSet> 物件。 雖然這些可列舉的資料來源是以各種不同的方式實作，但是它們全部都會公開 (Expose) 相同的語法和語言建構。 由於您可以用程式語言本身來撰寫查詢，因此不需要使用另一種查詢語言，進而內嵌為編譯器無法了解或驗證的字串常值。 將查詢整合至程式設計語言也可讓 Visual Studio 程式設計人員藉由提供編譯時間類型和語法檢查，以及來提高生產力 `IntelliSense` 。 這些功能會減少查詢偵錯和錯誤修正的需要。  
  
 將資料從 SQL 資料表傳輸至記憶體中物件通常很費時而且容易產生錯誤。 由 LINQ to DataSet 所執行的 LINQ 提供者，會 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] 將來源資料轉換為 <xref:System.Collections.IEnumerable> 基礎的物件集合。 當您查詢和更新時，程式設計人員永遠會將資料視為 <xref:System.Collections.IEnumerable> 集合。 針對這些集合撰寫查詢可獲得完整的 `IntelliSense` 支援。  
  
  (LINQ) 技術有三種不同的 ADO.NET 語言整合查詢： LINQ to DataSet、 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] 和 LINQ to Entities。 LINQ to DataSet 提供更豐富且優化的查詢， <xref:System.Data.DataSet> 並可 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] 讓您直接查詢 SQL Server 的資料庫架構，而 LINQ to Entities 則可讓您查詢實體資料模型。  
  
 下圖將提供 ADO.NET LINQ 技術如何與高階程式語言和啟用 LINQ 之資料來源相關聯的概觀。  
  
 ![LINQ to ADO.NET 概觀](./media/dpue-linqtoadonetoverview-bpuedev11.gif "DPUE_LinqToAdoNetOverview_bpuedev11")  
  
 如需 LINQ 的詳細資訊，請參閱 [ (linq) 的語言整合查詢 ](../../../csharp/programming-guide/concepts/linq/index.md)。
  
 下列各節提供有關 LINQ to DataSet、和 LINQ to Entities 的詳細資訊 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] 。  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  

 是已中斷連線之 <xref:System.Data.DataSet> 程式設計模型的重要元素，ADO.NET 是以其為基礎建立的，且已廣泛使用。 LINQ to DataSet 可讓開發人員 <xref:System.Data.DataSet> 使用適用于許多其他資料來源的相同查詢編寫機制，在中建立更豐富的查詢功能。 如需詳細資訊，請參閱 [LINQ to DataSet](linq-to-dataset.md)。  
  
## <a name="linq-to-sql"></a>LINQ to SQL  

 對於不需要對應至概念模型的開發人員而言，[!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] 是很有用的工具。 藉由使用 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] ，您可以直接在現有的資料庫架構上使用 LINQ 程式設計模型。 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] 可讓開發人員產生代表資料的 .NET Framework 類別。 然後，這些產生的類別會直接對應至資料庫資料表、檢視、預存程序 (Stored Procedure) 和使用者定義函式，而非對應至概念性資料模型。  
  
 使用時 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] ，開發人員可以使用與記憶體中集合和 <xref:System.Data.DataSet> 以外的其他資料來源（例如 XML）相同的 LINQ 程式設計模式，直接針對儲存架構撰寫程式碼。 如需詳細資訊，請參閱 [LINQ to SQL](./sql/linq/index.md)。  
  
## <a name="linq-to-entities"></a>LINQ to Entities  

 目前大部分應用程式都是根據關聯式資料庫所撰寫而成。 同時，這些應用程式將必須與關聯式格式表示的資料互動。 但是，資料庫結構描述不一定適合建立應用程式，而且應用程式的概念模型與資料庫的邏輯模型有所不同。 實體資料模型是可用來建立特定定義域資料模型的概念資料模型，讓應用程式可以與資料做為物件互動。 如需詳細資訊，請參閱 [ADO.NET Entity Framework](./ef/index.md)。  
  
 透過實體資料模型，關聯式資料會公開為 .NET 環境內的物件。 這讓物件層成為 LINQ 支援的理想目標，讓開發人員能夠根據用來建立商務邏輯的語言，為資料庫制訂查詢。 這項功能稱為 LINQ to Entities。 如需詳細資訊，請參閱 [LINQ to Entities](./ef/language-reference/linq-to-entities.md)。  
  
## <a name="see-also"></a>另請參閱

- [LINQ to DataSet](linq-to-dataset.md)
- [LINQ to SQL](./sql/linq/index.md)
- [LINQ to Entities](./ef/language-reference/linq-to-entities.md)
- [Language Integrated Query (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md)
- [ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)
