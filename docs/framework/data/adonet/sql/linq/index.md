---
title: LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 73d13345-eece-471a-af40-4cc7a2f11655
ms.openlocfilehash: b0660312f540a69911905edd08541ed70cf39bb5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174312"
---
# <a name="linq-to-sql"></a>LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]是 .NET Framework 版本 3.5 的一個元件，它提供了用於將關係資料作為物件管理的運行時基礎結構。  
  
> [!NOTE]
> 關聯式資料會顯示為二維資料表 (「關聯」** 或「一般檔案」**) 的集合，其中通用資料行會與資料表彼此相關。 若要有效地使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]，您必須熟悉關聯式資料庫的基礎原則。  
  
 在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，關聯式資料庫的資料模型會對應至以開發人員的程式設計語言表示的物件模型。 執行應用程式時，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會將物件模型中的 Language Integrated Query (LINQ) 轉譯成 SQL，並將這些查詢傳送至資料庫進行執行。 當資料庫傳回結果時，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會將結果轉譯回您可以在自己的程式語言中處理的物件。  
  
 使用 Visual Studio 的開發人員通常使用物件關係設計器，它提供了實現 的許多功能的[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]使用者介面。  
  
 這一版 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 隨附的文件會描述建置 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 應用程式所需的基本建置組塊、處理序和技巧。 您還可以搜索 Microsoft 文檔以查找特定問題，還可以參加[LINQ 論壇](https://social.msdn.microsoft.com/forums/home?forum=linqtosql)，與專家詳細討論更複雜的主題。 最後[，LINQ 到 SQL：.NET 語言集成查詢關係資料](https://docs.microsoft.com/previous-versions/dotnet/articles/bb425822(v=msdn.10))白皮書詳細介紹了[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]技術，並附有視覺化基本和 C# 代碼示例。  
  
## <a name="in-this-section"></a>本節內容  
 [快速入門](getting-started.md)  
 提供 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的扼要概觀，以及如何著手使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的相關資訊。  
  
 [程式設計指南](programming-guide.md)  
 提供對應、查詢、更新、偵錯和類似工作的步驟。  
  
 [參考](reference.md)  
 提供 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 某些層面的參考資訊。 主題包含 SQL-CLR 型別對應、標準查詢運算子轉譯等等。  
  
 [樣品](samples.md)  
 提供指向視覺化基本和 C# 示例的連結。  
  
## <a name="related-sections"></a>相關章節  
 [語言集成查詢 （LINQ） - C#](../../../../../csharp/programming-guide/concepts/linq/index.md)\
 在 C# 中提供 LINQ 技術的概述。

 [Language-Integrated Query (LINQ) - Visual Basic](../../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 在視覺化基礎知識中概述 LINQ 技術。
  
 [LINQ](../../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 介紹視覺化基本使用者的 LINQ 技術。  
  
 [LINQ 和 ADO.NET](../../linq-and-ado-net.md)  
 指向ADO.NET門戶的連結。  
  
 [LINQ to SQL 逐步解說](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb386295(v=vs.90))  
 列出 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 可用的逐步解說。  
  
 [下載範例資料庫](downloading-sample-databases.md)  
 描述如何下載文件中所用的範例程式庫。  
  
 [LinqDataSource Web 服務器控制概述](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))  
 描述<xref:System.Web.UI.WebControls.LinqDataSource>控制項如何通過ASP.NET資料來源控制體系結構向 Web 開發人員公開語言集成查詢 （LINQ）。
