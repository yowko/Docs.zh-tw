---
title: 作法：從頁面設定視窗寬度
ms.date: 03/30/2017
helpviewer_keywords:
- width of windows [WPF], setting from a page
- windows [WPF], setting width from a page
- pages [WPF], setting window width from
ms.assetid: 31601c92-7889-472a-b07e-bf675ad21c92
ms.openlocfilehash: 1e16b75ecb85550facdf24a5b9e341cf0c061178
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940768"
---
# <a name="how-to-set-the-width-of-a-window-from-a-page"></a>HOW TO：從頁面設定視窗寬度
這個範例說明如何從<xref:System.Windows.Controls.Page>設定視窗的寬度。  
  
## <a name="example"></a>範例  
 可以藉由設定<xref:System.Windows.Controls.Page.WindowWidth%2A>來設定其主視窗的寬度。 <xref:System.Windows.Controls.Page> 這個屬性可讓<xref:System.Windows.Controls.Page>不明確瞭解主控它的視窗類型。  
  
> [!NOTE]
> 若要使用<xref:System.Windows.Controls.Page.WindowWidth%2A>設定視窗的寬度<xref:System.Windows.Controls.Page> , 必須是視窗的子系。  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowWidthXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowWidthPage.xaml#setpagewindowwidthxaml)]
