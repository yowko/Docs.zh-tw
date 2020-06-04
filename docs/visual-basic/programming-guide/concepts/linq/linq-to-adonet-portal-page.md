---
title: LINQ to ADO.NET (入口網站頁面)
ms.date: 07/20/2015
ms.assetid: bbbd7c76-2981-4b91-b8d2-437547181f52
ms.openlocfilehash: 8c90783b56d6393ce3ac71945ed8ebffc8005ee1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84369176"
---
# <a name="linq-to-adonet-portal-page"></a>LINQ to ADO.NET (入口網站頁面)
LINQ to ADO.NET 可讓您使用語言整合式查詢（LINQ）程式設計模型，在 ADO.NET 中查詢任何可列舉物件。  
  
> [!NOTE]
> LINQ to ADO.NET 檔位於 .NET Framework SDK 的 ADO.NET 區段： [LINQ 和 ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md)。
  
 有三種不同的 ADO.NET 語言整合式查詢（LINQ）技術： LINQ to DataSet、 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 和 LINQ to Entities。 LINQ to DataSet 可提供更豐富且最佳化的 <xref:System.Data.DataSet> 查詢，[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 可讓您直接查詢 SQL Server 資料庫結構描述，而 LINQ to Entities 可讓您查詢實體資料模型。  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 <xref:System.Data.DataSet> 是 ADO.NET 中最廣為使用的元件之一，也是中斷連線程式設計模型 (ADO.NET 建置於其上) 的重要元素。 雖然 <xref:System.Data.DataSet> 具有上述優點，但是它的查詢功能仍然有限。  
  
 LINQ to DataSet 可讓您使用許多其他資料來源適用的相同查詢功能，將更為豐富的查詢功能建置在 <xref:System.Data.DataSet> 中。  
  
 如需詳細資訊，請參閱 [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)。  
  
## <a name="linq-to-sql"></a>LINQ to SQL  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 提供的執行階段基礎結構可以將關聯式資料當成物件來管理。 在 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 中，關聯式資料庫的資料模型會對應至以開發人員的程式設計語言表示的物件模型。 執行應用程式時，[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 會將物件模型中的 Language-integrated Query (LINQ) 轉譯成 SQL，並將這些查詢傳送至資料庫以便執行。 當資料庫傳回結果時，[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 會將結果轉譯回物件，方便您加以管理。  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 可支援資料庫的預存程序和使用者定義函式，以及物件模型中的繼承。  
  
 如需詳細資訊，請參閱 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)。  
  
## <a name="linq-to-entities"></a>LINQ to Entities  
 透過實體資料模型，關聯式資料會公開為 .NET 環境內的物件。 這讓物件層成為 LINQ 支援的理想目標，讓開發人員能夠根據用來建立商務邏輯的語言，為資料庫制訂查詢。 這項功能稱為 LINQ to Entities。 如需詳細資訊，請參閱 [LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md)。  
  
## <a name="see-also"></a>另請參閱

- [LINQ 和 ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md)
- [Language-Integrated Query (LINQ) (Visual Basic)](index.md)
