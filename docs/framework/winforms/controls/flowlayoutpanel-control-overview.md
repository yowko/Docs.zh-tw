---
title: FlowLayoutPanel 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- FlowLayoutPanel
helpviewer_keywords:
- forms [Windows Forms], dynamic layout
- layout [Windows Forms], dynamic
- Windows Forms, dynamic layout
- FlowLayoutPanel control [Windows Forms], about FlowLayoutPanel control
ms.assetid: 3883e024-f5a0-456d-9c27-b4dfa1cc9045
ms.openlocfilehash: 73767114da1c04222fb8ceaf812153421c4597aa
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45517758"
---
# <a name="flowlayoutpanel-control-overview"></a>FlowLayoutPanel 控制項概觀
<xref:System.Windows.Forms.FlowLayoutPanel> 控制項會以水平或垂直的流動方向來排列其內容。 您可以將控制項的內容從一個資料列包裝至下一個資料列，或從一個資料行包裝至下一個資料行。 或者，您可以用裁剪的方式，而不是包裝其內容。  
  
 您可以設定 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> 屬性的值來指定文字方向。 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項會在「由右至左 (RTL)」配置中，將其文字方向正確地反轉。 您也可以設定 <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> 屬性的值，指定要包裝或裁剪 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的內容。  
  
 當您將 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性設為 `true` 時，<xref:System.Windows.Forms.FlowLayoutPanel> 控制項會根據其內容自動調整大小。 它也會提供**FlowBreak**屬性給它的子控制項。 將 FlowBreak 屬性的值設為 `true` ，會導致 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項停止以目前的文字方向來配置控制項，並包裝至下一個資料列或資料行。  
  
 任何 Windows Form 控制項都可以是 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的子系，包括 <xref:System.Windows.Forms.FlowLayoutPanel> 的其他執行個體。 使用這項功能，您可以建構複雜的配置，以在執行階段調整為表單的維度。  
  
 另請參閱[逐步解說： 在 Windows Form 使用 FlowLayoutPanel 排列的控制項](https://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\))。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [FlowLayoutPanel 控制項](../../../../docs/framework/winforms/controls/flowlayoutpanel-control-windows-forms.md)
