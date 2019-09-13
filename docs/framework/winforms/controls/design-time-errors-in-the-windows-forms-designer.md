---
title: Windows Form 設計工具中的設計階段錯誤
ms.date: 09/09/2019
f1_keywords:
- DTELErrorList
- WhyDTELPage
helpviewer_keywords:
- errors [Windows Forms Designer]
- design-time errors [Windows Forms Designer]
ms.assetid: ad408380-825a-46d8-9a4a-531b130b88ce
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 96ec50e5d3aca2aa24d68d565a35ec7687df2a2e
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70893263"
---
# <a name="windows-forms-designer-error-page"></a><span data-ttu-id="e1e99-102">Windows Form 設計工具錯誤頁面</span><span class="sxs-lookup"><span data-stu-id="e1e99-102">Windows Forms Designer error page</span></span>

<span data-ttu-id="e1e99-103">如果 Windows Form 設計工具因程式碼中的錯誤、協力廠商元件或其他位置而無法載入時，您會看到錯誤頁面，而不是設計工具。</span><span class="sxs-lookup"><span data-stu-id="e1e99-103">If the Windows Forms Designer fails to load due to an error in your code, in a third-party component, or elsewhere, you'll see an error page instead of the designer.</span></span> <span data-ttu-id="e1e99-104">這個錯誤頁面不一定表示設計工具中有錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1e99-104">This error page does not necessarily signify a bug in the designer.</span></span> <span data-ttu-id="e1e99-105">錯誤可能是程式碼後置頁面中的某處，其\<名稱為 > 的格式。Designer.cs。</span><span class="sxs-lookup"><span data-stu-id="e1e99-105">The bug may be somewhere in the code-behind page that's named \<your-form-name>.Designer.cs.</span></span> <span data-ttu-id="e1e99-106">錯誤會出現在可折迭的黃色列中，並有連結可以跳到字碼頁上錯誤的位置。</span><span class="sxs-lookup"><span data-stu-id="e1e99-106">Errors appear in collapsible, yellow bars with a link to jump to the location of the error on the code page.</span></span>

![Windows Form 設計工具錯誤頁面](media/windows-forms-designer-error-page-collapsed.png)

<span data-ttu-id="e1e99-108">您可以選擇忽略錯誤，並按一下 [**略過並繼續**] 繼續載入設計工具。</span><span class="sxs-lookup"><span data-stu-id="e1e99-108">You can choose to ignore the errors and continue loading the designer by clicking **Ignore and Continue**.</span></span> <span data-ttu-id="e1e99-109">此動作可能會導致非預期的行為，例如，控制項可能不會出現在設計介面上。</span><span class="sxs-lookup"><span data-stu-id="e1e99-109">This action may result in unexpected behavior, for example, controls may not appear on the design surface.</span></span>

## <a name="instances-of-this-error"></a><span data-ttu-id="e1e99-110">此錯誤的實例</span><span class="sxs-lookup"><span data-stu-id="e1e99-110">Instances of this error</span></span>

<span data-ttu-id="e1e99-111">擴充黃色的誤差線時，會列出錯誤的每個實例。</span><span class="sxs-lookup"><span data-stu-id="e1e99-111">When the yellow error bar is expanded, each instance of the error is listed.</span></span> <span data-ttu-id="e1e99-112">許多錯誤類型包含以下列格式呈現的確切位置： *[專案名稱]* *[表單名稱]* 行： *[行號]* 欄： *[欄號]* 。</span><span class="sxs-lookup"><span data-stu-id="e1e99-112">Many error types include an exact location in the following format: *[Project Name]* *[Form Name]* Line:*[Line Number]* Column:*[Column Number]*.</span></span> <span data-ttu-id="e1e99-113">如果呼叫堆疊與錯誤相關聯，您可以按一下 [**顯示呼叫堆疊**] 連結來查看它。</span><span class="sxs-lookup"><span data-stu-id="e1e99-113">If a call stack is associated with the error, you can click the **Show Call Stack** link to see it.</span></span> <span data-ttu-id="e1e99-114">檢查呼叫堆疊可進一步協助您解決此錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1e99-114">Examining the call stack may further help you resolve the error.</span></span>

![Windows Form 設計工具展開的錯誤](media/windows-forms-designer-error-page-expanded.png)

> [!NOTE]
> - <span data-ttu-id="e1e99-116">針對 Visual Basic 應用程式，設計階段錯誤頁面不會顯示一個以上的錯誤，但可能會顯示多個相同錯誤的實例。</span><span class="sxs-lookup"><span data-stu-id="e1e99-116">For Visual Basic apps, the design-time error page does not display more than one error, but it may display multiple instances of the same error.</span></span>
> - <span data-ttu-id="e1e99-117">若C++為應用程式，錯誤不具有程式碼位置連結。</span><span class="sxs-lookup"><span data-stu-id="e1e99-117">For C++ apps, errors don't have code location links.</span></span>

## <a name="help-with-this-error"></a><span data-ttu-id="e1e99-118">關於此錯誤的說明</span><span class="sxs-lookup"><span data-stu-id="e1e99-118">Help with this error</span></span>

<span data-ttu-id="e1e99-119">如果有可用錯誤的說明主題，請按一下 [ **MSDN**說明] 連結，直接流覽至 docs.microsoft.com 上的 [說明] 頁面。</span><span class="sxs-lookup"><span data-stu-id="e1e99-119">If a help topic for the error is available, click the **MSDN Help** link to navigate directly to the help page on docs.microsoft.com.</span></span>

## <a name="forum-posts-about-this-error"></a><span data-ttu-id="e1e99-120">此錯誤的相關論壇文章</span><span class="sxs-lookup"><span data-stu-id="e1e99-120">Forum posts about this error</span></span>

