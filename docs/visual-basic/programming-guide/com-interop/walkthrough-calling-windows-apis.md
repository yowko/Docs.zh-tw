---
title: 逐步解說：呼叫 Windows API (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- DLLs, calling
- Windows API, walkthroughs
- platform invoke, walkthroughs
- API calls [Visual Basic], walkthroughs [Visual Basic]
- Windows API, calling
- walkthroughs [Visual Basic], API calls
- DllImport attribute, calling Windows API
- Declare statement [Visual Basic], declaring DLL functions
ms.assetid: 9280ca96-7a93-47a3-8d01-6d01be0657cb
ms.openlocfilehash: bb98d842bfe65bdf637a789fc9a8319a70cb2bc8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-calling-windows-apis-visual-basic"></a><span data-ttu-id="0c68d-102">逐步解說：呼叫 Windows API (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c68d-102">Walkthrough: Calling Windows APIs (Visual Basic)</span></span>
<span data-ttu-id="0c68d-103">Windows 應用程式開發介面是屬於 Windows 作業系統的動態連結程式庫 (Dll)。</span><span class="sxs-lookup"><span data-stu-id="0c68d-103">Windows APIs are dynamic-link libraries (DLLs) that are part of the Windows operating system.</span></span> <span data-ttu-id="0c68d-104">您可以使用它們來執行工作時很難撰寫您自己的對等的程序。</span><span class="sxs-lookup"><span data-stu-id="0c68d-104">You use them to perform tasks when it is difficult to write equivalent procedures of your own.</span></span> <span data-ttu-id="0c68d-105">例如，Windows 提供函式，名為`FlashWindowEx`，可讓您的應用程式的標題列切換淺色及深色陰影。</span><span class="sxs-lookup"><span data-stu-id="0c68d-105">For example, Windows provides a function named `FlashWindowEx` that lets you make the title bar for an application alternate between light and dark shades.</span></span>  
  
 <span data-ttu-id="0c68d-106">在您的程式碼中使用 Windows Api 的優點是因為它們包含數十個有用的函式已撰寫並可立即使用可節省開發時間。</span><span class="sxs-lookup"><span data-stu-id="0c68d-106">The advantage of using Windows APIs in your code is that they can save development time because they contain dozens of useful functions that are already written and waiting to be used.</span></span> <span data-ttu-id="0c68d-107">缺點是 Windows 應用程式開發介面很難進行時，發生錯誤之工作和正確性。</span><span class="sxs-lookup"><span data-stu-id="0c68d-107">The disadvantage is that Windows APIs can be difficult to work with and unforgiving when things go wrong.</span></span>  
  
 <span data-ttu-id="0c68d-108">Windows Api 就是一個特殊種類的互通性。</span><span class="sxs-lookup"><span data-stu-id="0c68d-108">Windows APIs represent a special category of interoperability.</span></span> <span data-ttu-id="0c68d-109">Windows 應用程式開發介面不會使用 managed 程式碼，並沒有內建型別程式庫，並使用不同於 Visual Studio 搭配使用的資料類型。</span><span class="sxs-lookup"><span data-stu-id="0c68d-109">Windows APIs do not use managed code, do not have built-in type libraries, and use data types that are different than those used with Visual Studio.</span></span> <span data-ttu-id="0c68d-110">因為這些差異，以及因為 Windows 應用程式開發介面不是 COM 物件，與 Windows Api 的互通性和[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]必須利用平台叫用時，或 PInvoke。</span><span class="sxs-lookup"><span data-stu-id="0c68d-110">Because of these differences, and because Windows APIs are not COM objects, interoperability with Windows APIs and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] is performed using platform invoke, or PInvoke.</span></span> <span data-ttu-id="0c68d-111">平台叫用是一項服務，可讓 managed 程式碼呼叫 unmanaged 函式實作在 Dll 中。</span><span class="sxs-lookup"><span data-stu-id="0c68d-111">Platform invoke is a service that enables managed code to call unmanaged functions implemented in DLLs.</span></span> <span data-ttu-id="0c68d-112">如需詳細資訊，請參閱[使用 Unmanaged DLL 函式](../../../framework/interop/consuming-unmanaged-dll-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="0c68d-112">For more information, see [Consuming Unmanaged DLL Functions](../../../framework/interop/consuming-unmanaged-dll-functions.md).</span></span> <span data-ttu-id="0c68d-113">您也可以使用 Visual Basic 中使用 PInvoke`Declare`陳述式或套用`DllImport`屬性設定為空的程序。</span><span class="sxs-lookup"><span data-stu-id="0c68d-113">You can use PInvoke in Visual Basic by using either the `Declare` statement or applying the `DllImport` attribute to an empty procedure.</span></span>  
  
 <span data-ttu-id="0c68d-114">Windows API 呼叫是 Visual Basic 在過去，程式設計中很重要的一部分，但很少會需要使用 Visual Basic.NET。</span><span class="sxs-lookup"><span data-stu-id="0c68d-114">Windows API calls were an important part of Visual Basic programming in the past, but are seldom necessary with Visual Basic .NET.</span></span> <span data-ttu-id="0c68d-115">可能的話，您應該使用 managed 程式碼從[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]來執行工作，而不是 Windows API 呼叫。</span><span class="sxs-lookup"><span data-stu-id="0c68d-115">Whenever possible, you should use managed code from the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] to perform tasks, instead of Windows API calls.</span></span> <span data-ttu-id="0c68d-116">本逐步解說提供針對這些情況中使用的資訊是必要的 Windows 應用程式開發介面。</span><span class="sxs-lookup"><span data-stu-id="0c68d-116">This walkthrough provides information for those situations in which using Windows APIs is necessary.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="api-calls-using-declare"></a><span data-ttu-id="0c68d-117">使用 API 呼叫宣告</span><span class="sxs-lookup"><span data-stu-id="0c68d-117">API Calls Using Declare</span></span>  
 <span data-ttu-id="0c68d-118">呼叫 Windows Api 的最常見方式是使用`Declare`陳述式。</span><span class="sxs-lookup"><span data-stu-id="0c68d-118">The most common way to call Windows APIs is by using the `Declare` statement.</span></span>  
  
