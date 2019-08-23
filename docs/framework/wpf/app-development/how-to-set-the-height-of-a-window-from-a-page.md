---
title: 作法：從頁面設定視窗高度
ms.date: 03/30/2017
helpviewer_keywords:
- windows [WPF], setting height from a page
- pages [WPF], setting window height from
- height of window [WPF], setting from a page
ms.assetid: 4e4488ff-ab5c-4ee9-81a4-e1addb55c5cc
ms.openlocfilehash: c1041af88241011b51c96d7b61423344a32b25ca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940793"
---
# <a name="how-to-set-the-height-of-a-window-from-a-page"></a>HOW TO：從頁面設定視窗高度
這個範例說明如何從<xref:System.Windows.Controls.Page>設定視窗的高度。  
  
## <a name="example"></a>範例  
 可以藉由設定<xref:System.Windows.Controls.Page.WindowHeight%2A>來設定其主視窗的高度。 <xref:System.Windows.Controls.Page> 這個屬性可讓<xref:System.Windows.Controls.Page>不明確瞭解主控它的視窗類型。  
  
> [!NOTE]
> 若要使用<xref:System.Windows.Controls.Page.WindowHeight%2A>設定視窗的高度<xref:System.Windows.Controls.Page> , 必須是視窗的子系。  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowHeightXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowHeightPage.xaml#setpagewindowheightxaml)]
