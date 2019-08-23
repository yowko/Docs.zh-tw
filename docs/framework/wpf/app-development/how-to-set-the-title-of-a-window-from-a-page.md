---
title: 作法：從頁面設定視窗標題
ms.date: 03/30/2017
helpviewer_keywords:
- windows [WPF], setting title from a page
- title of window [WPF], setting from a page
- pages [WPF], setting window title from
ms.assetid: fecf0d19-3eb6-4f8c-a44f-ff1b6f2b34b3
ms.openlocfilehash: 0f618af89965822b0df96a264997dabd9cae7608
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940791"
---
# <a name="how-to-set-the-title-of-a-window-from-a-page"></a>作法：從頁面設定視窗標題
這個範例示範如何設定裝載之<xref:System.Windows.Controls.Page>視窗的標題。  
  
## <a name="example"></a>範例  
 頁面可以藉由設定<xref:System.Windows.Controls.Page.WindowTitle%2A>屬性來變更裝載它的視窗標題, 如下所示:  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowTitleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowTitlePage.xaml#setpagewindowtitlexaml)]  
  
> [!NOTE]
> 設定頁面<xref:System.Windows.Controls.Page.Title%2A>的屬性並不會變更視窗標題的值。 相反地<xref:System.Windows.Controls.Page.Title%2A> , 會在導覽歷程記錄中指定頁面專案的名稱。
