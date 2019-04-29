---
title: Visual Basic 編碼慣例
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
ms.openlocfilehash: f73648888b28c349104a70e78c29eb208d438b78
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761685"
---
# <a name="visual-basic-coding-conventions"></a><span data-ttu-id="889af-102">Visual Basic 編碼慣例</span><span class="sxs-lookup"><span data-stu-id="889af-102">Visual Basic Coding Conventions</span></span>
<span data-ttu-id="889af-103">Microsoft 開發範例和文件，請遵循本主題中的指導方針。</span><span class="sxs-lookup"><span data-stu-id="889af-103">Microsoft develops samples and documentation that follow the guidelines in this topic.</span></span> <span data-ttu-id="889af-104">如果您遵循相同的程式碼撰寫慣例，您可能會獲得下列好處：</span><span class="sxs-lookup"><span data-stu-id="889af-104">If you follow the same coding conventions, you may gain the following benefits:</span></span>  
  
- <span data-ttu-id="889af-105">程式碼會有一致的外觀，讓讀者能夠更專注於未配置的內容。</span><span class="sxs-lookup"><span data-stu-id="889af-105">Your code will have a consistent look, so that readers can better focus on content, not layout.</span></span>  
  
- <span data-ttu-id="889af-106">讀者了解您的程式碼更快速地因為它們會使先前的經驗為基礎的假設。</span><span class="sxs-lookup"><span data-stu-id="889af-106">Readers understand your code more quickly because they can make assumptions based on previous experience.</span></span>  
  
- <span data-ttu-id="889af-107">您可以複製、 變更及更輕鬆地維護程式碼。</span><span class="sxs-lookup"><span data-stu-id="889af-107">You can copy, change, and maintain the code more easily.</span></span>  
  
- <span data-ttu-id="889af-108">您可以協助確保您的程式碼會示範 Visual Basic 的 「 最佳作法 」。</span><span class="sxs-lookup"><span data-stu-id="889af-108">You help ensure that your code demonstrates "best practices" for Visual Basic.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="889af-109">命名規範</span><span class="sxs-lookup"><span data-stu-id="889af-109">Naming Conventions</span></span>  
  
- <span data-ttu-id="889af-110">命名方針的相關資訊，請參閱[命名方針](../../../standard/design-guidelines/naming-guidelines.md)主題。</span><span class="sxs-lookup"><span data-stu-id="889af-110">For information about naming guidelines, see [Naming Guidelines](../../../standard/design-guidelines/naming-guidelines.md) topic.</span></span>  
  
- <span data-ttu-id="889af-111">請勿使用"My"my"做為變數名稱的一部分。</span><span class="sxs-lookup"><span data-stu-id="889af-111">Do not use "My" or "my" as part of a variable name.</span></span> <span data-ttu-id="889af-112">這種做法會建立與混淆`My`物件。</span><span class="sxs-lookup"><span data-stu-id="889af-112">This practice creates confusion with the `My` objects.</span></span>  
  
- <span data-ttu-id="889af-113">您不必變更自動產生程式碼，使其符合方針中的物件名稱。</span><span class="sxs-lookup"><span data-stu-id="889af-113">You do not have to change the names of objects in auto-generated code to make them fit the guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="889af-114">版面配置慣例</span><span class="sxs-lookup"><span data-stu-id="889af-114">Layout Conventions</span></span>  
  
- <span data-ttu-id="889af-115">插入定位點做為空格，並使用具有四個空格縮排的智慧縮排。</span><span class="sxs-lookup"><span data-stu-id="889af-115">Insert tabs as spaces, and use smart indenting with four-space indents.</span></span>  
  
