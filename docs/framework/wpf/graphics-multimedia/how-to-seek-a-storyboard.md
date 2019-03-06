---
title: HOW TO：尋找腳本
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], seeking
- seeking Storyboards [WPF]
ms.assetid: 887bb39a-0c2a-4ae8-956d-1d9f6f8ebbfc
ms.openlocfilehash: 7553550f406cc72603aa9f65e4233a13329223a9
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354280"
---
# <a name="how-to-seek-a-storyboard"></a><span data-ttu-id="24cf9-102">HOW TO：尋找腳本</span><span class="sxs-lookup"><span data-stu-id="24cf9-102">How to: Seek a Storyboard</span></span>
<span data-ttu-id="24cf9-103">下列範例示範如何使用<xref:System.Windows.Media.Animation.Storyboard.Seek%2A>方法的<xref:System.Windows.Media.Animation.Storyboard>跳到分鏡腳本動畫中的任何位置。</span><span class="sxs-lookup"><span data-stu-id="24cf9-103">The following example shows how to use the <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> method of a <xref:System.Windows.Media.Animation.Storyboard> to jump to any position in a storyboard animation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24cf9-104">範例</span><span class="sxs-lookup"><span data-stu-id="24cf9-104">Example</span></span>  
 <span data-ttu-id="24cf9-105">以下是此範例的 XAML 標記。</span><span class="sxs-lookup"><span data-stu-id="24cf9-105">Below is the XAML markup for the sample.</span></span>  
  
 [!code-xaml[SeekStoryboard_snip#SeekStoryboardExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardExample.xaml#seekstoryboardexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="24cf9-106">範例</span><span class="sxs-lookup"><span data-stu-id="24cf9-106">Example</span></span>  
 <span data-ttu-id="24cf9-107">以下是搭配上述 XAML 程式碼使用的程式碼。</span><span class="sxs-lookup"><span data-stu-id="24cf9-107">Below is the code used with the XAML code above.</span></span>  
  
 [!code-csharp[SeekStoryboard_snip#SeekStoryboardCodeBehindExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardExample.xaml.cs#seekstoryboardcodebehindexamplewholepage)]
 [!code-vb[SeekStoryboard_snip#SeekStoryboardCodeBehindExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SeekStoryboard_snip/VisualBasic/SeekStoryboardExample.xaml.vb#seekstoryboardcodebehindexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="24cf9-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24cf9-108">See also</span></span>
- [<span data-ttu-id="24cf9-109">同步搜尋分鏡腳本</span><span class="sxs-lookup"><span data-stu-id="24cf9-109">Seek a Storyboard Synchronously</span></span>](how-to-seek-a-storyboard-synchronously.md)
