---
title: LINQ to ADO.NET (入口網站頁面)
ms.date: 07/20/2015
ms.assetid: bbbd7c76-2981-4b91-b8d2-437547181f52
ms.openlocfilehash: 6e37a1ffdef3dd2299c2c534345ba7c6dc610471
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2018
ms.locfileid: "44367999"
---
# <a name="linq-to-adonet-portal-page"></a>LINQ to ADO.NET (入口網站頁面)
[!INCLUDE[linq_adonet](~/includes/linq-adonet-md.md)] 可讓您使用 [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] 程式設計模型，針對 [!INCLUDE[vstecado](~/includes/vstecado-md.md)] 中的任何可列舉物件進行查詢。  
  
> [!NOTE]
>  [!INCLUDE[linq_adonet](~/includes/linq-adonet-md.md)] 文件位於 .NET Framework SDK 的 ADO.NET 區段︰[LINQ 和 ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md)。
  
 有三種不同的 ADO.NET [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] 技術：[!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)]、[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 和 [!INCLUDE[linq_entities](~/includes/linq-entities-md.md)]。 [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)] 可提供更豐富且最佳化的 <xref:System.Data.DataSet> 查詢；[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 可讓您直接查詢 SQL Server 資料庫結構描述，而 [!INCLUDE[linq_entities](~/includes/linq-entities-md.md)] 可讓您查詢 [!INCLUDE[adonet_edm](~/includes/adonet-edm-md.md)]。  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 <xref:System.Data.DataSet> 是 [!INCLUDE[vstecado](~/includes/vstecado-md.md)] 中最廣為使用的其中一個元件，並為中斷連接的程式設計模型 ([!INCLUDE[vstecado](~/includes/vstecado-md.md)] 建置於其上) 的重要項目。 雖然 <xref:System.Data.DataSet> 具有上述優點，但是它的查詢功能仍然有限。  
  
 [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)] 可讓您藉由使用其他許多資料來源的相同查詢功能，將更為豐富的查詢功能建置在 <xref:System.Data.DataSet> 中。  
  
 如需詳細資訊，請參閱 [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)。  
  
## <a name="linq-to-sql"></a>LINQ to SQL  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 提供的執行階段基礎結構可以將關聯式資料當成物件來管理。 在 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 中，關聯式資料庫的資料模型會對應至以開發人員的程式設計語言表示的物件模型。 執行應用程式時，[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 會將物件模型中的 Language-integrated Query (LINQ) 轉譯成 SQL，並將這些查詢傳送至資料庫以便執行。 當資料庫傳回結果時，[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 會將結果轉譯回物件，方便您加以管理。  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 可支援資料庫的預存程序和使用者定義函式，以及物件模型中的繼承。  
  
 如需詳細資訊，請參閱 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)。  
  
## <a name="linq-to-entities"></a>LINQ to Entities  
 透過 [!INCLUDE[adonet_edm](~/includes/adonet-edm-md.md)]，關聯式資料會公開為 .NET 環境內的物件。 如此一來，物件層就成為理想的 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 支援目標，讓程式開發人員可以根據用於建置商務邏輯的語言，針對資料庫編寫查詢。 這項功能稱為 [!INCLUDE[linq_entities](~/includes/linq-entities-md.md)]。 如需詳細資訊，請參閱 [LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md)。  
  
## <a name="see-also"></a>另請參閱

- [LINQ 和 ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md)  
- [Language-Integrated Query (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)
