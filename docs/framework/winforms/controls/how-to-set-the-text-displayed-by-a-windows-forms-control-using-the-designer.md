---
title: HOW TO：使用設計工具設定 Windows Forms 控制項所顯示的文字
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], setting caption
- Windows Forms, setting the text displayed
ms.assetid: 9d18e0e0-f17f-4074-837d-e67ceeeaa89d
ms.openlocfilehash: 37ab3823a41cca2eeea550c90e92e90bc364c759
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2019
ms.locfileid: "65960345"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer"></a>HOW TO：使用設計工具設定 Windows Forms 控制項所顯示的文字

Windows Form 控制項通常會顯示一些文字相關控制項的主要功能。 比方說，<xref:System.Windows.Forms.Button>控制項通常會顯示標題，指出當按一下按鈕時，就會執行哪些動作。 針對所有控制項，您都可以使用 <xref:System.Windows.Forms.Control.Text%2A> 屬性來設定或傳回該文字。 您可以使用 <xref:System.Windows.Forms.Control.Font%2A> 屬性來變更字型。

### <a name="to-set-the-text-and-font-with-the-designer"></a>若要設定的文字和字型與設計工具

1. 在 [屬性] 視窗中，設定<xref:System.Windows.Forms.Control.Text%2A>設為適當的字串控制項屬性。

     若要建立加上底線的快速鍵，包括連字號 (&) 會成為快顯索引鍵的字母前面。

2. 在 [屬性] 視窗中，按一下 省略符號按鈕 (![的 Visual Studio 的 [屬性] 視窗中的省略符號按鈕 （...）](./media/visual-studio-ellipsis-button.png)) 旁邊<xref:System.Windows.Forms.Control.Font%2A>屬性。

     在標準的字型 對話方塊中，選取您想要的字型、 字型樣式、 大小、 作用 （例如刪除線或底線） 和指令碼。

## <a name="see-also"></a>另請參閱

- [如何：設定所顯示之文字的 Windows Form 控制項](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [使用字型和文字](../advanced/using-fonts-and-text.md)
- [標記個別 Windows Forms 控制項並提供其捷徑](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
