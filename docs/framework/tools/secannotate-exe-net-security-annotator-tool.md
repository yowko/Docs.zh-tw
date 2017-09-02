---
title: "SecAnnotate.exe (.NET Security Annotator Tool) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "SecAnnotate.exe"
  - "Security Annotator tool"
ms.assetid: 8104d208-7813-4a1d-8a75-58f9a7bcb8c9
caps.latest.revision: 22
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 22
---
# SecAnnotate.exe (.NET Security Annotator Tool)
.NET Security Annotator 工具 \(SecAnnotate.exe\) 是識別一個或多個組件之 `SecurityCritical` 和 `SecuritySafeCritical` 部分的命令列應用程式。  
  
 Visual Studio 擴充功能 \([Security Annotator](http://go.microsoft.com/fwlink/?LinkId=198007)\) 提供 SecAnnotate.exe 的圖形化使用者介面，讓您能夠從 Visual Studio 執行該工具。  
  
 此工具會自動與 Visual Studio 一起安裝。  若要執行此工具，請使用 \[開發人員命令提示字元\] \(或 Windows 7 中的 \[Visual Studio 命令提示字元\]\)。  如需詳細資訊，請參閱 [命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。  
  
 在命令提示字元下輸入以下內容，其中下一節會描述 *parameters*，而 *assemblies* 則包含以空格分隔的一個或多個組件名稱：  
  
## 語法  
  
```  
SecAnnotate.exe [parameters] [assemblies]  
```  
  
#### 參數  
  
|選項|描述|  
|--------|--------|  
|`/a`<br /><br /> 或<br /><br /> `/showstatistics`|顯示要分析之組件中有關透明度使用的統計資料。|  
|`/d:` *directory*<br /><br /> 或<br /><br /> `/referencedir:` *directory*|指定要在註釋期間搜尋相依組件的目錄。|  
|`/i`<br /><br /> 或<br /><br /> `/includesignatures`|在註釋報告檔中包含延伸的簽章資訊。|  
|`/n`<br /><br /> 或<br /><br /> `/nogac`|撤銷對全域組件快取中參考組件的搜尋。|  
|`/o:` *output.xml*  ``<br /><br /> 或<br /><br /> `/out:` *output.xml*|指定輸出的註釋檔案。|  
|`/p:` *maxpasses*  ``<br /><br /> 或<br /><br /> `/maximumpasses:` *maxpasses*|指定停止產生新註釋前，嘗試傳遞組件註釋的最大值。|  
|`/q`<br /><br /> 或<br /><br /> `/quiet`|指定無訊息模式，在此模式中，註釋工具不會輸出狀態訊息，只會輸出錯誤訊息。|  
|`/r:` *assembly*<br /><br /> 或<br /><br /> `/referenceassembly:` *assembly*|註釋期間解析相依組件時包含指定的組件。  參考組件的優先順序高於參考路徑中的組件。|  
|`/s:` *rulename*  ``<br /><br /> 或<br /><br /> `/suppressrule:` *rulename*|隱藏執行輸入組件上的指定透明度規則。|  
|`/t`<br /><br /> 或<br /><br /> `/forcetransparent`|強制 Annotator 工具將所有不具透明度註釋的組件視為完全透明。|  
|`/t`:*assembly*<br /><br /> 或<br /><br /> `/forcetransparent`:*assembly*|強制指定的組件呈現透明，無論目前組件層級註釋為何。|  
|||  
|`/v`<br /><br /> 或<br /><br /> `/verify`|只用於驗證組件的註釋是否正確，如果組件並未驗證，請勿為了找出所有必要的註釋而嘗試多次傳遞。|  
|`/x`<br /><br /> 或<br /><br /> `/verbose`|指定標註提供詳細輸出。|  
|`/y:` *directory*  ``<br /><br /> 或<br /><br /> `/symbolpath:` *directory*|註釋期間搜尋符號檔時包含指定的目錄。|  
  
## 備註  
 在命令列指定且前面加上一個 at 符號 \(@\) 的回應檔也可能會提供參數和組件。  回應檔中的每一行應該包含單一參數或組件名稱。  
  
 如需 .NET Security Annotator 的詳細資訊，請參閱 .NET Security 部落格中的項目 [使用 SecAnnotate 分析您的組件是否生透明度違規](http://go.microsoft.com/fwlink/?LinkId=187648)。  
  
## 範例