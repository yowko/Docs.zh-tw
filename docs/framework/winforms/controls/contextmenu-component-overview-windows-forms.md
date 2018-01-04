---
title: "ContextMenu 元件概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ContextMenu
helpviewer_keywords:
- ContextMenu component [Windows Forms], about ContextMenu component
- context menus [Windows Forms], ContextMenu component
- shortcut menus [Windows Forms], ContextMenu component
ms.assetid: 49d6398f-d3c4-4679-84fa-1de07b68b05e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b0db67e8da97f380c3bb2eb9aab951628c4b6487
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="contextmenu-component-overview-windows-forms"></a>ContextMenu 元件概觀 (Windows Form)
> [!IMPORTANT]
>  雖然<xref:System.Windows.Forms.MenuStrip>和<xref:System.Windows.Forms.ContextMenuStrip>取代，並將功能加入至<xref:System.Windows.Forms.MainMenu>和<xref:System.Windows.Forms.ContextMenu>的舊版中，控制項<xref:System.Windows.Forms.MainMenu>和<xref:System.Windows.Forms.ContextMenu>您選擇保留的回溯相容性及供未來使用。  
  
 使用 Windows Form<xref:System.Windows.Forms.ContextMenu>元件，您可以提供使用者更容易存取的快顯功能表與選取的物件相關聯的常用命令。 快顯功能表中的項目通常是從主應用程式中其他位置出現的功能表項目的子集。 使用者通常可以存取捷徑功能表上按一下滑鼠右鍵。 在 Windows Form 上快顯功能表與相關聯的控制項。  
  
## <a name="key-properties"></a>索引鍵內容  
 您可以藉由設定控制項的捷徑功能表建立關聯的控制項一起<xref:System.Windows.Forms.Control.ContextMenu%2A>屬性<xref:System.Windows.Forms.ContextMenu>元件。 單一的捷徑功能表可以是多個控制項，與相關聯，但每個控制項都可以有只有一個快顯功能表。  
  
 索引鍵內容<xref:System.Windows.Forms.ContextMenu>元件是<xref:System.Windows.Forms.Menu.MenuItems%2A>屬性。 您可以加入功能表項目以程式設計方式建立<xref:System.Windows.Forms.MenuItem>物件並將它們加入至<xref:System.Windows.Forms.Menu.MenuItemCollection>的快顯功能表。 快顯功能表中的項目通常取自其他功能表，因為您會將它們複製，快顯功能表中最常加入項目。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.ContextMenu>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>
