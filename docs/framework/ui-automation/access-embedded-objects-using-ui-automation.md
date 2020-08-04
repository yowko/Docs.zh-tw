---
title: UI 自動化存取內嵌物件
description: 請參閱如何在文字控制項內容中使用 UI 自動化來存取内嵌物件。 内嵌物件會被視為使用者介面自動化文字提供者的子系。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- embedded objects, accessing
- accessing embedded objects
- UI Automation, accessing embedded objects
ms.assetid: a5b513ec-7fa6-4460-869f-c18ff04f7cf2
ms.openlocfilehash: 031d9c90318eec59ad2b77d611e0ed0d5a3ae719
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2020
ms.locfileid: "87516966"
---
# <a name="access-embedded-objects-using-ui-automation"></a><span data-ttu-id="b8464-104">UI 自動化存取內嵌物件</span><span class="sxs-lookup"><span data-stu-id="b8464-104">Access Embedded Objects Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="b8464-105">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="b8464-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="b8464-106">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="b8464-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="b8464-107">本主題說明如何使用 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] ，以公開文字控制項內容中的內嵌物件。</span><span class="sxs-lookup"><span data-stu-id="b8464-107">This topic shows how [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] can be used to expose objects embedded within the content of a text control.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b8464-108">內嵌物件可以包含影像、超連結、按鈕、表格或 ActiveX 控制項。</span><span class="sxs-lookup"><span data-stu-id="b8464-108">Embedded objects can include images, hyperlinks, buttons, tables, or ActiveX controls.</span></span>  
  
 <span data-ttu-id="b8464-109">內嵌物件會被視為 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 文字提供者的子系。</span><span class="sxs-lookup"><span data-stu-id="b8464-109">Embedded objects are considered children of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="b8464-110">這個特性使得這些物件可以透過與其他所有 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] 項目相同的使用者介面自動化樹狀結構結構來公開。</span><span class="sxs-lookup"><span data-stu-id="b8464-110">This allows them to be exposed through the same UI Automation tree structure as all other [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elements.</span></span> <span data-ttu-id="b8464-111">功能則是透過內嵌物件控制項類型所要求的控制項模式公開 (例如，因為超連結是文字，所以支援 <xref:System.Windows.Automation.TextPattern>)。</span><span class="sxs-lookup"><span data-stu-id="b8464-111">Functionality, in turn, is exposed through the control patterns typically required by the embedded objects control type (for example, since hyperlinks are text-based they will support <xref:System.Windows.Automation.TextPattern>).</span></span>  
  
 <span data-ttu-id="b8464-112">![內嵌於文字容器中的物件。](./media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")</span><span class="sxs-lookup"><span data-stu-id="b8464-112">![Embedded objects in a text container.](./media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")</span></span>  
<span data-ttu-id="b8464-113">包含文字內容的範例檔（「您知道嗎？」...)和兩個內嵌物件（whale 的圖片和文字超連結），當做程式碼範例的目標使用。</span><span class="sxs-lookup"><span data-stu-id="b8464-113">A sample document with textual content, ("Did You Know?"…) and two embedded objects (a picture of a whale and a text hyperlink), used as a target for the code examples.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8464-114">範例</span><span class="sxs-lookup"><span data-stu-id="b8464-114">Example</span></span>  
 <span data-ttu-id="b8464-115">下列程式碼範例說明，如何從 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 文字提供者擷取內嵌物件的集合。</span><span class="sxs-lookup"><span data-stu-id="b8464-115">The following code example demonstrates how to retrieve a collection of embedded objects from within a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="b8464-116">簡介中所提供的範例文件，會傳回兩個物件 (影像項目及文字項目)。</span><span class="sxs-lookup"><span data-stu-id="b8464-116">For the sample document provided in the introduction, two objects would be returned (an image element and a text element).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b8464-117">影像項目應該要與一些描述影像的內建文字關聯，通常是在 <xref:System.Windows.Automation.AutomationElement.NameProperty> 中 (例如「藍鯨」)。</span><span class="sxs-lookup"><span data-stu-id="b8464-117">The image element should have some intrinsic text associated with it that describes the image, typically in its <xref:System.Windows.Automation.AutomationElement.NameProperty> (for example, "A blue whale.").</span></span> <span data-ttu-id="b8464-118">但是，當取得環繞影像物件的文字範圍時，文字資料流中不會傳回影像及描述文字。</span><span class="sxs-lookup"><span data-stu-id="b8464-118">However, when a text range spanning the image object is obtained, neither the image nor this descriptive text is returned in the text stream.</span></span>  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#GetChildren](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#getchildren)]
