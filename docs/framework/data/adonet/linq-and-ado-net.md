---
title: "LINQ 和 ADO.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec
caps.latest.revision: "8"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b020b3df627fcb220f4227d76fdf8eb3d60e80e4
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="linq-and-adonet"></a>LINQ 和 ADO.NET
現今許多商務程式開發人員必須使用兩種 (或多種) 程式語言：適用於商務邏輯層與展示層的高階語言 (例如 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 或 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)])，以及與資料庫互動的查詢語言 (例如 [!INCLUDE[tsql](../../../../includes/tsql-md.md)])。 因此，開發人員必須精通許多語言才能具有效率，而且也會在開發環境中產生語言不符的情況。 例如，使用資料存取 API 針對資料庫執行查詢的應用程式會使用引號，將查詢指定成字串常值 (String Literal)。 編譯器 (Compiler) 無法讀取這個查詢字串而且不會檢查是否有錯誤，例如語法無效或它所參考的資料行或資料列是否實際存在。 此外，系統無法提供查詢參數的型別檢查和 `IntelliSense` 支援。  
  
 [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] 可讓開發人員在其應用程式程式碼中撰寫以集合為基礎的查詢，而不需要使用不同的查詢語言。 您可以針對各種可列舉的資料來源 (亦即，實作 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 介面的資料來源) 撰寫 <xref:System.Collections.IEnumerable> 查詢，而這些資料來源包括記憶體中資料結構、XML 文件、SQL 資料庫和 <xref:System.Data.DataSet> 物件。 雖然這些可列舉的資料來源是以各種不同的方式實作，但是它們全部都會公開 (Expose) 相同的語法和語言建構。 由於您可以用程式語言本身來撰寫查詢，因此不需要使用另一種查詢語言，進而內嵌為編譯器無法了解或驗證的字串常值。 此外，將查詢整合至程式語言也會透過提供編譯時期型別和語法檢查以及 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]，提升 `IntelliSense` 程式設計人員的產能。 這些功能會減少查詢偵錯和錯誤修正的需要。  
  
 將資料從 SQL 資料表傳輸至記憶體中物件通常很費時而且容易產生錯誤。 由 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 和 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 所實作的 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] 提供者會將來源資料轉換成以 <xref:System.Collections.IEnumerable> 為基礎的物件集合。 當您查詢和更新時，程式設計人員永遠會將資料視為 <xref:System.Collections.IEnumerable> 集合。 針對這些集合撰寫查詢可獲得完整的 `IntelliSense` 支援。  
  
 有三種不同的 ADO.NET [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] 技術：[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]、[!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] 和 [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)]。 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 會提供更豐富且最佳化的 <xref:System.Data.DataSet> 查詢、[!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] 可讓您直接查詢 [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] 資料庫結構描述 (Database Schema)，而 [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)] 可讓您查詢 [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)]。  
  
 下圖將提供 ADO.NET LINQ 技術如何與高階程式語言和啟用 LINQ 之資料來源相關聯的概觀。  
  
 ![LINQ to ADO.NET 概觀](../../../../docs/framework/data/adonet/media/dpue-linqtoadonetoverview-bpuedev11.gif "DPUE_LinqToAdoNetOverview_bpuedev11")  
  
 如需 LINQ 語言功能的一般資訊，請參閱[LINQ 簡介](http://msdn.microsoft.com/library/24dddf19-12a0-4707-a4bc-eba4fa7f219e)。 在您的應用程式中使用 LINQ 相關資訊，請參閱[不在組建中： LINQ 的一般程式設計指南](http://msdn.microsoft.com/library/609c7a6b-cbdd-429d-99f3-78d13d3bc049)，其中包含詳細說明如何使用 LINQ 技術的相關資訊。  
  
 下列各節將提供有關 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]、[!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] 和 [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)] 的詳細資訊。  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 <xref:System.Data.DataSet> 是用來建立 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 之中斷連接程式設計模型的重要項目，而且廣為業界所使用。 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 可讓開發人員使用適用於許多其他資料來源的相同查詢編寫機制，在 <xref:System.Data.DataSet> 中建立更豐富的查詢功能。 如需詳細資訊，請參閱 [LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md)。  
  
## <a name="linq-to-sql"></a>LINQ to SQL  
 對於不需要對應至概念模型的開發人員而言，[!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] 是很有用的工具。 透過 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]，您就可以直接在現有的資料庫結構描述上使用 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 程式設計模型。 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] 可讓開發人員產生代表資料的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 類別。 然後，這些產生的類別會直接對應至資料庫資料表、檢視、預存程序 (Stored Procedure) 和使用者定義函式，而非對應至概念性資料模型。  
  
 透過 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]，開發人員就可以使用與記憶體中集合和 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] (以及 XML 等其他資料來源) 相同的 <xref:System.Data.DataSet> 程式設計模式，直接針對儲存結構描述撰寫程式碼。 如需詳細資訊，請參閱 [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)。  
  
## <a name="linq-to-entities"></a>LINQ to Entities  
 目前大部分應用程式都是根據關聯式資料庫所撰寫而成。 同時，這些應用程式將必須與關聯式格式表示的資料互動。 但是，資料庫結構描述不一定適合建立應用程式，而且應用程式的概念模型與資料庫的邏輯模型有所不同。 [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] 是可用於針對特定定義域資料建立模型的概念資料模型，讓應用程式能夠將資料當做物件進行互動。 請參閱[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)如需詳細資訊。  
  
 透過 [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)]，關聯式資料會公開為 .NET 環境內的物件。 如此一來，物件層就成為理想的 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 支援目標，讓程式開發人員可以根據用於建置商務邏輯的語言，針對資料庫編寫查詢。 這項功能稱為 [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)]。 如需詳細資訊，請參閱 [LINQ to Entities](../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)。  
  
## <a name="see-also"></a>請參閱  
 [LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md)  
 [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)  
 [LINQ to Entities](../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)  
 [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
