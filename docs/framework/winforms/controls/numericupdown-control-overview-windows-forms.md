---
title: "NumericUpDown 控制項概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: NumericUpDown
helpviewer_keywords:
- numeric spin button control [Windows Forms], Windows Forms
- NumericUpDown control [Windows Forms], about NumericUpDown control
- spin button control [Windows Forms], Windows Forms
ms.assetid: cff3cf30-4d46-4381-87df-37bfe83c71c5
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 067a8862ee991213e584819e1cf99eddde06e2bc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="numericupdown-control-overview-windows-forms"></a>NumericUpDown 控制項概觀 (Windows Form)
<xref:System.Windows.Forms.NumericUpDown>控制項看起來像文字方塊中的組合和一對箭號，讓使用者可以按一下以調整值。 控制項顯示，並設定單一數值的數字值的固定選擇清單中。 使用者可以增加和減少數目，依序按一下向上和向下箭號，按向上鍵和向下鍵，或在控制項中輸入數字。 按一下向上鍵移動朝最大值。按一下向下鍵移動朝最小值。  
  
 具有靈活的功能，因為此控制項是明顯的選項，例如，如果您想要建立音樂的播放器應用程式的音量控制項。 <xref:System.Windows.Forms.NumericUpDown>控制項用在許多 Windows 控制台應用程式。  
  
## <a name="key-properties-and-methods"></a>索引鍵屬性和方法  
 在控制項的文字方塊中顯示的數字可以是各種不同的格式，包括十六進位。 如需詳細資訊，請參閱[How to： 設定 Windows Form NumericUpDown 控制項的格式](../../../../docs/framework/winforms/controls/how-to-set-the-format-for-the-windows-forms-numericupdown-control.md)。 控制項的索引鍵屬性是<xref:System.Windows.Forms.NumericUpDown.Value%2A>， <xref:System.Windows.Forms.NumericUpDown.Maximum%2A> （預設值 100） <xref:System.Windows.Forms.NumericUpDown.Minimum%2A> （預設值為 0） 和<xref:System.Windows.Forms.NumericUpDown.Increment%2A>（預設值 1）。 <xref:System.Windows.Forms.NumericUpDown.Value%2A>屬性設定控制項中選取的目前數目。 <xref:System.Windows.Forms.NumericUpDown.Increment%2A>屬性會設定當使用者按一下向上或向下箭號調整的數字量。 當焦點離開控制項時，任何輸入將會驗證最小和最大的數字值。 您可以增加時，使用者持續按下向上或向下箭號的數字，移動控制項的速度與<xref:System.Windows.Forms.NumericUpDown.Accelerations%2A>屬性。 控制項的主要方法是<xref:System.Windows.Forms.NumericUpDown.UpButton%2A>和<xref:System.Windows.Forms.NumericUpDown.DownButton%2A>。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.NumericUpDown>  
 [NumericUpDown 控制項](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)  
 [操作說明：為 Windows Forms NumericUpDown 控制項設定格式](../../../../docs/framework/winforms/controls/how-to-set-the-format-for-the-windows-forms-numericupdown-control.md)  
 [TextBox 控制項](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
