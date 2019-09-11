---
title: 作法：執行可傳回複雜類型的查詢
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
ms.openlocfilehash: b08b220e969ad1c400413978c85b2f107d64a688
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854649"
---
# <a name="how-to-execute-a-query-that-returns-complex-types"></a><span data-ttu-id="f85b4-102">HOW TO：執行可傳回複雜類型的查詢</span><span class="sxs-lookup"><span data-stu-id="f85b4-102">How to: Execute a Query that Returns Complex Types</span></span>
<span data-ttu-id="f85b4-103">本主題顯示如何執行會傳回內含複雜型別屬性之實體類型物件的 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 查詢。</span><span class="sxs-lookup"><span data-stu-id="f85b4-103">This topic shows how to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query that returns entity type objects that contain a property of a complex type.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="f85b4-104">執行此範例中的程式碼</span><span class="sxs-lookup"><span data-stu-id="f85b4-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="f85b4-105">將[AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)加入至您的專案，並將專案設定為使用 Entity Framework。</span><span class="sxs-lookup"><span data-stu-id="f85b4-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="f85b4-106">如需詳細資訊，請參閱[如何：使用實體資料模型 Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="f85b4-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="f85b4-107">在應用程式的字碼頁中加入下列 `using` 陳述式 (在 Visual Basic 中為 `Imports`)：</span><span class="sxs-lookup"><span data-stu-id="f85b4-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3. <span data-ttu-id="f85b4-108">按兩下 .edmx 檔案，在 Entity Designer 的 [[模型瀏覽器] 視窗](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738483(v=vs.100))中顯示模型。</span><span class="sxs-lookup"><span data-stu-id="f85b4-108">Double click the .edmx file to display the model in the [Model Browser window](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738483(v=vs.100)) of the Entity Designer.</span></span> <span data-ttu-id="f85b4-109">在 Entity Designer 介面上，選取`Email`實體`Phone`類型的和`Contact`屬性，然後以滑鼠右鍵按一下並選取 **重構至新的複雜類型**。</span><span class="sxs-lookup"><span data-stu-id="f85b4-109">On the Entity Designer surface, select the `Email` and `Phone` properties of the `Contact` entity type, then right-click and select **Refactor into New Complex Type**.</span></span>  
  
4. <span data-ttu-id="f85b4-110">具有所選`Email`和`Phone`屬性的新複雜型別會加入至 [**模型瀏覽器**] 中。</span><span class="sxs-lookup"><span data-stu-id="f85b4-110">A new complex type with the selected `Email` and `Phone` properties is added to the **Model Browser**.</span></span> <span data-ttu-id="f85b4-111">在 [屬性] 視窗中，會為複雜型別指定`EmailPhone`預設名稱 ：將型別重新命名為。</span><span class="sxs-lookup"><span data-stu-id="f85b4-111">The complex type is given a default name: rename the type to `EmailPhone` in the **Properties** window.</span></span> <span data-ttu-id="f85b4-112">也會將新的 `ComplexProperty` 屬性加入至 `Contact` 實體類型。</span><span class="sxs-lookup"><span data-stu-id="f85b4-112">Also, a new `ComplexProperty` property is added to the `Contact` entity type.</span></span> <span data-ttu-id="f85b4-113">將屬性重新命名為 `EmailPhoneComplexType.`</span><span class="sxs-lookup"><span data-stu-id="f85b4-113">Rename the property to `EmailPhoneComplexType.`</span></span>  
  
     <span data-ttu-id="f85b4-114">如需使用實體資料模型 Wizard 來建立和修改複雜型別的詳細資訊， [請參閱如何：將現有的屬性重構成複雜型](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456814(v=vs.100))別[屬性，以及如何：建立和修改複雜類型](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="f85b4-114">For information about creating and modifying complex types by using the Entity Data Model Wizard, see [How to: Refactor Existing Properties into a Complex Type Property](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456814(v=vs.100)) and [How to: Create and Modify Complex Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f85b4-115">範例</span><span class="sxs-lookup"><span data-stu-id="f85b4-115">Example</span></span>  
 <span data-ttu-id="f85b4-116">下列範例會執行`Contact`查詢，以傳回物件的集合，並顯示`Contact`物件的兩個屬性： `ContactID`和`EmailPhoneComplexType`複雜類型的值。</span><span class="sxs-lookup"><span data-stu-id="f85b4-116">The following example executes a query that returns a collection of `Contact` objects and displays two properties of the `Contact` objects: `ContactID` and the values of the `EmailPhoneComplexType` complex type.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]
