---
title: "/moduleassemblyname (C# Compiler Option) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/moduleassemblyname"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "moduleassemblyname compiler option [C#]"
  - "/moduleassemblyname compiler option [C#]"
  - ".moduleassemblyname compiler option [C#]"
ms.assetid: d464d9b9-f18d-423b-95e9-66c7878fd53a
caps.latest.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 10
---
# /moduleassemblyname (C# Compiler Option)
指定組件，.netmodule 可存取該組件的非公開類型。  
  
## 語法  
  
```  
/moduleassemblyname:assembly_name  
```  
  
## Arguments  
 `assembly_name`  
 其非公用型別 .netmodule 可以存取的組件名稱。  
  
## 備註  
 在建置 .netmodule時應該使用**\/moduleassemblyname** ，且下列條件為 true 的位置：  
  
-   .netmodule 需要存取現有組件中的非公用型別。  
  
-   您知道 .netmodule 將建置在其中的組件名稱。  
  
-   現存組件已將 friend 組件的存取權授與給 .netmodule將建置在其中的組件。  
  
 如需組件 .netmodule的詳細資訊，請參閱 [\/target:module \(Create Module to Add to Assembly\)](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md)。  
  
 如需 friend 組件的詳細資訊，請參閱 [Friend 組件](../Topic/Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)。  
  
 這個選項在開發環境內無法使用；只有從命令列進行編譯時才能使用。  
  
 在 Visual Studio 中無法使用這個編譯器選項，而且無法利用程式設計的方式變更它。  
  
## 範例  
 這個範例會使用私用型別建置組件，並且讓 friend 組件存取名為 csman\_an\_assembly 的組件。  
  
```  
// moduleassemblyname_1.cs  
// compile with: /target:library  
using System;  
using System.Runtime.CompilerServices;  
  
[assembly:InternalsVisibleTo ("csman_an_assembly")]  
  
class An_Internal_Class   
{  
    public void Test()   
    {   
        Console.WriteLine("An_Internal_Class.Test called");   
    }  
}  
```  
  
## 範例  
 此範例組件一個會存取組件 moduleassemblyname\_1.dll 中非公用型別的 .netmodule。  透過知道 .netmodule 將建置到名為 csman\_an\_assembly的組件，我們可以指定 **\/moduleassemblyname**，讓 .netmodule 在授與 csman\_an\_assembly 的 friend 組件存取權限的組件中存取非公用型別。  
  
```  
// moduleassemblyname_2.cs  
// compile with: /moduleassemblyname:csman_an_assembly /target:module /reference:moduleassemblyname_1.dll  
class B {  
    public void Test() {  
        An_Internal_Class x = new An_Internal_Class();  
        x.Test();  
    }  
}  
```  
  
## 範例  
 這個程式碼範例會參考之前建置的組件以及 .netmodule，來建置組件 csman\_an\_assembly。  
  
```  
// csman_an_assembly.cs  
// compile with: /addmodule:moduleassemblyname_2.netmodule /reference:moduleassemblyname_1.dll  
class A {  
    public static void Main() {  
        B bb = new B();  
        bb.Test();  
    }  
}  
```  
  
  **呼叫的 An\_Internal\_Class.Test**   
## 請參閱  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)