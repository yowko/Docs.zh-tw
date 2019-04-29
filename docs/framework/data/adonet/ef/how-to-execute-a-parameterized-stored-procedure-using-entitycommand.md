---
title: HOW TO：使用 EntityCommand 執行參數化預存程序
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4f5639bf-bb7f-4982-bb1d-c7caa4348888
ms.openlocfilehash: deb1877397053ceab8c284a537a861ba56ffb729
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61606152"
---
# <a name="how-to-execute-a-parameterized-stored-procedure-using-entitycommand"></a><span data-ttu-id="0dd3a-102">HOW TO：使用 EntityCommand 執行參數化預存程序</span><span class="sxs-lookup"><span data-stu-id="0dd3a-102">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>
<span data-ttu-id="0dd3a-103">本主題顯示如何使用 <xref:System.Data.EntityClient.EntityCommand> 類別，執行參數化預存程序。</span><span class="sxs-lookup"><span data-stu-id="0dd3a-103">This topic shows how to execute a parameterized stored procedure by using the <xref:System.Data.EntityClient.EntityCommand> class.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="0dd3a-104">執行此範例中的程式碼</span><span class="sxs-lookup"><span data-stu-id="0dd3a-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="0dd3a-105">新增[School 模型](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))至您的專案，並設定您的專案使用[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0dd3a-105">Add the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="0dd3a-106">如需詳細資訊，請參閱[如何：使用 Entity Data Model 精靈](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="0dd3a-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="0dd3a-107">在應用程式的字碼頁中加入下列 `using` 陳述式 (在 Visual Basic 中為 `Imports`)：</span><span class="sxs-lookup"><span data-stu-id="0dd3a-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3. <span data-ttu-id="0dd3a-108">匯入 `GetStudentGrades` 預存程序，並指定 `CourseGrade` 實體做為傳回型別。</span><span class="sxs-lookup"><span data-stu-id="0dd3a-108">Import the `GetStudentGrades` stored procedure and specify `CourseGrade` entities as a return type.</span></span> <span data-ttu-id="0dd3a-109">如需如何匯入預存程序的詳細資訊，請參閱[How to:匯入預存程序](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896231(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="0dd3a-109">For information on how to import a stored procedure, see [How to: Import a Stored Procedure](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896231(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0dd3a-110">範例</span><span class="sxs-lookup"><span data-stu-id="0dd3a-110">Example</span></span>  
 <span data-ttu-id="0dd3a-111">下列程式碼會執行 `GetStudentGrades` 預存程序，其中 `StudentId` 是必要參數。</span><span class="sxs-lookup"><span data-stu-id="0dd3a-111">The following code executes the `GetStudentGrades` stored procedure where `StudentId` is a required parameter.</span></span> <span data-ttu-id="0dd3a-112">然後 <xref:System.Data.EntityClient.EntityDataReader> 會讀取結果。</span><span class="sxs-lookup"><span data-stu-id="0dd3a-112">The results are then read by an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#storedprocwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#storedprocwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="0dd3a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0dd3a-113">See also</span></span>

- [<span data-ttu-id="0dd3a-114">Entity Framework 的 EntityClient 提供者</span><span class="sxs-lookup"><span data-stu-id="0dd3a-114">EntityClient Provider for the Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)
