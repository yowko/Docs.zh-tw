---
title: "-target (C# 編譯器選項)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /target
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 44dd99ef834f98a1a918c659d3057f8f6f91805a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="-target-c-compiler-options"></a>-target (C# 編譯器選項)
您可以使用四種形式之一來指定 **-target** 編譯器選項︰  
  
 [-target:appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
 建立 [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)]應用程式的 .exe 檔。  
  
 [-target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md)  
 建立 .exe 檔案。  
  
 [-target:library](../../../csharp/language-reference/compiler-options/target-library-compiler-option.md)  
 建立程式碼程式庫。  
  
 [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md)  
 建立模組。  
  
 [-target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
 建立 Windows 程式。  
  
 [-target:winmdobj](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
 建立中繼 .winmdobj 檔案。  
  
 除非您指定 **-target:module**，否則 **-target** 會將 .NET Framework 組件資訊清單放入輸出檔案中。 如需詳細資訊，請參閱 [Common Language Runtime 中的組件](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md)和 [Common Attributes](../../programming-guide/concepts/attributes/common-attributes.md) (常見屬性)。  
  
 編譯時，組件資訊清單會放在第一個 .exe 輸出檔，如果沒有 .exe 輸出檔，則會放在第一個 DLL 中。 例如，在下列命令列中，資訊清單會放在 `1.exe` 中：  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 編譯器在每次編譯時都只會建立一個組件資訊清單。 編譯中所有檔案的資訊會放入組件資訊清單中。 使用 **-target:module** 所建立的輸出檔案以外的所有輸出檔案都可以包含組件資訊清單。 在命令列產生多個輸出檔時，只能建立一個組件資訊清單，而且它必須移至命令列上所指定的第一個輸出檔。 不論第一個輸出檔案為 (**-target:exe**、**-target:winexe**、**-target:library** 還是 **-target:module**)，在相同編譯中產生的任何其他輸出檔案都必須是模組 (**-target:module**)。  
  
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
  
## <a name="see-also"></a>請參閱  
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)  
 [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)  
 [-subsystemversion (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)
