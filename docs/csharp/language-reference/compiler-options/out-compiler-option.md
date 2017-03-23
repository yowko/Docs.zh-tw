---
title: "/out (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/out"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/out compiler option [C#]"
  - "out compiler option [C#]"
  - "-out compiler option [C#]"
ms.assetid: 70d91d01-7bd2-4aea-ba8b-4e9807e9caa5
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# /out (C# Compiler Options)
**\/out** 選項可以指定輸出檔名稱。  
  
## 語法  
  
```  
/out:filename  
```  
  
## Arguments  
 `filename`  
 編譯器建立的輸出檔名稱。  
  
## 備註  
 您可以在命令列上為您的編譯指定多個輸出檔，  編譯器可以在 **\/out** 選項後找到一個或多個原始程式碼檔。  然後，所有的原始程式碼檔就會編譯到 **\/out** 選項所指定的輸出檔。  
  
 請指定您要建立的檔案完整名稱和副檔名。  
  
 如果您未指定輸出檔名稱：  
  
-   .exe 的名稱將來自於包含 **Main** 方法的原始程式碼檔。  
  
-   .dll 檔或 .netmodule 檔的名稱將來自於第一個原始程式碼檔。  
  
 在同一個編譯裡，用來編譯某個輸出檔的原始程式碼檔，不能再使用於其他輸出檔的編譯。  
  
 在命令列編譯中產生多個輸出檔時，記得其中只有一個輸出檔可以是組件 \(Assembly\)，而且只有最先指定的輸出檔 \(使用 **\/out** 隱含或明確指定\) 可以是組件。  
  
 任何產生為編譯一部分的模組，都將與經由同樣編譯過程而產生的任何組件，產生檔案關聯。  使用 [ildasm.exe](../Topic/Ildasm.exe%20\(IL%20Disassembler\).md)，檢視組件資訊清單 \(Assembly Manifest\) 以查看關聯的檔案。  
  
 若要讓 exe 成為 friend 組件的目標，則需要 \/out 編譯器選項。  如需詳細資訊，請參閱[Friend 組件](../Topic/Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性**\] 頁面。  
  
2.  按一下 \[**應用程式**\] 屬性頁。  
  
3.  修改 \[**組件名稱**\] 屬性。  
  
     若要用程式設計方式設定這個編譯器選項︰<xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> 是唯讀屬性，由專案類型 \(exe、程式庫等\) 和組件名稱共同決定。  必須修改其中一個屬性或兩個屬性都修改，才能設定輸出檔名稱。  
  
## 範例  
 編譯 `t.cs` 並建立輸出檔 `t.exe`；同時建置 `t2.cs` 和建立模組輸出檔 `mymodule.netmodule`：  
  
```  
csc t.cs /out:mymodule.netmodule /target:module t2.cs  
```  
  
## 請參閱  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Friend 組件](../Topic/Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)   
 [如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)