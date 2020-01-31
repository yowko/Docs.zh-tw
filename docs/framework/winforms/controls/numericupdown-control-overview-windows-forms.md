---
title: NumericUpDown 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- NumericUpDown
helpviewer_keywords:
- numeric spin button control [Windows Forms], Windows Forms
- NumericUpDown control [Windows Forms], about NumericUpDown control
- spin button control [Windows Forms], Windows Forms
ms.assetid: cff3cf30-4d46-4381-87df-37bfe83c71c5
ms.openlocfilehash: 3e24fa543df9028e9866d91ec60c3cf88578ac56
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740796"
---
# <a name="numericupdown-control-overview-windows-forms"></a>NumericUpDown 控制項概觀 (Windows Form)
<xref:System.Windows.Forms.NumericUpDown> 控制項看起來像是文字方塊和一對箭號的組合，使用者可以按一下來調整值。 控制項會顯示並設定固定數值值挑選清單中的單一數值。 使用者可以藉由按一下向上和向下箭號、按向上鍵與向下箭號，或在控制項的文字方塊部分輸入數位來增加和減少數位。 按一下向上鍵會將數位往上移到最大值;按一下向下鍵會將數位往上移動到最小值。  
  
 這個控制項的功能很多，例如，如果您想要建立音樂播放機應用程式的音量控制，這是一種明顯的選擇。 <xref:System.Windows.Forms.NumericUpDown> 控制項用於許多 Windows 控制台應用程式中。  
  
## <a name="key-properties-and-methods"></a>索引鍵屬性和方法  
 顯示在控制項文字方塊中的數位可以使用各種格式，包括十六進位。 如需詳細資訊，請參閱[如何：設定 Windows Forms NumericUpDown 控制項的格式](how-to-set-the-format-for-the-windows-forms-numericupdown-control.md)。 控制項的索引鍵屬性為 <xref:System.Windows.Forms.NumericUpDown.Value%2A>、<xref:System.Windows.Forms.NumericUpDown.Maximum%2A> （預設值100）、<xref:System.Windows.Forms.NumericUpDown.Minimum%2A> （預設值0）和 <xref:System.Windows.Forms.NumericUpDown.Increment%2A> （預設值為1）。 <xref:System.Windows.Forms.NumericUpDown.Value%2A> 屬性會設定在控制項中選取的目前數位。 <xref:System.Windows.Forms.NumericUpDown.Increment%2A> 屬性會設定當使用者按一下向上或向下箭號時，數位的調整量。 當焦點移開控制項時，任何類型的輸入都會根據最小值和最大數值進行驗證。 當使用者連續按下向上或向下箭號時，您可以使用 [<xref:System.Windows.Forms.NumericUpDown.Accelerations%2A>] 屬性來增加控制項在數位之間移動的速度。 控制項的主要方法是 <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> 和 <xref:System.Windows.Forms.NumericUpDown.DownButton%2A>。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.NumericUpDown>
- [NumericUpDown 控制項](numericupdown-control-windows-forms.md)
- [如何：為 Windows Forms NumericUpDown 控制項設定格式](how-to-set-the-format-for-the-windows-forms-numericupdown-control.md)
- [TextBox 控制項](textbox-control-windows-forms.md)
