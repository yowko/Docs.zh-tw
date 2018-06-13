---
title: 如何：使用控制項呈現類別
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- professional appearance [Windows Forms], rendering Windows Forms controls
- visual themes [Windows Forms], applying to Windows Forms controls
- visual styles [Windows Forms], rendering Windows Forms controls
ms.assetid: c0125e34-cd74-4c35-818c-3e40f462b0a3
ms.openlocfilehash: e5b82c3317d2d162fbd5a182166a9e0061fd770e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534101"
---
# <a name="how-to-use-a-control-rendering-class"></a><span data-ttu-id="17e77-102">如何：使用控制項呈現類別</span><span class="sxs-lookup"><span data-stu-id="17e77-102">How to: Use a Control Rendering Class</span></span>
<span data-ttu-id="17e77-103">這個範例示範如何使用<xref:System.Windows.Forms.ComboBoxRenderer>來呈現的下拉式箭號，下拉式方塊控制項的類別。</span><span class="sxs-lookup"><span data-stu-id="17e77-103">This example demonstrates how to use the <xref:System.Windows.Forms.ComboBoxRenderer> class to render the drop-down arrow of a combo box control.</span></span> <span data-ttu-id="17e77-104">此範例包含<xref:System.Windows.Forms.Control.OnPaint%2A>簡單的自訂控制項的方法。</span><span class="sxs-lookup"><span data-stu-id="17e77-104">The example consists of the <xref:System.Windows.Forms.Control.OnPaint%2A> method of a simple custom control.</span></span> <span data-ttu-id="17e77-105"><xref:System.Windows.Forms.ComboBoxRenderer.IsSupported%2A?displayProperty=nameWithType>屬性用來判斷是否已啟用視覺化樣式應用程式視窗的工作區中。</span><span class="sxs-lookup"><span data-stu-id="17e77-105">The <xref:System.Windows.Forms.ComboBoxRenderer.IsSupported%2A?displayProperty=nameWithType> property is used to determine whether visual styles are enabled in the client area of application windows.</span></span> <span data-ttu-id="17e77-106">如果視覺化樣式作用中，則<xref:System.Windows.Forms.ComboBoxRenderer.DrawDropDownButton%2A?displayProperty=nameWithType>方法會呈現下拉式箭頭，以視覺化樣式; 否則<xref:System.Windows.Forms.ControlPaint.DrawComboButton%2A?displayProperty=nameWithType>方法會呈現在傳統的視窗樣式的下拉式箭號。</span><span class="sxs-lookup"><span data-stu-id="17e77-106">If visual styles are active, then the <xref:System.Windows.Forms.ComboBoxRenderer.DrawDropDownButton%2A?displayProperty=nameWithType> method will render the drop-down arrow with visual styles; otherwise, the <xref:System.Windows.Forms.ControlPaint.DrawComboButton%2A?displayProperty=nameWithType> method will render the drop-down arrow in the classic Windows style.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17e77-107">範例</span><span class="sxs-lookup"><span data-stu-id="17e77-107">Example</span></span>  
 [!code-cpp[System.Windows.Forms_ControlRenderer#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/cpp/form1.cpp#10)]
 [!code-csharp[System.Windows.Forms_ControlRenderer#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms_ControlRenderer#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="17e77-108">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="17e77-108">Compiling the Code</span></span>  
 <span data-ttu-id="17e77-109">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="17e77-109">This example requires:</span></span>  
  
-   <span data-ttu-id="17e77-110">自訂控制項衍生自<xref:System.Windows.Forms.Control>類別。</span><span class="sxs-lookup"><span data-stu-id="17e77-110">A custom control derived from the <xref:System.Windows.Forms.Control> class.</span></span>  
  
-   <span data-ttu-id="17e77-111">A<xref:System.Windows.Forms.Form>裝載自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="17e77-111">A <xref:System.Windows.Forms.Form> that hosts the custom control.</span></span>  
  
-   <span data-ttu-id="17e77-112">若要參考<xref:System?displayProperty=nameWithType>， <xref:System.Drawing?displayProperty=nameWithType>， <xref:System.Windows.Forms?displayProperty=nameWithType>，和<xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType>命名空間。</span><span class="sxs-lookup"><span data-stu-id="17e77-112">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17e77-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17e77-113">See Also</span></span>  
 [<span data-ttu-id="17e77-114">使用視覺化樣式呈現控制項</span><span class="sxs-lookup"><span data-stu-id="17e77-114">Rendering Controls with Visual Styles</span></span>](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)
