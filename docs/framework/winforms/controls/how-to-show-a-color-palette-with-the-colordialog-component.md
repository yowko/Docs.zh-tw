---
title: "如何：使用 ColorDialog 元件顯示色板"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- palettes [Windows Forms], showing color
- color dialog box [Windows Forms], showing color palettes
- colors [Windows Forms], allowing users to select
- color palettes [Windows Forms], dialog box
- ColorDialog component [Windows Forms], showing color palettes
- color palettes [Windows Forms], showing in ColorDialog component
- colors [Windows Forms], showing palettes
ms.assetid: ee050f61-dbc8-4436-ba22-51360981ab48
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: af773141039d049e010742f339ec4f9363d73cc3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-show-a-color-palette-with-the-colordialog-component"></a><span data-ttu-id="58841-102">如何：使用 ColorDialog 元件顯示色板</span><span class="sxs-lookup"><span data-stu-id="58841-102">How to: Show a Color Palette with the ColorDialog Component</span></span>
<span data-ttu-id="58841-103">[ColorDialog](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)元件會顯示色的調色盤，並傳回包含使用者所選取的色彩屬性。</span><span class="sxs-lookup"><span data-stu-id="58841-103">The [ColorDialog](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md) component displays a palette of colors and returns a property containing the color the user has selected.</span></span>  
  
### <a name="to-choose-a-color-using-the-colordialog-component"></a><span data-ttu-id="58841-104">選擇色彩，其使用 ColorDialog 元件</span><span class="sxs-lookup"><span data-stu-id="58841-104">To choose a color using the ColorDialog component</span></span>  
  
1.  <span data-ttu-id="58841-105">顯示對話方塊方塊使用<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="58841-105">Display the dialog box using the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
2.  <span data-ttu-id="58841-106">使用<xref:System.Windows.Forms.DialogResult>屬性來決定對話方塊關閉的方式。</span><span class="sxs-lookup"><span data-stu-id="58841-106">Use the <xref:System.Windows.Forms.DialogResult> property to determine how the dialog box was closed.</span></span>  
  
3.  <span data-ttu-id="58841-107">使用<xref:System.Windows.Forms.ColorDialog.Color%2A>屬性<xref:System.Windows.Forms.ColorDialog>設定所選的色彩的元件。</span><span class="sxs-lookup"><span data-stu-id="58841-107">Use the <xref:System.Windows.Forms.ColorDialog.Color%2A> property of the <xref:System.Windows.Forms.ColorDialog> component to set the chosen color.</span></span>  
  
     <span data-ttu-id="58841-108">在下列範例中，<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Click>事件處理常式會開啟<xref:System.Windows.Forms.ColorDialog>元件。</span><span class="sxs-lookup"><span data-stu-id="58841-108">In the example below, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens a <xref:System.Windows.Forms.ColorDialog> component.</span></span> <span data-ttu-id="58841-109">色彩選擇和使用者時按下**確定**、<xref:System.Windows.Forms.Button>控制項的背景色彩會設為選擇的色彩。</span><span class="sxs-lookup"><span data-stu-id="58841-109">When a color is chosen and the user clicks **OK**, the <xref:System.Windows.Forms.Button> control's background color is set to the chosen color.</span></span> <span data-ttu-id="58841-110">這個範例假設您的表單具有<xref:System.Windows.Forms.Button>控制項和<xref:System.Windows.Forms.ColorDialog>元件。</span><span class="sxs-lookup"><span data-stu-id="58841-110">The example assumes your form has a <xref:System.Windows.Forms.Button> control and a <xref:System.Windows.Forms.ColorDialog> component.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles Button1.Click  
       If ColorDialog1.ShowDialog() = DialogResult.OK Then  
          Button1.BackColor = ColorDialog1.Color  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(colorDialog1.ShowDialog() == DialogResult.OK)  
       {  
          button1.BackColor = colorDialog1.Color;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,   
          System::EventArgs ^ e)  
       {  
          if(colorDialog1->ShowDialog() == DialogResult::OK)  
          {  
             button1->BackColor = colorDialog1->Color;  
          }  
       }  
    ```  
  
     <span data-ttu-id="58841-111">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]、 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 請將下列程式碼置於表單的建構函式中，以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="58841-111">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=   
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="58841-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58841-112">See Also</span></span>  
 <xref:System.Windows.Forms.ColorDialog>  
 [<span data-ttu-id="58841-113">ColorDialog 元件</span><span class="sxs-lookup"><span data-stu-id="58841-113">ColorDialog Component</span></span>](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)
