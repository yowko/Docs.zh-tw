---
title: 如何：使用 EdmGen.exe 產生物件層程式碼
ms.date: 03/30/2017
ms.assetid: c44d2ebe-f66f-42cb-9741-4a3f0c2dcffb
ms.openlocfilehash: 1dbd2e25d5f9795af4f80e079c6a0b807666743d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150554"
---
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a><span data-ttu-id="e5a12-102">如何：使用 EdmGen.exe 產生物件層程式碼</span><span class="sxs-lookup"><span data-stu-id="e5a12-102">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>
<span data-ttu-id="e5a12-103">本主題演示如何使用[EDM 產生器 （EdmGen.exe）](edm-generator-edmgen-exe.md)工具基於 .csdl 檔生成物件層代碼。</span><span class="sxs-lookup"><span data-stu-id="e5a12-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md) tool to generate object-layer code  based on the .csdl file.</span></span>  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a><span data-ttu-id="e5a12-104">使用 EdmGen.exe 針對 Visual Basic 專案產生 School 模型的物件層程式碼</span><span class="sxs-lookup"><span data-stu-id="e5a12-104">To generate object-layer code for the School model for a Visual Basic project using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="e5a12-105">建立 School 資料庫。</span><span class="sxs-lookup"><span data-stu-id="e5a12-105">Create the School database.</span></span> <span data-ttu-id="e5a12-106">有關詳細資訊，請參閱[創建學校示例資料庫](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="e5a12-106">For more information, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="e5a12-107">產生 School 模型或取得 School.csdl 檔案。</span><span class="sxs-lookup"><span data-stu-id="e5a12-107">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="e5a12-108">有關詳細資訊，請參閱[：使用 EdmGen.exe 生成模型和映射檔](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)。</span><span class="sxs-lookup"><span data-stu-id="e5a12-108">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="e5a12-109">在命令提示字元中，執行下列命令但不含分行符號：</span><span class="sxs-lookup"><span data-stu-id="e5a12-109">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a><span data-ttu-id="e5a12-110">使用 EdmGen.exe 針對 C# 專案產生 School 模型的物件層程式碼</span><span class="sxs-lookup"><span data-stu-id="e5a12-110">To generate object-layer code for the School model for a C# project using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="e5a12-111">建立 School 資料庫。</span><span class="sxs-lookup"><span data-stu-id="e5a12-111">Create the School database.</span></span> <span data-ttu-id="e5a12-112">有關詳細資訊，請參閱[創建學校示例資料庫](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="e5a12-112">For more information, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="e5a12-113">產生 School 模型或取得 School.csdl 檔案。</span><span class="sxs-lookup"><span data-stu-id="e5a12-113">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="e5a12-114">有關詳細資訊，請參閱[：使用 EdmGen.exe 生成模型和映射檔](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)。</span><span class="sxs-lookup"><span data-stu-id="e5a12-114">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="e5a12-115">在命令提示字元中，執行下列命令但不含分行符號：</span><span class="sxs-lookup"><span data-stu-id="e5a12-115">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e5a12-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5a12-116">See also</span></span>

- [<span data-ttu-id="e5a12-117">建立模型和對應</span><span class="sxs-lookup"><span data-stu-id="e5a12-117">Modeling and Mapping</span></span>](modeling-and-mapping.md)
- <span data-ttu-id="e5a12-118">[如何：手動設定 Entity Framework 專案](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e5a12-118">[How to: Manually Configure an Entity Framework Project](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span></span>
- <span data-ttu-id="e5a12-119">[ADO.NET 實體資料模型工具](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e5a12-119">[ADO.NET Entity Data Model  Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
- <span data-ttu-id="e5a12-120">[如何：預先產生檢視以改善查詢效能](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e5a12-120">[How to: Pre-Generate Views to Improve Query Performance](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span></span>
- [<span data-ttu-id="e5a12-121">如何：使用 EdmGen.exe 產生模型和對應檔</span><span class="sxs-lookup"><span data-stu-id="e5a12-121">How to: Use EdmGen.exe to Generate the Model and Mapping Files</span></span>](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
