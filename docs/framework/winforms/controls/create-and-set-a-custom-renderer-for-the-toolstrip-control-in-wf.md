---
title: "如何：建立和設定 Windows Form 中的 ToolStrip 控制項自訂產生器 | Microsoft Docs"
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
  - "範例 [Windows Form], 工具列"
  - "工具列 [Windows Form], 呈現"
  - "ToolStrip 控制項 [Windows Forms], 自訂呈現"
  - "ToolStrip 控制項 [Windows Forms], 呈現"
ms.assetid: 88a804ba-679f-4ba3-938a-0dc396199c5b
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：建立和設定 Windows Form 中的 ToolStrip 控制項自訂產生器
<xref:System.Windows.Forms.ToolStrip> 控制項提供了主題和樣式的簡單支援。  藉由將 <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=fullName> 屬性或 <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=fullName> 屬性設為自訂產生器，便可完全自訂外觀和行為 \(外觀及操作\)。  
  
 您可以將產生器指派給每個個別 <xref:System.Windows.Forms.ToolStrip>、<xref:System.Windows.Forms.MenuStrip>、<xref:System.Windows.Forms.ContextMenuStrip> 或 <xref:System.Windows.Forms.StatusStrip> 控制項，或者將 <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=fullName> 屬性設為 <xref:System.Windows.Forms.ToolStripRenderMode?displayProperty=fullName>，此時只要使用 <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> 屬性就能影響所有物件。  
  
> [!NOTE]
>  只要 <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=fullName> 值不為 `null`，<xref:System.Windows.Forms.ToolStrip.RenderMode%2A> 就會傳回 <xref:System.Windows.Forms.ToolStripRenderMode>。  
  
### 若要建立自訂產生器  
  
1.  擴充 <xref:System.Windows.Forms.ToolStripRenderer> 類別。  
  
2.  藉由覆寫適當的 *On…* 成員來實作所需的自訂產生器  
  
    ```vb  
    Public Class RedTextRenderer  
        Inherits System.Windows.Forms.ToolStripRenderer  
        Protected Overrides Sub OnRenderItemText(ByVal e As _  
            ToolStripItemTextRenderEventArgs)   
            e.TextColor = Color.Red  
            e.TextFont = New Font("Helvetica", 7, FontStyle.Bold)  
            MyBase.OnRenderItemText(e)  
        End Sub  
    End Class  
  
    ```  
  
     \[C\#\]  
  
    ```  
    public class RedTextRenderer : _  
        System.Windows.Forms.ToolStripRenderer  
    {  
        protected override void _  
            OnRenderItemText(ToolStripItemTextRenderEventArgs e)  
        {  
            e.TextColor = Color.Red;  
            e.TextFont = new Font("Helvetica", 7, FontStyle.Bold);  
           base.OnRenderItemText(e);  
        }  
    }  
  
    ```  
  
### 若要將自訂產生器設定為目前產生器  
  
1.  若要為某一個 <xref:System.Windows.Forms.ToolStrip> 設定自訂產生器，請將 <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=fullName> 屬性設為自訂產生器。  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
  
    ```  
  
     \[C\#\]  
  
    ```  
    toolStrip1.Renderer = new RedTextRenderer();  
  
    ```  
  
2.  或者，若要為所有 <xref:System.Windows.Forms.ToolStrip> 類別設定自訂產生器，請將 <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=fullName> 屬性設為自訂產生器並將 <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> 屬性設為 <xref:System.Windows.Forms.ToolStripRenderMode>。  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
  
    ```  
  
     \[C\#\]  
  
    ```  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>   
 <xref:System.Windows.Forms.ToolStripRenderer>   
 <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>   
 [ToolStrip 控制項概觀](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)   
 [ToolStrip 控制項架構](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)   
 [ToolStrip 技術摘要](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)