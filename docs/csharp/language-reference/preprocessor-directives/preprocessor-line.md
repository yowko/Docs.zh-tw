---
title: "#line (C# 參考) | Microsoft Docs"
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
  - "#line"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "#line 指示詞 [C#]"
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# #line (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`#line` 讓您可以修改編譯器行號以及錯誤和警告的檔名輸出 \(選擇性\)。  這個範例示範如何報告兩個與行號相關聯的警告。  `#line 200` 指示詞會將行號強制設定為 200 \(雖然預設值為 \#7\)，而且在下一個 \#line 指示詞之前，檔案名稱都會以 "Special" 回報。  \#line 預設指示詞會將行號設定傳回到它的預設行號，這項設定會根據前一個指示詞重新編號的結果計算行號。  
  
```  
class MainClass  
{  
    static void Main()  
    {  
#line 200 "Special"  
        int i;    // CS0168 on line 200  
        int j;    // CS0168 on line 201  
#line default  
        char c;   // CS0168 on line 9  
        float f;  // CS0168 on line 10  
#line hidden // numbering not affected  
        string s;   
        double d; // CS0168 on line 13  
    }  
}  
```  
  
## 備註  
 在建置程序的自動及中繼步驟中可能會使用 `#line` 指示詞。  例如，如果已經從原始的原始程式碼檔案中移除某些行，但是仍然希望由編譯器依照原始檔案中，行號所標示的程式碼行能夠產生輸出時，此時您就可以在移除這些行之後，再模擬以 `#line` 標示的原始程式碼行。  
  
 `#line hidden` 指示詞會對偵錯工具隱藏連續程式碼行，這樣一來，當開發人員逐步偵錯程式碼時，任何介於 `#line hidden` 和下一個 `#line` 指示詞 \(假設這不是另一個 `#line hidden` 指示詞\) 之間的程式碼就不會進入函式。  這個選項也可以用來讓 ASP.NET 區別使用者定義和機器所產生的程式碼。  儘管 ASP.NET 是這個功能的主要使用者，但是似乎更多原始檔產生器 \(Source Generator\) 將會使用這個功能。  
  
 `#line hidden` 指示詞並不會影響錯誤報告中的檔案名稱或行號。  也就是說，如果隱藏區塊中出現錯誤的話，編譯器會報告該錯誤的現有檔案名稱和行號。  
  
 `#line filename` 指示詞指定您希望在編譯器輸出中顯示的檔名。  根據預設，會使用原始程式碼檔案的實際名稱。  檔案名稱必須以雙引號 \(""\) 括起來，而且名稱前面必須加上行號。  
  
 一個原始程式碼檔案可以有任意數量的 `#line` 指示詞。  
  
## 範例 1  
 下列範例將示範偵錯工具如何忽略程式碼中的隱藏程式碼行。  當執行範例時，便會顯示三行文字。  但是如果如範例所示設定中斷點，並按下 F10 以逐步偵錯程式碼時，偵錯工具就會忽略隱藏的程式碼行。  同時請注意，即使您在隱藏程式碼行中設定中斷點，偵錯工具仍會忽略該行。  
  
```  
// preprocessor_linehidden.cs  
using System;  
class MainClass   
{  
    static void Main()   
    {  
        Console.WriteLine("Normal line #1."); // Set break point here.  
#line hidden  
        Console.WriteLine("Hidden line.");  
#line default  
        Console.WriteLine("Normal line #2.");  
    }  
}  
```  
  
## 請參閱  
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 前置處理器指示詞](../../../csharp/language-reference/preprocessor-directives/index.md)