---
title: HOW TO：使用 EdmGen.exe 產生物件層程式碼
ms.date: 03/30/2017
ms.assetid: c44d2ebe-f66f-42cb-9741-4a3f0c2dcffb
ms.openlocfilehash: 04b35dbb5e487e573a2adfff196b79e10afdfb61
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59188224"
---
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a><span data-ttu-id="7c454-102">HOW TO：使用 EdmGen.exe 產生物件層程式碼</span><span class="sxs-lookup"><span data-stu-id="7c454-102">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>
<span data-ttu-id="7c454-103">本主題說明如何使用[EDM 產生器 (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) .csdl 檔案為基礎的工具來產生物件層程式碼。</span><span class="sxs-lookup"><span data-stu-id="7c454-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) tool to generate object-layer code  based on the .csdl file.</span></span>  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a><span data-ttu-id="7c454-104">使用 EdmGen.exe 針對 Visual Basic 專案產生 School 模型的物件層程式碼</span><span class="sxs-lookup"><span data-stu-id="7c454-104">To generate object-layer code for the School model for a Visual Basic project using EdmGen.exe</span></span>  
  
1.  <span data-ttu-id="7c454-105">建立 School 資料庫。</span><span class="sxs-lookup"><span data-stu-id="7c454-105">Create the School database.</span></span> <span data-ttu-id="7c454-106">如需詳細資訊，請參閱 <<c0> [ 建立 School 範例資料庫](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="7c454-106">For more information, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2.  <span data-ttu-id="7c454-107">產生 School 模型或取得 School.csdl 檔案。</span><span class="sxs-lookup"><span data-stu-id="7c454-107">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="7c454-108">如需詳細資訊，請參閱[如何：使用 EdmGen.exe 產生模型和對應檔](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)。</span><span class="sxs-lookup"><span data-stu-id="7c454-108">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3.  <span data-ttu-id="7c454-109">在命令提示字元中，執行下列命令但不含分行符號：</span><span class="sxs-lookup"><span data-stu-id="7c454-109">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a><span data-ttu-id="7c454-110">使用 EdmGen.exe 針對 C# 專案產生 School 模型的物件層程式碼</span><span class="sxs-lookup"><span data-stu-id="7c454-110">To generate object-layer code for the School model for a C# project using EdmGen.exe</span></span>  
  
1.  <span data-ttu-id="7c454-111">建立 School 資料庫。</span><span class="sxs-lookup"><span data-stu-id="7c454-111">Create the School database.</span></span> <span data-ttu-id="7c454-112">如需詳細資訊，請參閱 <<c0> [ 建立 School 範例資料庫](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="7c454-112">For more information, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2.  <span data-ttu-id="7c454-113">產生 School 模型或取得 School.csdl 檔案。</span><span class="sxs-lookup"><span data-stu-id="7c454-113">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="7c454-114">如需詳細資訊，請參閱[如何：使用 EdmGen.exe 產生模型和對應檔](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)。</span><span class="sxs-lookup"><span data-stu-id="7c454-114">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3.  <span data-ttu-id="7c454-115">在命令提示字元中，執行下列命令但不含分行符號：</span><span class="sxs-lookup"><span data-stu-id="7c454-115">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7c454-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c454-116">See also</span></span>

- [<span data-ttu-id="7c454-117">建立模型和對應</span><span class="sxs-lookup"><span data-stu-id="7c454-117">Modeling and Mapping</span></span>](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)
- [<span data-ttu-id="7c454-118">HOW TO：手動設定 Entity Framework 專案</span><span class="sxs-lookup"><span data-stu-id="7c454-118">How to: Manually Configure an Entity Framework Project</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))
- [<span data-ttu-id="7c454-119">ADO.NET 實體資料模型工具</span><span class="sxs-lookup"><span data-stu-id="7c454-119">ADO.NET Entity Data Model  Tools</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [<span data-ttu-id="7c454-120">HOW TO：預先產生檢視以改善查詢效能</span><span class="sxs-lookup"><span data-stu-id="7c454-120">How to: Pre-Generate Views to Improve Query Performance</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
- [<span data-ttu-id="7c454-121">HOW TO：使用 EdmGen.exe 產生模型和對應檔</span><span class="sxs-lookup"><span data-stu-id="7c454-121">How to: Use EdmGen.exe to Generate the Model and Mapping Files</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
