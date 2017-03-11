---
title: "/target:exe (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/exe"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "target compiler options [C#], /target:exe"
  - "/target compiler options [C#], /target:exe"
  - "-target compiler options [C#], /target:exe"
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
caps.latest.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 12
---
# /target:exe (C# Compiler Options)
**\/target:exe** 選項會讓編譯器建立可執行 \(EXE\) 的主控台應用程式。  
  
## 語法  
  
```  
/target:exe  
```  
  
## 備註  
 根據預設，**\/target:exe** 選項為作用中。  可執行檔會以 .exe 副檔名建立。  
  
 請使用 [\/target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) 建立可執行的 Windows 程式。  
  
 除非另外以 [\/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) 選項指定輸出檔名稱，否則將會以包含 [Main](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md) 方法的輸入檔名稱命名。  
  
 在命令列上指定時，直到下一個 **\/out** 或 **\/target:module** 選項的所有檔案，都是用來建立 .exe 檔案。  
  
 編譯成 .exe 的原始程式碼檔中只需要且只能有一個 **Main** 方法。  [\/main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) 編譯器選項可以在程式碼有一個以上具有 **Main** 方法的類別時，讓您指定含有 **Main** 方法的類別。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性**\] 頁面。  
  
2.  按一下 \[**應用程式**\] 屬性頁。  
  
3.  修改 \[**輸出類型**\] 屬性。  
  
 如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.OutputType%2A>。  
  
## 範例  
 以下命令行都會編譯 `in.cs` 並建立 `in.exe`：  
  
```  
csc /target:exe in.cs  
csc in.cs  
```  
  
## 請參閱  
 [\/target \(Specify Output File Format\)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)   
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)