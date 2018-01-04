---
title: "如何：擷取文字選取項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF], retrieving
- TextBox control [WPF], retrieving text
- retrieving text [WPF]
ms.assetid: d5793172-1e11-4a39-9be0-73f336ed858d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 32be79811de4b8056449c2c6d6c53eca8cc063f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-retrieve-a-text-selection"></a>如何：擷取文字選取項目
這個範例會示範一個方式來使用<xref:System.Windows.Controls.TextBox.SelectedText%2A>屬性，以擷取使用者在選取的文字<xref:System.Windows.Controls.TextBox>控制項。  
  
## <a name="example"></a>範例  
 下列[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]範例會示範定義<xref:System.Windows.Controls.TextBox>控制項，其中包含一些文字，若要選取，而<xref:System.Windows.Controls.Button>與指定的控制項<xref:System.Windows.Controls.Button.OnClick%2A>方法。  
  
 在此範例中，具有相關聯的按鈕<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件處理常式用來擷取文字選取範圍。 當使用者按一下按鈕，<xref:System.Windows.Controls.Button.OnClick%2A>方法在文字方塊中選取的文字複製成字串。 特定情況下，根據的文字選取範圍會擷取 （按一下按鈕），以及與該選取項目 （複製為字串的文字選取範圍） 中，所採取的動作可以輕鬆地修改以容納各種案例。  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxSelectTextXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxselecttextxaml)]  
  
## <a name="example"></a>範例  
 下列[!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)]範例所示<xref:System.Windows.Controls.Button.OnClick%2A>按鈕中所定義的事件處理常式[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]此範例中。  
  
 [!code-csharp[TextBox_MiscCode#_SelectText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_selecttext)]
 [!code-vb[TextBox_MiscCode#_SelectText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_selecttext)]  
  
## <a name="see-also"></a>請參閱  
 [TextBox 概觀](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox 概觀](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