#### <a name="to-declare-a-dll-procedure"></a><span data-ttu-id="0c68d-119">宣告 DLL 程序</span><span class="sxs-lookup"><span data-stu-id="0c68d-119">To declare a DLL procedure</span></span>  
  
1.  <span data-ttu-id="0c68d-120">決定您想要呼叫，函式加上引數，引數類型的名稱，並傳回值，以及名稱和包含該 DLL 的位置。</span><span class="sxs-lookup"><span data-stu-id="0c68d-120">Determine the name of the function you want to call, plus its arguments, argument types, and return value, as well as the name and location of the DLL that contains it.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0c68d-121">如需 Windows Api 的完整資訊，請參閱平台 SDK Windows API 中的 Win32 SDK 文件。</span><span class="sxs-lookup"><span data-stu-id="0c68d-121">For complete information about the Windows APIs, see the Win32 SDK documentation in the Platform SDK Windows API.</span></span> <span data-ttu-id="0c68d-122">如需有關 Windows 應用程式開發介面使用的常數的詳細資訊，請檢查例如 Windows.h 隨附平台 SDK 的標頭檔。</span><span class="sxs-lookup"><span data-stu-id="0c68d-122">For more information about the constants that Windows APIs use, examine the header files such as Windows.h included with the Platform SDK.</span></span>  
  
