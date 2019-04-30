---
title: DomainUpDown 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- DomainUpDown
helpviewer_keywords:
- spin button control [Windows Forms], about spin button
- DomainUpDown control [Windows Forms], about DomainUpDown control
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
ms.openlocfilehash: bfe3e7239f77c6f1a0d9bb46a96c704653b43364
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972064"
---
# <a name="domainupdown-control-overview-windows-forms"></a>DomainUpDown 控制項概觀 (Windows Form)
Windows Form<xref:System.Windows.Forms.DomainUpDown>控制項是本質上的文字方塊中的組合以及一組按鈕清單中向上或向下移動。 控制項顯示，並從清單中選擇設定文字字串。 按一下向上和向下按鈕移動清單、 按下向上鍵和向下鍵，或輸入字串符合清單中的項目，使用者可以選取字串。 這個控制項的可能用法之一是從名稱依字母順序排序清單中選取項目。  
  
> [!NOTE]
>  若要排序的清單，請設定<xref:System.Windows.Forms.DomainUpDown.Sorted%2A>屬性設`true`。  
  
 這個控制項的函式的清單方塊或下拉式方塊中，非常類似，但是它會佔用很少的空間。  
  
## <a name="key-properties"></a>索引鍵內容  
 控制項的索引鍵屬性是<xref:System.Windows.Forms.DomainUpDown.Items%2A>， <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>，和<xref:System.Windows.Forms.DomainUpDown.Wrap%2A>。 <xref:System.Windows.Forms.DomainUpDown.Items%2A>屬性包含的控制項中所顯示的文字值的物件清單。 如果<xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>設為`false`，控制項自動完成文字的使用者類型，並比對清單中的值。 如果<xref:System.Windows.Forms.DomainUpDown.Wrap%2A>設為`true`，過去的最後一個項目捲動會帶您前往第一個項目清單中，反之亦然。 控制項的主要方法會<xref:System.Windows.Forms.DomainUpDown.UpButton%2A>和<xref:System.Windows.Forms.DomainUpDown.DownButton%2A>。  
  
 此控制項會顯示只是文字字串。 如果您想要顯示數值的控制項，使用<xref:System.Windows.Forms.NumericUpDown>控制項。 如需詳細資訊，請參閱 < [NumericUpDown 控制項概觀](numericupdown-control-overview-windows-forms.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DomainUpDown>
- [DomainUpDown 控制項](domainupdown-control-windows-forms.md)
