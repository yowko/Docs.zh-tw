---
title: "如何：設定 MDI 應用程式的自動功能表合併功能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MenuStrip [Windows Forms], merging
- Merging [Windows Forms], automatic menu
ms.assetid: 55e32cad-1141-4a56-aa33-d9543ca3d393
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 14f9d956763685b5c03419515780ee2a6c3ede7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-up-automatic-menu-merging-for-mdi-applications"></a>如何：設定 MDI 應用程式的自動功能表合併功能
下列程序提供的基本步驟來設定中的多重文件介面 (MDI) 應用程式的自動合併<xref:System.Windows.Forms.MenuStrip>。  
  
### <a name="to-set-up-automatic-menu-merging"></a>若要設定自動功能表合併  
  
1.  建立 MDI 父表單藉由設定其<xref:System.Windows.Forms.Form.IsMdiContainer%2A>屬性`true`。  
  
2.  新增<xref:System.Windows.Forms.MenuStrip>到 MDI 父代，設定其<xref:System.Windows.Forms.Form.MainMenuStrip%2A>屬性的<xref:System.Windows.Forms.MenuStrip>。  
  
3.  建立 MDI 子表單，並設定其<xref:System.Windows.Forms.Form.MdiParent%2A>屬性設為父表單的名稱。  
  
4.  新增<xref:System.Windows.Forms.MenuStrip>MDI 子表單。  
  
5.  在子表單中，設定<xref:System.Windows.Forms.ToolStripItem.Visible%2A>屬性<xref:System.Windows.Forms.MenuStrip>至`false`。  
  
6.  將功能表項目加入至子表單的<xref:System.Windows.Forms.MenuStrip>您想要合併到父表單的<xref:System.Windows.Forms.MenuStrip>何時啟動子表單。  
  
7.  使用<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A>子表單中的內容功能表中的項目<xref:System.Windows.Forms.MenuStrip>來控制如何合併至父表單。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [MenuStrip 控制項概觀](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
