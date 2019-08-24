---
title: HOW TO：調整 Windows Forms 的控制項大小
ms.date: 03/30/2017
f1_keywords:
- Size.Height
- Size.Width
helpviewer_keywords:
- controls [Windows Forms], resizing
- size [Windows Forms], controls
- Windows Forms controls, size
ms.assetid: d2dba441-a8c0-4705-b8e8-2e5d86d6e7ec
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7e659bf02ea079afc10561e1d83f7ab7cef29a2e
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987055"
---
# <a name="how-to-resize-controls-on-windows-forms"></a>作法：調整 Windows Forms 上控制項的大小

您可以調整個別控制項的大小, 也可以調整相同或不同種類 (例如<xref:System.Windows.Forms.Button>和<xref:System.Windows.Forms.GroupBox>控制項) 的多個控制項大小。

## <a name="to-resize-a-control"></a>調整控制項的大小

在 Visual Studio 中, 選取要調整大小的控制項, 然後拖曳其中一個八個大小控點。

> [!NOTE]
> 選取控制項, 然後在按住**Shift**鍵時按**箭頭**鍵, 一次調整控制項的一個圖元。 按**向下**鍵或**向右鍵**, 同時按住**Shift**和**Ctrl**鍵, 以大幅增加控制項的大小。

## <a name="to-resize-multiple-controls-on-a-form"></a>調整表單上的多個控制項大小

1. 在 Visual Studio 中, 按住**Ctrl**或**Shift**鍵, 然後選取您想要調整大小的控制項。 您選取的第一個控制項的大小會用於其他控制項。

2. 在 [**格式**] 功能表上, 選擇 [**設成相同大小**], 然後選取四個選項的其中一個。 前三個命令會變更控制項的維度, 以符合第一個選取的控制項。

## <a name="see-also"></a>另請參閱

- [Windows Forms 控制項](index.md)
- [標記個別 Windows Forms 控制項並提供其捷徑](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [在 Windows Forms 上使用的控制項](controls-to-use-on-windows-forms.md)
- [依功能區分 Windows Forms 控制項](windows-forms-controls-by-function.md)
- [如何：使用設計工具調整 Windows Forms 大小](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100))
