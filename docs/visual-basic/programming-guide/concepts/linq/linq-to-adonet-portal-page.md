---
title: LINQ to ADO.NET (入口網站頁面)
ms.date: 07/20/2015
ms.assetid: bbbd7c76-2981-4b91-b8d2-437547181f52
ms.openlocfilehash: 850e154b40e69cc655ee1b59161351b0b2898033
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539377"
---
# <a name="linq-to-adonet-portal-page"></a>LINQ to ADO.NET (入口網站頁面)
LINQ to ADO.NET 可讓您藉由查詢任何可列舉的物件，在 ADO.NET 中[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]程式設計模型。  
  
> [!NOTE]
>  LINQ to ADO.NET 文件位於.NET Framework SDK 的 ADO.NET 區段：[LINQ 和 ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md)。
  
 有三個不同的 ADO.NET[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]技術：LINQ to DataSet， [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]，與 LINQ to Entities。 LINQ to DataSet 可讓您提供更豐富且最佳化的查詢<xref:System.Data.DataSet>，[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]可讓您直接查詢 SQL Server 資料庫結構描述，與 LINQ to Entities 可讓您查詢實體資料模型。  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 <xref:System.Data.DataSet> 是 ADO.NET 中最廣為使用的元件之一，也是中斷連線程式設計模型 (ADO.NET 建置於其上) 的重要元素。 雖然 <xref:System.Data.DataSet> 具有上述優點，但是它的查詢功能仍然有限。  
  
 LINQ to DataSet 可讓您更豐富查詢功能建置在<xref:System.Data.DataSet>藉由使用適用於許多其他資料來源的相同查詢功能。  
  
 如需詳細資訊，請參閱 [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)。  
  
## <a name="linq-to-sql"></a>LINQ to SQL  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 提供的執行階段基礎結構可以將關聯式資料當成物件來管理。 在 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 中，關聯式資料庫的資料模型會對應至以開發人員的程式設計語言表示的物件模型。 執行應用程式時，[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 會將物件模型中的 Language-integrated Query (LINQ) 轉譯成 SQL，並將這些查詢傳送至資料庫以便執行。 當資料庫傳回結果時，[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 會將結果轉譯回物件，方便您加以管理。  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 可支援資料庫的預存程序和使用者定義函式，以及物件模型中的繼承。  
  
 如需詳細資訊，請參閱 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)。  
  
## <a name="linq-to-entities"></a>LINQ to Entities  
 透過實體資料模型，關聯式資料會公開為 .NET 環境內的物件。 如此一來，物件層就成為理想的 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 支援目標，讓程式開發人員可以根據用於建置商務邏輯的語言，針對資料庫編寫查詢。 這項功能稱為 LINQ to Entities。 如需詳細資訊，請參閱 [LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md)。  
  
## <a name="see-also"></a>另請參閱

- [LINQ 和 ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md)
- [Language-Integrated Query (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)
