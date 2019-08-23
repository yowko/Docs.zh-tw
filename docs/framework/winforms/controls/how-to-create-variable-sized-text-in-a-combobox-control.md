---
title: 作法：在 ComboBox 控制項中建立各種大小的文字
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
ms.openlocfilehash: 7c0dc40f6cac0af1f88e72089865caa3a17fcf2a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914740"
---
# <a name="how-to-create-variable-sized-text-in-a-combobox-control"></a><span data-ttu-id="084ce-102">作法：在 ComboBox 控制項中建立各種大小的文字</span><span class="sxs-lookup"><span data-stu-id="084ce-102">How to: Create Variable Sized Text in a ComboBox Control</span></span>
<span data-ttu-id="084ce-103">這個範例示範<xref:System.Windows.Forms.ComboBox>控制項中文字的自訂繪製。</span><span class="sxs-lookup"><span data-stu-id="084ce-103">This example demonstrates custom drawing of text in a <xref:System.Windows.Forms.ComboBox> control.</span></span> <span data-ttu-id="084ce-104">當專案符合特定準則時, 它會以較大的字型繪製並變成紅色。</span><span class="sxs-lookup"><span data-stu-id="084ce-104">When an item meets a certain criteria, it is drawn in a larger font and turned red.</span></span>  
  
## <a name="example"></a><span data-ttu-id="084ce-105">範例</span><span class="sxs-lookup"><span data-stu-id="084ce-105">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="084ce-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="084ce-106">Compiling the Code</span></span>  
 <span data-ttu-id="084ce-107">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="084ce-107">This example requires:</span></span>  
  
- <span data-ttu-id="084ce-108">Windows form。</span><span class="sxs-lookup"><span data-stu-id="084ce-108">A Windows form.</span></span>  
  
- <span data-ttu-id="084ce-109">名<xref:System.Windows.Forms.ComboBox>為`ListBox1`的控制項<xref:System.Windows.Forms.ComboBox.Items%2A> , 其屬性中有三個專案。</span><span class="sxs-lookup"><span data-stu-id="084ce-109">A <xref:System.Windows.Forms.ComboBox> control named `ListBox1` with three items in the <xref:System.Windows.Forms.ComboBox.Items%2A> property.</span></span> <span data-ttu-id="084ce-110">在此範例中, 這三個專案`"One", Two", and Three"`的名稱為。</span><span class="sxs-lookup"><span data-stu-id="084ce-110">In this example, the three items are named `"One", Two", and Three"`.</span></span> <span data-ttu-id="084ce-111">的<xref:System.Windows.Forms.ComboBox.DrawMode%2A> <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable>屬性必須設定為。`ComboBox1`</span><span class="sxs-lookup"><span data-stu-id="084ce-111">The <xref:System.Windows.Forms.ComboBox.DrawMode%2A> property of `ComboBox1` must be set to <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable>.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="084ce-112">這項技術也適用于<xref:System.Windows.Forms.ListBox>控制項, 您可以將<xref:System.Windows.Forms.ListBox>取代為<xref:System.Windows.Forms.ComboBox>。</span><span class="sxs-lookup"><span data-stu-id="084ce-112">This technique is also applicable to the <xref:System.Windows.Forms.ListBox> control — you can substitute a <xref:System.Windows.Forms.ListBox> for the <xref:System.Windows.Forms.ComboBox>.</span></span>  
  
- <span data-ttu-id="084ce-113"><xref:System.Windows.Forms?displayProperty=nameWithType> 和 <xref:System.Drawing?displayProperty=nameWithType> 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="084ce-113">References to the <xref:System.Windows.Forms?displayProperty=nameWithType> and <xref:System.Drawing?displayProperty=nameWithType> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="084ce-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="084ce-114">See also</span></span>

- <xref:System.Windows.Forms.ComboBox.DrawItem>
- <xref:System.Windows.Forms.DrawItemEventArgs>
- <xref:System.Windows.Forms.ComboBox.MeasureItem>
- [<span data-ttu-id="084ce-115">使用內建主控描繪支援的控制項</span><span class="sxs-lookup"><span data-stu-id="084ce-115">Controls with Built-In Owner-Drawing Support</span></span>](controls-with-built-in-owner-drawing-support.md)
- [<span data-ttu-id="084ce-116">ListBox 控制項</span><span class="sxs-lookup"><span data-stu-id="084ce-116">ListBox Control</span></span>](listbox-control-windows-forms.md)
- [<span data-ttu-id="084ce-117">ComboBox 控制項</span><span class="sxs-lookup"><span data-stu-id="084ce-117">ComboBox Control</span></span>](combobox-control-windows-forms.md)
