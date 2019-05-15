---
title: HOW TO：自訂 Windows Forms DataGridView 控制項的資料列外觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- rows [Windows Forms], customizing in DataGridView control
- DataGridView control [Windows Forms], customizing rows
ms.assetid: d40b53d2-7e7c-48c5-8570-6e79d15c3bbb
ms.openlocfilehash: f7dcb3d949182efee3538174909b0f856dceedee
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65589481"
---
# <a name="how-to-customize-the-appearance-of-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="9a5ce-102">HOW TO：自訂 Windows Forms DataGridView 控制項的資料列外觀</span><span class="sxs-lookup"><span data-stu-id="9a5ce-102">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="9a5ce-103">您可以藉由處理一個或兩個 <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> 和 <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> 事件，來控制 <xref:System.Windows.Forms.DataGridView> 資料列的外觀 。</span><span class="sxs-lookup"><span data-stu-id="9a5ce-103">You can control the appearance of <xref:System.Windows.Forms.DataGridView> rows by handling one or both of the <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> and <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> events.</span></span> <span data-ttu-id="9a5ce-104">這些事件經過設計，以便您可以在 <xref:System.Windows.Forms.DataGridView> 控制項繪製其餘部分的時候只繪製您想要的部分。</span><span class="sxs-lookup"><span data-stu-id="9a5ce-104">These events are designed so that you can paint only what you want to while letting the <xref:System.Windows.Forms.DataGridView> control paint the rest.</span></span> <span data-ttu-id="9a5ce-105">例如，如果您想要繪製自訂背景，您可以處理 <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> 事件，然後讓個別儲存格繪製自己的前景內容。</span><span class="sxs-lookup"><span data-stu-id="9a5ce-105">For example, if you want to paint a custom background, you can handle the <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> event and let the individual cells paint their own foreground content.</span></span> <span data-ttu-id="9a5ce-106">或者，您可以讓儲存格繪製自己，並加入自訂前景內容到 <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> 事件的處理常式。</span><span class="sxs-lookup"><span data-stu-id="9a5ce-106">Alternately, you can let the cells paint themselves and add custom foreground content in a handler for the <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="9a5ce-107">您也可以停用儲存格繪製，自行在 <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> 事件處理常式中繪製全部內容。</span><span class="sxs-lookup"><span data-stu-id="9a5ce-107">You can also disable cell painting and paint everything yourself in a <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> event handler.</span></span>  
  
 <span data-ttu-id="9a5ce-108">下列程式碼範例會實作兩個事件的處理常式，以提供漸層選取背景和某些跨越多個資料行的自訂前景內容。</span><span class="sxs-lookup"><span data-stu-id="9a5ce-108">The following code example implements handlers for both events in order to provide a gradient selection background and some custom foreground content that spans multiple columns.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a5ce-109">範例</span><span class="sxs-lookup"><span data-stu-id="9a5ce-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewRowPainting#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/CS/datagridviewrowpainting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewRowPainting#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/VB/datagridviewrowpainting.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9a5ce-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="9a5ce-110">Compiling the Code</span></span>  
 <span data-ttu-id="9a5ce-111">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="9a5ce-111">This example requires:</span></span>  
  
- <span data-ttu-id="9a5ce-112">System、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="9a5ce-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a5ce-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a5ce-113">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>
- [<span data-ttu-id="9a5ce-114">自訂 Windows Forms DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="9a5ce-114">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="9a5ce-115">DataGridView 控制項架構</span><span class="sxs-lookup"><span data-stu-id="9a5ce-115">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)
