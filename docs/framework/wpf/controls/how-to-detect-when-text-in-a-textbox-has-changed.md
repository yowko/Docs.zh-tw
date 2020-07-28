---
title: 如何：偵測 TextBox 中的文字何時變更
description: 瞭解當 TextBox 控制項中的文字在 Windows Presentation Foundation 應用程式中變更時，如何使用 TextChanged 事件來執行方法。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 1e054380a8c77d32e6bb4adbbcb032e531bbefd0
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166219"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a><span data-ttu-id="5d000-103">如何：偵測 TextBox 中的文字何時變更</span><span class="sxs-lookup"><span data-stu-id="5d000-103">How to: Detect When Text in a TextBox Has Changed</span></span>

<span data-ttu-id="5d000-104">這個範例示範 <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> 當控制項中的文字變更時，使用事件來執行方法的一種方式 <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="5d000-104">This example shows one way to use the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event to execute a method whenever the text in a <xref:System.Windows.Controls.TextBox> control has changed.</span></span>

<span data-ttu-id="5d000-105">在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 包含 <xref:System.Windows.Controls.TextBox> 您想要監視變更之控制項的程式碼後置類別中，插入每當引發事件時要呼叫的方法 <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> 。</span><span class="sxs-lookup"><span data-stu-id="5d000-105">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="5d000-106">這個方法的簽章必須與委派所預期的簽章相符 <xref:System.Windows.Controls.TextChangedEventHandler> 。</span><span class="sxs-lookup"><span data-stu-id="5d000-106">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>

<span data-ttu-id="5d000-107">每當 <xref:System.Windows.Controls.TextBox> 使用者或以程式設計方式變更控制項的內容時，就會呼叫事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="5d000-107">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>

> [!NOTE]
> <span data-ttu-id="5d000-108">這個事件 <xref:System.Windows.Controls.TextBox> 會在建立控制項時引發，而且一開始會以文字填入。</span><span class="sxs-lookup"><span data-stu-id="5d000-108">This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>

## <a name="example"></a><span data-ttu-id="5d000-109">範例</span><span class="sxs-lookup"><span data-stu-id="5d000-109">Example</span></span>

<span data-ttu-id="5d000-110">在 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 定義控制項的中 <xref:System.Windows.Controls.TextBox> ， <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> 使用符合事件處理常式方法名稱的值來指定屬性。</span><span class="sxs-lookup"><span data-stu-id="5d000-110">In the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that defines your <xref:System.Windows.Controls.TextBox> control, specify the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> attribute with a value that matches the event handler method name.</span></span>

[!code-xaml[TextBox_MiscCode#_TextChangedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]

## <a name="example"></a><span data-ttu-id="5d000-111">範例</span><span class="sxs-lookup"><span data-stu-id="5d000-111">Example</span></span>

<span data-ttu-id="5d000-112">在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 包含 <xref:System.Windows.Controls.TextBox> 您想要監視變更之控制項的程式碼後置類別中，插入每當引發事件時要呼叫的方法 <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> 。</span><span class="sxs-lookup"><span data-stu-id="5d000-112">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="5d000-113">這個方法的簽章必須與委派所預期的簽章相符 <xref:System.Windows.Controls.TextChangedEventHandler> 。</span><span class="sxs-lookup"><span data-stu-id="5d000-113">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>

[!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
[!code-vb[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]

<span data-ttu-id="5d000-114">每當 <xref:System.Windows.Controls.TextBox> 使用者或以程式設計方式變更控制項的內容時，就會呼叫事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="5d000-114">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>

> [!NOTE]
> <span data-ttu-id="5d000-115">這個事件 <xref:System.Windows.Controls.TextBox> 會在建立控制項時引發，而且一開始會以文字填入。</span><span class="sxs-lookup"><span data-stu-id="5d000-115">This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>

<span data-ttu-id="5d000-116">註解</span><span class="sxs-lookup"><span data-stu-id="5d000-116">Comments</span></span>

## <a name="see-also"></a><span data-ttu-id="5d000-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d000-117">See also</span></span>

- <xref:System.Windows.Controls.TextChangedEventArgs>
- [<span data-ttu-id="5d000-118">TextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="5d000-118">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="5d000-119">RichTextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="5d000-119">RichTextBox Overview</span></span>](richtextbox-overview.md)
