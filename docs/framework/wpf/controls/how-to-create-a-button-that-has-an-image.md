---
title: HOW TO：建立具有影像的按鈕
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Button controls [WPF], creating
ms.assetid: 607a193c-4098-4dd8-8dc0-51256cec2020
ms.openlocfilehash: 5be928ac75ad727feabcde07ac0c6dc76ed130e6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59120714"
---
# <a name="how-to-create-a-button-that-has-an-image"></a>HOW TO：建立具有影像的按鈕
此範例示範如何在包含影像<xref:System.Windows.Controls.Button>。  
  
## <a name="example"></a>範例  
 下列範例會建立兩個<xref:System.Windows.Controls.Button>控制項。 一個<xref:System.Windows.Controls.Button>包含文字，另一個映像。 映像位於稱為資料，也就是此範例的專案資料夾的子資料夾的資料夾中。 當使用者按一下<xref:System.Windows.Controls.Button>有映像、 背景和其他文字<xref:System.Windows.Controls.Button>變更。  
  
 這個範例會建立<xref:System.Windows.Controls.Button>藉由使用標記來控制，但會使用程式碼撰寫<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件處理常式。  
  
 [!code-xaml[BtnColor#4](~/samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml#4)]  
  
 [!code-csharp[BtnColor#6](~/samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml.cs#6)]
 [!code-vb[BtnColor#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BtnColor/VisualBasic/Pane1.xaml.vb#6)]  
  
## <a name="see-also"></a>另請參閱

- [控制項](index.md)
- [控制項程式庫](control-library.md)
