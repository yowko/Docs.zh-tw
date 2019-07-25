---
title: Visual Basic 編碼慣例
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
ms.openlocfilehash: 580a6e1caa78ea981b6d2be68a6e7c61e2ad55d7
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433816"
---
# <a name="visual-basic-coding-conventions"></a><span data-ttu-id="674be-102">Visual Basic 編碼慣例</span><span class="sxs-lookup"><span data-stu-id="674be-102">Visual Basic Coding Conventions</span></span>
<span data-ttu-id="674be-103">Microsoft 會依照本主題中的指導方針來開發範例和檔。</span><span class="sxs-lookup"><span data-stu-id="674be-103">Microsoft develops samples and documentation that follow the guidelines in this topic.</span></span> <span data-ttu-id="674be-104">如果您遵循相同的編碼慣例, 您可能會獲得下列優點:</span><span class="sxs-lookup"><span data-stu-id="674be-104">If you follow the same coding conventions, you may gain the following benefits:</span></span>  
  
- <span data-ttu-id="674be-105">您的程式碼會有一致的外觀, 讓讀者可以更專注于內容, 而不是版面配置。</span><span class="sxs-lookup"><span data-stu-id="674be-105">Your code will have a consistent look, so that readers can better focus on content, not layout.</span></span>  
  
- <span data-ttu-id="674be-106">讀者會更快速地瞭解您的程式碼, 因為它們可以根據先前的經驗做出假設。</span><span class="sxs-lookup"><span data-stu-id="674be-106">Readers understand your code more quickly because they can make assumptions based on previous experience.</span></span>  
  
- <span data-ttu-id="674be-107">您可以更輕鬆地複製、變更及維護程式碼。</span><span class="sxs-lookup"><span data-stu-id="674be-107">You can copy, change, and maintain the code more easily.</span></span>  
  
- <span data-ttu-id="674be-108">您可以協助確保您的程式碼會針對 Visual Basic 示範「最佳做法」。</span><span class="sxs-lookup"><span data-stu-id="674be-108">You help ensure that your code demonstrates "best practices" for Visual Basic.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="674be-109">命名規範</span><span class="sxs-lookup"><span data-stu-id="674be-109">Naming Conventions</span></span>  
  
- <span data-ttu-id="674be-110">如需命名指導方針的詳細資訊, 請參閱[命名指導方針](../../../standard/design-guidelines/naming-guidelines.md)主題。</span><span class="sxs-lookup"><span data-stu-id="674be-110">For information about naming guidelines, see [Naming Guidelines](../../../standard/design-guidelines/naming-guidelines.md) topic.</span></span>  
  
- <span data-ttu-id="674be-111">請勿使用 "My" 或 "my" 作為變數名稱的一部分。</span><span class="sxs-lookup"><span data-stu-id="674be-111">Do not use "My" or "my" as part of a variable name.</span></span> <span data-ttu-id="674be-112">這種作法會與`My`物件產生混淆。</span><span class="sxs-lookup"><span data-stu-id="674be-112">This practice creates confusion with the `My` objects.</span></span>  
  
- <span data-ttu-id="674be-113">您不需要在自動產生的程式碼中變更物件的名稱, 使其符合方針。</span><span class="sxs-lookup"><span data-stu-id="674be-113">You do not have to change the names of objects in auto-generated code to make them fit the guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="674be-114">版面配置慣例</span><span class="sxs-lookup"><span data-stu-id="674be-114">Layout Conventions</span></span>  
  
- <span data-ttu-id="674be-115">將索引標籤插入空格, 並使用具有四個空格縮排的智慧型縮排。</span><span class="sxs-lookup"><span data-stu-id="674be-115">Insert tabs as spaces, and use smart indenting with four-space indents.</span></span>  
  
