---
title: "/lib (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/lib"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "lib compiler option [C#]"
  - "-lib compiler option [C#]"
  - "/lib compiler option [C#]"
ms.assetid: b0efcc88-e8aa-4df4-a00b-8bdef70b7673
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# /lib (C# Compiler Options)
**\/lib** 選項會透過 [\/reference \(Import Metadata\)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) 選項指定所參考組件的位置。  
  
## 語法  
  
```  
/lib:dir1[,dir2]  
```  
  
## 引數  
 `dir1`  
 如果在目前的工作目錄 \(叫用編譯器時所在的目錄\) 或 Common Language Runtime 的系統目錄中都找不到參考的組件時，編譯器所要查詢的目錄。  
  
 `dir2`  
 一個或多個用來尋找組件參考的其他目錄。  請用逗號隔開額外的目錄名稱，中間不需加上空格。  
  
## 備註  
 編譯器依據以下順序搜尋那些沒有完整路徑名稱的組件參考：  
  
1.  目前工作目錄。  就是從這個目錄叫用編譯器。  
  
2.  Common Language Runtime 的系統目錄。  
  
3.  **\/lib** 指定的目錄。  
  
4.  由 LIB 環境變數指定的目錄。  
  
 使用 **\/reference** 指定組件參考。  
  
 **\/lib** 是加法類 \(Additive\) 的選項；指定超過一次就會附加到任何先前的數值。  
  
 另外一種使用 **\/lib** 的方法，是將任何所需的組件複製到工作目錄中；這會將組件名稱傳遞到 **\/reference**。  您可以接著從工作目錄刪除這些組件。  因為相依組件路徑並沒有指定於組件資訊清單，所以此應用程式可以在目標電腦上啟動，並將搜尋和使用共用組件快取中的組件。  
  
 編譯器可以參考組件卻未必表示 Common Language Runtime 可以在執行階段時找到並載入組件。  如需執行階段搜尋參考組件方法的詳細資訊，請參閱[執行階段如何找出組件](../Topic/How%20the%20Runtime%20Locates%20Assemblies.md)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  
  
2.  按一下 \[**參考路徑**\] 屬性頁。  
  
3.  修改清單方塊的內容。  
  
 如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>。  
  
## 範例  
 編譯 t2.cs 來建立一個 .exe 檔，  編譯器會在工作目錄和 C 磁碟的根目錄中查詢組件參考。  
  
```  
csc /lib:c:\ /reference:t2.dll t2.cs  
```  
  
## 請參閱  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)