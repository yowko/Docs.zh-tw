---
title: "/target (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
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
  - "target compiler options [Visual Basic]"
  - "-target compiler options [Visual Basic]"
  - "/target compiler options [Visual Basic]"
ms.assetid: e0954147-548b-461f-9c4b-a8f88845616c
caps.latest.revision: 29
caps.handback.revision: 29
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /target (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

指定編譯器輸出格式。  
  
## 語法  
  
```  
/target:{exe | library | module | winexe | appcontainerexe | winmdobj}  
```  
  
## 備註  
 下表彙總 `/target` 選項的效果。  
  
|**選項**|**行為**|  
|------------|------------|  
|`/target:exe`|讓編譯器建立可執行的主控台應用程式。<br /><br /> 如果沒有指定 `/target` 選項，這就是預設選項。  建立的可執行檔具有 .exe 副檔名。<br /><br /> 除非用 `/out` 選項指定輸出檔名稱，否則輸出檔名會取自包含 `Sub Main` 程序的輸入檔名。<br /><br /> 編譯成 .exe 檔案的原始程式碼檔中只需要一個 `Sub Main` 程序。  使用 `/main` 編譯器選項可指定哪個類別包含 `Sub Main` 程序。|  
|`/target:library`|使編譯器建立「動態連結程式庫 \(DLL\)」。<br /><br /> 建立的動態連結程式庫檔案具有 .dll 副檔名。<br /><br /> 除非您已使用 `/out` 選項指定輸出檔名稱，否則將會以第一個輸入檔名稱命名。<br /><br /> 建置 DLL 時並不需要 `Sub Main` 程序。|  
|`/target:module`|讓編譯器產生可以加入至組件的模組。<br /><br /> 建立的輸出檔具有副檔名 .  netmodule。<br /><br /> .NET Common Language Runtime 無法載入不含組件的檔案。  但是，您可以使用 `/reference` 將這類檔案合併至組件的組件資訊清單 \(Assembly Manifest\) 中。<br /><br /> 當某個模組中的程式碼參考其他模組中的內部型別時，必須使用 `/reference` 將這兩個模組加入組件資訊清單中。<br /><br /> [\/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) 選項會從模組匯入中繼資料。|  
|`/target:winexe`|讓編譯器建立可執行的 Windows 應用程式。<br /><br /> 建立的可執行檔具有 .exe 副檔名。  Windows 應用程式是從 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] 類別庫 \(Class Library\) 或以 Win32 API 提供使用者介面。<br /><br /> 除非用 `/out` 選項指定輸出檔名稱，否則輸出檔名會取自包含 `Sub Main` 程序的輸入檔名。<br /><br /> 編譯成 .exe 檔案的原始程式碼檔中只需要一個 `Sub Main` 程序。  當您的程式碼具有多個擁有 `Sub Main` 程序的類別時，請使用 `/main` 編譯器選項，指定哪個類別包含 `Sub Main` 程序|  
|`/target:appcontainerexe`|讓編譯器建立應用程式容器必須執行的可執行的 Windows 架構應用程式。  這個設定是設計為 [!INCLUDE[win8_appname_long](../../../csharp/language-reference/compiler-options/includes/win8_appname_long_md.md)] 應用程式使用。<br /><br /> 將集合的 **appcontainerexe** 位在特性 [可移植的執行檔 \(PE\)。](http://go.microsoft.com/fwlink/p/?LinkId=236960) 檔案欄位。  這個欄位指示應用程式在容器必須執行應用程式。  當這個欄位設定時，就會發生錯誤，則 `CreateProcess` 方法嘗試啟動應用程式容器之外。  刪除這個欄位設定之外， **\/target:appcontainerexe** 與 **\/target:winexe**相當於。<br /><br /> 建立的可執行檔具有 .exe 副檔名。<br /><br /> 您可以使用 `/out` 選項，除非另有指定，否則輸出檔名會取自包含 `Sub Main` 程序輸入檔案的名稱。<br /><br /> 編譯成 .exe 檔案的原始程式碼檔中只需要一個 `Sub Main` 程序。  如果您的程式碼包含多個擁有 `Sub Main` 程序的類別，請使用 `/main` 編譯器選項指定含有 `Sub Main` 程序|  
|`/target:winmdobj`|讓編譯器建立可轉換為 Windows 執行階段二進位的中繼檔 \(.winmd\) 檔案。  除了 Managed 程式語言以外， .winmd 檔案可由 JavaScript 和 C\+\+ 程式會使用。<br /><br /> 中繼檔案建立 .winmdobj 副檔名。<br /><br /> 您可以使用 `/out` 選項，除非另有指定，否則輸出檔名會取自第一個輸入檔的名稱。  不需要 `Sub Main` 程序。<br /><br /> .winmdobj 檔案是設計用來做為輸入以 <xref:Microsoft.Build.Tasks.WinMDExp> 匯出工具可能會導致視窗中繼資料 \(WinMD\) 檔。  WinMD 檔案具有 .winmd 副檔名並包含從原始程式庫的程式碼和 JavaScript、C\+\+ 和 Windows 執行階段所使用的 WinMD 定義。|  
  
 除非您指定的是 `/target:module`，否則 `/target` 會將 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] 組件資訊清單加入至輸出檔。  
  
 每一個 Vbc.exe 的執行個體 \(Instance\) 最多只會產生一個輸出檔。  如果您指定的編譯器選項 \(如 `/out` 或 `/target`\) 超過一次以上，則編譯器所處理的最後一個選項會生效。  編譯中所有檔案的相關資訊都會加入至資訊清單。  除了使用 `/target:module` 建立的輸出檔之外，所有輸出檔在資訊清單中都包含組件中繼資料。  請使用 [Ildasm.exe \(IL Disassembler\)](../Topic/Ildasm.exe%20\(IL%20Disassembler\).md) 檢視輸出檔案中的中繼資料。  
  
 `/target` 的簡短形式為 `/t`。  
  
### 若要在 Visual Studio IDE 中設定 \/target  
  
1.  在 \[**方案總管**\] 中選取專案。  在 \[**專案**\] 功能表上，按一下 \[**屬性**\]。  如需詳細資訊，請參閱[Introduction to the Project Designer](http://msdn.microsoft.com/zh-tw/898dd854-c98d-430c-ba1b-a913ce3c73d7)。  
  
2.  按一下 \[**應用程式**\] 索引標籤。  
  
3.  修改 \[**應用程式類型**\] 方塊中的值。  
  
## 範例  
 下列程式碼會編譯 `in.vb`，並建立 `in.dll`：  
  
```  
vbc /target:library in.vb  
```  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/main](../../../visual-basic/reference/command-line-compiler/main.md)   
 [\/out](../../../visual-basic/reference/command-line-compiler/out.md)   
 [\/reference](../../../visual-basic/reference/command-line-compiler/reference.md)   
 [\/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)   
 [\/moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)   
 [組件和全域組件快取](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)