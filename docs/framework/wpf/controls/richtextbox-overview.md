---
title: RichTextBox 概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], RichTextBox
- RichTextBox control [WPF], about RichTextBox control
ms.assetid: c94548b2-c1e9-4b62-b10c-dd8740eb23d8
ms.openlocfilehash: bfed42bcf3693ef744b3ed2b54ebe070931513a9
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855730"
---
# <a name="richtextbox-overview"></a><span data-ttu-id="95906-102">RichTextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="95906-102">RichTextBox Overview</span></span>

<span data-ttu-id="95906-103"><xref:System.Windows.Controls.RichTextBox>控制項可讓您顯示或編輯流程內容，包括段落、影像、資料表等等。</span><span class="sxs-lookup"><span data-stu-id="95906-103">The <xref:System.Windows.Controls.RichTextBox> control enables you to display or edit flow content including paragraphs, images, tables, and more.</span></span> <span data-ttu-id="95906-104">本主題介紹<xref:System.Windows.Controls.TextBox>類別，並提供如何[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]在和C#中使用它的範例。</span><span class="sxs-lookup"><span data-stu-id="95906-104">This topic introduces the <xref:System.Windows.Controls.TextBox> class and provides examples of how to use it in both [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] and C#.</span></span>

<a name="textbox_or_richtextbox"></a>

## <a name="textbox-or-richtextbox"></a><span data-ttu-id="95906-105">TextBox 或 RichTextBox？</span><span class="sxs-lookup"><span data-stu-id="95906-105">TextBox or RichTextBox?</span></span>

