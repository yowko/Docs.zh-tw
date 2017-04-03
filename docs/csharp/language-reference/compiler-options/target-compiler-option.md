---
title: "-target (C# 編譯器選項) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /target
dev_langs:
- CSharp
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 615a0e2993dc78919008e8f9245504a486e2fb77
ms.lasthandoff: 03/13/2017

---
# <a name="target-c-compiler-options"></a>/target (C# 編譯器選項)
您可以使用四種形式之一來指定**/target** 編譯器選項︰  
  
 [/target:appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
 建立 [!INCLUDE[win8_appname_long](../../../csharp/includes/win8_appname_long_md.md)]應用程式的 .exe 檔。  
  
 [/target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md)  
 建立 .exe 檔案。  
  
 [/target:library](../../../csharp/language-reference/compiler-options/target-library-compiler-option.md)  
 建立程式碼程式庫。  
  
 [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md)  
 建立模組。  
  
 [/target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
 建立 Windows 程式。  
  
 [/target:winmdobj](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
 建立中繼 .winmdobj 檔案。  
  
 除非您指定 **/target:module**，否則 **/target** 會將 .NET Framework 組件資訊清單放入輸出檔中。 如需詳細資訊，請參閱 [Common Language Runtime 中的組件](https://msdn.microsoft.com/library/k3677y81)和 [Common Attributes](http://msdn.microsoft.com/library/2f48a7ec-9683-4899-a1d2-a08be8fc558b) (常見屬性)。  
  
 編譯時，組件資訊清單會放在第一個 .exe 輸出檔，如果沒有 .exe 輸出檔，則會放在第一個 DLL 中。 例如，在下列命令列中，資訊清單會放在 `1.exe` 中：  
  
```  
csc /out:1.exe t1.cs /out:2.netmodule t2.cs  
```  
  
 編譯器在每次編譯時都只會建立一個組件資訊清單。 編譯中所有檔案的資訊會放入組件資訊清單中。 使用 **/target:module** 所建立的輸出檔以外的所有輸出檔都可以包含組件資訊清單。 在命令列產生多個輸出檔時，只能建立一個組件資訊清單，而且它必須移至命令列上所指定的第一個輸出檔。 不論第一個輸出檔為 (**/target:exe**、**/target:winexe**、**/target:library** 還是 **/target:module**)，在相同編譯中產生的任何其他輸出檔都必須是模組 (**/target:module**)。  
  
 如果您建立組件，則可以使用 <xref:System.CLSCompliantAttribute> 屬性指出所有或部分程式碼符合 CLS 標準。  
  
```  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 如需如何以程式設計方式設定此編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.OutputType%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)   
 [如何：修改專案屬性和組態設定](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [/subsystemversion (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)
