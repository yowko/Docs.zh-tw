---
title: HOW TO：使用 EntityCommand 執行參數化預存程序
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4f5639bf-bb7f-4982-bb1d-c7caa4348888
ms.openlocfilehash: 433c04f673b402ae893507b1991f170119758b97
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59155268"
---
# <a name="how-to-execute-a-parameterized-stored-procedure-using-entitycommand"></a>HOW TO：使用 EntityCommand 執行參數化預存程序
本主題顯示如何使用 <xref:System.Data.EntityClient.EntityCommand> 類別，執行參數化預存程序。  
  
### <a name="to-run-the-code-in-this-example"></a>執行此範例中的程式碼  
  
1.  新增[School 模型](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))至您的專案，並設定您的專案使用[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]。 如需詳細資訊，請參閱[如何：使用 Entity Data Model 精靈](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))。  
  
2.  在應用程式的字碼頁中加入下列 `using` 陳述式 (在 Visual Basic 中為 `Imports`)：  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  匯入 `GetStudentGrades` 預存程序，並指定 `CourseGrade` 實體做為傳回型別。 如需如何匯入預存程序的詳細資訊，請參閱[How to:匯入預存程序](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896231(v=vs.100))。  
  
## <a name="example"></a>範例  
 下列程式碼會執行 `GetStudentGrades` 預存程序，其中 `StudentId` 是必要參數。 然後 <xref:System.Data.EntityClient.EntityDataReader> 會讀取結果。  
  
 [!code-csharp[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#storedprocwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#storedprocwithentitycommand)]  
  
## <a name="see-also"></a>另請參閱

- [Entity Framework 的 EntityClient 提供者](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)
