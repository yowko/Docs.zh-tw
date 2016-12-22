---
title: "/debug (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/debug"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "debug compiler option [C#]"
  - "-debug compiler option [C#]"
  - "/debug compiler option [C#]"
ms.assetid: e2b48c07-01bc-45cc-a52c-92e9085eb969
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /debug (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

**\/debug** 選項會讓編譯器產生偵錯資訊，並將其置於輸出檔中。  
  
## 語法  
  
```  
/debug[+ | -]  
/debug:{full | pdbonly}  
```  
  
## 引數  
 `+` &#124; `-`  
 指定 `+` \(或者只是 **\/debug**\) 會讓編譯器產生偵錯資訊，並將該資訊置於程式資料庫 \(.pdb 檔案\) 中。  指定 `-` \(如果沒有指定 **\/debug** 則生效\) 就不會建立偵錯資訊。  
  
 `full` &#124; `pdbonly`  
 指定編譯器所產生的偵錯資訊類型。  此 full 引數 \(它會在您沒有指定 **\/debug:pdbonly** 時生效\) 會啟用附加偵錯工具到正在執行的程式。  指定 pdbonly 可以讓程式在偵錯工具中啟動時進行原始程式碼偵錯，但是如果執行的程式是附加到偵錯工具，則只會顯示組合語言。  
  
## 備註  
 請使用這個選項來建立偵錯組建。  如果未指定 **\/debug**、**\/debug\+** 或 **\/debug:full**，您將無法對程式的輸出檔進行偵錯。  
  
 請注意，如果您使用 **\/debug:full**，會影響 JIT 最佳化程式碼的速度與大小，並且對使用 **\/debug:full** 的程式碼品質造成些許影響。  建議您使用 **\/debug:pdbonly** 或不使用 PDB 檔來產生發行程式碼。  
  
> [!NOTE]
>  **\/debug:pdbonly** 和 **\/debug:full** 之間的其中一項差異在於，編譯器使用 **\/debug:full** 發出 <xref:System.Diagnostics.DebuggableAttribute>，用來告知 JIT 編譯器已可取得偵錯資訊。  因此，如果您使用 **\/debug:full** 且程式碼中的 <xref:System.Diagnostics.DebuggableAttribute> 設定為 false，便會發生這個錯誤。  
  
 如需如何設定應用程式偵錯效能的相關資訊，請參閱[使映像偵錯更容易](../Topic/Making%20an%20Image%20Easier%20to%20Debug.md)。  
  
 若要變更 .pdb 檔案的位置，請參閱 [\/pdb \(Specify Debug Symbol File\)](../../../csharp/language-reference/compiler-options/pdb-compiler-option.md)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性**\] 頁面。  
  
2.  按一下 \[**建置**\] 屬性頁。  
  
3.  按一下 \[**進階**\] 按鈕。  
  
4.  修改 \[**偵錯資訊**\] 屬性。  
  
 如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DebugSymbols%2A>。  
  
## 範例  
 將偵錯資訊放入輸出檔 `app.pdb`：  
  
```  
csc /debug /pdb:app.pdb test.cs  
```  
  
## 請參閱  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)