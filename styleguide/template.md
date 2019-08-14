---
title:
- 文章標題
description: ''
author:
- GITHUB USERNAME
ms.author:
- MICROSOFT ALIAS OF INTERNAL OWNER
ms.date:
- CREATION/UPDATE DATE - mm/dd/yyyy
ms.topic:
- TOPIC TYPE
ms.prod:
- PRODUCT VALUE
helpviewer_keywords:
- OFFLINE BOOK INDEX ENTRIES
ms.openlocfilehash: 0e8548745768bc9137e8fc76f86fc9fc7982b8de
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "68616348"
---
# <a name="metadata-and-markdown-template"></a><span data-ttu-id="6a91a-102">中繼資料和 Markdown 範本</span><span class="sxs-lookup"><span data-stu-id="6a91a-102">Metadata and Markdown Template</span></span>

<span data-ttu-id="6a91a-103">此 dotnet/docs 範本包含 Markdown 語法，以及設定中繼資料的指導。</span><span class="sxs-lookup"><span data-stu-id="6a91a-103">This dotnet/docs template contains examples of Markdown syntax, as well as guidance on setting the metadata.</span></span> <span data-ttu-id="6a91a-104">若要善加利用它，您必須檢閱[原始的 Markdown (英文)](https://raw.githubusercontent.com/dotnet/docs/master/styleguide/template.md) 和[轉譯後的檢視 (英文)](https://github.com/dotnet/docs/blob/master/styleguide/template.md) (例如，原始的 Markdown 會顯示中繼資料區塊，而轉譯後的檢視則不會)。</span><span class="sxs-lookup"><span data-stu-id="6a91a-104">To get the most of it, you must view both the [raw Markdown](https://raw.githubusercontent.com/dotnet/docs/master/styleguide/template.md) and the [rendered view](https://github.com/dotnet/docs/blob/master/styleguide/template.md) (for instance, the raw Markdown shows the metadata block, while the rendered view does not).</span></span>

<span data-ttu-id="6a91a-105">在建立 Markdown 檔案的時候，您應將此範本複製到新的檔案，填入下列指定的中繼資料，將上方的 H1 標題設為文章的標題，然後刪除內容。</span><span class="sxs-lookup"><span data-stu-id="6a91a-105">When creating a Markdown file, you should copy this template to a new file, fill out the metadata as specified below, set the H1 heading above to the title of the article, and delete the content.</span></span>

## <a name="metadata"></a><span data-ttu-id="6a91a-106">中繼資料</span><span class="sxs-lookup"><span data-stu-id="6a91a-106">Metadata</span></span>

<span data-ttu-id="6a91a-107">完整的中繼資料區塊如上 (以[原始的 Markdown (英文)](https://raw.githubusercontent.com/dotnet/docs/master/styleguide/template.md) 顯示)，其中分為必要欄位和選擇性欄位。</span><span class="sxs-lookup"><span data-stu-id="6a91a-107">The full metadata block is above (in the [raw Markdown](https://raw.githubusercontent.com/dotnet/docs/master/styleguide/template.md)), divided into required fields and optional fields.</span></span> <span data-ttu-id="6a91a-108">重點提示：</span><span class="sxs-lookup"><span data-stu-id="6a91a-108">Some key notes:</span></span>

- <span data-ttu-id="6a91a-109">請「務必」  在中繼資料項目的值和冒號 (:) 之間加上一個空格。</span><span class="sxs-lookup"><span data-stu-id="6a91a-109">You **must** have a space between the colon (:) and the value for a metadata element.</span></span>
- <span data-ttu-id="6a91a-110">如果選擇性的中繼資料元素沒有值，請使用 # 將元素標記為註解，或將它移除 (請勿將它保留空白或使用 "na")。</span><span class="sxs-lookup"><span data-stu-id="6a91a-110">If an optional metadata element doesn't have a value, comment out the element with a # or remove it (don't leave it blank or use "na").</span></span> <span data-ttu-id="6a91a-111">如果您要將值新增至已設為註解的元素，請務必移除 #。</span><span class="sxs-lookup"><span data-stu-id="6a91a-111">If you're adding a value to an element that was commented out, be sure to remove the #.</span></span>
- <span data-ttu-id="6a91a-112">在值中出現冒號 (例如標題) 會中斷中繼資料剖析器。</span><span class="sxs-lookup"><span data-stu-id="6a91a-112">Colons in a value (for example, a title) break the metadata parser.</span></span> <span data-ttu-id="6a91a-113">在此情況下，請使用雙引號括住標題 (例如，`title: "Writing .NET Core console apps: An advanced step-by-step guide"`)。</span><span class="sxs-lookup"><span data-stu-id="6a91a-113">In this case, surround the title with double quotes (for example, `title: "Writing .NET Core console apps: An advanced step-by-step guide"`).</span></span>
- <span data-ttu-id="6a91a-114">**title**：出現在搜尋引擎結果中。</span><span class="sxs-lookup"><span data-stu-id="6a91a-114">**title**: Appears in search engine results.</span></span> <span data-ttu-id="6a91a-115">此標題不應該與 H1 標題中的標題相同，且應包含最多 60 個字元。</span><span class="sxs-lookup"><span data-stu-id="6a91a-115">The title shouldn't be identical to the title in your H1 heading, and it should contain 60 characters or less.</span></span>
- <span data-ttu-id="6a91a-116">**description**：摘要文章的內容。</span><span class="sxs-lookup"><span data-stu-id="6a91a-116">**description**: Summarizes the content of the article.</span></span> <span data-ttu-id="6a91a-117">它通常顯示在 [搜尋結果] 頁面中，但不會用於搜尋排名。</span><span class="sxs-lookup"><span data-stu-id="6a91a-117">It's usually shown in the search results page, but it isn't used for search ranking.</span></span> <span data-ttu-id="6a91a-118">其長度應該是 115-145 個字元，包括空格。</span><span class="sxs-lookup"><span data-stu-id="6a91a-118">Its length should be 115-145 characters including spaces.</span></span>
- <span data-ttu-id="6a91a-119">**author** 和 **ms.author**：author 欄位應包含該作者的 **GitHub 使用者名稱**，而不是別名。</span><span class="sxs-lookup"><span data-stu-id="6a91a-119">**author** and **ms.author**: The author field should contain the **GitHub username** of the author, not his/her alias.</span></span>  <span data-ttu-id="6a91a-120">另一方面，**ms.author** 欄位應該包含 Microsoft 別名，並指出負責維護文章的人員。</span><span class="sxs-lookup"><span data-stu-id="6a91a-120">The **ms.author** field, on the other hand, should contain a Microsoft alias and indicates the person responsible for maintaining the article.</span></span>
- <span data-ttu-id="6a91a-121">**ms.topic**：主題類型。</span><span class="sxs-lookup"><span data-stu-id="6a91a-121">**ms.topic**: The topic type.</span></span> <span data-ttu-id="6a91a-122">最常見的值是 `conceptual`，且是在全域層級設定。</span><span class="sxs-lookup"><span data-stu-id="6a91a-122">The most common value is `conceptual` and is set at a global level.</span></span> <span data-ttu-id="6a91a-123">其他常用的值為 `tutorial`、`overview` 和 `reference`。</span><span class="sxs-lookup"><span data-stu-id="6a91a-123">Other common values used are `tutorial`, `overview`, and `reference`.</span></span>
- <span data-ttu-id="6a91a-124">**ms.devlang** 會定義針對主題顯示的語言篩選條件。</span><span class="sxs-lookup"><span data-stu-id="6a91a-124">**ms.devlang** defines the language filter displayed for the topic.</span></span> <span data-ttu-id="6a91a-125">您可以在[支援的語言](#supported-languages)一節看到支援的值清單。</span><span class="sxs-lookup"><span data-stu-id="6a91a-125">You can see a list of the supported values in the [Supported languages](#supported-languages) section.</span></span> <span data-ttu-id="6a91a-126">只有當主題涵蓋多個程式設計語言時，才需要設定。</span><span class="sxs-lookup"><span data-stu-id="6a91a-126">Only needs to be set when there's more than one programming language covered in the topic.</span></span> <span data-ttu-id="6a91a-127">一般而言，我們只會在內容中使用 `csharp`、`vb`、`fsharp` 和 `cpp` 作為此值。</span><span class="sxs-lookup"><span data-stu-id="6a91a-127">Typically, we only use `csharp`, `vb`, `fsharp`, and `cpp` for this value in our content.</span></span>
- <span data-ttu-id="6a91a-128">**ms.prod**：用於 BI 用途的產品識別。</span><span class="sxs-lookup"><span data-stu-id="6a91a-128">**ms.prod**: Product identification used for BI purposes.</span></span> <span data-ttu-id="6a91a-129">它們通常是在全域層級設定，因此通常不會出現在每篇文章的中繼資料區塊中。</span><span class="sxs-lookup"><span data-stu-id="6a91a-129">They're usually set at a global level, so they don't usually appear in the metadata block of each article.</span></span>
- <span data-ttu-id="6a91a-130">**ms.technology**：其他 BI 分類。</span><span class="sxs-lookup"><span data-stu-id="6a91a-130">**ms.technology**: Additional BI classification.</span></span> <span data-ttu-id="6a91a-131">一些支援的值為 `devlang-csharp` (適用於 C# 主題)、`devlang-fsharp` (適用於 F# 主題) 和 `devlang-visual-basic` (適用於 VB 主題)。</span><span class="sxs-lookup"><span data-stu-id="6a91a-131">Some of the supported values are: `devlang-csharp` for C# topics, `devlang-fsharp` for F# topics, and `devlang-visual-basic` for VB topics.</span></span> <span data-ttu-id="6a91a-132">針對其他指南，值會有所不同，因此請詢問小組成員以取得指導方針。</span><span class="sxs-lookup"><span data-stu-id="6a91a-132">For other guides, the values will vary, so ask a member of the team for guidance.</span></span>
- <span data-ttu-id="6a91a-133">**ms.date**：格式為 MM/DD/YYYY 的日期。</span><span class="sxs-lookup"><span data-stu-id="6a91a-133">**ms.date**: A date in the format MM/DD/YYYY.</span></span> <span data-ttu-id="6a91a-134">顯示在已發佈頁面上，以指出上次文章基本上編輯或保證為「全新」的時間 (也就是，已檢查過文章並將其視為最新)。</span><span class="sxs-lookup"><span data-stu-id="6a91a-134">Displayed on the published page to indicate the last time the article was substantially edited or guaranteed "fresh" (that is, the article was reviewed and considered up-to-date).</span></span>
- <span data-ttu-id="6a91a-135">**helpviewer_keywords**：項目用於離線書籍索引 (Visual Studio 中的功能)。</span><span class="sxs-lookup"><span data-stu-id="6a91a-135">**helpviewer_keywords**: Entries are used for the offline books index (functionality in Visual Studio).</span></span>
- <span data-ttu-id="6a91a-136">**f1_keywords**：將文章連接至 F1 鍵 (Visual Studio 中的功能)。</span><span class="sxs-lookup"><span data-stu-id="6a91a-136">**f1_keywords**: Connects the article to the F1 key (functionality in Visual Studio).</span></span>

## <a name="basic-markdown-gfm-and-special-characters"></a><span data-ttu-id="6a91a-137">基本 Markdown、GFM 和特殊字元</span><span class="sxs-lookup"><span data-stu-id="6a91a-137">Basic Markdown, GFM, and special characters</span></span>

<span data-ttu-id="6a91a-138">支援所有基本和 GitHub Flavored Markdown (GFM)。</span><span class="sxs-lookup"><span data-stu-id="6a91a-138">All basic and GitHub Flavored Markdown (GFM) is supported.</span></span> <span data-ttu-id="6a91a-139">如需詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="6a91a-139">For more information on these, see:</span></span>

- [<span data-ttu-id="6a91a-140">基準 Markdown 語法 (英文)</span><span class="sxs-lookup"><span data-stu-id="6a91a-140">Baseline Markdown syntax</span></span>](https://daringfireball.net/projects/markdown/syntax)
- [<span data-ttu-id="6a91a-141">GFM 文件 (英文)</span><span class="sxs-lookup"><span data-stu-id="6a91a-141">GFM documentation</span></span>](https://guides.github.com/features/mastering-markdown)

<span data-ttu-id="6a91a-142">Markdown 使用 \*、\` 和 \# 等特殊字元來設定格式。</span><span class="sxs-lookup"><span data-stu-id="6a91a-142">Markdown uses special characters such as \*, \`, and \# for formatting.</span></span> <span data-ttu-id="6a91a-143">如果要在內容中包含這些字元，請遵循下列其中一種作法：</span><span class="sxs-lookup"><span data-stu-id="6a91a-143">If you wish to include one of these characters in your content, you must do one of two things:</span></span>

- <span data-ttu-id="6a91a-144">在該特殊字元前面加上反斜線來將它「逸出」(例如，\* 逸出為 `\*`)</span><span class="sxs-lookup"><span data-stu-id="6a91a-144">Put a backslash before the special character to "escape" it (for example, `\*` for a \*)</span></span>
- <span data-ttu-id="6a91a-145">使用該字元的 [HTML 實體代碼 (英文)](https://www.ascii.cl/htmlcodes.htm) (例如，&#42; 為 `&#42;`)。</span><span class="sxs-lookup"><span data-stu-id="6a91a-145">Use the [HTML entity code](https://www.ascii.cl/htmlcodes.htm) for the character (for example, `&#42;` for a &#42;).</span></span>

## <a name="file-name"></a><span data-ttu-id="6a91a-146">檔案名稱</span><span class="sxs-lookup"><span data-stu-id="6a91a-146">File name</span></span>

<span data-ttu-id="6a91a-147">檔案名稱使用下列規則︰</span><span class="sxs-lookup"><span data-stu-id="6a91a-147">File names use the following rules:</span></span>

* <span data-ttu-id="6a91a-148">只包含小寫字母、數字和連字號。</span><span class="sxs-lookup"><span data-stu-id="6a91a-148">Contain only lowercase letters, numbers, and hyphens.</span></span>
* <span data-ttu-id="6a91a-149">不使用空格或標點符號。</span><span class="sxs-lookup"><span data-stu-id="6a91a-149">No spaces or punctuation characters.</span></span> <span data-ttu-id="6a91a-150">使用連字號來分隔檔名中的文字和數字。</span><span class="sxs-lookup"><span data-stu-id="6a91a-150">Use the hyphens to separate words and numbers in the file name.</span></span>
* <span data-ttu-id="6a91a-151">使用明確的動作動詞，例如 develop、buy、build、troubleshoot。</span><span class="sxs-lookup"><span data-stu-id="6a91a-151">Use action verbs that are specific, such as develop, buy, build, troubleshoot.</span></span> <span data-ttu-id="6a91a-152">不使用 -ing 字詞。</span><span class="sxs-lookup"><span data-stu-id="6a91a-152">No -ing words.</span></span>
* <span data-ttu-id="6a91a-153">不使用短字詞，例如 a、and、the、in、or 等等。</span><span class="sxs-lookup"><span data-stu-id="6a91a-153">No small words - don't include a, and, the, in, or, etc.</span></span>
* <span data-ttu-id="6a91a-154">必須為 Markdown 格式且使用副檔名 .md。</span><span class="sxs-lookup"><span data-stu-id="6a91a-154">Must be in Markdown and use the .md file extension.</span></span>
* <span data-ttu-id="6a91a-155">盡可能保持檔名簡短。</span><span class="sxs-lookup"><span data-stu-id="6a91a-155">Keep file names reasonably short.</span></span> <span data-ttu-id="6a91a-156">它們會是文章 URL 的一部分。</span><span class="sxs-lookup"><span data-stu-id="6a91a-156">They are part of the URL for your articles.</span></span>

## <a name="headings"></a><span data-ttu-id="6a91a-157">標題</span><span class="sxs-lookup"><span data-stu-id="6a91a-157">Headings</span></span>

<span data-ttu-id="6a91a-158">使用句子樣式的大寫。</span><span class="sxs-lookup"><span data-stu-id="6a91a-158">Use sentence-style capitalization.</span></span> <span data-ttu-id="6a91a-159">下列情況一律大寫：</span><span class="sxs-lookup"><span data-stu-id="6a91a-159">Always capitalize:</span></span>

- <span data-ttu-id="6a91a-160">標題的第一個字。</span><span class="sxs-lookup"><span data-stu-id="6a91a-160">The first word of a heading.</span></span>
- <span data-ttu-id="6a91a-161">標題中冒號後的第一個字 (例如，"How to:Sort an array")。</span><span class="sxs-lookup"><span data-stu-id="6a91a-161">The word following a colon in a title or heading (for example, "How to: Sort an array").</span></span>

<span data-ttu-id="6a91a-162">標題應使用 atx 樣式，也就是在行開頭以 1 至 6 個井字號 (#) 來表示標題，這會對應到 HTML 標題層級 H1 至 H6。</span><span class="sxs-lookup"><span data-stu-id="6a91a-162">Headings should be done using atx-style, that is, use 1-6 hash characters (#) at the start of the line to indicate a heading, corresponding to HTML headings levels H1 through H6.</span></span> <span data-ttu-id="6a91a-163">上面使用的是第一和第二層級標題的範例。</span><span class="sxs-lookup"><span data-stu-id="6a91a-163">Examples of first- and second-level headers are used above.</span></span>

<span data-ttu-id="6a91a-164">請「務必」  確定主題中只有一個第一層級標題 (H1)，該標題會顯示為頁面標題。</span><span class="sxs-lookup"><span data-stu-id="6a91a-164">There **must** be only one first-level heading (H1) in your topic, which will be displayed as the on-page title.</span></span>

<span data-ttu-id="6a91a-165">如果您的標題結尾是 `#` 字元，則您必須在結尾另外加上一個 `#` 以使標題正確轉譯。</span><span class="sxs-lookup"><span data-stu-id="6a91a-165">If your heading finishes with a `#` character, you need to add an extra `#` character in the end in order for the title to render correctly.</span></span> <span data-ttu-id="6a91a-166">例如，`# Async Programming in F# #`。</span><span class="sxs-lookup"><span data-stu-id="6a91a-166">For example, `# Async Programming in F# #`.</span></span>

<span data-ttu-id="6a91a-167">第二層級的標題會產生頁面目錄，並顯示在頁面標題下的 [本文內容] 區段中。</span><span class="sxs-lookup"><span data-stu-id="6a91a-167">Second-level headings will generate the on-page TOC that appears in the "In this article" section underneath the on-page title.</span></span>

### <a name="third-level-heading"></a><span data-ttu-id="6a91a-168">第三層級標題</span><span class="sxs-lookup"><span data-stu-id="6a91a-168">Third-level heading</span></span>
#### <a name="fourth-level-heading"></a><span data-ttu-id="6a91a-169">第四層級標題</span><span class="sxs-lookup"><span data-stu-id="6a91a-169">Fourth-level heading</span></span>
##### <a name="fifth-level-heading"></a><span data-ttu-id="6a91a-170">第五層級標題</span><span class="sxs-lookup"><span data-stu-id="6a91a-170">Fifth level heading</span></span>
###### <a name="sixth-level-heading"></a><span data-ttu-id="6a91a-171">第六層級標題</span><span class="sxs-lookup"><span data-stu-id="6a91a-171">Sixth-level heading</span></span>

## <a name="text-styling"></a><span data-ttu-id="6a91a-172">文字樣式</span><span class="sxs-lookup"><span data-stu-id="6a91a-172">Text styling</span></span>

<span data-ttu-id="6a91a-173">「斜體」  用於檔案、資料夾、路徑 (較長的項目請分割為各行)、新字詞。</span><span class="sxs-lookup"><span data-stu-id="6a91a-173">*Italics* Use for files, folders, paths (for long items, split onto their own line), new terms.</span></span>

<span data-ttu-id="6a91a-174">**粗體** 用於 UI 元素。</span><span class="sxs-lookup"><span data-stu-id="6a91a-174">**Bold** Use for UI elements.</span></span>

<span data-ttu-id="6a91a-175">`Code` 用於內嵌程式碼、語言關鍵字、NuGet 套件名稱、命令列命令、資料庫資料表和資料行名稱，以及您不想要可以點按的 URL。</span><span class="sxs-lookup"><span data-stu-id="6a91a-175">`Code` Use for inline code, language keywords, NuGet package names, command-line commands, database table and column names, and URLs that you don't want to be clickable.</span></span>

## <a name="links"></a><span data-ttu-id="6a91a-176">連結</span><span class="sxs-lookup"><span data-stu-id="6a91a-176">Links</span></span>

### <a name="internal-links"></a><span data-ttu-id="6a91a-177">內部連結</span><span class="sxs-lookup"><span data-stu-id="6a91a-177">Internal Links</span></span>

<span data-ttu-id="6a91a-178">若要連結到同一個 Markdown 檔案中的標題 (又稱錨點連結)，您需要找出該標題的識別碼。</span><span class="sxs-lookup"><span data-stu-id="6a91a-178">To link to a header in the same Markdown file (also known as anchor links), you'll need to find out the id of the header you're trying to link to.</span></span> <span data-ttu-id="6a91a-179">若要確認識別碼，請檢視轉譯文章的原始程式碼，以找出該標題的識別碼 (例如，`id="blockquote"`)，然後使用「# + 識別碼」來連結 (例如，`#blockquote`)。</span><span class="sxs-lookup"><span data-stu-id="6a91a-179">To confirm the ID, view the source of the rendered article, find the id of the header (for example, `id="blockquote"`), and link using # + id (for example, `#blockquote`).</span></span>
<span data-ttu-id="6a91a-180">此識別碼是依據標題文字而自動產生。</span><span class="sxs-lookup"><span data-stu-id="6a91a-180">The id is auto-generated based on the header text.</span></span> <span data-ttu-id="6a91a-181">舉例來說，若某章節名稱為 `## Step 2`，則識別碼會是 `id="step-2"`。</span><span class="sxs-lookup"><span data-stu-id="6a91a-181">So, for example, given a unique section named `## Step 2`, the id would look like this `id="step-2"`.</span></span>

- <span data-ttu-id="6a91a-182">範例：`[Declare inline blocks with a language identifier](#inline-code-blocks-with-language-identifier)` 會產生[宣告具有語言識別碼的內嵌區塊](#inline-code-blocks-with-language-identifier)。</span><span class="sxs-lookup"><span data-stu-id="6a91a-182">Example: `[Declare inline blocks with a language identifier](#inline-code-blocks-with-language-identifier)` produces [Declare inline blocks with a language identifier](#inline-code-blocks-with-language-identifier).</span></span>

<span data-ttu-id="6a91a-183">若要連結到同一個存放庫中的 Markdown 檔案，請使用[相對連結](https://www.w3.org/TR/WD-html40-970917/htmlweb.html#h-5.1.2)，且檔案名稱結尾包含 ".md"。</span><span class="sxs-lookup"><span data-stu-id="6a91a-183">To link to a Markdown file in the same repo, use [relative links](https://www.w3.org/TR/WD-html40-970917/htmlweb.html#h-5.1.2), including the ".md" at the end of the filename.</span></span>

- <span data-ttu-id="6a91a-184">範例：`[Readme file](../README.md)` 會產生[讀我檔案](../README.md)。</span><span class="sxs-lookup"><span data-stu-id="6a91a-184">Example: `[Readme file](../README.md)` produces [Readme file](../README.md).</span></span> <span data-ttu-id="6a91a-185">(請注意，連結會區分大小寫。)</span><span class="sxs-lookup"><span data-stu-id="6a91a-185">(Note that links are case-sensitive.)</span></span>
- <span data-ttu-id="6a91a-186">範例：`[Welcome to .NET](../docs/welcome.md)` 會產生[歡迎使用 .NET](../docs/welcome.md)。</span><span class="sxs-lookup"><span data-stu-id="6a91a-186">Example: `[Welcome to .NET](../docs/welcome.md)` produces [Welcome to .NET](../docs/welcome.md).</span></span>

<span data-ttu-id="6a91a-187">若要連結到相同存放庫中 Markdown 檔案內的標題，請使用「相對連結 + 井字號」來連結。</span><span class="sxs-lookup"><span data-stu-id="6a91a-187">To link to a header in a Markdown file in the same repo, use relative linking + hashtag linking.</span></span>

- <span data-ttu-id="6a91a-188">範例：`[.NET Community](../docs/welcome.md#open-source)` 會產生 [.NET 社群](../docs/welcome.md#open-source)。</span><span class="sxs-lookup"><span data-stu-id="6a91a-188">Example: `[.NET Community](../docs/welcome.md#open-source)` produces [.NET Community](../docs/welcome.md#open-source).</span></span>

<span data-ttu-id="6a91a-189">在大部分情況下，我們會使用相對連結，且不鼓勵在連結中使用 `~/`，因為相對連結會在 GitHub 上的來源中解析。</span><span class="sxs-lookup"><span data-stu-id="6a91a-189">In most cases, we use the relative links and discourage the use of `~/` in links because relative links resolve in the source on GitHub.</span></span> <span data-ttu-id="6a91a-190">不過，每當我們連結至相依存放庫中的檔案時，我們會使用 `~/` 字元來提供路徑。</span><span class="sxs-lookup"><span data-stu-id="6a91a-190">However, whenever we link to a file in a dependent repo, we'll use the `~/` character to provide the path.</span></span> <span data-ttu-id="6a91a-191">因為相依存放庫中的檔案位於 GitHub 中不同位置，所以連結不會以相對連結正確解析，不論其撰寫方式為何。</span><span class="sxs-lookup"><span data-stu-id="6a91a-191">Because the files in the dependent repo are in a different location in GitHub the links won't resolve correctly with relative links regardless of how they were written.</span></span>

<span data-ttu-id="6a91a-192">C# 語言規格和 Visual Basic 語言規格包含在 .NET 文件中，方法是包含語言存放庫中的來源。</span><span class="sxs-lookup"><span data-stu-id="6a91a-192">The C# language specification and the Visual Basic language specification are included in the .NET docs by including the source from the language repositories.</span></span> <span data-ttu-id="6a91a-193">Markdown 來源是在 [csharplang](https://github.com/dotnet/csharplang) 和 [visual basic](https://github.com/dotnet/vblang) 存放庫中進行管理。</span><span class="sxs-lookup"><span data-stu-id="6a91a-193">The markdown sources are managed in the [csharplang](https://github.com/dotnet/csharplang) and [visual basic](https://github.com/dotnet/vblang) repositories.</span></span>

<span data-ttu-id="6a91a-194">規格連結必須指向包含這些規格的來源目錄。</span><span class="sxs-lookup"><span data-stu-id="6a91a-194">Links to the spec must point to the source directories where those specs are included.</span></span> <span data-ttu-id="6a91a-195">對於 C#，它是 **~/_csharplang/spec**，而對於 VB 而言，它是 **~/_vblang/spec**。</span><span class="sxs-lookup"><span data-stu-id="6a91a-195">For C#, it's **~/_csharplang/spec** and for VB, it's **~/_vblang/spec**.</span></span>

- <span data-ttu-id="6a91a-196">範例：`[C# Query Expressions](~/_csharplang/spec/expressions.md#query-expressions)` 會產生 [C# 查詢運算式](~/_csharplang/spec/expressions.md#query-expressions)。</span><span class="sxs-lookup"><span data-stu-id="6a91a-196">Example: `[C# Query Expressions](~/_csharplang/spec/expressions.md#query-expressions)` produces [C# Query Expressions](~/_csharplang/spec/expressions.md#query-expressions).</span></span>

### <a name="external-links"></a><span data-ttu-id="6a91a-197">外部連結</span><span class="sxs-lookup"><span data-stu-id="6a91a-197">External Links</span></span>

<span data-ttu-id="6a91a-198">若要連結到外部檔案，請使用完整 URL 作為連結。</span><span class="sxs-lookup"><span data-stu-id="6a91a-198">To link to an external file, use the full URL as the link.</span></span>

- <span data-ttu-id="6a91a-199">範例：`[GitHub](https://www.github.com)` 會產生 [GitHub](https://www.github.com)。</span><span class="sxs-lookup"><span data-stu-id="6a91a-199">Example: `[GitHub](https://www.github.com)` produces [GitHub](https://www.github.com).</span></span>

<span data-ttu-id="6a91a-200">如果 Markdown 檔案中出現 URL，系統會將它轉換成可點擊的連結。</span><span class="sxs-lookup"><span data-stu-id="6a91a-200">If a URL appears in a Markdown file, it will be transformed into a clickable link.</span></span>

- <span data-ttu-id="6a91a-201">範例：`<https://www.github.com>` 會產生 <https://www.github.com>。</span><span class="sxs-lookup"><span data-stu-id="6a91a-201">Example: `<https://www.github.com>` produces <https://www.github.com>.</span></span>

<span data-ttu-id="6a91a-202">外部連結最好使用 `https` 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="6a91a-202">Prefer the `https` protocol for external links.</span></span> <span data-ttu-id="6a91a-203">僅針對不支援 `https` 的網站使用 `http` 連結。</span><span class="sxs-lookup"><span data-stu-id="6a91a-203">Only use `http` links for sites that do not support `https`.</span></span>

### <a name="links-to-apis"></a><span data-ttu-id="6a91a-204">API 的連結</span><span class="sxs-lookup"><span data-stu-id="6a91a-204">Links to APIs</span></span>

<span data-ttu-id="6a91a-205">組建系統有些延伸模組可讓我們在不需使用外部連結的情況下，連結到 .NET API。</span><span class="sxs-lookup"><span data-stu-id="6a91a-205">The build system has some extensions that allow us to link to .NET APIs without having to use external links.</span></span>
<span data-ttu-id="6a91a-206">當連結到 API 時，您可以使用從原始程式碼自動產生的唯一識別碼 (UID)。</span><span class="sxs-lookup"><span data-stu-id="6a91a-206">When linking to an API, you can use its unique identifier (UID) that is auto-generated from the source code.</span></span>

<span data-ttu-id="6a91a-207">UID 等於完整型別和成員名稱。</span><span class="sxs-lookup"><span data-stu-id="6a91a-207">The UID equates to the fully qualified type and member name.</span></span>

<span data-ttu-id="6a91a-208">如果您在 UID 之後新增 \* (或 %2A)，則連結會代表多載頁面，而不是特定的 API。</span><span class="sxs-lookup"><span data-stu-id="6a91a-208">If you add a \* (or %2A) after the UID, the link then represents the overload page and not a specific API.</span></span> <span data-ttu-id="6a91a-209">例如，您可以用它來以一般方式連結至 [List\<T>.BinarySearch 方法](https://docs.microsoft.com/dotnet/api/system.collections.generic.list-1.binarysearch)頁面，而不是使用特定的多載，例如 [List\<T>.BinarySearch(T, IComparer\<T>)](https://docs.microsoft.com/dotnet/api/system.collections.generic.list-1.binarysearch#System_Collections_Generic_List_1_BinarySearch__0_)。</span><span class="sxs-lookup"><span data-stu-id="6a91a-209">For example, you can use that when you want to link to the [List\<T>.BinarySearch Method](https://docs.microsoft.com/dotnet/api/system.collections.generic.list-1.binarysearch) page in a generic way instead of a specific overload such as [List\<T>.BinarySearch(T, IComparer\<T>)](https://docs.microsoft.com/dotnet/api/system.collections.generic.list-1.binarysearch#System_Collections_Generic_List_1_BinarySearch__0_).</span></span> <span data-ttu-id="6a91a-210">當成員未多載時，您也可以使用 \* 連結至成員頁面；如此您便不必在 UID 中包含參數清單。</span><span class="sxs-lookup"><span data-stu-id="6a91a-210">You can also use \* to link to a member page when the member is not overloaded; this saves you from having to include the parameter list in the UID.</span></span>

<span data-ttu-id="6a91a-211">若要連結至特定方法多載，您必須包含每個方法參數的完整型別名稱。</span><span class="sxs-lookup"><span data-stu-id="6a91a-211">To link to a specific method overload, you must include the fully qualified type name of each of the method's parameters.</span></span> <span data-ttu-id="6a91a-212">例如，\<xref:System.DateTime.ToString> 會連結到無參數的 [DateTime.ToString](https://docs.microsoft.com/dotnet/api/system.datetime.tostring#System_DateTime_ToString) 方法，而 \<xref:System.DateTime.ToString(System.String,System.IFormatProvider)> 連結到 [DateTime.ToString(String,IFormatProvider)](https://docs.microsoft.com/dotnet/api/system.datetime.tostring#System_DateTime_ToString_System_String_System_IFormatProvider_) 方法。</span><span class="sxs-lookup"><span data-stu-id="6a91a-212">For example, \<xref:System.DateTime.ToString> links to the parameterless [DateTime.ToString](https://docs.microsoft.com/dotnet/api/system.datetime.tostring#System_DateTime_ToString) method, while \<xref:System.DateTime.ToString(System.String,System.IFormatProvider)> links to the  [DateTime.ToString(String,IFormatProvider)](https://docs.microsoft.com/dotnet/api/system.datetime.tostring#System_DateTime_ToString_System_String_System_IFormatProvider_) method.</span></span> <span data-ttu-id="6a91a-213">您可以從 `https://xref.docs.microsoft.com/autocomplete` 找到特定多載成員的 UID。</span><span class="sxs-lookup"><span data-stu-id="6a91a-213">You can find the UIDs of a particular overloaded member from `https://xref.docs.microsoft.com/autocomplete`.</span></span> <span data-ttu-id="6a91a-214">查詢字串 "?text= *\<type-member-name>* " 會識別您想要查看其 UID 的型別或成員。</span><span class="sxs-lookup"><span data-stu-id="6a91a-214">The query string "?text=*\<type-member-name>*" identifies the type or member whose UIDs you'd like to see.</span></span> <span data-ttu-id="6a91a-215">例如，`https://xref.docs.microsoft.com/autocomplete?text=string.format` 會擷取 [String.Format](https://docs.microsoft.com/dotnet/api/system.string.format) 多載。</span><span class="sxs-lookup"><span data-stu-id="6a91a-215">For example, `https://xref.docs.microsoft.com/autocomplete?text=string.format` retrieves the [String.Format](https://docs.microsoft.com/dotnet/api/system.string.format) overloads.</span></span>

<span data-ttu-id="6a91a-216">若要連結到泛型型別 (例如 [System.Collections.Generic.List\<T>](https://docs.microsoft.com/dotnet/api/system.collections.generic.list-1))，請使用 \` (%60) 字元，後面接著泛型型別參數的數目。</span><span class="sxs-lookup"><span data-stu-id="6a91a-216">To link to a generic type, such as [System.Collections.Generic.List\<T>](https://docs.microsoft.com/dotnet/api/system.collections.generic.list-1), you use the \` (%60) character followed by the number of generic type parameters.</span></span> <span data-ttu-id="6a91a-217">例如，\<xref:System.Nullable%601> 會連結到 [System.Nullable\<T>](https://docs.microsoft.com/dotnet/api/system.nullable-1) 型別，而 \<xref:System.Func%602> 連結到 [System.Func\<T,TResult>](https://docs.microsoft.com/dotnet/api/system.func-2) 委派。</span><span class="sxs-lookup"><span data-stu-id="6a91a-217">For example, \<xref:System.Nullable%601> links to the [System.Nullable\<T>](https://docs.microsoft.com/dotnet/api/system.nullable-1) type, while \<xref:System.Func%602> links to the [System.Func\<T,TResult>](https://docs.microsoft.com/dotnet/api/system.func-2) delegate.</span></span>

<span data-ttu-id="6a91a-218">您可以使用下列其中一個語法：</span><span class="sxs-lookup"><span data-stu-id="6a91a-218">You can use one of the following syntax:</span></span>

1. <span data-ttu-id="6a91a-219">自動連結：`<xref:UID>` 或 `<xref:UID?displayProperty=nameWithType>`</span><span class="sxs-lookup"><span data-stu-id="6a91a-219">Auto-link: `<xref:UID>` or `<xref:UID?displayProperty=nameWithType>`</span></span>

   <span data-ttu-id="6a91a-220">`displayProperty` 查詢參數會產生完整的連結文字。</span><span class="sxs-lookup"><span data-stu-id="6a91a-220">The `displayProperty` query    parameter produces a fully qualified link text.</span></span> <span data-ttu-id="6a91a-221">根據預設，連結文字只會顯示成員或型別名稱。</span><span class="sxs-lookup"><span data-stu-id="6a91a-221">By default, link text shows only the member or type name.</span></span>

2. <span data-ttu-id="6a91a-222">Markdown 連結：`[link text](xref:UID)`</span><span class="sxs-lookup"><span data-stu-id="6a91a-222">Markdown link: `[link text](xref:UID)`</span></span>

   <span data-ttu-id="6a91a-223">用於您想要自訂所顯示的連結文字時。</span><span class="sxs-lookup"><span data-stu-id="6a91a-223">Use when you want to customize the link text displayed.</span></span>

<span data-ttu-id="6a91a-224">例如：</span><span class="sxs-lookup"><span data-stu-id="6a91a-224">Examples:</span></span>

- <span data-ttu-id="6a91a-225">`<xref:System.String>` 會轉譯為 [String](https://docs.microsoft.com/dotnet/api/system.string)</span><span class="sxs-lookup"><span data-stu-id="6a91a-225">`<xref:System.String>` renders as [String](https://docs.microsoft.com/dotnet/api/system.string)</span></span>
- <span data-ttu-id="6a91a-226">`<xref:System.String?displayProperty=nameWithType>` 會轉譯為 [System.String](https://docs.microsoft.com/dotnet/api/system.string)</span><span class="sxs-lookup"><span data-stu-id="6a91a-226">`<xref:System.String?displayProperty=nameWithType>` renders as [System.String](https://docs.microsoft.com/dotnet/api/system.string)</span></span>
- <span data-ttu-id="6a91a-227">`[String class](xref:System.String)` 會轉譯為 [String 類別](https://docs.microsoft.com/dotnet/api/system.string)</span><span class="sxs-lookup"><span data-stu-id="6a91a-227">`[String class](xref:System.String)` renders as [String class](https://docs.microsoft.com/dotnet/api/system.string)</span></span>

<span data-ttu-id="6a91a-228">如需使用此標記法的詳細資訊，請參閱[使用交互參照 (英文)](https://dotnet.github.io/docfx/tutorial/links_and_cross_references.html#using-cross-reference)。</span><span class="sxs-lookup"><span data-stu-id="6a91a-228">For more information about using this notation, see [Using cross reference](https://dotnet.github.io/docfx/tutorial/links_and_cross_references.html#using-cross-reference).</span></span>

<span data-ttu-id="6a91a-229">尋找 UID 的方法有兩種：</span><span class="sxs-lookup"><span data-stu-id="6a91a-229">There are two ways to find the UID:</span></span>

- <span data-ttu-id="6a91a-230">查看您要連結到的 API 頁面來源並尋找 ms.assetid 值。</span><span class="sxs-lookup"><span data-stu-id="6a91a-230">View the source for the API page you want to link to and find the ms.assetid value.</span></span> <span data-ttu-id="6a91a-231">請注意，個別的多載值不會顯示在來源中。</span><span class="sxs-lookup"><span data-stu-id="6a91a-231">Note that individual overload values are not shown in the source.</span></span>
- <span data-ttu-id="6a91a-232">使用下列工具來搜尋 UID： https://xref.docs.microsoft.com/autocomplete?text=tostring (以您嘗試尋找的 API 名稱部分取代 tostring)。</span><span class="sxs-lookup"><span data-stu-id="6a91a-232">Use the following tool to search for UIDs: https://xref.docs.microsoft.com/autocomplete?text=tostring (replace tostring with parts of the API name you're trying to find).</span></span> <span data-ttu-id="6a91a-233">此工具會在 UID 的任何部分中搜尋所提供 `text` 查詢參數。</span><span class="sxs-lookup"><span data-stu-id="6a91a-233">The tool searches for the provided `text` query parameter in any part of the UID.</span></span> <span data-ttu-id="6a91a-234">例如，您可以搜尋成員名稱 (ToString)、部分成員名稱 (ToString)、型別和成員名稱 (Double.ToString) 等。</span><span class="sxs-lookup"><span data-stu-id="6a91a-234">For example, you can search for member name (ToString), partial member name (ToStri), type and member name (Double.ToString), etc.</span></span>

<span data-ttu-id="6a91a-235">當 UID 包含特殊字元 \`、\# 或 \* 時，該 UID 值必須分別編碼為 HTML 代碼 `%60`、`%23` 和 `%2A`。</span><span class="sxs-lookup"><span data-stu-id="6a91a-235">When the UID contains the special characters \`, \# or \*, the UID value needs to be HTML encoded as `%60`, `%23` and `%2A` respectively.</span></span> <span data-ttu-id="6a91a-236">您有時會看到括弧也經編碼，但這不是必要條件。</span><span class="sxs-lookup"><span data-stu-id="6a91a-236">You'll sometimes see parentheses encoded but it's not a requirement.</span></span>

<span data-ttu-id="6a91a-237">例如：</span><span class="sxs-lookup"><span data-stu-id="6a91a-237">Examples:</span></span>

- <span data-ttu-id="6a91a-238">System.Threading.Tasks.Task\`1 會變成 `System.Threading.Tasks.Task%601`</span><span class="sxs-lookup"><span data-stu-id="6a91a-238">System.Threading.Tasks.Task\`1 becomes `System.Threading.Tasks.Task%601`</span></span>
- <span data-ttu-id="6a91a-239">System.Exception.\#ctor 會變成 `System.Exception.%23ctor`</span><span class="sxs-lookup"><span data-stu-id="6a91a-239">System.Exception.\#ctor becomes `System.Exception.%23ctor`</span></span>
- <span data-ttu-id="6a91a-240">System.Lazy\`1.\#ctor(System.Threading.LazyThreadSafetyMode) 會變成 `System.Lazy%601.%23ctor%28System.Threading.LazyThreadSafetyMode%29`</span><span class="sxs-lookup"><span data-stu-id="6a91a-240">System.Lazy\`1.\#ctor(System.Threading.LazyThreadSafetyMode) becomes  `System.Lazy%601.%23ctor%28System.Threading.LazyThreadSafetyMode%29`</span></span>

## <a name="lists"></a><span data-ttu-id="6a91a-241">清單</span><span class="sxs-lookup"><span data-stu-id="6a91a-241">Lists</span></span>

### <a name="ordered-lists"></a><span data-ttu-id="6a91a-242">排序清單</span><span class="sxs-lookup"><span data-stu-id="6a91a-242">Ordered lists</span></span>

1. <span data-ttu-id="6a91a-243">這</span><span class="sxs-lookup"><span data-stu-id="6a91a-243">This</span></span>
1. <span data-ttu-id="6a91a-244">是</span><span class="sxs-lookup"><span data-stu-id="6a91a-244">Is</span></span>
1. <span data-ttu-id="6a91a-245">一個</span><span class="sxs-lookup"><span data-stu-id="6a91a-245">An</span></span>
1. <span data-ttu-id="6a91a-246">排序</span><span class="sxs-lookup"><span data-stu-id="6a91a-246">Ordered</span></span>
1. <span data-ttu-id="6a91a-247">清單</span><span class="sxs-lookup"><span data-stu-id="6a91a-247">List</span></span>

#### <a name="ordered-list-with-an-embedded-list"></a><span data-ttu-id="6a91a-248">包含內嵌清單的排序清單</span><span class="sxs-lookup"><span data-stu-id="6a91a-248">Ordered list with an embedded list</span></span>

1. <span data-ttu-id="6a91a-249">這裡</span><span class="sxs-lookup"><span data-stu-id="6a91a-249">Here</span></span>
1. <span data-ttu-id="6a91a-250">有</span><span class="sxs-lookup"><span data-stu-id="6a91a-250">comes</span></span>
1. <span data-ttu-id="6a91a-251">一個</span><span class="sxs-lookup"><span data-stu-id="6a91a-251">an</span></span>
1. <span data-ttu-id="6a91a-252">內嵌</span><span class="sxs-lookup"><span data-stu-id="6a91a-252">embedded</span></span>
    1. <span data-ttu-id="6a91a-253">Miss Scarlett</span><span class="sxs-lookup"><span data-stu-id="6a91a-253">Miss Scarlett</span></span>
    1. <span data-ttu-id="6a91a-254">Professor Plum</span><span class="sxs-lookup"><span data-stu-id="6a91a-254">Professor Plum</span></span>
1. <span data-ttu-id="6a91a-255">排序</span><span class="sxs-lookup"><span data-stu-id="6a91a-255">ordered</span></span>
1. <span data-ttu-id="6a91a-256">清單</span><span class="sxs-lookup"><span data-stu-id="6a91a-256">list</span></span>

### <a name="unordered-lists"></a><span data-ttu-id="6a91a-257">未排序清單</span><span class="sxs-lookup"><span data-stu-id="6a91a-257">Unordered Lists</span></span>

- <span data-ttu-id="6a91a-258">這個</span><span class="sxs-lookup"><span data-stu-id="6a91a-258">This</span></span>
- <span data-ttu-id="6a91a-259">是</span><span class="sxs-lookup"><span data-stu-id="6a91a-259">is</span></span>
- <span data-ttu-id="6a91a-260">一個</span><span class="sxs-lookup"><span data-stu-id="6a91a-260">a</span></span>
- <span data-ttu-id="6a91a-261">項目符號</span><span class="sxs-lookup"><span data-stu-id="6a91a-261">bulleted</span></span>
- <span data-ttu-id="6a91a-262">清單</span><span class="sxs-lookup"><span data-stu-id="6a91a-262">list</span></span>

#### <a name="unordered-list-with-an-embedded-list"></a><span data-ttu-id="6a91a-263">包含內嵌清單的未排序清單</span><span class="sxs-lookup"><span data-stu-id="6a91a-263">Unordered list with an embedded list</span></span>

- <span data-ttu-id="6a91a-264">這個</span><span class="sxs-lookup"><span data-stu-id="6a91a-264">This</span></span>
- <span data-ttu-id="6a91a-265">項目符號</span><span class="sxs-lookup"><span data-stu-id="6a91a-265">bulleted</span></span>
- <span data-ttu-id="6a91a-266">清單</span><span class="sxs-lookup"><span data-stu-id="6a91a-266">list</span></span>
  - <span data-ttu-id="6a91a-267">Mrs. Peacock</span><span class="sxs-lookup"><span data-stu-id="6a91a-267">Mrs. Peacock</span></span>
  - <span data-ttu-id="6a91a-268">Mr. Green</span><span class="sxs-lookup"><span data-stu-id="6a91a-268">Mr. Green</span></span>
- <span data-ttu-id="6a91a-269">包含</span><span class="sxs-lookup"><span data-stu-id="6a91a-269">contains</span></span>
- <span data-ttu-id="6a91a-270">另一個</span><span class="sxs-lookup"><span data-stu-id="6a91a-270">other</span></span>
  1. <span data-ttu-id="6a91a-271">Colonel Mustard</span><span class="sxs-lookup"><span data-stu-id="6a91a-271">Colonel Mustard</span></span>
  1. <span data-ttu-id="6a91a-272">Mrs. White</span><span class="sxs-lookup"><span data-stu-id="6a91a-272">Mrs. White</span></span>
- <span data-ttu-id="6a91a-273">清單</span><span class="sxs-lookup"><span data-stu-id="6a91a-273">lists</span></span>

## <a name="horizontal-rule"></a><span data-ttu-id="6a91a-274">水平線</span><span class="sxs-lookup"><span data-stu-id="6a91a-274">Horizontal rule</span></span>

---

## <a name="tables"></a><span data-ttu-id="6a91a-275">資料表</span><span class="sxs-lookup"><span data-stu-id="6a91a-275">Tables</span></span>

| <span data-ttu-id="6a91a-276">資料表</span><span class="sxs-lookup"><span data-stu-id="6a91a-276">Tables</span></span>        | <span data-ttu-id="6a91a-277">很</span><span class="sxs-lookup"><span data-stu-id="6a91a-277">Are</span></span>           | <span data-ttu-id="6a91a-278">酷</span><span class="sxs-lookup"><span data-stu-id="6a91a-278">Cool</span></span>  |
| ------------- |:-------------:| -----:|
| <span data-ttu-id="6a91a-279">欄 3 為</span><span class="sxs-lookup"><span data-stu-id="6a91a-279">col 3 is</span></span>      | <span data-ttu-id="6a91a-280">靠右對齊</span><span class="sxs-lookup"><span data-stu-id="6a91a-280">right-aligned</span></span> | <span data-ttu-id="6a91a-281">$1600</span><span class="sxs-lookup"><span data-stu-id="6a91a-281">$1600</span></span> |
| <span data-ttu-id="6a91a-282">欄 2 為</span><span class="sxs-lookup"><span data-stu-id="6a91a-282">col 2 is</span></span>      | <span data-ttu-id="6a91a-283">置中</span><span class="sxs-lookup"><span data-stu-id="6a91a-283">centered</span></span>      |   <span data-ttu-id="6a91a-284">$12</span><span class="sxs-lookup"><span data-stu-id="6a91a-284">$12</span></span> |
| <span data-ttu-id="6a91a-285">欄 1 為預設</span><span class="sxs-lookup"><span data-stu-id="6a91a-285">col 1 is default</span></span> | <span data-ttu-id="6a91a-286">靠左對齊</span><span class="sxs-lookup"><span data-stu-id="6a91a-286">left-aligned</span></span>     |    <span data-ttu-id="6a91a-287">$1</span><span class="sxs-lookup"><span data-stu-id="6a91a-287">$1</span></span> |

<span data-ttu-id="6a91a-288">您可以使用 [Markdown 表格產生工具 (英文)](https://www.tablesgenerator.com/markdown_tables) 來輕鬆產生表格。</span><span class="sxs-lookup"><span data-stu-id="6a91a-288">You can use a [Markdown table generator tool](https://www.tablesgenerator.com/markdown_tables) to help creating them more easily.</span></span>

## <a name="code"></a><span data-ttu-id="6a91a-289">程式碼</span><span class="sxs-lookup"><span data-stu-id="6a91a-289">Code</span></span>

<span data-ttu-id="6a91a-290">包含程式碼的最佳方法是加入實際範例的程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="6a91a-290">The best way to include code is to include snippets from a working sample.</span></span> <span data-ttu-id="6a91a-291">請遵循[參與指南](../CONTRIBUTING.md#contributing-to-samples)中的指示來建立範例。</span><span class="sxs-lookup"><span data-stu-id="6a91a-291">Create your sample following the instructions in the [contributing guide](../CONTRIBUTING.md#contributing-to-samples).</span></span>

<span data-ttu-id="6a91a-292">您可以使用下列語法來包含程式碼：</span><span class="sxs-lookup"><span data-stu-id="6a91a-292">You can include the code using the following syntax:</span></span>

```markdown
[!code-<language>[<name>](<pathToFile><queryoption><queryoptionvalue>)]
```

* <span data-ttu-id="6a91a-293">`-<language>` (「選擇性」  但「建議使用」  )</span><span class="sxs-lookup"><span data-stu-id="6a91a-293">`-<language>` (*optional* but *recommended*)</span></span>
  * <span data-ttu-id="6a91a-294">所參考程式碼片段的語言。</span><span class="sxs-lookup"><span data-stu-id="6a91a-294">Language of the code snippet being referenced.</span></span> <span data-ttu-id="6a91a-295">如需支援值的清單，請參閱[支援的語言](#supported-languages)。</span><span class="sxs-lookup"><span data-stu-id="6a91a-295">For a list of supported values, see [Supported languages](#supported-languages).</span></span>

* <span data-ttu-id="6a91a-296">`<name>` (選擇性  )</span><span class="sxs-lookup"><span data-stu-id="6a91a-296">`<name>` (*optional*)</span></span>
  * <span data-ttu-id="6a91a-297">程式碼片段的名稱。</span><span class="sxs-lookup"><span data-stu-id="6a91a-297">Name for the code snippet.</span></span> <span data-ttu-id="6a91a-298">它對輸出 HTML 沒有任何影響，但您可以用它來改善 Markdown 原始程式的可讀性。</span><span class="sxs-lookup"><span data-stu-id="6a91a-298">It doesn’t have any impact on the output HTML, but you can use it to improve the readability of your Markdown source.</span></span>

* <span data-ttu-id="6a91a-299">`<pathToFile>` (強制  )</span><span class="sxs-lookup"><span data-stu-id="6a91a-299">`<pathToFile>` (*mandatory*)</span></span>
  * <span data-ttu-id="6a91a-300">檔案系統中的相對路徑，表示要參考的程式碼片段檔案。</span><span class="sxs-lookup"><span data-stu-id="6a91a-300">Relative path in the file system that indicates the code snippet file to reference.</span></span>

* <span data-ttu-id="6a91a-301">`<queryoption>` 和 `<queryoptionvalue>` (選擇性  )</span><span class="sxs-lookup"><span data-stu-id="6a91a-301">`<queryoption>` and `<queryoptionvalue>` (*optional*)</span></span>
  * <span data-ttu-id="6a91a-302">一起使用以指定從檔案取出程式碼的方式：</span><span class="sxs-lookup"><span data-stu-id="6a91a-302">Used together to specify how the code should be retrieved from the file:</span></span>
    * <span data-ttu-id="6a91a-303">`#`：`#L{startlinenumber}-L{endlinenumber}` (行範圍) 「或」  `#{tagname}` (標籤名稱)。</span><span class="sxs-lookup"><span data-stu-id="6a91a-303">`#`:  `#L{startlinenumber}-L{endlinenumber}` (line range) *or* `#{tagname}` (tag name).</span></span>
    <span data-ttu-id="6a91a-304">不建議使用行號，因為此功能不盡完善。</span><span class="sxs-lookup"><span data-stu-id="6a91a-304">We discourage the use of line numbers because they are very brittle.</span></span> <span data-ttu-id="6a91a-305">標籤名稱是參考程式碼片段的慣用方式。</span><span class="sxs-lookup"><span data-stu-id="6a91a-305">Tag name is the preferred way of referencing code snippets.</span></span>
    * <span data-ttu-id="6a91a-306">`range`：`?range=1,3-5` 行範圍。</span><span class="sxs-lookup"><span data-stu-id="6a91a-306">`range`: `?range=1,3-5` A range of lines.</span></span> <span data-ttu-id="6a91a-307">這個範例包含第 1、3、4 和 5 行。</span><span class="sxs-lookup"><span data-stu-id="6a91a-307">This example includes lines 1, 3, 4, and 5.</span></span>
    * <span data-ttu-id="6a91a-308">`dedent`：`?dedent=8` 以數個空格將行縮排，在此案例中為 8 個空格。</span><span class="sxs-lookup"><span data-stu-id="6a91a-308">`dedent`: `?dedent=8` Dedents the lines by a number of spaces--in this case, 8.</span></span> <span data-ttu-id="6a91a-309">這可以與 `range` 和其他查詢選項結合，以選取檔案的部分行。</span><span class="sxs-lookup"><span data-stu-id="6a91a-309">This can be combined with the `range` and other query options that select a subset of the lines of a file.</span></span>
    * <span data-ttu-id="6a91a-310">`outdent`：`?outdent=8` 以數個空格反轉行的縮排，在此案例中為 8 個空格。</span><span class="sxs-lookup"><span data-stu-id="6a91a-310">`outdent`: `?outdent=8` Reverses the indent of the lines by a number of spaces--in this case, 8.</span></span> <span data-ttu-id="6a91a-311">這可以與 `range` 和其他查詢選項結合，以選取檔案的部分行。</span><span class="sxs-lookup"><span data-stu-id="6a91a-311">This can be combined with `range` and other query options that select a subset of the lines of a file.</span></span>

<span data-ttu-id="6a91a-312">我們建議您盡可能使用標籤名稱選項。</span><span class="sxs-lookup"><span data-stu-id="6a91a-312">We recommend using the tag name option whenever possible.</span></span> <span data-ttu-id="6a91a-313">標籤名稱是區域或程式碼註解的名稱，其格式如同在原始程式碼中出現的 `Snippettagname`。</span><span class="sxs-lookup"><span data-stu-id="6a91a-313">The tag name is the name of a region or of a code comment in the format of `Snippettagname` present in the source code.</span></span> <span data-ttu-id="6a91a-314">下列範例示範如何參考標籤名稱 `1`：</span><span class="sxs-lookup"><span data-stu-id="6a91a-314">The following example shows how to refer to the tag name `1`:</span></span>

```markdown
[!code-csharp[csrefKeyword#1](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]
```

<span data-ttu-id="6a91a-315">您可以看到程式碼片段標籤在[此原始程式檔案](https://github.com/dotnet/samples/blob/master/snippets/csharp/language-reference/keywords/throw/throw-1.cs)中的結構。</span><span class="sxs-lookup"><span data-stu-id="6a91a-315">And you can see how the snippet tags are structured in [this source file](https://github.com/dotnet/samples/blob/master/snippets/csharp/language-reference/keywords/throw/throw-1.cs).</span></span> <span data-ttu-id="6a91a-316">如需各語言程式碼片段原始程式檔中標籤名稱表示的詳細資料，請參閱 [DocFX 指導方針](https://dotnet.github.io/docfx/spec/docfx_flavored_markdown.html#tag-name-representation-in-code-snippet-source-file)。</span><span class="sxs-lookup"><span data-stu-id="6a91a-316">For details about tag name representation in code snippet source files by language, see the [DocFX guidelines](https://dotnet.github.io/docfx/spec/docfx_flavored_markdown.html#tag-name-representation-in-code-snippet-source-file).</span></span>

<span data-ttu-id="6a91a-317">包含來自完整程式的程式碼片段可確保所有程式碼都經過我們的持續整合 (CI) 系統。</span><span class="sxs-lookup"><span data-stu-id="6a91a-317">Including snippets from full programs ensures that all code runs through our Continuous Integration (CI) system.</span></span> <span data-ttu-id="6a91a-318">不過，如果您需要顯示一些造成編譯時間或執行階段錯誤的程式碼，您可以使用內嵌程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="6a91a-318">However, if you need to show something that causes compile time or runtime errors, you can use inline code blocks.</span></span>

### <a name="inline-code-blocks-with-language-identifier"></a><span data-ttu-id="6a91a-319">具有語言識別碼的內嵌程式碼區塊</span><span class="sxs-lookup"><span data-stu-id="6a91a-319">Inline code blocks with language identifier</span></span>

<span data-ttu-id="6a91a-320">使用「三個反引號 (\`\`\`) + 語言識別碼」，來在程式碼區塊套用該語言的語法著色。</span><span class="sxs-lookup"><span data-stu-id="6a91a-320">Use three backticks (\`\`\`) + a language ID to apply language-specific color coding to a code block.</span></span> <span data-ttu-id="6a91a-321">以下是支援的語言清單，其中顯示每個語言識別碼的 Markdown 標籤。</span><span class="sxs-lookup"><span data-stu-id="6a91a-321">Here is the list of supported languages showing the markdown label for each language ID.</span></span>

#### <a name="supported-languages"></a><span data-ttu-id="6a91a-322">支援的語言</span><span class="sxs-lookup"><span data-stu-id="6a91a-322">Supported languages</span></span>

|<span data-ttu-id="6a91a-323">名稱</span><span class="sxs-lookup"><span data-stu-id="6a91a-323">Name</span></span>|<span data-ttu-id="6a91a-324">Markdown 標籤</span><span class="sxs-lookup"><span data-stu-id="6a91a-324">Markdown label</span></span>|
|-----|-------|
|<span data-ttu-id="6a91a-325">ASP.NET 與 C#</span><span class="sxs-lookup"><span data-stu-id="6a91a-325">ASP.NET with C#</span></span>|<span data-ttu-id="6a91a-326">aspx-csharp</span><span class="sxs-lookup"><span data-stu-id="6a91a-326">aspx-csharp</span></span>|
|<span data-ttu-id="6a91a-327">ASP.NET 與 VB</span><span class="sxs-lookup"><span data-stu-id="6a91a-327">ASP.NET with VB</span></span>|<span data-ttu-id="6a91a-328">aspx-vb</span><span class="sxs-lookup"><span data-stu-id="6a91a-328">aspx-vb</span></span>|
|<span data-ttu-id="6a91a-329">Azure CLI</span><span class="sxs-lookup"><span data-stu-id="6a91a-329">Azure CLI</span></span>|<span data-ttu-id="6a91a-330">azurecli</span><span class="sxs-lookup"><span data-stu-id="6a91a-330">azurecli</span></span>|
|<span data-ttu-id="6a91a-331">AzCopy</span><span class="sxs-lookup"><span data-stu-id="6a91a-331">AzCopy</span></span>|<span data-ttu-id="6a91a-332">azcopy</span><span class="sxs-lookup"><span data-stu-id="6a91a-332">azcopy</span></span>|
|<span data-ttu-id="6a91a-333">C++</span><span class="sxs-lookup"><span data-stu-id="6a91a-333">C++</span></span>|<span data-ttu-id="6a91a-334">cpp</span><span class="sxs-lookup"><span data-stu-id="6a91a-334">cpp</span></span>|
|<span data-ttu-id="6a91a-335">C#</span><span class="sxs-lookup"><span data-stu-id="6a91a-335">C#</span></span>|<span data-ttu-id="6a91a-336">csharp</span><span class="sxs-lookup"><span data-stu-id="6a91a-336">csharp</span></span>|
|<span data-ttu-id="6a91a-337">瀏覽器中的 C#</span><span class="sxs-lookup"><span data-stu-id="6a91a-337">C# in browser</span></span>|<span data-ttu-id="6a91a-338">csharp-interactive</span><span class="sxs-lookup"><span data-stu-id="6a91a-338">csharp-interactive</span></span>|
|<span data-ttu-id="6a91a-339">主控台</span><span class="sxs-lookup"><span data-stu-id="6a91a-339">Console</span></span>|<span data-ttu-id="6a91a-340">主控台</span><span class="sxs-lookup"><span data-stu-id="6a91a-340">console</span></span>|
|<span data-ttu-id="6a91a-341">F#</span><span class="sxs-lookup"><span data-stu-id="6a91a-341">F#</span></span>|<span data-ttu-id="6a91a-342">fsharp</span><span class="sxs-lookup"><span data-stu-id="6a91a-342">fsharp</span></span>|
|<span data-ttu-id="6a91a-343">Java</span><span class="sxs-lookup"><span data-stu-id="6a91a-343">Java</span></span>|<span data-ttu-id="6a91a-344">java</span><span class="sxs-lookup"><span data-stu-id="6a91a-344">java</span></span>|
|<span data-ttu-id="6a91a-345">JavaScript</span><span class="sxs-lookup"><span data-stu-id="6a91a-345">JavaScript</span></span>|<span data-ttu-id="6a91a-346">javascript</span><span class="sxs-lookup"><span data-stu-id="6a91a-346">javascript</span></span>|
|<span data-ttu-id="6a91a-347">JSON</span><span class="sxs-lookup"><span data-stu-id="6a91a-347">JSON</span></span>|<span data-ttu-id="6a91a-348">json</span><span class="sxs-lookup"><span data-stu-id="6a91a-348">json</span></span>|
|<span data-ttu-id="6a91a-349">NodeJS</span><span class="sxs-lookup"><span data-stu-id="6a91a-349">NodeJS</span></span>|<span data-ttu-id="6a91a-350">nodejs</span><span class="sxs-lookup"><span data-stu-id="6a91a-350">nodejs</span></span>|
|<span data-ttu-id="6a91a-351">Objective-C</span><span class="sxs-lookup"><span data-stu-id="6a91a-351">Objective-C</span></span>|<span data-ttu-id="6a91a-352">objc</span><span class="sxs-lookup"><span data-stu-id="6a91a-352">objc</span></span>|
|<span data-ttu-id="6a91a-353">PHP</span><span class="sxs-lookup"><span data-stu-id="6a91a-353">PHP</span></span>|<span data-ttu-id="6a91a-354">php</span><span class="sxs-lookup"><span data-stu-id="6a91a-354">php</span></span>|
|<span data-ttu-id="6a91a-355">PowerShell</span><span class="sxs-lookup"><span data-stu-id="6a91a-355">PowerShell</span></span>|<span data-ttu-id="6a91a-356">powershell</span><span class="sxs-lookup"><span data-stu-id="6a91a-356">powershell</span></span>|
|<span data-ttu-id="6a91a-357">Python</span><span class="sxs-lookup"><span data-stu-id="6a91a-357">Python</span></span>|<span data-ttu-id="6a91a-358">Python</span><span class="sxs-lookup"><span data-stu-id="6a91a-358">python</span></span>|
|<span data-ttu-id="6a91a-359">Ruby</span><span class="sxs-lookup"><span data-stu-id="6a91a-359">Ruby</span></span>|<span data-ttu-id="6a91a-360">ruby</span><span class="sxs-lookup"><span data-stu-id="6a91a-360">ruby</span></span>|
|<span data-ttu-id="6a91a-361">SQL</span><span class="sxs-lookup"><span data-stu-id="6a91a-361">SQL</span></span>|<span data-ttu-id="6a91a-362">sql</span><span class="sxs-lookup"><span data-stu-id="6a91a-362">sql</span></span>|
|<span data-ttu-id="6a91a-363">Swift</span><span class="sxs-lookup"><span data-stu-id="6a91a-363">Swift</span></span>|<span data-ttu-id="6a91a-364">swift</span><span class="sxs-lookup"><span data-stu-id="6a91a-364">swift</span></span>|
|<span data-ttu-id="6a91a-365">VB</span><span class="sxs-lookup"><span data-stu-id="6a91a-365">VB</span></span>|<span data-ttu-id="6a91a-366">vb</span><span class="sxs-lookup"><span data-stu-id="6a91a-366">vb</span></span>|
|<span data-ttu-id="6a91a-367">XAML</span><span class="sxs-lookup"><span data-stu-id="6a91a-367">XAML</span></span>|<span data-ttu-id="6a91a-368">xaml</span><span class="sxs-lookup"><span data-stu-id="6a91a-368">xaml</span></span>|
|<span data-ttu-id="6a91a-369">XML</span><span class="sxs-lookup"><span data-stu-id="6a91a-369">XML</span></span>|<span data-ttu-id="6a91a-370">xml</span><span class="sxs-lookup"><span data-stu-id="6a91a-370">xml</span></span>|

<span data-ttu-id="6a91a-371">`csharp-interactive` 名稱會指定 C# 語言，以及從瀏覽器執行範例的能力。</span><span class="sxs-lookup"><span data-stu-id="6a91a-371">The `csharp-interactive` name specifies the C# language, and the ability to run the samples from the browser.</span></span> <span data-ttu-id="6a91a-372">這些程式碼片段會在 Docker 容器中進行編譯和執行，而該程式執行結果會顯示在使用者的瀏覽器視窗中。</span><span class="sxs-lookup"><span data-stu-id="6a91a-372">These snippets are compiled and executed in a Docker container, and the results of that program execution are displayed in the user's browser window.</span></span>

<span data-ttu-id="6a91a-373">下列程式碼區塊範例分別使用 C# 語言識別碼 (\`\`\`csharp)、Python 語言識別碼 (\`\`\`python) 和 PowerShell 語言識別碼 (\`\`\`powershell)。</span><span class="sxs-lookup"><span data-stu-id="6a91a-373">The following are examples of code blocks using the language IDs for C# (\`\`\`csharp), Python (\`\`\`python), and PowerShell (\`\`\`powershell).</span></span>

##### <a name="c9839"></a><span data-ttu-id="6a91a-374">C&#9839;</span><span class="sxs-lookup"><span data-stu-id="6a91a-374">C&#9839;</span></span>

```csharp
using System;
namespace HelloWorld
{
    class Hello
    {
        static void Main()
        {
            Console.WriteLine("Hello World!");

            // Keep the console window open in debug mode.
            Console.WriteLine("Press any key to exit.");
            Console.ReadKey();
        }
    }
}
```

#### <a name="python"></a><span data-ttu-id="6a91a-375">Python</span><span class="sxs-lookup"><span data-stu-id="6a91a-375">Python</span></span>

```python
friends = ['john', 'pat', 'gary', 'michael']
for i, name in enumerate(friends):
    print "iteration {iteration} is {name}".format(iteration=i, name=name)
```

#### <a name="powershell"></a><span data-ttu-id="6a91a-376">PowerShell</span><span class="sxs-lookup"><span data-stu-id="6a91a-376">PowerShell</span></span>

```powershell
Clear-Host
$Directory = "C:\Windows\"
$Files = Get-Childitem $Directory -recurse -Include *.log `
-ErrorAction SilentlyContinue
```

### <a name="generic-code-block"></a><span data-ttu-id="6a91a-377">一般程式碼區快</span><span class="sxs-lookup"><span data-stu-id="6a91a-377">Generic code block</span></span>

<span data-ttu-id="6a91a-378">使用三個反引號 (&#96;&#96;&#96;) 撰寫一般程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="6a91a-378">Use three backticks (&#96;&#96;&#96;) for generic code block coding.</span></span>

> <span data-ttu-id="6a91a-379">建議的做法是搭配語言識別碼使用程式碼區塊 (如上節所述)，以確保語法在文件網站上適當地醒目顯示。</span><span class="sxs-lookup"><span data-stu-id="6a91a-379">The recommended approach is to use code blocks with language identifiers as explained in the previous section to ensure the proper syntax highlighting in the documentation site.</span></span> <span data-ttu-id="6a91a-380">必要時才使用一般程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="6a91a-380">Use generic code blocks only when necessary.</span></span>

```
function fancyAlert(arg) {
    if(arg) {
        $.docs({div:'#foo'})
    }
}
```

## <a name="blockquotes"></a><span data-ttu-id="6a91a-381">引文</span><span class="sxs-lookup"><span data-stu-id="6a91a-381">Blockquotes</span></span>

> <span data-ttu-id="6a91a-382">The drought had lasted now for ten million years, and the reign of the terrible lizards had long since ended.</span><span class="sxs-lookup"><span data-stu-id="6a91a-382">The drought had lasted now for ten million years, and the reign of the terrible lizards had long since ended.</span></span> <span data-ttu-id="6a91a-383">Here on the Equator, in the continent which would one day be known as Africa, the battle for existence had reached a new climax of ferocity, and the victor was not yet in sight.</span><span class="sxs-lookup"><span data-stu-id="6a91a-383">Here on the Equator, in the continent which would one day be known as Africa, the battle for existence had reached a new climax of ferocity, and the victor was not yet in sight.</span></span> <span data-ttu-id="6a91a-384">In this barren and desiccated land, only the small or the swift or the fierce could flourish, or even hope to survive.</span><span class="sxs-lookup"><span data-stu-id="6a91a-384">In this barren and desiccated land, only the small or the swift or the fierce could flourish, or even hope to survive.</span></span>

## <a name="images"></a><span data-ttu-id="6a91a-385">影像</span><span class="sxs-lookup"><span data-stu-id="6a91a-385">Images</span></span>

### <a name="static-image-or-animated-gif"></a><span data-ttu-id="6a91a-386">靜態影像或動畫 GIF</span><span class="sxs-lookup"><span data-stu-id="6a91a-386">Static Image or Animated gif</span></span>

```markdown
![this is the alt text](../images/Logo_DotNet.png)
```

![這是替代文字](../images/Logo_DotNet.png)

### <a name="linked-image"></a><span data-ttu-id="6a91a-388">連結影像</span><span class="sxs-lookup"><span data-stu-id="6a91a-388">Linked Image</span></span>

```markdown
[![alt text for linked image](../images/Logo_DotNet.png)](https://dot.net)
```

<span data-ttu-id="6a91a-389">[![連結影像的替代文字](../images/Logo_DotNet.png)](https://dot.net)</span><span class="sxs-lookup"><span data-stu-id="6a91a-389">[![alt text for linked image](../images/Logo_DotNet.png)](https://dot.net)</span></span>

## <a name="videos"></a><span data-ttu-id="6a91a-390">視訊</span><span class="sxs-lookup"><span data-stu-id="6a91a-390">Videos</span></span>

<span data-ttu-id="6a91a-391">目前，您可以使用下列語法內嵌 Channel 9 和 YouTube 影片：</span><span class="sxs-lookup"><span data-stu-id="6a91a-391">Currently, you can embed both Channel 9 and YouTube videos with the following syntax:</span></span>

### <a name="channel-9"></a><span data-ttu-id="6a91a-392">Channel 9</span><span class="sxs-lookup"><span data-stu-id="6a91a-392">Channel 9</span></span>

```markdown
> [!VIDEO <channel9_video_link>]
```

<span data-ttu-id="6a91a-393">若要取得影片的正確 URL，請選取視訊框架下的 [內嵌]  索引標籤，然後從 `<iframe>` 元素複製 URL。</span><span class="sxs-lookup"><span data-stu-id="6a91a-393">To get the video's correct URL, select the **Embed** tab below the video frame, and copy the URL from the `<iframe>` element.</span></span> <span data-ttu-id="6a91a-394">例如：</span><span class="sxs-lookup"><span data-stu-id="6a91a-394">For example:</span></span>

```markdown
> [!VIDEO https://channel9.msdn.com/Blogs/dotnet/NET-Core-20-Released/player]
```

### <a name="youtube"></a><span data-ttu-id="6a91a-395">YouTube</span><span class="sxs-lookup"><span data-stu-id="6a91a-395">YouTube</span></span>

<span data-ttu-id="6a91a-396">若要取得影片的正確 URL，請在影片上按一下滑鼠右鍵、選取 [複製內嵌程式碼]  ，然後從 `<iframe>` 元素複製 URL。</span><span class="sxs-lookup"><span data-stu-id="6a91a-396">To get the video's correct URL, right-click on the video, select **Copy Embed Code**, and copy the URL from the `<iframe>` element.</span></span>

```markdown
> [!VIDEO <youtube_video_link>]
```

<span data-ttu-id="6a91a-397">例如：</span><span class="sxs-lookup"><span data-stu-id="6a91a-397">For example:</span></span>

```markdown
> [!VIDEO https://www.youtube.com/embed/Q2mMbjw6cLA]
```

## <a name="docsmicrosoft-extensions"></a><span data-ttu-id="6a91a-398">docs.microsoft 延伸模組</span><span class="sxs-lookup"><span data-stu-id="6a91a-398">docs.microsoft extensions</span></span>

<span data-ttu-id="6a91a-399">docs.microsoft 為 GitHub Flavored Markdown 提供幾個額外的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="6a91a-399">docs.microsoft provides a few additional extensions to GitHub Flavored Markdown.</span></span>

### <a name="alerts"></a><span data-ttu-id="6a91a-400">警示</span><span class="sxs-lookup"><span data-stu-id="6a91a-400">Alerts</span></span>

<span data-ttu-id="6a91a-401">請務必使用下列的警示樣式，這樣它們才能在文件網站中轉譯為適當的樣式。</span><span class="sxs-lookup"><span data-stu-id="6a91a-401">It's important to use the following alert styles so they render with the proper style in the documentation site.</span></span> <span data-ttu-id="6a91a-402">不過，GitHub 的轉譯引擎無法分辨這些樣式。</span><span class="sxs-lookup"><span data-stu-id="6a91a-402">However, the rendering engine on GitHub doesn't diferentiate them.</span></span>

```markdown
> [!NOTE]
> Information the user should notice even if skimming.

> [!TIP]
> Optional information to help a user be more successful.

> [!IMPORTANT]
> Essential information required for user success.

> [!CAUTION]
> Negative potential consequences of an action.

> [!WARNING]
> Dangerous certain consequences of an action.
```

<span data-ttu-id="6a91a-403">它們轉譯之後看起來像這樣：![警示樣式](../images/alerts.png)</span><span class="sxs-lookup"><span data-stu-id="6a91a-403">And they'll render like this: ![Alert styles](../images/alerts.png)</span></span>

### <a name="includes"></a><span data-ttu-id="6a91a-404">包括</span><span class="sxs-lookup"><span data-stu-id="6a91a-404">Includes</span></span>

<span data-ttu-id="6a91a-405">您可以使用 include，將一個檔案的 Markdown 內嵌至另一個檔案。</span><span class="sxs-lookup"><span data-stu-id="6a91a-405">You can embed the Markdown of one file into another using an include.</span></span>

[!INCLUDE[sample include file](../includes/sampleinclude.md)]

### <a name="checked-lists"></a><span data-ttu-id="6a91a-406">核取清單</span><span class="sxs-lookup"><span data-stu-id="6a91a-406">Checked lists</span></span>

<span data-ttu-id="6a91a-407">有適用於清單的自訂樣式。</span><span class="sxs-lookup"><span data-stu-id="6a91a-407">A custom style is available for lists.</span></span> <span data-ttu-id="6a91a-408">您可以轉譯具有綠色核取記號的清單。</span><span class="sxs-lookup"><span data-stu-id="6a91a-408">You can render lists with green check marks.</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="6a91a-409">如何建立 .NET Core 應用程式</span><span class="sxs-lookup"><span data-stu-id="6a91a-409">How to create a .NET Core app</span></span>
> * <span data-ttu-id="6a91a-410">如何新增 Microsoft.XmlSerializer.Generator 套件的參考</span><span class="sxs-lookup"><span data-stu-id="6a91a-410">How to add a reference to the Microsoft.XmlSerializer.Generator package</span></span>
> * <span data-ttu-id="6a91a-411">如何編輯 MyApp.csproj 以新增相依性</span><span class="sxs-lookup"><span data-stu-id="6a91a-411">How to edit your MyApp.csproj to add dependencies</span></span>
> * <span data-ttu-id="6a91a-412">如何新增類別和 XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="6a91a-412">How to add a class and an XmlSerializer</span></span>
> * <span data-ttu-id="6a91a-413">如何建置和執行應用程式</span><span class="sxs-lookup"><span data-stu-id="6a91a-413">How to build and run the application</span></span>

<span data-ttu-id="6a91a-414">您可以在 [.NET Core 文件](https://docs.microsoft.com/dotnet/core/additional-tools/xml-serializer-generator)中看到核取清單的實際範例。</span><span class="sxs-lookup"><span data-stu-id="6a91a-414">You can see an example of checked lists in action in the [.NET Core docs](https://docs.microsoft.com/dotnet/core/additional-tools/xml-serializer-generator).</span></span>

### <a name="buttons"></a><span data-ttu-id="6a91a-415">按鈕</span><span class="sxs-lookup"><span data-stu-id="6a91a-415">Buttons</span></span>

> [!div class="button"]
> [<span data-ttu-id="6a91a-416">按鈕連結</span><span class="sxs-lookup"><span data-stu-id="6a91a-416">button links</span></span>](../docs/core/index.md)

<span data-ttu-id="6a91a-417">您可以在 [Visual Studio 文件](https://docs.microsoft.com/visualstudio/install/install-visual-studio#step-2---download-visual-studio)中看到按鈕的實際範例。</span><span class="sxs-lookup"><span data-stu-id="6a91a-417">You can see an example of buttons in action in the [Visual Studio docs](https://docs.microsoft.com/visualstudio/install/install-visual-studio#step-2---download-visual-studio).</span></span>

### <a name="selectors"></a><span data-ttu-id="6a91a-418">選取器</span><span class="sxs-lookup"><span data-stu-id="6a91a-418">Selectors</span></span>

> [!div class="op_single_selector"]
- [<span data-ttu-id="6a91a-419">macOS</span><span class="sxs-lookup"><span data-stu-id="6a91a-419">macOS</span></span>](../docs/core/tutorials/using-on-macos.md)
- [<span data-ttu-id="6a91a-420">Windows</span><span class="sxs-lookup"><span data-stu-id="6a91a-420">Windows</span></span>](../docs/core/tutorials/with-visual-studio.md)

<span data-ttu-id="6a91a-421">您可以在 [Azure 文件](https://docs.microsoft.com/azure/expressroute/expressroute-howto-circuit-classic)中看到選取器的實際範例。</span><span class="sxs-lookup"><span data-stu-id="6a91a-421">You can see an example of selectors in action at the [Azure docs](https://docs.microsoft.com/azure/expressroute/expressroute-howto-circuit-classic).</span></span>

### <a name="step-by-steps"></a><span data-ttu-id="6a91a-422">逐步執行</span><span class="sxs-lookup"><span data-stu-id="6a91a-422">Step-By-Steps</span></span>

>[!div class="step-by-step"]
>[上一頁](../docs/csharp/expression-trees-interpreting.md)
>[下一頁](../docs/csharp/expression-trees-translating.md)

<span data-ttu-id="6a91a-424">您可以在 [C# 指南](https://docs.microsoft.com/dotnet/csharp/tour-of-csharp/program-structure)中看到逐步執行的實際範例。</span><span class="sxs-lookup"><span data-stu-id="6a91a-424">You can see an example of step-by-steps in action at the [C# Guide](https://docs.microsoft.com/dotnet/csharp/tour-of-csharp/program-structure).</span></span>
