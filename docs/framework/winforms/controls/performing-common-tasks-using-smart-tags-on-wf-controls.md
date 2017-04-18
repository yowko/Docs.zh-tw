---
title: "逐步解說：使用 Windows Form 控制項中的智慧標籤執行一般工作 | Microsoft Docs"
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
  - "設計工具動作"
  - "DesignerAction 物件模型"
  - "智慧標籤"
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 逐步解說：使用 Windows Form 控制項中的智慧標籤執行一般工作
在您建構 Windows Form 應用程式的表單和控制項時，您會重複執行許多工作。  您會遇到某些經常執行的工作：  
  
-   加入或移除 <xref:System.Windows.Forms.TabControl> 上的索引標籤。  
  
-   將控制項停駐在父代。  
  
-   變更 <xref:System.Windows.Forms.SplitContainer> 控制項的方向。  
  
 為了加快開發的速度，許多控制項都提供有智慧標籤，這些標籤是可讓您執行一般工作 \(例如在設計階段單一筆勢中的這些工作\) 的區分內容的功能表。  這些工作稱為「*智慧標籤動作*」\(Smart\-tag Verbs\)。  
  
 在設計工具中，智慧標籤在存留期 \(Lifetime\) 內都會保持附加至控制項執行個體的狀態，並且永遠都可使用。  
  
 逐步解說將說明的工作包括：  
  
-   建立 Windows Form 專案  
  
-   使用智慧標籤  
  
-   啟用和停用智慧標籤  
  
 當您完成時，將會對這些重要的配置功能所扮演的角色有所了解。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 建立專案  
 第一個步驟是建立專案並設定表單。  
  
#### 若要建立專案  
  
1.  建立名為「SmartTagsExample」的 Windows 架構應用程式專案。  如需詳細資訊，請參閱 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa)。  
  
2.  從 \[**Windows Form 設計工具**\] 中選取表單。  
  
## 使用智慧標籤  
 在設計階段時，永遠都可以在提供智慧標籤的控制項上使用智慧標籤。  
  
#### 若要使用智慧標籤  
  
1.  將 <xref:System.Windows.Forms.TabControl> 從 \[**工具箱**\] 拖曳到表單上。  請注意出現在 <xref:System.Windows.Forms.TabControl> 旁邊的智慧標籤圖像 \(![智慧標籤圖像](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.png "VS\_WinFormSmtTagGlyph")\)。  
  
2.  按一下智慧標籤圖像。  在顯示於圖像旁邊的捷徑功能表中，選取 \[**加入索引標籤**\] 項目。  觀察新的索引標籤頁已加入至 <xref:System.Windows.Forms.TabControl>。  
  
3.  從 \[**工具箱**\] 將 <xref:System.Windows.Forms.TableLayoutPanel> 控制項拖曳至表單。  
  
4.  按一下智慧標籤圖像。  在顯示於圖像旁邊的捷徑功能表中，選取 \[**加入資料行**\] 項目。  觀察新的資料行已加入至 <xref:System.Windows.Forms.TableLayoutPanel> 控制項。  
  
5.  從 \[**工具箱**\] 將 <xref:System.Windows.Forms.SplitContainer> 控制項拖曳至表單。  
  
6.  按一下智慧標籤圖像。  在顯示於圖像旁邊的捷徑功能表中，選取 \[**水平的分隔器方向**\] 項目。  觀察 <xref:System.Windows.Forms.SplitContainer> 控制項的分隔列現在是水平方向。  
  
## 請參閱  
 <xref:System.Windows.Forms.TextBox>   
 <xref:System.Windows.Forms.TabControl>   
 <xref:System.Windows.Forms.SplitContainer>   
 <xref:System.ComponentModel.Design.DesignerActionList>   
 [Walkthrough: Adding Smart Tags to a Windows Forms Component](../Topic/Walkthrough:%20Adding%20Smart%20Tags%20to%20a%20Windows%20Forms%20Component.md)