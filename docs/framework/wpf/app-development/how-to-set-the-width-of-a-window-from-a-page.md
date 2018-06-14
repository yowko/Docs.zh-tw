---
title: 如何： 設定頁面的視窗的寬度
ms.date: 03/30/2017
helpviewer_keywords:
- width of windows [WPF], setting from a page
- windows [WPF], setting width from a page
- pages [WPF], setting window width from
ms.assetid: 31601c92-7889-472a-b07e-bf675ad21c92
ms.openlocfilehash: a0ae0e136e0b7f1cd2a2ec56455e14723e8fa306
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545986"
---
# <a name="how-to-set-the-width-of-a-window-from-a-page"></a>如何： 設定頁面的視窗的寬度
此範例說明如何設定從視窗的寬度<xref:System.Windows.Controls.Page>。  
  
## <a name="example"></a>範例  
 A<xref:System.Windows.Controls.Page>設定即可設定其裝載視窗的寬度<xref:System.Windows.Controls.Page.WindowWidth%2A>。 這個屬性允許<xref:System.Windows.Controls.Page>沒有明確的認知的視窗針對裝載它的類型。  
  
> [!NOTE]
>  若要設定的視窗，使用寬度<xref:System.Windows.Controls.Page.WindowWidth%2A>、<xref:System.Windows.Controls.Page>必須是視窗的子系。  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowWidthXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowWidthPage.xaml#setpagewindowwidthxaml)]
