---
title: 如何：使用 EdmGen.exe 驗證模型和對應檔
ms.date: 03/30/2017
ms.assetid: 2641906a-971a-4d0b-8aee-13fabc02a1cc
ms.openlocfilehash: 197af6ae86de4057b864ef211c36f19aad83b003
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-use-edmgenexe-to-validate-model-and-mapping-files"></a><span data-ttu-id="613f2-102">如何：使用 EdmGen.exe 驗證模型和對應檔</span><span class="sxs-lookup"><span data-stu-id="613f2-102">How to: Use EdmGen.exe to Validate Model and Mapping Files</span></span>
<span data-ttu-id="613f2-103">本主題示範如何使用[EDM 產生器 (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md)工具來驗證模型和對應檔。</span><span class="sxs-lookup"><span data-stu-id="613f2-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) tool to validate the model and mapping files.</span></span> <span data-ttu-id="613f2-104">如需詳細資訊，請參閱[實體資料模型](../../../../../docs/framework/data/adonet/entity-data-model.md)。</span><span class="sxs-lookup"><span data-stu-id="613f2-104">For more information, see [Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md).</span></span>  
  
### <a name="to-validate-the-school-model-using-edmgenexe"></a><span data-ttu-id="613f2-105">使用 EdmGen.exe 驗證 School 模型</span><span class="sxs-lookup"><span data-stu-id="613f2-105">To validate the School model using EdmGen.exe</span></span>  
  
1.  <span data-ttu-id="613f2-106">建立 School 資料庫。</span><span class="sxs-lookup"><span data-stu-id="613f2-106">Create the School database.</span></span> <span data-ttu-id="613f2-107">如需詳細資訊，請參閱[建立 School 範例資料庫](http://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0)。</span><span class="sxs-lookup"><span data-stu-id="613f2-107">For more information, see [Creating the School Sample Database](http://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).</span></span>  
  
2.  <span data-ttu-id="613f2-108">產生 School 模型。</span><span class="sxs-lookup"><span data-stu-id="613f2-108">Generate the School model.</span></span> <span data-ttu-id="613f2-109">如需詳細資訊，請參閱[How to： 使用 EdmGen.exe 產生模型和對應檔](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)。</span><span class="sxs-lookup"><span data-stu-id="613f2-109">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3.  <span data-ttu-id="613f2-110">在命令提示字元中，執行下列命令但不含分行符號：</span><span class="sxs-lookup"><span data-stu-id="613f2-110">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:ValidateArtifacts /inssdl:.\School.ssdl /inmsl:.\School.msl /incsdl:.\School.csdl  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="613f2-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="613f2-111">See Also</span></span>  
 [<span data-ttu-id="613f2-112">如何： 手動設定 Entity Framework 專案</span><span class="sxs-lookup"><span data-stu-id="613f2-112">How to: Manually Configure an Entity Framework Project</span></span>](http://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)  
 [<span data-ttu-id="613f2-113">ADO.NET 實體資料模型工具</span><span class="sxs-lookup"><span data-stu-id="613f2-113">ADO.NET Entity Data Model  Tools</span></span>](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)  
 [<span data-ttu-id="613f2-114">如何： 預先產生檢視，以改善查詢效能</span><span class="sxs-lookup"><span data-stu-id="613f2-114">How to: Pre-Generate Views to Improve Query Performance</span></span>](http://msdn.microsoft.com/library/b18a9d16-e10b-4043-ba91-b632f85a2579)  
 [<span data-ttu-id="613f2-115">如何：使用 EdmGen.exe 產生物件層程式碼</span><span class="sxs-lookup"><span data-stu-id="613f2-115">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md)
