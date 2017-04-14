---
title: "如何：測試 UserControl 的執行階段行為 | Microsoft Docs"
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
  - "複合控制項, 測試"
  - "使用者控制項 [Windows Form], 測試"
  - "UserControl 類別, 執行階段行為"
  - "UserControl 類別, 測試"
  - "UserControl 測試容器"
ms.assetid: 4e4d5c49-1346-40ac-9d96-40211b573583
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：測試 UserControl 的執行階段行為
當您開發 <xref:System.Windows.Forms.UserControl> 時，會需要測試執行階段行為。  您可以建立個別的 Windows 架構應用程式專案，並將控制項放置在測試表單上，但是這個程序並不方便。  較快速而輕鬆的方式便是使用 Visual Studio 所提供的 \[**使用者控制項測試容器**\]。  這個測試容器可直接從您的 Windows 控制項程式庫專案啟動。  
  
> [!IMPORTANT]
>  若要測試容器載入您的 <xref:System.Windows.Forms.UserControl>，控制項就必須擁有至少一個公用建構函式。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
> [!NOTE]
>  Visual C\+\+ 控制項不可以使用 \[**使用者控制項測試容器**\] 進行測試。  
  
### 若要測試使用者控制項的執行階段行為  
  
1.  建立名為 TestContainerExample 的 Windows 控制項程式庫專案。  如需詳細資訊，請參閱[Windows Control Library Template](http://msdn.microsoft.com/zh-tw/722f4e2d-1310-4ed5-8f33-593337ab66b4)。  
  
2.  在 \[**Windows Form 設計工具**\] 中，將 <xref:System.Windows.Forms.Label> 控制項從 \[**工具箱**\] 拖曳至控制項的設計介面。  
  
3.  按下 F5 以建置專案，並在 \[**使用者控制項測試容器**\] 中執行。  在 \[**預覽**\] 窗格中會出現測試容器和 <xref:System.Windows.Forms.UserControl>。  
  
4.  選取顯示於 \[**預覽**\] 窗格右邊的 <xref:System.Windows.Forms.PropertyGrid> 控制項中的 <xref:System.Windows.Forms.Control.BackColor%2A> 屬性。  將值變更為 `ControlDark`。  觀察控制項變更為較暗的顏色。  嘗試變更其他的屬性值，並觀察在控制項上的作用。  
  
5.  按一下 \[**預覽**\] 窗格下方的 \[**停駐填滿使用者控制項**\] 核取方塊。  觀察控制項調整大小以填滿窗格。  調整測試容器大小，並觀察控制項會根據窗格調整大小。  
  
6.  關閉測試容器。  
  
7.  加入另一個使用者控制項至 TestContainerExample 專案。  如需詳細資訊，請參閱 [NIB:How to: Add Existing Items to a Project](http://msdn.microsoft.com/zh-tw/15f4cfb7-78ab-457f-9f14-099a25a6a2d3)。  
  
8.  在 \[**Windows Form 設計工具**\] 中，將 <xref:System.Windows.Forms.Button> 控制項從 \[**工具箱**\] 拖曳至控制項的設計介面。  
  
9. 按 F5 以建置專案並執行測試容器。  
  
10. 按一下 \[**選取使用者控制項**\] <xref:System.Windows.Forms.ComboBox> 以便在兩個使用者控制項之間切換。  
  
## 從另一個專案測試使用者控制項  
 您可以從目前專案之測試容器中的其他專案測試使用者控制項。  
  
#### 若要從另一個專案測試使用者控制項  
  
1.  建立名為 TestContainerExample2 的 Windows 控制項程式庫專案。  如需詳細資訊，請參閱[Windows Control Library Template](http://msdn.microsoft.com/zh-tw/722f4e2d-1310-4ed5-8f33-593337ab66b4)。  
  
2.  在 \[**Windows Form 設計工具**\] 中，將 <xref:System.Windows.Forms.RadioButton> 控制項從 \[**工具箱**\] 拖曳至控制項的設計介面。  
  
3.  按 F5 以建置專案並執行測試容器。  在 \[**預覽**\] 窗格中會出現測試容器和 <xref:System.Windows.Forms.UserControl>。  
  
4.  按一下 \[**載入**\] 按鈕。  
  
5.  在 \[**開啟**\] 對話方塊中，巡覽至您在前一程序所建置的 TestContainerExample.dll。  選取 TestContainerExample.dll 並按一下 \[**開啟**\] 按鈕，以載入使用者控制項。  
  
6.  使用 \[**選取使用者控制項**\] <xref:System.Windows.Forms.ComboBox> 以便在 TestContainerExample 專案的兩個使用者控制項之間切換。  
  
## 請參閱  
 <xref:System.Windows.Forms.UserControl>   
 [如何：撰寫複合控制項](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)   
 [逐步解說：使用 Visual Basic 撰寫複合控制項](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)   
 [逐步解說：使用 Visual C\# 撰寫複合控制項](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)   
 [User Control Designer](http://msdn.microsoft.com/zh-tw/2abb9eec-ba32-45cb-b73d-8b52a8bd6bf1)