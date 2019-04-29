---
title: HOW TO：在 RichTextBox 中置放自訂操作功能表
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom context menus [WPF], positioning
- positioning custom context menus [WPF]
- RichTextBox control [WPF], positioning custom context menus
- context menus [WPF], positioning
ms.assetid: bf77c930-a546-4573-9a56-9af345ba189a
ms.openlocfilehash: f9407f59c3daafd09fa5b84006f33ef2f3ebd31f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770821"
---
# <a name="how-to-position-a-custom-context-menu-in-a-richtextbox"></a><span data-ttu-id="7f8d1-102">HOW TO：在 RichTextBox 中置放自訂操作功能表</span><span class="sxs-lookup"><span data-stu-id="7f8d1-102">How to: Position a Custom Context Menu in a RichTextBox</span></span>
<span data-ttu-id="7f8d1-103">此範例說明如何放置自訂操作功能表<xref:System.Windows.Controls.RichTextBox>。</span><span class="sxs-lookup"><span data-stu-id="7f8d1-103">This example shows how to position a custom context menu for a <xref:System.Windows.Controls.RichTextBox>.</span></span>  
  
 <span data-ttu-id="7f8d1-104">當您實作 **RichTextBox** 的自訂操作功能表時，需負責處理操作功能表的位置。</span><span class="sxs-lookup"><span data-stu-id="7f8d1-104">When you implement a custom context menu for a **RichTextBox**, you are responsible for handling the placement of the context menu.</span></span>  <span data-ttu-id="7f8d1-105">自訂操作功能表預設會在 **RichTextBox** 的中央開啟。</span><span class="sxs-lookup"><span data-stu-id="7f8d1-105">By default, a custom context menu is opened at the center of the **RichTextBox**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f8d1-106">範例</span><span class="sxs-lookup"><span data-stu-id="7f8d1-106">Example</span></span>  
 <span data-ttu-id="7f8d1-107">若要覆寫預設放置行為，請新增 接聽程式<xref:System.Windows.FrameworkContentElement.ContextMenuOpening>事件。</span><span class="sxs-lookup"><span data-stu-id="7f8d1-107">To override the default placement behavior, add a listener for the <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> event.</span></span>  <span data-ttu-id="7f8d1-108">下列範例顯示如何以程式設計方式執行此操作。</span><span class="sxs-lookup"><span data-stu-id="7f8d1-108">The following example shows how to do this programmatically.</span></span>  
  
 [!code-csharp[RichTextBox_ContextMenu#_AddListener](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_addlistener)]
 [!code-vb[RichTextBox_ContextMenu#_AddListener](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_addlistener)]  
  
## <a name="example"></a><span data-ttu-id="7f8d1-109">範例</span><span class="sxs-lookup"><span data-stu-id="7f8d1-109">Example</span></span>  
 <span data-ttu-id="7f8d1-110">下列範例示範實作對應<xref:System.Windows.FrameworkContentElement.ContextMenuOpening>事件接聽程式。</span><span class="sxs-lookup"><span data-stu-id="7f8d1-110">The following example shows an implementation the corresponding <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> event listener.</span></span>  
  
 [!code-csharp[RichTextBox_ContextMenu#_ListenerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_listenerbody)]
 [!code-vb[RichTextBox_ContextMenu#_ListenerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_listenerbody)]  
  
## <a name="see-also"></a><span data-ttu-id="7f8d1-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f8d1-111">See also</span></span>

- [<span data-ttu-id="7f8d1-112">RichTextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="7f8d1-112">RichTextBox Overview</span></span>](richtextbox-overview.md)
- [<span data-ttu-id="7f8d1-113">TextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="7f8d1-113">TextBox Overview</span></span>](textbox-overview.md)
