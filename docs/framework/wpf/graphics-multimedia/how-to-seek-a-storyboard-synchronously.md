---
title: "操作說明：同步搜尋分鏡腳本"
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
helpviewer_keywords:
- seeking Storyboards synchronously [WPF]
- Storyboards [WPF], seeking synchronously
ms.assetid: 03e06271-a946-4810-88ea-3fb4cfa9e0f1
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 45d71dde85ea65e45a36b4f938e1fd5135cc0e00
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-seek-a-storyboard-synchronously"></a><span data-ttu-id="d3145-102">操作說明：同步搜尋分鏡腳本</span><span class="sxs-lookup"><span data-stu-id="d3145-102">How to: Seek a Storyboard Synchronously</span></span>
<span data-ttu-id="d3145-103">下列範例示範如何使用<xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>方法<xref:System.Windows.Media.Animation.Storyboard>來以同步方式搜尋至分鏡腳本動畫中的任何位置。</span><span class="sxs-lookup"><span data-stu-id="d3145-103">The following example shows how to use the <xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A> method of a <xref:System.Windows.Media.Animation.Storyboard> to seek to any position in a storyboard animation synchronously.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3145-104">範例</span><span class="sxs-lookup"><span data-stu-id="d3145-104">Example</span></span>  
 <span data-ttu-id="d3145-105">以下是範例的 XAML 標記。</span><span class="sxs-lookup"><span data-stu-id="d3145-105">The following is the XAML markup for the sample.</span></span>  
  
 [!code-xaml[SeekStoryboard_snip#SeekStoryboardSynchronouslyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardSynchronouslyExample.xaml#seekstoryboardsynchronouslyexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="d3145-106">範例</span><span class="sxs-lookup"><span data-stu-id="d3145-106">Example</span></span>  
 <span data-ttu-id="d3145-107">以下是搭配上述 XAML 程式碼使用的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d3145-107">The following is the code used with the XAML code above.</span></span>  
  
 [!code-csharp[SeekStoryboard_snip#SeekStoryboardSynchronouslyCodeBehindExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardSynchronouslyExample.xaml.cs#seekstoryboardsynchronouslycodebehindexamplewholepage)]
 [!code-vb[SeekStoryboard_snip#SeekStoryboardSynchronouslyCodeBehindExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SeekStoryboard_snip/VisualBasic/SeekStoryboardSynchronouslyExample.xaml.vb#seekstoryboardsynchronouslycodebehindexamplewholepage)]
