---
title: 如何：讓模型和對應檔成為內嵌資源
ms.date: 03/30/2017
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
ms.openlocfilehash: 35507f92d0ba9f434156773c8dc5621ed3c423c0
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43555346"
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a><span data-ttu-id="e059a-102">如何：讓模型和對應檔成為內嵌資源</span><span class="sxs-lookup"><span data-stu-id="e059a-102">How to: Make Model and Mapping Files Embedded Resources</span></span>
<span data-ttu-id="e059a-103">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]可讓您部署模型和對應檔做為內嵌資源的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e059a-103">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] enables you to deploy model and mapping files as embedded resources of an application.</span></span> <span data-ttu-id="e059a-104">具有內嵌模型和對應檔的組件必須載入與實體連接相同的應用程式定義域中。</span><span class="sxs-lookup"><span data-stu-id="e059a-104">The assembly with the embedded model and mapping files must be loaded in the same application domain as the entity connection.</span></span> <span data-ttu-id="e059a-105">如需詳細資訊，請參閱[連接字串](../../../../../docs/framework/data/adonet/ef/connection-strings.md)。</span><span class="sxs-lookup"><span data-stu-id="e059a-105">For more information, see [Connection Strings](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span></span> <span data-ttu-id="e059a-106">根據預設，[!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] 工具會內嵌模型和對應檔。</span><span class="sxs-lookup"><span data-stu-id="e059a-106">By default, the [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] tools embed the model and mapping files.</span></span> <span data-ttu-id="e059a-107">當您手動定義模型和對應檔時，請使用這個程序，確保檔案與 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 應用程式已一起部署為內嵌資源。</span><span class="sxs-lookup"><span data-stu-id="e059a-107">When you manually define the model and mapping files, use this procedure to ensure that the files are deployed as embedded resources together with an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e059a-108">若要維護內嵌資源，您必須在每次修改模型和對應檔時重複這個程序。</span><span class="sxs-lookup"><span data-stu-id="e059a-108">To maintain embedded resources, you must repeat this procedure whenever the model and mapping files are modified.</span></span>  
  
### <a name="to-embed-model-and-mapping-files"></a><span data-ttu-id="e059a-109">內嵌模型和對應檔</span><span class="sxs-lookup"><span data-stu-id="e059a-109">To embed model and mapping files</span></span>  
  
1.  <span data-ttu-id="e059a-110">在 [**方案總管] 中**，選取概念 (.csdl) 檔案。</span><span class="sxs-lookup"><span data-stu-id="e059a-110">In **Solution Explorer**, select the conceptual (.csdl) file.</span></span>  
  
2.  <span data-ttu-id="e059a-111">在 **屬性**窗格中，將**建置動作**來**內嵌資源**。</span><span class="sxs-lookup"><span data-stu-id="e059a-111">In the **Properties** pane, set **Build Action** to **Embedded Resource**.</span></span>  
  
3.  <span data-ttu-id="e059a-112">針對儲存 (.ssdl) 檔和對應檔 (.msl) 重複步驟 1 和 2。</span><span class="sxs-lookup"><span data-stu-id="e059a-112">Repeat steps 1 and 2 for the storage (.ssdl) file and the mapping (.msl) file.</span></span>  
  
4.  <span data-ttu-id="e059a-113">在**方案總管**中，按兩下 App.config 檔案，然後修改`Metadata`中的參數`connectionString`屬性根據下列格式之一：</span><span class="sxs-lookup"><span data-stu-id="e059a-113">In **Solution Explorer**, double-click the App.config file and then modify the `Metadata` parameter in the `connectionString` attribute based on one of the following formats:</span></span>  
  
    -   <span data-ttu-id="e059a-114">`Metadata=` `res://<assemblyFullName>/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="e059a-114">`Metadata=` `res://<assemblyFullName>/<resourceName>;`</span></span>  
  
    -   <span data-ttu-id="e059a-115">`Metadata=` `res://*/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="e059a-115">`Metadata=` `res://*/<resourceName>;`</span></span>  
  
    -   `Metadata=res://*;`  
  
     <span data-ttu-id="e059a-116">如需詳細資訊，請參閱[連接字串](../../../../../docs/framework/data/adonet/ef/connection-strings.md)。</span><span class="sxs-lookup"><span data-stu-id="e059a-116">For more information, see [Connection Strings](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e059a-117">範例</span><span class="sxs-lookup"><span data-stu-id="e059a-117">Example</span></span>  
 <span data-ttu-id="e059a-118">下列連接字串參考內嵌的模型和對應檔[AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)。</span><span class="sxs-lookup"><span data-stu-id="e059a-118">The following connection string references embedded model and mapping files for the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).</span></span> <span data-ttu-id="e059a-119">此連接字串儲存在專案的 App.config 檔案中。</span><span class="sxs-lookup"><span data-stu-id="e059a-119">This connection string is stored in the project's App.config file.</span></span>  
  
  
  
## <a name="see-also"></a><span data-ttu-id="e059a-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e059a-120">See Also</span></span>  
 [<span data-ttu-id="e059a-121">建立模型和對應</span><span class="sxs-lookup"><span data-stu-id="e059a-121">Modeling and Mapping</span></span>](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)  
 [<span data-ttu-id="e059a-122">如何：定義連接字串</span><span class="sxs-lookup"><span data-stu-id="e059a-122">How to: Define the Connection String</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md)  
 [<span data-ttu-id="e059a-123">如何：建置 EntityCollection 連接字串</span><span class="sxs-lookup"><span data-stu-id="e059a-123">How to: Build an EntityConnection Connection String</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
 [<span data-ttu-id="e059a-124">ADO.NET 實體資料模型工具</span><span class="sxs-lookup"><span data-stu-id="e059a-124">ADO.NET Entity Data Model  Tools</span></span>](https://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)
