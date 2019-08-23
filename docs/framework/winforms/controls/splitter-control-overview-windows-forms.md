---
title: Splitter 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- Splitter
helpviewer_keywords:
- Splitter control [Windows Forms], about Splitter control
ms.assetid: e2b6ab83-dfdd-40ec-9762-850702c82dcb
ms.openlocfilehash: 934efd707f2a52da5ba604139c8e4510aad4606b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964463"
---
# <a name="splitter-control-overview-windows-forms"></a>Splitter 控制項概觀 (Windows Form)
> [!IMPORTANT]
> 雖然<xref:System.Windows.Forms.SplitContainer>會取代並加入舊版的<xref:System.Windows.Forms.Splitter>控制項功能, 但如果<xref:System.Windows.Forms.Splitter>您選擇, 則會保留以提供回溯相容性及未來使用。  
  
 Windows Forms <xref:System.Windows.Forms.Splitter>控制項是用來在執行時間調整停駐的控制項大小。 <xref:System.Windows.Forms.Splitter>控制項通常用於具有不同資料長度的控制項 (例如 Windows Explorer), 其資料窗格包含不同時間的差異寬度資訊。  
  
## <a name="working-with-the-splitter-control"></a>使用分隔器控制項  
 當使用者將滑鼠指標指向控制項的停駐邊緣, 可由分隔器控制項調整大小時, 指標會變更其外觀, 以指出控制項可以調整大小。 使用分隔器控制項, 使用者可以調整緊接在其前面的停駐控制項大小。 因此, 若要讓使用者在執行時間調整停駐控制項的大小, 請將控制項的大小設為容器的邊緣, 然後將分隔器控制項停駐在該容器的同一側邊。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.SplitContainer>
- [如何：將控制項停駐在 Windows Forms](how-to-dock-controls-on-windows-forms.md)
- [在 Windows Forms 上使用的控制項](controls-to-use-on-windows-forms.md)
