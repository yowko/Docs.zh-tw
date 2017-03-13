---
title: "/netcf | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "/netcf"
  - "netcf"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "-netcf compiler option [Visual Basic]"
  - "netcf compiler option [Visual Basic]"
  - "/netcf compiler option [Visual Basic]"
ms.assetid: db7cfa59-c315-401c-a59b-0daf355343d6
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# /netcf
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

針對 [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact-md.md)] 設定編譯器。  
  
## 語法  
  
```  
/netcf  
```  
  
## 備註  
 `/netcf` 選項會指示 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 編譯器將目標放在 [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact-md.md)] 而非完整的 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)]。  僅在完整的 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 中提供的語言功能停用。  
  
 `/netcf` 選項是設計與 [\/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) 搭配使用。  `/netcf` 停用的語言功能如同在 `/sdkpath` 指定的檔案中，未提供的語言功能一樣。  
  
> [!NOTE]
>  `/netcf` 選項無法在 Visual Studio 開發環境內使用；只有在命令列編譯時才能使用。  載入 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 裝置專案時，會設定 `/netcf` 選項。  
  
 `/netcf` 選項可變更下列語言功能：  
  
-   停用可終止程式執行的 [End \<keyword\> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) 關鍵字。  下列程式可在不使用 `/netcf` 的情況下編譯和執行，但使用 `/netcf` 時，會在編譯時期失敗。  
  
     [!code-vb[VbVbalrCompiler#34](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_1.vb)]  
  
-   所有形式的晚期繫結都會停用。  當遭遇到辨識出的晚期繫結案例時，就會產生編譯時期錯誤。  下列程式可在不使用 `/netcf` 的情況下編譯和執行，但使用 `/netcf` 時，會在編譯時期失敗。  
  
     [!code-vb[VbVbalrCompiler#35](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_2.vb)]  
  
-   停用 [Auto](../../../visual-basic/language-reference/modifiers/auto.md)、[Ansi](../../../visual-basic/language-reference/modifiers/ansi.md) 和 [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) 修飾詞 \(Modifier\)。  也會將 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) 陳述式的語法修改成 `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`。  下列的程式碼將顯示出使用 `/netcf` 編譯的效果。  
  
     [!code-vb[VbVbalrCompiler#36](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_3.vb)]  
  
-   使用自 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 移除的 Visual Basic 6.0 關鍵字時，會在使用 `/netcf` 時產生不同的錯誤。  這會影響在下列關鍵字中所看到的錯誤訊息：  
  
    -   `Open`  
  
    -   `Close`  
  
    -   `Put`  
  
    -   `Print`  
  
    -   `Write`  
  
    -   `Input`  
  
    -   `Lock`  
  
    -   `Unlock`  
  
    -   `Seek`  
  
    -   `Width`  
  
    -   `Name`  
  
    -   `FreeFile`  
  
    -   `EOF`  
  
    -   `Loc`  
  
    -   `LOF`  
  
    -   `Line`  
  
## 範例  
 下列的程式碼會使用 C 磁碟中 [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact-md.md)] 預設安裝目錄下的 Mscorlib.dll 和 Microsoft.VisualBasic.dll 版本，利用 [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact-md.md)] 來編譯 `Myfile.vb`。  您通常可使用最新版的 [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact-md.md)]。  
  
```  
vbc /netcf /sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [\/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)