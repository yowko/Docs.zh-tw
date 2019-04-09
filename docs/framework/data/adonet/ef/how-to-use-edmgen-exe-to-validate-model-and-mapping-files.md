---
title: HOW TO：使用 EdmGen.exe 驗證模型和對應檔
ms.date: 03/30/2017
ms.assetid: 2641906a-971a-4d0b-8aee-13fabc02a1cc
ms.openlocfilehash: 1981e293d634af451a7084ac519a97f1ad5b5fd6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076516"
---
# <a name="how-to-use-edmgenexe-to-validate-model-and-mapping-files"></a><span data-ttu-id="37c94-102">HOW TO：使用 EdmGen.exe 驗證模型和對應檔</span><span class="sxs-lookup"><span data-stu-id="37c94-102">How to: Use EdmGen.exe to Validate Model and Mapping Files</span></span>
<span data-ttu-id="37c94-103">本主題說明如何使用[EDM 產生器 (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md)工具來驗證模型和對應檔。</span><span class="sxs-lookup"><span data-stu-id="37c94-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) tool to validate the model and mapping files.</span></span> <span data-ttu-id="37c94-104">如需詳細資訊，請參閱 < [Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md)。</span><span class="sxs-lookup"><span data-stu-id="37c94-104">For more information, see [Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md).</span></span>  
  
### <a name="to-validate-the-school-model-using-edmgenexe"></a><span data-ttu-id="37c94-105">使用 EdmGen.exe 驗證 School 模型</span><span class="sxs-lookup"><span data-stu-id="37c94-105">To validate the School model using EdmGen.exe</span></span>  
  
1.  <span data-ttu-id="37c94-106">建立 School 資料庫。</span><span class="sxs-lookup"><span data-stu-id="37c94-106">Create the School database.</span></span> <span data-ttu-id="37c94-107">如需詳細資訊，請參閱 <<c0> [ 建立 School 範例資料庫](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="37c94-107">For more information, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2.  <span data-ttu-id="37c94-108">產生 School 模型。</span><span class="sxs-lookup"><span data-stu-id="37c94-108">Generate the School model.</span></span> <span data-ttu-id="37c94-109">如需詳細資訊，請參閱[如何：使用 EdmGen.exe 產生模型和對應檔](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)。</span><span class="sxs-lookup"><span data-stu-id="37c94-109">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3.  <span data-ttu-id="37c94-110">在命令提示字元中，執行下列命令但不含分行符號：</span><span class="sxs-lookup"><span data-stu-id="37c94-110">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:ValidateArtifacts /inssdl:.\School.ssdl /inmsl:.\School.msl /incsdl:.\School.csdl  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="37c94-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37c94-111">See also</span></span>

- [<span data-ttu-id="37c94-112">HOW TO：手動設定 Entity Framework 專案</span><span class="sxs-lookup"><span data-stu-id="37c94-112">How to: Manually Configure an Entity Framework Project</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))
- [<span data-ttu-id="37c94-113">ADO.NET 實體資料模型工具</span><span class="sxs-lookup"><span data-stu-id="37c94-113">ADO.NET Entity Data Model Tools</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [<span data-ttu-id="37c94-114">HOW TO：預先產生檢視以改善查詢效能</span><span class="sxs-lookup"><span data-stu-id="37c94-114">How to: Pre-Generate Views to Improve Query Performance</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
- [<span data-ttu-id="37c94-115">HOW TO：使用 EdmGen.exe 產生物件層程式碼</span><span class="sxs-lookup"><span data-stu-id="37c94-115">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md)
