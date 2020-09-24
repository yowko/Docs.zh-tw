---
title: LINQ to SQL
description: LINQ to SQL 是 .NET Framework 的元件，可提供用來將關聯式資料當作物件來管理的執行時間基礎結構。
ms.date: 03/30/2017
ms.assetid: 73d13345-eece-471a-af40-4cc7a2f11655
ms.openlocfilehash: 961e0713de714d0e75417f93e84e0ab748fd9a42
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158314"
---
# <a name="linq-to-sql"></a>LINQ to SQL

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 是 .NET Framework 版本3.5 的元件，可提供用來將關聯式資料當作物件來管理的執行時間基礎結構。  
  
> [!NOTE]
> 關聯式資料會顯示為二維資料表 (「關聯」** 或「一般檔案」**) 的集合，其中通用資料行會與資料表彼此相關。 若要有效地使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]，您必須熟悉關聯式資料庫的基礎原則。  
  
 在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，關聯式資料庫的資料模型會對應至以開發人員的程式設計語言表示的物件模型。 執行應用程式時，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會將物件模型中的 Language Integrated Query (LINQ) 轉譯成 SQL，並將這些查詢傳送至資料庫進行執行。 當資料庫傳回結果時，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會將結果轉譯回您可以在自己的程式語言中處理的物件。  
  
 使用 Visual Studio 的開發人員通常會使用物件關聯式設計工具，其提供用來執行許多功能的使用者介面 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 。  
  
 這一版 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 隨附的文件會描述建置 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 應用程式所需的基本建置組塊、處理序和技巧。 您也可以搜尋特定問題的 Microsoft Docs，也可以參與 [LINQ 論壇](https://social.msdn.microsoft.com/forums/home?forum=linqtosql)，您可以在其中詳細討論更多複雜的主題與專家。 最後， [LINQ to SQL：適用于關聯式資料的 .Net 語言整合查詢-](/previous-versions/dotnet/articles/bb425822(v=msdn.10)) 白皮書詳細資料 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 技術，完整說明 Visual Basic 和 c # 程式碼範例。  
  
## <a name="in-this-section"></a>本節內容  

 [快速入門](getting-started.md)  
 提供 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的扼要概觀，以及如何著手使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的相關資訊。  
  
 [程式設計指南](programming-guide.md)  
 提供對應、查詢、更新、偵錯和類似工作的步驟。  
  
 [參考](reference.md)  
 提供 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 某些層面的參考資訊。 主題包含 SQL-CLR 型別對應、標準查詢運算子轉譯等等。  
  
 [範例](samples.md)  
 提供 Visual Basic 和 c # 範例的連結。  
  
## <a name="related-sections"></a>相關章節  

 [ (LINQ) C 的語言整合式查詢#](../../../../../csharp/programming-guide/concepts/linq/index.md)\
 提供 c # 中的 LINQ 技術概述。

 [Language-Integrated Query (LINQ) - Visual Basic](../../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 提供 Visual Basic 中 LINQ 技術的總覽。
  
 [LINQ](../../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 描述 Visual Basic 使用者的 LINQ 技術。  
  
 [LINQ 和 ADO.NET](../../linq-and-ado-net.md)  
 連結至 ADO.NET 入口網站。  
  
 [LINQ to SQL 逐步解說](/previous-versions/visualstudio/visual-studio-2008/bb386295(v=vs.90))  
 列出 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 可用的逐步解說。  
  
 [下載範例資料庫](downloading-sample-databases.md)  
 描述如何下載文件中所用的範例程式庫。  
  
 [LinqDataSource Web 服務器控制項總覽](/previous-versions/aspnet/bb547113(v=vs.100))  
 描述控制項如何 <xref:System.Web.UI.WebControls.LinqDataSource> 透過 ASP.NET 資料來源控制項架構，為 Web 開發人員公開語言整合查詢 (LINQ) 。
