---
title: HOW TO：從頁面設定視窗寬度
ms.date: 03/30/2017
helpviewer_keywords:
- width of windows [WPF], setting from a page
- windows [WPF], setting width from a page
- pages [WPF], setting window width from
ms.assetid: 31601c92-7889-472a-b07e-bf675ad21c92
ms.openlocfilehash: fee6d4c9ae9dae03e81cc4be56576763cb59958b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62006711"
---
# <a name="how-to-set-the-width-of-a-window-from-a-page"></a>HOW TO：從頁面設定視窗寬度
此範例說明如何設定從視窗的寬度<xref:System.Windows.Controls.Page>。  
  
## <a name="example"></a>範例  
 A<xref:System.Windows.Controls.Page>可以設定其裝載視窗的寬度，藉由設定<xref:System.Windows.Controls.Page.WindowWidth%2A>。 這個屬性可讓<xref:System.Windows.Controls.Page>沒有明確的認知的裝載它的視窗類型。  
  
> [!NOTE]
>  若要設定的視窗中，使用寬度<xref:System.Windows.Controls.Page.WindowWidth%2A>、<xref:System.Windows.Controls.Page>必須是視窗的子系。  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowWidthXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowWidthPage.xaml#setpagewindowwidthxaml)]
