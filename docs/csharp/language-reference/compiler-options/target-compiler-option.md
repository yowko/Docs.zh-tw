---
title: -target (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /target
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
ms.openlocfilehash: ea5481810e629d911c4d5aba62e60c98d0783f34
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644350"
---
# <a name="-target-c-compiler-options"></a>-target (C# 編譯器選項)
**目標**編譯器選項可以以以下四種形式之一指定:  
  
 [-target:appcontainerexe](./target-appcontainerexe-compiler-option.md)  
 為 Windows 8.x 應用商店應用創建 .exe 檔。  
  
 [-target:exe](./target-exe-compiler-option.md)  
 建立 .exe 檔案。  
  
 [-target:library](./target-library-compiler-option.md)  
 建立程式碼程式庫。  
  
 [-target:module](./target-module-compiler-option.md)  
 建立模組。  
  
 [-target:winexe](./target-winexe-compiler-option.md)  
 建立 Windows 程式。  
  
 [-target:winmdobj](./target-winmdobj-compiler-option.md)  
 建立中繼 .winmdobj 檔案。  
  
 除非指定 **-目標:模組** **,-目標**會導致將 .NET 框架程式集清單放置在輸出檔中。 有關詳細資訊,請參閱[.NET](../../../standard/assembly/index.md)中的程式集和[通用屬性](../attributes/global.md)。  
  
 編譯時，組件資訊清單會放在第一個 .exe 輸出檔，如果沒有 .exe 輸出檔，則會放在第一個 DLL 中。 例如，在下列命令列中，資訊清單會放在 `1.exe` 中：  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 編譯器在每次編譯時都只會建立一個組件資訊清單。 編譯中所有檔案的資訊會放入組件資訊清單中。 除使用 **-target:模組**創建的輸出檔外,所有輸出檔都可以包含程式集清單。 在命令列產生多個輸出檔時，只能建立一個組件資訊清單，而且它必須移至命令列上所指定的第一個輸出檔。 無論第一個輸出檔是什麼 **(-目標:exe,-****目標:winexe,****目標:庫**或 **-目標:模組**),在同一編譯中生成的任何其他輸出檔都必須是模組 **(-目標:模組**)。  
  
 如果您建立組件，則可以使用 <xref:System.CLSCompliantAttribute> 屬性指出所有或部分程式碼符合 CLS 標準。  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 如需以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.OutputType%2A>。  
  
## <a name="see-also"></a>另請參閱

- [C# 編譯器選項](./index.md)
- [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)
- [-subsystemversion (C# 編譯器選項)](./subsystemversion-compiler-option.md)
