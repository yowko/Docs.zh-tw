---
title: "Visual Basic 編碼慣例 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- coding conventions, Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
caps.latest.revision: 48
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 16d4ddccd3a16c48e58f297faf8909148899013f
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="visual-basic-coding-conventions"></a><span data-ttu-id="1d2c3-102">Visual Basic 編碼慣例</span><span class="sxs-lookup"><span data-stu-id="1d2c3-102">Visual Basic Coding Conventions</span></span>
<span data-ttu-id="1d2c3-103">Microsoft 開發範例和文件，請遵循本主題中的指導方針。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-103">Microsoft develops samples and documentation that follow the guidelines in this topic.</span></span> <span data-ttu-id="1d2c3-104">如果您遵循相同的程式碼撰寫慣例，您可能會獲得下列好處︰</span><span class="sxs-lookup"><span data-stu-id="1d2c3-104">If you follow the same coding conventions, you may gain the following benefits:</span></span>  
  
-   <span data-ttu-id="1d2c3-105">您的程式碼將會有一致的外觀，讓讀者能夠更專注於內容，而非版面配置。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-105">Your code will have a consistent look, so that readers can better focus on content, not layout.</span></span>  
  
-   <span data-ttu-id="1d2c3-106">讀者了解您的程式碼更快速地因為它們會使先前的經驗為基礎的假設。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-106">Readers understand your code more quickly because they can make assumptions based on previous experience.</span></span>  
  
-   <span data-ttu-id="1d2c3-107">您可以複製、 變更及維護程式碼更容易。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-107">You can copy, change, and maintain the code more easily.</span></span>  
  
-   <span data-ttu-id="1d2c3-108">您可以協助確保您的程式碼會示範 Visual Basic 的 「 最佳作法 」。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-108">You help ensure that your code demonstrates "best practices" for Visual Basic.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="1d2c3-109">命名規範</span><span class="sxs-lookup"><span data-stu-id="1d2c3-109">Naming Conventions</span></span>  
  
