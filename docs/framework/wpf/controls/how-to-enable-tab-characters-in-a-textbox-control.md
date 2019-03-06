---
title: HOW TO：在 TextBox 控制項中啟用定位字元
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [WPF], enabling tab characters
- tab characters [WPF], enabling
ms.assetid: 14b1b064-61f7-4958-be63-88d85b868d03
ms.openlocfilehash: 6d134757c3c08e92e608a7ff868b2f3d28a69b27
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356542"
---
# <a name="how-to-enable-tab-characters-in-a-textbox-control"></a>HOW TO：在 TextBox 控制項中啟用定位字元
此範例示範如何做為標準輸入中啟用定位字元接受<xref:System.Windows.Controls.TextBox>控制項。  
  
## <a name="example"></a>範例  
 若要啟用的定位點字元接受做為輸入，在<xref:System.Windows.Controls.TextBox>控制項，並設定<xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsTab%2A>屬性設定為 **，則為 true**。  
  
 [!code-xaml[TextBox_EnablingTab#_AcceptsTab](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_EnablingTab/CS/Window1.xaml#_acceptstab)]  
  
## <a name="see-also"></a>另請參閱
- [TextBox 概觀](textbox-overview.md)
- [RichTextBox 概觀](richtextbox-overview.md)
