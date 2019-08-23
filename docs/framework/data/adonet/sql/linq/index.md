---
title: LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 73d13345-eece-471a-af40-4cc7a2f11655
ms.openlocfilehash: 86c7e9fae270e75d1ba7e9725ded22ea1961311a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911993"
---
# <a name="linq-to-sql"></a>LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]是 .NET Framework 版本3.5 的元件, 可提供用來將關聯式資料當做物件管理的執行時間基礎結構。  
  
> [!NOTE]
> 關聯式資料會顯示為二維資料表 (「關聯」或「一般檔案」) 的集合，其中通用資料行會與資料表彼此相關。 若要有效地使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]，您必須熟悉關聯式資料庫的基礎原則。  
  
 在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，關聯式資料庫的資料模型會對應至以開發人員的程式設計語言表示的物件模型。 執行應用程式時，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會將物件模型中的 Language Integrated Query (LINQ) 轉譯成 SQL，並將這些查詢傳送至資料庫進行執行。 當資料庫傳回結果時，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會將結果轉譯回您可以在自己的程式語言中處理的物件。  
  
 使用 Visual Studio 的開發人員通常會使用物件關聯式設計工具, 它會提供用來執行許多功能的[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]使用者介面。  
  
 這一版 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 隨附的文件會描述建置 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 應用程式所需的基本建置組塊、處理序和技巧。 您也可以搜尋 Microsoft Docs 中的特定問題, 而且您可以參與[LINQ 論壇](https://go.microsoft.com/fwlink/?LinkId=76488), 您可以在其中詳細討論更複雜的主題。 最後, [LINQ to SQL: 關聯式資料的 .net 語言整合式查詢](https://go.microsoft.com/fwlink/?LinkId=93205)白皮書詳細說明[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]技術, 完成 Visual Basic 和C#程式碼範例。  
  
## <a name="in-this-section"></a>本節內容  
 [快速入門](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)  
 提供 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的扼要概觀，以及如何著手使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的相關資訊。  
  
 [程式設計手冊](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 提供對應、查詢、更新、偵錯和類似工作的步驟。  
  
 [參考資料](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 提供 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 某些層面的參考資訊。 主題包含 SQL-CLR 型別對應、標準查詢運算子轉譯等等。  
  
 [範例](../../../../../../docs/framework/data/adonet/sql/linq/samples.md)  
 提供 Visual Basic 和C#範例的連結。  
  
## <a name="related-sections"></a>相關章節  
 [語言整合式查詢 (LINQ)-C#](../../../../../csharp/programming-guide/concepts/linq/index.md)\
 概述中C#的 LINQ 技術。
 
 [Language-Integrated Query (LINQ) - Visual Basic](../../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 概述 Visual Basic 中的 LINQ 技術。
  
 [LINQ](../../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 描述[!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] Visual Basic 使用者的技術。  
  
 [LINQ 和 ADO.NET](../../../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 ADO.NET 入口網站的連結。  
  
 [LINQ to SQL 逐步解說](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb386295(v=vs.90))  
 列出 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 可用的逐步解說。  
  
 [下載範例資料庫](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 描述如何下載文件中所用的範例程式庫。  
  
 [LinqDataSource Web 服務器控制項總覽](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))  
 描述<xref:System.Web.UI.WebControls.LinqDataSource>控制項如何透過 ASP.NET [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)]資料原始檔控制架構, 向 Web 開發人員公開。
