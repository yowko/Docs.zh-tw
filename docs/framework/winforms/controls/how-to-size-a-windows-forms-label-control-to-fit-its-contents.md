---
title: 調整標籤控制項的大小以符合其內容
ms.date: 03/30/2017
helpviewer_keywords:
- captions [Windows Forms], sizing
- sizing controls
- size [Windows Forms], controls
- labels [Windows Forms], sizing to fit contents
- Label control [Windows Forms], sizing to fit contents
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
ms.openlocfilehash: 6a563693feaa5074f5d13f0b82cc4d0305a79c23
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743781"
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a><span data-ttu-id="f67b0-102">如何：調整 Windows Form Label 控制項大小以適合其內容</span><span class="sxs-lookup"><span data-stu-id="f67b0-102">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>
<span data-ttu-id="f67b0-103">Windows Forms <xref:System.Windows.Forms.Label> 控制項可以是單行或多行，也可以是固定大小，也可以自動調整本身以配合其標題。</span><span class="sxs-lookup"><span data-stu-id="f67b0-103">The Windows Forms <xref:System.Windows.Forms.Label> control can be single-line or multi-line, and it can be either fixed in size or can automatically resize itself to accommodate its caption.</span></span> <span data-ttu-id="f67b0-104"><xref:System.Windows.Forms.Label.AutoSize%2A> 屬性可協助您調整控制項的大小，以容納較大或較小的標題，如果標題會在執行時間變更，這特別有用。</span><span class="sxs-lookup"><span data-stu-id="f67b0-104">The <xref:System.Windows.Forms.Label.AutoSize%2A> property helps you size the controls to fit larger or smaller captions, which is particularly useful if the caption will change at run time.</span></span>  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a><span data-ttu-id="f67b0-105">使標籤控制項動態調整大小以符合其內容</span><span class="sxs-lookup"><span data-stu-id="f67b0-105">To make a label control resize dynamically to fit its contents</span></span>  
  
1. <span data-ttu-id="f67b0-106">將其 [<xref:System.Windows.Forms.Label.AutoSize%2A>] 屬性設定為 [`true`]。</span><span class="sxs-lookup"><span data-stu-id="f67b0-106">Set its <xref:System.Windows.Forms.Label.AutoSize%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="f67b0-107">如果 <xref:System.Windows.Forms.Label.AutoSize%2A> 設定為 `false`，則在 <xref:System.Windows.Forms.Label.Text%2A> 屬性中指定的單字會盡可能換行到下一行，但控制項不會成長。</span><span class="sxs-lookup"><span data-stu-id="f67b0-107">If <xref:System.Windows.Forms.Label.AutoSize%2A> is set to `false`, the words specified in the <xref:System.Windows.Forms.Label.Text%2A> property will wrap to the next line if possible, but the control will not grow.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f67b0-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="f67b0-108">See also</span></span>

- [<span data-ttu-id="f67b0-109">操作說明：使用 Windows Forms Label 控制項建立便捷鍵</span><span class="sxs-lookup"><span data-stu-id="f67b0-109">How to: Create Access Keys with Windows Forms Label Controls</span></span>](how-to-create-access-keys-with-windows-forms-label-controls.md)
- [<span data-ttu-id="f67b0-110">Label 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="f67b0-110">Label Control Overview</span></span>](label-control-overview-windows-forms.md)
- [<span data-ttu-id="f67b0-111">Label 控制項</span><span class="sxs-lookup"><span data-stu-id="f67b0-111">Label Control</span></span>](label-control-windows-forms.md)
