---
title: HOW TO：將 ListBox 繫結至資料
ms.date: 03/30/2017
helpviewer_keywords:
- ListBox controls [WPF], binding data to
- data binding [WPF], ListBox control
- binding data [WPF], to ListBox control
ms.assetid: de93a907-709a-44a7-84bf-578b846a3d8b
ms.openlocfilehash: 4dea53a524247d18628b3e7e7b2c06906dced53d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59106429"
---
# <a name="how-to-bind-a-listbox-to-data"></a>HOW TO：將 ListBox 繫結至資料
應用程式開發人員可以建立<xref:System.Windows.Controls.ListBox>不使用指定的每個內容控制項<xref:System.Windows.Controls.ListBoxItem>分開。 您可以使用資料繫結至資料繫結至個別的項目。  
  
 下列範例示範如何建立<xref:System.Windows.Controls.ListBox>填入<xref:System.Windows.Controls.ListBoxItem>藉由名為資料來源的資料繫結的項目*色彩*。 在此情況下不需要使用<xref:System.Windows.Controls.ListBoxItem>標記，以指定的每個項目內容。  
  
## <a name="example"></a>範例  
 [!code-xaml[ListBoxEvent#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#7)]  
[!code-xaml[ListBoxEvent#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#3)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.Controls.ListBoxItem>
- [控制項](../advanced/optimizing-performance-controls.md)
