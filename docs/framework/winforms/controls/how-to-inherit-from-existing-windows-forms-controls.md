---
title: "如何：繼承自現有的 Windows Form 控制項 | Microsoft Docs"
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
  - "自訂控制項 [Windows Form], 繼承"
  - "繼承, Windows Form 自訂控制項"
ms.assetid: 1e1fc8ea-c615-4cf0-a356-16d6df7444ab
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 如何：繼承自現有的 Windows Form 控制項
如果您要擴充現有控制項的功能，您可以建立透過繼承而從現有控制項衍生控制項。  繼承現有控制項時，您將繼承該控制項的所有功能和視覺屬性。  例如，如果您建立繼承 <xref:System.Windows.Forms.Button> 的控制項時，則新控制項的外觀和動作將和標準的 <xref:System.Windows.Forms.Button> 控制項完全一樣。  然後您可以透過自訂方法和屬性的實作，來擴充或修改新控制項的功能。  在部分控制項中，您也可以覆寫其 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法來變更您所繼承控制項的視覺外觀。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要建立繼承的控制項  
  
1.  建立新的 \[**Windows Form 應用程式**\] 專案。  
  
2.  從 \[**專案**\] 功能表選擇 \[**加入新項目**\]。  
  
     \[**加入新項目**\] 對話方塊隨即出現。  
  
3.  在 \[**加入新項目**\] 對話方塊中，按兩下 \[**自訂控制項**\]。  
  
     新的自訂控制項將加入至您的專案中。  
  
4.  如果您是使用 Visual Basic，請按一下 \[**方案總管**\] 頂端的 \[**顯示所有檔案**\]。  展開 \[CustomControl1.vb\]，然後在 \[程式碼編輯器\] 中開啟 \[CustomControl1.Designer.vb\]。  
  
5.  如果您是使用 C\#，請在 \[程式碼編輯器\] 中開啟 \[CustomControl1.cs\]。  
  
6.  尋找類別宣告，它是繼承自 <xref:System.Windows.Forms.Control>。  
  
7.  將基底類別變更為要做為繼承來源的控制項。  
  
     例如，如果您要繼承自 <xref:System.Windows.Forms.Button>，則將類別宣告變更為下列內容：  
  
    ```vb  
    Partial Class CustomControl1  
        Inherits System.Windows.Forms.Button  
    ```  
  
    ```csharp  
    public partial class CustomControl1 : System.Windows.Forms.Button  
    ```  
  
8.  如果您是使用 Visual Basic，則儲存並關閉 \[CustomControl1.Designer.vb\]。  在 \[程式碼編輯器\] 中開啟 \[CustomControl1.vb\]。  
  
9. 實作您的控制項將加入的任何自訂方法或屬性。  
  
10. 如果要修改控制項的圖形外觀，請覆寫 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法。  
  
    > [!NOTE]
    >  覆寫 <xref:System.Windows.Forms.Control.OnPaint%2A> 將無法讓您修改所有控制項的外觀。  如果某些控制項的繪製都是由 Windows 所完成的 \(例如，<xref:System.Windows.Forms.TextBox>\)，則這些控制項一定不會呼叫其 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法，因此也一定不會使用自訂程式碼。  請參閱要修改的特定控制項的說明文件，以查看是否可以使用 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法。  如需所有 Windows Form 控制項的清單，請參閱[在 Windows Form 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)。  如果控制項沒有將 <xref:System.Windows.Forms.Control.OnPaint%2A> 列為成員方法，則您無法藉由覆寫這個方法來變更其外觀。  如需自訂繪製的詳細資訊，請參閱[自訂控制項繪製和轉譯](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)。  
  
    ```vb  
    Protected Overrides Sub OnPaint(ByVal e As _  
       System.Windows.Forms.PaintEventArgs)  
       MyBase.OnPaint(e)  
       ' Insert code to do custom painting.   
       ' If you want to completely change the appearance of your control,  
       ' do not call MyBase.OnPaint(e).  
    End Sub  
  
    ```  
  
    ```csharp  
    protected override void OnPaint(PaintEventArgs pe)  
    {  
       base.OnPaint(pe);  
       // Insert code to do custom painting.  
       // If you want to completely change the appearance of your control,  
       // do not call base.OnPaint(pe).  
    }  
    ```  
  
11. 儲存和測試您的控制項。  
  
## 請參閱  
 [各種自訂控制項](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)   
 [如何：繼承自 Control 類別](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)   
 [如何：繼承自 UserControl 類別](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)   
 [如何：撰寫 Windows Form 的控制項](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)   
 [Troubleshooting Inherited Event Handlers in Visual Basic](../Topic/Troubleshooting%20Inherited%20Event%20Handlers%20in%20Visual%20Basic.md)   
 [逐步解說：使用 Visual Basic 繼承自 Windows Form 控制項](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)   
 [逐步解說：使用 Visual C\# 繼承自 Windows Form 控制項](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)