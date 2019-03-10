---
title: NumericUpDown 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- NumericUpDown
helpviewer_keywords:
- numeric spin button control [Windows Forms], Windows Forms
- NumericUpDown control [Windows Forms], about NumericUpDown control
- spin button control [Windows Forms], Windows Forms
ms.assetid: cff3cf30-4d46-4381-87df-37bfe83c71c5
ms.openlocfilehash: 7d762330a3287892409b308b077ab4879ad88dcd
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704592"
---
# <a name="numericupdown-control-overview-windows-forms"></a>NumericUpDown 控制項概觀 (Windows Form)
<xref:System.Windows.Forms.NumericUpDown>控制項看起來像在文字方塊中的組合和一對箭號，讓使用者可以按一下來調整值。 控制項顯示，並從固定的數字值選項清單中設定單一數值。 使用者可以增加和減少數目，依序按一下向上和向下箭頭，按下向上鍵和向下鍵，或輸入控制項的文字部份的數字。 按一下向上鍵移動的號碼，朝最大值;按一下向下鍵移動的號碼，朝最小值。  
  
 其用途廣泛的功能，因為這個控制項是最佳的選擇，比方說，如果您想要建立音樂的播放器應用程式的音量控制項。 <xref:System.Windows.Forms.NumericUpDown>控制使用於許多 Windows 控制台應用程式。  
  
## <a name="key-properties-and-methods"></a>索引鍵屬性和方法  
 控制項的文字方塊中顯示的數字可以是各種不同的格式，包括十六進位。 如需詳細資訊，請參閱[如何：為 Windows Forms NumericUpDown 控制項設定格式](how-to-set-the-format-for-the-windows-forms-numericupdown-control.md)。 控制項的索引鍵屬性是<xref:System.Windows.Forms.NumericUpDown.Value%2A>， <xref:System.Windows.Forms.NumericUpDown.Maximum%2A> （預設值 100）， <xref:System.Windows.Forms.NumericUpDown.Minimum%2A> （預設值為 0） 和<xref:System.Windows.Forms.NumericUpDown.Increment%2A>（預設值 1）。 <xref:System.Windows.Forms.NumericUpDown.Value%2A>屬性會設定控制項中選取的目前數目。 <xref:System.Windows.Forms.NumericUpDown.Increment%2A>屬性會設定當使用者按一下向上或向下鍵調整的數字的數量。 當焦點移離控制項時，請將驗證任何具類型的輸入，針對最小和最大的數字值。 您可以增加控制項通過數字，當使用者持續按下向上或向下箭號，速度與<xref:System.Windows.Forms.NumericUpDown.Accelerations%2A>屬性。 控制項的主要方法會<xref:System.Windows.Forms.NumericUpDown.UpButton%2A>和<xref:System.Windows.Forms.NumericUpDown.DownButton%2A>。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.NumericUpDown>
- [NumericUpDown 控制項](numericupdown-control-windows-forms.md)
- [如何：Windows Form NumericUpDown 控制項設定格式](how-to-set-the-format-for-the-windows-forms-numericupdown-control.md)
- [TextBox 控制項](textbox-control-windows-forms.md)
