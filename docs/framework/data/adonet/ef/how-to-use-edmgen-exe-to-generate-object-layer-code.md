---
title: HOW TO：使用 EdmGen.exe 產生物件層程式碼
ms.date: 03/30/2017
ms.assetid: c44d2ebe-f66f-42cb-9741-4a3f0c2dcffb
ms.openlocfilehash: b85bacff093c268cd35dca2ede36e6ceb74ca4d1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251411"
---
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a>作法：使用 EdmGen.exe 產生物件層程式碼
本主題說明如何使用 EDM 產生器[(edmgen.exe)](edm-generator-edmgen-exe.md)工具, 根據 csdl 檔案來產生物件層程式碼。  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>使用 EdmGen.exe 針對 Visual Basic 專案產生 School 模型的物件層程式碼  
  
1. 建立 School 資料庫。 如需詳細資訊, 請參閱[建立 School 範例資料庫](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100))。  
  
2. 產生 School 模型或取得 School.csdl 檔案。 如需詳細資訊，請參閱[如何：使用 Edmgen.exe 來產生模型和對應](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)檔。  
  
3. 在命令提示字元中，執行下列命令但不含分行符號：  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a>使用 EdmGen.exe 針對 C# 專案產生 School 模型的物件層程式碼  
  
1. 建立 School 資料庫。 如需詳細資訊, 請參閱[建立 School 範例資料庫](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100))。  
  
2. 產生 School 模型或取得 School.csdl 檔案。 如需詳細資訊，請參閱[如何：使用 Edmgen.exe 來產生模型和對應](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)檔。  
  
3. 在命令提示字元中，執行下列命令但不含分行符號：  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a>另請參閱

- [建立模型和對應](modeling-and-mapping.md)
- [如何：手動設定 Entity Framework 專案](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))
- [ADO.NET 實體資料模型工具](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [如何：預先產生視圖以改善查詢效能](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
- [如何：使用 Edmgen.exe 來產生模型和對應檔](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
