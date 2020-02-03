---
title: DomainUpDown 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- DomainUpDown control [Windows Forms]
- spin button control [Windows Forms], up-down controls
- up-down controls
- spin button control
- up-down controls [Windows Forms], spin button controls
ms.assetid: fb7cf017-e931-4a95-9d21-8caee4ee122a
ms.openlocfilehash: b538350a84e341d6b2759a7db28f8799f3777a86
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745835"
---
# <a name="domainupdown-control-windows-forms"></a>DomainUpDown 控制項 (Windows Form)
Windows Forms <xref:System.Windows.Forms.DomainUpDown> 控制項看起來像是文字方塊和一對按鈕的組合，可在清單中向上或向下移動。 控制項會顯示並設定挑選清單中的文字字串。 使用者可以選取字串，方法是按一下向上和向下按鈕以移動清單、按向上鍵和向下鍵，或輸入符合清單中專案的字串。 此控制項的其中一個可能用途是從依字母順序排序的名稱清單中選取專案。 （若要排序清單，請將 [<xref:System.Windows.Forms.DomainUpDown.Sorted%2A>] 屬性設定為 [`true`]）。此控制項的功能與清單方塊或下拉式方塊非常類似，但佔用的空間非常少。  
  
 控制項的索引鍵屬性為 <xref:System.Windows.Forms.DomainUpDown.Items%2A>、<xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>和 <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>。 <xref:System.Windows.Forms.DomainUpDown.Items%2A> 屬性包含其文字值顯示在控制項中的物件清單。 如果 <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> 設定為 [`false`]，控制項會自動完成使用者輸入的文字，並將其與清單中的值比對。 如果 <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> 設定為 `true`，則在最後一個專案之後的滾動會帶您前往清單中的第一個專案，反之亦然。 控制項的主要方法是 <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> 和 <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>。  
  
 此控制項只會顯示文字字串。 如果您想要顯示數值的控制項，請使用 <xref:System.Windows.Forms.NumericUpDown> 控制項。 如需詳細資訊，請參閱[NumericUpDown Control](numericupdown-control-windows-forms.md) 。  
  
## <a name="in-this-section"></a>本節內容  
 [DomainUpDown 控制項概觀](domainupdown-control-overview-windows-forms.md)  
 介紹 <xref:System.Windows.Forms.DomainUpDown> 控制項的一般概念，可讓使用者流覽並從文字字串清單中選取。  
  
 [操作說明：以程式設計的方式將項目加入至 Windows Forms DomainUpDown 控制項](how-to-add-items-to-windows-forms-domainupdown-controls-programmatically.md)  
 描述如何指定 <xref:System.Windows.Forms.DomainUpDown> 控制項應顯示的文字字串。  
  
 [操作說明：從 Windows Forms DomainUpDown 控制項中移除項目](how-to-remove-items-from-windows-forms-domainupdown-controls.md)  
 描述如何在程式碼中刪除 <xref:System.Windows.Forms.DomainUpDown> 控制項的專案。  
  
## <a name="reference"></a>參考  
 <xref:System.Windows.Forms.DomainUpDown>  
 說明這個類別，並且提供其所有成員的連結。  
  
 <xref:System.Windows.Forms.NumericUpDown>  
 描述這個類別，並具有其所有成員的連結。  
  
## <a name="related-sections"></a>相關章節  
 [可以在 Windows Forms 上使用的控制項](controls-to-use-on-windows-forms.md)  
 提供 Windows Form 控制項的完整清單，以及其用法的資訊連結。
