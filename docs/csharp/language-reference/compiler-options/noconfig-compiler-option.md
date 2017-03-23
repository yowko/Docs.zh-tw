---
title: "/noconfig (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/noconfig"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/noconfig compiler option [C#]"
  - "csc.rsp"
  - "-noconfig compiler option [C#]"
  - "noconfig compiler option [C#]"
ms.assetid: cd26967e-e494-4c8c-b5c9-af13b2f78b2e
caps.latest.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 11
---
# /noconfig (C# Compiler Options)
**\/noconfig** 選項會告訴編譯器，不要使用與 csc.exe 檔位在相同目錄並經由該目錄載入的 csc.rsp 檔編譯。  
  
## 語法  
  
```  
/noconfig  
```  
  
## 備註  
 csc.rsp 檔參考所有隨附於 .NET Framework 的組件。  Visual Studio .NET 開發環境所包含的實際參考，是取決於專案類型而定。  
  
 您可以修改 csc.rsp 檔和指定其他編譯器選項，這些選項 \(除了 **\/noconfig** 選項\) 應該包含在每次經由命令列使用 csc.exe 的編譯之中。  
  
 編譯器最後才會處理傳遞至 **csc** 命令的選項。  因此，命令列中的任何選項都會覆蓋 csc.rsp 檔中相同選項的設定。  
  
 如果您不希望由編譯器尋找和使用 csc.rsp 檔中的設定時，請指定 **\/noconfig**。  
  
 在 Visual Studio 中無法使用這個編譯器選項，而且無法利用程式設計的方式變更它。  
  
## 請參閱  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)