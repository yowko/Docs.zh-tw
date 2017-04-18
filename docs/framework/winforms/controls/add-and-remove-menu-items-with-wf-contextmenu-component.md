---
title: "如何：使用 Windows Form ContextMenu 元件加入和移除功能表項目 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "內容功能表, 加入項目"
  - "內容功能表, 範例"
  - "內容功能表, 移除項目"
  - "ContextMenu 元件 [Windows Form], 加入項目"
  - "ContextMenu 元件 [Windows Form], 移除項目"
  - "範例 [Windows Form], 內容功能表"
  - "捷徑功能表, 加入項目"
  - "捷徑功能表, 範例"
  - "捷徑功能表, 移除項目"
ms.assetid: 426d1eaf-7fb8-4b0b-8a33-5e8721786ea4
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：使用 Windows Form ContextMenu 元件加入和移除功能表項目
說明如何在 Windows Form 中加入和移除捷徑功能表項目。  
  
 Windows Form 的 <xref:System.Windows.Forms.ContextMenu> 元件提供與所選物件相關的常用命令表單。  您可以藉由新增 <xref:System.Windows.Forms.MenuItem> 物件至 <xref:System.Windows.Forms.Menu.MenuItems%2A> 集合，將項目加入至捷徑功能表。  
  
 您可以將項目從捷徑功能表中永久移除；然而，在執行階段時將項目隱藏或停用，可能會是比較適合的作法。  
  
> [!IMPORTANT]
>  雖然 <xref:System.Windows.Forms.MenuStrip> 和 <xref:System.Windows.Forms.ContextMenuStrip> 會取代和加入功能至舊版的 <xref:System.Windows.Forms.MainMenu> 和 <xref:System.Windows.Forms.ContextMenu> 控制項，但是會保留 <xref:System.Windows.Forms.MainMenu> 和 <xref:System.Windows.Forms.ContextMenu> 以提供回溯相容性 \(Backward Compatibility\) 和未來使用 \(如果您選擇要用\)。  
  
### 若要從捷徑功能表移除項目  
  
1.  使用 <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> 或 <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> 方法 \(在 <xref:System.Windows.Forms.ContextMenu> 元件的 <xref:System.Windows.Forms.Menu.MenuItems%2A> 集合中\) 來移除特定的功能表項目。  
  
    ```vb  
    ' Removes the first item in the shortcut menu.  
    ContextMenu1.MenuItems.RemoveAt(0)  
    ' Removes a particular object from the shortcut menu.  
    ContextMenu1.MenuItems.Remove(mnuItemNew)  
  
    ```  
  
    ```csharp  
    // Removes the first item in the shortcut menu.  
    contextMenu1.MenuItems.RemoveAt(0);  
    // Removes a particular object from the shortcut menu.  
    contextMenu1.MenuItems.Remove(mnuItemNew);  
  
    ```  
  
    ```cpp  
    // Removes the first item in the shortcut menu.  
    contextMenu1->MenuItems->RemoveAt(0);  
    // Removes a particular object from the shortcut menu.  
    contextMenu1->MenuItems->Remove(mnuItemNew);  
    ```  
  
     \-或\-  
  
2.  使用 `Clear` 方法 \(在 <xref:System.Windows.Forms.ContextMenu> 元件的 `MenuItems` 集合中\) 來移除所有功能表的項目。  
  
    ```vb  
    ContextMenu1.MenuItems.Clear()  
  
    ```  
  
    ```csharp  
    contextMenu1.MenuItems.Clear();  
  
    ```  
  
    ```cpp  
    contextMenu1->MenuItems->Clear();  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.ContextMenu>   
 [ContextMenu 元件](../../../../docs/framework/winforms/controls/contextmenu-component-windows-forms.md)   
 [ContextMenu 控制項概觀](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md)