---
title: "/optimize (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/optimize"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/optimize compiler option [C#]"
  - "-o compiler option [C#]"
  - "optimize compiler option [C#]"
  - "/o compiler option [C#]"
  - "-optimize compiler option [C#]"
  - "compiler optimization [C#]"
  - "o compiler option [C#]"
ms.assetid: 6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# /optimize (C# Compiler Options)
**\/optimize** 選項會啟用或停用編譯器執行的最佳化，讓您的輸出檔變得更小、更快而且更有效率。  
  
## 語法  
  
```  
/optimize[+ | -]  
```  
  
## 備註  
 **\/optimize** 同時也通知 Common Language Runtime 在執行階段時最佳化程式碼。  
  
 根據預設，最佳化功能是停用的。  請指定 **\/optimize\+** 以啟用最佳化。  
  
 建置模組以供組件 \(Assembly\) 使用時，請使用與組件相同的 **\/optimize** 設定。  
  
 **\/o** 是 **\/optimize** 的簡短形式。  
  
 **\/optimize** 和 [\/debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) 選項可以結合。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性**\] 頁面。  
  
2.  按一下 \[**建置**\] 屬性頁。  
  
3.  修改 \[**最佳化程式碼**\] 屬性。  
  
 如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>。  
  
## 範例  
 將 `t2.cs`並啟用編譯器最佳化:  
  
```  
csc t2.cs /optimize  
```  
  
## 請參閱  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)