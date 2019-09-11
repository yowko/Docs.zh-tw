---
title: SQL 產生
ms.date: 03/30/2017
ms.assetid: 0e16aa02-d458-4418-a765-58b42aad9315
ms.openlocfilehash: 9c5301d3f4d5bc2e0db4a138c6d8ceb06d3a7845
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854363"
---
# <a name="sql-generation"></a>SQL 產生
當您撰寫 Entity Framework 的提供者時，您必須將 Entity Framework 的命令樹轉譯成特定資料庫可瞭解的 SQL，例如適用于 SQL Server 的 Transact-sql 或 Oracle 的 PL/SQL。 在本節中，您將瞭解如何為 Entity Framework 提供者開發 SQL 世代元件（適用于 SELECT 查詢）。 如需插入、更新和刪除查詢的詳細資訊，請參閱[修改 SQL 產生](modification-sql-generation.md)。  
  
 若要瞭解這一節，您應該熟悉 Entity Framework 和 ADO.NET 提供者模型。 您也應該了解命令樹和 <xref:System.Data.Common.CommandTrees.DbExpression>。  
  
## <a name="the-role-of-the-sql-generation-module"></a>SQL 產生模組的角色  
 Entity Framework 提供者的 SQL 產生模組會將指定的查詢命令樹轉譯成以 SQL：1999相容資料庫為目標的單一 SQL SELECT 語句。 產生的 SQL 應該盡量擁有少一點的巢狀查詢。 SQL 產生模組不應該簡化查詢命令樹的輸出。 Entity Framework 將會執行這項操作，例如，藉由排除聯結和折迭連續的篩選節點。  
  
 <xref:System.Data.Common.DbProviderServices> 類別是存取 SQL 產生層的起點，可將命令樹轉換成 <xref:System.Data.Common.DbCommand>。  
  
## <a name="in-this-section"></a>本節內容  
 [命令樹的形狀](the-shape-of-the-command-trees.md)  
  
 [從命令樹產生 SQL - 最佳做法](generating-sql-from-command-trees-best-practices.md)  
  
 [範例提供者中的 SQL 產生](sql-generation-in-the-sample-provider.md)  
  
## <a name="see-also"></a>另請參閱

- [撰寫 Entity Framework 資料提供者](writing-an-ef-data-provider.md)
