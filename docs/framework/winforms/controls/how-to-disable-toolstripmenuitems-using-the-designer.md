---
title: "如何：使用設計工具停用 ToolStripMenuItems | Microsoft Docs"
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
  - "功能表項目, 停用"
  - "功能表, 停用項目"
  - "MenuStrip 控制項 [Windows Form], 在設計工具中停用功能表項目"
  - "ToolStripMenuItems, 在設計工具中停用"
ms.assetid: 985e311e-7d67-4205-b5a3-d045b68a4a03
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：使用設計工具停用 ToolStripMenuItems
您可以限制或放寬使用者可透過啟用和停用功能表項目來執行的命令，以回應使用者活動。  根據預設，在建立功能表項目時就會啟用這些項目，但這一點可透過 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> 屬性做調整。  您可在執行階段於 \[**屬性**\] 視窗中管理這個屬性，或在程式碼中設定此屬性，以程式設計方式進行管理。  如需詳細資訊，請參閱 [如何：停用 ToolStripMenuItems](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要在設計階段停用功能表項目  
  
1.  使用在表單上選取的功能表項目，將 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> 屬性設定為 `false`。  
  
    > [!TIP]
    >  停用功能表中第一個或最上層的功能表項目，將會停用功能表內包含的所有功能表項目。  同樣的，停用具有子功能表項目的功能表項目，也會停用該子功能表項目。  如果使用者無法使用指定功能表上的所有命令時，隱藏並停用整個功能表會是個不錯的程式設計，因為這樣可以呈現單純的使用者介面。  由於單靠隱藏並不能防止利用快速鍵存取功能表命令，您應該隱藏並停用功能表。  將最上層功能表項目的 <xref:System.Windows.Forms.ToolStripItem.Visible%2A> 屬性設定為 `false`，以隱藏整個功能表。  
  
## 請參閱  
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ToolStripMenuItem>   
 [如何：隱藏 ToolStripMenuItems](../../../../docs/framework/winforms/controls/how-to-hide-toolstripmenuitems.md)   
 [MenuStrip 控制項概觀](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)