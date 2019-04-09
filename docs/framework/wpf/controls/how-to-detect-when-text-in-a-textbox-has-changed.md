---
title: HOW TO：偵測 TextBox 中的文字何時變更
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 1adadb0f071815930d34f40ddf244ffc8c19131b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091144"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a><span data-ttu-id="fb974-102">HOW TO：偵測 TextBox 中的文字何時變更</span><span class="sxs-lookup"><span data-stu-id="fb974-102">How to: Detect When Text in a TextBox Has Changed</span></span>
<span data-ttu-id="fb974-103">此範例示範使用一種方式<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>事件，以執行方法，每次中的文字<xref:System.Windows.Controls.TextBox>控制項已變更。</span><span class="sxs-lookup"><span data-stu-id="fb974-103">This example shows one way to use the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event to execute a method whenever the text in a <xref:System.Windows.Controls.TextBox> control has changed.</span></span>  
  
 <span data-ttu-id="fb974-104">中的程式碼後置類別[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，其中包含<xref:System.Windows.Controls.TextBox>控制項，您想要監視的變更，插入要每次呼叫的方法<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>引發事件。</span><span class="sxs-lookup"><span data-stu-id="fb974-104">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="fb974-105">這個方法必須不符合預期的簽章<xref:System.Windows.Controls.TextChangedEventHandler>委派。</span><span class="sxs-lookup"><span data-stu-id="fb974-105">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>  
  
 <span data-ttu-id="fb974-106">會呼叫事件處理常式時的內容<xref:System.Windows.Controls.TextBox>控制項已變更，可能是由使用者或以程式設計的方式。</span><span class="sxs-lookup"><span data-stu-id="fb974-106">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>  
  
 <span data-ttu-id="fb974-107">**注意：** 時，會引發這個事件<xref:System.Windows.Controls.TextBox>建立控制項並將其一開始填入文字。</span><span class="sxs-lookup"><span data-stu-id="fb974-107">**Note:** This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb974-108">範例</span><span class="sxs-lookup"><span data-stu-id="fb974-108">Example</span></span>  
 <span data-ttu-id="fb974-109">在  [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ，定義您<xref:System.Windows.Controls.TextBox>控制項，指定<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>屬性值符合事件處理常式方法名稱。</span><span class="sxs-lookup"><span data-stu-id="fb974-109">In the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that defines your <xref:System.Windows.Controls.TextBox> control, specify the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> attribute with a value that matches the event handler method name.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_TextChangedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]  
  
## <a name="example"></a><span data-ttu-id="fb974-110">範例</span><span class="sxs-lookup"><span data-stu-id="fb974-110">Example</span></span>  
 <span data-ttu-id="fb974-111">中的程式碼後置類別[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，其中包含<xref:System.Windows.Controls.TextBox>控制項，您想要監視的變更，插入要每次呼叫的方法<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>引發事件。</span><span class="sxs-lookup"><span data-stu-id="fb974-111">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="fb974-112">這個方法必須不符合預期的簽章<xref:System.Windows.Controls.TextChangedEventHandler>委派。</span><span class="sxs-lookup"><span data-stu-id="fb974-112">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
 [!code-vb[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]  
  
 <span data-ttu-id="fb974-113">會呼叫事件處理常式時的內容<xref:System.Windows.Controls.TextBox>控制項已變更，可能是由使用者或以程式設計的方式。</span><span class="sxs-lookup"><span data-stu-id="fb974-113">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>  
  
 <span data-ttu-id="fb974-114">**注意：** 時，會引發這個事件<xref:System.Windows.Controls.TextBox>建立控制項並將其一開始填入文字。</span><span class="sxs-lookup"><span data-stu-id="fb974-114">**Note:** This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>  
  
 <span data-ttu-id="fb974-115">註解</span><span class="sxs-lookup"><span data-stu-id="fb974-115">Comments</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb974-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb974-116">See also</span></span>

- <xref:System.Windows.Controls.TextChangedEventArgs>
- [<span data-ttu-id="fb974-117">TextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="fb974-117">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="fb974-118">RichTextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="fb974-118">RichTextBox Overview</span></span>](richtextbox-overview.md)
