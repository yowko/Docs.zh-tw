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
ms.openlocfilehash: cc77668d9544cb37a8c9d1fcbdc3ed0351bc9eef
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-tab-characters-in-a-textbox-control"></a>如何：在 TextBox 控制項中啟用定位字元
這個範例示範如何啟用做為標準輸入中的定位字元接受<xref:System.Windows.Controls.TextBox>控制項。  
  
## <a name="example"></a>範例  
 若要啟用的定位字元接受做為輸入中<xref:System.Windows.Controls.TextBox>控制，請設定<xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsTab%2A>屬性**，則為 true**。  
  
 [!code-xaml[TextBox_EnablingTab#_AcceptsTab](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_EnablingTab/CS/Window1.xaml#_acceptstab)]  
  
## <a name="see-also"></a>另請參閱  
 [TextBox 概觀](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox 概觀](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
