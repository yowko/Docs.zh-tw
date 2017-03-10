---
title: "/pdb (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/pdb"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "-pdb compiler option [C#]"
  - "pdb compiler option [C#]"
  - "/pdb compiler option [C#]"
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
caps.latest.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 8
---
# /pdb (C# Compiler Options)
**\/pdb** 編譯器選項會指定偵錯符號檔的名稱和位置。  
  
## 語法  
  
```  
/pdb:filename  
```  
  
## 引數  
 `filename`  
 偵錯符號檔的名稱和位置。  
  
## 備註  
 當您指定 [\/debug \(Emit Debugging Information\)](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) 時，編譯器會在相同目錄中建立 .pdb 檔，在這個目錄中編譯器會使用與輸出檔相同的檔案名稱建立輸出檔 \(.exe 或 .dll\)。  
  
 **\/pdb** 可讓您對 .pdb 檔案指定非預設的檔案名稱和位置。  
  
 這個編譯器選項無法在 Visual Studio 開發環境中設定，也不能以程式設計的方式變更。  
  
## 範例  
 編譯 `t.cs` 和建立名為 tt.pdb 的 .pdb 檔案：  
  
```  
csc /debug /pdb:tt t.cs  
```  
  
## 請參閱  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)