---
title: DomainUpDown 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- DomainUpDown
helpviewer_keywords:
- spin button control [Windows Forms], about spin button
- DomainUpDown control [Windows Forms], about DomainUpDown control
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
ms.openlocfilehash: 6fda542204e2b41dd1d729d2b940c6f38a5812ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965305"
---
# <a name="domainupdown-control-overview-windows-forms"></a>DomainUpDown 控制項概觀 (Windows Form)
Windows Forms <xref:System.Windows.Forms.DomainUpDown>控制項基本上是文字方塊和一對按鈕的組合, 可在清單中向上或向下移動。 控制項會顯示並設定挑選清單中的文字字串。 使用者可以選取字串, 方法是按一下向上和向下按鈕以移動清單、按向上鍵和向下鍵, 或輸入符合清單中專案的字串。 此控制項的其中一個可能用途是從依字母順序排序的名稱清單中選取專案。  
  
> [!NOTE]
> 若要排序清單, 請將<xref:System.Windows.Forms.DomainUpDown.Sorted%2A>屬性設定`true`為。  
  
 此控制項的功能與清單方塊或下拉式方塊非常類似, 但佔用的空間非常少。  
  
## <a name="key-properties"></a>索引鍵內容  
 控制項的索引鍵屬性為<xref:System.Windows.Forms.DomainUpDown.Items%2A>、 <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>和<xref:System.Windows.Forms.DomainUpDown.Wrap%2A>。 <xref:System.Windows.Forms.DomainUpDown.Items%2A>屬性包含物件的清單, 其文字值會顯示在控制項中。 如果<xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>設定為`false`, 控制項會自動完成使用者輸入的文字, 並將其與清單中的值比對。 如果<xref:System.Windows.Forms.DomainUpDown.Wrap%2A>設定為`true`, 則在最後一個專案之後的滾動會帶您前往清單中的第一個專案, 反之亦然。 控制項的主要方法是<xref:System.Windows.Forms.DomainUpDown.UpButton%2A>和。 <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>  
  
 此控制項只會顯示文字字串。 如果您想要顯示數值的控制項, 請使用<xref:System.Windows.Forms.NumericUpDown>控制項。 如需詳細資訊, 請參閱[NumericUpDown 控制項總覽](numericupdown-control-overview-windows-forms.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DomainUpDown>
- [DomainUpDown 控制項](domainupdown-control-windows-forms.md)
