---
title: "/main (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/main"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "-main compiler option [C#]"
  - "main compiler option [C#]"
  - "/main compiler option [C#]"
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# /main (C# Compiler Options)
如果一個以上的類別包含 **Main** 方法，這個選項會指定包含程式進入點 \(Entry Point\) 的類別。  
  
## 語法  
  
```  
/main:class  
```  
  
## 引數  
 `class`  
 包含 **Main** 方法的型別。  
  
## 備註  
 如果您的編譯包括一個以上具有 [Main](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md) 方法的型別，您可以指定包含了您要用來當做程式進入點之 **Main** 方法的型別。  
  
 這個選項是在編譯 .exe 檔時使用的。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性**\] 頁面。  
  
2.  按一下 \[**應用程式**\] 屬性頁。  
  
3.  修改 \[**啟始物件**\] 屬性。  
  
     若要用程式設計的方式設定這個編譯器選項，請參閱 <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>。  
  
## 範例  
 編譯 `t2.cs` 和 `t3.cs`，指定可以在 `Test2` 中找到 **Main** 方法：  
  
```  
csc t2.cs t3.cs /main:Test2  
```  
  
## 請參閱  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)