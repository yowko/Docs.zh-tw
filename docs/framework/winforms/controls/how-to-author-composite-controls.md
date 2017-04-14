---
title: "如何：撰寫複合控制項 | Microsoft Docs"
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
  - "複合控制項, 建立"
  - "使用者控制項 [Windows Form], 建立"
  - "使用者控制項 [Windows Form], 繼承自"
  - "UserControl 類別, 建立複合控制項"
ms.assetid: 79c9cf05-5ab6-4a18-886d-88a64748b098
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：撰寫複合控制項
複合控制項 \(Composite Control\) 可用於許多方面。  您可以將它們撰寫為 Windows 桌面應用程式專案的一部分，並且只在專案的表單上使用它們。  或者您可以在 Windows 控制項程式庫專案中撰寫它們、將專案編譯成組件 \(Assembly\)，並在其他專案中使用控制項。  您甚至可以繼承它們，然後針對特殊目的，使用視覺繼承來快速自訂它們。  
  
> [!NOTE]
>  如果您想要撰寫使用於 Web Form 上的複合控制項，請參閱 [Developing Custom ASP.NET Server Controls](../Topic/Developing%20Custom%20ASP.NET%20Server%20Controls.md)。  
>   
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要撰寫複合控制項  
  
1.  開啟名為 `DemoControlHost` 的新 \[**Windows 應用程式**\] 專案。  
  
2.  在 \[**專案**\] 功能表上，按一下 \[**加入使用者控制項**\]。  
  
3.  在 \[**加入新項目**\] 對話方塊中，提供您希望複合控制項擁有的名稱給類別檔案 \(.vb 或 .cs 檔\)。  
  
4.  按一下 \[**加入**\] 按鈕以建立複合控制項的類別檔案。  
  
5.  從 \[**工具箱**\] 將控制項加入至複合控制項介面。  
  
6.  在事件程序中放置程式碼，以便處理複合控制項或其構成控制項所引發的事件。  
  
7.  關閉複合控制項的設計工具，並在接到提示時儲存檔案。  
  
8.  在 \[**建置**\] 功能表上，按一下 \[**建置方案**\]。  
  
     必須建置專案，自訂控制項才能出現在 \[**工具箱**\] 中。  
  
9. 使用 \[**工具箱**\] 的 \[**DemoControlHost**\] 索引標籤，將控制項的執行個體加入至 `Form1`。  
  
### 若要撰寫控制項類別程式庫  
  
1.  開啟新的 \[**Windows 控制項程式庫**\] 專案。  
  
     根據預設，專案包含有複合控制項。  
  
2.  如以上程序所述加入控制項和程式碼。  
  
3.  選擇不要繼承類別變更的控制項，並將這個控制項的 \[**Modifiers**\] 屬性設定為 \[**Private**\]。  
  
4.  建置 DLL。  
  
### 若要繼承控制項類別程式庫中的複合控制項  
  
1.  在 \[**檔案**\] 功能表上指向 \[**加入**\]，然後按一下 \[**新增專案**\]，以加入新的 \[**Windows 應用程式**\] 專案至方案。  
  
2.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下新專案的 \[**參考**\] 資料夾，並選擇 \[**加入參考**\] 以開啟 \[**加入參考**\] 對話方塊。  
  
3.  選取 \[**專案**\] 索引標籤並且按兩下您的控制項程式庫專案。  
  
4.  在 \[**建置**\] 功能表上，按一下 \[**建置方案**\]。  
  
5.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下控制項程式庫專案，然後從捷徑功能表中選取 \[**加入新項目**\]。  
  
6.  從 \[**加入新項目**\] 對話方塊選取 \[**繼承的使用者控制項**\] 樣板。  
  
7.  在 \[**繼承選取器**\] 對話方塊中，按兩下要繼承的控制項。  
  
     新的控制項已加入至您的專案中。  
  
8.  開啟新控制項的視覺設計工具，及加入額外的組成控制項。  
  
     您可以看到繼承自 DLL 的複合控制項的組成控制項，而且可以改變 \[**Modifiers**\] 屬性為 \[**Public**\] 的控制項屬性。  您無法變更 \[**Modifiers**\] 屬性為 \[**Private**\] 的控制項屬性。  
  
## 請參閱  
 [逐步解說：使用 Visual Basic 撰寫複合控制項](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)   
 [逐步解說：使用 Visual C\# 撰寫複合控制項](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)   
 [逐步解說：使用 Visual Basic 繼承自 Windows Form 控制項](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)   
 [逐步解說：使用 Visual C\# 繼承自 Windows Form 控制項](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)   
 [控制項類型建議](../../../../docs/framework/winforms/controls/control-type-recommendations.md)   
 [如何：撰寫 Windows Form 的控制項](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)   
 [各種自訂控制項](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)