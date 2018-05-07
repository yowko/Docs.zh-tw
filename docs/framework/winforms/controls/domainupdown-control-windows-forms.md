---
title: DomainUpDown 控制項 (Windows Form)
ms.date: 03/30/2017
helpviewer_keywords:
- DomainUpDown control [Windows Forms]
- spin button control [Windows Forms], up-down controls
- up-down controls
- spin button control
- up-down controls [Windows Forms], spin button controls
ms.assetid: fb7cf017-e931-4a95-9d21-8caee4ee122a
ms.openlocfilehash: c23f374f1ec9cab6e43b12d32b97c40533ac36cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="domainupdown-control-windows-forms"></a>DomainUpDown 控制項 (Windows Form)
Windows Form<xref:System.Windows.Forms.DomainUpDown>控制項看起來對按鈕及文字方塊中的組合的清單中向上或向下移動。 控制項顯示，並設定選項的清單中的文字字串。 按一下向上和向下按鈕移動清單、 按向上鍵和向下鍵，或輸入清單中的項目相符的字串，使用者可以選取的字串。 這個控制項的其中一個可能的使用是從依字母順序排序的名稱清單中選取項目。 (若要排序清單，請設定<xref:System.Windows.Forms.DomainUpDown.Sorted%2A>屬性`true`。)這個控制項的功能清單方塊或下拉式方塊中，非常類似，但是它會佔用很少的空間。  
  
 控制項的索引鍵屬性是<xref:System.Windows.Forms.DomainUpDown.Items%2A>， <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>，和<xref:System.Windows.Forms.DomainUpDown.Wrap%2A>。 <xref:System.Windows.Forms.DomainUpDown.Items%2A>屬性包含的控制項中顯示其文字值的物件清單。 如果<xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>設`false`，控制項時自動完成文字使用者輸入，然後進行比對清單中的值。 如果<xref:System.Windows.Forms.DomainUpDown.Wrap%2A>設`true`，過去的最後一個項目捲動會帶您前往第一個項目在清單中，反之亦然。 控制項的主要方法是<xref:System.Windows.Forms.DomainUpDown.UpButton%2A>和<xref:System.Windows.Forms.DomainUpDown.DownButton%2A>。  
  
 此控制項顯示只是文字字串。 如果您想要顯示數值的控制項，使用<xref:System.Windows.Forms.NumericUpDown>控制項。 如需詳細資訊，請參閱[NumericUpDown 控制項](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [DomainUpDown 控制項概觀](../../../../docs/framework/winforms/controls/domainupdown-control-overview-windows-forms.md)  
 導入的一般概念<xref:System.Windows.Forms.DomainUpDown>控制項，可讓使用者瀏覽並選取從文字字串的清單。  
  
 [操作說明：以程式設計的方式將項目加入至 Windows Forms DomainUpDown 控制項](../../../../docs/framework/winforms/controls/how-to-add-items-to-windows-forms-domainupdown-controls-programmatically.md)  
 描述如何指定文字字串<xref:System.Windows.Forms.DomainUpDown>控制項應顯示。  
  
 [操作說明：從 Windows Forms DomainUpDown 控制項中移除項目](../../../../docs/framework/winforms/controls/how-to-remove-items-from-windows-forms-domainupdown-controls.md)  
 描述如何刪除項目從<xref:System.Windows.Forms.DomainUpDown>程式碼中的控制項。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Windows.Forms.DomainUpDown>  
 描述這個類別，並且提供其所有成員的連結。  
  
 <xref:System.Windows.Forms.NumericUpDown>  
 描述這個類別，並且提供其所有成員都的連結...  
  
## <a name="related-sections"></a>相關章節  
 [可以在 Windows Forms 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 提供 Windows Form 控制項的完整清單，以及其用法的資訊連結。
