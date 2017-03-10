---
title: "@ (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "@"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "response files, specifying for compilation [C#]"
  - "@ compiler option"
ms.assetid: dda4fa9f-a02c-400f-8b6a-d58834e13d7f
caps.latest.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 9
---
# @ (C# Compiler Options)
@ 選項讓您指定包含編譯器選項和原始程式檔以供編譯的檔案。  
  
## 語法  
  
```  
@response_file  
```  
  
## 引數  
 `response_file`  
 列出編譯器選項或原始程式碼檔以供編譯的檔案。  
  
## 備註  
 這些編譯器選項和原始程式碼檔將由編譯器處理，就如同在命令列上指定一般。  
  
 若要在編譯中指定一個以上的回應檔，請指定多個回應檔選項。  例如：  
  
```  
@file1.rsp @file2.rsp  
```  
  
 在回應檔中，數個編譯器選項和原始程式碼檔可以出現在同一行中。  然而單一編譯器選項規格則必須出現在一行內 \(不能擴展至多行\)。  回應檔可以有以 \# 符號為開頭的註解。  
  
 從回應檔內指定編譯器選項，就如同從命令列中發出這些命令一樣。  如需詳細資訊，請參閱[從命令列建置](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)。  
  
 編譯器會處理遇到的命令選項。  因此，命令列引數可以覆寫先前在回應檔中列出的選項。  反之亦然，回應檔的選項也可以覆寫先前在命令列或其他回應檔中列出的選項。  
  
 C\# 會提供與 csc.exe 檔位在相同目錄中的 csc.rsp 檔。  如需 csc.rsp 的詳細資訊，請參閱 [\/noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md)。  
  
 這個編譯器選項無法在 Visual Studio 開發環境中設定，也不能以程式設計的方式變更。  
  
## 範例  
 下面是從範例回應檔中擷取的幾行：  
  
```  
# build the first output file  
/target:exe /out:MyExe.exe source1.cs source2.cs  
```  
  
## 請參閱  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)