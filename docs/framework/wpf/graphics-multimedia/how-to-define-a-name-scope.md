---
title: "如何：定義名稱範圍"
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
- name scope [WPF], defining
- Storyboards [WPF], animating in procedural code
- animation [WPF], Storyboards [WPF], in procedural code
ms.assetid: 4f361925-6a08-40dc-8231-a61111c6b28b
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8d3199de53f93f07e36e7a6e0a02ed9e80b4d591
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-a-name-scope"></a><span data-ttu-id="a1b74-102">如何：定義名稱範圍</span><span class="sxs-lookup"><span data-stu-id="a1b74-102">How to: Define a Name Scope</span></span>
<span data-ttu-id="a1b74-103">若要動畫方式顯示與<xref:System.Windows.Media.Animation.Storyboard>在程式碼中，您必須建立<xref:System.Windows.NameScope>並向擁有該名稱範圍的項目中的目標物件的名稱。</span><span class="sxs-lookup"><span data-stu-id="a1b74-103">To animate with <xref:System.Windows.Media.Animation.Storyboard> in code, you must create a <xref:System.Windows.NameScope> and register the target objects' names with the element that owns that name scope.</span></span> <span data-ttu-id="a1b74-104">在下列範例中，<xref:System.Windows.NameScope>建立`myMainPanel`。</span><span class="sxs-lookup"><span data-stu-id="a1b74-104">In the following example, a <xref:System.Windows.NameScope> is created for `myMainPanel`.</span></span> <span data-ttu-id="a1b74-105">兩個按鈕，`button1`和`button2`，會加入至面板，並註冊其名稱。</span><span class="sxs-lookup"><span data-stu-id="a1b74-105">Two buttons, `button1` and `button2`, are added to the panel, and their names registered.</span></span> <span data-ttu-id="a1b74-106">數個動畫和<xref:System.Windows.Media.Animation.Storyboard>所建立。</span><span class="sxs-lookup"><span data-stu-id="a1b74-106">Several animations and a <xref:System.Windows.Media.Animation.Storyboard> are created.</span></span> <span data-ttu-id="a1b74-107">分鏡腳本<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>方法用來啟動動畫。</span><span class="sxs-lookup"><span data-stu-id="a1b74-107">The storyboard's <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method is used to start the animations.</span></span>  
  
 <span data-ttu-id="a1b74-108">因為`button1`， `button2`，和`myMainPanel`所有共用相同的名稱範圍，其中任何一個可以搭配<xref:System.Windows.Media.Animation.Storyboard><xref:System.Windows.Media.Animation.Storyboard.Begin%2A>方法啟動動畫。</span><span class="sxs-lookup"><span data-stu-id="a1b74-108">Because `button1`, `button2`, and `myMainPanel` all share the same name scope, any one of them can be used with the <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method to start the animations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1b74-109">範例</span><span class="sxs-lookup"><span data-stu-id="a1b74-109">Example</span></span>  
 [!code-csharp[StoryboardBeginAnimation_procedural_snip#NameScopeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/CSharp/ScopeExample.cs#namescopeexample)]
 [!code-vb[StoryboardBeginAnimation_procedural_snip#NameScopeExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/visualbasic/scopeexample.vb#namescopeexample)]  
  
## <a name="see-also"></a><span data-ttu-id="a1b74-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1b74-110">See Also</span></span>  
 [<span data-ttu-id="a1b74-111">使用分鏡腳本建立屬性的動畫</span><span class="sxs-lookup"><span data-stu-id="a1b74-111">Animate a Property by Using a Storyboard</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)  
 [<span data-ttu-id="a1b74-112">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="a1b74-112">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
