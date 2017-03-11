---
title: "/win32res (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/win32res"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "win32res compiler option"
  - "/win32res compiler option [C#]"
  - "-win32res compiler option [C#]"
  - "win32res compiler option [C#]"
ms.assetid: 3c33f750-6948-4c7e-a27e-bef98f77255b
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# /win32res (C# Compiler Options)
**\/win32res** 選項會將 Win32 資源插入輸出檔中。  
  
## 語法  
  
```  
/win32res:filename  
```  
  
## Arguments  
 `filename`  
 您要加入至輸出檔的資源檔。  
  
## 備註  
 您可以使用[資源編譯器](http://go.microsoft.com/fwlink/?LinkId=148370)建立 Win32 資源檔。  資源編譯器是在編譯 Visual C\+\+ 程式時叫用的，而 .res 檔案則是用 .rc 檔案建立的。  
  
 Win32 資源可以包含版本或點陣圖 \(圖示\) 資訊，這項資訊可以協助您在檔案總管中識別應用程式。  如果您沒有指定 **\/win32res**，編譯器會根據組件版本來產生版本資訊。  
  
 如需參考 .NET Framework 資源檔，請參閱 [\/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md)；如需附加 .NET Framework 資源檔，請參閱 [\/resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性**\] 頁面。  
  
2.  按一下 \[**應用程式**\] 屬性頁。  
  
3.  按一下 \[**資源檔**\] 按鈕，然後使用下拉式方塊選擇檔案。  
  
## 範例  
 編譯 `in.cs` 並附加 `rf.res` Win32 資源檔以產生 `in.exe`：  
  
```  
csc /win32res:rf.res in.cs  
```  
  
## 請參閱  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)