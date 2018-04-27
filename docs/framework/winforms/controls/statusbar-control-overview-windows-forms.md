---
title: StatusBar 控制項概觀 (Windows Form)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8e84ae7d62649c0c547417e954560ac0faccafdd
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="statusbar-control-overview-windows-forms"></a>StatusBar 控制項概觀 (Windows Form)
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip>和<xref:System.Windows.Forms.ToolStripStatusLabel>控制項取代，並將功能加入至<xref:System.Windows.Forms.StatusBar>和<xref:System.Windows.Forms.StatusBarPanel>控制項，不過，<xref:System.Windows.Forms.StatusBar>和<xref:System.Windows.Forms.StatusBarPanel>控制項是被保留為回溯相容性及未來使用，如果您選擇。  
  
 Windows Form [StatusBar 控制項](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md)可在表單區域的區域，通常會顯示在視窗中，在其中應用程式可以顯示各種狀態資訊的底部。 <xref:System.Windows.Forms.StatusBar> 控制項可以有狀態列面板上顯示文字或圖示以表示狀態或一系列的動畫圖示，以指出程序可以運作。例如，[!INCLUDE[ofprword](../../../../includes/ofprword-md.md)]表示正在儲存文件。  
  
## <a name="using-the-statusbar-control"></a>使用 StatusBar 控制項  
 Internet Explorer 使用狀態列表示網頁的 URL，當滑鼠彙總超連結。[!INCLUDE[ofprword](../../../../includes/ofprword-md.md)]提供您資訊頁面的位置、 區段位置，以及編輯模式，例如取代和追蹤修訂; 和 Visual Studio 會使用狀態列讓內容相關資訊，例如告訴您如何管理可停駐視窗為停駐或浮動。  
  
 您可以藉由設定 [狀態] 列上顯示單一訊息<xref:System.Windows.Forms.StatusBar.ShowPanels%2A>屬性`false`（預設值） 和設定<xref:System.Windows.Forms.StatusBar.Text%2A>至您想要顯示在狀態列中文字的 [狀態] 列的屬性。 [狀態] 列分成面板，以顯示多種類型的資訊，藉由設定<xref:System.Windows.Forms.StatusBar.ShowPanels%2A>屬性`true`和使用<xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A>方法<xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [操作說明：判斷在 Windows Forms StatusBar 控制項中按下的面板](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)
