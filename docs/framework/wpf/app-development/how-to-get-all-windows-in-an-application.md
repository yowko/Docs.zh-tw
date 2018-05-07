---
title: 如何： 取得所有 Windows 應用程式中
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- window objects [WPF], getting
ms.assetid: f120f06e-993b-4a97-9657-af0d1986981f
ms.openlocfilehash: 476905899f5f7d573a16ba876c72f28ea34bbf9d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-get-all-windows-in-an-application"></a>如何： 取得所有 Windows 應用程式中
這個範例示範如何取得所有<xref:System.Windows.Window>應用程式中的物件。  
  
## <a name="example"></a>範例  
 每個具現化<xref:System.Windows.Window>物件是否為可見或不是，會自動加入至集合中的視窗由管理的參考<xref:System.Windows.Application>，和從公開<xref:System.Windows.Application.Windows%2A>。  
  
 您可以列舉<xref:System.Windows.Application.Windows%2A>若要取得所有具現化的 windows，使用下列程式碼：  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetAllWindows](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/CustomWindow.xaml.cs#getallwindows)]
 [!code-vb[HOWTOWindowManagementSnippets#GetAllWindows](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/customwindow.xaml.vb#getallwindows)]
