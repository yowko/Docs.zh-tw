---
title: HOW TO：使用 EdmGen.exe 驗證模型和對應檔
ms.date: 03/30/2017
ms.assetid: 2641906a-971a-4d0b-8aee-13fabc02a1cc
ms.openlocfilehash: 87150aee8eac6a594b18b77230889c1208003dde
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566355"
---
# <a name="how-to-use-edmgenexe-to-validate-model-and-mapping-files"></a>HOW TO：使用 EdmGen.exe 驗證模型和對應檔
本主題說明如何使用[EDM 產生器 (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md)工具來驗證模型和對應檔。 如需詳細資訊，請參閱 < [Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md)。  
  
### <a name="to-validate-the-school-model-using-edmgenexe"></a>使用 EdmGen.exe 驗證 School 模型  
  
1.  建立 School 資料庫。 如需詳細資訊，請參閱 <<c0> [ 建立 School 範例資料庫](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0)。  
  
2.  產生 School 模型。 如需詳細資訊，請參閱[＜How to：使用 EdmGen.exe 產生模型和對應檔](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)。  
  
3.  在命令提示字元中，執行下列命令但不含分行符號：  
  
    ```console
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:ValidateArtifacts /inssdl:.\School.ssdl /inmsl:.\School.msl /incsdl:.\School.csdl  
    ```  
  
## <a name="see-also"></a>另請參閱
- [如何：手動設定 Entity Framework 專案](https://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)
- [ADO.NET 實體資料模型工具](https://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)
- [如何：預先產生檢視以改善查詢效能](https://msdn.microsoft.com/library/b18a9d16-e10b-4043-ba91-b632f85a2579)
- [如何：使用 EdmGen.exe 產生物件層程式碼](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md)
