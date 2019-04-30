---
title: HOW TO：取得應用程式中的所有視窗
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- window objects [WPF], getting
ms.assetid: f120f06e-993b-4a97-9657-af0d1986981f
ms.openlocfilehash: 34316f0c6f81b960a8e00131a30b9a237b9ca938
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947767"
---
# <a name="how-to-get-all-windows-in-an-application"></a><span data-ttu-id="1df14-102">HOW TO：取得應用程式中的所有視窗</span><span class="sxs-lookup"><span data-stu-id="1df14-102">How to: Get all Windows in an Application</span></span>
<span data-ttu-id="1df14-103">此範例示範如何取得所有<xref:System.Windows.Window>應用程式中的物件。</span><span class="sxs-lookup"><span data-stu-id="1df14-103">This example shows how to get all <xref:System.Windows.Window> objects in an application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1df14-104">範例</span><span class="sxs-lookup"><span data-stu-id="1df14-104">Example</span></span>  
 <span data-ttu-id="1df14-105">每個具現化<xref:System.Windows.Window>物件是否為可見或不是，會自動新增至受管理的視窗中參考的集合<xref:System.Windows.Application>，並公開從<xref:System.Windows.Application.Windows%2A>。</span><span class="sxs-lookup"><span data-stu-id="1df14-105">Every instantiated <xref:System.Windows.Window> object, whether visible or not, is automatically added to a collection of window references that is managed by <xref:System.Windows.Application>, and exposed from <xref:System.Windows.Application.Windows%2A>.</span></span>  
  
 <span data-ttu-id="1df14-106">您可以列舉<xref:System.Windows.Application.Windows%2A>若要取得所有具現化的 windows，使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="1df14-106">You can enumerate <xref:System.Windows.Application.Windows%2A> to get all instantiated windows using the following code:</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetAllWindows](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/CustomWindow.xaml.cs#getallwindows)]
 [!code-vb[HOWTOWindowManagementSnippets#GetAllWindows](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/customwindow.xaml.vb#getallwindows)]
