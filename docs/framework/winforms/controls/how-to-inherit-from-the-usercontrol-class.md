---
title: "如何：繼承自 UserControl 類別 | Microsoft Docs"
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
  - "繼承, Windows Form 自訂控制項"
  - "使用者控制項 [Windows Form], 建立"
  - "UserControl 類別, 繼承自"
ms.assetid: 67713625-e2e4-4f6a-bce7-0855ee5043d9
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：繼承自 UserControl 類別
如果您要將一或多個 Windows Form 控制項的功能與自訂程式碼結合，就必須建立「*使用者控制項*」。  使用者控制項結合快速控制項開發、標準 Windows Form 控制項功能，及自訂屬性和方法的多樣化功能。  建立使用者控制項時，會顯示可見的設計工具，您可使用它來放置標準的 Windows Form 控制項。  這些控制項會保留所有的固有功能，以及標準控制項的外觀和行為 \(外觀及操作\)。  然而，一旦這些控制項建置到使用者控制項時，就無法再透過程式碼使用它們了。  使用者控制項執行它們自己的繪製，也處理控制項相關的所有基本功能。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要建立使用者控制項  
  
1.  建立新的 \[**Windows 控制項程式庫**\] 專案。  
  
     新專案將以空白的使用者控制項建立。  
  
2.  將控制項從 \[**工具箱**\] 的 \[**Windows Form**\] 索引標籤拖曳至您的設計工具。  
  
3.  當您要這些控制項出現在最終的使用者控制項時，您必須放置和設計它們。  如果您要允許開發者存取組成控制項 \(Constituent Control\)，您必須將它們宣告為公用，或選擇性地公開組成控制項的屬性。  如需詳細資訊，請參閱 [如何：公開組成控制項的屬性](../../../../docs/framework/winforms/controls/how-to-expose-properties-of-constituent-controls.md)。  
  
4.  實作您的控制項將加入的任何自訂方法或屬性。  
  
5.  按下 F5 鍵以建置專案，並在 \[**使用者控制項測試容器**\] 中執行控制項。  如需詳細資訊，請參閱 [如何：測試 UserControl 的執行階段行為](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)。  
  
## 請參閱  
 [各種自訂控制項](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)   
 [如何：繼承自 Control 類別](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)   
 [如何：繼承自現有的 Windows Form 控制項](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)   
 [如何：撰寫 Windows Form 的控制項](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)   
 [Troubleshooting Inherited Event Handlers in Visual Basic](../Topic/Troubleshooting%20Inherited%20Event%20Handlers%20in%20Visual%20Basic.md)   
 [如何：測試 UserControl 的執行階段行為](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)