[!code-vb[FindText#GetChildren](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#getchildren)]  
  
## <a name="example"></a><span data-ttu-id="b8464-119">範例</span><span class="sxs-lookup"><span data-stu-id="b8464-119">Example</span></span>  
 <span data-ttu-id="b8464-120">下列程式碼範例說明，如何從 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 文字提供者的內嵌物件中取得文字範圍。</span><span class="sxs-lookup"><span data-stu-id="b8464-120">The following code example demonstrates how to obtain a text range from an embedded object within a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="b8464-121">擷取的文字範圍是空白範圍，起始結束點前面接的是 "…</span><span class="sxs-lookup"><span data-stu-id="b8464-121">The text range retrieved is an empty range where the starting endpoint follows "…</span></span> <span data-ttu-id="b8464-122">ocean.(空格)"，而結尾結束點的後面則是結尾點 "."，代表內嵌超連結 (如簡介中提供的影像所示)。</span><span class="sxs-lookup"><span data-stu-id="b8464-122">ocean.(space)" and the ending endpoint precedes the closing "." representing the embedded hyperlink (as shown by the image provided in the introduction).</span></span> <span data-ttu-id="b8464-123">即使這是空白範圍，但並不會被視為變質範圍，因為其擁有非零值的範圍。</span><span class="sxs-lookup"><span data-stu-id="b8464-123">Even though this is an empty range, it is not considered a degenerate range because it has a non-zero span.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b8464-124"><xref:System.Windows.Automation.TextPattern> 可以擷取文字式的內嵌物件，例如超連結，但是必須取得內嵌物件中的次要 <xref:System.Windows.Automation.TextPattern> ，才能公開其完整的功能。</span><span class="sxs-lookup"><span data-stu-id="b8464-124"><xref:System.Windows.Automation.TextPattern> can retrieve a text-based embedded object such as a hyperlink; however, a secondary <xref:System.Windows.Automation.TextPattern> will have to be obtained from the embedded object to expose its full functionality.</span></span>  
  
 [!code-csharp[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#getrangefromchild)]
 [!code-vb[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#getrangefromchild)]  
  
## <a name="see-also"></a><span data-ttu-id="b8464-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8464-125">See also</span></span>

- [<span data-ttu-id="b8464-126">UI 自動化 TextPattern 概觀</span><span class="sxs-lookup"><span data-stu-id="b8464-126">UI Automation TextPattern Overview</span></span>](ui-automation-textpattern-overview.md)
- [<span data-ttu-id="b8464-127">UI 自動化控制項模式概觀</span><span class="sxs-lookup"><span data-stu-id="b8464-127">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="b8464-128">用戶端的 UI 自動化控制項模式</span><span class="sxs-lookup"><span data-stu-id="b8464-128">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="b8464-129">使用 UI 自動化將內容加入至文字方塊</span><span class="sxs-lookup"><span data-stu-id="b8464-129">Add Content to a Text Box Using UI Automation</span></span>](add-content-to-a-text-box-using-ui-automation.md)
- [<span data-ttu-id="b8464-130">利用 UI 自動化尋找和反白顯示文字</span><span class="sxs-lookup"><span data-stu-id="b8464-130">Find and Highlight Text Using UI Automation</span></span>](find-and-highlight-text-using-ui-automation.md)
