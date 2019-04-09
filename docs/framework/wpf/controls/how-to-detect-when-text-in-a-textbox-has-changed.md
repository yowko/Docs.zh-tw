---
title: HOW TO：偵測 TextBox 中的文字何時變更
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 1adadb0f071815930d34f40ddf244ffc8c19131b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091144"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a>HOW TO：偵測 TextBox 中的文字何時變更
此範例示範使用一種方式<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>事件，以執行方法，每次中的文字<xref:System.Windows.Controls.TextBox>控制項已變更。  
  
 中的程式碼後置類別[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，其中包含<xref:System.Windows.Controls.TextBox>控制項，您想要監視的變更，插入要每次呼叫的方法<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>引發事件。  這個方法必須不符合預期的簽章<xref:System.Windows.Controls.TextChangedEventHandler>委派。  
  
 會呼叫事件處理常式時的內容<xref:System.Windows.Controls.TextBox>控制項已變更，可能是由使用者或以程式設計的方式。  
  
 **注意：** 時，會引發這個事件<xref:System.Windows.Controls.TextBox>建立控制項並將其一開始填入文字。  
  
## <a name="example"></a>範例  
 在  [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ，定義您<xref:System.Windows.Controls.TextBox>控制項，指定<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>屬性值符合事件處理常式方法名稱。  
  
 [!code-xaml[TextBox_MiscCode#_TextChangedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]  
  
## <a name="example"></a>範例  
 中的程式碼後置類別[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，其中包含<xref:System.Windows.Controls.TextBox>控制項，您想要監視的變更，插入要每次呼叫的方法<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>引發事件。  這個方法必須不符合預期的簽章<xref:System.Windows.Controls.TextChangedEventHandler>委派。  
  
 [!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
 [!code-vb[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]  
  
 會呼叫事件處理常式時的內容<xref:System.Windows.Controls.TextBox>控制項已變更，可能是由使用者或以程式設計的方式。  
  
 **注意：** 時，會引發這個事件<xref:System.Windows.Controls.TextBox>建立控制項並將其一開始填入文字。  
  
 註解  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.TextChangedEventArgs>
- [TextBox 概觀](textbox-overview.md)
- [RichTextBox 概觀](richtextbox-overview.md)
