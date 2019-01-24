---
title: HOW TO：使用內容功能表的拼字檢查
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- enabling spell checking in a text box [WPF]
- reenabling spell checking in a text box [WPF]
- spell checking with a context menu [WPF]
ms.assetid: 61f69a20-2ff3-4056-9060-e32f4483ec5e
ms.openlocfilehash: 2b6790fd4d5d2e322a46bd98ed19e7b88c4923c4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713112"
---
# <a name="how-to-use-spell-checking-with-a-context-menu"></a><span data-ttu-id="9fb8d-102">HOW TO：使用內容功能表的拼字檢查</span><span class="sxs-lookup"><span data-stu-id="9fb8d-102">How to: Use Spell Checking with a Context Menu</span></span>
<span data-ttu-id="9fb8d-103">根據預設，當您啟用編輯控制項中的拼字檢查像是<xref:System.Windows.Controls.TextBox>或<xref:System.Windows.Controls.RichTextBox>，您取得操作功能表中的拼字檢查的選項。</span><span class="sxs-lookup"><span data-stu-id="9fb8d-103">By default, when you enable spell checking in an editing control like <xref:System.Windows.Controls.TextBox> or <xref:System.Windows.Controls.RichTextBox>, you get spell-checking choices in the context menu.</span></span> <span data-ttu-id="9fb8d-104">比方說，當使用者以滑鼠右鍵按一下拼錯的字，他們會取得一組拼字建議或選擇**全部略過**。</span><span class="sxs-lookup"><span data-stu-id="9fb8d-104">For example, when users right-click a misspelled word, they get a set of spelling suggestions or the option to **Ignore All**.</span></span> <span data-ttu-id="9fb8d-105">不過，當您覆寫預設的內容功能表，以您自己的自訂內容功能表，這項功能將會遺失，而且您需要撰寫程式碼，以重新啟用快顯功能表的拼字檢查功能。</span><span class="sxs-lookup"><span data-stu-id="9fb8d-105">However, when you override the default context menu with your own custom context menu, this functionality is lost, and you need to write code to reenable the spell-checking feature in the context menu.</span></span> <span data-ttu-id="9fb8d-106">下列範例示範如何在啟用此<xref:System.Windows.Controls.TextBox>。</span><span class="sxs-lookup"><span data-stu-id="9fb8d-106">The following example shows how to enable this on a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9fb8d-107">範例</span><span class="sxs-lookup"><span data-stu-id="9fb8d-107">Example</span></span>  
 <span data-ttu-id="9fb8d-108">下列範例所示[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]來建立<xref:System.Windows.Controls.TextBox>與用來實作快顯功能表的某些事件。</span><span class="sxs-lookup"><span data-stu-id="9fb8d-108">The following example shows the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that creates a <xref:System.Windows.Controls.TextBox> with some events that are used to implement the context menu.</span></span>  
  
 [!code-xaml[TextBoxMiscSnippets_snip#SpellerCustomContextMenuExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml#spellercustomcontextmenuexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="9fb8d-109">範例</span><span class="sxs-lookup"><span data-stu-id="9fb8d-109">Example</span></span>  
 <span data-ttu-id="9fb8d-110">下列範例顯示實作快顯功能表的程式碼。</span><span class="sxs-lookup"><span data-stu-id="9fb8d-110">The following example shows the code that implements the context menu.</span></span>  
  
 [!code-csharp[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml.cs#spellercustomcontextmenucodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/speller_custom_context_menu.xaml.vb#spellercustomcontextmenucodeexamplewholepage)]  
  
 <span data-ttu-id="9fb8d-111">用來執行此程式碼<xref:System.Windows.Controls.RichTextBox>類似。</span><span class="sxs-lookup"><span data-stu-id="9fb8d-111">The code used for doing this with a <xref:System.Windows.Controls.RichTextBox> is similar.</span></span> <span data-ttu-id="9fb8d-112">傳遞至參數中的主要差異在於`GetSpellingError`方法。</span><span class="sxs-lookup"><span data-stu-id="9fb8d-112">The main difference is in the parameter passed to the `GetSpellingError` method.</span></span> <span data-ttu-id="9fb8d-113">針對<xref:System.Windows.Controls.TextBox>，將插入號位置的整數索引：</span><span class="sxs-lookup"><span data-stu-id="9fb8d-113">For a <xref:System.Windows.Controls.TextBox>, pass the integer index of the caret position:</span></span>  
  
 `spellingError = myTextBox.GetSpellingError(caretIndex);`  
  
 <span data-ttu-id="9fb8d-114">針對<xref:System.Windows.Controls.RichTextBox>，傳遞<xref:System.Windows.Documents.TextPointer>指定插入號位置：</span><span class="sxs-lookup"><span data-stu-id="9fb8d-114">For a <xref:System.Windows.Controls.RichTextBox>, pass the <xref:System.Windows.Documents.TextPointer> that specifies the caret position:</span></span>  
  
 `spellingError = myRichTextBox.GetSpellingError(myRichTextBox.CaretPosition);`  
  
## <a name="see-also"></a><span data-ttu-id="9fb8d-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9fb8d-115">See also</span></span>
- [<span data-ttu-id="9fb8d-116">TextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="9fb8d-116">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)
- [<span data-ttu-id="9fb8d-117">RichTextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="9fb8d-117">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
- [<span data-ttu-id="9fb8d-118">在文字編輯控制項中啟用拼字檢查</span><span class="sxs-lookup"><span data-stu-id="9fb8d-118">Enable Spell Checking in a Text Editing Control</span></span>](../../../../docs/framework/wpf/controls/how-to-enable-spell-checking-in-a-text-editing-control.md)
- [<span data-ttu-id="9fb8d-119">在文字方塊使用自訂內容功能表</span><span class="sxs-lookup"><span data-stu-id="9fb8d-119">Use a Custom Context Menu with a TextBox</span></span>](../../../../docs/framework/wpf/controls/how-to-use-a-custom-context-menu-with-a-textbox.md)
