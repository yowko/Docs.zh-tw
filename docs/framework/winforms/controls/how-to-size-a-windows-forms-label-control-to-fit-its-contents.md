---
title: HOW TO：調整大小以容納其內容的 Windows Form Label 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- captions [Windows Forms], sizing
- sizing controls
- size [Windows Forms], controls
- labels [Windows Forms], sizing to fit contents
- Label control [Windows Forms], sizing to fit contents
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
ms.openlocfilehash: 5771b232d77e3e5a792b179ebffd3fa0edda7c9b
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57702190"
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a>HOW TO：調整大小以容納其內容的 Windows Form Label 控制項
Windows Form<xref:System.Windows.Forms.Label>控制項可以是單行或多行，以及它可以是固定的大小，或可以自動調整大小，以容納其標題。 <xref:System.Windows.Forms.Label.AutoSize%2A>屬性可協助您調整控制項的大小來容納較大或較小的原文字幕，這是特別有用，如果標題將會在執行階段變更。  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a>若要進行動態調整大小以容納其內容為 label 控制項  
  
1.  設定其<xref:System.Windows.Forms.Label.AutoSize%2A>屬性設`true`。  
  
 如果<xref:System.Windows.Forms.Label.AutoSize%2A>設定為`false`，以指定字組<xref:System.Windows.Forms.Label.Text%2A>屬性會自動換行至下一行可能的話，但是控制項不會成長。  
  
## <a name="see-also"></a>另請參閱
- [如何：使用 Windows Forms Label 控制項建立便捷鍵](how-to-create-access-keys-with-windows-forms-label-controls.md)
- [Label 控制項概觀](label-control-overview-windows-forms.md)
- [Label 控制項](label-control-windows-forms.md)
