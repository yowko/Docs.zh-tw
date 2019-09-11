---
title: HOW TO：讓模型和對應檔成為內嵌資源
ms.date: 03/30/2017
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
ms.openlocfilehash: 371f8f0317295ee39d543b5637afb93102036b62
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854585"
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a><span data-ttu-id="3f290-102">作法：讓模型和對應檔成為內嵌資源</span><span class="sxs-lookup"><span data-stu-id="3f290-102">How to: Make Model and Mapping Files Embedded Resources</span></span>
<span data-ttu-id="3f290-103">此 Entity Framework 可讓您將模型和對應檔部署為應用程式的內嵌資源。</span><span class="sxs-lookup"><span data-stu-id="3f290-103">The Entity Framework enables you to deploy model and mapping files as embedded resources of an application.</span></span> <span data-ttu-id="3f290-104">具有內嵌模型和對應檔的組件必須載入與實體連接相同的應用程式定義域中。</span><span class="sxs-lookup"><span data-stu-id="3f290-104">The assembly with the embedded model and mapping files must be loaded in the same application domain as the entity connection.</span></span> <span data-ttu-id="3f290-105">如需詳細資訊，請參閱[連接字串](connection-strings.md)。</span><span class="sxs-lookup"><span data-stu-id="3f290-105">For more information, see [Connection Strings](connection-strings.md).</span></span> <span data-ttu-id="3f290-106">根據預設，實體資料模型工具會內嵌模型和對應檔。</span><span class="sxs-lookup"><span data-stu-id="3f290-106">By default, the Entity Data Model tools embed the model and mapping files.</span></span> <span data-ttu-id="3f290-107">當您手動定義模型和對應檔時，請使用此程式，以確保檔案會部署為內嵌資源，以及 Entity Framework 應用程式。</span><span class="sxs-lookup"><span data-stu-id="3f290-107">When you manually define the model and mapping files, use this procedure to ensure that the files are deployed as embedded resources together with an Entity Framework application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3f290-108">若要維護內嵌資源，您必須在每次修改模型和對應檔時重複這個程序。</span><span class="sxs-lookup"><span data-stu-id="3f290-108">To maintain embedded resources, you must repeat this procedure whenever the model and mapping files are modified.</span></span>  
  
### <a name="to-embed-model-and-mapping-files"></a><span data-ttu-id="3f290-109">內嵌模型和對應檔</span><span class="sxs-lookup"><span data-stu-id="3f290-109">To embed model and mapping files</span></span>  
  
1. <span data-ttu-id="3f290-110">在 **方案總管**中，選取概念（csdl）檔案。</span><span class="sxs-lookup"><span data-stu-id="3f290-110">In **Solution Explorer**, select the conceptual (.csdl) file.</span></span>  
  
2. <span data-ttu-id="3f290-111">在 [**屬性**] 窗格中，將 [**組建動作**] 設定為 [**內嵌資源**]。</span><span class="sxs-lookup"><span data-stu-id="3f290-111">In the **Properties** pane, set **Build Action** to **Embedded Resource**.</span></span>  
  
3. <span data-ttu-id="3f290-112">針對儲存 (.ssdl) 檔和對應檔 (.msl) 重複步驟 1 和 2。</span><span class="sxs-lookup"><span data-stu-id="3f290-112">Repeat steps 1 and 2 for the storage (.ssdl) file and the mapping (.msl) file.</span></span>  
  
4. <span data-ttu-id="3f290-113">在**方案總管**中，按兩下 app.config 檔案，然後根據下列其中一種格式`Metadata` ，修改`connectionString`屬性中的參數：</span><span class="sxs-lookup"><span data-stu-id="3f290-113">In **Solution Explorer**, double-click the App.config file and then modify the `Metadata` parameter in the `connectionString` attribute based on one of the following formats:</span></span>  
  
    - <span data-ttu-id="3f290-114">`Metadata=` `res://<assemblyFullName>/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="3f290-114">`Metadata=` `res://<assemblyFullName>/<resourceName>;`</span></span>  
  
    - <span data-ttu-id="3f290-115">`Metadata=` `res://*/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="3f290-115">`Metadata=` `res://*/<resourceName>;`</span></span>  
  
    - `Metadata=res://*;`  
  
     <span data-ttu-id="3f290-116">如需詳細資訊，請參閱[連接字串](connection-strings.md)。</span><span class="sxs-lookup"><span data-stu-id="3f290-116">For more information, see [Connection Strings](connection-strings.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f290-117">範例</span><span class="sxs-lookup"><span data-stu-id="3f290-117">Example</span></span>  
 <span data-ttu-id="3f290-118">下列連接字串會參考[AdventureWorks Sales model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)的內嵌模型和對應檔。</span><span class="sxs-lookup"><span data-stu-id="3f290-118">The following connection string references embedded model and mapping files for the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span> <span data-ttu-id="3f290-119">此連接字串儲存在專案的 App.config 檔案中。</span><span class="sxs-lookup"><span data-stu-id="3f290-119">This connection string is stored in the project's App.config file.</span></span>  

## <a name="see-also"></a><span data-ttu-id="3f290-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f290-120">See also</span></span>

- [<span data-ttu-id="3f290-121">建立模型和對應</span><span class="sxs-lookup"><span data-stu-id="3f290-121">Modeling and Mapping</span></span>](modeling-and-mapping.md)
- [<span data-ttu-id="3f290-122">如何：定義連接字串</span><span class="sxs-lookup"><span data-stu-id="3f290-122">How to: Define the Connection String</span></span>](how-to-define-the-connection-string.md)
- [<span data-ttu-id="3f290-123">如何：建立 EntityConnection 連接字串</span><span class="sxs-lookup"><span data-stu-id="3f290-123">How to: Build an EntityConnection Connection String</span></span>](how-to-build-an-entityconnection-connection-string.md)
- <span data-ttu-id="3f290-124">[ADO.NET 實體資料模型工具](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3f290-124">[ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
