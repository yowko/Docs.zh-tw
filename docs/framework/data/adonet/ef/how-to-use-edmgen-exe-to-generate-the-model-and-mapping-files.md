---
title: "如何：使用 EdmGen.exe 產生模型和對應檔"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40db462d-2fd2-4cc1-ad86-d280403e63fa
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 741da2e7f69d5f8fa54f07046d88fec9cf722dbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-edmgenexe-to-generate-the-model-and-mapping-files"></a>如何：使用 EdmGen.exe 產生模型和對應檔
本主題示範如何使用 EDM 產生器 (EdmGen.exe) 工具依據 School 資料庫產生下列檔案：  
  
-   概念模型 (.csdl 檔)。  
  
-   儲存體模型 (.ssdl 檔)。  
  
-   概念模型和儲存模型之間的對應 (.msl 檔)。  
  
-   Visual Basic 或 C# 中的物件層程式碼。  
  
-   檢視檔案。  
  
 EdmGen.exe 工具使用 /mode:FullGeneration 產生以上所列檔案。 如需 EdmGen.exe 命令的詳細資訊，請參閱[EDM 產生器 (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md)。  
  
 如果使用 EdmGen.exe 產生模型和對應檔，仍然必須將 [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] 專案設定成使用 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]。 如需詳細資訊，請參閱[How to： 手動設定 Entity Framework 專案](http://msdn.microsoft.com/en-us/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)。  
  
> [!NOTE]
>  EdmGen.exe 所產生的概念模型會包括資料庫中的所有物件。 如果您想要產生僅包含特定物件的概念模型，請使用 Entity Data Model 精靈。 如需詳細資訊，請參閱[How to： 使用實體資料模型精靈](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d)。  
  
### <a name="to-generate-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>若要使用 EdmGen.exe 來產生 Visual Basic 專案的 School 模型  
  
1.  建立 School 資料庫。 如需詳細資訊，請參閱[建立 School 範例資料庫](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0)。  
  
2.  在命令提示字元中，執行下列命令但不含分行符號：  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:VB  
    ```  
  
### <a name="to-generate-the-school-model-for-a-c-project-using-edmgenexe"></a>若要使用 EdmGen.exe 來產生 C# 專案的 School 模型  
  
1.  建立 School 資料庫。 如需詳細資訊，請參閱[建立 School 範例資料庫](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0)。  
  
2.  在命令提示字元中，執行下列命令但不含分行符號：  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:CSharp  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [建立模型和對應](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)  
 [如何： 手動設定 Entity Framework 專案](http://msdn.microsoft.com/en-us/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)  
 [如何： 預先產生檢視，以改善查詢效能](http://msdn.microsoft.com/en-us/b18a9d16-e10b-4043-ba91-b632f85a2579)  
 [ADO.NET 實體資料模型工具](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)  
 [如何： 使用 EdmGen.exe 驗證模型和對應檔](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)
