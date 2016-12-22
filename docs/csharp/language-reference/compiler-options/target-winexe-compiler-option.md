---
title: "/target:winexe (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/target:winexe"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/target compiler options [C#], /target:winexe"
  - "-target compiler options [C#], /target:winexe"
  - "target compiler options [C#], /target:winexe"
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /target:winexe (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

**\/target:winexe** 選項會讓編譯器建立可執行 \(EXE\) 的 Windows 程式。  
  
## 語法  
  
```  
/target:winexe  
```  
  
## 備註  
 可執行檔會以 .exe 副檔名建立。  Windows 程式會從 Services Framework 類別庫 \(Class Library\) 或以 Win32 API 為使用者提供介面。  
  
 使用 [\/target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md) 建立主控台應用程式。  
  
 除非另外以 [\/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) 選項指定輸出檔名稱，否則將會以包含 [Main](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md) 方法的輸入檔名稱命名。  
  
 在命令列上指定時，所有原始程式檔都會用來建立 Windows 程式，直到使用下一個 **\/out** 或 [\/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) 選項為止。  
  
 編譯成 .exe 的原始程式碼檔中只需要且只能有一個 **Main** 方法。  [\/main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) 選項可以在程式碼有一個以上具有 **Main** 方法的類別時，讓您指定哪一個類別含有 **Main** 方法。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性**\] 頁面。  
  
2.  按一下 \[**應用程式**\] 屬性頁。  
  
3.  修改 \[**輸出類型**\] 屬性。  
  
 如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.OutputType%2A>。  
  
## 範例  
 將 `in.cs` 編譯成 Windows 程式：  
  
```  
csc /target:winexe in.cs  
```  
  
## 請參閱  
 [\/target \(Specify Output File Format\)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)   
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)