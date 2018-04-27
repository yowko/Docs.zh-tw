---
title: 如何：定義連接字串
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 7cfde8d819a9b3a4eaeaed5f20c07130198714fd
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-define-the-connection-string"></a><span data-ttu-id="0c833-102">如何：定義連接字串</span><span class="sxs-lookup"><span data-stu-id="0c833-102">How to: Define the Connection String</span></span>
<span data-ttu-id="0c833-103">本主題將示範如何定義連接至概念模型時所使用的連接字串 (Connection String)。</span><span class="sxs-lookup"><span data-stu-id="0c833-103">This topic shows how to define the connection string that is used when connecting to a conceptual model.</span></span> <span data-ttu-id="0c833-104">本主題根據[AdventureWorks Sales](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)概念模型。</span><span class="sxs-lookup"><span data-stu-id="0c833-104">This topic is based on the [AdventureWorks Sales](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) conceptual model.</span></span> <span data-ttu-id="0c833-105">AdventureWorks Sales Model 會在 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 文件的所有工作相關的主題內使用。</span><span class="sxs-lookup"><span data-stu-id="0c833-105">The AdventureWorks Sales Model is used throughout the task-related topics in the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] documentation.</span></span> <span data-ttu-id="0c833-106">本主題假設您已經設定[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]和定義 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="0c833-106">This topic assumes that you have already configured the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] and defined the AdventureWorks Sales Model.</span></span> <span data-ttu-id="0c833-107">如需詳細資訊，請參閱[How to： 手動定義模型和對應檔](http://msdn.microsoft.com/library/d4fd6864-f2a1-48f0-aa32-1e318775a99a)。</span><span class="sxs-lookup"><span data-stu-id="0c833-107">For more information, see [How to: Manually Define the Model and Mapping Files](http://msdn.microsoft.com/library/d4fd6864-f2a1-48f0-aa32-1e318775a99a).</span></span> <span data-ttu-id="0c833-108">本主題中的程序也會包含在[How to： 手動設定 Entity Framework 專案](http://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)。</span><span class="sxs-lookup"><span data-stu-id="0c833-108">The procedures in this topic are also included in [How to: Manually Configure an Entity Framework Project](http://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0c833-109">如果您使用[!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)]精靈在 Visual Studio 專案中，自動產生的.edmx 檔案並設定專案以使用[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0c833-109">If you use the [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] Wizard in a Visual Studio project, it automatically generates an .edmx file and configures the project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="0c833-110">如需詳細資訊，請參閱[How to： 使用實體資料模型精靈](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d)</span><span class="sxs-lookup"><span data-stu-id="0c833-110">For more information, see [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d)</span></span>  
  
### <a name="to-define-the-entity-framework-connection-string"></a><span data-ttu-id="0c833-111">定義 Entity Framework 連接字串</span><span class="sxs-lookup"><span data-stu-id="0c833-111">To define the Entity Framework connection string</span></span>  
  
-   <span data-ttu-id="0c833-112">開啟專案的應用程式組態檔 (app.config) 並加入下列連接字串：</span><span class="sxs-lookup"><span data-stu-id="0c833-112">Open the project's application configuration file (app.config) and add the following connection string:</span></span>  
  
  
  
     <span data-ttu-id="0c833-113">如果您的專案沒有應用程式組態檔，您可以加入一個選取**加入新項目**從**專案**功能表上，選取**一般**類別目錄選取**應用程式組態檔**，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="0c833-113">If your project does not have an application configuration file, you can add one by selecting **Add New Item** from the **Project** menu, selecting the **General** category, selecting **Application Configuration File**, and then clicking **Add**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c833-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c833-114">See Also</span></span>  
 [<span data-ttu-id="0c833-115">快速入門</span><span class="sxs-lookup"><span data-stu-id="0c833-115">Quickstart</span></span>](http://msdn.microsoft.com/library/0bc534be-789f-4819-b9f6-76e51d961675)  
 [<span data-ttu-id="0c833-116">如何： 建立新的.edmx 檔案</span><span class="sxs-lookup"><span data-stu-id="0c833-116">How to: Create a New .edmx File</span></span>](http://msdn.microsoft.com/library/beb8189e-e51c-4051-839c-9902c224abf2)  
 [<span data-ttu-id="0c833-117">ADO.NET 實體資料模型工具</span><span class="sxs-lookup"><span data-stu-id="0c833-117">ADO.NET Entity Data Model  Tools</span></span>](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)
