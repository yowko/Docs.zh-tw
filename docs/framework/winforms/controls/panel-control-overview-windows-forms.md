---
title: Panel 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- Panel
helpviewer_keywords:
- grouping controls [Windows Forms], Panel control
- Panel control [Windows Forms], about Panel control
ms.assetid: b6b83636-2c39-4dad-89d6-f0fa41049a74
ms.openlocfilehash: 2b70996f7944f3f5ef8ef8bc80015836956a9b00
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715499"
---
# <a name="panel-control-overview-windows-forms"></a>Panel 控制項概觀 (Windows Form)
Windows Form<xref:System.Windows.Forms.Panel>控制項可用來提供其他控制項的可識別分組。 一般而言，您可以使用面板細分函式的表單。 例如，您可能會指定郵寄的選項，例如要使用哪一個隔夜承運商的訂單表單。 將面板中的所有選項，可讓使用者邏輯的視覺提示。 在設計階段控制項可以輕易地移動所有 — 當您移動<xref:System.Windows.Forms.Panel>控制所有其包含的控制項移動，太。 可以透過存取面板中分組的控制項及其<xref:System.Windows.Forms.Control.Controls%2A>屬性。 這個屬性傳回的集合<xref:System.Windows.Forms.Control>執行個體，因此您通常需要轉型控制項擷取這種方式，為其特定的型別。  
  
## <a name="panel-versus-groupbox"></a>GroupBox 與面板  
 <xref:System.Windows.Forms.Panel>控制項是類似於<xref:System.Windows.Forms.GroupBox>控制; 不過，只有<xref:System.Windows.Forms.Panel>控制項有捲軸，並只<xref:System.Windows.Forms.GroupBox>控制項顯示標題。  
  
## <a name="key-properties"></a>索引鍵內容  
 若要顯示捲軸，請設定<xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A>屬性設`true`。 您也可以藉由設定自訂面板的外觀<xref:System.Windows.Forms.Control.BackColor%2A>， <xref:System.Windows.Forms.Control.BackgroundImage%2A>，和<xref:System.Windows.Forms.Panel.BorderStyle%2A>屬性。 如需詳細資訊<xref:System.Windows.Forms.Control.BackColor%2A>並<xref:System.Windows.Forms.Control.BackgroundImage%2A>屬性，請參閱[How to:設定面板背景](how-to-set-the-background-of-a-windows-forms-panel.md)。 <xref:System.Windows.Forms.Panel.BorderStyle%2A>屬性會決定是否外框的不可見的框線的面板 (<xref:System.Windows.Forms.BorderStyle.None>)，純文字的行 (<xref:System.Windows.Forms.BorderStyle.FixedSingle>)，或遮蔽的列 (<xref:System.Windows.Forms.BorderStyle.Fixed3D>)。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.Panel>
- [GroupBox 控制項](groupbox-control-windows-forms.md)
- [如何：搭配 Windows Form Panel 控制項使用設計工具群組控制項](group-controls-with-wf-panel-control-using-the-designer.md)
- [如何：設定使用設計工具的 Windows Form 面板的背景](how-to-set-the-background-of-a-windows-forms-panel-using-the-designer.md)