-   <span data-ttu-id="1d2c3-110">命名方針的相關資訊，請參閱[命名方針](http://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3)主題。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-110">For information about naming guidelines, see [Naming Guidelines](http://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3) topic.</span></span>  
  
-   <span data-ttu-id="1d2c3-111">請勿使用 「 我的 」 或 「 我的 」 做為變數名稱的一部分。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-111">Do not use "My" or "my" as part of a variable name.</span></span> <span data-ttu-id="1d2c3-112">這種作法建立混淆在一起`My`物件。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-112">This practice creates confusion with the `My` objects.</span></span>  
  
-   <span data-ttu-id="1d2c3-113">您不必變更中自動產生的程式碼使其符合準則的物件名稱。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-113">You do not have to change the names of objects in auto-generated code to make them fit the guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="1d2c3-114">版面配置慣例</span><span class="sxs-lookup"><span data-stu-id="1d2c3-114">Layout Conventions</span></span>  
  
-   <span data-ttu-id="1d2c3-115">插入空格 索引標籤，並使用四個空間縮排與智慧型縮排。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-115">Insert tabs as spaces, and use smart indenting with four-space indents.</span></span>  
  
-   <span data-ttu-id="1d2c3-116">使用**美化 （重新格式化） 的程式碼**重新格式化程式碼編輯器中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-116">Use **Pretty listing (reformatting) of code** to reformat your code in the code editor.</span></span> <span data-ttu-id="1d2c3-117">如需詳細資訊，請參閱[基本文字編輯器、 選項 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/options-text-editor-basic-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-117">For more information, see [Options, Text Editor, Basic (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/options-text-editor-basic-visual-basic).</span></span>  
  
-   <span data-ttu-id="1d2c3-118">使用每行只有一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-118">Use only one statement per line.</span></span> <span data-ttu-id="1d2c3-119">請勿使用 Visual Basic 的行分隔符號字元 （:）。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-119">Don't use the Visual Basic line separator character (:).</span></span>  
  
-   <span data-ttu-id="1d2c3-120">請避免使用明確的行接續字元"_"有利於隱含行接續符號，只要該語言可以讓它。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-120">Avoid using the explicit line continuation character "_" in favor of implicit line continuation wherever the language allows it.</span></span>  
  
-   <span data-ttu-id="1d2c3-121">使用每行只有一個宣告。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-121">Use only one declaration per line.</span></span>  
  
-   <span data-ttu-id="1d2c3-122">如果**美化 （重新格式化） 的程式碼**不接續線格式自動、 手動縮排接續行一個定位點。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-122">If **Pretty listing (reformatting) of code** doesn't format continuation lines automatically, manually indent continuation lines one tab stop.</span></span> <span data-ttu-id="1d2c3-123">不過，一定左對齊 清單中的項目。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-123">However, always left-align items in a list.</span></span>  
  
    ```  
    a As Integer,  
    b As Integer  
    ```  
  
-   <span data-ttu-id="1d2c3-124">新增方法與屬性定義之間的至少一個空白行。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-124">Add at least one blank line between method and property definitions.</span></span>  
  
## <a name="commenting-conventions"></a><span data-ttu-id="1d2c3-125">註解慣例</span><span class="sxs-lookup"><span data-stu-id="1d2c3-125">Commenting Conventions</span></span>  
  
-   <span data-ttu-id="1d2c3-126">將註解放到結尾的一行程式碼，而不是個別行上。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-126">Put comments on a separate line instead of at the end of a line of code.</span></span>  
  
-   <span data-ttu-id="1d2c3-127">開始以大寫字母，註解文字，並以句號結束註解文字。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-127">Start comment text with an uppercase letter, and end comment text with a period.</span></span>  
  
-   <span data-ttu-id="1d2c3-128">插入註解分隔符號 （'） 與註解文字之間的一個空格。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-128">Insert one space between the comment delimiter (') and the comment text.</span></span>  
  
     <span data-ttu-id="1d2c3-129">[!code-vb[VbVbalrGuidelines #&2;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="1d2c3-129">[!code-vb[VbVbalrGuidelines#2](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_1.vb)]</span></span>  
  
-   <span data-ttu-id="1d2c3-130">請勿用格式化的星號區塊註解。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-130">Do not surround comments with formatted blocks of asterisks.</span></span>  
  
## <a name="program-structure"></a><span data-ttu-id="1d2c3-131">程式結構</span><span class="sxs-lookup"><span data-stu-id="1d2c3-131">Program Structure</span></span>  
  
-   <span data-ttu-id="1d2c3-132">當您使用`Main`方法，使用預設建構新的主控台應用程式，並使用`My`命令列引數。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-132">When you use the `Main` method, use the default construct for new console applications, and use `My` for command-line arguments.</span></span>  
  
     <span data-ttu-id="1d2c3-133">[!code-vb[VbVbalrGuidelines #&3;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="1d2c3-133">[!code-vb[VbVbalrGuidelines#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_2.vb)]</span></span>  
  
## <a name="language-guidelines"></a><span data-ttu-id="1d2c3-134">語言指導方針</span><span class="sxs-lookup"><span data-stu-id="1d2c3-134">Language Guidelines</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="1d2c3-135">String 資料類型</span><span class="sxs-lookup"><span data-stu-id="1d2c3-135">String Data Type</span></span>  
  
-   <span data-ttu-id="1d2c3-136">若要串連的字串，使用連字號 （&）。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-136">To concatenate strings, use an ampersand (&).</span></span>  
  
     <span data-ttu-id="1d2c3-137">[!code-vb[VbVbalrGuidelines #&4;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="1d2c3-137">[!code-vb[VbVbalrGuidelines#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_3.vb)]</span></span>  
  
-   <span data-ttu-id="1d2c3-138">若要附加在迴圈中的字串，請使用<xref:System.Text.StringBuilder>物件。</xref:System.Text.StringBuilder></span><span class="sxs-lookup"><span data-stu-id="1d2c3-138">To append strings in loops, use the <xref:System.Text.StringBuilder> object.</span></span>  
  
     <span data-ttu-id="1d2c3-139">[!code-vb[VbVbalrGuidelines #&5;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="1d2c3-139">[!code-vb[VbVbalrGuidelines#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_4.vb)]</span></span>  
  
### <a name="relaxed-delegates-in-event-handlers"></a><span data-ttu-id="1d2c3-140">寬鬆的委派事件處理常式中</span><span class="sxs-lookup"><span data-stu-id="1d2c3-140">Relaxed Delegates in Event Handlers</span></span>  
 <span data-ttu-id="1d2c3-141">請勿明確限定 （物件和 EventArgs） 的引數至事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-141">Do not explicitly qualify the arguments (Object and EventArgs) to event handlers.</span></span> <span data-ttu-id="1d2c3-142">如果您未使用的事件引數傳遞至事件 （例如，寄件者物件，e EventArgs），使用比較不嚴謹的委派，並排除您的程式碼中的事件引數︰</span><span class="sxs-lookup"><span data-stu-id="1d2c3-142">If you are not using the event arguments that are passed to an event (for example, sender as Object, e as EventArgs), use relaxed delegates, and leave out the event arguments in your code:</span></span>  
  
 <span data-ttu-id="1d2c3-143">[!code-vb[VbVbalrGuidelines #&7;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="1d2c3-143">[!code-vb[VbVbalrGuidelines#7](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_5.vb)]</span></span>  
  
### <a name="unsigned-data-type"></a><span data-ttu-id="1d2c3-144">不帶正負號的資料類型</span><span class="sxs-lookup"><span data-stu-id="1d2c3-144">Unsigned Data Type</span></span>  
  
-   <span data-ttu-id="1d2c3-145">使用`Integer`而不是不帶正負號的型別，除非它們所需的位置。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-145">Use `Integer` rather than unsigned types, except where they are necessary.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="1d2c3-146">陣列</span><span class="sxs-lookup"><span data-stu-id="1d2c3-146">Arrays</span></span>  
  
-   <span data-ttu-id="1d2c3-147">當您在宣告行上初始化陣列時，請使用簡短的語法。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-147">Use the short syntax when you initialize arrays on the declaration line.</span></span> <span data-ttu-id="1d2c3-148">例如，使用下列語法。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-148">For example, use the following syntax.</span></span>  
  
     <span data-ttu-id="1d2c3-149">[!code-vb[VbVbalrGuidelines #&8;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="1d2c3-149">[!code-vb[VbVbalrGuidelines#8](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_6.vb)]</span></span>  
  
     <span data-ttu-id="1d2c3-150">請勿使用下列語法。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-150">Do not use the following syntax.</span></span>  
  
     <span data-ttu-id="1d2c3-151">[!code-vb[VbVbalrGuidelines #&9;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="1d2c3-151">[!code-vb[VbVbalrGuidelines#9](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_7.vb)]</span></span>  
  
-   <span data-ttu-id="1d2c3-152">變數型別，而非將陣列指示項。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-152">Put the array designator on the type, not on the variable.</span></span> <span data-ttu-id="1d2c3-153">例如，使用下列語法︰</span><span class="sxs-lookup"><span data-stu-id="1d2c3-153">For example, use the following syntax:</span></span>  
  
     <span data-ttu-id="1d2c3-154">[!code-vb[VbVbalrGuidelines #&11;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="1d2c3-154">[!code-vb[VbVbalrGuidelines#11](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_8.vb)]</span></span>  
  
     <span data-ttu-id="1d2c3-155">請勿使用下列語法︰</span><span class="sxs-lookup"><span data-stu-id="1d2c3-155">Do not use the following syntax:</span></span>  
  
     <span data-ttu-id="1d2c3-156">[!code-vb[VbVbalrGuidelines #&10;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="1d2c3-156">[!code-vb[VbVbalrGuidelines#10](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_9.vb)]</span></span>  
  
-   <span data-ttu-id="1d2c3-157">宣告和初始化陣列的基本資料型別時，請使用 {} 語法。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-157">Use the { } syntax when you declare and initialize arrays of basic data types.</span></span> <span data-ttu-id="1d2c3-158">例如，使用下列語法︰</span><span class="sxs-lookup"><span data-stu-id="1d2c3-158">For example, use the following syntax:</span></span>  
  
     <span data-ttu-id="1d2c3-159">[!code-vb[VbVbalrGuidelines #&12;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_10.vb)]</span><span class="sxs-lookup"><span data-stu-id="1d2c3-159">[!code-vb[VbVbalrGuidelines#12](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_10.vb)]</span></span>  
  
     <span data-ttu-id="1d2c3-160">請勿使用下列語法︰</span><span class="sxs-lookup"><span data-stu-id="1d2c3-160">Do not use the following syntax:</span></span>  
  
     <span data-ttu-id="1d2c3-161">[!code-vb[VbVbalrGuidelines #&13;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_11.vb)]</span><span class="sxs-lookup"><span data-stu-id="1d2c3-161">[!code-vb[VbVbalrGuidelines#13](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_11.vb)]</span></span>  
  
### <a name="use-the-with-keyword"></a><span data-ttu-id="1d2c3-162">使用 With 關鍵字</span><span class="sxs-lookup"><span data-stu-id="1d2c3-162">Use the With Keyword</span></span>  
 <span data-ttu-id="1d2c3-163">當您進行一系列的一個物件的呼叫時，請考慮使用`With`關鍵字︰</span><span class="sxs-lookup"><span data-stu-id="1d2c3-163">When you make a series of calls to one object, consider using the `With` keyword:</span></span>  
  
 <span data-ttu-id="1d2c3-164">[!code-vb[VbVbalrGuidelines #&15;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_12.vb)]</span><span class="sxs-lookup"><span data-stu-id="1d2c3-164">[!code-vb[VbVbalrGuidelines#15](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_12.vb)]</span></span>  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a><span data-ttu-id="1d2c3-165">使用 Try …Catch 和 Using 陳述式時使用 例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="1d2c3-165">Use the Try...Catch and Using Statements when you use Exception Handling</span></span>  
 <span data-ttu-id="1d2c3-166">請勿使用`On Error Goto`。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-166">Do not use `On Error Goto`.</span></span>  
  
### <a name="use-the-isnot-keyword"></a><span data-ttu-id="1d2c3-167">使用 IsNot 關鍵字</span><span class="sxs-lookup"><span data-stu-id="1d2c3-167">Use the IsNot Keyword</span></span>  
 <span data-ttu-id="1d2c3-168">使用`IsNot`關鍵字取代`Not...Is Nothing`。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-168">Use the `IsNot` keyword instead of `Not...Is Nothing`.</span></span>  
  
### <a name="new-keyword"></a><span data-ttu-id="1d2c3-169">New 關鍵字</span><span class="sxs-lookup"><span data-stu-id="1d2c3-169">New Keyword</span></span>  
  
-   <span data-ttu-id="1d2c3-170">使用簡短的具現化。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-170">Use short instantiation.</span></span> <span data-ttu-id="1d2c3-171">例如，使用下列語法︰</span><span class="sxs-lookup"><span data-stu-id="1d2c3-171">For example, use the following syntax:</span></span>  
  
     <span data-ttu-id="1d2c3-172">[!code-vb[VbVbalrGuidelines #&21;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_13.vb)]</span><span class="sxs-lookup"><span data-stu-id="1d2c3-172">[!code-vb[VbVbalrGuidelines#21](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_13.vb)]</span></span>  
  
     <span data-ttu-id="1d2c3-173">前一行相當於這個︰</span><span class="sxs-lookup"><span data-stu-id="1d2c3-173">The preceding line is equivalent to this:</span></span>  
  
     <span data-ttu-id="1d2c3-174">[!code-vb[VbVbalrGuidelines #&22;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_14.vb)]</span><span class="sxs-lookup"><span data-stu-id="1d2c3-174">[!code-vb[VbVbalrGuidelines#22](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_14.vb)]</span></span>  
  
-   <span data-ttu-id="1d2c3-175">為新的物件，而不是無參數建構函式中使用物件初始設定式︰</span><span class="sxs-lookup"><span data-stu-id="1d2c3-175">Use object initializers for new objects instead of the parameterless constructor:</span></span>  
  
     <span data-ttu-id="1d2c3-176">[!code-vb[VbVbalrGuidelines #&23;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_15.vb)]</span><span class="sxs-lookup"><span data-stu-id="1d2c3-176">[!code-vb[VbVbalrGuidelines#23](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_15.vb)]</span></span>  
  
### <a name="event-handling"></a><span data-ttu-id="1d2c3-177">事件處理</span><span class="sxs-lookup"><span data-stu-id="1d2c3-177">Event Handling</span></span>  
  
-   <span data-ttu-id="1d2c3-178">使用`Handles`而不是`AddHandler`:</span><span class="sxs-lookup"><span data-stu-id="1d2c3-178">Use `Handles` rather than `AddHandler`:</span></span>  
  
     <span data-ttu-id="1d2c3-179">[!code-vb[VbVbalrGuidelines #&24;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_16.vb)]</span><span class="sxs-lookup"><span data-stu-id="1d2c3-179">[!code-vb[VbVbalrGuidelines#24](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_16.vb)]</span></span>  
  
-   <span data-ttu-id="1d2c3-180">使用`AddressOf`，並不明確產生的委派︰</span><span class="sxs-lookup"><span data-stu-id="1d2c3-180">Use `AddressOf`, and do not instantiate the delegate explicitly:</span></span>  
  
     <span data-ttu-id="1d2c3-181">[!code-vb[VbVbalrGuidelines #&25;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_17.vb)]</span><span class="sxs-lookup"><span data-stu-id="1d2c3-181">[!code-vb[VbVbalrGuidelines#25](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_17.vb)]</span></span>  
  
-   <span data-ttu-id="1d2c3-182">當您定義的事件時，使用簡短的語法，並讓編譯器定義委派︰</span><span class="sxs-lookup"><span data-stu-id="1d2c3-182">When you define an event, use the short syntax, and let the compiler define the delegate:</span></span>  
  
     <span data-ttu-id="1d2c3-183">[!code-vb[VbVbalrGuidelines #&26;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_18.vb)]</span><span class="sxs-lookup"><span data-stu-id="1d2c3-183">[!code-vb[VbVbalrGuidelines#26](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_18.vb)]</span></span>  
  
-   <span data-ttu-id="1d2c3-184">不會驗證事件是否`Nothing`(null) 才能呼叫`RaiseEvent`方法。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-184">Do not verify whether an event is `Nothing` (null) before you call the `RaiseEvent` method.</span></span> <span data-ttu-id="1d2c3-185">`RaiseEvent`檢查是否有`Nothing`引發事件之前。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-185">`RaiseEvent` checks for `Nothing` before it raises the event.</span></span>  
  
### <a name="using-shared-members"></a><span data-ttu-id="1d2c3-186">使用共用的成員</span><span class="sxs-lookup"><span data-stu-id="1d2c3-186">Using Shared Members</span></span>  
 <span data-ttu-id="1d2c3-187">呼叫`Shared`成員使用的類別名稱，不能從執行個體變數。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-187">Call `Shared` members by using the class name, not from an instance variable.</span></span>  
  
### <a name="use-xml-literals"></a><span data-ttu-id="1d2c3-188">使用 XML 常值</span><span class="sxs-lookup"><span data-stu-id="1d2c3-188">Use XML Literals</span></span>  
 <span data-ttu-id="1d2c3-189">XML 常值來簡化處理 （例如載入、 查詢和轉換） 的 XML 時遇到的常見工作。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-189">XML literals simplify the most common tasks that you encounter when you work with XML (for example, load, query, and transform).</span></span> <span data-ttu-id="1d2c3-190">當您開發 xml 時，請遵循下列方針︰</span><span class="sxs-lookup"><span data-stu-id="1d2c3-190">When you develop with XML, follow these guidelines:</span></span>  
  
-   <span data-ttu-id="1d2c3-191">您可以使用 XML 常值來建立 XML 文件和片段，而不是直接呼叫 XML Api。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-191">Use XML literals to create XML documents and fragments instead of calling XML APIs directly.</span></span>  
  
-   <span data-ttu-id="1d2c3-192">匯入 XML 命名空間，在檔案或專案層級，若要利用 XML 常值的效能最佳化。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-192">Import XML namespaces at the file or project level to take advantage of the performance optimizations for XML literals.</span></span>  
  
-   <span data-ttu-id="1d2c3-193">您可以使用 XML 軸屬性來存取 XML 文件中元素和屬性。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-193">Use the XML axis properties to access elements and attributes in an XML document.</span></span>  
  
-   <span data-ttu-id="1d2c3-194">使用內嵌的運算式包含值，並從現有的值，而不是使用 API 呼叫，例如建立 XML`Add`方法︰</span><span class="sxs-lookup"><span data-stu-id="1d2c3-194">Use embedded expressions to include values and to create XML from existing values instead of using API calls such as the `Add` method:</span></span>  
  
     <span data-ttu-id="1d2c3-195">[!code-vb[VbVbalrGuidelines #&27;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_19.vb)]</span><span class="sxs-lookup"><span data-stu-id="1d2c3-195">[!code-vb[VbVbalrGuidelines#27](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_19.vb)]</span></span>  
  
### <a name="linq-queries"></a><span data-ttu-id="1d2c3-196">LINQ 查詢</span><span class="sxs-lookup"><span data-stu-id="1d2c3-196">LINQ Queries</span></span>  
  
-   <span data-ttu-id="1d2c3-197">使用有意義的名稱，請為查詢變數︰</span><span class="sxs-lookup"><span data-stu-id="1d2c3-197">Use meaningful names for query variables:</span></span>  
  
     <span data-ttu-id="1d2c3-198">[!code-vb[VbVbalrGuidelines #&28;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_20.vb)]</span><span class="sxs-lookup"><span data-stu-id="1d2c3-198">[!code-vb[VbVbalrGuidelines#28](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_20.vb)]</span></span>  
  
-   <span data-ttu-id="1d2c3-199">提供的查詢，以確定，匿名型別的屬性名稱大寫正確使用 pascal 命名法中的項目名稱大小寫︰</span><span class="sxs-lookup"><span data-stu-id="1d2c3-199">Provide names for elements in a query to make sure that property names of anonymous types are correctly capitalized using Pascal casing:</span></span>  
  
     <span data-ttu-id="1d2c3-200">[!code-vb[VbVbalrGuidelines #&29;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_21.vb)]</span><span class="sxs-lookup"><span data-stu-id="1d2c3-200">[!code-vb[VbVbalrGuidelines#29](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_21.vb)]</span></span>  
  
-   <span data-ttu-id="1d2c3-201">當結果中的屬性名稱可能會造成混淆時，請重新命名屬性。</span><span class="sxs-lookup"><span data-stu-id="1d2c3-201">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="1d2c3-202">例如，如果您的查詢傳回了客戶名稱和訂單 ID，重新命名並不是保留為`Name`和`ID`結果︰</span><span class="sxs-lookup"><span data-stu-id="1d2c3-202">For example, if your query returns a customer name and an order ID, rename them instead of leaving them as `Name` and `ID` in the result:</span></span>  
  
     <span data-ttu-id="1d2c3-203">[!code-vb[VbVbalrGuidelines #&30;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_22.vb)]</span><span class="sxs-lookup"><span data-stu-id="1d2c3-203">[!code-vb[VbVbalrGuidelines#30](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_22.vb)]</span></span>  
  
-   <span data-ttu-id="1d2c3-204">查詢變數和範圍變數的宣告中使用型別推斷︰</span><span class="sxs-lookup"><span data-stu-id="1d2c3-204">Use type inference in the declaration of query variables and range variables:</span></span>  
  
     <span data-ttu-id="1d2c3-205">[!code-vb[VbVbalrGuidelines #&31;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_23.vb)]</span><span class="sxs-lookup"><span data-stu-id="1d2c3-205">[!code-vb[VbVbalrGuidelines#31](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_23.vb)]</span></span>  
  
-   <span data-ttu-id="1d2c3-206">對齊查詢子句下,`From`陳述式︰</span><span class="sxs-lookup"><span data-stu-id="1d2c3-206">Align query clauses under the `From` statement:</span></span>  
  
     <span data-ttu-id="1d2c3-207">[!code-vb[VbVbalrGuidelines #&32;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_24.vb)]</span><span class="sxs-lookup"><span data-stu-id="1d2c3-207">[!code-vb[VbVbalrGuidelines#32](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_24.vb)]</span></span>  
  
-   <span data-ttu-id="1d2c3-208">使用`Where`子句之前其他查詢子句，以便之後的查詢子句對篩選的資料集︰</span><span class="sxs-lookup"><span data-stu-id="1d2c3-208">Use `Where` clauses before other query clauses so that later query clauses operate on the filtered set of data:</span></span>  
  
     <span data-ttu-id="1d2c3-209">[!code-vb[VbVbalrGuidelines #&33;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_25.vb)]</span><span class="sxs-lookup"><span data-stu-id="1d2c3-209">[!code-vb[VbVbalrGuidelines#33](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_25.vb)]</span></span>  
  
-   <span data-ttu-id="1d2c3-210">使用`Join`子句來明確定義的聯結作業，而不是使用`Where`子句來隱含定義的聯結作業︰</span><span class="sxs-lookup"><span data-stu-id="1d2c3-210">Use the `Join` clause to explicitly define a join operation instead of using the `Where` clause to implicitly define a join operation:</span></span>  
  
     <span data-ttu-id="1d2c3-211">[!code-vb[VbVbalrGuidelines #&34;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_26.vb)]</span><span class="sxs-lookup"><span data-stu-id="1d2c3-211">[!code-vb[VbVbalrGuidelines#34](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_26.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d2c3-212">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d2c3-212">See Also</span></span>  
 [<span data-ttu-id="1d2c3-213">安全程式碼撰寫方針</span><span class="sxs-lookup"><span data-stu-id="1d2c3-213">Secure Coding Guidelines</span></span>](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)
