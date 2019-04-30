---
title: HOW TO：從頁面設定視窗高度
ms.date: 03/30/2017
helpviewer_keywords:
- windows [WPF], setting height from a page
- pages [WPF], setting window height from
- height of window [WPF], setting from a page
ms.assetid: 4e4488ff-ab5c-4ee9-81a4-e1addb55c5cc
ms.openlocfilehash: c99ea134478635f368b71443f43e4d8f772cb5aa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007297"
---
# <a name="how-to-set-the-height-of-a-window-from-a-page"></a>HOW TO：從頁面設定視窗高度
此範例說明如何設定從視窗的高度<xref:System.Windows.Controls.Page>。  
  
## <a name="example"></a>範例  
 A<xref:System.Windows.Controls.Page>可以設定其裝載視窗的高度，藉由設定<xref:System.Windows.Controls.Page.WindowHeight%2A>。 這個屬性可讓<xref:System.Windows.Controls.Page>沒有明確的認知的裝載它的視窗類型。  
  
> [!NOTE]
>  若要設定的視窗中，使用高度<xref:System.Windows.Controls.Page.WindowHeight%2A>、<xref:System.Windows.Controls.Page>必須是視窗的子系。  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowHeightXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowHeightPage.xaml#setpagewindowheightxaml)]
