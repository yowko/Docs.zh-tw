---
title: "StatusBar 控制項概觀 (Windows Form) | Microsoft Docs"
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
  - "StatusBar"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "狀態列"
  - "StatusBar 控制項 [Windows Form], 關於 StatusBar 控制項"
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# StatusBar 控制項概觀 (Windows Form)
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip> 和 <xref:System.Windows.Forms.ToolStripStatusLabel> 控制項會取代和加入功能至 <xref:System.Windows.Forms.StatusBar> 和 <xref:System.Windows.Forms.StatusBarPanel> 控制項；不過 <xref:System.Windows.Forms.StatusBar> 和 <xref:System.Windows.Forms.StatusBarPanel> 控制項會保留以提供回溯相容性和未來使用 \(如果您選擇要使用\)。  
  
 Windows Form [StatusBar 控制項](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) 在表單中會形成一個區域，通常是顯示在視窗的底部，應用程式可以在此區域顯示不同類型的狀態資訊。  <xref:System.Windows.Forms.StatusBar> 控制項上可能會有狀態列面板，以顯示圖示來表示狀態，或以動畫中的一連串圖示表示正在執行處理序 \(例如，[!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] 指出文件正在儲存中\)。  
  
## 使用 StatusBar 控制項  
 當滑鼠經過超連結 \(Hyperlink\) 時，Internet Explorer 利用狀態列表示網頁的 URL；[!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] 提供了頁面位置、區段位置，和編輯模式 \(取代及版本追蹤\) 的資訊；[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 則利用狀態列提供即時線上資訊，例如告訴您如何用停駐或浮動模式來操作可停駐視窗。  
  
 您可以將 <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> 屬性設定為 `false` \(預設值\)，並將狀態列的 <xref:System.Windows.Forms.StatusBar.Text%2A> 屬性設定為要出現在狀態列中的文字，即可在狀態列中顯示單一訊息。  您可以將狀態列分割成面板來顯示多類資訊，方法是將 <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> 屬性設定為 `true`，並使用 <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> 的 <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> 方法。  
  
## 請參閱  
 <xref:System.Windows.Forms.StatusBar>   
 <xref:System.Windows.Forms.ToolStripStatusLabel>   
 [如何：判斷在 Windows Form StatusBar 控制項中按下的面板](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)