---
title: "/bugreport | Microsoft Docs"
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
  - "-bugreport compiler option [Visual Basic]"
  - "bugreport compiler option [Visual Basic]"
  - "/bugreport compiler option [Visual Basic]"
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# /bugreport
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

建立可以用來為錯誤報告建檔的檔案。  
  
## 語法  
  
```  
/bugreport:file  
```  
  
## 引數  
  
|||  
|-|-|  
|詞彙|定義|  
|`file`|必要項。  包含錯誤報告的檔案名稱。  如果檔案名稱包含空格，請加上雙引號 \(" "\)。|  
  
## 備註  
 下列資訊會加入到 `file`：  
  
-   編譯中所有原始程式碼檔的複本。  
  
-   編譯中使用的編譯器選項清單。  
  
-   有關您的編譯器、Common Language Runtime 和作業系統的版本資訊。  
  
-   編譯器輸出 \(如果有的話\)。  
  
-   問題的描述，會提示您輸入。  
  
-   您認為問題該如何解決的描述，會提示您輸入。  
  
 由於所有原始程式碼檔的複本都是包含在 `file` 中，因此您可能會想要在最短的程式中重現 \(可能的\) 程式碼缺失。  
  
> [!IMPORTANT]
>  `/bugreport` 選項會產生包含潛在機密資訊的檔案。  其中包括目前的時間、編譯器版本、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 版本、OS 版本、使用者名稱、執行編譯器的命令列引數、所有的原始程式碼，以及二進位格式的所有參考組件。  只要針對 [!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp-md.md)] 應用程式的伺服器端編譯所用的 Web.config 檔案，指定命令列選項，便能存取此選項。  為了防止發生這種情況，請修改 Machine.config 檔案，禁止使用者在伺服器上編譯。  
  
 如果將這個選項與 `/errorreport:prompt`、`/errorreport:queue` 或 `/errorreport:send` 搭配使用，而且應用程式發生編譯器內部錯誤，則會將 `file` 中的資訊傳送至 Microsoft Corporation。  該資訊將協助 Microsoft 工程師識別錯誤的原因，也有助於改善下一版 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)]。  根據預設值，不會將資訊傳給 Microsoft。  然而，當您使用 `/errorreport:queue` 編譯應用程式時 \(依預設值啟用\)，應用程式便會收集其錯誤報告。  然後，當電腦的系統管理員登入時，錯誤報告系統便會顯示一個快顯視窗，讓系統管理員能將自登入以來發生的所有錯誤都轉寄給 Microsoft。  
  
> [!NOTE]
>  `/bugreport` 選項無法從 Visual Studio 開發環境使用，只有在命令列編譯時才能使用。  
  
## 範例  
 下列範例會編譯 `T2.vb`，並將所有錯誤報告資訊置於 `Problem.txt` 檔案中。  
  
```  
vbc /bugreport:problem.txt t2.vb  
```  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/debug](../../../visual-basic/reference/command-line-compiler/debug.md)   
 [\/errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [securityPolicy 的 trustLevel 項目 \(ASP.NET 設定結構描述\)](http://msdn.microsoft.com/zh-tw/729ab04c-03da-4ee5-86b1-be9d08a09369)