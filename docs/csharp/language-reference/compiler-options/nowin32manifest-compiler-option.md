---
title: "/nowin32manifest (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/nowin32manifest"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "nowin32manifest compiler option [C#]"
  - "-nowin32manifest compiler option [C#]"
  - "/nowin32manifest compiler option [C#]"
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 13
---
# /nowin32manifest (C# Compiler Options)
使用 **\/nowin32manifest** 選項，指示編譯器 \(Compiler\) 不要將任何應用程式資訊清單內嵌在可執行檔中。  
  
## 語法  
  
```  
/nowin32manifest  
```  
  
## 備註  
 使用此選項時，應用程式會受制於 Windows Vista 的虛擬化，除非您在 Win32 資源檔或稍後建置步驟中提供應用程式資訊清單。  如需虛擬化的詳細資訊，請參閱 [New UAC Technologies for Windows Vista](http://msdn.microsoft.com/zh-tw/80efa4c7-3904-45c5-82e8-2d558fe67db9)。  
  
 在 Visual Studio 中，選取 \[**資訊清單**\] 下拉式清單中的 \[**建立無資訊清單應用程式**\] 選項，以在 \[**應用程式屬性**\] 頁面中設定這個選項。  如需詳細資訊，請參閱[專案設計工具，應用程式頁 \(C\#\)](/visual-studio/ide/reference/application-page-project-designer-csharp)。  
  
 如需建立資訊清單的詳細資訊，請參閱 [\/win32manifest \(Import a Custom Win32 Manifest File\)](../../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md)。  
  
## 請參閱  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)