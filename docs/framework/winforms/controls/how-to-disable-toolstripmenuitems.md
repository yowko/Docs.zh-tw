---
title: "如何：停用 ToolStripMenuItems | Microsoft Docs"
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
  - "停用功能表項目"
  - "功能表項目, 停用"
  - "功能表項目, 啟用"
  - "功能表, 停用功能表項目"
  - "ToolStripMenuItems, 停用"
  - "ToolStripMenuItems, 啟用"
ms.assetid: bcc1da84-50fd-41d2-8475-103b581d5654
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：停用 ToolStripMenuItems
您可以限制或放寬使用者可透過啟用和停用功能表項目來執行的命令，以回應使用者活動。  根據預設，在建立功能表項目時就會啟用這些項目，但這一點可透過 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> 屬性做調整。  您可在執行階段於 \[**屬性**\] 視窗中管理這個屬性，或在程式碼中設定此屬性，以程式設計方式進行管理。  
  
### 若要以程式設計方式停用功能表項目  
  
-   在設定功能表項目屬性的方法中，加入程式碼將 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> 屬性設定為 `false`。  
  
    ```vb  
    MenuItem1.Enabled = False  
    ```  
  
    ```csharp  
    menuItem1.Enabled = false;  
    ```  
  
    ```cpp  
    menuItem1->Enabled = false;  
    ```  
  
    > [!TIP]
    >  停用功能表中第一個或最上層的功能表項目，會隱藏功能表內包含的所有功能表項目，但是不會將它們停用。  同樣的，停用具有子功能表項目的功能表項目，會隱藏這些子功能表項目，但不會將它們停用。  如果使用者無法使用指定功能表上的所有命令時，隱藏並停用整個功能表會是個不錯的程式設計，因為這樣可以呈現單純的使用者介面。  由於單靠隱藏並不能防止利用快速鍵存取功能表命令，因此您應該隱藏並停用功能表，以及停用功能表中的每個項目和子功能表項目。  將最上層功能表項目的 <xref:System.Windows.Forms.ToolStripItem.Visible%2A> 屬性設定為 `false`，以隱藏整個功能表。  
  
## 請參閱  
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ToolStripMenuItem>   
 [如何：隱藏 ToolStripMenuItems](../../../../docs/framework/winforms/controls/how-to-hide-toolstripmenuitems.md)   
 [MenuStrip 控制項概觀](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)