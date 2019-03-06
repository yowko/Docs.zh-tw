---
title: 儲存筆墨
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ISF (Ink Serialized Format)
- storing ink [WPF]
- ink [WPF], storing
- retrieving ink [WPF]
- Ink Serialized Format (ISF)
ms.assetid: a3f6d16b-d682-4680-9965-907332b4d2b8
ms.openlocfilehash: aec89286cfac9b0a315dc2d00135543511b2d1ac
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57353955"
---
# <a name="storing-ink"></a><span data-ttu-id="c4e2a-102">儲存筆墨</span><span class="sxs-lookup"><span data-stu-id="c4e2a-102">Storing Ink</span></span>
<span data-ttu-id="c4e2a-103"><xref:System.Windows.Ink.StrokeCollection.Save%2A>方法儲存筆墨為 Ink Serialized Format (ISF) 提供支援。</span><span class="sxs-lookup"><span data-stu-id="c4e2a-103">The <xref:System.Windows.Ink.StrokeCollection.Save%2A> methods provide support for storing ink as Ink Serialized Format (ISF).</span></span> <span data-ttu-id="c4e2a-104">建構函式<xref:System.Windows.Ink.StrokeCollection>類別提供讀取筆墨資料的支援。</span><span class="sxs-lookup"><span data-stu-id="c4e2a-104">Constructors for the <xref:System.Windows.Ink.StrokeCollection> class provide support for reading ink data.</span></span>  
  
## <a name="ink-storage-and-retrieval"></a><span data-ttu-id="c4e2a-105">筆墨儲存和擷取</span><span class="sxs-lookup"><span data-stu-id="c4e2a-105">Ink Storage and Retrieval</span></span>  
 <span data-ttu-id="c4e2a-106">本節討論如何儲存和擷取筆墨[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]平台。</span><span class="sxs-lookup"><span data-stu-id="c4e2a-106">This section discusses how to store and retrieve ink in the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] platform.</span></span>  
  
 <span data-ttu-id="c4e2a-107">下列範例會顯示 [儲存檔案] 對話方塊中，並將儲存筆墨的按鈕 click 事件處理常式<xref:System.Windows.Controls.InkCanvas>外的檔案。</span><span class="sxs-lookup"><span data-stu-id="c4e2a-107">The following example implements a button-click event handler that presents the user with a File Save dialog box and saves the ink from an <xref:System.Windows.Controls.InkCanvas> out to a file.</span></span>  
  
 [!code-csharp[DigitalInkTopics#12](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#12)]
 [!code-vb[DigitalInkTopics#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#12)]  
  
 <span data-ttu-id="c4e2a-108">下列範例會顯示 [開啟舊檔] 對話方塊，並從檔案讀取筆墨的按鈕 click 事件處理常式<xref:System.Windows.Controls.InkCanvas>項目。</span><span class="sxs-lookup"><span data-stu-id="c4e2a-108">The following example implements a button-click event handler that presents the user with a File Open dialog box and reads ink from the file into an <xref:System.Windows.Controls.InkCanvas> element.</span></span>  
  
 [!code-csharp[DigitalInkTopics#13](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#13)]
 [!code-vb[DigitalInkTopics#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="c4e2a-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4e2a-109">See also</span></span>
- <xref:System.Windows.Controls.InkCanvas>
- [<span data-ttu-id="c4e2a-110">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="c4e2a-110">Windows Presentation Foundation</span></span>](../index.md)
