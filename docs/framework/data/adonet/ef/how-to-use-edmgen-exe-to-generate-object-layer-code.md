---
title: 作法：使用 EdmGen.exe 產生物件層程式碼
ms.date: 03/30/2017
ms.assetid: c44d2ebe-f66f-42cb-9741-4a3f0c2dcffb
ms.openlocfilehash: a243a588dcb6f7e7001de331cb9011a23ee2fdbe
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198219"
---
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a><span data-ttu-id="d6b29-102">作法：使用 EdmGen.exe 產生物件層程式碼</span><span class="sxs-lookup"><span data-stu-id="d6b29-102">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>

<span data-ttu-id="d6b29-103">本主題說明如何使用 EDM 產生器 [ ( # A0) ](edm-generator-edmgen-exe.md) 工具，根據 csdl 檔案產生物件層程式碼。</span><span class="sxs-lookup"><span data-stu-id="d6b29-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md) tool to generate object-layer code  based on the .csdl file.</span></span>  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a><span data-ttu-id="d6b29-104">使用 EdmGen.exe 針對 Visual Basic 專案產生 School 模型的物件層程式碼</span><span class="sxs-lookup"><span data-stu-id="d6b29-104">To generate object-layer code for the School model for a Visual Basic project using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="d6b29-105">建立 School 資料庫。</span><span class="sxs-lookup"><span data-stu-id="d6b29-105">Create the School database.</span></span> <span data-ttu-id="d6b29-106">如需詳細資訊，請參閱 [建立 School 範例資料庫](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="d6b29-106">For more information, see [Creating the School Sample Database](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="d6b29-107">產生 School 模型或取得 School.csdl 檔案。</span><span class="sxs-lookup"><span data-stu-id="d6b29-107">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="d6b29-108">如需詳細資訊，請參閱 [如何：使用 EdmGen.exe 產生模型和對應](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)檔。</span><span class="sxs-lookup"><span data-stu-id="d6b29-108">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="d6b29-109">在命令提示字元中，執行下列命令但不含分行符號：</span><span class="sxs-lookup"><span data-stu-id="d6b29-109">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a><span data-ttu-id="d6b29-110">使用 EdmGen.exe 針對 C# 專案產生 School 模型的物件層程式碼</span><span class="sxs-lookup"><span data-stu-id="d6b29-110">To generate object-layer code for the School model for a C# project using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="d6b29-111">建立 School 資料庫。</span><span class="sxs-lookup"><span data-stu-id="d6b29-111">Create the School database.</span></span> <span data-ttu-id="d6b29-112">如需詳細資訊，請參閱 [建立 School 範例資料庫](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="d6b29-112">For more information, see [Creating the School Sample Database](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="d6b29-113">產生 School 模型或取得 School.csdl 檔案。</span><span class="sxs-lookup"><span data-stu-id="d6b29-113">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="d6b29-114">如需詳細資訊，請參閱 [如何：使用 EdmGen.exe 產生模型和對應](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)檔。</span><span class="sxs-lookup"><span data-stu-id="d6b29-114">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="d6b29-115">在命令提示字元中，執行下列命令但不含分行符號：</span><span class="sxs-lookup"><span data-stu-id="d6b29-115">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d6b29-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6b29-116">See also</span></span>

- [<span data-ttu-id="d6b29-117">建立模型和對應</span><span class="sxs-lookup"><span data-stu-id="d6b29-117">Modeling and Mapping</span></span>](modeling-and-mapping.md)
- <span data-ttu-id="d6b29-118">[如何：手動設定 Entity Framework 專案](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d6b29-118">[How to: Manually Configure an Entity Framework Project](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span></span>
- <span data-ttu-id="d6b29-119">[ADO.NET 實體資料模型工具](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d6b29-119">[ADO.NET Entity Data Model  Tools](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
- <span data-ttu-id="d6b29-120">[如何：預先產生檢視以改善查詢效能](/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d6b29-120">[How to: Pre-Generate Views to Improve Query Performance](/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span></span>
- [<span data-ttu-id="d6b29-121">作法：使用 EdmGen.exe 產生模型和對應檔</span><span class="sxs-lookup"><span data-stu-id="d6b29-121">How to: Use EdmGen.exe to Generate the Model and Mapping Files</span></span>](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
