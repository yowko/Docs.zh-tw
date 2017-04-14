---
title: "如何：隱藏 ToolStripMenuItems | Microsoft Docs"
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
  - "隱藏功能表項目"
  - "功能表項目, 隱藏"
  - "功能表, 隱藏功能表項目"
  - "MenuStrip 控制項 [Windows Form], 隱藏功能表項目"
  - "ToolStripMenuItems, 隱藏"
ms.assetid: 418a768f-808a-44cd-8cef-f4e161883621
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：隱藏 ToolStripMenuItems
隱藏功能表項目是控制您的應用程式使用者介面和限制使用者命令的方式。  通常，當功能表上的所有功能表項目都無法使用時，您會想要隱藏整個功能表。  這樣可以減少使用者的操作困擾。  此外，您可能會想要隱藏並停用功能表或功能表項目，因為單獨隱藏並無法防止使用者經由使用快速鍵存取功能表命令。  
  
### 若要以程式設計方式隱藏任何功能表項目  
  
-   在設定功能表項目屬性的方法內加入程式碼，將 <xref:System.Windows.Forms.ToolStripItem.Visible%2A> 屬性設定為 `false`。  
  
    ```vb  
    MenuItem3.Visible = False  
  
    ```  
  
    ```csharp  
    menuItem3.Visible = false;  
  
    ```  
  
    ```cpp  
    menuItem3->Visible = false;  
  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.ToolStripItem.Visible%2A>   
 <xref:System.Windows.Forms.MenuStrip>   
 [MenuStrip 控制項概觀](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)   
 [如何：停用 ToolStripMenuItems](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems.md)