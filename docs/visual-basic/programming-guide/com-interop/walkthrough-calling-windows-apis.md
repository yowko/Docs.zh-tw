---
title: "逐步解說︰ 呼叫 Windows Api (Visual Basic) |Microsoft 文件"
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
- DLLs, calling
- Windows API, walkthroughs
- platform invoke, walkthroughs
- API calls, walkthroughs [Visual Basic]
- Windows API, calling
- walkthroughs [Visual Basic], API calls
- DllImport attribute, calling Windows API
- Declare statement, declaring DLL functions
ms.assetid: 9280ca96-7a93-47a3-8d01-6d01be0657cb
caps.latest.revision: 20
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
ms.openlocfilehash: ae1ef60e6e27658c872689f5bfe2779493d42e7a
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-calling-windows-apis-visual-basic"></a><span data-ttu-id="8facc-102">逐步解說：呼叫 Windows API (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8facc-102">Walkthrough: Calling Windows APIs (Visual Basic)</span></span>
<span data-ttu-id="8facc-103">Windows Api，是屬於 Windows 作業系統的動態連結程式庫 (Dll)。</span><span class="sxs-lookup"><span data-stu-id="8facc-103">Windows APIs are dynamic-link libraries (DLLs) that are part of the Windows operating system.</span></span> <span data-ttu-id="8facc-104">您可以使用它們來執行工作時很難撰寫您自己的對等的程序。</span><span class="sxs-lookup"><span data-stu-id="8facc-104">You use them to perform tasks when it is difficult to write equivalent procedures of your own.</span></span> <span data-ttu-id="8facc-105">例如，Windows 提供函式，名為`FlashWindowEx`，可讓您的應用程式的標題列光影灰色陰影之間交替。</span><span class="sxs-lookup"><span data-stu-id="8facc-105">For example, Windows provides a function named `FlashWindowEx` that lets you make the title bar for an application alternate between light and dark shades.</span></span>  
  
 <span data-ttu-id="8facc-106">在您的程式碼中使用 Windows Api 的優點是，它們就可以節省開發時間，因為它們包含數十個有用的功能已經撰寫，並可立即使用。</span><span class="sxs-lookup"><span data-stu-id="8facc-106">The advantage of using Windows APIs in your code is that they can save development time because they contain dozens of useful functions that are already written and waiting to be used.</span></span> <span data-ttu-id="8facc-107">缺點是 Windows Api 很難發生錯誤時工作和正確性。</span><span class="sxs-lookup"><span data-stu-id="8facc-107">The disadvantage is that Windows APIs can be difficult to work with and unforgiving when things go wrong.</span></span>  
  
 <span data-ttu-id="8facc-108">Windows Api 都代表一個特殊種類的互通性。</span><span class="sxs-lookup"><span data-stu-id="8facc-108">Windows APIs represent a special category of interoperability.</span></span> <span data-ttu-id="8facc-109">Windows Api 不會使用 managed 程式碼，並沒有內建型別程式庫，並使用不同的 Visual Studio 搭配使用的資料型別。</span><span class="sxs-lookup"><span data-stu-id="8facc-109">Windows APIs do not use managed code, do not have built-in type libraries, and use data types that are different than those used with Visual Studio.</span></span> <span data-ttu-id="8facc-110">由於這些差異，而且因為 Windows Api 不是 COM 物件，與 Windows Api 的互通性和[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]透過平台叫用，或 PInvoke。</span><span class="sxs-lookup"><span data-stu-id="8facc-110">Because of these differences, and because Windows APIs are not COM objects, interoperability with Windows APIs and the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] is performed using platform invoke, or PInvoke.</span></span> <span data-ttu-id="8facc-111">平台叫用是一項服務，可讓 managed 程式碼呼叫 unmanaged 函式在 Dll 中實作。</span><span class="sxs-lookup"><span data-stu-id="8facc-111">Platform invoke is a service that enables managed code to call unmanaged functions implemented in DLLs.</span></span> <span data-ttu-id="8facc-112">如需詳細資訊，請參閱[使用 Unmanaged DLL 函式](http://msdn.microsoft.com/library/eca7606e-ebfb-4f47-b8d9-289903fdc045)。</span><span class="sxs-lookup"><span data-stu-id="8facc-112">For more information, see [Consuming Unmanaged DLL Functions](http://msdn.microsoft.com/library/eca7606e-ebfb-4f47-b8d9-289903fdc045).</span></span> <span data-ttu-id="8facc-113">您可以使用中的 PInvoke[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]使用`Declare`陳述式或套用`DllImport`屬性設定為空的程序。</span><span class="sxs-lookup"><span data-stu-id="8facc-113">You can use PInvoke in [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] by using either the `Declare` statement or applying the `DllImport` attribute to an empty procedure.</span></span>  
  
 <span data-ttu-id="8facc-114">Windows API 呼叫是很重要的一部分[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]程式設計在過去，但這是很少需要[!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8facc-114">Windows API calls were an important part of [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programming in the past, but are seldom necessary with [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)].</span></span> <span data-ttu-id="8facc-115">可能的話，您應該使用 managed 程式碼的[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]來執行工作，而不是 Windows API 呼叫。</span><span class="sxs-lookup"><span data-stu-id="8facc-115">Whenever possible, you should use managed code from the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] to perform tasks, instead of Windows API calls.</span></span> <span data-ttu-id="8facc-116">本逐步解說提供這兩種情況中使用的資訊是必要的 Windows Api。</span><span class="sxs-lookup"><span data-stu-id="8facc-116">This walkthrough provides information for those situations in which using Windows APIs is necessary.</span></span>  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
## <a name="api-calls-using-declare"></a><span data-ttu-id="8facc-117">API 呼叫使用宣告</span><span class="sxs-lookup"><span data-stu-id="8facc-117">API Calls Using Declare</span></span>  
 <span data-ttu-id="8facc-118">呼叫 Windows Api 的最常見方式是使用`Declare`陳述式。</span><span class="sxs-lookup"><span data-stu-id="8facc-118">The most common way to call Windows APIs is by using the `Declare` statement.</span></span>  
  
#### <a name="to-declare-a-dll-procedure"></a><span data-ttu-id="8facc-119">宣告 DLL 程序</span><span class="sxs-lookup"><span data-stu-id="8facc-119">To declare a DLL procedure</span></span>  
  
1.  <span data-ttu-id="8facc-120">決定您想要呼叫時，函式加上引數，引數類型的名稱，並傳回值，以及名稱和包含該 DLL 的位置。</span><span class="sxs-lookup"><span data-stu-id="8facc-120">Determine the name of the function you want to call, plus its arguments, argument types, and return value, as well as the name and location of the DLL that contains it.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8facc-121">如需 Windows Api 的完整資訊，請參閱平台 SDK Windows API 中的 Win32 SDK 文件。</span><span class="sxs-lookup"><span data-stu-id="8facc-121">For complete information about the Windows APIs, see the Win32 SDK documentation in the Platform SDK Windows API.</span></span> <span data-ttu-id="8facc-122">如需有關使用 Windows Api 的常數的詳細資訊，請檢查例如 Windows.h 平台 SDK 隨附的標頭檔。</span><span class="sxs-lookup"><span data-stu-id="8facc-122">For more information about the constants that Windows APIs use, examine the header files such as Windows.h included with the Platform SDK.</span></span>  
  
2.  <span data-ttu-id="8facc-123">開啟新的 Windows 應用程式專案，依序按一下**新增**上**檔案**] 功能表，然後按一下 [**專案**。</span><span class="sxs-lookup"><span data-stu-id="8facc-123">Open a new Windows Application project by clicking **New** on the **File** menu, and then clicking **Project**.</span></span> <span data-ttu-id="8facc-124">[ **新增專案** ] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="8facc-124">The **New Project** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="8facc-125">選取**Windows 應用程式**從清單中的[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]專案範本。</span><span class="sxs-lookup"><span data-stu-id="8facc-125">Select **Windows Application** from the list of [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] project templates.</span></span> <span data-ttu-id="8facc-126">會顯示新的專案。</span><span class="sxs-lookup"><span data-stu-id="8facc-126">The new project is displayed.</span></span>  
  
4.  <span data-ttu-id="8facc-127">新增下列`Declare`函式類別，或是您要使用 DLL 的模組︰</span><span class="sxs-lookup"><span data-stu-id="8facc-127">Add the following `Declare` function either to the class or module in which you want to use the DLL:</span></span>  
  
     <span data-ttu-id="8facc-128">[!code-vb[VbVbalrInterop #&9;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="8facc-128">[!code-vb[VbVbalrInterop#9](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_1.vb)]</span></span>  
  
### <a name="parts-of-the-declare-statement"></a><span data-ttu-id="8facc-129">組件的 Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="8facc-129">Parts of the Declare Statement</span></span>  
 <span data-ttu-id="8facc-130">`Declare`陳述式包括下列項目。</span><span class="sxs-lookup"><span data-stu-id="8facc-130">The `Declare` statement includes the following elements.</span></span>  
  
#### <a name="auto-modifier"></a><span data-ttu-id="8facc-131">自動修飾詞</span><span class="sxs-lookup"><span data-stu-id="8facc-131">Auto modifier</span></span>  
 <span data-ttu-id="8facc-132">`Auto`修飾詞會指示執行階段根據根據通用語言執行階段規則 （或別名名稱，如果指定） 的方法名稱的字串轉換。</span><span class="sxs-lookup"><span data-stu-id="8facc-132">The `Auto` modifier instructs the runtime to convert the string based on the method name according to common language runtime rules (or alias name if specified).</span></span>  
  
#### <a name="lib-and-alias-keywords"></a><span data-ttu-id="8facc-133">Lib 和別名的關鍵字</span><span class="sxs-lookup"><span data-stu-id="8facc-133">Lib and Alias keywords</span></span>  
 <span data-ttu-id="8facc-134">名稱下`Function`關鍵字是程式用來存取匯入函式的名稱。</span><span class="sxs-lookup"><span data-stu-id="8facc-134">The name following the `Function` keyword is the name your program uses to access the imported function.</span></span> <span data-ttu-id="8facc-135">它可以是您呼叫的函式的實際名稱相同，或者您可以使用任何有效的程序名稱，然後採用`Alias`關鍵字來指定您要呼叫的函式的實際名稱。</span><span class="sxs-lookup"><span data-stu-id="8facc-135">It can be the same as the real name of the function you are calling, or you can use any valid procedure name and then employ the `Alias` keyword to specify the real name of the function you are calling.</span></span>  
  
 <span data-ttu-id="8facc-136">指定`Lib`關鍵字，後面的名稱和位置，其中包含您要呼叫的函式的 dll。</span><span class="sxs-lookup"><span data-stu-id="8facc-136">Specify the `Lib` keyword, followed by the name and location of the DLL that contains the function you are calling.</span></span> <span data-ttu-id="8facc-137">您不需要指定位於 Windows 系統目錄中檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="8facc-137">You do not need to specify the path for files located in the Windows system directories.</span></span>  
  
 <span data-ttu-id="8facc-138">使用`Alias`關鍵字，如果您要呼叫的函式名稱不是有效的[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]程序名稱或與您的應用程式中其他項目的名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="8facc-138">Use the `Alias` keyword if the name of the function you are calling is not a valid [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] procedure name, or conflicts with the name of other items in your application.</span></span> <span data-ttu-id="8facc-139">`Alias`表示所呼叫的函式，則為 true 的名稱。</span><span class="sxs-lookup"><span data-stu-id="8facc-139">`Alias` indicates the true name of the function being called.</span></span>  
  
#### <a name="argument-and-data-type-declarations"></a><span data-ttu-id="8facc-140">引數和資料型別宣告</span><span class="sxs-lookup"><span data-stu-id="8facc-140">Argument and Data Type Declarations</span></span>  
 <span data-ttu-id="8facc-141">宣告的引數和其資料型別。</span><span class="sxs-lookup"><span data-stu-id="8facc-141">Declare the arguments and their data types.</span></span> <span data-ttu-id="8facc-142">此組件可能項挑戰，因為 Windows 所使用的資料型別不會對應至 Visual Studio 資料型別。</span><span class="sxs-lookup"><span data-stu-id="8facc-142">This part can be challenging because the data types that Windows uses do not correspond to Visual Studio data types.</span></span> [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="8facc-143">將引數轉換為相容的資料型別，稱為程序會為您完成許多工作*封送處理*。</span><span class="sxs-lookup"><span data-stu-id="8facc-143"> does a lot of the work for you by converting arguments to compatible data types, a process called *marshaling*.</span></span> <span data-ttu-id="8facc-144">您可以明確地控制如何引數會封送處理使用<xref:System.Runtime.InteropServices.MarshalAsAttribute>中定義屬性<xref:System.Runtime.InteropServices>命名空間。</xref:System.Runtime.InteropServices> </xref:System.Runtime.InteropServices.MarshalAsAttribute></span><span class="sxs-lookup"><span data-stu-id="8facc-144">You can explicitly control how arguments are marshaled by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute defined in the <xref:System.Runtime.InteropServices> namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8facc-145">舊版的[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]允許您將參數宣告`As Any`，亦即該資料的任何資料型別可用。</span><span class="sxs-lookup"><span data-stu-id="8facc-145">Previous versions of [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] allowed you to declare parameters `As Any`, meaning that data of any data type could be used.</span></span> [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="8facc-146">要求您使用特定資料型別所有`Declare`陳述式。</span><span class="sxs-lookup"><span data-stu-id="8facc-146"> requires that you use a specific data type for all `Declare` statements.</span></span>  
  
#### <a name="windows-api-constants"></a><span data-ttu-id="8facc-147">Windows API 常數</span><span class="sxs-lookup"><span data-stu-id="8facc-147">Windows API Constants</span></span>  
 <span data-ttu-id="8facc-148">某些引數為常數的組合。</span><span class="sxs-lookup"><span data-stu-id="8facc-148">Some arguments are combinations of constants.</span></span> <span data-ttu-id="8facc-149">例如，`MessageBox`本逐步解說中的 API 可接受整數引數呼叫`Typ`，控制訊息方塊的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="8facc-149">For example, the `MessageBox` API shown in this walkthrough accepts an integer argument called `Typ` that controls how the message box is displayed.</span></span> <span data-ttu-id="8facc-150">您可以藉由檢查來判斷兩個常數數值`#define`winuser.h 檔案中的陳述式。</span><span class="sxs-lookup"><span data-stu-id="8facc-150">You can determine the numeric value of these constants by examining the `#define` statements in the file WinUser.h.</span></span> <span data-ttu-id="8facc-151">數字的值是通常以十六進位顯示，因此您可以使用 [小算盤] 將活動加入並轉換為十進位數。</span><span class="sxs-lookup"><span data-stu-id="8facc-151">The numeric values are generally shown in hexadecimal, so you may want to use a calculator to add them and convert to decimal.</span></span> <span data-ttu-id="8facc-152">例如，如果您想要合併的驚嘆號樣式常數`MB_ICONEXCLAMATION`0x00000030 與是/無樣式`MB_YESNO`0x00000004，您可以將數字相加，並取得 0x00000034 或 52 結果十進位。</span><span class="sxs-lookup"><span data-stu-id="8facc-152">For example, if you want to combine the constants for the exclamation style `MB_ICONEXCLAMATION` 0x00000030 and the Yes/No style `MB_YESNO` 0x00000004, you can add the numbers and get a result of 0x00000034, or 52 decimal.</span></span> <span data-ttu-id="8facc-153">雖然您可以直接使用十進位結果，最好是將這些值宣告為您的應用程式中的常數，並將它們結合使用`Or`運算子。</span><span class="sxs-lookup"><span data-stu-id="8facc-153">Although you can use the decimal result directly, it is better to declare these values as constants in your application and combine them using the `Or` operator.</span></span>  
  
###### <a name="to-declare-constants-for-windows-api-calls"></a><span data-ttu-id="8facc-154">若要宣告常數的 Windows API 呼叫</span><span class="sxs-lookup"><span data-stu-id="8facc-154">To declare constants for Windows API calls</span></span>  
  
1.  <span data-ttu-id="8facc-155">您要呼叫 Windows 函式，請參閱文件。</span><span class="sxs-lookup"><span data-stu-id="8facc-155">Consult the documentation for the Windows function you are calling.</span></span> <span data-ttu-id="8facc-156">決定使用的常數名稱以及包含這些常數數值的.h 檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="8facc-156">Determine the name of the constants it uses and the name of the .h file that contains the numeric values for these constants.</span></span>  
  
2.  <span data-ttu-id="8facc-157">若要檢視內容的標頭 (.h) 檔，使用文字編輯器，例如 [記事本]，並找出您正在使用的常數與相關聯的值。</span><span class="sxs-lookup"><span data-stu-id="8facc-157">Use a text editor, such as Notepad, to view the contents of the header (.h) file, and find the values associated with the constants you are using.</span></span> <span data-ttu-id="8facc-158">例如， `MessageBox` API 所使用的常數`MB_ICONQUESTION`在訊息方塊中顯示問號。</span><span class="sxs-lookup"><span data-stu-id="8facc-158">For example, the `MessageBox` API uses the constant `MB_ICONQUESTION` to show a question mark in the message box.</span></span> <span data-ttu-id="8facc-159">定義`MB_ICONQUESTION`WinUser.h 中，會出現，如下所示︰</span><span class="sxs-lookup"><span data-stu-id="8facc-159">The definition for `MB_ICONQUESTION` is in WinUser.h and appears as follows:</span></span>  
  
     `#define MB_ICONQUESTION             0x00000020L`  
  
3.  <span data-ttu-id="8facc-160">加入對等項目`Const`至您的類別或模組，讓您的應用程式可使用這些常數的陳述式。</span><span class="sxs-lookup"><span data-stu-id="8facc-160">Add equivalent `Const` statements to your class or module to make these constants available to your application.</span></span> <span data-ttu-id="8facc-161">例如: </span><span class="sxs-lookup"><span data-stu-id="8facc-161">For example:</span></span>  
  
     <span data-ttu-id="8facc-162">[!code-vb[VbVbalrInterop #&11;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="8facc-162">[!code-vb[VbVbalrInterop#11](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_2.vb)]</span></span>  
  
###### <a name="to-call-the-dll-procedure"></a><span data-ttu-id="8facc-163">呼叫 DLL 的程序</span><span class="sxs-lookup"><span data-stu-id="8facc-163">To call the DLL procedure</span></span>  
  
1.  <span data-ttu-id="8facc-164">新增一個按鈕名為`Button1`啟動表單專案，然後按兩下以檢視其程式碼。</span><span class="sxs-lookup"><span data-stu-id="8facc-164">Add a button named `Button1` to the startup form for your project, and then double-click it to view its code.</span></span> <span data-ttu-id="8facc-165">隨即出現按鈕的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="8facc-165">The event handler for the button is displayed.</span></span>  
  
2.  <span data-ttu-id="8facc-166">加入程式碼以`Click`加入呼叫程序，並提供適當的引數的按鈕事件處理常式︰</span><span class="sxs-lookup"><span data-stu-id="8facc-166">Add code to the `Click` event handler for the button you added, to call the procedure and provide the appropriate arguments:</span></span>  
  
     <span data-ttu-id="8facc-167">[!code-vb[VbVbalrInterop #&12;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="8facc-167">[!code-vb[VbVbalrInterop#12](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_3.vb)]</span></span>  
  
3.  <span data-ttu-id="8facc-168">按 F5 執行專案。</span><span class="sxs-lookup"><span data-stu-id="8facc-168">Run the project by pressing F5.</span></span> <span data-ttu-id="8facc-169">訊息方塊會顯示這兩個**是**和**否**回應按鈕。</span><span class="sxs-lookup"><span data-stu-id="8facc-169">The message box is displayed with both **Yes** and **No** response buttons.</span></span> <span data-ttu-id="8facc-170">按一下其中一個。</span><span class="sxs-lookup"><span data-stu-id="8facc-170">Click either one.</span></span>  
  
#### <a name="data-marshaling"></a><span data-ttu-id="8facc-171">資料封送處理</span><span class="sxs-lookup"><span data-stu-id="8facc-171">Data Marshaling</span></span>  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="8facc-172">自動轉換資料類型的參數和傳回值的 Windows API 呼叫，但是您可以使用`MarshalAs`屬性來明確指定 API 所預期的不受管理的資料型別。</span><span class="sxs-lookup"><span data-stu-id="8facc-172"> automatically converts the data types of parameters and return values for Windows API calls, but you can use the `MarshalAs` attribute to explicitly specify unmanaged data types that an API expects.</span></span> <span data-ttu-id="8facc-173">如需 interop 封送處理的詳細資訊，請參閱[Interop 封送處理](http://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a)。</span><span class="sxs-lookup"><span data-stu-id="8facc-173">For more information about interop marshaling, see [Interop Marshaling](http://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a).</span></span>  
  
###### <a name="to-use-declare-and-marshalas-in-an-api-call"></a><span data-ttu-id="8facc-174">若要使用 Declare 和 MarshalAs API 呼叫</span><span class="sxs-lookup"><span data-stu-id="8facc-174">To use Declare and MarshalAs in an API call</span></span>  
  
1.  <span data-ttu-id="8facc-175">決定您想要再加上其引數，呼叫資料類型的函式的名稱，並傳回值。</span><span class="sxs-lookup"><span data-stu-id="8facc-175">Determine the name of the function you want to call, plus its arguments, data types, and return value.</span></span>  
  
2.  <span data-ttu-id="8facc-176">若要簡化存取`MarshalAs`屬性中，加入`Imports`陳述式的類別或模組，如下列範例所示的程式碼頂端︰</span><span class="sxs-lookup"><span data-stu-id="8facc-176">To simplify access to the `MarshalAs` attribute, add an `Imports` statement to the top of the code for the class or module, as in the following example:</span></span>  
  
     <span data-ttu-id="8facc-177">[!code-vb[VbVbalrInterop #&13;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="8facc-177">[!code-vb[VbVbalrInterop#13](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_4.vb)]</span></span>  
  
3.  <span data-ttu-id="8facc-178">將函式原型來匯入函式加入至類別或模組，您使用，並套用`MarshalAs`屬性的參數或傳回值。</span><span class="sxs-lookup"><span data-stu-id="8facc-178">Add a function prototype for the imported function to the class or module you are using, and apply the `MarshalAs` attribute to the parameters or return value.</span></span> <span data-ttu-id="8facc-179">在下列範例中，可預期的型別的 API 呼叫`void*`封送處理為`AsAny`:</span><span class="sxs-lookup"><span data-stu-id="8facc-179">In the following example, an API call that expects the type `void*` is marshaled as `AsAny`:</span></span>  
  
     <span data-ttu-id="8facc-180">[!code-vb[VbVbalrInterop #&14;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="8facc-180">[!code-vb[VbVbalrInterop#14](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_5.vb)]</span></span>  
  
## <a name="api-calls-using-dllimport"></a><span data-ttu-id="8facc-181">API 呼叫使用 DllImport</span><span class="sxs-lookup"><span data-stu-id="8facc-181">API Calls Using DllImport</span></span>  
 <span data-ttu-id="8facc-182">`DllImport`屬性會提供 Dll 中呼叫函式，而不需要型別程式庫的第二種方式。</span><span class="sxs-lookup"><span data-stu-id="8facc-182">The `DllImport` attribute provides a second way to call functions in DLLs without type libraries.</span></span> <span data-ttu-id="8facc-183">`DllImport`大致上相當於使用`Declare`陳述式，但提供更充分掌控函式呼叫的方式。</span><span class="sxs-lookup"><span data-stu-id="8facc-183">`DllImport` is roughly equivalent to using a `Declare` statement but provides more control over how functions are called.</span></span>  
  
 <span data-ttu-id="8facc-184">您可以使用`DllImport`與大多數 Windows API 呼叫，只要呼叫指的是共用 (有時稱為*靜態*) 方法。</span><span class="sxs-lookup"><span data-stu-id="8facc-184">You can use `DllImport` with most Windows API calls as long as the call refers to a shared (sometimes called *static*) method.</span></span> <span data-ttu-id="8facc-185">您不能使用需要的類別執行個體的方法。</span><span class="sxs-lookup"><span data-stu-id="8facc-185">You cannot use methods that require an instance of a class.</span></span> <span data-ttu-id="8facc-186">不同於`Declare`陳述式，`DllImport`呼叫不能使用`MarshalAs`屬性。</span><span class="sxs-lookup"><span data-stu-id="8facc-186">Unlike `Declare` statements, `DllImport` calls cannot use the `MarshalAs` attribute.</span></span>  
  
#### <a name="to-call-a-windows-api-using-the-dllimport-attribute"></a><span data-ttu-id="8facc-187">呼叫 Windows API 使用 DllImport 屬性</span><span class="sxs-lookup"><span data-stu-id="8facc-187">To call a Windows API using the DllImport attribute</span></span>  
  
1.  <span data-ttu-id="8facc-188">開啟新的 Windows 應用程式專案，依序按一下**新增**上**檔案**] 功能表，然後按一下 [**專案**。</span><span class="sxs-lookup"><span data-stu-id="8facc-188">Open a new Windows Application project by clicking **New** on the **File** menu, and then clicking **Project**.</span></span> <span data-ttu-id="8facc-189">[ **新增專案** ] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="8facc-189">The **New Project** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="8facc-190">選取**Windows 應用程式**從清單中的[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]專案範本。</span><span class="sxs-lookup"><span data-stu-id="8facc-190">Select **Windows Application** from the list of [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] project templates.</span></span> <span data-ttu-id="8facc-191">會顯示新的專案。</span><span class="sxs-lookup"><span data-stu-id="8facc-191">The new project is displayed.</span></span>  
  
3.  <span data-ttu-id="8facc-192">新增一個按鈕名為`Button2`的啟動表單。</span><span class="sxs-lookup"><span data-stu-id="8facc-192">Add a button named `Button2` to the startup form.</span></span>  
  
4.  <span data-ttu-id="8facc-193">按兩下`Button2`開啟表單的程式碼檢視。</span><span class="sxs-lookup"><span data-stu-id="8facc-193">Double-click `Button2` to open the code view for the form.</span></span>  
  
5.  <span data-ttu-id="8facc-194">若要簡化存取`DllImport`，加入`Imports`啟動表單類別的程式碼頂端的陳述式︰</span><span class="sxs-lookup"><span data-stu-id="8facc-194">To simplify access to `DllImport`, add an `Imports` statement to the top of the code for the startup form class:</span></span>  
  
     <span data-ttu-id="8facc-195">[!code-vb[VbVbalrInterop #&13;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="8facc-195">[!code-vb[VbVbalrInterop#13](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_4.vb)]</span></span>  
  
6.  <span data-ttu-id="8facc-196">空白的函式之前宣告`End Class`表單中，而且名稱函式的陳述式`MoveFile`。</span><span class="sxs-lookup"><span data-stu-id="8facc-196">Declare an empty function preceding the `End Class` statement for the form, and name the function `MoveFile`.</span></span>  
  
7.  <span data-ttu-id="8facc-197">套用`Public`和`Shared`函式宣告和設定參數的修飾詞`MoveFile`根據 Windows API 函式會使用的引數︰</span><span class="sxs-lookup"><span data-stu-id="8facc-197">Apply the `Public` and `Shared` modifiers to the function declaration and set parameters for `MoveFile` based on the arguments the Windows API function uses:</span></span>  
  
     <span data-ttu-id="8facc-198">[!code-vb[VbVbalrInterop #&16;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="8facc-198">[!code-vb[VbVbalrInterop#16](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_6.vb)]</span></span>  
  
     <span data-ttu-id="8facc-199">您的函式可以有任何有效的程序名稱;`DllImport`屬性在 DLL 中指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="8facc-199">Your function can have any valid procedure name; the `DllImport` attribute specifies the name in the DLL.</span></span> <span data-ttu-id="8facc-200">它也會處理互通性封送處理參數和傳回值，因此您可以選擇 Visual Studio 資料類型類似的資料類型則 API 使用。</span><span class="sxs-lookup"><span data-stu-id="8facc-200">It also handles interoperability marshaling for the parameters and return values, so you can choose Visual Studio data types that are similar to the data types the API uses.</span></span>  
  
8.  <span data-ttu-id="8facc-201">套用`DllImport`屬性設定為空白的函式。</span><span class="sxs-lookup"><span data-stu-id="8facc-201">Apply the `DllImport` attribute to the empty function.</span></span> <span data-ttu-id="8facc-202">第一個參數是包含您要呼叫的函式的 dll 位置與名稱。</span><span class="sxs-lookup"><span data-stu-id="8facc-202">The first parameter is the name and location of the DLL containing the function you are calling.</span></span> <span data-ttu-id="8facc-203">您不需要指定位於 Windows 系統目錄中檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="8facc-203">You do not need to specify the path for files located in the Windows system directories.</span></span> <span data-ttu-id="8facc-204">第二個參數是在 Windows API 中指定的函式名稱的具名引數。</span><span class="sxs-lookup"><span data-stu-id="8facc-204">The second parameter is a named argument that specifies the name of the function in the Windows API.</span></span> <span data-ttu-id="8facc-205">在此範例中，`DllImport`屬性會強制執行呼叫`MoveFile`轉送至`MoveFileW`KERNEL32 中。DLL。</span><span class="sxs-lookup"><span data-stu-id="8facc-205">In this example, the `DllImport` attribute forces calls to `MoveFile` to be forwarded to `MoveFileW` in KERNEL32.DLL.</span></span> <span data-ttu-id="8facc-206">`MoveFileW`方法會複製檔案的路徑`src`路徑`dst`。</span><span class="sxs-lookup"><span data-stu-id="8facc-206">The `MoveFileW` method copies a file from the path `src` to the path `dst`.</span></span>  
  
     <span data-ttu-id="8facc-207">[!code-vb[VbVbalrInterop #&17;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="8facc-207">[!code-vb[VbVbalrInterop#17](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_7.vb)]</span></span>  
  
9. <span data-ttu-id="8facc-208">加入程式碼以`Button2_Click`事件處理常式呼叫的函式︰</span><span class="sxs-lookup"><span data-stu-id="8facc-208">Add code to the `Button2_Click` event handler to call the function:</span></span>  
  
     <span data-ttu-id="8facc-209">[!code-vb[VbVbalrInterop #&18;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="8facc-209">[!code-vb[VbVbalrInterop#18](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_8.vb)]</span></span>  
  
10. <span data-ttu-id="8facc-210">建立名為 Test.txt 的檔案，並將它放在硬碟上 C:\Tmp 目錄中。</span><span class="sxs-lookup"><span data-stu-id="8facc-210">Create a file named Test.txt and place it in the C:\Tmp directory on your hard drive.</span></span> <span data-ttu-id="8facc-211">如有必要，請建立 Tmp 目錄。</span><span class="sxs-lookup"><span data-stu-id="8facc-211">Create the Tmp directory if necessary.</span></span>  
  
11. <span data-ttu-id="8facc-212">請按 F5 啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="8facc-212">Press F5 to start the application.</span></span> <span data-ttu-id="8facc-213">主表單隨即出現。</span><span class="sxs-lookup"><span data-stu-id="8facc-213">The main form appears.</span></span>  
  
12. <span data-ttu-id="8facc-214">按一下  **Button2**。</span><span class="sxs-lookup"><span data-stu-id="8facc-214">Click **Button2**.</span></span> <span data-ttu-id="8facc-215">如果可以移動檔案，會顯示 「 已成功移動檔案 」 訊息。</span><span class="sxs-lookup"><span data-stu-id="8facc-215">The message "The file was moved successfully" is displayed if the file can be moved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8facc-216">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8facc-216">See Also</span></span>  
 <span data-ttu-id="8facc-217"><xref:System.Runtime.InteropServices.DllImportAttribute></xref:System.Runtime.InteropServices.DllImportAttribute></span><span class="sxs-lookup"><span data-stu-id="8facc-217"><xref:System.Runtime.InteropServices.DllImportAttribute></span></span>   
 <span data-ttu-id="8facc-218"><xref:System.Runtime.InteropServices.MarshalAsAttribute></xref:System.Runtime.InteropServices.MarshalAsAttribute></span><span class="sxs-lookup"><span data-stu-id="8facc-218"><xref:System.Runtime.InteropServices.MarshalAsAttribute></span></span>   
<span data-ttu-id="8facc-219"> [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md) </span><span class="sxs-lookup"><span data-stu-id="8facc-219"> [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) </span></span>  
<span data-ttu-id="8facc-220"> [自動](../../../visual-basic/language-reference/modifiers/auto.md) </span><span class="sxs-lookup"><span data-stu-id="8facc-220"> [Auto](../../../visual-basic/language-reference/modifiers/auto.md) </span></span>  
<span data-ttu-id="8facc-221"> [別名](../../../visual-basic/language-reference/statements/alias-clause.md) </span><span class="sxs-lookup"><span data-stu-id="8facc-221"> [Alias](../../../visual-basic/language-reference/statements/alias-clause.md) </span></span>  
<span data-ttu-id="8facc-222"> [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md) </span><span class="sxs-lookup"><span data-stu-id="8facc-222"> [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md) </span></span>  
<span data-ttu-id="8facc-223"> [在 Managed 程式碼中建立原型](http://msdn.microsoft.com/library/ecdcf25d-cae3-4f07-a2b6-8397ac6dc42d) </span><span class="sxs-lookup"><span data-stu-id="8facc-223"> [Creating Prototypes in Managed Code](http://msdn.microsoft.com/library/ecdcf25d-cae3-4f07-a2b6-8397ac6dc42d) </span></span>  
<span data-ttu-id="8facc-224"> [做為回呼方法，委派封送處理](http://msdn.microsoft.com/library/6ddd7866-9804-4571-84de-83f5cc017a5a)</span><span class="sxs-lookup"><span data-stu-id="8facc-224"> [Marshaling a Delegate as a Callback Method](http://msdn.microsoft.com/library/6ddd7866-9804-4571-84de-83f5cc017a5a)</span></span>
