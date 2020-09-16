---
title: 作法：執行可傳回複雜類型的查詢
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
ms.openlocfilehash: 01958637cedcd6d502d51e9f0821ff3a9faae840
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545320"
---
# <a name="how-to-execute-a-query-that-returns-complex-types"></a>作法：執行可傳回複雜類型的查詢
本主題顯示如何執行會傳回內含複雜型別屬性之實體類型物件的 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 查詢。  
  
### <a name="to-run-the-code-in-this-example"></a>執行此範例中的程式碼  
  
1. 將 [AdventureWorks Sales 模型](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) 加入至您的專案，並將您的專案設定為使用 Entity Framework。 如需詳細資訊，請參閱 [如何：使用實體資料模型 Wizard](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))。  
  
2. 在應用程式的字碼頁中加入下列 `using` 陳述式 (在 Visual Basic 中為 `Imports`)：  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3. 按兩下 .edmx 檔案，在 Entity Designer 的 [ [模型瀏覽器] 視窗](/previous-versions/dotnet/netframework-4.0/bb738483(v=vs.100)) 中顯示模型。 在 Entity Designer 介面上，選取 `Email` `Phone` 實體類型的和屬性 `Contact` ，然後以滑鼠右鍵按一下並選取 [ **重構至新的複雜型**別]。  
  
4. 具有所選和屬性的新複雜型別 `Email` `Phone` 會加入至 **模型瀏覽器**。 在 [ `EmailPhone` **屬性** ] 視窗中，會為複雜型別指定預設名稱：將型別重新命名為。 也會將新的 `ComplexProperty` 屬性加入至 `Contact` 實體類型。 將屬性重新命名為 `EmailPhoneComplexType.`  
  
     如需使用實體資料模型 Wizard 建立和修改複雜型別的詳細資訊，請參閱 how [to：將現有屬性重構成複雜型別屬性](/previous-versions/dotnet/netframework-4.0/dd456814(v=vs.100)) 和 [如何：建立和修改複雜](/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100))型別。  
  
## <a name="example"></a>範例  
 下列範例會執行查詢，以傳回物件的集合 `Contact` 並顯示物件的兩個屬性 `Contact` ： `ContactID` 和 `EmailPhoneComplexType` 複雜型別的值。  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]