- <span data-ttu-id="674be-116">使用程式**代碼的整齊清單 (重新格式化)** , 在程式碼編輯器中重新格式化您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="674be-116">Use **Pretty listing (reformatting) of code** to reformat your code in the code editor.</span></span> <span data-ttu-id="674be-117">如需詳細資訊, 請參閱[選項、文字編輯器、基本 (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="674be-117">For more information, see [Options, Text Editor, Basic (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).</span></span>  
  
- <span data-ttu-id="674be-118">每行只能使用一個語句。</span><span class="sxs-lookup"><span data-stu-id="674be-118">Use only one statement per line.</span></span> <span data-ttu-id="674be-119">請勿使用 Visual Basic 行分隔字元 (:)。</span><span class="sxs-lookup"><span data-stu-id="674be-119">Don't use the Visual Basic line separator character (:).</span></span>  
  
- <span data-ttu-id="674be-120">請避免使用明確行接續字元 "_", 以在語言允許的地方隱含行接續。</span><span class="sxs-lookup"><span data-stu-id="674be-120">Avoid using the explicit line continuation character "_" in favor of implicit line continuation wherever the language allows it.</span></span>  
  
- <span data-ttu-id="674be-121">每行只能使用一個宣告。</span><span class="sxs-lookup"><span data-stu-id="674be-121">Use only one declaration per line.</span></span>  
  
- <span data-ttu-id="674be-122">如果程式**代碼的整齊清單 (重新格式化)** 不會自動格式化接續行, 請手動將接續行縮排一次定位停駐點。</span><span class="sxs-lookup"><span data-stu-id="674be-122">If **Pretty listing (reformatting) of code** doesn't format continuation lines automatically, manually indent continuation lines one tab stop.</span></span> <span data-ttu-id="674be-123">不過, 一律會靠左對齊清單中的專案。</span><span class="sxs-lookup"><span data-stu-id="674be-123">However, always left-align items in a list.</span></span>  
  
    ```  
    a As Integer,  
    b As Integer  
    ```  
  
- <span data-ttu-id="674be-124">在方法和屬性定義之間新增至少一個空白行。</span><span class="sxs-lookup"><span data-stu-id="674be-124">Add at least one blank line between method and property definitions.</span></span>  
  
## <a name="commenting-conventions"></a><span data-ttu-id="674be-125">註解慣例</span><span class="sxs-lookup"><span data-stu-id="674be-125">Commenting Conventions</span></span>  
  
- <span data-ttu-id="674be-126">將批註放在另一行, 而不是一行程式碼的結尾。</span><span class="sxs-lookup"><span data-stu-id="674be-126">Put comments on a separate line instead of at the end of a line of code.</span></span>  
  
- <span data-ttu-id="674be-127">以大寫字母開始註解文字, 並以句點結束註解文字。</span><span class="sxs-lookup"><span data-stu-id="674be-127">Start comment text with an uppercase letter, and end comment text with a period.</span></span>  
  
- <span data-ttu-id="674be-128">在批註分隔符號 (') 和註解文字之間插入一個空格。</span><span class="sxs-lookup"><span data-stu-id="674be-128">Insert one space between the comment delimiter (') and the comment text.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#2)]  
  
- <span data-ttu-id="674be-129">不要以星號的格式化區塊來括住批註。</span><span class="sxs-lookup"><span data-stu-id="674be-129">Do not surround comments with formatted blocks of asterisks.</span></span>  
  
## <a name="program-structure"></a><span data-ttu-id="674be-130">程式結構</span><span class="sxs-lookup"><span data-stu-id="674be-130">Program Structure</span></span>  
  
- <span data-ttu-id="674be-131">當您使用`Main`方法時, 請使用新的主控台應用程式的預設結構, `My`並使用做為命令列引數。</span><span class="sxs-lookup"><span data-stu-id="674be-131">When you use the `Main` method, use the default construct for new console applications, and use `My` for command-line arguments.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#3)]  
  
## <a name="language-guidelines"></a><span data-ttu-id="674be-132">語言指導方針</span><span class="sxs-lookup"><span data-stu-id="674be-132">Language Guidelines</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="674be-133">String 資料類型</span><span class="sxs-lookup"><span data-stu-id="674be-133">String Data Type</span></span>  
  
- <span data-ttu-id="674be-134">使用[字串內插補點](https://docs.microsoft.com/dotnet/visual-basic/programming-guide/language-features/strings/interpolated-strings)串連短字串，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="674be-134">Use [string interpolation](https://docs.microsoft.com/dotnet/visual-basic/programming-guide/language-features/strings/interpolated-strings) to concatenate short strings, as shown in the following code.</span></span>
  
     ```vb
     MsgBox($"hello{vbCrLf}goodbye")
     ```
  
- <span data-ttu-id="674be-135">若要在迴圈中附加字串, <xref:System.Text.StringBuilder>請使用物件。</span><span class="sxs-lookup"><span data-stu-id="674be-135">To append strings in loops, use the <xref:System.Text.StringBuilder> object.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#5)]  
  
### <a name="relaxed-delegates-in-event-handlers"></a><span data-ttu-id="674be-136">事件處理常式中的寬鬆委派</span><span class="sxs-lookup"><span data-stu-id="674be-136">Relaxed Delegates in Event Handlers</span></span>  
 <span data-ttu-id="674be-137">請勿將引數 (物件和 EventArgs) 明確限定為事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="674be-137">Do not explicitly qualify the arguments (Object and EventArgs) to event handlers.</span></span> <span data-ttu-id="674be-138">如果您不是使用傳遞至事件的事件引數 (例如, 傳送者作為物件, e as EventArgs), 請使用寬鬆的委派, 並在您的程式碼中省略事件引數:</span><span class="sxs-lookup"><span data-stu-id="674be-138">If you are not using the event arguments that are passed to an event (for example, sender as Object, e as EventArgs), use relaxed delegates, and leave out the event arguments in your code:</span></span>  
  
 [!code-vb[VbVbalrGuidelines#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#7)]  
  
### <a name="unsigned-data-type"></a><span data-ttu-id="674be-139">不帶正負號的資料類型</span><span class="sxs-lookup"><span data-stu-id="674be-139">Unsigned Data Type</span></span>  
  
- <span data-ttu-id="674be-140">使用`Integer` , 而不是不帶正負號的類型, 但必要的位置除外。</span><span class="sxs-lookup"><span data-stu-id="674be-140">Use `Integer` rather than unsigned types, except where they are necessary.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="674be-141">陣列</span><span class="sxs-lookup"><span data-stu-id="674be-141">Arrays</span></span>  
  
- <span data-ttu-id="674be-142">當您在宣告行上初始化陣列時, 請使用簡短的語法。</span><span class="sxs-lookup"><span data-stu-id="674be-142">Use the short syntax when you initialize arrays on the declaration line.</span></span> <span data-ttu-id="674be-143">例如, 使用下列語法。</span><span class="sxs-lookup"><span data-stu-id="674be-143">For example, use the following syntax.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#8)]  
  
     <span data-ttu-id="674be-144">請勿使用下列語法。</span><span class="sxs-lookup"><span data-stu-id="674be-144">Do not use the following syntax.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#9)]  
  
- <span data-ttu-id="674be-145">將陣列指示項放在型別上, 而不是在變數上。</span><span class="sxs-lookup"><span data-stu-id="674be-145">Put the array designator on the type, not on the variable.</span></span> <span data-ttu-id="674be-146">例如, 使用下列語法:</span><span class="sxs-lookup"><span data-stu-id="674be-146">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#11)]  
  
     <span data-ttu-id="674be-147">請勿使用下列語法:</span><span class="sxs-lookup"><span data-stu-id="674be-147">Do not use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#10)]  
  
- <span data-ttu-id="674be-148">當您宣告並初始化基本資料類型的陣列時, 請使用 {} 語法。</span><span class="sxs-lookup"><span data-stu-id="674be-148">Use the { } syntax when you declare and initialize arrays of basic data types.</span></span> <span data-ttu-id="674be-149">例如, 使用下列語法:</span><span class="sxs-lookup"><span data-stu-id="674be-149">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#12)]  
  
     <span data-ttu-id="674be-150">請勿使用下列語法:</span><span class="sxs-lookup"><span data-stu-id="674be-150">Do not use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#13)]  
  
### <a name="use-the-with-keyword"></a><span data-ttu-id="674be-151">使用 With 關鍵字</span><span class="sxs-lookup"><span data-stu-id="674be-151">Use the With Keyword</span></span>  
 <span data-ttu-id="674be-152">當您對一個物件進行一系列的呼叫時, 請考慮`With`使用關鍵字:</span><span class="sxs-lookup"><span data-stu-id="674be-152">When you make a series of calls to one object, consider using the `With` keyword:</span></span>  
  
 [!code-vb[VbVbalrGuidelines#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#15)]  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a><span data-ttu-id="674be-153">使用 [嘗試 ...]使用例外狀況處理時的 Catch 和 Using 語句</span><span class="sxs-lookup"><span data-stu-id="674be-153">Use the Try...Catch and Using Statements when you use Exception Handling</span></span>  
 <span data-ttu-id="674be-154">請勿使用 `On Error Goto`。</span><span class="sxs-lookup"><span data-stu-id="674be-154">Do not use `On Error Goto`.</span></span>  
  
### <a name="use-the-isnot-keyword"></a><span data-ttu-id="674be-155">使用 IsNot 關鍵字</span><span class="sxs-lookup"><span data-stu-id="674be-155">Use the IsNot Keyword</span></span>  
 <span data-ttu-id="674be-156">請使用`IsNot`關鍵字, `Not...Is Nothing`而不是。</span><span class="sxs-lookup"><span data-stu-id="674be-156">Use the `IsNot` keyword instead of `Not...Is Nothing`.</span></span>  
  
### <a name="new-keyword"></a><span data-ttu-id="674be-157">New 關鍵字</span><span class="sxs-lookup"><span data-stu-id="674be-157">New Keyword</span></span>  
  
- <span data-ttu-id="674be-158">使用簡短的具現化。</span><span class="sxs-lookup"><span data-stu-id="674be-158">Use short instantiation.</span></span> <span data-ttu-id="674be-159">例如, 使用下列語法:</span><span class="sxs-lookup"><span data-stu-id="674be-159">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#21)]  
  
     <span data-ttu-id="674be-160">上一行相當於:</span><span class="sxs-lookup"><span data-stu-id="674be-160">The preceding line is equivalent to this:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#22)]  
  
- <span data-ttu-id="674be-161">針對新物件使用物件初始化運算式, 而不是無參數的函式:</span><span class="sxs-lookup"><span data-stu-id="674be-161">Use object initializers for new objects instead of the parameterless constructor:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#23)]  
  
### <a name="event-handling"></a><span data-ttu-id="674be-162">事件處理</span><span class="sxs-lookup"><span data-stu-id="674be-162">Event Handling</span></span>  
  
- <span data-ttu-id="674be-163">使用`Handles` ,`AddHandler`而不是:</span><span class="sxs-lookup"><span data-stu-id="674be-163">Use `Handles` rather than `AddHandler`:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#24)]  
  
- <span data-ttu-id="674be-164">使用`AddressOf`, 而且不明確地具現化委派:</span><span class="sxs-lookup"><span data-stu-id="674be-164">Use `AddressOf`, and do not instantiate the delegate explicitly:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#25)]  
  
- <span data-ttu-id="674be-165">當您定義事件時, 請使用簡短語法, 並讓編譯器定義委派:</span><span class="sxs-lookup"><span data-stu-id="674be-165">When you define an event, use the short syntax, and let the compiler define the delegate:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#26)]  
  
- <span data-ttu-id="674be-166">`Nothing` 在`RaiseEvent`呼叫方法之前, 請不要驗證事件是否為 (null)。</span><span class="sxs-lookup"><span data-stu-id="674be-166">Do not verify whether an event is `Nothing` (null) before you call the `RaiseEvent` method.</span></span> <span data-ttu-id="674be-167">`RaiseEvent`在引發`Nothing`事件之前, 檢查是否有。</span><span class="sxs-lookup"><span data-stu-id="674be-167">`RaiseEvent` checks for `Nothing` before it raises the event.</span></span>  
  
### <a name="using-shared-members"></a><span data-ttu-id="674be-168">使用共用成員</span><span class="sxs-lookup"><span data-stu-id="674be-168">Using Shared Members</span></span>  
 <span data-ttu-id="674be-169">使用`Shared`類別名稱呼叫成員, 而不是從執行個體變數。</span><span class="sxs-lookup"><span data-stu-id="674be-169">Call `Shared` members by using the class name, not from an instance variable.</span></span>  
  
### <a name="use-xml-literals"></a><span data-ttu-id="674be-170">使用 XML 常值</span><span class="sxs-lookup"><span data-stu-id="674be-170">Use XML Literals</span></span>  
 <span data-ttu-id="674be-171">XML 常值可簡化您在使用 XML 時所遇到的最常見工作 (例如, 載入、查詢和轉換)。</span><span class="sxs-lookup"><span data-stu-id="674be-171">XML literals simplify the most common tasks that you encounter when you work with XML (for example, load, query, and transform).</span></span> <span data-ttu-id="674be-172">當您使用 XML 進行開發時, 請遵循下列指導方針:</span><span class="sxs-lookup"><span data-stu-id="674be-172">When you develop with XML, follow these guidelines:</span></span>  
  
- <span data-ttu-id="674be-173">使用 XML 常值來建立 XML 檔和片段, 而不是直接呼叫 XML Api。</span><span class="sxs-lookup"><span data-stu-id="674be-173">Use XML literals to create XML documents and fragments instead of calling XML APIs directly.</span></span>  
  
- <span data-ttu-id="674be-174">匯入檔案或專案層級的 XML 命名空間, 以利用 XML 常值的效能優化。</span><span class="sxs-lookup"><span data-stu-id="674be-174">Import XML namespaces at the file or project level to take advantage of the performance optimizations for XML literals.</span></span>  
  
- <span data-ttu-id="674be-175">使用 XML 軸屬性來存取 XML 檔中的元素和屬性。</span><span class="sxs-lookup"><span data-stu-id="674be-175">Use the XML axis properties to access elements and attributes in an XML document.</span></span>  
  
- <span data-ttu-id="674be-176">使用內嵌運算式來包含值, 並從現有的值建立 XML, 而不是使用 API 呼叫`Add` , 例如方法:</span><span class="sxs-lookup"><span data-stu-id="674be-176">Use embedded expressions to include values and to create XML from existing values instead of using API calls such as the `Add` method:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#27)]  
  
### <a name="linq-queries"></a><span data-ttu-id="674be-177">LINQ 查詢</span><span class="sxs-lookup"><span data-stu-id="674be-177">LINQ Queries</span></span>  
  
- <span data-ttu-id="674be-178">針對查詢變數使用有意義的名稱:</span><span class="sxs-lookup"><span data-stu-id="674be-178">Use meaningful names for query variables:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#28)]  
  
- <span data-ttu-id="674be-179">在查詢中提供元素的名稱, 以確定匿名型別的屬性名稱使用 Pascal 大小寫正確地大寫:</span><span class="sxs-lookup"><span data-stu-id="674be-179">Provide names for elements in a query to make sure that property names of anonymous types are correctly capitalized using Pascal casing:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#29)]  
  
- <span data-ttu-id="674be-180">當結果中的屬性名稱可能會造成混淆時，請重新命名屬性。</span><span class="sxs-lookup"><span data-stu-id="674be-180">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="674be-181">例如, 如果您的查詢傳回客戶名稱和訂單識別碼, 請將其重新命名, 而不要在`Name`結果`ID`中將它們保留為和:</span><span class="sxs-lookup"><span data-stu-id="674be-181">For example, if your query returns a customer name and an order ID, rename them instead of leaving them as `Name` and `ID` in the result:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#30)]  
  
- <span data-ttu-id="674be-182">在查詢變數和範圍變數的宣告中使用類型推斷:</span><span class="sxs-lookup"><span data-stu-id="674be-182">Use type inference in the declaration of query variables and range variables:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#31)]  
  
- <span data-ttu-id="674be-183">在`From`語句底下對齊查詢子句:</span><span class="sxs-lookup"><span data-stu-id="674be-183">Align query clauses under the `From` statement:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#32)]  
  
- <span data-ttu-id="674be-184">在`Where`其他查詢子句之前使用子句, 讓稍後的查詢子句在篩選的資料集上運作:</span><span class="sxs-lookup"><span data-stu-id="674be-184">Use `Where` clauses before other query clauses so that later query clauses operate on the filtered set of data:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#33)]  
  
- <span data-ttu-id="674be-185">使用子句來明確定義聯結作業, 而不是`Where`使用子句來隱含定義聯結運算: `Join`</span><span class="sxs-lookup"><span data-stu-id="674be-185">Use the `Join` clause to explicitly define a join operation instead of using the `Where` clause to implicitly define a join operation:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#34)]  
  
## <a name="see-also"></a><span data-ttu-id="674be-186">另請參閱</span><span class="sxs-lookup"><span data-stu-id="674be-186">See also</span></span>

- [<span data-ttu-id="674be-187">安全程式碼撰寫方針</span><span class="sxs-lookup"><span data-stu-id="674be-187">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)
