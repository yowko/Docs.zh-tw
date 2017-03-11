---
title: "/win32icon (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/win32icon"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "win32icon compiler option [C#]"
  - "/win32icon compiler option [C#]"
  - "-win32icon compiler option [C#]"
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
caps.latest.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 18
---
# /win32icon (C# Compiler Options)
**\/win32icon** 選項可以在輸出檔內插入一個 .ico 檔，讓輸出檔在檔案總管中具有所需的外觀。  
  
## 語法  
  
```  
/win32icon:filename  
```  
  
## Arguments  
 `filename`  
 您要加入至輸出檔的 .ico 檔案。  
  
## 備註  
 .ico 檔案可以透過 [資源編譯器](http://go.microsoft.com/fwlink/?LinkId=148370)來建造。  資源編譯器是在編譯 Visual C\+\+ 程式時叫用的，而 .res 檔案則是以 .rc 檔案建立的。  
  
 如需參考 .NET Framework 資源檔，請參閱 [\/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md)；如需附加 .NET Framework 資源檔，請參閱 [\/resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md)。  請參閱 [\/win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) 來匯入 .res 檔。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性**\] 頁面。  
  
2.  按一下 \[**應用程式**\] 屬性頁。  
  
3.  修改 \[**應用程式圖示**\] 屬性。  
  
 如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>。  
  
## 範例  
 編譯 `in.cs` 並附加 `rf.ico` 檔案以產生 `in.exe`：  
  
```  
csc /win32icon:rf.ico in.cs  
```  
  
## 請參閱  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)