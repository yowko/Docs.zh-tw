---
title: "如何：呈現視覺化樣式項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- visual themes [Windows Forms], applying to elements of Windows Forms applications
- professional appearance [Windows Forms], applying to elements of Windows Forms applications
- visual styles [Windows Forms], rendering Windows Forms controls
ms.assetid: a207781b-1baa-4ce9-b788-1e951bd4b5df
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b96f9e6cc54e028e94cc7ae377012ac4f1328bb0
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-render-a-visual-style-element"></a><span data-ttu-id="d73aa-102">如何：呈現視覺化樣式項目</span><span class="sxs-lookup"><span data-stu-id="d73aa-102">How to: Render a Visual Style Element</span></span>
<span data-ttu-id="d73aa-103"><xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType>命名空間會公開<xref:System.Windows.Forms.VisualStyles.VisualStyleElement>物件，表示 Windows 使用者介面 (UI) 項目支援視覺化樣式。</span><span class="sxs-lookup"><span data-stu-id="d73aa-103">The <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> namespace exposes <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> objects that represent the Windows user interface (UI) elements supported by visual styles.</span></span> <span data-ttu-id="d73aa-104">本主題示範如何使用<xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>類別來呈現<xref:System.Windows.Forms.VisualStyles.VisualStyleElement>表示**登出**和**關機**[開始] 功能表按鈕。</span><span class="sxs-lookup"><span data-stu-id="d73aa-104">This topic demonstrates how to use the <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> class to render the <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> that represents the **Log Off** and **Shut Down** buttons of the Start menu.</span></span>  
  
### <a name="to-render-a-visual-style-element"></a><span data-ttu-id="d73aa-105">要呈現視覺化樣式項目</span><span class="sxs-lookup"><span data-stu-id="d73aa-105">To render a visual style element</span></span>  
  
1.  <span data-ttu-id="d73aa-106">建立<xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>並將它設定為您想要繪製的項目。</span><span class="sxs-lookup"><span data-stu-id="d73aa-106">Create a <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> and set it to the element you want to draw.</span></span> <span data-ttu-id="d73aa-107">請注意使用<xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A?displayProperty=nameWithType>屬性和<xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.IsElementDefined%2A?displayProperty=nameWithType>方法;<xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor%2A>建構函式將會擲回例外狀況，如果已停用視覺化樣式，或項目就是未定義。</span><span class="sxs-lookup"><span data-stu-id="d73aa-107">Note the use of the <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A?displayProperty=nameWithType> property and the <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.IsElementDefined%2A?displayProperty=nameWithType> method; the <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor%2A> constructor will throw an exception if visual styles are disabled or an element is undefined.</span></span>  
  
     [!code-cpp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/cpp/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/VB/form1.vb#4)]  
  
2.  <span data-ttu-id="d73aa-108">呼叫<xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.DrawBackground%2A>方法來呈現項目<xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>目前表示。</span><span class="sxs-lookup"><span data-stu-id="d73aa-108">Call the <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.DrawBackground%2A> method to render the element that the <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> currently represents.</span></span>  
  
     [!code-cpp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/cpp/form1.cpp#6)]
     [!code-csharp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/VB/form1.vb#6)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d73aa-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="d73aa-109">Compiling the Code</span></span>  
 <span data-ttu-id="d73aa-110">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="d73aa-110">This example requires:</span></span>  
  
-   <span data-ttu-id="d73aa-111">自訂控制項衍生自<xref:System.Windows.Forms.Control>類別。</span><span class="sxs-lookup"><span data-stu-id="d73aa-111">A custom control derived from the <xref:System.Windows.Forms.Control> class.</span></span>  
  
-   <span data-ttu-id="d73aa-112">A<xref:System.Windows.Forms.Form>裝載自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="d73aa-112">A <xref:System.Windows.Forms.Form> that hosts the custom control.</span></span>  
  
-   <span data-ttu-id="d73aa-113">若要參考<xref:System?displayProperty=nameWithType>， <xref:System.Drawing?displayProperty=nameWithType>， <xref:System.Windows.Forms?displayProperty=nameWithType>，和<xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType>命名空間。</span><span class="sxs-lookup"><span data-stu-id="d73aa-113">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d73aa-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d73aa-114">See Also</span></span>  
 [<span data-ttu-id="d73aa-115">使用視覺化樣式呈現控制項</span><span class="sxs-lookup"><span data-stu-id="d73aa-115">Rendering Controls with Visual Styles</span></span>](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)
