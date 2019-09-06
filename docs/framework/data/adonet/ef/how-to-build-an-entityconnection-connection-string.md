---
title: HOW TO：建置 EntityCollection 連接字串
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5bd1a748-3df7-4d0a-a607-14f25e3175e9
ms.openlocfilehash: 33a52b2542a2e312f7fbb8b7ca09a8b85662d2d4
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251542"
---
# <a name="how-to-build-an-entityconnection-connection-string"></a><span data-ttu-id="b7e91-102">作法：建置 EntityCollection 連接字串</span><span class="sxs-lookup"><span data-stu-id="b7e91-102">How to: Build an EntityConnection Connection String</span></span>
<span data-ttu-id="b7e91-103">本主題提供的範例將示範如何建立 <xref:System.Data.EntityClient.EntityConnection>。</span><span class="sxs-lookup"><span data-stu-id="b7e91-103">This topic provides an example of how to build an <xref:System.Data.EntityClient.EntityConnection>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="b7e91-104">執行此範例中的程式碼</span><span class="sxs-lookup"><span data-stu-id="b7e91-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="b7e91-105">將[AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)新增至您的專案，並將您的[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]專案設定為使用。</span><span class="sxs-lookup"><span data-stu-id="b7e91-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="b7e91-106">如需詳細資訊，請參閱[如何：使用實體資料模型 Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="b7e91-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="b7e91-107">在應用程式的字碼頁中加入下列 `using` 陳述式 (在 Visual Basic 中為 `Imports`)：</span><span class="sxs-lookup"><span data-stu-id="b7e91-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="b7e91-108">範例</span><span class="sxs-lookup"><span data-stu-id="b7e91-108">Example</span></span>  
 <span data-ttu-id="b7e91-109">下列範例會初始化基礎提供者的 <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType>，然後初始化 <xref:System.Data.EntityClient.EntityConnectionStringBuilder?displayProperty=nameWithType> 物件並將此物件傳遞給 <xref:System.Data.EntityClient.EntityConnection> 的建構函式 (Constructor)。</span><span class="sxs-lookup"><span data-stu-id="b7e91-109">The following example initializes the <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType> for the underlying provider, then initializes the <xref:System.Data.EntityClient.EntityConnectionStringBuilder?displayProperty=nameWithType> object and passes this object to the constructor of the <xref:System.Data.EntityClient.EntityConnection>.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#BuildingConnectionStringWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#buildingconnectionstringwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#BuildingConnectionStringWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#buildingconnectionstringwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="b7e91-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7e91-110">See also</span></span>

- <span data-ttu-id="b7e91-111">[如何：搭配物件內容使用 EntityConnection](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738461(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b7e91-111">[How to: Use EntityConnection with an Object Context](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738461(v=vs.100))</span></span>
- [<span data-ttu-id="b7e91-112">Entity Framework 的 EntityClient 提供者</span><span class="sxs-lookup"><span data-stu-id="b7e91-112">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)
