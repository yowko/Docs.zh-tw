---
title: HOW TO：定義名稱範圍
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- name scope [WPF], defining
- Storyboards [WPF], animating in procedural code
- animation [WPF], Storyboards [WPF], in procedural code
ms.assetid: 4f361925-6a08-40dc-8231-a61111c6b28b
ms.openlocfilehash: a03f477dd31909e8cb9dde9cd29da6f38d665758
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59086815"
---
# <a name="how-to-define-a-name-scope"></a><span data-ttu-id="8049d-102">HOW TO：定義名稱範圍</span><span class="sxs-lookup"><span data-stu-id="8049d-102">How to: Define a Name Scope</span></span>
<span data-ttu-id="8049d-103">若要以動畫顯示<xref:System.Windows.Media.Animation.Storyboard>程式碼中，您必須建立<xref:System.Windows.NameScope>並向擁有該名稱範圍的項目中的目標物件的名稱。</span><span class="sxs-lookup"><span data-stu-id="8049d-103">To animate with <xref:System.Windows.Media.Animation.Storyboard> in code, you must create a <xref:System.Windows.NameScope> and register the target objects' names with the element that owns that name scope.</span></span> <span data-ttu-id="8049d-104">在下列範例中，<xref:System.Windows.NameScope>已經為`myMainPanel`。</span><span class="sxs-lookup"><span data-stu-id="8049d-104">In the following example, a <xref:System.Windows.NameScope> is created for `myMainPanel`.</span></span> <span data-ttu-id="8049d-105">兩個按鈕`button1`和`button2`，會新增至面板，並註冊其名稱。</span><span class="sxs-lookup"><span data-stu-id="8049d-105">Two buttons, `button1` and `button2`, are added to the panel, and their names registered.</span></span> <span data-ttu-id="8049d-106">數個動畫和<xref:System.Windows.Media.Animation.Storyboard>所建立。</span><span class="sxs-lookup"><span data-stu-id="8049d-106">Several animations and a <xref:System.Windows.Media.Animation.Storyboard> are created.</span></span> <span data-ttu-id="8049d-107">分鏡腳本的<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>方法用來啟動動畫。</span><span class="sxs-lookup"><span data-stu-id="8049d-107">The storyboard's <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method is used to start the animations.</span></span>  
  
 <span data-ttu-id="8049d-108">因為`button1`， `button2`，並`myMainPanel`所有共用相同的名稱範圍，其中任何一個可以搭配<xref:System.Windows.Media.Animation.Storyboard><xref:System.Windows.Media.Animation.Storyboard.Begin%2A>方法來啟動動畫。</span><span class="sxs-lookup"><span data-stu-id="8049d-108">Because `button1`, `button2`, and `myMainPanel` all share the same name scope, any one of them can be used with the <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method to start the animations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8049d-109">範例</span><span class="sxs-lookup"><span data-stu-id="8049d-109">Example</span></span>  
 [!code-csharp[StoryboardBeginAnimation_procedural_snip#NameScopeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/CSharp/ScopeExample.cs#namescopeexample)]
 [!code-vb[StoryboardBeginAnimation_procedural_snip#NameScopeExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/visualbasic/scopeexample.vb#namescopeexample)]  
  
## <a name="see-also"></a><span data-ttu-id="8049d-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8049d-110">See also</span></span>

- [<span data-ttu-id="8049d-111">使用分鏡腳本建立屬性的動畫</span><span class="sxs-lookup"><span data-stu-id="8049d-111">Animate a Property by Using a Storyboard</span></span>](how-to-animate-a-property-by-using-a-storyboard.md)
- [<span data-ttu-id="8049d-112">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="8049d-112">Animation Overview</span></span>](animation-overview.md)
