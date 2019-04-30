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
ms.openlocfilehash: 83d674e3fb7ff7e715b75c635b891cd4e9703a21
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972051"
---
# <a name="domainupdown-control-windows-forms"></a>DomainUpDown 控制項 (Windows Form)
Windows Form<xref:System.Windows.Forms.DomainUpDown>控制項看起來像組合的文字方塊和按鈕的清單中向上或向下移動。 控制項顯示，並從清單中選擇設定文字字串。 按一下向上和向下按鈕移動清單、 按下向上鍵和向下鍵，或輸入字串符合清單中的項目，使用者可以選取字串。 這個控制項的可能用法之一是從名稱依字母順序排序清單中選取項目。 (若要排序的清單，請設定<xref:System.Windows.Forms.DomainUpDown.Sorted%2A>屬性設`true`。)這個控制項的函式的清單方塊或下拉式方塊中，非常類似，但是它會佔用很少的空間。  
  
 控制項的索引鍵屬性是<xref:System.Windows.Forms.DomainUpDown.Items%2A>， <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>，和<xref:System.Windows.Forms.DomainUpDown.Wrap%2A>。 <xref:System.Windows.Forms.DomainUpDown.Items%2A>屬性包含的控制項中所顯示的文字值的物件清單。 如果<xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>設為`false`，控制項自動完成文字的使用者類型，並比對清單中的值。 如果<xref:System.Windows.Forms.DomainUpDown.Wrap%2A>設為`true`，過去的最後一個項目捲動會帶您前往第一個項目清單中，反之亦然。 控制項的主要方法會<xref:System.Windows.Forms.DomainUpDown.UpButton%2A>和<xref:System.Windows.Forms.DomainUpDown.DownButton%2A>。  
  
 此控制項會顯示只是文字字串。 如果您想要顯示數值的控制項，使用<xref:System.Windows.Forms.NumericUpDown>控制項。 如需詳細資訊，請參閱 < [NumericUpDown 控制項](numericupdown-control-windows-forms.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [DomainUpDown 控制項概觀](domainupdown-control-overview-windows-forms.md)  
 導入的一般概念<xref:System.Windows.Forms.DomainUpDown>控制項，可讓使用者瀏覽和選取從文字字串的清單。  
  
 [如何：以程式設計方式將項目加入 Windows Form DomainUpDown 控制項](how-to-add-items-to-windows-forms-domainupdown-controls-programmatically.md)  
 描述如何指定文字字串<xref:System.Windows.Forms.DomainUpDown>控制項應顯示。  
  
 [如何：移除 Windows Form DomainUpDown 控制項中的項目](how-to-remove-items-from-windows-forms-domainupdown-controls.md)  
 描述如何刪除項目從<xref:System.Windows.Forms.DomainUpDown>在程式碼中的控制項。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Windows.Forms.DomainUpDown>  
 說明這個類別，並且提供其所有成員的連結。  
  
 <xref:System.Windows.Forms.NumericUpDown>  
 描述這個類別並且連結到其所有成員...  
  
## <a name="related-sections"></a>相關章節  
 [可以在 Windows Forms 上使用的控制項](controls-to-use-on-windows-forms.md)  
 提供 Windows Form 控制項的完整清單，以及其用法的資訊連結。
