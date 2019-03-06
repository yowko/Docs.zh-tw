---
title: HOW TO：從頁面設定視窗的寬度
ms.date: 03/30/2017
helpviewer_keywords:
- width of windows [WPF], setting from a page
- windows [WPF], setting width from a page
- pages [WPF], setting window width from
ms.assetid: 31601c92-7889-472a-b07e-bf675ad21c92
ms.openlocfilehash: fee6d4c9ae9dae03e81cc4be56576763cb59958b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379350"
---
# <a name="how-to-set-the-width-of-a-window-from-a-page"></a>HOW TO：從頁面設定視窗的寬度
此範例說明如何設定從視窗的寬度<xref:System.Windows.Controls.Page>。  
  
## <a name="example"></a>範例  
 A<xref:System.Windows.Controls.Page>可以設定其裝載視窗的寬度，藉由設定<xref:System.Windows.Controls.Page.WindowWidth%2A>。 這個屬性可讓<xref:System.Windows.Controls.Page>沒有明確的認知的裝載它的視窗類型。  
  
> [!NOTE]
>  若要設定的視窗中，使用寬度<xref:System.Windows.Controls.Page.WindowWidth%2A>、<xref:System.Windows.Controls.Page>必須是視窗的子系。  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowWidthXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowWidthPage.xaml#setpagewindowwidthxaml)]
