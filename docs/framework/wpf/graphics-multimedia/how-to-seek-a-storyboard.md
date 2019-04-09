---
title: HOW TO：尋找分鏡腳本
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], seeking
- seeking Storyboards [WPF]
ms.assetid: 887bb39a-0c2a-4ae8-956d-1d9f6f8ebbfc
ms.openlocfilehash: a57272c17a5bc6f5baaa21fb77233fc5693d1914
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131660"
---
# <a name="how-to-seek-a-storyboard"></a><span data-ttu-id="8517a-102">HOW TO：尋找分鏡腳本</span><span class="sxs-lookup"><span data-stu-id="8517a-102">How to: Seek a Storyboard</span></span>
<span data-ttu-id="8517a-103">下列範例示範如何使用<xref:System.Windows.Media.Animation.Storyboard.Seek%2A>方法的<xref:System.Windows.Media.Animation.Storyboard>跳到分鏡腳本動畫中的任何位置。</span><span class="sxs-lookup"><span data-stu-id="8517a-103">The following example shows how to use the <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> method of a <xref:System.Windows.Media.Animation.Storyboard> to jump to any position in a storyboard animation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8517a-104">範例</span><span class="sxs-lookup"><span data-stu-id="8517a-104">Example</span></span>  
 <span data-ttu-id="8517a-105">以下是此範例的 XAML 標記。</span><span class="sxs-lookup"><span data-stu-id="8517a-105">Below is the XAML markup for the sample.</span></span>  
  
 [!code-xaml[SeekStoryboard_snip#SeekStoryboardExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardExample.xaml#seekstoryboardexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="8517a-106">範例</span><span class="sxs-lookup"><span data-stu-id="8517a-106">Example</span></span>  
 <span data-ttu-id="8517a-107">以下是搭配上述 XAML 程式碼使用的程式碼。</span><span class="sxs-lookup"><span data-stu-id="8517a-107">Below is the code used with the XAML code above.</span></span>  
  
 [!code-csharp[SeekStoryboard_snip#SeekStoryboardCodeBehindExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardExample.xaml.cs#seekstoryboardcodebehindexamplewholepage)]
 [!code-vb[SeekStoryboard_snip#SeekStoryboardCodeBehindExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SeekStoryboard_snip/VisualBasic/SeekStoryboardExample.xaml.vb#seekstoryboardcodebehindexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="8517a-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8517a-108">See also</span></span>

- [<span data-ttu-id="8517a-109">同步搜尋分鏡腳本</span><span class="sxs-lookup"><span data-stu-id="8517a-109">Seek a Storyboard Synchronously</span></span>](how-to-seek-a-storyboard-synchronously.md)
