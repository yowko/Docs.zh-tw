---
title: HOW TO：以 Visual Basic 或 C# 產生物件模型
ms.date: 03/30/2017
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
ms.openlocfilehash: 7d2c0600534c93f5884eec48a4bdaa3ce99945e9
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002809"
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a>HOW TO：在 Visual Basic 或 C @ no__t 中產生物件模型-0
在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，採用您自己之程式語言的物件模型 (Object Model) 會對應至關聯式資料庫。 有兩種工具可讓您從現有資料庫C#的中繼資料自動產生 Visual Basic 或模型。  
  
- 如果您使用 Visual Studio，您可以使用物件關聯式設計工具來產生物件模型。 O/R 設計工具提供豐富的使用者介面，可協助您產生 @no__t 0 的物件模型。 如需詳細資訊，請參閱[Visual Studio 中的 Linq TO SQL 工具](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)。
  
- SQLMetal 命令列工具。 如需詳細資訊，請參閱 [SqlMetal.exe (程式碼產生工具)](../../../../tools/sqlmetal-exe-code-generation-tool.md)。  
  
    > [!NOTE]
    > 如果您沒有現有的資料庫而想要從物件模型建立一個資料庫，可以使用程式碼編輯器和 <xref:System.Data.Linq.DataContext.CreateDatabase%2A> 建立物件模型。 如需詳細資訊，請參閱[如何：以動態方式建立資料庫 @ no__t-0。  
  
 O/R 設計工具的檔提供如何使用 O/R 設計工具產生C# Visual Basic 或物件模型的範例。 下列資訊提供了如何使用 SQLMetal 命令列工具的範例。 如需詳細資訊，請參閱 [SqlMetal.exe (程式碼產生工具)](../../../../tools/sqlmetal-exe-code-generation-tool.md)。  
  
## <a name="example"></a>範例  
 下列範例中所示的 SQLMetal 命令列會產生 Visual Basic 程式碼，做為 Northwind 範例資料庫的屬性型物件模型。 預存程序和函式也會呈現。  
  
```console  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a>範例  
 下列範例中所示的 SQLMetal 命令列產生的 C# 程式碼與 Northwind 範例資料庫之以屬性為基礎的物件模型相同。 預存程序和函式也會呈現，而且會自動將資料表名稱複數化。  
  
```console  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a>另請參閱

- [程式設計手冊](programming-guide.md)
- [LINQ to SQL 物件模型](the-linq-to-sql-object-model.md)
- [依逐步解說學習](learning-by-walkthroughs.md)
- [如何：使用程式碼編輯器自訂實體類別 @ no__t-0
- [以屬性為基礎的對應](attribute-based-mapping.md)
- [SqlMetal.exe (程式碼產生工具)](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [外部對應](external-mapping.md)
- [下載範例資料庫](downloading-sample-databases.md)
- [建立物件模型](creating-the-object-model.md)