<span data-ttu-id="e1e99-121">按一下**MSDN 論壇，尋找與此錯誤連結相關的文章**，以流覽至 Microsoft 開發人員網路論壇。</span><span class="sxs-lookup"><span data-stu-id="e1e99-121">Click the **Search the MSDN Forums for posts related to this error** link to navigate to the Microsoft Developer Network forums.</span></span> <span data-ttu-id="e1e99-122">您可能想要特別搜尋[Windows Form 設計工具](https://social.msdn.microsoft.com/Forums/windows/home?forum=winformsdesigner)或[Windows Forms](https://social.msdn.microsoft.com/Forums/windows/home?category=windowsforms)論壇。</span><span class="sxs-lookup"><span data-stu-id="e1e99-122">You may want to specifically search the [Windows Forms Designer](https://social.msdn.microsoft.com/Forums/windows/home?forum=winformsdesigner) or [Windows Forms](https://social.msdn.microsoft.com/Forums/windows/home?category=windowsforms) forums.</span></span>

## <a name="design-time-errors"></a><span data-ttu-id="e1e99-123">設計階段錯誤</span><span class="sxs-lookup"><span data-stu-id="e1e99-123">Design-time errors</span></span>

<span data-ttu-id="e1e99-124">本節列出您可能會遇到的一些錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1e99-124">This section lists some of the errors you may encounter.</span></span>

### <a name="identifier-name-is-not-a-valid-identifier"></a><span data-ttu-id="e1e99-125">'\<識別碼名稱 > ' 不是有效的識別碼</span><span class="sxs-lookup"><span data-stu-id="e1e99-125">'\<identifier name>' is not a valid identifier</span></span>

<span data-ttu-id="e1e99-126">此錯誤表示欄位、方法、事件或物件的名稱不正確。</span><span class="sxs-lookup"><span data-stu-id="e1e99-126">This error indicates that a field, method, event, or object is improperly named.</span></span>

### <a name="name-already-exists-in-project-name"></a><span data-ttu-id="e1e99-127">' name > ' 已存在 '\<專案名稱 > ' 中\<</span><span class="sxs-lookup"><span data-stu-id="e1e99-127">'\<name>' already exists in '\<project name>'</span></span>

<span data-ttu-id="e1e99-128">錯誤訊息：「'\<name > ' 已經存在 '\<project name > ' 中。</span><span class="sxs-lookup"><span data-stu-id="e1e99-128">Error message: "'\<name>' already exists in '\<project name>'.</span></span> <span data-ttu-id="e1e99-129">請輸入唯一的名稱。」</span><span class="sxs-lookup"><span data-stu-id="e1e99-129">Please enter a unique name."</span></span>

<span data-ttu-id="e1e99-130">您已為專案中已經存在的繼承表單指定名稱。</span><span class="sxs-lookup"><span data-stu-id="e1e99-130">You've specified a name for an inherited form that already exists in the project.</span></span> <span data-ttu-id="e1e99-131">若要更正此錯誤，請為繼承的表單指定唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="e1e99-131">To correct this error, give the inherited form a unique name.</span></span>

### <a name="toolbox-tab-name-is-not-a-toolbox-category"></a><span data-ttu-id="e1e99-132">[\<工具箱] 索引標籤名稱 > ' 不是工具箱分類</span><span class="sxs-lookup"><span data-stu-id="e1e99-132">'\<Toolbox tab name>' is not a toolbox category</span></span>

<span data-ttu-id="e1e99-133">協力廠商設計人員嘗試存取 [工具箱] 上不存在的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e1e99-133">A third-party designer has tried to access a tab on the Toolbox that does not exist.</span></span> <span data-ttu-id="e1e99-134">請洽詢元件廠商。</span><span class="sxs-lookup"><span data-stu-id="e1e99-134">Contact the component vendor.</span></span>

### <a name="a-requested-language-parser-is-not-installed"></a><span data-ttu-id="e1e99-135">未安裝要求的語言剖析器</span><span class="sxs-lookup"><span data-stu-id="e1e99-135">A requested language parser is not installed</span></span>

<span data-ttu-id="e1e99-136">錯誤訊息：「未安裝要求的語言剖析器。</span><span class="sxs-lookup"><span data-stu-id="e1e99-136">Error message: "A requested language parser is not installed.</span></span> <span data-ttu-id="e1e99-137">語言剖析器名稱為 '{0}'。」</span><span class="sxs-lookup"><span data-stu-id="e1e99-137">The language parser name is '{0}'."</span></span>

<span data-ttu-id="e1e99-138">Visual Studio 嘗試載入已註冊檔案類型但無法執行的設計工具。</span><span class="sxs-lookup"><span data-stu-id="e1e99-138">Visual Studio attempted to a load a designer that's registered for the file type but could not.</span></span> <span data-ttu-id="e1e99-139">這很可能是因為在安裝期間發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1e99-139">This is most likely because of an error that occurred during setup.</span></span> <span data-ttu-id="e1e99-140">請洽詢您要用來修正的語言廠商。</span><span class="sxs-lookup"><span data-stu-id="e1e99-140">Contact the vendor of the language you're using for a fix.</span></span>

### <a name="a-service-required-for-generating-and-parsing-source-code-is-missing"></a><span data-ttu-id="e1e99-141">遺失產生及剖析原始程式碼所必備的服務</span><span class="sxs-lookup"><span data-stu-id="e1e99-141">A service required for generating and parsing source code is missing</span></span>

<span data-ttu-id="e1e99-142">這是協力廠商元件的問題。</span><span class="sxs-lookup"><span data-stu-id="e1e99-142">This is a problem with a third-party component.</span></span> <span data-ttu-id="e1e99-143">請洽詢元件廠商。</span><span class="sxs-lookup"><span data-stu-id="e1e99-143">Contact the component vendor.</span></span>

### <a name="an-exception-occurred-while-trying-to-create-an-instance-of-object-name"></a><span data-ttu-id="e1e99-144">嘗試建立 '\<object name > ' 的實例時發生例外狀況</span><span class="sxs-lookup"><span data-stu-id="e1e99-144">An exception occurred while trying to create an instance of '\<object name>'</span></span>

<span data-ttu-id="e1e99-145">錯誤訊息：「嘗試建立 '\<object name > ' 的實例時發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e1e99-145">Error message: "An exception occurred while trying to create an instance of '\<object name>'.</span></span> <span data-ttu-id="e1e99-146">例外狀況是\<「例外狀況\>字串」。</span><span class="sxs-lookup"><span data-stu-id="e1e99-146">The exception was "\<exception string\>".</span></span>

<span data-ttu-id="e1e99-147">協力廠商設計師要求 Visual Studio 建立物件，但物件引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1e99-147">A third-party designer requested that Visual Studio create an object, but the object raised an error.</span></span> <span data-ttu-id="e1e99-148">請洽詢元件廠商。</span><span class="sxs-lookup"><span data-stu-id="e1e99-148">Contact the component vendor.</span></span>

### <a name="another-editor-has-document-name-open-in-an-incompatible-mode"></a><span data-ttu-id="e1e99-149">另一個編輯器\<在不相容的模式下開啟 [檔案名稱 >]</span><span class="sxs-lookup"><span data-stu-id="e1e99-149">Another editor has '\<document name>' open in an incompatible mode</span></span>

<span data-ttu-id="e1e99-150">錯誤訊息：「另一個編輯器在\<不相容的模式下開啟了「檔案名稱 >」。</span><span class="sxs-lookup"><span data-stu-id="e1e99-150">Error message: "Another editor has '\<document name>' open in an incompatible mode.</span></span> <span data-ttu-id="e1e99-151">請關閉編輯器，然後再次嘗試此操作。」</span><span class="sxs-lookup"><span data-stu-id="e1e99-151">Please close the editor and try this operation again."</span></span>

<span data-ttu-id="e1e99-152">如果您嘗試開啟已在另一個編輯器中開啟的檔案，就會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1e99-152">This error arises if you try to open a file that is already opened in another editor.</span></span> <span data-ttu-id="e1e99-153">隨即顯示已開啟檔案的編輯器。</span><span class="sxs-lookup"><span data-stu-id="e1e99-153">The editor that already has the file open is shown.</span></span> <span data-ttu-id="e1e99-154">若要更正這個錯誤，請關閉已開啟檔案的編輯器，然後再試一次。</span><span class="sxs-lookup"><span data-stu-id="e1e99-154">To correct this error, close the editor that has the file open, and try again.</span></span>

### <a name="another-editor-has-made-changes-to-document-name"></a><span data-ttu-id="e1e99-155">另一個編輯器已變更\<「檔案名稱 >」</span><span class="sxs-lookup"><span data-stu-id="e1e99-155">Another editor has made changes to '\<document name>'</span></span>

<span data-ttu-id="e1e99-156">關閉並重新開啟設計工具，變更才會生效。</span><span class="sxs-lookup"><span data-stu-id="e1e99-156">Close and reopen the designer for the changes to take effect.</span></span> <span data-ttu-id="e1e99-157">一般來說，Visual Studio 在進行變更之後，會自動重載設計工具。</span><span class="sxs-lookup"><span data-stu-id="e1e99-157">Normally, Visual Studio automatically reloads a designer after changes are made.</span></span> <span data-ttu-id="e1e99-158">不過，其他設計工具（例如協力廠商元件設計工具）可能不支援重載行為。</span><span class="sxs-lookup"><span data-stu-id="e1e99-158">However, other designers, such as third-party component designers, may not support reload behavior.</span></span> <span data-ttu-id="e1e99-159">在此情況下，Visual Studio 會提示您手動關閉並重新開啟設計工具。</span><span class="sxs-lookup"><span data-stu-id="e1e99-159">In this case, Visual Studio prompts you to close and reopen the designer manually.</span></span>

### <a name="another-editor-has-the-file-open-in-an-incompatible-mode"></a><span data-ttu-id="e1e99-160">另一個編輯器在不相容的模式下開啟檔案</span><span class="sxs-lookup"><span data-stu-id="e1e99-160">Another editor has the file open in an incompatible mode</span></span>

<span data-ttu-id="e1e99-161">錯誤訊息：「另一個編輯器在不相容的模式下開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="e1e99-161">Error message: "Another editor has the file open in an incompatible mode.</span></span> <span data-ttu-id="e1e99-162">請關閉編輯器，然後再次嘗試此操作。」</span><span class="sxs-lookup"><span data-stu-id="e1e99-162">Please close the editor and try this operation again."</span></span>

<span data-ttu-id="e1e99-163">此訊息類似于「另一個編輯器\<在不相容的模式中開啟 >」，但 Visual Studio 無法判斷檔案名。</span><span class="sxs-lookup"><span data-stu-id="e1e99-163">This message is similar to "Another editor has '\<document name>' open in an incompatible mode", but Visual Studio is unable to determine the file name.</span></span> <span data-ttu-id="e1e99-164">若要更正這個錯誤，請關閉已開啟檔案的編輯器，然後再試一次。</span><span class="sxs-lookup"><span data-stu-id="e1e99-164">To correct this error, close the editor that has the file open, and try again.</span></span>

### <a name="array-rank-rank-in-array-is-too-high"></a><span data-ttu-id="e1e99-165">陣列次序 '\<陣列中的順位 > ' 太高</span><span class="sxs-lookup"><span data-stu-id="e1e99-165">Array rank '\<rank in array>' is too high</span></span>

<span data-ttu-id="e1e99-166">Visual Studio 只支援設計工具剖析之程式碼區塊中的單一維度陣列。</span><span class="sxs-lookup"><span data-stu-id="e1e99-166">Visual Studio only supports single-dimension arrays in the code block that's parsed by the designer.</span></span> <span data-ttu-id="e1e99-167">多維陣列在此區域外有效。</span><span class="sxs-lookup"><span data-stu-id="e1e99-167">Multidimensional arrays are valid outside this area.</span></span>

### <a name="assembly-assembly-name-could-not-be-opened"></a><span data-ttu-id="e1e99-168">無法開啟\<元件 ' assembly name > '</span><span class="sxs-lookup"><span data-stu-id="e1e99-168">Assembly '\<assembly name>' could not be opened</span></span>

<span data-ttu-id="e1e99-169">錯誤訊息：無法開啟「\<元件」元件名稱 > '。</span><span class="sxs-lookup"><span data-stu-id="e1e99-169">Error message: "Assembly '\<assembly name>' could not be opened.</span></span> <span data-ttu-id="e1e99-170">請確認檔案仍然存在。」</span><span class="sxs-lookup"><span data-stu-id="e1e99-170">Verify that the file still exists."</span></span>

<span data-ttu-id="e1e99-171">當您嘗試開啟無法開啟的檔案時，就會出現這個錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="e1e99-171">This error message arises when you try to open a file that could not be opened.</span></span> <span data-ttu-id="e1e99-172">請確認檔案存在，而且是有效的元件。</span><span class="sxs-lookup"><span data-stu-id="e1e99-172">Verify that the file exists and is a valid assembly.</span></span>

### <a name="bad-element-type-this-serializer-expects-an-element-of-type-type-name"></a><span data-ttu-id="e1e99-173">不正確的元素類型。</span><span class="sxs-lookup"><span data-stu-id="e1e99-173">Bad element type.</span></span> <span data-ttu-id="e1e99-174">此序列化程式需要類型 '\<type name > ' 的元素</span><span class="sxs-lookup"><span data-stu-id="e1e99-174">This serializer expects an element of type '\<type name>'</span></span>

<span data-ttu-id="e1e99-175">這是協力廠商元件的問題。</span><span class="sxs-lookup"><span data-stu-id="e1e99-175">This is a problem with a third-party component.</span></span> <span data-ttu-id="e1e99-176">請洽詢元件廠商。</span><span class="sxs-lookup"><span data-stu-id="e1e99-176">Contact the component vendor.</span></span>

### <a name="cannot-access-the-visual-studio-toolbox-at-this-time"></a><span data-ttu-id="e1e99-177">目前無法存取 Visual Studio 工具箱</span><span class="sxs-lookup"><span data-stu-id="e1e99-177">Cannot access the Visual Studio Toolbox at this time</span></span>

<span data-ttu-id="e1e99-178">Visual Studio 對 [工具箱] 進行呼叫，這是無法使用的。</span><span class="sxs-lookup"><span data-stu-id="e1e99-178">Visual Studio made a call to the Toolbox, which was not available.</span></span> <span data-ttu-id="e1e99-179">如果您看到此錯誤，如果您看到此錯誤，請使用 [回報[問題](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)] 來記錄問題。</span><span class="sxs-lookup"><span data-stu-id="e1e99-179">If you see this error, If you see this error, please log an issue by using [Report a Problem](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).</span></span>

### <a name="cannot-bind-an-event-handler-to-the-event-name-event-because-it-is-read-only"></a><span data-ttu-id="e1e99-180">無法將事件處理常式系結至\<' event name > ' 事件，因為它是唯讀的</span><span class="sxs-lookup"><span data-stu-id="e1e99-180">Cannot bind an event handler to the '\<event name>' event because it is read-only</span></span>

<span data-ttu-id="e1e99-181">當您嘗試將事件連接至繼承自基類的控制項時，通常會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1e99-181">This error most often arises when you've tried to connect an event to a control that's inherited from a base class.</span></span> <span data-ttu-id="e1e99-182">如果控制項的成員變數為私用，Visual Studio 無法將事件連接至方法。</span><span class="sxs-lookup"><span data-stu-id="e1e99-182">If the control's member variable is private, Visual Studio cannot connect the event to the method.</span></span> <span data-ttu-id="e1e99-183">私下繼承的控制項不能有其他系結的事件。</span><span class="sxs-lookup"><span data-stu-id="e1e99-183">Privately inherited controls cannot have additional events bound to them.</span></span>

### <a name="cannot-create-a-method-name-for-the-requested-component-because-it-is-not-a-member-of-the-design-container"></a><span data-ttu-id="e1e99-184">因為要求的元件不是設計容器的成員，所以無法建立方法名稱</span><span class="sxs-lookup"><span data-stu-id="e1e99-184">Cannot create a method name for the requested component because it is not a member of the design container</span></span>

<span data-ttu-id="e1e99-185">Visual Studio 嘗試將事件處理常式加入至設計工具中沒有成員變數的元件。</span><span class="sxs-lookup"><span data-stu-id="e1e99-185">Visual Studio has tried to add an event handler to a component that does not have a member variable in the designer.</span></span> <span data-ttu-id="e1e99-186">請洽詢元件廠商。</span><span class="sxs-lookup"><span data-stu-id="e1e99-186">Contact the component vendor.</span></span>

### <a name="cannot-name-the-object-name-because-it-is-already-named-name"></a><span data-ttu-id="e1e99-187">無法命名物件 '\<name > '，因為它已經命名為 '\<name > '</span><span class="sxs-lookup"><span data-stu-id="e1e99-187">Cannot name the object '\<name>' because it is already named '\<name>'</span></span>

<span data-ttu-id="e1e99-188">這是 Visual Studio 序列化程式中的內部錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1e99-188">This is an internal error in the Visual Studio serializer.</span></span> <span data-ttu-id="e1e99-189">這表示序列化程式嘗試將物件命名為兩次，這是不支援的。</span><span class="sxs-lookup"><span data-stu-id="e1e99-189">It indicates that the serializer has tried to name an object twice, which is not supported.</span></span> <span data-ttu-id="e1e99-190">如果您看到此錯誤，請使用 [回報[問題](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)] 來記錄問題。</span><span class="sxs-lookup"><span data-stu-id="e1e99-190">If you see this error, please log an issue by using [Report a Problem](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).</span></span>

### <a name="cannot-remove-or-destroy-inherited-component-component-name"></a><span data-ttu-id="e1e99-191">無法移除或摧毀繼承的元件\<' component name > '</span><span class="sxs-lookup"><span data-stu-id="e1e99-191">Cannot remove or destroy inherited component '\<component name>'</span></span>

<span data-ttu-id="e1e99-192">繼承的控制項在繼承類別的擁有權之下。</span><span class="sxs-lookup"><span data-stu-id="e1e99-192">Inherited controls are under the ownership of their inheriting class.</span></span> <span data-ttu-id="e1e99-193">繼承控制項的變更必須在控制項來源的類別中進行。</span><span class="sxs-lookup"><span data-stu-id="e1e99-193">Changes to the inherited control must be made in the class from which the control originates.</span></span> <span data-ttu-id="e1e99-194">因此，您無法將它重新命名或摧毀。</span><span class="sxs-lookup"><span data-stu-id="e1e99-194">Thus, you cannot rename or destroy it.</span></span>

### <a name="category-toolbox-tab-name-does-not-have-a-tool-for-class-class-name"></a><span data-ttu-id="e1e99-195">分類的 [\<工具箱]索引標籤名稱>'沒有類別「類別名稱\<>」的工具</span><span class="sxs-lookup"><span data-stu-id="e1e99-195">Category '\<Toolbox tab name>' does not have a tool for class '\<class name>'</span></span>

<span data-ttu-id="e1e99-196">設計工具嘗試參考特定 [工具箱] 索引標籤上的類別，但該類別不存在。</span><span class="sxs-lookup"><span data-stu-id="e1e99-196">The designer tried to reference a class on a particular Toolbox tab, but the class does not exist.</span></span> <span data-ttu-id="e1e99-197">請洽詢元件廠商。</span><span class="sxs-lookup"><span data-stu-id="e1e99-197">Contact the component vendor.</span></span>

### <a name="class-class-name-has-no-matching-constructor"></a><span data-ttu-id="e1e99-198">類別 '\<class name > ' 沒有相符的函式</span><span class="sxs-lookup"><span data-stu-id="e1e99-198">Class '\<class name>' has no matching constructor</span></span>

<span data-ttu-id="e1e99-199">協力廠商的設計工具要求 Visual Studio 在不存在的函式中，以特定參數建立物件。</span><span class="sxs-lookup"><span data-stu-id="e1e99-199">A third-party designer has asked Visual Studio to create an object with particular parameters in the constructor that does not exist.</span></span> <span data-ttu-id="e1e99-200">請洽詢元件廠商。</span><span class="sxs-lookup"><span data-stu-id="e1e99-200">Contact the component vendor.</span></span>

### <a name="code-generation-for-property-property-name-failed"></a><span data-ttu-id="e1e99-201">屬性 '\<屬性名稱 > ' 的程式碼產生失敗</span><span class="sxs-lookup"><span data-stu-id="e1e99-201">Code generation for property '\<property name>' failed</span></span>

<span data-ttu-id="e1e99-202">這是錯誤的泛型包裝函式。</span><span class="sxs-lookup"><span data-stu-id="e1e99-202">This is a generic wrapper for an error.</span></span> <span data-ttu-id="e1e99-203">此訊息隨附的錯誤字串將提供有關錯誤訊息的更多詳細資料，並具有更特定說明主題的連結。</span><span class="sxs-lookup"><span data-stu-id="e1e99-203">The error string that accompanies this message will give more details about the error message and have a link to a more specific help topic.</span></span> <span data-ttu-id="e1e99-204">若要更正此錯誤，請解決錯誤訊息中所指定的錯誤，此錯誤會附加到此錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1e99-204">To correct this error, address the error specified in the error message appended to this error.</span></span>

### <a name="component-component-name-did-not-call-containeradd-in-its-constructor"></a><span data-ttu-id="e1e99-205">元件的\<元件名稱 > ' 未在其函式中呼叫 Container. Add （）</span><span class="sxs-lookup"><span data-stu-id="e1e99-205">Component '\<component name>' did not call Container.Add() in its constructor</span></span>

<span data-ttu-id="e1e99-206">這是您剛載入或置於表單上的元件中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1e99-206">This is an error in the component you just loaded or placed on the form.</span></span> <span data-ttu-id="e1e99-207">這表示元件並未將本身新增至其容器控制項（不論是另一個控制項或表單）。</span><span class="sxs-lookup"><span data-stu-id="e1e99-207">It indicates that the component did not add itself to its container control (whether that is another control or a form).</span></span> <span data-ttu-id="e1e99-208">設計工具會繼續運作，但元件可能會在執行時間發生問題。</span><span class="sxs-lookup"><span data-stu-id="e1e99-208">The designer will continue to work, but there may be problems with the component at run time.</span></span>

<span data-ttu-id="e1e99-209">若要更正錯誤，請洽詢元件廠商。</span><span class="sxs-lookup"><span data-stu-id="e1e99-209">To correct the error, contact the component vendor.</span></span> <span data-ttu-id="e1e99-210">或者，如果它是您所建立的元件，請`IContainer.Add`在元件的「函式」中呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="e1e99-210">Or, if it is a component you created, call the `IContainer.Add` method in the component's constructor.</span></span>

### <a name="component-name-cannot-be-empty"></a><span data-ttu-id="e1e99-211">元件名稱不可為空白</span><span class="sxs-lookup"><span data-stu-id="e1e99-211">Component name cannot be empty</span></span>

<span data-ttu-id="e1e99-212">當您嘗試將元件重新命名為空值時，就會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1e99-212">This error arises when you try to rename a component to an empty value.</span></span>

### <a name="could-not-access-the-variable-variable-name-because-it-has-not-been-initialized-yet"></a><span data-ttu-id="e1e99-213">無法存取變數\<的變數名稱 > '，因為它尚未初始化</span><span class="sxs-lookup"><span data-stu-id="e1e99-213">Could not access the variable '\<variable name>' because it has not been initialized yet</span></span>

<span data-ttu-id="e1e99-214">發生此錯誤的原因有兩個。</span><span class="sxs-lookup"><span data-stu-id="e1e99-214">This error can arise because of two scenarios.</span></span> <span data-ttu-id="e1e99-215">協力廠商元件廠商的控制項或元件已散發，或是您所撰寫的程式碼在元件之間具有遞迴相依性時，可能會有問題。</span><span class="sxs-lookup"><span data-stu-id="e1e99-215">Either a third-party component vendor has a problem with a control or component they have distributed, or the code you have written has recursive dependencies between components.</span></span>

<span data-ttu-id="e1e99-216">若要更正這個錯誤，請確定您的程式碼沒有遞迴相依性。</span><span class="sxs-lookup"><span data-stu-id="e1e99-216">To correct this error, ensure that your code does not have a recursive dependency.</span></span> <span data-ttu-id="e1e99-217">如果沒有這類問題，請注意錯誤訊息的確切文字，並與元件廠商聯繫。</span><span class="sxs-lookup"><span data-stu-id="e1e99-217">If it is free of such problems, note the exact text of the error message and contact the component vendor.</span></span>

### <a name="could-not-find-type-type-name"></a><span data-ttu-id="e1e99-218">找不到類型 '\<type name > '</span><span class="sxs-lookup"><span data-stu-id="e1e99-218">Could not find type '\<type name>'</span></span>

<span data-ttu-id="e1e99-219">錯誤訊息：「找不到類型\<名稱 > '。</span><span class="sxs-lookup"><span data-stu-id="e1e99-219">Error message: "Could not find type '\<type name>'.</span></span> <span data-ttu-id="e1e99-220">請確定已參考包含此類型的元件。</span><span class="sxs-lookup"><span data-stu-id="e1e99-220">Please make sure that the assembly that contains this type is referenced.</span></span> <span data-ttu-id="e1e99-221">如果這種類型是您開發專案的一部分，請確定已成功建立專案。」</span><span class="sxs-lookup"><span data-stu-id="e1e99-221">If this type is a part of your development project, make sure that the project has been successfully built."</span></span>

<span data-ttu-id="e1e99-222">發生此錯誤的原因是找不到參考。</span><span class="sxs-lookup"><span data-stu-id="e1e99-222">This error occurred because a reference was not found.</span></span> <span data-ttu-id="e1e99-223">請確定已參考錯誤訊息中所指出的類型，而且也會參考該類型所需的任何元件。</span><span class="sxs-lookup"><span data-stu-id="e1e99-223">Make sure the type indicated in the error message is referenced, and that any assemblies that the type requires are also referenced.</span></span> <span data-ttu-id="e1e99-224">問題通常是，尚未建立解決方案中的控制項。</span><span class="sxs-lookup"><span data-stu-id="e1e99-224">Often, the problem is that a control in the solution has not been built.</span></span> <span data-ttu-id="e1e99-225">若要建立，請從 [**建立**] 功能表中選取 [**建立方案**]。</span><span class="sxs-lookup"><span data-stu-id="e1e99-225">To build, select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="e1e99-226">否則，如果已經建立控制項，請從方案總管中 [**參考**] 或 [相依性 **]** 資料夾的右鍵功能表中，手動加入參考。</span><span class="sxs-lookup"><span data-stu-id="e1e99-226">Otherwise, if the control has already been built, add a reference manually from the right-click menu of the **References** or **Dependencies** folder in Solution Explorer.</span></span>

### <a name="could-not-load-type-type-name"></a><span data-ttu-id="e1e99-227">無法載入類型 '\<type name > '</span><span class="sxs-lookup"><span data-stu-id="e1e99-227">Could not load type '\<type name>'</span></span>

<span data-ttu-id="e1e99-228">錯誤訊息：「無法載入類型 '\<類型名稱 > '。</span><span class="sxs-lookup"><span data-stu-id="e1e99-228">Error message: "Could not load type '\<type name>'.</span></span> <span data-ttu-id="e1e99-229">請確定包含此類型的元件已加入至專案參考。」</span><span class="sxs-lookup"><span data-stu-id="e1e99-229">Please make sure that the assembly containing this type is added to the project references."</span></span>

<span data-ttu-id="e1e99-230">Visual Studio 嘗試連接事件處理方法，但找不到方法的一或多個參數類型。</span><span class="sxs-lookup"><span data-stu-id="e1e99-230">Visual Studio attempted to wire up an event-handling method and could not find one or more parameter types for the method.</span></span> <span data-ttu-id="e1e99-231">這通常是因為遺漏參考所造成。</span><span class="sxs-lookup"><span data-stu-id="e1e99-231">This is usually caused by a missing reference.</span></span> <span data-ttu-id="e1e99-232">若要更正這個錯誤，請將包含該類型的參考新增至專案，然後再試一次。</span><span class="sxs-lookup"><span data-stu-id="e1e99-232">To correct this error, add the reference containing the type to the project and try again.</span></span>

### <a name="could-not-locate-the-project-item-templates-for-inherited-components"></a><span data-ttu-id="e1e99-233">找不到繼承元件的專案項目範本</span><span class="sxs-lookup"><span data-stu-id="e1e99-233">Could not locate the project item templates for inherited components</span></span>

<span data-ttu-id="e1e99-234">Visual Studio 中的繼承表單的範本無法使用。</span><span class="sxs-lookup"><span data-stu-id="e1e99-234">The templates for inherited forms in Visual Studio are not available.</span></span> <span data-ttu-id="e1e99-235">如果您看到此錯誤，請使用 [回報[問題](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)] 來記錄問題。</span><span class="sxs-lookup"><span data-stu-id="e1e99-235">If you see this error, please log an issue by using [Report a Problem](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).</span></span>

### <a name="delegate-class-class-name-has-no-invoke-method-is-this-class-a-delegate"></a><span data-ttu-id="e1e99-236">委派類別 '\<class name > ' 沒有 invoke 方法。</span><span class="sxs-lookup"><span data-stu-id="e1e99-236">Delegate class '\<class name>' has no invoke method.</span></span> <span data-ttu-id="e1e99-237">這個類別是委派嗎？</span><span class="sxs-lookup"><span data-stu-id="e1e99-237">Is this class a delegate?</span></span>

<span data-ttu-id="e1e99-238">Visual Studio 嘗試建立事件處理常式，但事件種類發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1e99-238">Visual Studio has tried to create an event handler, but there is something wrong with the event type.</span></span> <span data-ttu-id="e1e99-239">如果事件是由不符合 CLS 標準的語言所建立，則會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="e1e99-239">This can happen if the event was created by a non-CLS-compliant language.</span></span> <span data-ttu-id="e1e99-240">請洽詢元件廠商。</span><span class="sxs-lookup"><span data-stu-id="e1e99-240">Contact the component vendor.</span></span>

### <a name="duplicate-declaration-of-member-member-name"></a><span data-ttu-id="e1e99-241">成員 '\<member name > ' 的重複宣告</span><span class="sxs-lookup"><span data-stu-id="e1e99-241">Duplicate declaration of member '\<member name>'</span></span>

<span data-ttu-id="e1e99-242">發生此錯誤的原因是成員變數已宣告兩次（例如，在程式碼`Button1`中宣告了兩個名為的控制項）。</span><span class="sxs-lookup"><span data-stu-id="e1e99-242">This error arises because a member variable has been declared twice (for example, two controls named `Button1` are declared in the code).</span></span> <span data-ttu-id="e1e99-243">名稱在繼承的表單中必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="e1e99-243">Names must be unique across inherited forms.</span></span> <span data-ttu-id="e1e99-244">此外，名稱不能只有大小寫不同。</span><span class="sxs-lookup"><span data-stu-id="e1e99-244">Additionally, names cannot differ only by case.</span></span>

### <a name="error-reading-resources-from-the-resource-file-for-the-culture-culture-name"></a><span data-ttu-id="e1e99-245">從資源檔讀取文化特性 '\<文化特性名稱 > ' 的資源時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="e1e99-245">Error reading resources from the resource file for the culture '\<culture name>'</span></span>

<span data-ttu-id="e1e99-246">如果專案中有錯誤的 .resx 檔案，就會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1e99-246">This error can occur if there is a bad .resx file in the project.</span></span>

<span data-ttu-id="e1e99-247">若要更正此錯誤：</span><span class="sxs-lookup"><span data-stu-id="e1e99-247">To correct this error:</span></span>

1. <span data-ttu-id="e1e99-248">按一下 方案總管中的 **顯示所有**檔案 按鈕，以查看與方案相關聯的 .resx 檔案。</span><span class="sxs-lookup"><span data-stu-id="e1e99-248">Click the **Show All Files** button in Solution Explorer to view the .resx files associated with the solution.</span></span>
2. <span data-ttu-id="e1e99-249">在 XML 編輯器中載入 .resx 檔案，方法是以滑鼠右鍵按一下 .resx 檔案，然後選擇 [**開啟**]。</span><span class="sxs-lookup"><span data-stu-id="e1e99-249">Load the .resx file in the XML Editor by right-clicking the .resx file and choosing **Open**.</span></span>
3. <span data-ttu-id="e1e99-250">手動編輯 .resx 檔案以解決錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1e99-250">Edit the .resx file manually to address the errors.</span></span>

### <a name="error-reading-resources-from-the-resource-file-for-the-default-culture-culture-name"></a><span data-ttu-id="e1e99-251">從資源檔讀取預設文化\<特性名稱 > ' 的資源時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="e1e99-251">Error reading resources from the resource file for the default culture '\<culture name>'</span></span>

<span data-ttu-id="e1e99-252">如果專案中有不正確的 .resx 檔案作為預設文化特性，就會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1e99-252">This error can occur if there is a bad .resx file in the project for the default culture.</span></span>

<span data-ttu-id="e1e99-253">若要更正此錯誤：</span><span class="sxs-lookup"><span data-stu-id="e1e99-253">To correct this error:</span></span>

1. <span data-ttu-id="e1e99-254">按一下 方案總管中的 **顯示所有**檔案 按鈕，以查看與方案相關聯的 .resx 檔案。</span><span class="sxs-lookup"><span data-stu-id="e1e99-254">Click the **Show All Files** button in Solution Explorer to view the .resx files associated with the solution.</span></span>
2. <span data-ttu-id="e1e99-255">在 XML 編輯器中載入 .resx 檔案，方法是以滑鼠右鍵按一下 .resx 檔案，然後選擇 [**開啟**]。</span><span class="sxs-lookup"><span data-stu-id="e1e99-255">Load the .resx file in the XML Editor by right-clicking the .resx file and choosing **Open**.</span></span>
3. <span data-ttu-id="e1e99-256">手動編輯 .resx 檔案以解決錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1e99-256">Edit the .resx file manually to address the errors.</span></span>

### <a name="failed-to-parse-method-method-name"></a><span data-ttu-id="e1e99-257">無法剖析方法 '\<method name > '</span><span class="sxs-lookup"><span data-stu-id="e1e99-257">Failed to parse method '\<method name>'</span></span>

<span data-ttu-id="e1e99-258">錯誤訊息：「無法剖析方法 '\<方法名稱 > '。</span><span class="sxs-lookup"><span data-stu-id="e1e99-258">Error message: "Failed to parse method '\<method name>'.</span></span> <span data-ttu-id="e1e99-259">剖析器回報下列錯誤：\<「錯誤字串 >」。</span><span class="sxs-lookup"><span data-stu-id="e1e99-259">The parser reported the following error: '\<error string>'.</span></span> <span data-ttu-id="e1e99-260">請查看工作清單中是否有潛在的錯誤。」</span><span class="sxs-lookup"><span data-stu-id="e1e99-260">Please look in the Task List for potential errors."</span></span>

<span data-ttu-id="e1e99-261">這是在剖析期間所發生之問題的一般錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="e1e99-261">This is a general error message for problems that arise during parsing.</span></span> <span data-ttu-id="e1e99-262">這些錯誤通常是因為語法錯誤所造成。</span><span class="sxs-lookup"><span data-stu-id="e1e99-262">These errors are often due to syntax errors.</span></span> <span data-ttu-id="e1e99-263">如需與錯誤相關的特定訊息，請參閱工作清單。</span><span class="sxs-lookup"><span data-stu-id="e1e99-263">See the Task List for specific messages related to the error.</span></span>

### <a name="invalid-component-name-component-name"></a><span data-ttu-id="e1e99-264">不正確元件名稱：\<' 元件名稱 > '</span><span class="sxs-lookup"><span data-stu-id="e1e99-264">Invalid component name: '\<component name>'</span></span>

<span data-ttu-id="e1e99-265">您已嘗試將元件重新命名為該語言的無效值。</span><span class="sxs-lookup"><span data-stu-id="e1e99-265">You've tried to rename a component to an invalid value for that language.</span></span> <span data-ttu-id="e1e99-266">若要更正此錯誤，請為元件命名，使其符合該語言的命名規則。</span><span class="sxs-lookup"><span data-stu-id="e1e99-266">To correct this error, name the component such that it complies with the naming rules for that language.</span></span>

### <a name="the-type-class-name-is-made-of-several-partial-classes-in-the-same-file"></a><span data-ttu-id="e1e99-267">類型 '\<class name > ' 是由相同檔案中的數個部分類別所組成</span><span class="sxs-lookup"><span data-stu-id="e1e99-267">The type '\<class name>' is made of several partial classes in the same file</span></span>

<span data-ttu-id="e1e99-268">當您使用[partial](/dotnet/csharp/language-reference/keywords/partial-type)關鍵字在多個檔案中定義類別時，每個檔案中只能有一個部分定義。</span><span class="sxs-lookup"><span data-stu-id="e1e99-268">When you define a class in multiple files by using the [partial](/dotnet/csharp/language-reference/keywords/partial-type) keyword, you can only have one partial definition in each file.</span></span>

<span data-ttu-id="e1e99-269">若要更正這個錯誤，請從檔案中移除類別的所有部分定義，而不是全部。</span><span class="sxs-lookup"><span data-stu-id="e1e99-269">To correct this error, remove all but one of the partial definitions of your class from the file.</span></span>

### <a name="the-assembly-assembly-name-could-not-be-found"></a><span data-ttu-id="e1e99-270">找不到\<元件 ' assembly name > '</span><span class="sxs-lookup"><span data-stu-id="e1e99-270">The assembly '\<assembly name>' could not be found</span></span>

<span data-ttu-id="e1e99-271">錯誤訊息：找不到「\<元件」元件名稱 > '。</span><span class="sxs-lookup"><span data-stu-id="e1e99-271">Error message: "The assembly '\<assembly name>' could not be found.</span></span> <span data-ttu-id="e1e99-272">請確定已參考此元件。</span><span class="sxs-lookup"><span data-stu-id="e1e99-272">Ensure that the assembly is referenced.</span></span> <span data-ttu-id="e1e99-273">如果元件是目前開發專案的一部分，請確定已建立專案。」</span><span class="sxs-lookup"><span data-stu-id="e1e99-273">If the assembly is part of the current development project, ensure that the project has been built."</span></span>

<span data-ttu-id="e1e99-274">此錯誤類似「找不到類型 '\<類型名稱 > '」，但通常是因為中繼資料屬性而發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1e99-274">This error is similar to "The type '\<type name>' could not be found", but this error usually happens because of a metadata attribute.</span></span> <span data-ttu-id="e1e99-275">若要更正這個錯誤，請檢查屬性所使用的所有元件都已被參考。</span><span class="sxs-lookup"><span data-stu-id="e1e99-275">To correct this error, check that all assemblies used by attributes are referenced.</span></span>

### <a name="the-assembly-name-assembly-name-is-invalid"></a><span data-ttu-id="e1e99-276">元件名稱 '\<assembly name > ' 無效</span><span class="sxs-lookup"><span data-stu-id="e1e99-276">The assembly name '\<assembly name>' is invalid</span></span>

<span data-ttu-id="e1e99-277">元件已要求特定的元件，但元件提供的名稱不是有效的元件名稱。</span><span class="sxs-lookup"><span data-stu-id="e1e99-277">A component has requested a particular assembly, but the name provided by the component is not a valid assembly name.</span></span> <span data-ttu-id="e1e99-278">請洽詢元件廠商。</span><span class="sxs-lookup"><span data-stu-id="e1e99-278">Contact the component vendor.</span></span>

### <a name="the-base-class-class-name-cannot-be-designed"></a><span data-ttu-id="e1e99-279">無法設計基類 '\<class name > '</span><span class="sxs-lookup"><span data-stu-id="e1e99-279">The base class '\<class name>' cannot be designed</span></span>

<span data-ttu-id="e1e99-280">Visual Studio 載入類別，但無法設計類別，因為類別的實施者並未提供設計工具。</span><span class="sxs-lookup"><span data-stu-id="e1e99-280">Visual Studio loaded the class, but the class cannot be designed because the implementer of the class did not provide a designer.</span></span> <span data-ttu-id="e1e99-281">如果類別支援設計工具，請確定沒有任何問題會導致在設計工具（例如編譯器錯誤）中顯示問題。</span><span class="sxs-lookup"><span data-stu-id="e1e99-281">If the class supports a designer, make sure there are no problems that would cause issues with displaying it in a designer, such as compiler errors.</span></span> <span data-ttu-id="e1e99-282">此外，請確定對類別的所有參考都是正確的，而且所有類別名稱的拼寫正確。</span><span class="sxs-lookup"><span data-stu-id="e1e99-282">Also, make sure that all references to the class are correct and all class names are correctly spelled.</span></span> <span data-ttu-id="e1e99-283">否則，如果類別無法設計，請在程式碼視圖中進行編輯。</span><span class="sxs-lookup"><span data-stu-id="e1e99-283">Otherwise, if the class is not designable, edit it in Code view.</span></span>

### <a name="the-base-class-class-name-could-not-be-loaded"></a><span data-ttu-id="e1e99-284">無法載入基類 '\<class name > '</span><span class="sxs-lookup"><span data-stu-id="e1e99-284">The base class '\<class name>' could not be loaded</span></span>

<span data-ttu-id="e1e99-285">專案中未參考類別，因此 Visual Studio 無法載入。</span><span class="sxs-lookup"><span data-stu-id="e1e99-285">The class is not referenced in the project, so Visual Studio can't load it.</span></span> <span data-ttu-id="e1e99-286">若要更正這個錯誤，請將參考新增至專案中的類別，然後關閉並重新開啟 [Windows Form 設計工具] 視窗。</span><span class="sxs-lookup"><span data-stu-id="e1e99-286">To correct this error, add a reference to the class in the project, and close and reopen the Windows Forms Designer window.</span></span>

### <a name="the-class-class-name-cannot-be-designed-in-this-version-of-visual-studio"></a><span data-ttu-id="e1e99-287">無法在這個\<版本的中設計類別的類別名稱 > ' Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e1e99-287">The class '\<class name>' cannot be designed in this version of Visual Studio</span></span>

<span data-ttu-id="e1e99-288">這個控制項或元件的設計工具不支援與 Visual Studio 相同的類型。</span><span class="sxs-lookup"><span data-stu-id="e1e99-288">The designer for this control or component does not support the same types that Visual Studio does.</span></span> <span data-ttu-id="e1e99-289">請洽詢元件廠商。</span><span class="sxs-lookup"><span data-stu-id="e1e99-289">Contact the component vendor.</span></span>

### <a name="the-class-name-is-not-a-valid-identifier-for-this-language"></a><span data-ttu-id="e1e99-290">類別名稱不是此語言的有效識別項</span><span class="sxs-lookup"><span data-stu-id="e1e99-290">The class name is not a valid identifier for this language</span></span>

<span data-ttu-id="e1e99-291">使用者所建立的原始程式碼具有類別名稱，對所使用的語言無效。</span><span class="sxs-lookup"><span data-stu-id="e1e99-291">The source code being created by the user has a class name that is not valid for the language being used.</span></span> <span data-ttu-id="e1e99-292">若要更正此錯誤，請將類別命名為符合語言需求。</span><span class="sxs-lookup"><span data-stu-id="e1e99-292">To correct this error, name the class such that it conforms to the language requirements.</span></span>

### <a name="the-component-cannot-be-added-because-it-contains-a-circular-reference-to-reference-name"></a><span data-ttu-id="e1e99-293">無法加入元件，因為它包含 '\<reference name > ' 的迴圈參考</span><span class="sxs-lookup"><span data-stu-id="e1e99-293">The component cannot be added because it contains a circular reference to '\<reference name>'</span></span>

<span data-ttu-id="e1e99-294">您不能將控制項或元件新增至本身。</span><span class="sxs-lookup"><span data-stu-id="e1e99-294">You cannot add a control or component to itself.</span></span> <span data-ttu-id="e1e99-295">發生這種情況的另一種情況是，如果表單的 InitializeComponent 方法中有程式碼（例如 Form1），則會建立另一個 Form1 的實例。</span><span class="sxs-lookup"><span data-stu-id="e1e99-295">Another situation where this might occur is if there is code in the InitializeComponent method of a form (for example, Form1) that creates another instance of Form1.</span></span>

### <a name="the-designer-cannot-be-modified-at-this-time"></a><span data-ttu-id="e1e99-296">目前無法修改設計工具</span><span class="sxs-lookup"><span data-stu-id="e1e99-296">The designer cannot be modified at this time</span></span>

<span data-ttu-id="e1e99-297">當編輯器中的檔案標示為唯讀時，就會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1e99-297">This error occurs when the file in the editor is marked as read-only.</span></span> <span data-ttu-id="e1e99-298">請確定檔案未標示為唯讀，且應用程式未執行。</span><span class="sxs-lookup"><span data-stu-id="e1e99-298">Ensure that the file is not marked read-only and the application is not running.</span></span>

### <a name="the-designer-could-not-be-shown-for-this-file-because-none-of-the-classes-within-it-can-be-designed"></a><span data-ttu-id="e1e99-299">無法對這個檔案顯示設計工具，因為檔案中沒有可以設計的類別</span><span class="sxs-lookup"><span data-stu-id="e1e99-299">The designer could not be shown for this file because none of the classes within it can be designed</span></span>

<span data-ttu-id="e1e99-300">當 Visual Studio 找不到滿足設計工具需求的基類時，就會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1e99-300">This error occurs when Visual Studio cannot find a base class that satisfies designer requirements.</span></span> <span data-ttu-id="e1e99-301">表單和控制項必須衍生自支援設計工具的基類。</span><span class="sxs-lookup"><span data-stu-id="e1e99-301">Forms and controls must derive from a base class that supports designers.</span></span> <span data-ttu-id="e1e99-302">如果您是從繼承的表單或控制項衍生，請確定已建立專案。</span><span class="sxs-lookup"><span data-stu-id="e1e99-302">If you're deriving from an inherited form or control, make sure the project has been built.</span></span>

### <a name="the-designer-for-base-class-class-name-is-not-installed"></a><span data-ttu-id="e1e99-303">未安裝基類\<「類別名稱 >」的設計工具</span><span class="sxs-lookup"><span data-stu-id="e1e99-303">The designer for base class '\<class name>' is not installed</span></span>

<span data-ttu-id="e1e99-304">Visual Studio 無法載入類別的設計工具。</span><span class="sxs-lookup"><span data-stu-id="e1e99-304">Visual Studio could not load the designer for the class.</span></span> <span data-ttu-id="e1e99-305">如果您看到此錯誤，請使用 [回報[問題](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)] 來記錄問題。</span><span class="sxs-lookup"><span data-stu-id="e1e99-305">If you see this error, please log an issue by using [Report a Problem](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).</span></span>

### <a name="the-designer-must-create-an-instance-of-type-type-name-but-it-cant-because-the-type-is-declared-as-abstract"></a><span data-ttu-id="e1e99-306">設計工具必須建立類型 '\<type name > ' 的實例，但因為該類型宣告為抽象，所以無法這麼做</span><span class="sxs-lookup"><span data-stu-id="e1e99-306">The designer must create an instance of type '\<type name>', but it can't because the type is declared as abstract</span></span>

<span data-ttu-id="e1e99-307">發生這個錯誤的原因是，傳遞至設計工具之物件的基類是[抽象](/dotnet/csharp/language-reference/keywords/abstract)的，這是不允許的。</span><span class="sxs-lookup"><span data-stu-id="e1e99-307">This error occurred because the base class of the object being passed to the designer is [abstract](/dotnet/csharp/language-reference/keywords/abstract), which is not allowed.</span></span>

### <a name="the-file-could-not-be-loaded-in-the-designer"></a><span data-ttu-id="e1e99-308">設計工具無法載入檔案</span><span class="sxs-lookup"><span data-stu-id="e1e99-308">The file could not be loaded in the designer</span></span>

<span data-ttu-id="e1e99-309">這個檔案的基類不支援任何設計工具。</span><span class="sxs-lookup"><span data-stu-id="e1e99-309">The base class of this file does not support any designers.</span></span> <span data-ttu-id="e1e99-310">因應措施是使用程式碼 view 來處理檔案。</span><span class="sxs-lookup"><span data-stu-id="e1e99-310">As a workaround, use Code view to work on the file.</span></span> <span data-ttu-id="e1e99-311">以滑鼠右鍵按一下方案總管中的檔案，然後選擇 [ **View Code**]。</span><span class="sxs-lookup"><span data-stu-id="e1e99-311">Right-click the file in Solution Explorer and choose **View Code**.</span></span>

### <a name="the-language-for-this-file-does-not-support-the-necessary-code-parsing-and-generation-services"></a><span data-ttu-id="e1e99-312">這個檔案所使用的語言不支援必要的程式碼剖析與產生服務</span><span class="sxs-lookup"><span data-stu-id="e1e99-312">The language for this file does not support the necessary code parsing and generation services</span></span>

<span data-ttu-id="e1e99-313">錯誤訊息：「此檔案的語言不支援必要的程式碼剖析和產生服務。</span><span class="sxs-lookup"><span data-stu-id="e1e99-313">Error message: "The language for this file does not support the necessary code parsing and generation services.</span></span> <span data-ttu-id="e1e99-314">請確定您要開啟的檔案是專案的成員，然後再次嘗試開啟檔案。」</span><span class="sxs-lookup"><span data-stu-id="e1e99-314">Please ensure the file you are opening is a member of a project and then try to open the file again."</span></span>

<span data-ttu-id="e1e99-315">這個錯誤最可能是因為在不支援設計工具的專案中開啟檔案所造成。</span><span class="sxs-lookup"><span data-stu-id="e1e99-315">This error most likely resulted from opening a file that's in a project that does not support designers.</span></span>

### <a name="the-language-parser-class-class-name-is-not-implemented-properly"></a><span data-ttu-id="e1e99-316">語言剖析器類別 '\<class name > ' 未正確執行</span><span class="sxs-lookup"><span data-stu-id="e1e99-316">The language parser class '\<class name>' is not implemented properly</span></span>

<span data-ttu-id="e1e99-317">錯誤訊息：「語言剖析器類別\<的類別名稱 > ' 未正確執行。</span><span class="sxs-lookup"><span data-stu-id="e1e99-317">Error message: "The language parser class '\<class name>' is not implemented properly.</span></span> <span data-ttu-id="e1e99-318">請洽詢廠商以取得更新的剖析器模組。」</span><span class="sxs-lookup"><span data-stu-id="e1e99-318">Contact the vendor for an updated parser module."</span></span>

<span data-ttu-id="e1e99-319">使用中的語言已註冊的設計工具類別不是衍生自正確的基類。</span><span class="sxs-lookup"><span data-stu-id="e1e99-319">The language in use has registered a designer class that doesn't derive from the correct base class.</span></span> <span data-ttu-id="e1e99-320">請洽詢您所使用之語言的廠商。</span><span class="sxs-lookup"><span data-stu-id="e1e99-320">Contact the vendor of the language you're using.</span></span>

### <a name="the-name-name-is-already-used-by-another-object"></a><span data-ttu-id="e1e99-321">名稱 '\<name > ' 已經由另一個物件使用</span><span class="sxs-lookup"><span data-stu-id="e1e99-321">The name '\<name>' is already used by another object</span></span>

<span data-ttu-id="e1e99-322">這是 Visual Studio 序列化程式中的內部錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1e99-322">This is an internal error in the Visual Studio serializer.</span></span> <span data-ttu-id="e1e99-323">如果您看到此錯誤，請使用 [回報[問題](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)] 來記錄問題。</span><span class="sxs-lookup"><span data-stu-id="e1e99-323">If you see this error, please log an issue by using [Report a Problem](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).</span></span>

### <a name="the-object-object-name-does-not-implement-the-icomponent-interface"></a><span data-ttu-id="e1e99-324">物件\<的物件名稱 > ' 未執行 IComponent 介面</span><span class="sxs-lookup"><span data-stu-id="e1e99-324">The object '\<object name>' does not implement the IComponent interface</span></span>

<span data-ttu-id="e1e99-325">Visual Studio 嘗試建立元件，但建立的物件未執行<xref:System.ComponentModel.IComponent>介面。</span><span class="sxs-lookup"><span data-stu-id="e1e99-325">Visual Studio tried to create a component, but the object created does not implement the <xref:System.ComponentModel.IComponent> interface.</span></span> <span data-ttu-id="e1e99-326">請洽詢元件廠商以取得修正。</span><span class="sxs-lookup"><span data-stu-id="e1e99-326">Contact the component vendor for a fix.</span></span>

### <a name="the-object-object-name-returned-null-for-the-property-property-name-but-this-is-not-allowed"></a><span data-ttu-id="e1e99-327">物件\<的物件名稱 > ' 為\<屬性的屬性名稱 > ' 傳回 null，但不允許這種情況</span><span class="sxs-lookup"><span data-stu-id="e1e99-327">The object '\<object name>' returned null for the property '\<property name>' but this is not allowed</span></span>

<span data-ttu-id="e1e99-328">有些 .NET 屬性應該一律會傳回物件。</span><span class="sxs-lookup"><span data-stu-id="e1e99-328">There are some .NET properties that should always return an object.</span></span> <span data-ttu-id="e1e99-329">例如，表單的**controls**集合應該一律傳回物件，即使其中沒有控制項。</span><span class="sxs-lookup"><span data-stu-id="e1e99-329">For example, the **Controls** collection of a form should always return an object, even when there are no controls in it.</span></span>

<span data-ttu-id="e1e99-330">若要更正這個錯誤，請確定錯誤中指定的屬性不是 null。</span><span class="sxs-lookup"><span data-stu-id="e1e99-330">To correct this error, ensure that the property specified in the error is not null.</span></span>

### <a name="the-serialization-data-object-is-not-of-the-proper-type"></a><span data-ttu-id="e1e99-331">序列化資料物件不是適當的類型</span><span class="sxs-lookup"><span data-stu-id="e1e99-331">The serialization data object is not of the proper type</span></span>

<span data-ttu-id="e1e99-332">序列化程式所提供的資料物件不是符合目前正在使用之序列化程式的型別實例。</span><span class="sxs-lookup"><span data-stu-id="e1e99-332">A data object offered by the serializer is not an instance of a type that matches the current serializer being used.</span></span> <span data-ttu-id="e1e99-333">請洽詢元件廠商。</span><span class="sxs-lookup"><span data-stu-id="e1e99-333">Contact the component vendor.</span></span>

### <a name="the-service-service-name-is-required-but-could-not-be-located"></a><span data-ttu-id="e1e99-334">服務 '\<服務名稱 > ' 是必要的，但找不到</span><span class="sxs-lookup"><span data-stu-id="e1e99-334">The service '\<service name>' is required, but could not be located</span></span>

<span data-ttu-id="e1e99-335">錯誤訊息：「服務\<」服務名稱 > ' 是必要的，但找不到。</span><span class="sxs-lookup"><span data-stu-id="e1e99-335">Error message: "The service '\<service name>' is required, but could not be located.</span></span> <span data-ttu-id="e1e99-336">您的 Visual Studio 安裝可能有問題。」</span><span class="sxs-lookup"><span data-stu-id="e1e99-336">There may be a problem with your Visual Studio installation."</span></span>

<span data-ttu-id="e1e99-337">Visual Studio 所需的服務無法使用。</span><span class="sxs-lookup"><span data-stu-id="e1e99-337">A service required by Visual Studio is unavailable.</span></span> <span data-ttu-id="e1e99-338">如果您嘗試載入不支援該設計工具的專案，請使用 [程式碼編輯器] 來進行所需的變更。</span><span class="sxs-lookup"><span data-stu-id="e1e99-338">If you were trying to load a project that does not support that designer, use the Code Editor to make the changes you require.</span></span> <span data-ttu-id="e1e99-339">否則，如果您看到此錯誤，請使用 [回報[問題](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)] 來記錄問題。</span><span class="sxs-lookup"><span data-stu-id="e1e99-339">Otherwise, If you see this error, please log an issue by using [Report a Problem](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).</span></span>

### <a name="the-service-instance-must-derive-from-or-implement-interface-name"></a><span data-ttu-id="e1e99-340">服務實例必須衍生自或執行 '\<介面名稱 > '</span><span class="sxs-lookup"><span data-stu-id="e1e99-340">The service instance must derive from or implement '\<interface name>'</span></span>

<span data-ttu-id="e1e99-341">此錯誤表示元件或元件設計工具已呼叫**AddService**方法，這需要介面和物件，但指定的物件未執行指定的介面。</span><span class="sxs-lookup"><span data-stu-id="e1e99-341">This error indicates that a component or component designer has called the **AddService** method, which requires an interface and object, but the object specified does not implement the interface specified.</span></span> <span data-ttu-id="e1e99-342">請洽詢元件廠商。</span><span class="sxs-lookup"><span data-stu-id="e1e99-342">Contact the component vendor.</span></span>

### <a name="the-text-in-the-code-window-could-not-be-modified"></a><span data-ttu-id="e1e99-343">無法修改程式碼視窗中的文字</span><span class="sxs-lookup"><span data-stu-id="e1e99-343">The text in the code window could not be modified</span></span>

<span data-ttu-id="e1e99-344">錯誤訊息：「無法修改程式碼視窗中的文字。</span><span class="sxs-lookup"><span data-stu-id="e1e99-344">Error message: "The text in the code window could not be modified.</span></span> <span data-ttu-id="e1e99-345">檢查檔案不是唯讀的，而且有足夠的磁碟空間。」</span><span class="sxs-lookup"><span data-stu-id="e1e99-345">Check that the file is not read-only and there is sufficient disk space."</span></span>

<span data-ttu-id="e1e99-346">當 Visual Studio 因為磁碟空間或記憶體問題而無法編輯檔案，或檔案標示為唯讀時，就會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1e99-346">This error occurs when Visual Studio is unable to edit a file due to disk space or memory problems, or the file is marked read-only.</span></span>

### <a name="the-toolbox-enumerator-object-only-supports-retrieving-one-item-at-a-time"></a><span data-ttu-id="e1e99-347">工具箱列舉值物件一次只支援擷取一個項目</span><span class="sxs-lookup"><span data-stu-id="e1e99-347">The Toolbox enumerator object only supports retrieving one item at a time</span></span>

<span data-ttu-id="e1e99-348">如果您看到此錯誤，如果您看到此錯誤，請使用 [回報[問題](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)] 來記錄問題。</span><span class="sxs-lookup"><span data-stu-id="e1e99-348">If you see this error, If you see this error, please log an issue by using [Report a Problem](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).</span></span>

### <a name="the-toolbox-item-for-component-name-could-not-be-retrieved-from-the-toolbox"></a><span data-ttu-id="e1e99-349">無法從工具箱抓取 '\<component name > ' 的工具箱專案</span><span class="sxs-lookup"><span data-stu-id="e1e99-349">The Toolbox item for '\<component name>' could not be retrieved from the Toolbox</span></span>

<span data-ttu-id="e1e99-350">錯誤訊息：「無法從工具箱抓取 '\<component name > ' 的工具箱專案。</span><span class="sxs-lookup"><span data-stu-id="e1e99-350">Error message: "The Toolbox item for '\<component name>' could not be retrieved from the Toolbox.</span></span> <span data-ttu-id="e1e99-351">請確定已正確安裝包含 [工具箱] 專案的元件。</span><span class="sxs-lookup"><span data-stu-id="e1e99-351">Make sure the assembly that contains the Toolbox item is correctly installed.</span></span> <span data-ttu-id="e1e99-352">工具箱專案引發下列錯誤： \<錯誤字串 >。」</span><span class="sxs-lookup"><span data-stu-id="e1e99-352">The Toolbox item raised the following error: \<error string>."</span></span>

<span data-ttu-id="e1e99-353">有問題的元件在 Visual Studio 存取時擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e1e99-353">The component in question threw an exception when Visual Studio accessed it.</span></span> <span data-ttu-id="e1e99-354">請洽詢元件廠商。</span><span class="sxs-lookup"><span data-stu-id="e1e99-354">Contact the component vendor.</span></span>

### <a name="the-toolbox-item-for-toolbox-item-name-could-not-be-retrieved-from-the-toolbox"></a><span data-ttu-id="e1e99-355">無法從工具箱抓取 '\<工具箱專案名稱 > ' 的工具箱專案</span><span class="sxs-lookup"><span data-stu-id="e1e99-355">The Toolbox item for '\<Toolbox item name>' could not be retrieved from the Toolbox</span></span>

<span data-ttu-id="e1e99-356">錯誤訊息：「無法從工具箱抓取 '\<工具箱專案名稱 > ' 的工具箱專案。</span><span class="sxs-lookup"><span data-stu-id="e1e99-356">Error message: "The Toolbox item for '\<Toolbox item name>' could not be retrieved from the Toolbox.</span></span> <span data-ttu-id="e1e99-357">請嘗試從 [工具箱] 中移除該專案，然後再將它加回。」</span><span class="sxs-lookup"><span data-stu-id="e1e99-357">Try removing the item from the Toolbox and adding it back."</span></span>

<span data-ttu-id="e1e99-358">如果 [工具箱] 專案內的資料損毀或元件版本已變更，就會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1e99-358">This error occurs if the data within the Toolbox item becomes corrupted or the version of the component has changed.</span></span> <span data-ttu-id="e1e99-359">請嘗試從 [工具箱] 移除該專案，然後再次將它重新加入。</span><span class="sxs-lookup"><span data-stu-id="e1e99-359">Try removing the item from the Toolbox and adding it back again.</span></span>

### <a name="the-type-type-name-could-not-be-found"></a><span data-ttu-id="e1e99-360">找不到\<類型 ' type name > '</span><span class="sxs-lookup"><span data-stu-id="e1e99-360">The type '\<type name>' could not be found</span></span>

<span data-ttu-id="e1e99-361">錯誤訊息：找不到「\<類型 ' 類型名稱 >」。</span><span class="sxs-lookup"><span data-stu-id="e1e99-361">Error message: "The type '\<type name>' could not be found.</span></span> <span data-ttu-id="e1e99-362">請確定已參考包含該類型的元件。</span><span class="sxs-lookup"><span data-stu-id="e1e99-362">Ensure that the assembly containing the type is referenced.</span></span> <span data-ttu-id="e1e99-363">如果元件是目前開發專案的一部分，請確定已建立專案。」</span><span class="sxs-lookup"><span data-stu-id="e1e99-363">If the assembly is part of the current development project, ensure that the project has been built."</span></span>

<span data-ttu-id="e1e99-364">載入設計工具時，Visual Studio 無法找到類型。</span><span class="sxs-lookup"><span data-stu-id="e1e99-364">While loading the designer, Visual Studio failed to find a type.</span></span> <span data-ttu-id="e1e99-365">請確定已參考包含該類型的元件。</span><span class="sxs-lookup"><span data-stu-id="e1e99-365">Ensure that the assembly containing the type is referenced.</span></span> <span data-ttu-id="e1e99-366">如果元件是目前開發專案的一部分，請確定已建立專案。</span><span class="sxs-lookup"><span data-stu-id="e1e99-366">If the assembly is part of the current development project, ensure that the project has been built.</span></span>

### <a name="the-type-resolution-service-may-only-be-called-from-the-main-application-thread"></a><span data-ttu-id="e1e99-367">只能從主應用程式的執行緒中呼叫類型解析服務</span><span class="sxs-lookup"><span data-stu-id="e1e99-367">The type resolution service may only be called from the main application thread</span></span>

<span data-ttu-id="e1e99-368">Visual Studio 嘗試從錯誤的執行緒存取所需的資源。</span><span class="sxs-lookup"><span data-stu-id="e1e99-368">Visual Studio attempted to access required resources from the wrong thread.</span></span> <span data-ttu-id="e1e99-369">當用來建立設計工具的程式碼從主應用程式執行緒以外的執行緒呼叫型別解析服務時，就會顯示此錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1e99-369">This error is displayed when the code used to create the designer has called the type resolution service from a thread other than the main application thread.</span></span> <span data-ttu-id="e1e99-370">若要更正此錯誤，請從正確的執行緒呼叫服務，或洽詢元件廠商。</span><span class="sxs-lookup"><span data-stu-id="e1e99-370">To correct this error, call the service from the correct thread or contact the component vendor.</span></span>

### <a name="the-variable-variable-name-is-either-undeclared-or-was-never-assigned"></a><span data-ttu-id="e1e99-371">變數 '\<variable name > ' 未宣告或從未指派</span><span class="sxs-lookup"><span data-stu-id="e1e99-371">The variable '\<variable name>' is either undeclared or was never assigned</span></span>

<span data-ttu-id="e1e99-372">原始程式碼具有未宣告或指派之變數的參考（例如**Button1**）。</span><span class="sxs-lookup"><span data-stu-id="e1e99-372">The source code has a reference to a variable, such as **Button1**, that isn't declared or assigned.</span></span> <span data-ttu-id="e1e99-373">如果尚未指派變數，此訊息就會顯示為警告，而不是錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1e99-373">If the variable has not been assigned, this message appears as a warning, not an error.</span></span>

### <a name="there-is-already-a-command-handler-for-the-menu-command-menu-command-name"></a><span data-ttu-id="e1e99-374">功能表命令\<的功能表命令名稱 > ' 已經有命令處理常式</span><span class="sxs-lookup"><span data-stu-id="e1e99-374">There is already a command handler for the menu command '\<menu command name>'</span></span>

<span data-ttu-id="e1e99-375">如果協力廠商設計工具將已經有處理常式的命令加入命令資料表中，就會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1e99-375">This error arises if a third-party designer adds a command that already has a handler to the command table.</span></span> <span data-ttu-id="e1e99-376">請洽詢元件廠商。</span><span class="sxs-lookup"><span data-stu-id="e1e99-376">Contact the component vendor.</span></span>

### <a name="there-is-already-a-component-named-component-name"></a><span data-ttu-id="e1e99-377">已經有名為 '\<component name > ' 的元件</span><span class="sxs-lookup"><span data-stu-id="e1e99-377">There is already a component named '\<component name>'</span></span>

<span data-ttu-id="e1e99-378">錯誤訊息：「已經有名為 '\<component name > ' 的元件。</span><span class="sxs-lookup"><span data-stu-id="e1e99-378">Error message: "There is already a component named '\<component name>'.</span></span> <span data-ttu-id="e1e99-379">元件必須有唯一的名稱，而且名稱不得區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="e1e99-379">Components must have unique names, and names must not be case-sensitive.</span></span> <span data-ttu-id="e1e99-380">名稱也不能與繼承類別中任何元件的名稱衝突。」</span><span class="sxs-lookup"><span data-stu-id="e1e99-380">A name also cannot conflict with the name of any component in an inherited class."</span></span>

<span data-ttu-id="e1e99-381">當屬性視窗中的元件名稱有所變更時，就會出現這個錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="e1e99-381">This error message arises when there has been a change to the name of a component in the Properties window.</span></span> <span data-ttu-id="e1e99-382">若要更正這個錯誤，請確定所有元件名稱都是唯一的、不區分大小寫，而且不會與繼承類別中任何元件的名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="e1e99-382">To correct this error, ensure that all component names are unique, are not case-sensitive, and do not conflict with the names of any components in the inherited classes.</span></span>

### <a name="there-is-already-a-toolbox-item-creator-registered-for-the-format-format-name"></a><span data-ttu-id="e1e99-383">已經為 [格式名稱 >] 格式\<註冊工具箱專案建立者</span><span class="sxs-lookup"><span data-stu-id="e1e99-383">There is already a Toolbox item creator registered for the format '\<format name>'</span></span>

<span data-ttu-id="e1e99-384">協力廠商元件對 [工具箱] 索引標籤上的專案進行回呼，但該專案已包含回呼。</span><span class="sxs-lookup"><span data-stu-id="e1e99-384">A third-party component made a callback to an item on a Toolbox tab, but the item already contained a callback.</span></span> <span data-ttu-id="e1e99-385">請洽詢元件廠商。</span><span class="sxs-lookup"><span data-stu-id="e1e99-385">Contact the component vendor.</span></span>

### <a name="this-language-engine-does-not-support-a-codemodel-with-which-to-load-a-designer"></a><span data-ttu-id="e1e99-386">此語言引擎不支援使用 CodeModel 載入設計工具</span><span class="sxs-lookup"><span data-stu-id="e1e99-386">This language engine does not support a CodeModel with which to load a designer</span></span>

<span data-ttu-id="e1e99-387">此訊息類似「此檔案的語言不支援必要的程式碼剖析和產生服務」，但此訊息牽涉到內部註冊問題。</span><span class="sxs-lookup"><span data-stu-id="e1e99-387">This message is similar to "The language for this file does not support the necessary code parsing and generation services", but this message involves an internal registration problem.</span></span> <span data-ttu-id="e1e99-388">如果您看到此錯誤，如果您看到此錯誤，請使用 [回報[問題](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)] 來記錄問題。</span><span class="sxs-lookup"><span data-stu-id="e1e99-388">If you see this error, If you see this error, please log an issue by using [Report a Problem](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).</span></span>

### <a name="type-type-name-does-not-have-a-constructor-with-parameters-of-types-parameter-type-names"></a><span data-ttu-id="e1e99-389">類型 '\<type name\>' 沒有具有參數類型為 '\<參數類型名稱 > ' 的函式</span><span class="sxs-lookup"><span data-stu-id="e1e99-389">Type '\<type name\>' does not have a constructor with parameters of types '\<parameter type names>'</span></span>

<span data-ttu-id="e1e99-390">Visual Studio 找不到具有相符參數的[函數](/dotnet/csharp/programming-guide/classes-and-structs/constructors)。</span><span class="sxs-lookup"><span data-stu-id="e1e99-390">Visual Studio could not find a [constructor](/dotnet/csharp/programming-guide/classes-and-structs/constructors) that had matching parameters.</span></span> <span data-ttu-id="e1e99-391">這可能是因為所需的型別不是必要的類型而提供的。</span><span class="sxs-lookup"><span data-stu-id="e1e99-391">This may be the result of supplying a constructor with types other than those that are required.</span></span> <span data-ttu-id="e1e99-392">例如，**點**函數可能會採用兩個整數。</span><span class="sxs-lookup"><span data-stu-id="e1e99-392">For example, a **Point** constructor might take two integers.</span></span> <span data-ttu-id="e1e99-393">如果您提供浮動，就會引發此錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1e99-393">If you provided floats, this error is raised.</span></span>

<span data-ttu-id="e1e99-394">若要更正這個錯誤，請使用不同的函式，或明確地轉換參數類型，使其符合由函式所提供的型別。</span><span class="sxs-lookup"><span data-stu-id="e1e99-394">To correct this error, use a different constructor or explicitly cast the parameter types such that they match those provided by the constructor.</span></span>

### <a name="unable-to-add-reference-reference-name-to-the-current-application"></a><span data-ttu-id="e1e99-395">無法將參考 '\<參考名稱 > ' 加入至目前的應用程式</span><span class="sxs-lookup"><span data-stu-id="e1e99-395">Unable to add reference '\<reference name>' to the current application</span></span>

<span data-ttu-id="e1e99-396">錯誤訊息：「無法將參考 '\<參考名稱 > ' 加入至目前的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e1e99-396">Error message: "Unable to add reference '\<reference name>' to the current application.</span></span> <span data-ttu-id="e1e99-397">檢查是否有不同版本的 '\<reference name > ' 尚未參考。」</span><span class="sxs-lookup"><span data-stu-id="e1e99-397">Check that a different version of '\<reference name>' is not already referenced."</span></span>

<span data-ttu-id="e1e99-398">Visual Studio 無法加入參考。</span><span class="sxs-lookup"><span data-stu-id="e1e99-398">Visual Studio is unable to add a reference.</span></span> <span data-ttu-id="e1e99-399">若要更正此錯誤，請檢查是否有其他版本的參考尚未被參考。</span><span class="sxs-lookup"><span data-stu-id="e1e99-399">To correct this error, check that a different version of the reference is not already referenced.</span></span>

### <a name="unable-to-check-out-the-current-file"></a><span data-ttu-id="e1e99-400">無法簽出目前的檔案</span><span class="sxs-lookup"><span data-stu-id="e1e99-400">Unable to check out the current file</span></span>

<span data-ttu-id="e1e99-401">錯誤訊息：「無法簽出目前的檔案。</span><span class="sxs-lookup"><span data-stu-id="e1e99-401">Error message: "Unable to check out the current file.</span></span> <span data-ttu-id="e1e99-402">檔案可能已鎖定，或您可能需要手動簽出檔案。」</span><span class="sxs-lookup"><span data-stu-id="e1e99-402">The file may be locked, or you may need to check out the file manually."</span></span>

<span data-ttu-id="e1e99-403">當您將目前簽入的檔案變更為原始程式碼控制時，就會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1e99-403">This error arises when you change a file that's currently checked in to source-code control.</span></span> <span data-ttu-id="e1e99-404">Visual Studio 通常會顯示 [檔案簽出] 對話方塊，讓使用者可以簽出檔案。</span><span class="sxs-lookup"><span data-stu-id="e1e99-404">Usually, Visual Studio presents the file checkout dialog box so that the user can check out the file.</span></span> <span data-ttu-id="e1e99-405">這次檔案未簽出，可能是因為在簽出期間發生合併衝突。</span><span class="sxs-lookup"><span data-stu-id="e1e99-405">This time, the file was not checked out, perhaps because of a merge conflict during checkout.</span></span> <span data-ttu-id="e1e99-406">若要更正此錯誤，請確定檔案未鎖定，然後嘗試手動簽出檔案。</span><span class="sxs-lookup"><span data-stu-id="e1e99-406">To correct this error, ensure that the file is not locked, and then try to check out the file manually.</span></span>

### <a name="unable-to-find-page-named-options-dialog-box-tab-name"></a><span data-ttu-id="e1e99-407">找不到名為\<[選項對話方塊索引標籤名稱 >] 的頁面</span><span class="sxs-lookup"><span data-stu-id="e1e99-407">Unable to find page named '\<Options dialog box tab name>'</span></span>

<span data-ttu-id="e1e99-408">當元件設計工具使用不存在的名稱，從 [選項] 對話方塊要求存取頁面時，就會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1e99-408">This error arises when a component designer requests access to a page from the Options dialog box by using a name that does not exist.</span></span> <span data-ttu-id="e1e99-409">請洽詢元件廠商。</span><span class="sxs-lookup"><span data-stu-id="e1e99-409">Contact the component vendor.</span></span>

### <a name="unable-to-find-property-property-name-on-page-options-dialog-box-tab-name"></a><span data-ttu-id="e1e99-410">在頁面上的\< \<[選項] 對話方塊索引標籤名稱 > ' 中找不到屬性 ' 屬性名稱 > '</span><span class="sxs-lookup"><span data-stu-id="e1e99-410">Unable to find property '\<property name>' on page '\<Options dialog box tab name>'</span></span>

<span data-ttu-id="e1e99-411">當元件設計工具要求 [選項] 對話方塊中的頁面上有特定值的存取權，但該值不存在時，就會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1e99-411">This error arises when a component designer requests access to a particular value on a page from the Options dialog box, but that value does not exist.</span></span> <span data-ttu-id="e1e99-412">請洽詢元件廠商。</span><span class="sxs-lookup"><span data-stu-id="e1e99-412">Contact the component vendor.</span></span>

### <a name="visual-studio-cannot-open-a-designer-for-the-file-because-the-class-within-it-does-not-inherit-from-a-class-that-can-be-visually-designed"></a><span data-ttu-id="e1e99-413">Visual Studio 無法開啟這個檔案的設計工具，因為它裡面的類別不會從能以視覺化方式設計的類別繼承</span><span class="sxs-lookup"><span data-stu-id="e1e99-413">Visual Studio cannot open a designer for the file because the class within it does not inherit from a class that can be visually designed</span></span>

<span data-ttu-id="e1e99-414">Visual Studio 已載入類別，但無法載入該類別的設計工具。</span><span class="sxs-lookup"><span data-stu-id="e1e99-414">Visual Studio loaded the class, but the designer for that class could not be loaded.</span></span> <span data-ttu-id="e1e99-415">Visual Studio 需要設計工具使用檔案中的第一個類別。</span><span class="sxs-lookup"><span data-stu-id="e1e99-415">Visual Studio requires that designers use the first class in a file.</span></span> <span data-ttu-id="e1e99-416">若要更正這個錯誤，請移動類別程式碼，使其成為檔案中的第一個類別，然後再次載入設計工具。</span><span class="sxs-lookup"><span data-stu-id="e1e99-416">To correct this error, move the class code so that it is the first class in the file, and then load the designer again.</span></span>

### <a name="visual-studio-cannot-save-or-load-instances-of-the-type-type-name"></a><span data-ttu-id="e1e99-417">Visual Studio 無法儲存或載入類型 '\<type name > ' 的實例</span><span class="sxs-lookup"><span data-stu-id="e1e99-417">Visual Studio cannot save or load instances of the type '\<type name>'</span></span>

<span data-ttu-id="e1e99-418">這是協力廠商元件的問題。</span><span class="sxs-lookup"><span data-stu-id="e1e99-418">This is a problem with a third-party component.</span></span> <span data-ttu-id="e1e99-419">請洽詢元件廠商。</span><span class="sxs-lookup"><span data-stu-id="e1e99-419">Contact the component vendor.</span></span>

### <a name="visual-studio-is-unable-to-open-document-name-in-design-view"></a><span data-ttu-id="e1e99-420">Visual Studio 無法在設計檢視中開啟\<「檔案名稱 >」</span><span class="sxs-lookup"><span data-stu-id="e1e99-420">Visual Studio is unable to open '\<document name>' in Design view</span></span>

<span data-ttu-id="e1e99-421">錯誤訊息：「Visual Studio 無法在設計檢視中開啟\<「檔案名稱 >」。</span><span class="sxs-lookup"><span data-stu-id="e1e99-421">Error message: "Visual Studio is unable to open '\<document name>' in Design view.</span></span> <span data-ttu-id="e1e99-422">未安裝檔案類型的剖析器。」</span><span class="sxs-lookup"><span data-stu-id="e1e99-422">No parser is installed for the file type."</span></span>

<span data-ttu-id="e1e99-423">此錯誤表示專案的語言不支援設計工具，而且當您嘗試在 [開啟檔案] 對話方塊或方案總管中開啟檔案時，就會發生此問題。</span><span class="sxs-lookup"><span data-stu-id="e1e99-423">This error indicates that the language of the project does not support a designer and arises when you attempt to open a file in the Open File dialog box or from Solution Explorer.</span></span> <span data-ttu-id="e1e99-424">相反地，請在程式碼視圖中編輯檔案。</span><span class="sxs-lookup"><span data-stu-id="e1e99-424">Instead, edit the file in Code view.</span></span>

### <a name="visual-studio-was-unable-to-find-a-designer-for-classes-of-type-type-name"></a><span data-ttu-id="e1e99-425">Visual Studio 找不到類型\<為「類型名稱 >」之類別的設計工具</span><span class="sxs-lookup"><span data-stu-id="e1e99-425">Visual Studio was unable to find a designer for classes of type '\<type name>'</span></span>

<span data-ttu-id="e1e99-426">Visual Studio 已載入類別，但無法設計類別。</span><span class="sxs-lookup"><span data-stu-id="e1e99-426">Visual Studio loaded the class, but the class cannot be designed.</span></span> <span data-ttu-id="e1e99-427">相反地，請在程式碼視圖中編輯類別，方法是以滑鼠右鍵按一下類別，然後選擇 [ **View Code**]。</span><span class="sxs-lookup"><span data-stu-id="e1e99-427">Instead, edit the class in Code view by right-clicking the class and choosing **View Code**.</span></span>

## <a name="see-also"></a><span data-ttu-id="e1e99-428">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1e99-428">See also</span></span>

- [<span data-ttu-id="e1e99-429">使用設計工具開發 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="e1e99-429">Develop Windows Forms controls using the designer</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="e1e99-430">Windows Form 設計工具論壇</span><span class="sxs-lookup"><span data-stu-id="e1e99-430">Windows Forms Designer forum</span></span>](https://social.msdn.microsoft.com/Forums/windows/home?forum=winformsdesigner)
