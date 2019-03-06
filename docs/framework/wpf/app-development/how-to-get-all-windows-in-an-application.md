---
title: HOW TO：取得應用程式中的所有 Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- window objects [WPF], getting
ms.assetid: f120f06e-993b-4a97-9657-af0d1986981f
ms.openlocfilehash: 34316f0c6f81b960a8e00131a30b9a237b9ca938
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378814"
---
# <a name="how-to-get-all-windows-in-an-application"></a>HOW TO：取得應用程式中的所有 Windows
此範例示範如何取得所有<xref:System.Windows.Window>應用程式中的物件。  
  
## <a name="example"></a>範例  
 每個具現化<xref:System.Windows.Window>物件是否為可見或不是，會自動新增至受管理的視窗中參考的集合<xref:System.Windows.Application>，並公開從<xref:System.Windows.Application.Windows%2A>。  
  
 您可以列舉<xref:System.Windows.Application.Windows%2A>若要取得所有具現化的 windows，使用下列程式碼：  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetAllWindows](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/CustomWindow.xaml.cs#getallwindows)]
 [!code-vb[HOWTOWindowManagementSnippets#GetAllWindows](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/customwindow.xaml.vb#getallwindows)]
