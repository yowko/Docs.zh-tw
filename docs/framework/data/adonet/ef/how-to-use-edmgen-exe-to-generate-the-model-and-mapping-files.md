---
title: 如何：使用 EdmGen.exe 產生模型和對應檔
ms.date: 03/30/2017
ms.assetid: 40db462d-2fd2-4cc1-ad86-d280403e63fa
ms.openlocfilehash: ee8297c0833378b2b44800355b47db9caa2dc7fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150505"
---
# <a name="how-to-use-edmgenexe-to-generate-the-model-and-mapping-files"></a>如何：使用 EdmGen.exe 產生模型和對應檔
本主題示範如何使用 EDM 產生器 (EdmGen.exe) 工具依據 School 資料庫產生下列檔案：  
  
- 概念模型 (.csdl 檔)。  
  
- 儲存體模型 (.ssdl 檔)。  
  
- 概念模型和儲存模型之間的對應 (.msl 檔)。  
  
- Visual Basic 或 C# 中的物件層程式碼。  
  
- 檢視檔案。  
  
 EdmGen.exe 工具使用 /mode:FullGeneration 產生以上所列檔案。 有關 EdmGen.exe 命令的詳細資訊，請參閱[EDM 產生器 （EdmGen.exe）。](edm-generator-edmgen-exe.md)  
  
 如果使用 EdmGen.exe 生成模型和映射檔，您仍然需要將 Visual Studio 專案配置為使用實體框架。 有關詳細資訊，請參閱[如何：手動設定實體框架專案](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))。  
  
> [!NOTE]
> EdmGen.exe 所產生的概念模型會包括資料庫中的所有物件。 如果您想要產生僅包含特定物件的概念模型，請使用 Entity Data Model 精靈。 有關詳細資訊，請參閱[：使用實體資料模型嚮導](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))。  
  
### <a name="to-generate-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>若要使用 EdmGen.exe 來產生 Visual Basic 專案的 School 模型  
  
1. 建立 School 資料庫。 有關詳細資訊，請參閱[創建學校示例資料庫](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100))。  
  
2. 在命令提示字元中，執行下列命令但不含分行符號：  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:VB  
    ```  
  
### <a name="to-generate-the-school-model-for-a-c-project-using-edmgenexe"></a>若要使用 EdmGen.exe 來產生 C# 專案的 School 模型  
  
1. 建立 School 資料庫。 有關詳細資訊，請參閱[創建學校示例資料庫](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100))。  
  
2. 在命令提示字元中，執行下列命令但不含分行符號：  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:CSharp  
    ```  
  
## <a name="see-also"></a>另請參閱

- [建立模型和對應](modeling-and-mapping.md)
- [如何：手動設定 Entity Framework 專案](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))
- [如何：預先產生檢視以改善查詢效能](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
- [ADO.NET實體資料模型工具](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [如何：使用 EdmGen.exe 驗證模型和對應檔](how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)
