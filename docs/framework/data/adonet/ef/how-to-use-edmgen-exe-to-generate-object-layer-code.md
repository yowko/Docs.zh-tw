---
title: HOW TO：使用 EdmGen.exe 產生物件層程式碼
ms.date: 03/30/2017
ms.assetid: c44d2ebe-f66f-42cb-9741-4a3f0c2dcffb
ms.openlocfilehash: 63542866441cb347362e64b08b5de11bde19d50b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654564"
---
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a>HOW TO：使用 EdmGen.exe 產生物件層程式碼
本主題說明如何使用[EDM 產生器 (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) .csdl 檔案為基礎的工具來產生物件層程式碼。  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>使用 EdmGen.exe 針對 Visual Basic 專案產生 School 模型的物件層程式碼  
  
1.  建立 School 資料庫。 如需詳細資訊，請參閱 <<c0> [ 建立 School 範例資料庫](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0)。  
  
2.  產生 School 模型或取得 School.csdl 檔案。 如需詳細資訊，請參閱[＜How to：使用 EdmGen.exe 產生模型和對應檔](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)。  
  
3.  在命令提示字元中，執行下列命令但不含分行符號：  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a>使用 EdmGen.exe 針對 C# 專案產生 School 模型的物件層程式碼  
  
1.  建立 School 資料庫。 如需詳細資訊，請參閱 <<c0> [ 建立 School 範例資料庫](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0)。  
  
2.  產生 School 模型或取得 School.csdl 檔案。 如需詳細資訊，請參閱[＜How to：使用 EdmGen.exe 產生模型和對應檔](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)。  
  
3.  在命令提示字元中，執行下列命令但不含分行符號：  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a>另請參閱
- [建立模型和對應](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)
- [如何：手動設定 Entity Framework 專案](https://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)
- [ADO.NET 實體資料模型工具](https://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)
- [如何：預先產生檢視以改善查詢效能](https://msdn.microsoft.com/library/b18a9d16-e10b-4043-ba91-b632f85a2579)
- [如何：使用 EdmGen.exe 產生模型和對應檔](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
