---
title: "DomainUpDown 控制項概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DomainUpDown
helpviewer_keywords:
- spin button control [Windows Forms], about spin button
- DomainUpDown control [Windows Forms], about DomainUpDown control
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e5a86dc6c56c3afff8d8a3a4ca2c5d5efa8eac1a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="domainupdown-control-overview-windows-forms"></a>DomainUpDown 控制項概觀 (Windows Form)
Windows Form<xref:System.Windows.Forms.DomainUpDown>控制項是基本上文字方塊中的組合和一組的清單中向上或向下移動的按鈕。 控制項顯示，並設定選項的清單中的文字字串。 按一下向上和向下按鈕移動清單、 按向上鍵和向下鍵，或輸入清單中的項目相符的字串，使用者可以選取的字串。 這個控制項的其中一個可能的使用是從依字母順序排序的名稱清單中選取項目。  
  
> [!NOTE]
>  若要排序清單，請設定<xref:System.Windows.Forms.DomainUpDown.Sorted%2A>屬性`true`。  
  
 這個控制項的功能清單方塊或下拉式方塊中，非常類似，但是它會佔用很少的空間。  
  
## <a name="key-properties"></a>索引鍵內容  
 控制項的索引鍵屬性是<xref:System.Windows.Forms.DomainUpDown.Items%2A>， <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>，和<xref:System.Windows.Forms.DomainUpDown.Wrap%2A>。 <xref:System.Windows.Forms.DomainUpDown.Items%2A>屬性包含的控制項中顯示其文字值的物件清單。 如果<xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>設`false`，控制項時自動完成文字使用者輸入，然後進行比對清單中的值。 如果<xref:System.Windows.Forms.DomainUpDown.Wrap%2A>設`true`，過去的最後一個項目捲動會帶您前往第一個項目在清單中，反之亦然。 控制項的主要方法是<xref:System.Windows.Forms.DomainUpDown.UpButton%2A>和<xref:System.Windows.Forms.DomainUpDown.DownButton%2A>。  
  
 此控制項顯示只是文字字串。 如果您想要顯示數值的控制項，使用<xref:System.Windows.Forms.NumericUpDown>控制項。 如需詳細資訊，請參閱[NumericUpDown 控制項概觀](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md)。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.DomainUpDown>  
 [DomainUpDown 控制項](../../../../docs/framework/winforms/controls/domainupdown-control-windows-forms.md)
