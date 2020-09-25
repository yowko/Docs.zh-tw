---
description: -target (C# 編譯器選項)
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
ms.openlocfilehash: bcae4b64bdd2a939e35666a9068611b273c261da
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91188417"
---
# <a name="-target-c-compiler-options"></a>-target (C# 編譯器選項)

您可以用下列其中一種形式指定 **-target** 編譯器選項：  
  
 [-target:appcontainerexe](./target-appcontainerexe-compiler-option.md)  
 為 Windows 8. x 儲存區應用程式建立 .exe 檔。  
  
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
  
 除非您指定 **-target： module**，否則 **-target** 會使 .NET Framework 組件資訊清單放在輸出檔中。 如需詳細資訊，請參閱 [.net 中的元件](../../../standard/assembly/index.md) 和 [通用屬性](../attributes/global.md)。  
  
 編譯時，組件資訊清單會放在第一個 .exe 輸出檔，如果沒有 .exe 輸出檔，則會放在第一個 DLL 中。 例如，在下列命令列中，資訊清單會放在 `1.exe` 中：  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 編譯器在每次編譯時都只會建立一個組件資訊清單。 編譯中所有檔案的資訊會放入組件資訊清單中。 除了使用 **-target： module** 建立的所有輸出檔案，都可以包含組件資訊清單。 在命令列產生多個輸出檔時，只能建立一個組件資訊清單，而且它必須移至命令列上所指定的第一個輸出檔。 無論第一個輸出檔是 (**目標： exe**、 **-target： winexe**、 **-target： library** 或 **-target： module**) ，在相同編譯中產生的任何其他輸出檔都必須是模組 (**-target： module**) 。  
  
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
