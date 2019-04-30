---
title: HOW TO：調整 Windows Forms Label 控制項的大小使符合其內容
ms.date: 03/30/2017
helpviewer_keywords:
- captions [Windows Forms], sizing
- sizing controls
- size [Windows Forms], controls
- labels [Windows Forms], sizing to fit contents
- Label control [Windows Forms], sizing to fit contents
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
ms.openlocfilehash: 110aab0c0826bb4b06e22158afd6af37b5406be4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971193"
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a><span data-ttu-id="b2702-102">HOW TO：調整 Windows Forms Label 控制項的大小使符合其內容</span><span class="sxs-lookup"><span data-stu-id="b2702-102">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>
<span data-ttu-id="b2702-103">Windows Form<xref:System.Windows.Forms.Label>控制項可以是單行或多行，以及它可以是固定的大小，或可以自動調整大小，以容納其標題。</span><span class="sxs-lookup"><span data-stu-id="b2702-103">The Windows Forms <xref:System.Windows.Forms.Label> control can be single-line or multi-line, and it can be either fixed in size or can automatically resize itself to accommodate its caption.</span></span> <span data-ttu-id="b2702-104"><xref:System.Windows.Forms.Label.AutoSize%2A>屬性可協助您調整控制項的大小來容納較大或較小的原文字幕，這是特別有用，如果標題將會在執行階段變更。</span><span class="sxs-lookup"><span data-stu-id="b2702-104">The <xref:System.Windows.Forms.Label.AutoSize%2A> property helps you size the controls to fit larger or smaller captions, which is particularly useful if the caption will change at run time.</span></span>  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a><span data-ttu-id="b2702-105">若要進行動態調整大小以容納其內容為 label 控制項</span><span class="sxs-lookup"><span data-stu-id="b2702-105">To make a label control resize dynamically to fit its contents</span></span>  
  
1. <span data-ttu-id="b2702-106">設定其<xref:System.Windows.Forms.Label.AutoSize%2A>屬性設`true`。</span><span class="sxs-lookup"><span data-stu-id="b2702-106">Set its <xref:System.Windows.Forms.Label.AutoSize%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="b2702-107">如果<xref:System.Windows.Forms.Label.AutoSize%2A>設定為`false`，以指定字組<xref:System.Windows.Forms.Label.Text%2A>屬性會自動換行至下一行可能的話，但是控制項不會成長。</span><span class="sxs-lookup"><span data-stu-id="b2702-107">If <xref:System.Windows.Forms.Label.AutoSize%2A> is set to `false`, the words specified in the <xref:System.Windows.Forms.Label.Text%2A> property will wrap to the next line if possible, but the control will not grow.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2702-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2702-108">See also</span></span>

- [<span data-ttu-id="b2702-109">如何：使用 Windows Forms Label 控制項建立便捷鍵</span><span class="sxs-lookup"><span data-stu-id="b2702-109">How to: Create Access Keys with Windows Forms Label Controls</span></span>](how-to-create-access-keys-with-windows-forms-label-controls.md)
- [<span data-ttu-id="b2702-110">Label 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="b2702-110">Label Control Overview</span></span>](label-control-overview-windows-forms.md)
- [<span data-ttu-id="b2702-111">Label 控制項</span><span class="sxs-lookup"><span data-stu-id="b2702-111">Label Control</span></span>](label-control-windows-forms.md)
