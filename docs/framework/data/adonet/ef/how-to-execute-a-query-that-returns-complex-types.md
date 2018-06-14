---
title: 如何：執行可傳回複雜類型的查詢
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
ms.openlocfilehash: b999033046eb251400f033314ae7eb197a8f110a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760527"
---
# <a name="how-to-execute-a-query-that-returns-complex-types"></a>如何：執行可傳回複雜類型的查詢
本主題顯示如何執行會傳回內含複雜型別屬性之實體類型物件的 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 查詢。  
  
### <a name="to-run-the-code-in-this-example"></a>執行此範例中的程式碼  
  
1.  新增[AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)至您的專案，並設定專案使用[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]。 如需詳細資訊，請參閱[How to： 使用實體資料模型精靈](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d)。  
  
2.  在應用程式的字碼頁中加入下列 `using` 陳述式 (在 Visual Basic 中為 `Imports`)：  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  按兩下以顯示在模型的.edmx 檔[模型瀏覽器視窗](http://msdn.microsoft.com/library/94e836e8-a5ea-47ff-aa3e-599d8a02ebfd)實體設計工具。 實體設計工具介面上，選取`Email`和`Phone`屬性`Contact`實體類型，然後以滑鼠右鍵按一下並選取**重構至新的複雜型別**。  
  
4.  新的複雜型別與所選`Email`和`Phone`屬性加入至**模型瀏覽器**。 複雜型別指定預設名稱： 重新命名的型別`EmailPhone`中**屬性**視窗。 也會將新的 `ComplexProperty` 屬性加入至 `Contact` 實體類型。 將屬性重新命名為 `EmailPhoneComplexType.`  
  
     建立和使用實體資料模型精靈修改複雜類型的相關資訊，請參閱[How to： 重構現有的屬性設成的複雜類型屬性](http://msdn.microsoft.com/library/5b2eb3b3-693d-42cb-b43a-405812d677eb)和[How to： 建立和修改複雜型別](http://msdn.microsoft.com/library/afb8e206-0ffe-4597-b6d4-6ab566897e1d).  
  
## <a name="example"></a>範例  
 下列範例會執行查詢，傳回的集合`Contact`物件並顯示的兩個屬性`Contact`物件：`ContactID`和值`EmailPhoneComplexType`複雜型別。  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]
