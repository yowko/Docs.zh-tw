---
title: HOW TO：在 TextBox 控制項中啟用定位字元
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [WPF], enabling tab characters
- tab characters [WPF], enabling
ms.assetid: 14b1b064-61f7-4958-be63-88d85b868d03
ms.openlocfilehash: 9a01ae93d1b75c604fbe4f15f720e0a84086bd1a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59149483"
---
# <a name="how-to-enable-tab-characters-in-a-textbox-control"></a>HOW TO：在 TextBox 控制項中啟用定位字元
此範例示範如何做為標準輸入中啟用定位字元接受<xref:System.Windows.Controls.TextBox>控制項。  
  
## <a name="example"></a>範例  
 若要啟用的定位點字元接受做為輸入，在<xref:System.Windows.Controls.TextBox>控制項，並設定<xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsTab%2A>屬性設定為 **，則為 true**。  
  
 [!code-xaml[TextBox_EnablingTab#_AcceptsTab](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_EnablingTab/CS/Window1.xaml#_acceptstab)]  
  
## <a name="see-also"></a>另請參閱

- [TextBox 概觀](textbox-overview.md)
- [RichTextBox 概觀](richtextbox-overview.md)
