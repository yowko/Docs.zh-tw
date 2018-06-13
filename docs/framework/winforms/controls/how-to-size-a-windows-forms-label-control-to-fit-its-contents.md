---
title: 如何：調整 Windows Form Label 控制項大小以適合其內容
ms.date: 03/30/2017
helpviewer_keywords:
- captions [Windows Forms], sizing
- sizing controls
- size [Windows Forms], controls
- labels [Windows Forms], sizing to fit contents
- Label control [Windows Forms], sizing to fit contents
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
ms.openlocfilehash: e067966b606d77ceb9d11d2784c0d5f73ad332a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533724"
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a><span data-ttu-id="562a2-102">如何：調整 Windows Form Label 控制項大小以適合其內容</span><span class="sxs-lookup"><span data-stu-id="562a2-102">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>
<span data-ttu-id="562a2-103">Windows Form<xref:System.Windows.Forms.Label>控制項可以是單行或多行，而且它可以是固定的大小，或可以自動調整大小，以容納其標題。</span><span class="sxs-lookup"><span data-stu-id="562a2-103">The Windows Forms <xref:System.Windows.Forms.Label> control can be single-line or multi-line, and it can be either fixed in size or can automatically resize itself to accommodate its caption.</span></span> <span data-ttu-id="562a2-104"><xref:System.Windows.Forms.Label.AutoSize%2A>屬性可協助您調整控制項的大小以配合較大或較小的標題，即標題將會在執行階段變更的特別有用。</span><span class="sxs-lookup"><span data-stu-id="562a2-104">The <xref:System.Windows.Forms.Label.AutoSize%2A> property helps you size the controls to fit larger or smaller captions, which is particularly useful if the caption will change at run time.</span></span>  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a><span data-ttu-id="562a2-105">若要進行動態調整大小以符合其內容的標籤控制項</span><span class="sxs-lookup"><span data-stu-id="562a2-105">To make a label control resize dynamically to fit its contents</span></span>  
  
1.  <span data-ttu-id="562a2-106">設定其<xref:System.Windows.Forms.Label.AutoSize%2A>屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="562a2-106">Set its <xref:System.Windows.Forms.Label.AutoSize%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="562a2-107">如果<xref:System.Windows.Forms.Label.AutoSize%2A>設`false`中, 指定文字<xref:System.Windows.Forms.Label.Text%2A>屬性會自動換行至下一行可能的話，但是控制項不會成長。</span><span class="sxs-lookup"><span data-stu-id="562a2-107">If <xref:System.Windows.Forms.Label.AutoSize%2A> is set to `false`, the words specified in the <xref:System.Windows.Forms.Label.Text%2A> property will wrap to the next line if possible, but the control will not grow.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="562a2-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="562a2-108">See Also</span></span>  
 [<span data-ttu-id="562a2-109">操作說明：使用 Windows Forms Label 控制項建立便捷鍵</span><span class="sxs-lookup"><span data-stu-id="562a2-109">How to: Create Access Keys with Windows Forms Label Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md)  
 [<span data-ttu-id="562a2-110">Label 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="562a2-110">Label Control Overview</span></span>](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)  
 [<span data-ttu-id="562a2-111">Label 控制項</span><span class="sxs-lookup"><span data-stu-id="562a2-111">Label Control</span></span>](../../../../docs/framework/winforms/controls/label-control-windows-forms.md)
