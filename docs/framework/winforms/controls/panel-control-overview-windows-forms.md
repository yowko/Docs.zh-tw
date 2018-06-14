---
title: Panel 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- Panel
helpviewer_keywords:
- grouping controls [Windows Forms], Panel control
- Panel control [Windows Forms], about Panel control
ms.assetid: b6b83636-2c39-4dad-89d6-f0fa41049a74
ms.openlocfilehash: 1ba766629f923b091459531ce74d28dca4b4ea0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539338"
---
# <a name="panel-control-overview-windows-forms"></a>Panel 控制項概觀 (Windows Form)
Windows Form<xref:System.Windows.Forms.Panel>控制項可用來提供其他控制項可識別的群組。 一般而言，您可以使用面板細分函式表單。 比方說，您可能會指定郵寄選項，例如要使用哪個夜間貨運訂購表單。 將在面板中的所有選項，可讓使用者邏輯的視覺提示。 在設計階段控制項可以輕易地移動所有 — 當您移動<xref:System.Windows.Forms.Panel>控制所有其包含的控制項，跟著移動。 可以透過存取面板中分組的控制項及其<xref:System.Windows.Forms.Control.Controls%2A>屬性。 這個屬性傳回的集合<xref:System.Windows.Forms.Control>執行個體，因此您通常需要轉型控制項擷取這種方式為其特定的型別。  
  
## <a name="panel-versus-groupbox"></a>GroupBox 與面板  
 <xref:System.Windows.Forms.Panel>控制項是類似於<xref:System.Windows.Forms.GroupBox>控制項等控制項，不過，只有<xref:System.Windows.Forms.Panel>控制項有捲軸僅限和<xref:System.Windows.Forms.GroupBox>控制項顯示的標題。  
  
## <a name="key-properties"></a>索引鍵屬性  
 若要顯示捲軸，設定<xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A>屬性`true`。 您也可以藉由設定自訂面板的外觀<xref:System.Windows.Forms.Control.BackColor%2A>， <xref:System.Windows.Forms.Control.BackgroundImage%2A>，和<xref:System.Windows.Forms.Panel.BorderStyle%2A>屬性。 如需有關<xref:System.Windows.Forms.Control.BackColor%2A>和<xref:System.Windows.Forms.Control.BackgroundImage%2A>屬性，請參閱[How to： 設定面板的背景](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md)。 <xref:System.Windows.Forms.Panel.BorderStyle%2A>屬性會決定是否看不到框線與概述面板 (<xref:System.Windows.Forms.BorderStyle.None>)，純文字的一行 (<xref:System.Windows.Forms.BorderStyle.FixedSingle>)，或加上陰影的列 (<xref:System.Windows.Forms.BorderStyle.Fixed3D>)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.Panel>  
 [GroupBox 控制項](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)  
 [操作說明：搭配 Windows Forms Panel 控制項使用設計工具群組控制項](../../../../docs/framework/winforms/controls/group-controls-with-wf-panel-control-using-the-designer.md)  
 [操作說明：使用設計工具設定 Windows Forms 面板的背景](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel-using-the-designer.md)
