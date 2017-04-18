---
title: "如何：在選擇工具箱項目對話方塊中顯示控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "全域組件快取, [選擇工具箱項目] 對話方塊"
  - "AssemblyFoldersEx, [選擇工具箱項目] 對話方塊"
  - "控制項, 在 [選擇工具箱項目] 對話方塊中顯示"
  - "組件資料夾註冊, [選擇工具箱項目] 對話方塊"
  - "[選擇工具箱項目] 對話方塊, 顯示控制項"
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：在選擇工具箱項目對話方塊中顯示控制項
當您在開發和散發控制項時，可能希望這些控制項能出現在 \[**選擇工具箱項目**\] 對話方塊中，這個對話方塊會在您以滑鼠按一下 \[**工具箱**\] 並選取 \[**選擇項目**\] 時顯示。  您可以使用 AssemblyFoldersEx 註冊程序，讓控制項出現在這個對話方塊中。  
  
### 若要在選擇工具箱項目對話方塊中顯示控制項  
  
-   將控制項組件安裝至全域組件快取。  如需詳細資訊，請參閱 [如何：將組件安裝到全域組件快取](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
  
     \-或\-  
  
-   使用 AssemblyFoldersEx 註冊程序來註冊控制項及其關聯的設計階段組件。  AssemblyFoldersEx 是註冊位置，協力廠商使用這個位置來儲存他們支援的每個架構版本的路徑。  設計階段解決方案可以查詢這個註冊位置，以尋找參考組件。  註冊指令碼可以指定要顯示在 \[工具箱\] 的控制項。  如需詳細資訊，請參閱[部署自訂控制項和設計階段屬性](http://msdn.microsoft.com/zh-tw/96158eb0-b691-4ae1-9e7b-3c65a1b798cb)。  
  
## 請參閱  
 [Choose Toolbox Items Dialog Box \(Visual Studio\)](http://msdn.microsoft.com/zh-tw/bd07835f-18a8-433e-bccc-7141f65263bb)   
 [部署自訂控制項和設計階段屬性](http://msdn.microsoft.com/zh-tw/96158eb0-b691-4ae1-9e7b-3c65a1b798cb)   
 [在設計階段開發 Windows Form 控制項](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)   
 [如何：將組件安裝到全域組件快取](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)   
 [逐步解說：自動將自訂元件填入工具箱](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)