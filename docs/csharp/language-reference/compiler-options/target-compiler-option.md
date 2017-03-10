---
title: "/target (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/target"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "target compiler options [C#]"
  - "/target compiler options [C#]"
  - "assemblies [C#], compiling"
  - "-target compiler options [C#]"
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
caps.latest.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 22
---
# /target (C# Compiler Options)
**\/target** 編譯器選項可以用下列四種格式中的任何一種指定：  
  
 [\/target:appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
 建立 [!INCLUDE[win8_appname_long](../../../csharp/includes/win8-appname-long-md.md)] 應用程式的 .exe 檔。  
  
 [\/target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md)  
 建立 .exe 檔。  
  
 [\/target:library](../../../csharp/language-reference/compiler-options/target-library-compiler-option.md)  
 建立程式碼程式庫。  
  
 [\/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md)  
 建立模組。  
  
 [\/target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
 建立 Windows 程式。  
  
 [\/target:winmdobj](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
 建立一個中繼 .winmdobj 檔案。  
  
 除非您指定的是 **\/target:module**，否則 **\/target** 會將 .NET Framework 組件資訊清單置於輸出檔。  如需詳細資訊，請參閱 [Common Language Runtime 中的組件](../Topic/Assemblies%20in%20the%20Common%20Language%20Runtime.md)和[常見屬性](../Topic/Common%20Attributes%20\(C%23%20and%20Visual%20Basic\).md)。  
  
 如果您沒有指定 .exe 輸出檔，組件資訊清單會置於編譯中的第一個 .exe 輸出檔或第一個 DLL。  例如，下列命令列會將資訊清單檔置於 `1.exe`：  
  
```  
csc /out:1.exe t1.cs /out:2.netmodule t2.cs  
```  
  
 編譯器每次編譯只建立一個組件資訊清單。  編譯的所有檔案資訊都放置在組件資訊清單中。  除了以 **\/target:module** 所建立的輸出檔之外，所有的輸出檔都可以包含一個組件資訊清單。  當命令列上產生多個輸出檔時，此時只能建立一個組件，而且這個組件必須進入該命令列指定的第一個輸出檔。  不論第一個輸出檔為何 \(**\/target:exe**、**\/target:winexe**、**\/target:library** 或 **\/target:module**\)，相同編譯中產生的任何其他輸出檔都必須是模組 \(**\/target:module**\)。  
  
 如果您建立了組件，便可使用 <xref:System.CLSCompliantAttribute> 屬性將所有或部分程式碼指定為符合 CLS。  
  
```  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 如需以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.OutputType%2A>。  
  
## 請參閱  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [\/subsystemversion \(Specify minimum subsystem version\)](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)