---
title: "如何：執行可傳回複雜類型的查詢"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: cae0cc50b18641634fc8109fb29eeb30e9cf7cd8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-execute-a-query-that-returns-complex-types"></a><span data-ttu-id="459c3-102">如何：執行可傳回複雜類型的查詢</span><span class="sxs-lookup"><span data-stu-id="459c3-102">How to: Execute a Query that Returns Complex Types</span></span>
<span data-ttu-id="459c3-103">本主題顯示如何執行會傳回內含複雜型別屬性之實體類型物件的 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 查詢。</span><span class="sxs-lookup"><span data-stu-id="459c3-103">This topic shows how to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query that returns entity type objects that contain a property of a complex type.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="459c3-104">執行此範例中的程式碼</span><span class="sxs-lookup"><span data-stu-id="459c3-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="459c3-105">新增[AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)至您的專案，並設定專案使用[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="459c3-105">Add the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="459c3-106">如需詳細資訊，請參閱[How to： 使用實體資料模型精靈](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d)。</span><span class="sxs-lookup"><span data-stu-id="459c3-106">For more information, see [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span></span>  
  
2.  <span data-ttu-id="459c3-107">在應用程式的字碼頁中加入下列 `using` 陳述式 (在 Visual Basic 中為 `Imports`)：</span><span class="sxs-lookup"><span data-stu-id="459c3-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  <span data-ttu-id="459c3-108">按兩下以顯示在模型的.edmx 檔[模型瀏覽器視窗](http://msdn.microsoft.com/library/94e836e8-a5ea-47ff-aa3e-599d8a02ebfd)實體設計工具。</span><span class="sxs-lookup"><span data-stu-id="459c3-108">Double click the .edmx file to display the model in the [Model Browser window](http://msdn.microsoft.com/library/94e836e8-a5ea-47ff-aa3e-599d8a02ebfd) of the Entity Designer.</span></span> <span data-ttu-id="459c3-109">實體設計工具介面上，選取`Email`和`Phone`屬性`Contact`實體類型，然後以滑鼠右鍵按一下並選取**重構至新的複雜型別**。</span><span class="sxs-lookup"><span data-stu-id="459c3-109">On the Entity Designer surface, select the `Email` and `Phone` properties of the `Contact` entity type, then right-click and select **Refactor into New Complex Type**.</span></span>  
  
4.  <span data-ttu-id="459c3-110">新的複雜型別與所選`Email`和`Phone`屬性加入至**模型瀏覽器**。</span><span class="sxs-lookup"><span data-stu-id="459c3-110">A new complex type with the selected `Email` and `Phone` properties is added to the **Model Browser**.</span></span> <span data-ttu-id="459c3-111">複雜型別指定預設名稱： 重新命名的型別`EmailPhone`中**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="459c3-111">The complex type is given a default name: rename the type to `EmailPhone` in the **Properties** window.</span></span> <span data-ttu-id="459c3-112">也會將新的 `ComplexProperty` 屬性加入至 `Contact` 實體類型。</span><span class="sxs-lookup"><span data-stu-id="459c3-112">Also, a new `ComplexProperty` property is added to the `Contact` entity type.</span></span> <span data-ttu-id="459c3-113">將屬性重新命名為 `EmailPhoneComplexType.`</span><span class="sxs-lookup"><span data-stu-id="459c3-113">Rename the property to `EmailPhoneComplexType.`</span></span>  
  
     <span data-ttu-id="459c3-114">建立和使用實體資料模型精靈修改複雜類型的相關資訊，請參閱[How to： 重構現有的屬性設成的複雜類型屬性](http://msdn.microsoft.com/library/5b2eb3b3-693d-42cb-b43a-405812d677eb)和[How to： 建立和修改複雜型別](http://msdn.microsoft.com/library/afb8e206-0ffe-4597-b6d4-6ab566897e1d).</span><span class="sxs-lookup"><span data-stu-id="459c3-114">For information about creating and modifying complex types by using the Entity Data Model Wizard, see [How to: Refactor Existing Properties into a Complex Type Property](http://msdn.microsoft.com/library/5b2eb3b3-693d-42cb-b43a-405812d677eb) and [How to: Create and Modify Complex Types](http://msdn.microsoft.com/library/afb8e206-0ffe-4597-b6d4-6ab566897e1d).</span></span>  
  
## <a name="example"></a><span data-ttu-id="459c3-115">範例</span><span class="sxs-lookup"><span data-stu-id="459c3-115">Example</span></span>  
 <span data-ttu-id="459c3-116">下列範例會執行查詢，傳回的集合`Contact`物件並顯示的兩個屬性`Contact`物件：`ContactID`和值`EmailPhoneComplexType`複雜型別。</span><span class="sxs-lookup"><span data-stu-id="459c3-116">The following example executes a query that returns a collection of `Contact` objects and displays two properties of the `Contact` objects: `ContactID` and the values of the `EmailPhoneComplexType` complex type.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]
