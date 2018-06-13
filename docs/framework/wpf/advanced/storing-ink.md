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
ms.openlocfilehash: d3d33be5e8b5cf9dd7e32a52dfc258aa934c5c11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546093"
---
# <a name="storing-ink"></a><span data-ttu-id="67845-102">儲存筆墨</span><span class="sxs-lookup"><span data-stu-id="67845-102">Storing Ink</span></span>
<span data-ttu-id="67845-103"><xref:System.Windows.Ink.StrokeCollection.Save%2A>方法來儲存筆跡為筆跡序列化格式 (ISF) 提供支援。</span><span class="sxs-lookup"><span data-stu-id="67845-103">The <xref:System.Windows.Ink.StrokeCollection.Save%2A> methods provide support for storing ink as Ink Serialized Format (ISF).</span></span> <span data-ttu-id="67845-104">建構函式<xref:System.Windows.Ink.StrokeCollection>類別提供用來讀取筆墨資料支援。</span><span class="sxs-lookup"><span data-stu-id="67845-104">Constructors for the <xref:System.Windows.Ink.StrokeCollection> class provide support for reading ink data.</span></span>  
  
## <a name="ink-storage-and-retrieval"></a><span data-ttu-id="67845-105">筆墨儲存和擷取</span><span class="sxs-lookup"><span data-stu-id="67845-105">Ink Storage and Retrieval</span></span>  
 <span data-ttu-id="67845-106">本章節將討論如何儲存和擷取中的筆墨[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]平台。</span><span class="sxs-lookup"><span data-stu-id="67845-106">This section discusses how to store and retrieve ink in the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] platform.</span></span>  
  
 <span data-ttu-id="67845-107">下列範例會實作按鈕 click 事件處理常式，對使用者顯示儲存檔案 對話方塊，並將儲存的筆墨<xref:System.Windows.Controls.InkCanvas>延展至檔案。</span><span class="sxs-lookup"><span data-stu-id="67845-107">The following example implements a button-click event handler that presents the user with a File Save dialog box and saves the ink from an <xref:System.Windows.Controls.InkCanvas> out to a file.</span></span>  
  
 [!code-csharp[DigitalInkTopics#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#12)]
 [!code-vb[DigitalInkTopics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#12)]  
  
 <span data-ttu-id="67845-108">下列範例會實作按鈕 click 事件處理常式，對使用者顯示檔案開啟對話方塊，並從檔案讀取筆墨<xref:System.Windows.Controls.InkCanvas>項目。</span><span class="sxs-lookup"><span data-stu-id="67845-108">The following example implements a button-click event handler that presents the user with a File Open dialog box and reads ink from the file into an <xref:System.Windows.Controls.InkCanvas> element.</span></span>  
  
 [!code-csharp[DigitalInkTopics#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#13)]
 [!code-vb[DigitalInkTopics#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="67845-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67845-109">See Also</span></span>  
 <xref:System.Windows.Controls.InkCanvas>  
 [<span data-ttu-id="67845-110">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="67845-110">Windows Presentation Foundation</span></span>](../../../../docs/framework/wpf/index.md)
