---
title: "如何：在 TextBox 控制項中啟用定位字元"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TextBox control [WPF], enabling tab characters
- tab characters [WPF], enabling
ms.assetid: 14b1b064-61f7-4958-be63-88d85b868d03
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 35bcd5b3f53e8da72e8bd598641f1da87d424a2d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-tab-characters-in-a-textbox-control"></a>如何：在 TextBox 控制項中啟用定位字元
這個範例示範如何啟用做為標準輸入中的定位字元接受<xref:System.Windows.Controls.TextBox>控制項。  
  
## <a name="example"></a>範例  
 若要啟用的定位字元接受做為輸入中<xref:System.Windows.Controls.TextBox>控制，請設定<xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsTab%2A>屬性**，則為 true**。  
  
 [!code-xaml[TextBox_EnablingTab#_AcceptsTab](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_EnablingTab/CS/Window1.xaml#_acceptstab)]  
  
## <a name="see-also"></a>請參閱  
 [TextBox 概觀](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox 概觀](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
