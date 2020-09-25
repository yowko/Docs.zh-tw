---
title: 作法：讓模型和對應檔成為內嵌資源
ms.date: 03/30/2017
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
ms.openlocfilehash: 8496dcad5422d1a45af52e58325efd360768da34
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198284"
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a><span data-ttu-id="82d30-102">作法：讓模型和對應檔成為內嵌資源</span><span class="sxs-lookup"><span data-stu-id="82d30-102">How to: Make Model and Mapping Files Embedded Resources</span></span>

<span data-ttu-id="82d30-103">Entity Framework 可讓您將模型和對應檔部署為應用程式的內嵌資源。</span><span class="sxs-lookup"><span data-stu-id="82d30-103">The Entity Framework enables you to deploy model and mapping files as embedded resources of an application.</span></span> <span data-ttu-id="82d30-104">具有內嵌模型和對應檔的組件必須載入與實體連接相同的應用程式定義域中。</span><span class="sxs-lookup"><span data-stu-id="82d30-104">The assembly with the embedded model and mapping files must be loaded in the same application domain as the entity connection.</span></span> <span data-ttu-id="82d30-105">如需詳細資訊，請參閱[連接字串](connection-strings.md)。</span><span class="sxs-lookup"><span data-stu-id="82d30-105">For more information, see [Connection Strings](connection-strings.md).</span></span> <span data-ttu-id="82d30-106">根據預設，實體資料模型工具會內嵌模型和對應檔。</span><span class="sxs-lookup"><span data-stu-id="82d30-106">By default, the Entity Data Model tools embed the model and mapping files.</span></span> <span data-ttu-id="82d30-107">當您手動定義模型和對應檔時，請使用這個程式，確保檔案與 Entity Framework 的應用程式一起部署為內嵌資源。</span><span class="sxs-lookup"><span data-stu-id="82d30-107">When you manually define the model and mapping files, use this procedure to ensure that the files are deployed as embedded resources together with an Entity Framework application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="82d30-108">若要維護內嵌資源，您必須在每次修改模型和對應檔時重複這個程序。</span><span class="sxs-lookup"><span data-stu-id="82d30-108">To maintain embedded resources, you must repeat this procedure whenever the model and mapping files are modified.</span></span>  
  
### <a name="to-embed-model-and-mapping-files"></a><span data-ttu-id="82d30-109">內嵌模型和對應檔</span><span class="sxs-lookup"><span data-stu-id="82d30-109">To embed model and mapping files</span></span>  
  
1. <span data-ttu-id="82d30-110">在 **方案總管**中，選取概念 ( csdl) 檔。</span><span class="sxs-lookup"><span data-stu-id="82d30-110">In **Solution Explorer**, select the conceptual (.csdl) file.</span></span>  
  
2. <span data-ttu-id="82d30-111">在 [ **屬性** ] 窗格中，將 [ **組建動作** ] 設定為 [ **內嵌資源**]。</span><span class="sxs-lookup"><span data-stu-id="82d30-111">In the **Properties** pane, set **Build Action** to **Embedded Resource**.</span></span>  
  
3. <span data-ttu-id="82d30-112">針對儲存 (.ssdl) 檔和對應檔 (.msl) 重複步驟 1 和 2。</span><span class="sxs-lookup"><span data-stu-id="82d30-112">Repeat steps 1 and 2 for the storage (.ssdl) file and the mapping (.msl) file.</span></span>  
  
4. <span data-ttu-id="82d30-113">在 **方案總管**中，按兩下 App.config 檔案，然後 `Metadata` `connectionString` 根據下列其中一種格式來修改屬性中的參數：</span><span class="sxs-lookup"><span data-stu-id="82d30-113">In **Solution Explorer**, double-click the App.config file and then modify the `Metadata` parameter in the `connectionString` attribute based on one of the following formats:</span></span>  
  
    - <span data-ttu-id="82d30-114">`Metadata=` `res://<assemblyFullName>/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="82d30-114">`Metadata=` `res://<assemblyFullName>/<resourceName>;`</span></span>  
  
    - <span data-ttu-id="82d30-115">`Metadata=` `res://*/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="82d30-115">`Metadata=` `res://*/<resourceName>;`</span></span>  
  
    - `Metadata=res://*;`  
  
     <span data-ttu-id="82d30-116">如需詳細資訊，請參閱[連接字串](connection-strings.md)。</span><span class="sxs-lookup"><span data-stu-id="82d30-116">For more information, see [Connection Strings](connection-strings.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="82d30-117">範例</span><span class="sxs-lookup"><span data-stu-id="82d30-117">Example</span></span>  

 <span data-ttu-id="82d30-118">下列連接字串會參考 [AdventureWorks Sales model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)的內嵌模型和對應檔。</span><span class="sxs-lookup"><span data-stu-id="82d30-118">The following connection string references embedded model and mapping files for the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span> <span data-ttu-id="82d30-119">此連接字串儲存在專案的 App.config 檔案中。</span><span class="sxs-lookup"><span data-stu-id="82d30-119">This connection string is stored in the project's App.config file.</span></span>  

## <a name="see-also"></a><span data-ttu-id="82d30-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82d30-120">See also</span></span>

- [<span data-ttu-id="82d30-121">建立模型和對應</span><span class="sxs-lookup"><span data-stu-id="82d30-121">Modeling and Mapping</span></span>](modeling-and-mapping.md)
- [<span data-ttu-id="82d30-122">作法：定義連接字串</span><span class="sxs-lookup"><span data-stu-id="82d30-122">How to: Define the Connection String</span></span>](how-to-define-the-connection-string.md)
- [<span data-ttu-id="82d30-123">作法：建置 EntityCollection 連接字串</span><span class="sxs-lookup"><span data-stu-id="82d30-123">How to: Build an EntityConnection Connection String</span></span>](how-to-build-an-entityconnection-connection-string.md)
- <span data-ttu-id="82d30-124">[ADO.NET 實體資料模型工具](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="82d30-124">[ADO.NET Entity Data Model Tools](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
