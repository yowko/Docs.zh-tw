---
title: "如何：建立具有影像的按鈕"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Button controls [WPF], creating
ms.assetid: 607a193c-4098-4dd8-8dc0-51256cec2020
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e95f027a8e3568365fa7957c36241b6ec2c30d28
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-button-that-has-an-image"></a>如何：建立具有影像的按鈕
這個範例示範如何在包含影像<xref:System.Windows.Controls.Button>。  
  
## <a name="example"></a>範例  
 下列範例會建立兩個<xref:System.Windows.Controls.Button>控制項。 一個<xref:System.Windows.Controls.Button>包含文字和另一個包含映像。 影像是在呼叫資料，這是範例的專案資料夾的子資料夾中。 當使用者按一下<xref:System.Windows.Controls.Button>具有映像、 背景和其他項目的文字<xref:System.Windows.Controls.Button>變更。  
  
 這個範例會建立<xref:System.Windows.Controls.Button>控制使用的標記，但用來寫入的程式碼<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件處理常式。  
  
 [!code-xaml[BtnColor#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml#4)]  
  
 [!code-csharp[BtnColor#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml.cs#6)]
 [!code-vb[BtnColor#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BtnColor/VisualBasic/Pane1.xaml.vb#6)]  
  
## <a name="see-also"></a>請參閱  
 [控制項](../../../../docs/framework/wpf/controls/index.md)  
 [控制項程式庫](../../../../docs/framework/wpf/controls/control-library.md)
