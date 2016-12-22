---
title: "/reference (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "/reference compiler option [Visual Basic]"
  - "r compiler option [Visual Basic]"
  - "-reference compiler option [Visual Basic]"
  - "/r compiler option [Visual Basic]"
  - "reference compiler option [Visual Basic]"
  - "-r compiler option [Visual Basic]"
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /reference (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

讓編譯器允許您目前正在編譯的專案使用指定組件中的型別資訊。  
  
## 語法  
  
```  
/reference:fileList  
' -or-  
/r:fileList  
```  
  
## 引數  
  
|||  
|-|-|  
|詞彙|定義|  
|`fileList`|必要項。  逗號分隔的組件檔名清單。  如果檔案名稱包含空格，請將名稱加上雙引號 \(" "\)。|  
  
## 備註  
 您匯入的檔案必須包含組件中繼資料。  在組件外部只能看見公用型別。  [\/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) 選項會從模組匯入中繼資料。  
  
 如果您參考的組件 \(A 組件\) 本身又參考到其他組件 \(B 組件\) 的話，以下情況時，您需要參考 B 組件：  
  
-   來自 A 組件的型別繼承自某個型別，或是從 B 組件實作介面。  
  
-   從 B 組件叫用 \(Invoke\) 具有傳回型別或參數型別的欄位、屬性 \(Property\)、事件或方法。  
  
 請使用 [\/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) 指定一或多個組件參考所在的目錄。  
  
 若要讓編譯器 \(Compiler\) 辨識組件 \(非模組\) 中的型別，則必須強制它解析該型別。  如何這麼做的其中一個範例就是定義型別的執行個體。  編譯器還可以使用其他方式來解析組件中的型別名稱。  例如，如果是從組件中的型別繼承而來，編譯器就會知道型別名稱。  
  
 根據預設會使用參考常用 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] 組件的 Vbc.rsp 回應檔 \(Response File\)。  如果您不想讓編譯器使用 Vbc.rsp，請使用 `/noconfig`。  
  
 `/reference`  的簡短形式為 `/r`。  
  
## 範例  
 下列程式碼會編譯原始程式檔 I`nput.vb`，並參考 M`etad1.dll` 和 M`etad2.dll` 中的組件來產生 O`ut.exe`。  
  
```  
vbc /reference:metad1.dll,metad2.dll /out:out.exe input.vb  
```  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)   
 [\/target](../../../visual-basic/reference/command-line-compiler/target.md)   
 [Public](../../../visual-basic/language-reference/modifiers/public.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)