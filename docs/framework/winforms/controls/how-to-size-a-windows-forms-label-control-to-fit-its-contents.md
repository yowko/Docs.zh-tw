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
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a>如何：調整 Windows Form Label 控制項大小以適合其內容
Windows Form<xref:System.Windows.Forms.Label>控制項可以是單行或多行，而且它可以是固定的大小，或可以自動調整大小，以容納其標題。 <xref:System.Windows.Forms.Label.AutoSize%2A>屬性可協助您調整控制項的大小以配合較大或較小的標題，即標題將會在執行階段變更的特別有用。  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a>若要進行動態調整大小以符合其內容的標籤控制項  
  
1.  設定其<xref:System.Windows.Forms.Label.AutoSize%2A>屬性`true`。  
  
 如果<xref:System.Windows.Forms.Label.AutoSize%2A>設`false`中, 指定文字<xref:System.Windows.Forms.Label.Text%2A>屬性會自動換行至下一行可能的話，但是控制項不會成長。  
  
## <a name="see-also"></a>另請參閱  
 [操作說明：使用 Windows Forms Label 控制項建立便捷鍵](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md)  
 [Label 控制項概觀](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)  
 [Label 控制項](../../../../docs/framework/winforms/controls/label-control-windows-forms.md)