<span data-ttu-id="95906-106"><xref:System.Windows.Controls.RichTextBox> 和<xref:System.Windows.Controls.TextBox>都可讓使用者編輯文字，但在不同的案例中會使用這兩個控制項。</span><span class="sxs-lookup"><span data-stu-id="95906-106">Both <xref:System.Windows.Controls.RichTextBox> and <xref:System.Windows.Controls.TextBox> allow users to edit text, however, the two controls are used in different scenarios.</span></span> <span data-ttu-id="95906-107"><xref:System.Windows.Controls.RichTextBox>當使用者需要編輯格式化的文字、影像、資料表或其他豐富內容時，是較好的選擇。</span><span class="sxs-lookup"><span data-stu-id="95906-107">A <xref:System.Windows.Controls.RichTextBox> is a better choice when it is necessary for the user to edit formatted text, images, tables, or other rich content.</span></span> <span data-ttu-id="95906-108">例如，編輯需要格式化、影像等的檔、發行項或 blog，最好是使用<xref:System.Windows.Controls.RichTextBox>來完成。</span><span class="sxs-lookup"><span data-stu-id="95906-108">For example, editing a document, article, or blog that requires formatting, images, etc is best accomplished using a <xref:System.Windows.Controls.RichTextBox>.</span></span> <span data-ttu-id="95906-109">A <xref:System.Windows.Controls.TextBox>需要較少的<xref:System.Windows.Controls.RichTextBox>系統資源，而且在只需要編輯純文字（也就是表單的使用方式）時非常理想。</span><span class="sxs-lookup"><span data-stu-id="95906-109">A <xref:System.Windows.Controls.TextBox> requires less system resources then a <xref:System.Windows.Controls.RichTextBox> and it is ideal when only plain text needs to be edited (i.e. usage in forms).</span></span> <span data-ttu-id="95906-110">如需的詳細資訊<xref:System.Windows.Controls.TextBox>，請參閱[TextBox 總覽](textbox-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="95906-110">See [TextBox Overview](textbox-overview.md) for more information on <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="95906-111">下表摘要說明<xref:System.Windows.Controls.TextBox>和<xref:System.Windows.Controls.RichTextBox>的主要功能。</span><span class="sxs-lookup"><span data-stu-id="95906-111">The table below summarizes the main features of <xref:System.Windows.Controls.TextBox> and <xref:System.Windows.Controls.RichTextBox>.</span></span>

|<span data-ttu-id="95906-112">控制項</span><span class="sxs-lookup"><span data-stu-id="95906-112">Control</span></span>|<span data-ttu-id="95906-113">即時拼字檢查</span><span class="sxs-lookup"><span data-stu-id="95906-113">Real-time Spellchecking</span></span>|<span data-ttu-id="95906-114">操作功能表</span><span class="sxs-lookup"><span data-stu-id="95906-114">Context Menu</span></span>|<span data-ttu-id="95906-115">格式化命令， <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A>例如（Ctr + B）</span><span class="sxs-lookup"><span data-stu-id="95906-115">Formatting commands like <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (Ctr+B)</span></span>|<span data-ttu-id="95906-116"><xref:System.Windows.Documents.FlowDocument>影像、段落、資料表等內容</span><span class="sxs-lookup"><span data-stu-id="95906-116"><xref:System.Windows.Documents.FlowDocument> content like images, paragraphs, tables, etc.</span></span>|
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|<xref:System.Windows.Controls.TextBox>|<span data-ttu-id="95906-117">是</span><span class="sxs-lookup"><span data-stu-id="95906-117">Yes</span></span>|<span data-ttu-id="95906-118">是</span><span class="sxs-lookup"><span data-stu-id="95906-118">Yes</span></span>|<span data-ttu-id="95906-119">否</span><span class="sxs-lookup"><span data-stu-id="95906-119">No</span></span>|<span data-ttu-id="95906-120">資料分割</span><span class="sxs-lookup"><span data-stu-id="95906-120">No.</span></span>|
|<xref:System.Windows.Controls.RichTextBox>|<span data-ttu-id="95906-121">是</span><span class="sxs-lookup"><span data-stu-id="95906-121">Yes</span></span>|<span data-ttu-id="95906-122">是</span><span class="sxs-lookup"><span data-stu-id="95906-122">Yes</span></span>|<span data-ttu-id="95906-123">是</span><span class="sxs-lookup"><span data-stu-id="95906-123">Yes</span></span>|<span data-ttu-id="95906-124">是</span><span class="sxs-lookup"><span data-stu-id="95906-124">Yes</span></span>|

> [!NOTE]
> <span data-ttu-id="95906-125">雖然<xref:System.Windows.Controls.TextBox>不支援格式化相關的<xref:System.Windows.Documents.EditingCommands.ToggleBold%2A>命令（如（Ctr + B）），但這兩個控制項都支援許多<xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>基本命令，例如。</span><span class="sxs-lookup"><span data-stu-id="95906-125">Although <xref:System.Windows.Controls.TextBox> does not support formatting related commands like <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (Ctr+B), many basic commands are supported by both controls such as <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>.</span></span>

<span data-ttu-id="95906-126">稍後會更詳細說明上表中的功能。</span><span class="sxs-lookup"><span data-stu-id="95906-126">The features from the table above are covered in more detail later.</span></span>

<a name="creating_a_richtextbox"></a>

## <a name="creating-a-richtextbox"></a><span data-ttu-id="95906-127">建立 RichTextBox</span><span class="sxs-lookup"><span data-stu-id="95906-127">Creating a RichTextBox</span></span>

<span data-ttu-id="95906-128">下列<xref:System.Windows.Controls.RichTextBox>程式碼示範如何建立使用者可以在中編輯豐富內容的。</span><span class="sxs-lookup"><span data-stu-id="95906-128">The code below shows how to create a <xref:System.Windows.Controls.RichTextBox> that a user can edit rich content in.</span></span>

[!code-xaml[RichTextBoxMiscSnippets_snip#BasicRichTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/BasicRichTextBoxExample.xaml#basicrichtextboxexamplewholepage)]

<span data-ttu-id="95906-129">具體而言，在中<xref:System.Windows.Controls.RichTextBox>編輯的內容是「流動內容」。</span><span class="sxs-lookup"><span data-stu-id="95906-129">Specifically, the content edited in a <xref:System.Windows.Controls.RichTextBox> is flow content.</span></span> <span data-ttu-id="95906-130">非固定格式內容可以包含許多型別的元素，包括格式化文字、影像、清單及表格。</span><span class="sxs-lookup"><span data-stu-id="95906-130">Flow content can contain many types of elements including formatted text, images, lists, and tables.</span></span> <span data-ttu-id="95906-131">如需有關非固定格式文件的深入資訊，請參閱[非固定格式文件概觀](../advanced/flow-document-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="95906-131">See [Flow Document Overview](../advanced/flow-document-overview.md) for in depth information on flow documents.</span></span> <span data-ttu-id="95906-132">為了包含非固定格式內容， <xref:System.Windows.Controls.RichTextBox>會<xref:System.Windows.Documents.FlowDocument>主控物件，而後者又包含可編輯的內容。</span><span class="sxs-lookup"><span data-stu-id="95906-132">In order to contain flow content, a <xref:System.Windows.Controls.RichTextBox> hosts a <xref:System.Windows.Documents.FlowDocument> object which in turn contains the editable content.</span></span> <span data-ttu-id="95906-133">為了示範中的<xref:System.Windows.Controls.RichTextBox>流程內容，下列程式碼顯示如何<xref:System.Windows.Controls.RichTextBox>使用段落和一些粗體文字來建立。</span><span class="sxs-lookup"><span data-stu-id="95906-133">To demonstrate flow content in a <xref:System.Windows.Controls.RichTextBox>, the following code shows how to create a <xref:System.Windows.Controls.RichTextBox> with a paragraph and some bolded text.</span></span>

[!code-xaml[RichTextBoxMiscSnippets_snip#RichTextBoxWithContentExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/RichTextBoxWithContentExample.xaml#richtextboxwithcontentexamplewholepage)]

[!code-csharp[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/CSharp/BasicRichTextBoxWithContentExample.cs#basicrichtextboxwithcontentcodeonlyexample)]
[!code-vb[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/visualbasic/basicrichtextboxwithcontentexample.vb#basicrichtextboxwithcontentcodeonlyexample)]

<span data-ttu-id="95906-134">下圖顯示此範例的轉譯方式。</span><span class="sxs-lookup"><span data-stu-id="95906-134">The following illustration shows how this sample renders.</span></span>

<span data-ttu-id="95906-135">![具有內容的 RichTextBox](./media/editing-richtextbox-with-content.png "Editing_RichTextBox_with_Content")</span><span class="sxs-lookup"><span data-stu-id="95906-135">![RichTextBox with content](./media/editing-richtextbox-with-content.png "Editing_RichTextBox_with_Content")</span></span>

<span data-ttu-id="95906-136"><xref:System.Windows.Controls.RichTextBox>和<xref:System.Windows.Documents.Paragraph> 之類的元素會決定中的<xref:System.Windows.Documents.Bold>內容如何出現。</span><span class="sxs-lookup"><span data-stu-id="95906-136">Elements like <xref:System.Windows.Documents.Paragraph> and <xref:System.Windows.Documents.Bold> determine how the content inside a <xref:System.Windows.Controls.RichTextBox> appears.</span></span> <span data-ttu-id="95906-137">當使用者編輯<xref:System.Windows.Controls.RichTextBox>內容時，會變更此流程內容。</span><span class="sxs-lookup"><span data-stu-id="95906-137">As a user edits <xref:System.Windows.Controls.RichTextBox> content, they change this flow content.</span></span> <span data-ttu-id="95906-138">若要深入了解非固定格式內容的功能及如何與其搭配運作，請參閱[非固定格式文件概觀](../advanced/flow-document-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="95906-138">To learn more about the features of flow content and how to work with it, see [Flow Document Overview](../advanced/flow-document-overview.md).</span></span>

> [!NOTE]
> <span data-ttu-id="95906-139">內的<xref:System.Windows.Controls.RichTextBox>非固定格式內容，其行為與其他控制項中所包含的流程內容完全相同。</span><span class="sxs-lookup"><span data-stu-id="95906-139">Flow content inside a <xref:System.Windows.Controls.RichTextBox> does not behave exactly like flow content contained in other controls.</span></span> <span data-ttu-id="95906-140">例如，中<xref:System.Windows.Controls.RichTextBox>沒有任何資料行，因此不會自動調整大小行為。</span><span class="sxs-lookup"><span data-stu-id="95906-140">For example, there are no columns in a <xref:System.Windows.Controls.RichTextBox> and hence no automatic resizing behavior.</span></span> <span data-ttu-id="95906-141">此外，內建功能（例如搜尋、視圖模式、頁面流覽和縮放）無法在中<xref:System.Windows.Controls.RichTextBox>使用。</span><span class="sxs-lookup"><span data-stu-id="95906-141">Also, built in features like search, viewing mode, page navigation, and zoom are not available within a <xref:System.Windows.Controls.RichTextBox>.</span></span>

<a name="realtime_spellechecking"></a>

## <a name="real-time-spell-checking"></a><span data-ttu-id="95906-142">即時拼字檢查</span><span class="sxs-lookup"><span data-stu-id="95906-142">Real-time Spell Checking</span></span>

<span data-ttu-id="95906-143">您可以在<xref:System.Windows.Controls.TextBox>或<xref:System.Windows.Controls.RichTextBox>中啟用即時拼寫檢查。</span><span class="sxs-lookup"><span data-stu-id="95906-143">You can enable real-time spell checking in a <xref:System.Windows.Controls.TextBox> or <xref:System.Windows.Controls.RichTextBox>.</span></span> <span data-ttu-id="95906-144">啟用拼字檢查時，拼錯的文字下方會出現紅色線條 (請見下圖)。</span><span class="sxs-lookup"><span data-stu-id="95906-144">When spellchecking is turned on, a red line appears underneath any misspelled words (see picture below).</span></span>

<span data-ttu-id="95906-145">![具有拼字檢查功能的 TextBox](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")</span><span class="sxs-lookup"><span data-stu-id="95906-145">![Textbox with spell&#45;checking](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")</span></span>

<span data-ttu-id="95906-146">若要了解如何啟用拼字檢查，請參閱[在文字編輯控制項中啟用拼字檢查](how-to-enable-spell-checking-in-a-text-editing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="95906-146">See [Enable Spell Checking in a Text Editing Control](how-to-enable-spell-checking-in-a-text-editing-control.md) to learn how to enable spellchecking.</span></span>

<a name="context_menu"></a>

## <a name="context-menu"></a><span data-ttu-id="95906-147">操作功能表</span><span class="sxs-lookup"><span data-stu-id="95906-147">Context Menu</span></span>

<span data-ttu-id="95906-148">根據預設，和<xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox>都會有一個內容功能表，當使用者在控制項內按一下滑鼠右鍵時，就會出現此功能表。</span><span class="sxs-lookup"><span data-stu-id="95906-148">By default, both <xref:System.Windows.Controls.TextBox> and <xref:System.Windows.Controls.RichTextBox> have a context menu that appears when a user right-clicks inside the control.</span></span> <span data-ttu-id="95906-149">使用者可以使用此操作功能表來剪下、複製或貼上 (請見下圖)。</span><span class="sxs-lookup"><span data-stu-id="95906-149">The context menu allows the user to cut, copy, or paste (see illustration below).</span></span>

<span data-ttu-id="95906-150">![具有操作功能表的 TextBox](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")</span><span class="sxs-lookup"><span data-stu-id="95906-150">![TextBox with context menu](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")</span></span>

<span data-ttu-id="95906-151">您可以建立自己的自訂操作功能表來覆寫預設的操作功能表。</span><span class="sxs-lookup"><span data-stu-id="95906-151">You can create your own custom context menu to override the default one.</span></span> <span data-ttu-id="95906-152">如需詳細資訊，請參閱[在 RichTextBox 中放置自訂內容功能表](how-to-position-a-custom-context-menu-in-a-richtextbox.md)。</span><span class="sxs-lookup"><span data-stu-id="95906-152">See [Position a Custom Context Menu in a RichTextBox](how-to-position-a-custom-context-menu-in-a-richtextbox.md) for more information.</span></span>

<a name="detect_when_content_changes"></a>

## <a name="editing-commands"></a><span data-ttu-id="95906-153">編輯命令</span><span class="sxs-lookup"><span data-stu-id="95906-153">Editing Commands</span></span>

<span data-ttu-id="95906-154">編輯命令可讓使用者在內設定可編輯<xref:System.Windows.Controls.RichTextBox>內容的格式。</span><span class="sxs-lookup"><span data-stu-id="95906-154">Editing commands enable users to format editable content inside a <xref:System.Windows.Controls.RichTextBox>.</span></span> <span data-ttu-id="95906-155">除了基本的編輯命令<xref:System.Windows.Controls.RichTextBox>之外，還包括<xref:System.Windows.Controls.TextBox>不支援的格式化命令。</span><span class="sxs-lookup"><span data-stu-id="95906-155">Besides basic editing commands, <xref:System.Windows.Controls.RichTextBox> includes formatting commands that <xref:System.Windows.Controls.TextBox> does not support.</span></span> <span data-ttu-id="95906-156">例如，在中<xref:System.Windows.Controls.RichTextBox>編輯時，使用者可以按 Ctr + B 來切換粗體文字格式。</span><span class="sxs-lookup"><span data-stu-id="95906-156">For example, when editing in a <xref:System.Windows.Controls.RichTextBox>, a user could press Ctr+B to toggle bold text formatting.</span></span> <span data-ttu-id="95906-157">如<xref:System.Windows.Documents.EditingCommands>需可用命令的完整清單，請參閱。</span><span class="sxs-lookup"><span data-stu-id="95906-157">See <xref:System.Windows.Documents.EditingCommands> for a complete list of commands available.</span></span> <span data-ttu-id="95906-158">除了使用鍵盤快速鍵之外，您還可以將命令與其他控制項 (例如按鈕) 連接。</span><span class="sxs-lookup"><span data-stu-id="95906-158">In addition to using keyboard shortcuts, you can hook commands up to other controls like buttons.</span></span> <span data-ttu-id="95906-159">下列範例示範如何建立一個簡單的工具列，其中包含使用者可用來變更文字格式設定的按鈕。</span><span class="sxs-lookup"><span data-stu-id="95906-159">The following example shows how to create a simple tool bar containing buttons that the user can use to change text formatting.</span></span>

[!code-xaml[RichTextBox_InputPanel_snip#RichTextBoxWithToolBarExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_InputPanel_snip/CS/Window1.xaml#richtextboxwithtoolbarexamplewholepage)]

<span data-ttu-id="95906-160">下圖顯示此範例的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="95906-160">The following illustration shows how this sample displays.</span></span>

<span data-ttu-id="95906-161">![具有工具列的 RichTextBox](./media/editing-richtextbox-with-toobar.gif "Editing_RichTextBox_with_Content")</span><span class="sxs-lookup"><span data-stu-id="95906-161">![RichTextBox with ToolBar](./media/editing-richtextbox-with-toobar.gif "Editing_RichTextBox_with_TooBar")</span></span>

<a name="editing_commands"></a>

## <a name="detect-when-content-changes"></a><span data-ttu-id="95906-162">偵測內容變更</span><span class="sxs-lookup"><span data-stu-id="95906-162">Detect when Content Changes</span></span>

<span data-ttu-id="95906-163">通常應該使用<xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox> <xref:System.Windows.UIElement.KeyDown>事件來偵測中的文字，或變更，而不是您預期的方式。 <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged></span><span class="sxs-lookup"><span data-stu-id="95906-163">Usually the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event should be used to detect whenever the text in a <xref:System.Windows.Controls.TextBox> or <xref:System.Windows.Controls.RichTextBox> changes rather then <xref:System.Windows.UIElement.KeyDown> as you might expect.</span></span> <span data-ttu-id="95906-164">如需範例，請參閱[偵測 TextBox 中的文字變更](how-to-detect-when-text-in-a-textbox-has-changed.md)。</span><span class="sxs-lookup"><span data-stu-id="95906-164">See [Detect When Text in a TextBox Has Changed](how-to-detect-when-text-in-a-textbox-has-changed.md) for an example.</span></span>

<a name="save_load_and_print_richtextbox_content"></a>

## <a name="save-load-and-print-richtextbox-content"></a><span data-ttu-id="95906-165">儲存、載入和列印 RichTextBox 內容</span><span class="sxs-lookup"><span data-stu-id="95906-165">Save, Load, and Print RichTextBox Content</span></span>

<span data-ttu-id="95906-166">下列範例示範如何將的內容<xref:System.Windows.Controls.RichTextBox>儲存至檔案、將該內容載入回<xref:System.Windows.Controls.RichTextBox>，並列印內容。</span><span class="sxs-lookup"><span data-stu-id="95906-166">The following example shows how to save content of a <xref:System.Windows.Controls.RichTextBox> to a file, load that content back into the <xref:System.Windows.Controls.RichTextBox>, and print the contents.</span></span> <span data-ttu-id="95906-167">以下是此範例的標記。</span><span class="sxs-lookup"><span data-stu-id="95906-167">Below is the markup for the example.</span></span>

[!code-xaml[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml#saveloadprintrtbexamplewholepage)]

<span data-ttu-id="95906-168">以下是此範例的程式碼後置。</span><span class="sxs-lookup"><span data-stu-id="95906-168">Below is the code behind for the example.</span></span>

[!code-csharp[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml.cs#saveloadprintrtbcodeexamplewholepage)]
[!code-vb[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/SaveLoadPrintRTB.xaml.vb#saveloadprintrtbcodeexamplewholepage)]

## <a name="see-also"></a><span data-ttu-id="95906-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95906-169">See also</span></span>

- [<span data-ttu-id="95906-170">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="95906-170">How-to Topics</span></span>](richtextbox-how-to-topics.md)
- [<span data-ttu-id="95906-171">TextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="95906-171">TextBox Overview</span></span>](textbox-overview.md)
