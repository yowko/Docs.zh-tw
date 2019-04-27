---
title: HOW TO：使用 ColorDialog 元件顯示調色盤
ms.date: 03/30/2017
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
ms.openlocfilehash: 587b2c3a502ec8a1cb2f4f7c0d981baa0f18ead6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012988"
---
# <a name="how-to-show-a-color-palette-with-the-colordialog-component"></a><span data-ttu-id="669a5-102">HOW TO：使用 ColorDialog 元件顯示調色盤</span><span class="sxs-lookup"><span data-stu-id="669a5-102">How to: Show a Color Palette with the ColorDialog Component</span></span>
<span data-ttu-id="669a5-103">[ColorDialog](colordialog-component-windows-forms.md)元件會顯示色的調色盤，並傳回包含使用者選取的色彩屬性。</span><span class="sxs-lookup"><span data-stu-id="669a5-103">The [ColorDialog](colordialog-component-windows-forms.md) component displays a palette of colors and returns a property containing the color the user has selected.</span></span>  
  
### <a name="to-choose-a-color-using-the-colordialog-component"></a><span data-ttu-id="669a5-104">若要選擇色彩，其使用 ColorDialog 元件</span><span class="sxs-lookup"><span data-stu-id="669a5-104">To choose a color using the ColorDialog component</span></span>  
  
1. <span data-ttu-id="669a5-105">顯示對話方塊方塊中，使用<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="669a5-105">Display the dialog box using the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
2. <span data-ttu-id="669a5-106">使用<xref:System.Windows.Forms.DialogResult>屬性來決定對話方塊關閉的方式。</span><span class="sxs-lookup"><span data-stu-id="669a5-106">Use the <xref:System.Windows.Forms.DialogResult> property to determine how the dialog box was closed.</span></span>  
  
3. <span data-ttu-id="669a5-107">使用<xref:System.Windows.Forms.ColorDialog.Color%2A>屬性<xref:System.Windows.Forms.ColorDialog>元件來設定選擇的色彩。</span><span class="sxs-lookup"><span data-stu-id="669a5-107">Use the <xref:System.Windows.Forms.ColorDialog.Color%2A> property of the <xref:System.Windows.Forms.ColorDialog> component to set the chosen color.</span></span>  
  
     <span data-ttu-id="669a5-108">在下列範例中，<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Click>事件處理常式會開啟<xref:System.Windows.Forms.ColorDialog>元件。</span><span class="sxs-lookup"><span data-stu-id="669a5-108">In the example below, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens a <xref:System.Windows.Forms.ColorDialog> component.</span></span> <span data-ttu-id="669a5-109">色彩選擇和使用者時按下 **[確定]**，則<xref:System.Windows.Forms.Button>控制項的背景色彩會設為選擇的色彩。</span><span class="sxs-lookup"><span data-stu-id="669a5-109">When a color is chosen and the user clicks **OK**, the <xref:System.Windows.Forms.Button> control's background color is set to the chosen color.</span></span> <span data-ttu-id="669a5-110">此範例假設您的表單具有<xref:System.Windows.Forms.Button>控制項和<xref:System.Windows.Forms.ColorDialog>元件。</span><span class="sxs-lookup"><span data-stu-id="669a5-110">The example assumes your form has a <xref:System.Windows.Forms.Button> control and a <xref:System.Windows.Forms.ColorDialog> component.</span></span>  
  
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
  
     <span data-ttu-id="669a5-111">(Visual C# [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 下列程式碼置於表單的建構函式，以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="669a5-111">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=   
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="669a5-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="669a5-112">See also</span></span>

- <xref:System.Windows.Forms.ColorDialog>
- [<span data-ttu-id="669a5-113">ColorDialog 元件</span><span class="sxs-lookup"><span data-stu-id="669a5-113">ColorDialog Component</span></span>](colordialog-component-windows-forms.md)
