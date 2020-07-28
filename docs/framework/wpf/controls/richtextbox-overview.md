---
title: RichTextBox 概觀
description: '瞭解 Windows Presentation Foundation RichTextBox 控制項如何讓使用者顯示或編輯文字、影像和資料表這類內容。 請參閱 XAML 和 c # 範例。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], RichTextBox
- RichTextBox control [WPF], about RichTextBox control
ms.assetid: c94548b2-c1e9-4b62-b10c-dd8740eb23d8
ms.openlocfilehash: 525e27f9602136c68f160c738fd1c92ea761536c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166240"
---
# <a name="richtextbox-overview"></a><span data-ttu-id="ed31c-104">RichTextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="ed31c-104">RichTextBox Overview</span></span>

<span data-ttu-id="ed31c-105"><xref:System.Windows.Controls.RichTextBox>控制項可讓您顯示或編輯流程內容，包括段落、影像、資料表等等。</span><span class="sxs-lookup"><span data-stu-id="ed31c-105">The <xref:System.Windows.Controls.RichTextBox> control enables you to display or edit flow content including paragraphs, images, tables, and more.</span></span> <span data-ttu-id="ed31c-106">本主題介紹 <xref:System.Windows.Controls.TextBox> 類別，並提供如何在和 c # 中使用它的範例 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ed31c-106">This topic introduces the <xref:System.Windows.Controls.TextBox> class and provides examples of how to use it in both [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] and C#.</span></span>

<a name="textbox_or_richtextbox"></a>

## <a name="textbox-or-richtextbox"></a><span data-ttu-id="ed31c-107">TextBox 或 RichTextBox？</span><span class="sxs-lookup"><span data-stu-id="ed31c-107">TextBox or RichTextBox?</span></span>

<span data-ttu-id="ed31c-108"><xref:System.Windows.Controls.RichTextBox>和都 <xref:System.Windows.Controls.TextBox> 可讓使用者編輯文字，但在不同的案例中會使用這兩個控制項。</span><span class="sxs-lookup"><span data-stu-id="ed31c-108">Both <xref:System.Windows.Controls.RichTextBox> and <xref:System.Windows.Controls.TextBox> allow users to edit text, however, the two controls are used in different scenarios.</span></span> <span data-ttu-id="ed31c-109"><xref:System.Windows.Controls.RichTextBox>當使用者需要編輯格式化的文字、影像、資料表或其他豐富內容時，是較好的選擇。</span><span class="sxs-lookup"><span data-stu-id="ed31c-109">A <xref:System.Windows.Controls.RichTextBox> is a better choice when it is necessary for the user to edit formatted text, images, tables, or other rich content.</span></span> <span data-ttu-id="ed31c-110">例如，編輯需要格式化、影像等的檔、發行項或 blog，最好是使用來完成 <xref:System.Windows.Controls.RichTextBox> 。</span><span class="sxs-lookup"><span data-stu-id="ed31c-110">For example, editing a document, article, or blog that requires formatting, images, etc is best accomplished using a <xref:System.Windows.Controls.RichTextBox>.</span></span> <span data-ttu-id="ed31c-111">A <xref:System.Windows.Controls.TextBox> 需要較少的系統資源 <xref:System.Windows.Controls.RichTextBox> ，而且在只需要編輯純文字（也就是表單的使用方式）時非常理想。</span><span class="sxs-lookup"><span data-stu-id="ed31c-111">A <xref:System.Windows.Controls.TextBox> requires less system resources then a <xref:System.Windows.Controls.RichTextBox> and it is ideal when only plain text needs to be edited (i.e. usage in forms).</span></span> <span data-ttu-id="ed31c-112">如需的詳細資訊，請參閱[TextBox 總覽](textbox-overview.md) <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="ed31c-112">See [TextBox Overview](textbox-overview.md) for more information on <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="ed31c-113">下表摘要說明和的主要功能 <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox> 。</span><span class="sxs-lookup"><span data-stu-id="ed31c-113">The table below summarizes the main features of <xref:System.Windows.Controls.TextBox> and <xref:System.Windows.Controls.RichTextBox>.</span></span>

