---
title: "Windows Form 設計工具的設計階段錯誤 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DTELErrorList"
  - "WhyDTELPage"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "設計階段錯誤 [Windows Form 設計工具]"
  - "錯誤 [Windows Form 設計工具]"
ms.assetid: ad408380-825a-46d8-9a4a-531b130b88ce
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Windows Form 設計工具的設計階段錯誤
本主題說明當 Windows Form 設計工具載入失敗時，Microsoft Visual Studio 中所顯示設計階段錯誤清單的意義與使用方式。  如果出現此錯誤清單，您不應該將其視為設計工具的錯誤，反而要視為在程式碼更正錯誤的助益。  
  
 如果您對此錯誤清單有基本了解，則透過此清單提供之錯誤和建議可用解決方案的詳細資訊，可協助您偵錯應用程式。  
  
## 設計階段錯誤清單介面  
 如果在載入 Windows Form 設計工具時失敗，設計工具中就會出現錯誤清單。  這些錯誤會經過分類。  例如，您的未宣告變數有四個執行個體，則這些執行個體都會歸類於相同的錯誤分類。  每個錯誤分類都包含該錯誤的簡短摘要描述。  
  
 您可以按一下錯誤分類標題或按一下展開\/摺疊＞形箭號，展開或折疊錯誤分類。  當您展開錯誤分類，便會顯示下列額外說明：  
  
-   此錯誤的實例。  
  
-   此錯誤的說明。  
  
-   此錯誤的相關論壇文章。  
  
### 此錯誤的實例  
 此額外說明會列出目前專案中該錯誤的所有實例。  許多錯誤都包含格式如下的確切位置：*\[Project Name\]* *\[Form Name\]* 行數：*\[Line Number\]*資料行數：*\[Column Number\]*。  \[**移至程式碼**\] 連結會將您移至程式碼中發生錯誤的位置。  
  
 如果某個呼叫堆疊與此錯誤相關聯，您可以按一下 \[**呼叫堆疊顯示**\] 連結，以進一步展開錯誤來顯示呼叫堆疊。  檢查堆疊可提供寶貴的偵錯資訊。  例如，您可以追蹤發生錯誤之前所呼叫的功能。  由於呼叫堆疊是可選取的，因此，您可以加以複製和儲存。  
  
> [!NOTE]
>  在 Visual Basic 中，設計階段錯誤清單不會顯示一個以上的錯誤，但可顯示相同錯誤的多個實例。  在 Visual C\+\+ 中，錯誤都沒有 \[移至程式碼\] 連結 \/ \[行數\] 連結。  
  
### 此錯誤的說明  
 如果錯誤包含相關聯 MSDN 說明主題的連結，則額外說明也會包含該說明主題的連結。  當您按一下該連結，Visual Studio 中便會出現此相關聯的說明主題。  
  
### 此錯誤的相關論壇文章  
 額外說明會包含與此錯誤相關之 MSDN 論壇文章的連結。  您可以根據錯誤訊息的字串來搜尋論壇。  您也可以嘗試搜尋下列論壇：  
  
-   [Windows Form 設計工具論壇](http://go.microsoft.com/fwlink/?LinkId=203524) \(英文\)  
  
-   [Windows Form 論壇](http://go.microsoft.com/fwlink/?LinkId=203523) \(英文\)  
  
### 忽略並繼續  
 您可以選擇忽略錯誤狀況，然後繼續載入設計工具。  選擇這個動作可能會導致未預期的行為。  例如，控制項可能不會在設計介面中出現。  
  
## 請參閱  
 [Troubleshooting Design\-Time Development](../Topic/Troubleshooting%20Design-Time%20Development.md)   
 [控制項和元件撰寫疑難排解](../../../../docs/framework/winforms/controls/troubleshooting-control-and-component-authoring.md)   
 [在設計階段開發 Windows Form 控制項](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)   
 [Windows Forms Designer Error Messages](http://msdn.microsoft.com/zh-tw/cf610bf4-5fe4-471c-bce7-6a05ece07bd2)