---
title: 分析 LINQ to SQL 原始程式碼
ms.date: 03/30/2017
ms.assetid: cba3eef8-e108-4478-b588-ad59580e133e
ms.openlocfilehash: e39b1686269442044beb73bb7e572738832bec27
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164580"
---
# <a name="analyzing-linq-to-sql-source-code"></a>分析 LINQ to SQL 原始程式碼

使用下列步驟，您就可以從 Northwind 範例資料庫產生 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 原始程式碼。 您可以比較物件模型的項目與資料庫的項目，進一步了解不同項目的對應方式。  
  
> [!NOTE]
> 使用 Visual Studio 的開發人員可以使用 O/R 設計工具來產生此程式碼。  
  
1. 如果您的開發電腦上還沒有 Northwind 範例資料庫，則可以免費進行下載。 如需詳細資訊，請參閱 [下載範例資料庫](downloading-sample-databases.md)。  
  
2. 使用 SqlMetal 命令列工具產生 Visual Basic 或 C# 原始程式檔。 如需詳細資訊，請參閱 [SqlMetal.exe (程式碼產生工具)](../../../../tools/sqlmetal-exe-code-generation-tool.md)。 在命令提示字元中輸入下列命令，就可以產生內含預存程序 (Stored Procedure) 和函式的 Visual Basic 和 C# 原始程式檔：  
  
    - `sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
    - `sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
## <a name="see-also"></a>另請參閱

- [參考](reference.md)
- [背景資訊](background-information.md)
