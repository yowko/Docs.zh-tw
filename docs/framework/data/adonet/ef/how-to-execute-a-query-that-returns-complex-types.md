---
title: HOW TO：執行可傳回複雜類型的查詢
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
ms.openlocfilehash: a428f54c3834ccdf6a0c7a5bfce8307172724524
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59322884"
---
# <a name="how-to-execute-a-query-that-returns-complex-types"></a>HOW TO：執行可傳回複雜類型的查詢
本主題顯示如何執行會傳回內含複雜型別屬性之實體類型物件的 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 查詢。  
  
### <a name="to-run-the-code-in-this-example"></a>執行此範例中的程式碼  
  
1. 新增[AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)至您的專案，並設定您的專案使用[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]。 如需詳細資訊，請參閱[如何：使用 Entity Data Model 精靈](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))。  
  
2. 在應用程式的字碼頁中加入下列 `using` 陳述式 (在 Visual Basic 中為 `Imports`)：  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3. 按兩下 要顯示在模型的.edmx 檔案[模型瀏覽器視窗](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738483(v=vs.100))在實體設計工具。 Entity Designer 介面上，選取`Email`並`Phone`的屬性`Contact`實體類型，然後以滑鼠右鍵按一下並選取**重構至新的複雜型別**。  
  
4. 新的複雜型別與所選`Email`並`Phone`屬性新增至**模型瀏覽器**。 複雜型別有預設名稱： 重新命名的型別`EmailPhone`中**屬性**視窗。 也會將新的 `ComplexProperty` 屬性加入至 `Contact` 實體類型。 將屬性重新命名為 `EmailPhoneComplexType.`  
  
     建立和修改複雜型別的使用 Entity Data Model 精靈的相關資訊，請參閱[How to:將現有屬性重構到複雜型別屬性](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456814(v=vs.100))和[How to:建立和修改複雜型別](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100))。  
  
## <a name="example"></a>範例  
 下列範例會執行查詢，傳回的集合`Contact`物件，並會顯示兩個屬性`Contact`物件：`ContactID`的值和`EmailPhoneComplexType`複雜型別。  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]
