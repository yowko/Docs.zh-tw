---
title: "HOW TO：在 Visual Basic 或 C# 中產生物件模型 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# HOW TO：在 Visual Basic 或 C# 中產生物件模型
在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，採用您自己之程式語言的物件模型 \(Object Model\) 會對應至關聯式資料庫。  有兩項工具可用於從現有資料庫的中繼資料 \(Metadata\)，自動產生 [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] 或 C\# 模型。  
  
-   如果您使用的是 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)]，則可使用[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]來產生物件模型。  [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] 提供了豐富的使用者介面，可協助您產生 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 物件模型。  
  
-   SQLMetal 命令列工具。  如需詳細資訊，請參閱[SqlMetal.exe \(程式碼產生工具\)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)。  
  
    > [!NOTE]
    >  如果您沒有現有的資料庫而想要從物件模型建立一個資料庫，可以使用程式碼編輯器和 <xref:System.Data.Linq.DataContext.CreateDatabase%2A> 建立物件模型。  如需詳細資訊，請參閱[HOW TO：動態建立資料庫](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md)。  
  
 [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]的文件提供了如何使用 [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]來產生 [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] 或 C\# 物件模型的範例。  下列資訊提供了如何使用 SQLMetal 命令列工具的範例。  如需詳細資訊，請參閱[SqlMetal.exe \(程式碼產生工具\)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)。  
  
## 範例  
 下列範例中所示的 SQLMetal 命令列會產生 [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] 程式碼，當做 Northwind 範例資料庫之以屬性為基礎的物件模型。  預存程序和函式也會呈現。  
  
```  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## 範例  
 下列範例中所示的 SQLMetal 命令列產生的 C\# 程式碼與 Northwind 範例資料庫之以屬性為基礎的物件模型相同。  預存程序和函式也會呈現，而且會自動將資料表名稱複數化。  
  
```  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## 請參閱  
 [程式設計手冊](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)   
 [LINQ to SQL 物件模型](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)   
 [從逐步解說學習](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)   
 [HOW TO：使用程式碼編輯器自訂實體類別](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)   
 [以屬性為基礎的對應](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)   
 [SqlMetal.exe \(程式碼產生工具\)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)   
 [外部對應](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)   
 [下載範例資料庫](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)   
 [建立物件模型](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)