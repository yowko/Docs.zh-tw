---
title: "如何：使用 EdmGen.exe 產生物件層程式碼"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c44d2ebe-f66f-42cb-9741-4a3f0c2dcffb
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 394215b6e532013953fd1850ea8dbe973bdd960a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a>如何：使用 EdmGen.exe 產生物件層程式碼
本主題示範如何使用[EDM 產生器 (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md)產生物件層程式碼的工具依據.csdl 檔案。  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>使用 EdmGen.exe 針對 Visual Basic 專案產生 School 模型的物件層程式碼  
  
1.  建立 School 資料庫。 如需詳細資訊，請參閱[建立 School 範例資料庫](http://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0)。  
  
2.  產生 School 模型或取得 School.csdl 檔案。 如需詳細資訊，請參閱[How to： 使用 EdmGen.exe 產生模型和對應檔](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)。  
  
3.  在命令提示字元中，執行下列命令但不含分行符號：  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a>使用 EdmGen.exe 針對 C# 專案產生 School 模型的物件層程式碼  
  
1.  建立 School 資料庫。 如需詳細資訊，請參閱[建立 School 範例資料庫](http://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0)。  
  
2.  產生 School 模型或取得 School.csdl 檔案。 如需詳細資訊，請參閱[How to： 使用 EdmGen.exe 產生模型和對應檔](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)。  
  
3.  在命令提示字元中，執行下列命令但不含分行符號：  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a>請參閱  
 [建立模型和對應](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)  
 [如何： 手動設定 Entity Framework 專案](http://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)  
 [ADO.NET 實體資料模型工具](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)  
 [如何： 預先產生檢視，以改善查詢效能](http://msdn.microsoft.com/library/b18a9d16-e10b-4043-ba91-b632f85a2579)  
 [如何：使用 EdmGen.exe 產生模型和對應檔](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