|<span data-ttu-id="ed31c-114">控制</span><span class="sxs-lookup"><span data-stu-id="ed31c-114">Control</span></span>|<span data-ttu-id="ed31c-115">即時拼字檢查</span><span class="sxs-lookup"><span data-stu-id="ed31c-115">Real-time Spellchecking</span></span>|<span data-ttu-id="ed31c-116">操作功能表</span><span class="sxs-lookup"><span data-stu-id="ed31c-116">Context Menu</span></span>|<span data-ttu-id="ed31c-117">格式化命令，例如 <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> （Ctr + B）</span><span class="sxs-lookup"><span data-stu-id="ed31c-117">Formatting commands like <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (Ctr+B)</span></span>|<span data-ttu-id="ed31c-118"><xref:System.Windows.Documents.FlowDocument>影像、段落、資料表等內容</span><span class="sxs-lookup"><span data-stu-id="ed31c-118"><xref:System.Windows.Documents.FlowDocument> content like images, paragraphs, tables, etc.</span></span>|
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|<xref:System.Windows.Controls.TextBox>|<span data-ttu-id="ed31c-119">是</span><span class="sxs-lookup"><span data-stu-id="ed31c-119">Yes</span></span>|<span data-ttu-id="ed31c-120">是</span><span class="sxs-lookup"><span data-stu-id="ed31c-120">Yes</span></span>|<span data-ttu-id="ed31c-121">否</span><span class="sxs-lookup"><span data-stu-id="ed31c-121">No</span></span>|<span data-ttu-id="ed31c-122">不會。</span><span class="sxs-lookup"><span data-stu-id="ed31c-122">No.</span></span>|
|<xref:System.Windows.Controls.RichTextBox>|<span data-ttu-id="ed31c-123">是</span><span class="sxs-lookup"><span data-stu-id="ed31c-123">Yes</span></span>|<span data-ttu-id="ed31c-124">是</span><span class="sxs-lookup"><span data-stu-id="ed31c-124">Yes</span></span>|<span data-ttu-id="ed31c-125">是</span><span class="sxs-lookup"><span data-stu-id="ed31c-125">Yes</span></span>|<span data-ttu-id="ed31c-126">是</span><span class="sxs-lookup"><span data-stu-id="ed31c-126">Yes</span></span>|

> [!NOTE]
> <span data-ttu-id="ed31c-127">雖然不 <xref:System.Windows.Controls.TextBox> 支援格式化相關 <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> 的命令（如（Ctr + B）），但這兩個控制項都支援許多基本命令，例如 <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A> 。</span><span class="sxs-lookup"><span data-stu-id="ed31c-127">Although <xref:System.Windows.Controls.TextBox> does not support formatting related commands like <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (Ctr+B), many basic commands are supported by both controls such as <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>.</span></span>

<span data-ttu-id="ed31c-128">稍後會更詳細說明上表中的功能。</span><span class="sxs-lookup"><span data-stu-id="ed31c-128">The features from the table above are covered in more detail later.</span></span>

<a name="creating_a_richtextbox"></a>

## <a name="creating-a-richtextbox"></a><span data-ttu-id="ed31c-129">建立 RichTextBox</span><span class="sxs-lookup"><span data-stu-id="ed31c-129">Creating a RichTextBox</span></span>

<span data-ttu-id="ed31c-130">下列程式碼示範如何建立 <xref:System.Windows.Controls.RichTextBox> 使用者可以在中編輯豐富內容的。</span><span class="sxs-lookup"><span data-stu-id="ed31c-130">The code below shows how to create a <xref:System.Windows.Controls.RichTextBox> that a user can edit rich content in.</span></span>

