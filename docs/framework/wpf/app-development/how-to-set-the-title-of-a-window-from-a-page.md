---
title: HOW TO：從頁面設定視窗標題
ms.date: 03/30/2017
helpviewer_keywords:
- windows [WPF], setting title from a page
- title of window [WPF], setting from a page
- pages [WPF], setting window title from
ms.assetid: fecf0d19-3eb6-4f8c-a44f-ff1b6f2b34b3
ms.openlocfilehash: 55444de6c61107979307b94910ba944e7001cf9e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053999"
---
# <a name="how-to-set-the-title-of-a-window-from-a-page"></a>HOW TO：從頁面設定視窗標題
此範例示範如何在其中設定視窗的標題<xref:System.Windows.Controls.Page>裝載。  
  
## <a name="example"></a>範例  
 頁面上可以變更會藉由設定其裝載視窗的標題<xref:System.Windows.Controls.Page.WindowTitle%2A>屬性，就像這樣：  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowTitleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowTitlePage.xaml#setpagewindowtitlexaml)]  
  
> [!NOTE]
>  設定<xref:System.Windows.Controls.Page.Title%2A>頁面的屬性不會變更視窗標題的值。 相反地，<xref:System.Windows.Controls.Page.Title%2A>巡覽記錄中指定頁面項目的名稱。