- <span data-ttu-id="889af-116">使用**美化排列 （重新格式化） 的程式碼**重新格式化程式碼編輯器中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="889af-116">Use **Pretty listing (reformatting) of code** to reformat your code in the code editor.</span></span> <span data-ttu-id="889af-117">如需詳細資訊，請參閱 <<c0> [ 選項、 文字編輯器、 基本 (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="889af-117">For more information, see [Options, Text Editor, Basic (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).</span></span>  
  
- <span data-ttu-id="889af-118">使用每一行只有一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="889af-118">Use only one statement per line.</span></span> <span data-ttu-id="889af-119">請勿使用 Visual Basic 分隔符號字元 （:）。</span><span class="sxs-lookup"><span data-stu-id="889af-119">Don't use the Visual Basic line separator character (:).</span></span>  
  
- <span data-ttu-id="889af-120">請避免使用明確行接續字元"_"而隱含行接續，在語言允許它。</span><span class="sxs-lookup"><span data-stu-id="889af-120">Avoid using the explicit line continuation character "_" in favor of implicit line continuation wherever the language allows it.</span></span>  
  
- <span data-ttu-id="889af-121">使用每一行只有一個宣告。</span><span class="sxs-lookup"><span data-stu-id="889af-121">Use only one declaration per line.</span></span>  
  
- <span data-ttu-id="889af-122">如果**美化排列 （重新格式化） 的程式碼**不格式化接續行自動、 手動縮排接續行一個定位停駐點。</span><span class="sxs-lookup"><span data-stu-id="889af-122">If **Pretty listing (reformatting) of code** doesn't format continuation lines automatically, manually indent continuation lines one tab stop.</span></span> <span data-ttu-id="889af-123">不過，永遠靠左對齊清單中的項目。</span><span class="sxs-lookup"><span data-stu-id="889af-123">However, always left-align items in a list.</span></span>  
  
    ```  
    a As Integer,  
    b As Integer  
    ```  
  
- <span data-ttu-id="889af-124">加入方法和屬性定義之間的至少一個空白行。</span><span class="sxs-lookup"><span data-stu-id="889af-124">Add at least one blank line between method and property definitions.</span></span>  
  
## <a name="commenting-conventions"></a><span data-ttu-id="889af-125">註解慣例</span><span class="sxs-lookup"><span data-stu-id="889af-125">Commenting Conventions</span></span>  
  
- <span data-ttu-id="889af-126">將註解放到結尾的一行程式碼，而不是個別行上。</span><span class="sxs-lookup"><span data-stu-id="889af-126">Put comments on a separate line instead of at the end of a line of code.</span></span>  
  
- <span data-ttu-id="889af-127">開始以大寫字母，註解文字，並以句號結束註解文字。</span><span class="sxs-lookup"><span data-stu-id="889af-127">Start comment text with an uppercase letter, and end comment text with a period.</span></span>  
  
- <span data-ttu-id="889af-128">插入註解分隔符號 （'） 與註解文字之間的一個空格。</span><span class="sxs-lookup"><span data-stu-id="889af-128">Insert one space between the comment delimiter (') and the comment text.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#2)]  
  
- <span data-ttu-id="889af-129">請勿用格式化星號區塊註解。</span><span class="sxs-lookup"><span data-stu-id="889af-129">Do not surround comments with formatted blocks of asterisks.</span></span>  
  
## <a name="program-structure"></a><span data-ttu-id="889af-130">程式結構</span><span class="sxs-lookup"><span data-stu-id="889af-130">Program Structure</span></span>  
  
- <span data-ttu-id="889af-131">當您使用`Main`方法，使用預設建構新的主控台應用程式，並使用`My`命令列引數。</span><span class="sxs-lookup"><span data-stu-id="889af-131">When you use the `Main` method, use the default construct for new console applications, and use `My` for command-line arguments.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#3)]  
  
## <a name="language-guidelines"></a><span data-ttu-id="889af-132">語言指導方針</span><span class="sxs-lookup"><span data-stu-id="889af-132">Language Guidelines</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="889af-133">String 資料類型</span><span class="sxs-lookup"><span data-stu-id="889af-133">String Data Type</span></span>  
  
- <span data-ttu-id="889af-134">若要串連字串，請使用連字號 (&)。</span><span class="sxs-lookup"><span data-stu-id="889af-134">To concatenate strings, use an ampersand (&).</span></span>  
  
     [!code-vb[VbVbalrGuidelines#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#4)]  
  
- <span data-ttu-id="889af-135">若要附加在迴圈中的字串，請使用<xref:System.Text.StringBuilder>物件。</span><span class="sxs-lookup"><span data-stu-id="889af-135">To append strings in loops, use the <xref:System.Text.StringBuilder> object.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#5)]  
  
### <a name="relaxed-delegates-in-event-handlers"></a><span data-ttu-id="889af-136">寬鬆的委派事件處理常式</span><span class="sxs-lookup"><span data-stu-id="889af-136">Relaxed Delegates in Event Handlers</span></span>  
 <span data-ttu-id="889af-137">不要明確限定 （Object 和 EventArgs） 的引數至事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="889af-137">Do not explicitly qualify the arguments (Object and EventArgs) to event handlers.</span></span> <span data-ttu-id="889af-138">如果您未使用的事件引數傳遞至事件 (例如，sender as Object、 e as EventArgs)，使用寬鬆的委派，並省略事件引數，在您的程式碼：</span><span class="sxs-lookup"><span data-stu-id="889af-138">If you are not using the event arguments that are passed to an event (for example, sender as Object, e as EventArgs), use relaxed delegates, and leave out the event arguments in your code:</span></span>  
  
 [!code-vb[VbVbalrGuidelines#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#7)]  
  
### <a name="unsigned-data-type"></a><span data-ttu-id="889af-139">不帶正負號的資料類型</span><span class="sxs-lookup"><span data-stu-id="889af-139">Unsigned Data Type</span></span>  
  
- <span data-ttu-id="889af-140">使用`Integer`而不是不帶正負號的類型，除非它們是必要。</span><span class="sxs-lookup"><span data-stu-id="889af-140">Use `Integer` rather than unsigned types, except where they are necessary.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="889af-141">陣列</span><span class="sxs-lookup"><span data-stu-id="889af-141">Arrays</span></span>  
  
- <span data-ttu-id="889af-142">當您初始化陣列的宣告行上時，請使用簡短的語法。</span><span class="sxs-lookup"><span data-stu-id="889af-142">Use the short syntax when you initialize arrays on the declaration line.</span></span> <span data-ttu-id="889af-143">例如，使用下列語法。</span><span class="sxs-lookup"><span data-stu-id="889af-143">For example, use the following syntax.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#8)]  
  
     <span data-ttu-id="889af-144">請勿使用下列語法。</span><span class="sxs-lookup"><span data-stu-id="889af-144">Do not use the following syntax.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#9)]  
  
- <span data-ttu-id="889af-145">在類型上，不是在變數上，請將陣列指示項。</span><span class="sxs-lookup"><span data-stu-id="889af-145">Put the array designator on the type, not on the variable.</span></span> <span data-ttu-id="889af-146">例如，使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="889af-146">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#11)]  
  
     <span data-ttu-id="889af-147">請勿使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="889af-147">Do not use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#10)]  
  
- <span data-ttu-id="889af-148">當您宣告並初始化基本資料類型的陣列，請使用 {} 語法。</span><span class="sxs-lookup"><span data-stu-id="889af-148">Use the { } syntax when you declare and initialize arrays of basic data types.</span></span> <span data-ttu-id="889af-149">例如，使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="889af-149">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#12)]  
  
     <span data-ttu-id="889af-150">請勿使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="889af-150">Do not use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#13)]  
  
### <a name="use-the-with-keyword"></a><span data-ttu-id="889af-151">使用 With 關鍵字</span><span class="sxs-lookup"><span data-stu-id="889af-151">Use the With Keyword</span></span>  
 <span data-ttu-id="889af-152">當您進行一系列的一個物件的呼叫時，請考慮使用`With`關鍵字：</span><span class="sxs-lookup"><span data-stu-id="889af-152">When you make a series of calls to one object, consider using the `With` keyword:</span></span>  
  
 [!code-vb[VbVbalrGuidelines#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#15)]  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a><span data-ttu-id="889af-153">使用 Try...Catch 和 Using 陳述式時使用 例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="889af-153">Use the Try...Catch and Using Statements when you use Exception Handling</span></span>  
 <span data-ttu-id="889af-154">請勿使用 `On Error Goto`。</span><span class="sxs-lookup"><span data-stu-id="889af-154">Do not use `On Error Goto`.</span></span>  
  
### <a name="use-the-isnot-keyword"></a><span data-ttu-id="889af-155">使用 IsNot 關鍵字</span><span class="sxs-lookup"><span data-stu-id="889af-155">Use the IsNot Keyword</span></span>  
 <span data-ttu-id="889af-156">使用`IsNot`關鍵字取代`Not...Is Nothing`。</span><span class="sxs-lookup"><span data-stu-id="889af-156">Use the `IsNot` keyword instead of `Not...Is Nothing`.</span></span>  
  
### <a name="new-keyword"></a><span data-ttu-id="889af-157">新的關鍵字</span><span class="sxs-lookup"><span data-stu-id="889af-157">New Keyword</span></span>  
  
- <span data-ttu-id="889af-158">使用簡短的具現化。</span><span class="sxs-lookup"><span data-stu-id="889af-158">Use short instantiation.</span></span> <span data-ttu-id="889af-159">例如，使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="889af-159">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#21)]  
  
     <span data-ttu-id="889af-160">前一行相當於這個：</span><span class="sxs-lookup"><span data-stu-id="889af-160">The preceding line is equivalent to this:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#22)]  
  
- <span data-ttu-id="889af-161">為新的物件，而不是無參數建構函式中使用物件初始設定式：</span><span class="sxs-lookup"><span data-stu-id="889af-161">Use object initializers for new objects instead of the parameterless constructor:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#23)]  
  
### <a name="event-handling"></a><span data-ttu-id="889af-162">事件處理</span><span class="sxs-lookup"><span data-stu-id="889af-162">Event Handling</span></span>  
  
- <span data-ttu-id="889af-163">使用`Handles`而非`AddHandler`:</span><span class="sxs-lookup"><span data-stu-id="889af-163">Use `Handles` rather than `AddHandler`:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#24)]  
  
- <span data-ttu-id="889af-164">使用`AddressOf`，並執行不具現化委派明確：</span><span class="sxs-lookup"><span data-stu-id="889af-164">Use `AddressOf`, and do not instantiate the delegate explicitly:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#25)]  
  
- <span data-ttu-id="889af-165">當您定義事件時，使用簡短的語法，並讓編譯器定義委派：</span><span class="sxs-lookup"><span data-stu-id="889af-165">When you define an event, use the short syntax, and let the compiler define the delegate:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#26)]  
  
- <span data-ttu-id="889af-166">不要驗證事件是否`Nothing`(null) 才能呼叫`RaiseEvent`方法。</span><span class="sxs-lookup"><span data-stu-id="889af-166">Do not verify whether an event is `Nothing` (null) before you call the `RaiseEvent` method.</span></span> <span data-ttu-id="889af-167">`RaiseEvent` 檢查是否有`Nothing`引發事件之前。</span><span class="sxs-lookup"><span data-stu-id="889af-167">`RaiseEvent` checks for `Nothing` before it raises the event.</span></span>  
  
### <a name="using-shared-members"></a><span data-ttu-id="889af-168">使用共用的成員</span><span class="sxs-lookup"><span data-stu-id="889af-168">Using Shared Members</span></span>  
 <span data-ttu-id="889af-169">呼叫`Shared`成員使用的類別名稱，不是從執行個體變數。</span><span class="sxs-lookup"><span data-stu-id="889af-169">Call `Shared` members by using the class name, not from an instance variable.</span></span>  
  
### <a name="use-xml-literals"></a><span data-ttu-id="889af-170">使用 XML 常值</span><span class="sxs-lookup"><span data-stu-id="889af-170">Use XML Literals</span></span>  
 <span data-ttu-id="889af-171">XML 常值來簡化您使用 （例如載入、 查詢及轉換） 的 XML 時所遇到的常見工作。</span><span class="sxs-lookup"><span data-stu-id="889af-171">XML literals simplify the most common tasks that you encounter when you work with XML (for example, load, query, and transform).</span></span> <span data-ttu-id="889af-172">當您使用 XML 進行開發時，請遵循這些指導方針：</span><span class="sxs-lookup"><span data-stu-id="889af-172">When you develop with XML, follow these guidelines:</span></span>  
  
- <span data-ttu-id="889af-173">您可以使用 XML 常值來建立 XML 文件和片段，而不要直接呼叫 XML Api。</span><span class="sxs-lookup"><span data-stu-id="889af-173">Use XML literals to create XML documents and fragments instead of calling XML APIs directly.</span></span>  
  
- <span data-ttu-id="889af-174">匯入 XML 命名空間，在檔案或專案層級，才能利用 XML 常值的效能最佳化。</span><span class="sxs-lookup"><span data-stu-id="889af-174">Import XML namespaces at the file or project level to take advantage of the performance optimizations for XML literals.</span></span>  
  
- <span data-ttu-id="889af-175">您可以使用 XML 軸屬性來存取 XML 文件中元素和屬性。</span><span class="sxs-lookup"><span data-stu-id="889af-175">Use the XML axis properties to access elements and attributes in an XML document.</span></span>  
  
- <span data-ttu-id="889af-176">使用內嵌的運算式，以加入值，並從現有的值，而不是使用 API 呼叫，例如建立 XML`Add`方法：</span><span class="sxs-lookup"><span data-stu-id="889af-176">Use embedded expressions to include values and to create XML from existing values instead of using API calls such as the `Add` method:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#27)]  
  
### <a name="linq-queries"></a><span data-ttu-id="889af-177">LINQ 查詢</span><span class="sxs-lookup"><span data-stu-id="889af-177">LINQ Queries</span></span>  
  
- <span data-ttu-id="889af-178">使用有意義的名稱，做為查詢變數：</span><span class="sxs-lookup"><span data-stu-id="889af-178">Use meaningful names for query variables:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#28)]  
  
- <span data-ttu-id="889af-179">提供名稱的項目查詢中，以確定，匿名類型的屬性名稱大寫採用正確的 pascal 命名法大小寫：</span><span class="sxs-lookup"><span data-stu-id="889af-179">Provide names for elements in a query to make sure that property names of anonymous types are correctly capitalized using Pascal casing:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#29)]  
  
- <span data-ttu-id="889af-180">當結果中的屬性名稱可能會造成混淆時，請重新命名屬性。</span><span class="sxs-lookup"><span data-stu-id="889af-180">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="889af-181">例如，如果您的查詢會傳回客戶名稱和訂單 ID，將其重新命名將它們保留為`Name`和`ID`結果：</span><span class="sxs-lookup"><span data-stu-id="889af-181">For example, if your query returns a customer name and an order ID, rename them instead of leaving them as `Name` and `ID` in the result:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#30)]  
  
- <span data-ttu-id="889af-182">使用類型推斷查詢變數和範圍變數的宣告中：</span><span class="sxs-lookup"><span data-stu-id="889af-182">Use type inference in the declaration of query variables and range variables:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#31)]  
  
- <span data-ttu-id="889af-183">下對齊查詢子句`From`陳述式：</span><span class="sxs-lookup"><span data-stu-id="889af-183">Align query clauses under the `From` statement:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#32)]  
  
- <span data-ttu-id="889af-184">使用`Where`子句在其他查詢子句，以便之後的查詢子句對篩選的資料集：</span><span class="sxs-lookup"><span data-stu-id="889af-184">Use `Where` clauses before other query clauses so that later query clauses operate on the filtered set of data:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#33)]  
  
- <span data-ttu-id="889af-185">使用`Join`子句來明確定義聯結作業，而不是使用`Where`子句隱含定義聯結作業：</span><span class="sxs-lookup"><span data-stu-id="889af-185">Use the `Join` clause to explicitly define a join operation instead of using the `Where` clause to implicitly define a join operation:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#34)]  
  
## <a name="see-also"></a><span data-ttu-id="889af-186">另請參閱</span><span class="sxs-lookup"><span data-stu-id="889af-186">See also</span></span>

- [<span data-ttu-id="889af-187">安全程式碼撰寫方針</span><span class="sxs-lookup"><span data-stu-id="889af-187">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)
