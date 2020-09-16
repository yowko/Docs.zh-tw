---
title: 作法：使用 EntityCommand 執行參數化預存程序
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4f5639bf-bb7f-4982-bb1d-c7caa4348888
ms.openlocfilehash: 7a055fc3e62821285fe2b6e1333d516c477d025b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90549753"
---
# <a name="how-to-execute-a-parameterized-stored-procedure-using-entitycommand"></a>作法：使用 EntityCommand 執行參數化預存程序
本主題顯示如何使用 <xref:System.Data.EntityClient.EntityCommand> 類別，執行參數化預存程序。  
  
### <a name="to-run-the-code-in-this-example"></a>執行此範例中的程式碼  
  
1. 將 [School 模型](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) 新增至您的專案，並將您的專案設定為使用 Entity Framework。 如需詳細資訊，請參閱 [如何：使用實體資料模型 Wizard](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))。  
  
2. 在應用程式的字碼頁中加入下列 `using` 陳述式 (在 Visual Basic 中為 `Imports`)：  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3. 匯入 `GetStudentGrades` 預存程序，並指定 `CourseGrade` 實體做為傳回型別。 如需如何匯入預存程式的詳細資訊，請參閱 [如何：匯入預存](/previous-versions/dotnet/netframework-4.0/bb896231(v=vs.100))程式。  
  
## <a name="example"></a>範例  
 下列程式碼會執行 `GetStudentGrades` 預存程序，其中 `StudentId` 是必要參數。 然後 <xref:System.Data.EntityClient.EntityDataReader> 會讀取結果。  
  
 [!code-csharp[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#storedprocwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#storedprocwithentitycommand)]  
  
## <a name="see-also"></a>另請參閱

- [Entity Framework 的 EntityClient 提供者](entityclient-provider-for-the-entity-framework.md)
