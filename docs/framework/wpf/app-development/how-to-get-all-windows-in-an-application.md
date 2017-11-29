---
title: "如何： 取得所有 Windows 應用程式中"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: window objects [WPF], getting
ms.assetid: f120f06e-993b-4a97-9657-af0d1986981f
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8577817f62ece1465f9c7577f3e1b7ff5ecefe44
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-get-all-windows-in-an-application"></a><span data-ttu-id="2e03a-102">如何： 取得所有 Windows 應用程式中</span><span class="sxs-lookup"><span data-stu-id="2e03a-102">How to: Get all Windows in an Application</span></span>
<span data-ttu-id="2e03a-103">這個範例示範如何取得所有<xref:System.Windows.Window>應用程式中的物件。</span><span class="sxs-lookup"><span data-stu-id="2e03a-103">This example shows how to get all <xref:System.Windows.Window> objects in an application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e03a-104">範例</span><span class="sxs-lookup"><span data-stu-id="2e03a-104">Example</span></span>  
 <span data-ttu-id="2e03a-105">每個具現化<xref:System.Windows.Window>物件是否為可見或不是，會自動加入至集合中的視窗由管理的參考<xref:System.Windows.Application>，和從公開<xref:System.Windows.Application.Windows%2A>。</span><span class="sxs-lookup"><span data-stu-id="2e03a-105">Every instantiated <xref:System.Windows.Window> object, whether visible or not, is automatically added to a collection of window references that is managed by <xref:System.Windows.Application>, and exposed from <xref:System.Windows.Application.Windows%2A>.</span></span>  
  
 <span data-ttu-id="2e03a-106">您可以列舉<xref:System.Windows.Application.Windows%2A>若要取得所有具現化的 windows，使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="2e03a-106">You can enumerate <xref:System.Windows.Application.Windows%2A> to get all instantiated windows using the following code:</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetAllWindows](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/CustomWindow.xaml.cs#getallwindows)]
 [!code-vb[HOWTOWindowManagementSnippets#GetAllWindows](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/customwindow.xaml.vb#getallwindows)]
