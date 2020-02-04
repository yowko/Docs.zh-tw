---
title: LINQ 和 ADO.NET
titleSuffix: ''
ms.date: 03/30/2017
ms.assetid: bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec
ms.openlocfilehash: e24473f68fe5ccd993c5d205660ea8f397b6f797
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980089"
---
# <a name="linq-and-adonet"></a>LINQ 和 ADO.NET
現今，許多商務開發人員都必須使用兩個（或更多）程式設計語言：商務邏輯和展示層的高階語言（例如視覺C#效果或 Visual Basic），以及與資料庫互動的查詢語言（例如 transact-sql）。 因此，開發人員必須精通許多語言才能具有效率，而且也會在開發環境中產生語言不符的情況。 例如，使用資料存取 API 針對資料庫執行查詢的應用程式會使用引號，將查詢指定成字串常值 (String Literal)。 編譯器 (Compiler) 無法讀取這個查詢字串而且不會檢查是否有錯誤，例如語法無效或它所參考的資料行或資料列是否實際存在。 此外，系統無法提供查詢參數的型別檢查和 `IntelliSense` 支援。  
  
 語言整合式查詢（LINQ）可讓開發人員在其應用程式程式碼中形成以集合為基礎的查詢，而不需要使用不同的查詢語言。 您可以針對各種可列舉的資料來源（也就是執行 <xref:System.Collections.IEnumerable> 介面的資料來源）撰寫 LINQ 查詢，例如記憶體中的資料結構、XML 檔、SQL 資料庫和 <xref:System.Data.DataSet> 物件。 雖然這些可列舉的資料來源是以各種不同的方式實作，但是它們全部都會公開 (Expose) 相同的語法和語言建構。 由於您可以用程式語言本身來撰寫查詢，因此不需要使用另一種查詢語言，進而內嵌為編譯器無法了解或驗證的字串常值。 將查詢整合至程式設計語言也可以提供編譯時間型別和語法檢查，以及 `IntelliSense`，讓 Visual Studio 程式設計師更具生產力。 這些功能會減少查詢偵錯和錯誤修正的需要。  
  
 將資料從 SQL 資料表傳輸至記憶體中物件通常很費時而且容易產生錯誤。 LINQ to DataSet 和 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] 所實的 LINQ 提供者，會將來源資料轉換成 <xref:System.Collections.IEnumerable>的物件集合。 當您查詢和更新時，程式設計人員永遠會將資料視為 <xref:System.Collections.IEnumerable> 集合。 針對這些集合撰寫查詢可獲得完整的 `IntelliSense` 支援。  
  
 有三種不同的 ADO.NET 語言整合式查詢（LINQ）技術： LINQ to DataSet、[!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]和 LINQ to Entities。 LINQ to DataSet 提供更豐富且優化的 <xref:System.Data.DataSet> 查詢，[!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] 可讓您直接查詢 SQL Server 資料庫架構，而 LINQ to Entities 可讓您查詢實體資料模型。  
  
 下圖將提供 ADO.NET LINQ 技術如何與高階程式語言和啟用 LINQ 之資料來源相關聯的概觀。  
  
 ![LINQ to ADO.NET 總覽](./media/dpue-linqtoadonetoverview-bpuedev11.gif "DPUE_LinqToAdoNetOverview_bpuedev11")  
  
 如需 LINQ 的詳細資訊，請參閱[語言整合式查詢（LINQ）](../../../csharp/programming-guide/concepts/linq/index.md)。
  
 下列各節提供有關 LINQ to DataSet、[!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]和 LINQ to Entities 的詳細資訊。  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 <xref:System.Data.DataSet> 是已中斷連線之程式設計模型的關鍵元素，ADO.NET 是以其為基礎，並廣泛使用。 LINQ to DataSet 可讓開發人員使用適用于許多其他資料來源的相同查詢編寫機制，在 <xref:System.Data.DataSet> 中建立更豐富的查詢功能。 如需詳細資訊，請參閱 [LINQ to DataSet](linq-to-dataset.md)。  
  
## <a name="linq-to-sql"></a>LINQ to SQL  
 對於不需要對應至概念模型的開發人員而言，[!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] 是很有用的工具。 藉由使用 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]，您可以直接在現有的資料庫架構上使用 LINQ 程式設計模型。 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] enables developers to generate .NET Framework classes that represent data. 然後，這些產生的類別會直接對應至資料庫資料表、檢視、預存程序 (Stored Procedure) 和使用者定義函式，而非對應至概念性資料模型。  
  
 With [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], developers can write code directly against the storage schema using the same LINQ programming pattern as in-memory collections and the <xref:System.Data.DataSet>, in addition to other data sources such as XML. 如需詳細資訊，請參閱 [LINQ to SQL](./sql/linq/index.md)。  
  
## <a name="linq-to-entities"></a>LINQ to Entities  
 目前大部分應用程式都是根據關聯式資料庫所撰寫而成。 同時，這些應用程式將必須與關聯式格式表示的資料互動。 但是，資料庫結構描述不一定適合建立應用程式，而且應用程式的概念模型與資料庫的邏輯模型有所不同。 The Entity Data Model is a conceptual data model that can be used to model the data of a particular domain so that applications can interact with data as objects. See [ADO.NET Entity Framework](./ef/index.md) for more information.  
  
 透過實體資料模型，關聯式資料會公開為 .NET 環境內的物件。 This makes the object layer an ideal target for LINQ support, allowing developers to formulate queries against the database from the language used to build the business logic. 這項功能稱為 LINQ to Entities。 如需詳細資訊，請參閱 [LINQ to Entities](./ef/language-reference/linq-to-entities.md)。  
  
## <a name="see-also"></a>請參閱

- [LINQ to DataSet](linq-to-dataset.md)
- [LINQ to SQL](./sql/linq/index.md)
- [LINQ to Entities](./ef/language-reference/linq-to-entities.md)
- [Language-Integrated Query (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md)
- [ADO.NET 概觀](ado-net-overview.md)
