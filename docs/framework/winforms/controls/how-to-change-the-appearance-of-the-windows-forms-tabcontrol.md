---
title: "如何：變更 Windows Form TabControl 的外觀 | Microsoft Docs"
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
  - "按鈕, 顯示為標籤"
  - "圖示, 標籤上顯示"
  - "TabControl 控制項 [Windows Form], 變更頁面外觀"
  - "索引標籤, 控制外觀"
ms.assetid: 7c6cc443-ed62-4d26-b94d-b8913b44f773
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：變更 Windows Form TabControl 的外觀
您可以使用組成控制項上個別索引標籤的 <xref:System.Windows.Forms.TabControl> 和 <xref:System.Windows.Forms.TabPage> 物件的屬性，變更 Windows Form 中索引標籤的外觀。  藉由設定這些屬性，您可以顯示索引標籤上的影像、垂直 \(而非水平\) 顯示索引標籤、顯示多列的索引標籤，及以程式設計的方式啟用或停用索引標籤。  
  
### 若要顯示索引標籤的標籤部分之圖示  
  
1.  將 <xref:System.Windows.Forms.ImageList> 控制項加入表單。  
  
2.  將影像加入至影像清單 \(Image List\)。  
  
     如需影像清單的詳細資訊，請參閱 [ImageList 元件](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) 和 [如何：使用 Windows Form ImageList 元件加入或移除影像](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)。  
  
3.  將 <xref:System.Windows.Forms.TabControl> 的 <xref:System.Windows.Forms.TabControl.ImageList%2A> 屬性設定為 <xref:System.Windows.Forms.ImageList> 控制項。  
  
4.  將 <xref:System.Windows.Forms.TabPage> 的 <xref:System.Windows.Forms.TabPage.ImageIndex%2A> 屬性設定為清單中適當影像的索引。  
  
### 若要建立多列的索引標籤  
  
1.  加入您想要的索引標籤頁數目。  
  
2.  將 <xref:System.Windows.Forms.TabControl> 的 <xref:System.Windows.Forms.TabControl.Multiline%2A> 屬性設為 `true`。  
  
3.  如果索引標籤未以多列出現，請將 <xref:System.Windows.Forms.TabControl> 的 <xref:System.Windows.Forms.Control.Width%2A> 屬性設定為比所有索引標籤窄。  
  
### 若要排列控制項旁邊的索引標籤  
  
-   將 <xref:System.Windows.Forms.TabControl> 的 <xref:System.Windows.Forms.TabControl.Alignment%2A> 屬性設為 <xref:System.Windows.Forms.TabAlignment> 或 <xref:System.Windows.Forms.TabAlignment>。  
  
### 若要以程式設計方式啟用或停用索引標籤上的所有控制項  
  
1.  將 <xref:System.Windows.Forms.TabPage> 的 <xref:System.Windows.Forms.TabPage.Enabled%2A> 屬性設為 `true` 或 `false`。  
  
    ```vb  
    TabPage1.Enabled = False  
  
    ```  
  
    ```csharp  
    tabPage1.Enabled = false;  
  
    ```  
  
    ```cpp  
    tabPage1->Enabled = false;  
    ```  
  
### 若要將索引標籤顯示為按鈕  
  
-   將 <xref:System.Windows.Forms.TabControl> 的 <xref:System.Windows.Forms.TabControl.Appearance%2A> 屬性設為 <xref:System.Windows.Forms.TabAppearance> 或 <xref:System.Windows.Forms.TabAppearance>。  
  
## 請參閱  
 [TabControl 控制項](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)   
 [TabControl 控制項概觀](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)   
 [如何：將控制項加入至索引標籤頁](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)   
 [如何：停用索引標籤頁](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)   
 [如何：使用 Windows Form TabControl 加入和移除索引標籤](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)