[!code-xaml[RichTextBoxMiscSnippets_snip#BasicRichTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/BasicRichTextBoxExample.xaml#basicrichtextboxexamplewholepage)]

<span data-ttu-id="ed31c-131">具體而言，在中編輯的內容 <xref:System.Windows.Controls.RichTextBox> 是「流動內容」。</span><span class="sxs-lookup"><span data-stu-id="ed31c-131">Specifically, the content edited in a <xref:System.Windows.Controls.RichTextBox> is flow content.</span></span> <span data-ttu-id="ed31c-132">非固定格式內容可以包含許多型別的元素，包括格式化文字、影像、清單及表格。</span><span class="sxs-lookup"><span data-stu-id="ed31c-132">Flow content can contain many types of elements including formatted text, images, lists, and tables.</span></span> <span data-ttu-id="ed31c-133">如需有關非固定格式文件的深入資訊，請參閱[非固定格式文件概觀](../advanced/flow-document-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="ed31c-133">See [Flow Document Overview](../advanced/flow-document-overview.md) for in depth information on flow documents.</span></span> <span data-ttu-id="ed31c-134">為了包含非固定格式內容，會 <xref:System.Windows.Controls.RichTextBox> 主控 <xref:System.Windows.Documents.FlowDocument> 物件，而後者又包含可編輯的內容。</span><span class="sxs-lookup"><span data-stu-id="ed31c-134">In order to contain flow content, a <xref:System.Windows.Controls.RichTextBox> hosts a <xref:System.Windows.Documents.FlowDocument> object which in turn contains the editable content.</span></span> <span data-ttu-id="ed31c-135">為了示範中的流程內容 <xref:System.Windows.Controls.RichTextBox> ，下列程式碼顯示如何 <xref:System.Windows.Controls.RichTextBox> 使用段落和一些粗體文字來建立。</span><span class="sxs-lookup"><span data-stu-id="ed31c-135">To demonstrate flow content in a <xref:System.Windows.Controls.RichTextBox>, the following code shows how to create a <xref:System.Windows.Controls.RichTextBox> with a paragraph and some bolded text.</span></span>

[!code-xaml[RichTextBoxMiscSnippets_snip#RichTextBoxWithContentExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/RichTextBoxWithContentExample.xaml#richtextboxwithcontentexamplewholepage)]

[!code-csharp[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/CSharp/BasicRichTextBoxWithContentExample.cs#basicrichtextboxwithcontentcodeonlyexample)]
[!code-vb[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/visualbasic/basicrichtextboxwithcontentexample.vb#basicrichtextboxwithcontentcodeonlyexample)]

<span data-ttu-id="ed31c-136">下圖顯示此範例的轉譯方式。</span><span class="sxs-lookup"><span data-stu-id="ed31c-136">The following illustration shows how this sample renders.</span></span>

<span data-ttu-id="ed31c-137">![具有內容的 RichTextBox](./media/editing-richtextbox-with-content.png "Editing_RichTextBox_with_Content")</span><span class="sxs-lookup"><span data-stu-id="ed31c-137">![RichTextBox with content](./media/editing-richtextbox-with-content.png "Editing_RichTextBox_with_Content")</span></span>

<span data-ttu-id="ed31c-138">和之類 <xref:System.Windows.Documents.Paragraph> <xref:System.Windows.Documents.Bold> 的元素會決定中的內容如何 <xref:System.Windows.Controls.RichTextBox> 出現。</span><span class="sxs-lookup"><span data-stu-id="ed31c-138">Elements like <xref:System.Windows.Documents.Paragraph> and <xref:System.Windows.Documents.Bold> determine how the content inside a <xref:System.Windows.Controls.RichTextBox> appears.</span></span> <span data-ttu-id="ed31c-139">當使用者編輯 <xref:System.Windows.Controls.RichTextBox> 內容時，會變更此流程內容。</span><span class="sxs-lookup"><span data-stu-id="ed31c-139">As a user edits <xref:System.Windows.Controls.RichTextBox> content, they change this flow content.</span></span> <span data-ttu-id="ed31c-140">若要深入了解非固定格式內容的功能及如何與其搭配運作，請參閱[非固定格式文件概觀](../advanced/flow-document-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="ed31c-140">To learn more about the features of flow content and how to work with it, see [Flow Document Overview](../advanced/flow-document-overview.md).</span></span>

> [!NOTE]
> <span data-ttu-id="ed31c-141">內的 <xref:System.Windows.Controls.RichTextBox> 非固定格式內容，其行為與其他控制項中所包含的流程內容完全相同。</span><span class="sxs-lookup"><span data-stu-id="ed31c-141">Flow content inside a <xref:System.Windows.Controls.RichTextBox> does not behave exactly like flow content contained in other controls.</span></span> <span data-ttu-id="ed31c-142">例如，中沒有任何資料行， <xref:System.Windows.Controls.RichTextBox> 因此不會自動調整大小行為。</span><span class="sxs-lookup"><span data-stu-id="ed31c-142">For example, there are no columns in a <xref:System.Windows.Controls.RichTextBox> and hence no automatic resizing behavior.</span></span> <span data-ttu-id="ed31c-143">此外，內建功能（例如搜尋、視圖模式、頁面流覽和縮放）無法在中使用 <xref:System.Windows.Controls.RichTextBox> 。</span><span class="sxs-lookup"><span data-stu-id="ed31c-143">Also, built in features like search, viewing mode, page navigation, and zoom are not available within a <xref:System.Windows.Controls.RichTextBox>.</span></span>

<a name="realtime_spellechecking"></a>

## <a name="real-time-spell-checking"></a><span data-ttu-id="ed31c-144">即時拼字檢查</span><span class="sxs-lookup"><span data-stu-id="ed31c-144">Real-time Spell Checking</span></span>

<span data-ttu-id="ed31c-145">您可以在或中啟用即時拼寫檢查 <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox> 。</span><span class="sxs-lookup"><span data-stu-id="ed31c-145">You can enable real-time spell checking in a <xref:System.Windows.Controls.TextBox> or <xref:System.Windows.Controls.RichTextBox>.</span></span> <span data-ttu-id="ed31c-146">啟用拼字檢查時，拼錯的文字下方會出現紅色線條 (請見下圖)。</span><span class="sxs-lookup"><span data-stu-id="ed31c-146">When spellchecking is turned on, a red line appears underneath any misspelled words (see picture below).</span></span>

<span data-ttu-id="ed31c-147">![具有拼寫&#45;檢查的 Textbox](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")</span><span class="sxs-lookup"><span data-stu-id="ed31c-147">![Textbox with spell&#45;checking](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")</span></span>

<span data-ttu-id="ed31c-148">若要了解如何啟用拼字檢查，請參閱[在文字編輯控制項中啟用拼字檢查](how-to-enable-spell-checking-in-a-text-editing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="ed31c-148">See [Enable Spell Checking in a Text Editing Control](how-to-enable-spell-checking-in-a-text-editing-control.md) to learn how to enable spellchecking.</span></span>

<a name="context_menu"></a>

## <a name="context-menu"></a><span data-ttu-id="ed31c-149">操作功能表</span><span class="sxs-lookup"><span data-stu-id="ed31c-149">Context Menu</span></span>

<span data-ttu-id="ed31c-150">根據預設， <xref:System.Windows.Controls.TextBox> 和都會 <xref:System.Windows.Controls.RichTextBox> 有一個內容功能表，當使用者在控制項內按一下滑鼠右鍵時，就會出現此功能表。</span><span class="sxs-lookup"><span data-stu-id="ed31c-150">By default, both <xref:System.Windows.Controls.TextBox> and <xref:System.Windows.Controls.RichTextBox> have a context menu that appears when a user right-clicks inside the control.</span></span> <span data-ttu-id="ed31c-151">使用者可以使用此操作功能表來剪下、複製或貼上 (請見下圖)。</span><span class="sxs-lookup"><span data-stu-id="ed31c-151">The context menu allows the user to cut, copy, or paste (see illustration below).</span></span>

<span data-ttu-id="ed31c-152">![具有內容功能表的 TextBox](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_CoNtext_Menu")</span><span class="sxs-lookup"><span data-stu-id="ed31c-152">![TextBox with context menu](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")</span></span>

<span data-ttu-id="ed31c-153">您可以建立自己的自訂操作功能表來覆寫預設的操作功能表。</span><span class="sxs-lookup"><span data-stu-id="ed31c-153">You can create your own custom context menu to override the default one.</span></span> <span data-ttu-id="ed31c-154">如需詳細資訊，請參閱[在 RichTextBox 中放置自訂內容功能表](how-to-position-a-custom-context-menu-in-a-richtextbox.md)。</span><span class="sxs-lookup"><span data-stu-id="ed31c-154">See [Position a Custom Context Menu in a RichTextBox](how-to-position-a-custom-context-menu-in-a-richtextbox.md) for more information.</span></span>

<a name="detect_when_content_changes"></a>

## <a name="editing-commands"></a><span data-ttu-id="ed31c-155">編輯命令</span><span class="sxs-lookup"><span data-stu-id="ed31c-155">Editing Commands</span></span>

<span data-ttu-id="ed31c-156">編輯命令可讓使用者在內設定可編輯內容的格式 <xref:System.Windows.Controls.RichTextBox> 。</span><span class="sxs-lookup"><span data-stu-id="ed31c-156">Editing commands enable users to format editable content inside a <xref:System.Windows.Controls.RichTextBox>.</span></span> <span data-ttu-id="ed31c-157">除了基本的編輯命令之外， <xref:System.Windows.Controls.RichTextBox> 還包括不支援的格式化命令 <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="ed31c-157">Besides basic editing commands, <xref:System.Windows.Controls.RichTextBox> includes formatting commands that <xref:System.Windows.Controls.TextBox> does not support.</span></span> <span data-ttu-id="ed31c-158">例如，在中編輯時 <xref:System.Windows.Controls.RichTextBox> ，使用者可以按 Ctr + B 來切換粗體文字格式。</span><span class="sxs-lookup"><span data-stu-id="ed31c-158">For example, when editing in a <xref:System.Windows.Controls.RichTextBox>, a user could press Ctr+B to toggle bold text formatting.</span></span> <span data-ttu-id="ed31c-159"><xref:System.Windows.Documents.EditingCommands>如需可用命令的完整清單，請參閱。</span><span class="sxs-lookup"><span data-stu-id="ed31c-159">See <xref:System.Windows.Documents.EditingCommands> for a complete list of commands available.</span></span> <span data-ttu-id="ed31c-160">除了使用鍵盤快速鍵之外，您還可以將命令與其他控制項 (例如按鈕) 連接。</span><span class="sxs-lookup"><span data-stu-id="ed31c-160">In addition to using keyboard shortcuts, you can hook commands up to other controls like buttons.</span></span> <span data-ttu-id="ed31c-161">下列範例示範如何建立一個簡單的工具列，其中包含使用者可用來變更文字格式設定的按鈕。</span><span class="sxs-lookup"><span data-stu-id="ed31c-161">The following example shows how to create a simple tool bar containing buttons that the user can use to change text formatting.</span></span>

[!code-xaml[RichTextBox_InputPanel_snip#RichTextBoxWithToolBarExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_InputPanel_snip/CS/Window1.xaml#richtextboxwithtoolbarexamplewholepage)]

<span data-ttu-id="ed31c-162">下圖顯示此範例的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="ed31c-162">The following illustration shows how this sample displays.</span></span>

<span data-ttu-id="ed31c-163">![具有工具列的 RichTextBox](./media/editing-richtextbox-with-toobar.gif "Editing_RichTextBox_with_TooBar")</span><span class="sxs-lookup"><span data-stu-id="ed31c-163">![RichTextBox with ToolBar](./media/editing-richtextbox-with-toobar.gif "Editing_RichTextBox_with_TooBar")</span></span>

<a name="editing_commands"></a>

## <a name="detect-when-content-changes"></a><span data-ttu-id="ed31c-164">偵測內容變更</span><span class="sxs-lookup"><span data-stu-id="ed31c-164">Detect when Content Changes</span></span>

<span data-ttu-id="ed31c-165">通常 <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> 應該使用事件來偵測中的文字， <xref:System.Windows.Controls.TextBox> 或 <xref:System.Windows.Controls.RichTextBox> 變更，而不是 <xref:System.Windows.UIElement.KeyDown> 您預期的方式。</span><span class="sxs-lookup"><span data-stu-id="ed31c-165">Usually the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event should be used to detect whenever the text in a <xref:System.Windows.Controls.TextBox> or <xref:System.Windows.Controls.RichTextBox> changes rather then <xref:System.Windows.UIElement.KeyDown> as you might expect.</span></span> <span data-ttu-id="ed31c-166">如需範例，請參閱[偵測 TextBox 中的文字變更](how-to-detect-when-text-in-a-textbox-has-changed.md)。</span><span class="sxs-lookup"><span data-stu-id="ed31c-166">See [Detect When Text in a TextBox Has Changed](how-to-detect-when-text-in-a-textbox-has-changed.md) for an example.</span></span>

<a name="save_load_and_print_richtextbox_content"></a>

## <a name="save-load-and-print-richtextbox-content"></a><span data-ttu-id="ed31c-167">儲存、載入和列印 RichTextBox 內容</span><span class="sxs-lookup"><span data-stu-id="ed31c-167">Save, Load, and Print RichTextBox Content</span></span>

<span data-ttu-id="ed31c-168">下列範例示範如何將的內容儲存至檔案 <xref:System.Windows.Controls.RichTextBox> 、將該內容載入回 <xref:System.Windows.Controls.RichTextBox> ，並列印內容。</span><span class="sxs-lookup"><span data-stu-id="ed31c-168">The following example shows how to save content of a <xref:System.Windows.Controls.RichTextBox> to a file, load that content back into the <xref:System.Windows.Controls.RichTextBox>, and print the contents.</span></span> <span data-ttu-id="ed31c-169">以下是此範例的標記。</span><span class="sxs-lookup"><span data-stu-id="ed31c-169">Below is the markup for the example.</span></span>

[!code-xaml[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml#saveloadprintrtbexamplewholepage)]

<span data-ttu-id="ed31c-170">以下是此範例的程式碼後置。</span><span class="sxs-lookup"><span data-stu-id="ed31c-170">Below is the code behind for the example.</span></span>

[!code-csharp[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml.cs#saveloadprintrtbcodeexamplewholepage)]
[!code-vb[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/SaveLoadPrintRTB.xaml.vb#saveloadprintrtbcodeexamplewholepage)]

## <a name="see-also"></a><span data-ttu-id="ed31c-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed31c-171">See also</span></span>

- [<span data-ttu-id="ed31c-172">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="ed31c-172">How-to Topics</span></span>](richtextbox-how-to-topics.md)
- [<span data-ttu-id="ed31c-173">TextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="ed31c-173">TextBox Overview</span></span>](textbox-overview.md)
