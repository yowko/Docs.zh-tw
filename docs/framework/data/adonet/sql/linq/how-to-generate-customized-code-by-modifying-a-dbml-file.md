---
title: HOW TO：藉由修改 DBML 檔案產生自訂程式碼
ms.date: 03/30/2017
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
ms.openlocfilehash: c3fa4d9db4076309ab7d6066cc7072797eaead54
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59338419"
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a>HOW TO：藉由修改 DBML 檔案產生自訂程式碼
您可以產生 Visual Basic 或C#從資料庫標記語言 (.dbml) 中繼資料檔案的原始程式碼。 這種方法讓您有機會在產生應用程式對應程式碼之前，先自訂預設 .dbml 檔。 這是一項進階功能。  
  
 這項處理的步驟如下：  
  
1. 產生 .dbml 檔。  
  
2. 使用編輯器修改 .dbml 檔。 請注意，針對的結構描述定義 (.xsd) 檔驗證.dbml 檔案，必須[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].dbml 檔案。 如需詳細資訊，請參閱 < [LINQ to SQL 中的程式碼產生](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)。  
  
3. 產生 Visual Basic 或C#原始程式碼。  
  
 下列範例會使用 SQLMetal 命令列工具。 如需詳細資訊，請參閱 [SqlMetal.exe (程式碼產生工具)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)。  
  
## <a name="example"></a>範例  
 下列程式碼會從 Northwind 範例資料庫產生 .dbml 檔。 若為資料庫中繼資料的來源，您可以使用資料庫的名稱或 .mdf 檔的名稱。  
  
```  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a>範例  
 下列程式碼會產生 Visual Basic 或C#從.dbml 檔的原始程式碼檔。  
  
```  
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a>另請參閱

- [LINQ to SQL 中的程式碼產生](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [SqlMetal.exe (程式碼產生工具)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
- [建立物件模型](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
