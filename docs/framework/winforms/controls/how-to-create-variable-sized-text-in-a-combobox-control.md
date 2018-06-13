---
title: 如何：在 ComboBox 控制項中建立各種大小的文字
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- text [Windows Forms], drawing in combo boxes
- examples [Windows Forms], ComboBox control
- combo boxes [Windows Forms], drawing text
- ComboBox control [Windows Forms], examples [C#]
- ComboBox control [Windows Forms], drawing custom text
ms.assetid: ce39b9ea-e626-49fe-bd5a-f567f6d157df
ms.openlocfilehash: a76e1d78cd9fade550fa846488e8bf4a93a21c31
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533227"
---
# <a name="how-to-create-variable-sized-text-in-a-combobox-control"></a><span data-ttu-id="6f62c-102">如何：在 ComboBox 控制項中建立各種大小的文字</span><span class="sxs-lookup"><span data-stu-id="6f62c-102">How to: Create Variable Sized Text in a ComboBox Control</span></span>
<span data-ttu-id="6f62c-103">這個範例會示範自訂繪圖中的文字<xref:System.Windows.Forms.ComboBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="6f62c-103">This example demonstrates custom drawing of text in a <xref:System.Windows.Forms.ComboBox> control.</span></span> <span data-ttu-id="6f62c-104">當項目符合特定準則時，它是在較大的字型中繪製，變成紅色。</span><span class="sxs-lookup"><span data-stu-id="6f62c-104">When an item meets a certain criteria, it is drawn in a larger font and turned red.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f62c-105">範例</span><span class="sxs-lookup"><span data-stu-id="6f62c-105">Example</span></span>  
  
```vb  
Private Sub ComboBox1_MeasureItem(ByVal sender As Object, ByVal e As _  
System.Windows.Forms.MeasureItemEventArgs) Handles ComboBox1.MeasureItem  
    Dim bFont As New Font("Arial", 8, FontStyle.Bold)  
    Dim lFont As New Font("Arial", 12, FontStyle.Bold)  
    Dim siText As SizeF  
  
    If ComboBox1.Items().Item(e.Index) = "Two" Then  
        siText = e.Graphics.MeasureString(ComboBox1.Items().Item(e.Index), _  
lFont)  
    Else  
        siText = e.Graphics.MeasureString(ComboBox1.Items().Item(e.Index), bFont)  
    End If  
  
    e.ItemHeight = siText.Height  
    e.ItemWidth = siText.Width  
End Sub  
  
Private Sub ComboBox1_DrawItem(ByVal sender As Object, ByVal e As _  
System.Windows.Forms.DrawItemEventArgs) Handles ComboBox1.DrawItem  
    Dim g As Graphics = e.Graphics  
    Dim bFont As New Font("Arial", 8, FontStyle.Bold)  
    Dim lFont As New Font("Arial", 12, FontStyle.Bold)  
  
    If ComboBox1.Items().Item(e.Index) = "Two" Then  
        g.DrawString(ComboBox1.Items.Item(e.Index), lfont, Brushes.Red, _  
e.Bounds.X, e.Bounds.Y)  
    Else  
        g.DrawString(ComboBox1.Items.Item(e.Index), bFont, Brushes.Black, e.Bounds.X, e.Bounds.Y)  
    End If  
End Sub  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6f62c-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="6f62c-106">Compiling the Code</span></span>  
 <span data-ttu-id="6f62c-107">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="6f62c-107">This example requires:</span></span>  
  
-   <span data-ttu-id="6f62c-108">Windows form。</span><span class="sxs-lookup"><span data-stu-id="6f62c-108">A Windows form.</span></span>  
  
-   <span data-ttu-id="6f62c-109">A<xref:System.Windows.Forms.ComboBox>控制項，名為`ListBox1`與中的三個項目<xref:System.Windows.Forms.ComboBox.Items%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="6f62c-109">A <xref:System.Windows.Forms.ComboBox> control named `ListBox1` with three items in the <xref:System.Windows.Forms.ComboBox.Items%2A> property.</span></span> <span data-ttu-id="6f62c-110">在此範例中，三個項目會命名為`"One", Two", and Three"`。</span><span class="sxs-lookup"><span data-stu-id="6f62c-110">In this example, the three items are named `"One", Two", and Three"`.</span></span> <span data-ttu-id="6f62c-111"><xref:System.Windows.Forms.ComboBox.DrawMode%2A>屬性`ComboBox1`必須設為<xref:System.Windows.Forms.DrawMode.OwnerDrawVariable>。</span><span class="sxs-lookup"><span data-stu-id="6f62c-111">The <xref:System.Windows.Forms.ComboBox.DrawMode%2A> property of `ComboBox1` must be set to <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6f62c-112">這項技術也會適用於<xref:System.Windows.Forms.ListBox>控制項，您可以取代<xref:System.Windows.Forms.ListBox>如<xref:System.Windows.Forms.ComboBox>。</span><span class="sxs-lookup"><span data-stu-id="6f62c-112">This technique is also applicable to the <xref:System.Windows.Forms.ListBox> control — you can substitute a <xref:System.Windows.Forms.ListBox> for the <xref:System.Windows.Forms.ComboBox>.</span></span>  
  
-   <span data-ttu-id="6f62c-113"><xref:System.Windows.Forms?displayProperty=nameWithType> 和 <xref:System.Drawing?displayProperty=nameWithType> 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="6f62c-113">References to the <xref:System.Windows.Forms?displayProperty=nameWithType> and <xref:System.Drawing?displayProperty=nameWithType> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f62c-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f62c-114">See Also</span></span>  
 <xref:System.Windows.Forms.ComboBox.DrawItem>  
 <xref:System.Windows.Forms.DrawItemEventArgs>  
 <xref:System.Windows.Forms.ComboBox.MeasureItem>  
 [<span data-ttu-id="6f62c-115">使用內建主控描繪支援的控制項</span><span class="sxs-lookup"><span data-stu-id="6f62c-115">Controls with Built-In Owner-Drawing Support</span></span>](../../../../docs/framework/winforms/controls/controls-with-built-in-owner-drawing-support.md)  
 [<span data-ttu-id="6f62c-116">ListBox 控制項</span><span class="sxs-lookup"><span data-stu-id="6f62c-116">ListBox Control</span></span>](../../../../docs/framework/winforms/controls/listbox-control-windows-forms.md)  
 [<span data-ttu-id="6f62c-117">ComboBox 控制項</span><span class="sxs-lookup"><span data-stu-id="6f62c-117">ComboBox Control</span></span>](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md)
