---
title: "/warn (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/warn"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "warning level [C#]"
  - "/w compiler option [C#]"
  - "-w compiler option [C#]"
  - "-warn compiler option [C#]"
  - "/warn compiler option [C#]"
  - "w compiler option [C#]"
  - "warn compiler option [C#]"
ms.assetid: 5f80ff59-4991-4382-9f9a-77da18446e71
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# /warn (C# Compiler Options)
**\/warn** 選項會指定編譯器顯示的警告層級。  
  
## 語法  
  
```  
/warn:option  
```  
  
## Arguments  
 `option`  
 您要顯示的編譯警告層級：數字愈小，就只顯示嚴重性高的警告；數字愈大，顯示的警告愈多。  有效值為 0\-4：  
  
|警告層級|意義|  
|----------|--------|  
|0|關閉所有警告訊息的發送。|  
|1|顯示嚴重的警告訊息。|  
|2|顯示警告層級 1 及某些較不嚴重的警告，如有關隱藏類別成員的警告。|  
|3|顯示警告層級 2 及某些較不嚴重的警告，如一定會評估為 `true` 或 `false` 的運算式警告。|  
|4 \(預設值\)|顯示警告層級 3 及某些資訊警告。|  
  
## 備註  
 若要取得錯誤或警告的詳細資訊，您可以在說明索引中查詢錯誤碼。  如需取得錯誤或警告資訊的其他方式，請參閱 [C\# Compiler Errors](../../../csharp/language-reference/compiler-messages/index.md)。  
  
 使用 [\/warnaserror](../../../csharp/language-reference/compiler-options/warnaserror-compiler-option.md)，將所有警告視為錯誤。  使用 [\/nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) 停用某些警告。  
  
 **\/w** 是 **\/warn** 的簡短形式。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性**\] 頁面。  
  
2.  按一下 \[**建置**\] 屬性頁。  
  
3.  修改 \[**警告層級**\] 屬性。  
  
 如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>。  
  
## 範例  
 編譯 `in.cs` 並使編譯器只顯示警告層級 1 ：  
  
```  
csc /warn:1 in.cs  
```  
  
## 請參閱  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)