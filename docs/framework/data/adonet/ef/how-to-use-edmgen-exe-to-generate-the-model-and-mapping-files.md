---
title: 如何：使用 EdmGen.exe 產生模型和對應檔
ms.date: 03/30/2017
ms.assetid: 40db462d-2fd2-4cc1-ad86-d280403e63fa
ms.openlocfilehash: 8eb7e0c19d775e516765b0e88f61789a9136e6e1
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467792"
---
# <a name="how-to-use-edmgenexe-to-generate-the-model-and-mapping-files"></a>如何：使用 EdmGen.exe 產生模型和對應檔
本主題示範如何使用 EDM 產生器 (EdmGen.exe) 工具依據 School 資料庫產生下列檔案：  
  
-   概念模型 (.csdl 檔)。  
  
-   儲存體模型 (.ssdl 檔)。  
  
-   概念模型和儲存模型之間的對應 (.msl 檔)。  
  
-   Visual Basic 或 C# 中的物件層程式碼。  
  
-   檢視檔案。  
  
 EdmGen.exe 工具使用 /mode:FullGeneration 產生以上所列檔案。 如需 EdmGen.exe 命令的詳細資訊，請參閱[EDM 產生器 (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md)。  
  
 如果您使用 EdmGen.exe 產生模型和對應檔時，您仍然需要設定 Visual Studio 專案，以使用[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 如何： 手動設定 Entity Framework 專案](https://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)。  
  
> [!NOTE]
>  EdmGen.exe 所產生的概念模型會包括資料庫中的所有物件。 如果您想要產生僅包含特定物件的概念模型，請使用 Entity Data Model 精靈。 如需詳細資訊，請參閱 <<c0> [ 如何： 使用 Entity Data Model 精靈](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d)。  
  
### <a name="to-generate-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>若要使用 EdmGen.exe 來產生 Visual Basic 專案的 School 模型  
  
1.  建立 School 資料庫。 如需詳細資訊，請參閱 <<c0> [ 建立 School 範例資料庫](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0)。  
  
2.  在命令提示字元中，執行下列命令但不含分行符號：  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:VB  
    ```  
  
### <a name="to-generate-the-school-model-for-a-c-project-using-edmgenexe"></a>若要使用 EdmGen.exe 來產生 C# 專案的 School 模型  
  
1.  建立 School 資料庫。 如需詳細資訊，請參閱 <<c0> [ 建立 School 範例資料庫](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0)。  
  
2.  在命令提示字元中，執行下列命令但不含分行符號：  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:CSharp  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [建立模型和對應](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)  
 [如何： 手動設定 Entity Framework 專案](https://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)  
 [如何： 預先產生檢視以改善查詢效能](https://msdn.microsoft.com/library/b18a9d16-e10b-4043-ba91-b632f85a2579)  
 [ADO.NET 實體資料模型工具](https://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)  
 [如何：使用 EdmGen.exe 驗證模型和對應檔](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)