2.  <span data-ttu-id="0c68d-123">開啟新的 Windows 應用程式專案，依序按一下**新增**上**檔案**] 功能表，然後按一下 [**專案**。</span><span class="sxs-lookup"><span data-stu-id="0c68d-123">Open a new Windows Application project by clicking **New** on the **File** menu, and then clicking **Project**.</span></span> <span data-ttu-id="0c68d-124">[ **新增專案** ] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="0c68d-124">The **New Project** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="0c68d-125">選取**Windows 應用程式**從 Visual Basic 專案範本的清單。</span><span class="sxs-lookup"><span data-stu-id="0c68d-125">Select **Windows Application** from the list of Visual Basic project templates.</span></span> <span data-ttu-id="0c68d-126">新的專案隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="0c68d-126">The new project is displayed.</span></span>  
  
4.  <span data-ttu-id="0c68d-127">加入下列`Declare`函式類別，或是您要使用 DLL 的模組：</span><span class="sxs-lookup"><span data-stu-id="0c68d-127">Add the following `Declare` function either to the class or module in which you want to use the DLL:</span></span>  
  
     [!code-vb[VbVbalrInterop#9](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_1.vb)]  
  
### <a name="parts-of-the-declare-statement"></a><span data-ttu-id="0c68d-128">組件的 Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="0c68d-128">Parts of the Declare Statement</span></span>  
 <span data-ttu-id="0c68d-129">`Declare`陳述式包含下列項目。</span><span class="sxs-lookup"><span data-stu-id="0c68d-129">The `Declare` statement includes the following elements.</span></span>  
  
#### <a name="auto-modifier"></a><span data-ttu-id="0c68d-130">Auto 修飾詞</span><span class="sxs-lookup"><span data-stu-id="0c68d-130">Auto modifier</span></span>  
 <span data-ttu-id="0c68d-131">`Auto`修飾詞會指示執行階段將根據根據 common language runtime 的規則 （或如果指定的別名名稱） 的方法名稱的字串轉換。</span><span class="sxs-lookup"><span data-stu-id="0c68d-131">The `Auto` modifier instructs the runtime to convert the string based on the method name according to common language runtime rules (or alias name if specified).</span></span>  
  
#### <a name="lib-and-alias-keywords"></a><span data-ttu-id="0c68d-132">Lib 和別名的關鍵字</span><span class="sxs-lookup"><span data-stu-id="0c68d-132">Lib and Alias keywords</span></span>  
 <span data-ttu-id="0c68d-133">名稱下`Function`關鍵字是程式用來存取匯入的函式的名稱。</span><span class="sxs-lookup"><span data-stu-id="0c68d-133">The name following the `Function` keyword is the name your program uses to access the imported function.</span></span> <span data-ttu-id="0c68d-134">它可以您呼叫的函式的實際名稱相同，或者您可以使用任何有效的程序名稱，然後採用`Alias`關鍵字來指定您要呼叫的函式的實際名稱。</span><span class="sxs-lookup"><span data-stu-id="0c68d-134">It can be the same as the real name of the function you are calling, or you can use any valid procedure name and then employ the `Alias` keyword to specify the real name of the function you are calling.</span></span>  
  
 <span data-ttu-id="0c68d-135">指定`Lib`關鍵字，後面的名稱和包含您要呼叫的函式之 dll 的位置。</span><span class="sxs-lookup"><span data-stu-id="0c68d-135">Specify the `Lib` keyword, followed by the name and location of the DLL that contains the function you are calling.</span></span> <span data-ttu-id="0c68d-136">您不需要指定位於 Windows 系統目錄中檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="0c68d-136">You do not need to specify the path for files located in the Windows system directories.</span></span>  
  
 <span data-ttu-id="0c68d-137">使用`Alias`關鍵字，如果您要呼叫的函式名稱不是有效的 Visual Basic 程序名稱，或與您的應用程式中其他項目的名稱發生衝突。</span><span class="sxs-lookup"><span data-stu-id="0c68d-137">Use the `Alias` keyword if the name of the function you are calling is not a valid Visual Basic procedure name, or conflicts with the name of other items in your application.</span></span> <span data-ttu-id="0c68d-138">`Alias` 表示正在呼叫函式，則為 true 的名稱。</span><span class="sxs-lookup"><span data-stu-id="0c68d-138">`Alias` indicates the true name of the function being called.</span></span>  
  
#### <a name="argument-and-data-type-declarations"></a><span data-ttu-id="0c68d-139">引數和資料型別宣告</span><span class="sxs-lookup"><span data-stu-id="0c68d-139">Argument and Data Type Declarations</span></span>  
 <span data-ttu-id="0c68d-140">宣告引數和其資料類型。</span><span class="sxs-lookup"><span data-stu-id="0c68d-140">Declare the arguments and their data types.</span></span> <span data-ttu-id="0c68d-141">此組件會有點困難，因為 Windows 使用的資料型別沒有對應至 Visual Studio 資料類型。</span><span class="sxs-lookup"><span data-stu-id="0c68d-141">This part can be challenging because the data types that Windows uses do not correspond to Visual Studio data types.</span></span> <span data-ttu-id="0c68d-142">Visual Basic 將引數轉換成相容的資料類型，稱為程序，將大量的工作會為您*封送處理*。</span><span class="sxs-lookup"><span data-stu-id="0c68d-142">Visual Basic does a lot of the work for you by converting arguments to compatible data types, a process called *marshaling*.</span></span> <span data-ttu-id="0c68d-143">您可以明確地控制如何引數封送處理使用<xref:System.Runtime.InteropServices.MarshalAsAttribute>中定義屬性<xref:System.Runtime.InteropServices>命名空間。</span><span class="sxs-lookup"><span data-stu-id="0c68d-143">You can explicitly control how arguments are marshaled by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute defined in the <xref:System.Runtime.InteropServices> namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0c68d-144">舊版的 Visual Basic 可讓您將參數宣告`As Any`，這表示該資料的任何資料類型無法使用。</span><span class="sxs-lookup"><span data-stu-id="0c68d-144">Previous versions of Visual Basic allowed you to declare parameters `As Any`, meaning that data of any data type could be used.</span></span> <span data-ttu-id="0c68d-145">Visual Basic 會要求您使用特定資料類型，所有`Declare`陳述式。</span><span class="sxs-lookup"><span data-stu-id="0c68d-145">Visual Basic requires that you use a specific data type for all `Declare` statements.</span></span>  
  
#### <a name="windows-api-constants"></a><span data-ttu-id="0c68d-146">Windows 應用程式開發介面常數</span><span class="sxs-lookup"><span data-stu-id="0c68d-146">Windows API Constants</span></span>  
 <span data-ttu-id="0c68d-147">某些引數為常數的組合。</span><span class="sxs-lookup"><span data-stu-id="0c68d-147">Some arguments are combinations of constants.</span></span> <span data-ttu-id="0c68d-148">例如， `MessageBox` API 在這個逐步解說中所示接受整數引數呼叫`Typ`，控制訊息方塊的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="0c68d-148">For example, the `MessageBox` API shown in this walkthrough accepts an integer argument called `Typ` that controls how the message box is displayed.</span></span> <span data-ttu-id="0c68d-149">您可以藉由檢查來判斷這些常數的數值`#define`WinUser.h 檔案中的陳述式。</span><span class="sxs-lookup"><span data-stu-id="0c68d-149">You can determine the numeric value of these constants by examining the `#define` statements in the file WinUser.h.</span></span> <span data-ttu-id="0c68d-150">數字的值是通常以十六進位顯示，所以您可能想要使用 [小算盤] 將活動加入並轉換為十進位數。</span><span class="sxs-lookup"><span data-stu-id="0c68d-150">The numeric values are generally shown in hexadecimal, so you may want to use a calculator to add them and convert to decimal.</span></span> <span data-ttu-id="0c68d-151">例如，如果您想要合併的驚嘆號樣式常數`MB_ICONEXCLAMATION`0x00000030 和 是/沒有樣式`MB_YESNO`0x00000004，您可以將時數，並取得結果 0x00000034 或 52 十進位。</span><span class="sxs-lookup"><span data-stu-id="0c68d-151">For example, if you want to combine the constants for the exclamation style `MB_ICONEXCLAMATION` 0x00000030 and the Yes/No style `MB_YESNO` 0x00000004, you can add the numbers and get a result of 0x00000034, or 52 decimal.</span></span> <span data-ttu-id="0c68d-152">雖然您可以直接使用十進位的結果，最好是將這些值宣告為您的應用程式中的常數，並將它們結合使用`Or`運算子。</span><span class="sxs-lookup"><span data-stu-id="0c68d-152">Although you can use the decimal result directly, it is better to declare these values as constants in your application and combine them using the `Or` operator.</span></span>  
  
###### <a name="to-declare-constants-for-windows-api-calls"></a><span data-ttu-id="0c68d-153">若要宣告常數的 Windows API 呼叫</span><span class="sxs-lookup"><span data-stu-id="0c68d-153">To declare constants for Windows API calls</span></span>  
  
1.  <span data-ttu-id="0c68d-154">您要呼叫 Windows 函式，請參閱文件。</span><span class="sxs-lookup"><span data-stu-id="0c68d-154">Consult the documentation for the Windows function you are calling.</span></span> <span data-ttu-id="0c68d-155">決定使用的常數的名稱以及包含這些常數數值的.h 檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="0c68d-155">Determine the name of the constants it uses and the name of the .h file that contains the numeric values for these constants.</span></span>  
  
2.  <span data-ttu-id="0c68d-156">使用文字編輯器，例如 [記事本]，檢視標頭 (.h) 檔案的內容，並尋找您要使用的常數與相關聯的值。</span><span class="sxs-lookup"><span data-stu-id="0c68d-156">Use a text editor, such as Notepad, to view the contents of the header (.h) file, and find the values associated with the constants you are using.</span></span> <span data-ttu-id="0c68d-157">例如， `MessageBox` API 所使用常數`MB_ICONQUESTION`以訊息方塊中顯示一個問號。</span><span class="sxs-lookup"><span data-stu-id="0c68d-157">For example, the `MessageBox` API uses the constant `MB_ICONQUESTION` to show a question mark in the message box.</span></span> <span data-ttu-id="0c68d-158">定義`MB_ICONQUESTION`WinUser.h 中，而且會出現，如下所示：</span><span class="sxs-lookup"><span data-stu-id="0c68d-158">The definition for `MB_ICONQUESTION` is in WinUser.h and appears as follows:</span></span>  
  
     `#define MB_ICONQUESTION             0x00000020L`  
  
3.  <span data-ttu-id="0c68d-159">加入對等項目`Const`類別或模組，以便讓應用程式可以使用這些常數的陳述式。</span><span class="sxs-lookup"><span data-stu-id="0c68d-159">Add equivalent `Const` statements to your class or module to make these constants available to your application.</span></span> <span data-ttu-id="0c68d-160">例如: </span><span class="sxs-lookup"><span data-stu-id="0c68d-160">For example:</span></span>  
  
     [!code-vb[VbVbalrInterop#11](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_2.vb)]  
  
###### <a name="to-call-the-dll-procedure"></a><span data-ttu-id="0c68d-161">若要呼叫的 DLL 程序</span><span class="sxs-lookup"><span data-stu-id="0c68d-161">To call the DLL procedure</span></span>  
  
1.  <span data-ttu-id="0c68d-162">將名為按鈕加入`Button1`啟動以您的專案，然後按兩下以檢視其程式碼。</span><span class="sxs-lookup"><span data-stu-id="0c68d-162">Add a button named `Button1` to the startup form for your project, and then double-click it to view its code.</span></span> <span data-ttu-id="0c68d-163">隨即出現按鈕的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="0c68d-163">The event handler for the button is displayed.</span></span>  
  
2.  <span data-ttu-id="0c68d-164">將程式碼加入`Click`加入呼叫程序，並提供適當的引數的按鈕的事件處理常式：</span><span class="sxs-lookup"><span data-stu-id="0c68d-164">Add code to the `Click` event handler for the button you added, to call the procedure and provide the appropriate arguments:</span></span>  
  
     [!code-vb[VbVbalrInterop#12](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_3.vb)]  
  
3.  <span data-ttu-id="0c68d-165">按 F5 執行專案。</span><span class="sxs-lookup"><span data-stu-id="0c68d-165">Run the project by pressing F5.</span></span> <span data-ttu-id="0c68d-166">訊息方塊會顯示與這兩個**是**和**否**回應按鈕。</span><span class="sxs-lookup"><span data-stu-id="0c68d-166">The message box is displayed with both **Yes** and **No** response buttons.</span></span> <span data-ttu-id="0c68d-167">按一下其中一個。</span><span class="sxs-lookup"><span data-stu-id="0c68d-167">Click either one.</span></span>  
  
#### <a name="data-marshaling"></a><span data-ttu-id="0c68d-168">資料封送處理</span><span class="sxs-lookup"><span data-stu-id="0c68d-168">Data Marshaling</span></span>  
 <span data-ttu-id="0c68d-169">Visual Basic 會自動轉換資料類型的參數和傳回值的 Windows API 呼叫，但是您可以使用`MarshalAs`屬性來明確地指定應用程式開發介面所預期的 unmanaged 的資料類型。</span><span class="sxs-lookup"><span data-stu-id="0c68d-169">Visual Basic automatically converts the data types of parameters and return values for Windows API calls, but you can use the `MarshalAs` attribute to explicitly specify unmanaged data types that an API expects.</span></span> <span data-ttu-id="0c68d-170">如需 interop 封送處理的詳細資訊，請參閱[Interop 封送處理](../../../framework/interop/interop-marshaling.md)。</span><span class="sxs-lookup"><span data-stu-id="0c68d-170">For more information about interop marshaling, see [Interop Marshaling](../../../framework/interop/interop-marshaling.md).</span></span>  
  
###### <a name="to-use-declare-and-marshalas-in-an-api-call"></a><span data-ttu-id="0c68d-171">API 呼叫中使用 Declare 與 MarshalAs</span><span class="sxs-lookup"><span data-stu-id="0c68d-171">To use Declare and MarshalAs in an API call</span></span>  
  
1.  <span data-ttu-id="0c68d-172">決定您想要加上其引數，呼叫資料類型的函式的名稱，並傳回值。</span><span class="sxs-lookup"><span data-stu-id="0c68d-172">Determine the name of the function you want to call, plus its arguments, data types, and return value.</span></span>  
  
2.  <span data-ttu-id="0c68d-173">若要簡化存取`MarshalAs`屬性，請將`Imports`陳述式的類別或模組，如下列範例所示的程式碼的頂端：</span><span class="sxs-lookup"><span data-stu-id="0c68d-173">To simplify access to the `MarshalAs` attribute, add an `Imports` statement to the top of the code for the class or module, as in the following example:</span></span>  
  
     [!code-vb[VbVbalrInterop#13](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_4.vb)]  
  
3.  <span data-ttu-id="0c68d-174">將匯入的函式的函式原型加入至類別或模組，您可以使用，並套用`MarshalAs`屬性的參數或傳回值。</span><span class="sxs-lookup"><span data-stu-id="0c68d-174">Add a function prototype for the imported function to the class or module you are using, and apply the `MarshalAs` attribute to the parameters or return value.</span></span> <span data-ttu-id="0c68d-175">在下列範例中，預期的類型的應用程式開發介面呼叫`void*`封送處理為`AsAny`:</span><span class="sxs-lookup"><span data-stu-id="0c68d-175">In the following example, an API call that expects the type `void*` is marshaled as `AsAny`:</span></span>  
  
     [!code-vb[VbVbalrInterop#14](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_5.vb)]  
  
## <a name="api-calls-using-dllimport"></a><span data-ttu-id="0c68d-176">API 呼叫使用 DllImport</span><span class="sxs-lookup"><span data-stu-id="0c68d-176">API Calls Using DllImport</span></span>  
 <span data-ttu-id="0c68d-177">`DllImport`屬性提供第二個方法呼叫 Dll 中的函式，而不需要型別程式庫。</span><span class="sxs-lookup"><span data-stu-id="0c68d-177">The `DllImport` attribute provides a second way to call functions in DLLs without type libraries.</span></span> <span data-ttu-id="0c68d-178">`DllImport` 大致上相當於使用`Declare`陳述式，但是提供更充分掌控函式呼叫的方式。</span><span class="sxs-lookup"><span data-stu-id="0c68d-178">`DllImport` is roughly equivalent to using a `Declare` statement but provides more control over how functions are called.</span></span>  
  
 <span data-ttu-id="0c68d-179">您可以使用`DllImport`與大部分 Windows 應用程式開發介面呼叫，只要呼叫是指共用 (有時稱為*靜態*) 方法。</span><span class="sxs-lookup"><span data-stu-id="0c68d-179">You can use `DllImport` with most Windows API calls as long as the call refers to a shared (sometimes called *static*) method.</span></span> <span data-ttu-id="0c68d-180">您無法使用需要的類別執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="0c68d-180">You cannot use methods that require an instance of a class.</span></span> <span data-ttu-id="0c68d-181">不同於`Declare`陳述式，`DllImport`呼叫不能使用`MarshalAs`屬性。</span><span class="sxs-lookup"><span data-stu-id="0c68d-181">Unlike `Declare` statements, `DllImport` calls cannot use the `MarshalAs` attribute.</span></span>  
  
#### <a name="to-call-a-windows-api-using-the-dllimport-attribute"></a><span data-ttu-id="0c68d-182">若要呼叫 Windows API 使用 DllImport 屬性</span><span class="sxs-lookup"><span data-stu-id="0c68d-182">To call a Windows API using the DllImport attribute</span></span>  
  
1.  <span data-ttu-id="0c68d-183">開啟新的 Windows 應用程式專案，依序按一下**新增**上**檔案**] 功能表，然後按一下 [**專案**。</span><span class="sxs-lookup"><span data-stu-id="0c68d-183">Open a new Windows Application project by clicking **New** on the **File** menu, and then clicking **Project**.</span></span> <span data-ttu-id="0c68d-184">[ **新增專案** ] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="0c68d-184">The **New Project** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="0c68d-185">選取**Windows 應用程式**從 Visual Basic 專案範本的清單。</span><span class="sxs-lookup"><span data-stu-id="0c68d-185">Select **Windows Application** from the list of Visual Basic project templates.</span></span> <span data-ttu-id="0c68d-186">新的專案隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="0c68d-186">The new project is displayed.</span></span>  
  
3.  <span data-ttu-id="0c68d-187">將名為按鈕加入`Button2`的啟動表單。</span><span class="sxs-lookup"><span data-stu-id="0c68d-187">Add a button named `Button2` to the startup form.</span></span>  
  
4.  <span data-ttu-id="0c68d-188">按兩下`Button2`開啟表單的程式碼檢視。</span><span class="sxs-lookup"><span data-stu-id="0c68d-188">Double-click `Button2` to open the code view for the form.</span></span>  
  
5.  <span data-ttu-id="0c68d-189">若要簡化存取`DllImport`，新增`Imports`陳述式來啟動表單類別的程式碼的頂端：</span><span class="sxs-lookup"><span data-stu-id="0c68d-189">To simplify access to `DllImport`, add an `Imports` statement to the top of the code for the startup form class:</span></span>  
  
     [!code-vb[VbVbalrInterop#13](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_4.vb)]  
  
6.  <span data-ttu-id="0c68d-190">宣告空白的函式前面`End Class`表單中，而且名稱函式的陳述式`MoveFile`。</span><span class="sxs-lookup"><span data-stu-id="0c68d-190">Declare an empty function preceding the `End Class` statement for the form, and name the function `MoveFile`.</span></span>  
  
7.  <span data-ttu-id="0c68d-191">套用`Public`和`Shared`修飾詞的函式宣告和設定參數，如`MoveFile`根據 Windows API 函式使用的引數：</span><span class="sxs-lookup"><span data-stu-id="0c68d-191">Apply the `Public` and `Shared` modifiers to the function declaration and set parameters for `MoveFile` based on the arguments the Windows API function uses:</span></span>  
  
     [!code-vb[VbVbalrInterop#16](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_6.vb)]  
  
     <span data-ttu-id="0c68d-192">您的函式可以具有任何有效的程序名稱;`DllImport`屬性在 DLL 中指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="0c68d-192">Your function can have any valid procedure name; the `DllImport` attribute specifies the name in the DLL.</span></span> <span data-ttu-id="0c68d-193">它也會處理互通性封送處理參數和傳回值，因此您可以選擇 Visual Studio 資料類型類似的資料類型的應用程式開發介面使用。</span><span class="sxs-lookup"><span data-stu-id="0c68d-193">It also handles interoperability marshaling for the parameters and return values, so you can choose Visual Studio data types that are similar to the data types the API uses.</span></span>  
  
8.  <span data-ttu-id="0c68d-194">套用`DllImport`屬性為空白的函式。</span><span class="sxs-lookup"><span data-stu-id="0c68d-194">Apply the `DllImport` attribute to the empty function.</span></span> <span data-ttu-id="0c68d-195">第一個參數是包含您要呼叫的函式的 dll 位置與名稱。</span><span class="sxs-lookup"><span data-stu-id="0c68d-195">The first parameter is the name and location of the DLL containing the function you are calling.</span></span> <span data-ttu-id="0c68d-196">您不需要指定位於 Windows 系統目錄中檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="0c68d-196">You do not need to specify the path for files located in the Windows system directories.</span></span> <span data-ttu-id="0c68d-197">第二個參數是在 Windows API 中指定的函式名稱的具名引數。</span><span class="sxs-lookup"><span data-stu-id="0c68d-197">The second parameter is a named argument that specifies the name of the function in the Windows API.</span></span> <span data-ttu-id="0c68d-198">在此範例中，`DllImport`屬性會強制執行呼叫`MoveFile`轉送至`MoveFileW`KERNEL32 中。DLL。</span><span class="sxs-lookup"><span data-stu-id="0c68d-198">In this example, the `DllImport` attribute forces calls to `MoveFile` to be forwarded to `MoveFileW` in KERNEL32.DLL.</span></span> <span data-ttu-id="0c68d-199">`MoveFileW`方法會複製檔案的路徑中`src`路徑`dst`。</span><span class="sxs-lookup"><span data-stu-id="0c68d-199">The `MoveFileW` method copies a file from the path `src` to the path `dst`.</span></span>  
  
     [!code-vb[VbVbalrInterop#17](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_7.vb)]  
  
9. <span data-ttu-id="0c68d-200">將程式碼加入`Button2_Click`事件處理常式呼叫的函式：</span><span class="sxs-lookup"><span data-stu-id="0c68d-200">Add code to the `Button2_Click` event handler to call the function:</span></span>  
  
     [!code-vb[VbVbalrInterop#18](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_8.vb)]  
  
10. <span data-ttu-id="0c68d-201">建立名為 Test.txt 的檔案，並將它放在您的硬碟上 C:\Tmp 目錄中。</span><span class="sxs-lookup"><span data-stu-id="0c68d-201">Create a file named Test.txt and place it in the C:\Tmp directory on your hard drive.</span></span> <span data-ttu-id="0c68d-202">如有必要，請建立 Tmp 目錄。</span><span class="sxs-lookup"><span data-stu-id="0c68d-202">Create the Tmp directory if necessary.</span></span>  
  
11. <span data-ttu-id="0c68d-203">請按 F5 啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="0c68d-203">Press F5 to start the application.</span></span> <span data-ttu-id="0c68d-204">主要表單隨即出現。</span><span class="sxs-lookup"><span data-stu-id="0c68d-204">The main form appears.</span></span>  
  
12. <span data-ttu-id="0c68d-205">按一下**Button2**。</span><span class="sxs-lookup"><span data-stu-id="0c68d-205">Click **Button2**.</span></span> <span data-ttu-id="0c68d-206">如果可以移動檔案，會顯示 「 已成功移動檔案 」 訊息。</span><span class="sxs-lookup"><span data-stu-id="0c68d-206">The message "The file was moved successfully" is displayed if the file can be moved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c68d-207">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c68d-207">See Also</span></span>  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="0c68d-208">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="0c68d-208">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [<span data-ttu-id="0c68d-209">Auto</span><span class="sxs-lookup"><span data-stu-id="0c68d-209">Auto</span></span>](../../../visual-basic/language-reference/modifiers/auto.md)  
 [<span data-ttu-id="0c68d-210">Alias</span><span class="sxs-lookup"><span data-stu-id="0c68d-210">Alias</span></span>](../../../visual-basic/language-reference/statements/alias-clause.md)  
 [<span data-ttu-id="0c68d-211">COM Interop</span><span class="sxs-lookup"><span data-stu-id="0c68d-211">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)  
 [<span data-ttu-id="0c68d-212">在 Managed 程式碼中建立原型</span><span class="sxs-lookup"><span data-stu-id="0c68d-212">Creating Prototypes in Managed Code</span></span>](../../../framework/interop/creating-prototypes-in-managed-code.md)  
 [<span data-ttu-id="0c68d-213">做為回呼方法，委派封送處理</span><span class="sxs-lookup"><span data-stu-id="0c68d-213">Marshaling a Delegate as a Callback Method</span></span>](../../../framework/interop/marshaling-a-delegate-as-a-callback-method.md)
