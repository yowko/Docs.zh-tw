---
title: "/nostdlib (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "nostdlib compiler option [Visual Basic]"
  - "-nostdlib compiler option [Visual Basic]"
  - "/nostdlib compiler option [Visual Basic]"
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# /nostdlib (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

導致編譯器 \(Compiler\) 不會自動參考標準程式庫。  
  
## 語法  
  
```  
/nostdlib  
```  
  
## 備註  
 `/nostdlib` 選項會移除對 System.dll 組件的自動參考，並防止編譯器讀取 Vbc.rsp 檔。  Vbc.rsp 檔 \(與 Vbc.exe 檔位於相同的目錄中\) 會參考常用的 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 組件並匯入 `System` 和 `Microsoft.VisualBasic` 命名空間。  
  
> [!NOTE]
>  一定會參考 Mscorlib.dll 和 Microsoft.VisualBasic.dll 組件。  
  
> [!NOTE]
>  `/nostdlib` 選項無法在 Visual Studio 開發環境內使用，只有在命令列編譯時才能使用。  
  
## 範例  
 下列程式碼會編譯 `T2.vb`，但不參考標準程式庫。  您必須將 `_MYTYPE` 條件式編譯的常數設定為字串 "Empty"，以便移除 `My` 物件。  
  
```  
vbc /nostdlib /define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## 請參閱  
 [\/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)   
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Customizing Which Objects are Available in My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)