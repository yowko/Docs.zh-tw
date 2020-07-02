---
ms.openlocfilehash: 2aa6603e2ed77ffa94fbc6325cd5db50985bda6a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620079"
---
### <a name="previewlostkeyboardfocus-is-called-repeatedly-if-its-handler-shows-a-windows-forms-message-box"></a><span data-ttu-id="af828-101">如果其處理常式顯示 Windows Forms 訊息方塊，則會重複呼叫 PreviewLostKeyboardFocus</span><span class="sxs-lookup"><span data-stu-id="af828-101">PreviewLostKeyboardFocus is called repeatedly if its handler shows a Windows Forms message box</span></span>

#### <a name="details"></a><span data-ttu-id="af828-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="af828-102">Details</span></span>

<span data-ttu-id="af828-103">從 .NET Framework 4.5 開始，從 <xref:System.Windows.UIElement.PreviewLostKeyboardFocus> 處理常式呼叫 <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> 會使處理常式在關閉訊息方塊時重新引發，而可能產生無限的訊息方塊迴圈。</span><span class="sxs-lookup"><span data-stu-id="af828-103">Beginning in the .NET Framework 4.5, calling <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> from a <xref:System.Windows.UIElement.PreviewLostKeyboardFocus> handler will cause the handler to re-fire when the message box is closed, potentially resulting in an infinite loop of message boxes.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="af828-104">建議</span><span class="sxs-lookup"><span data-stu-id="af828-104">Suggestion</span></span>

<span data-ttu-id="af828-105">此問題有兩個解決方法：</span><span class="sxs-lookup"><span data-stu-id="af828-105">There are two options to work around this issue:</span></span><ol><li><span data-ttu-id="af828-106">藉由呼叫 <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType> (而不是 <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType>) 來避免此問題。</span><span class="sxs-lookup"><span data-stu-id="af828-106">It may be avoided by calling <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType> instead of <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType>.</span></span></li><li><span data-ttu-id="af828-107">藉由從 <xref:System.Windows.UIElement.LostKeyboardFocus> 事件處理常式 (相對於 <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=fullName> 事件處理常式) 顯示訊息方塊來避免此問題。</span><span class="sxs-lookup"><span data-stu-id="af828-107">It may be avoided by showing the message box from a <xref:System.Windows.UIElement.LostKeyboardFocus> event handler (as opposed to a <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=fullName> event handler).</span></span></li></ol>

| <span data-ttu-id="af828-108">名稱</span><span class="sxs-lookup"><span data-stu-id="af828-108">Name</span></span>    | <span data-ttu-id="af828-109">值</span><span class="sxs-lookup"><span data-stu-id="af828-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="af828-110">影響範圍</span><span class="sxs-lookup"><span data-stu-id="af828-110">Scope</span></span>   |<span data-ttu-id="af828-111">Edge</span><span class="sxs-lookup"><span data-stu-id="af828-111">Edge</span></span>|
|<span data-ttu-id="af828-112">版本</span><span class="sxs-lookup"><span data-stu-id="af828-112">Version</span></span>|<span data-ttu-id="af828-113">4.5</span><span class="sxs-lookup"><span data-stu-id="af828-113">4.5</span></span>|
|<span data-ttu-id="af828-114">類型</span><span class="sxs-lookup"><span data-stu-id="af828-114">Type</span></span>|<span data-ttu-id="af828-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="af828-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="af828-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="af828-116">Affected APIs</span></span>

-<xref:System.Windows.ContentElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.IInputElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement3D.PreviewLostKeyboardFocus?displayProperty=nameWithType></li></ul>|
