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
ms.sourcegitcommit: 869b5832b667915ac4a5dd8c86b1109ed26b6c08
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2018
ms.locfileid: "39332856"
---
# <a name="walkthrough-calling-windows-apis-visual-basic"></a><span data-ttu-id="1bfbc-102">逐步解說：呼叫 Windows API (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1bfbc-102">Walkthrough: Calling Windows APIs (Visual Basic)</span></span>
<span data-ttu-id="1bfbc-103">Windows Api 是屬於 Windows 作業系統的動態連結程式庫 (Dll)。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-103">Windows APIs are dynamic-link libraries (DLLs) that are part of the Windows operating system.</span></span> <span data-ttu-id="1bfbc-104">您可以使用它們來執行工作時很難撰寫您自己的對等的程序。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-104">You use them to perform tasks when it is difficult to write equivalent procedures of your own.</span></span> <span data-ttu-id="1bfbc-105">比方說，Windows 會提供名為函式`FlashWindowEx`，可讓您的應用程式的標題列淺色與深色陰影之間。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-105">For example, Windows provides a function named `FlashWindowEx` that lets you make the title bar for an application alternate between light and dark shades.</span></span>  
  
 <span data-ttu-id="1bfbc-106">在您的程式碼中使用 Windows Api 的優點是，他們就可以節省開發時間，因為它們包含數十個有用的功能，已撰寫並可立即使用。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-106">The advantage of using Windows APIs in your code is that they can save development time because they contain dozens of useful functions that are already written and waiting to be used.</span></span> <span data-ttu-id="1bfbc-107">缺點是 Windows Api 很難進行運作和十足，發生錯誤時。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-107">The disadvantage is that Windows APIs can be difficult to work with and unforgiving when things go wrong.</span></span>  
  
 <span data-ttu-id="1bfbc-108">Windows Api 就是一個特殊種類的互通性。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-108">Windows APIs represent a special category of interoperability.</span></span> <span data-ttu-id="1bfbc-109">Windows Api 無法使用 managed 程式碼，並沒有內建型別程式庫，並使用不同於 Visual Studio 搭配使用的資料類型。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-109">Windows APIs do not use managed code, do not have built-in type libraries, and use data types that are different than those used with Visual Studio.</span></span> <span data-ttu-id="1bfbc-110">由於這些差異，以及因為 Windows Api 不是 COM 物件，與 Windows Api 的互通性和[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]必須利用平台叫用，或 PInvoke。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-110">Because of these differences, and because Windows APIs are not COM objects, interoperability with Windows APIs and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] is performed using platform invoke, or PInvoke.</span></span> <span data-ttu-id="1bfbc-111">平台叫用是一項服務，可讓 managed 程式碼呼叫 unmanaged 的 Dll 中實作的函式。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-111">Platform invoke is a service that enables managed code to call unmanaged functions implemented in DLLs.</span></span> <span data-ttu-id="1bfbc-112">如需詳細資訊，請參閱 <<c0> [ 使用 Unmanaged DLL 函式](../../../framework/interop/consuming-unmanaged-dll-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-112">For more information, see [Consuming Unmanaged DLL Functions](../../../framework/interop/consuming-unmanaged-dll-functions.md).</span></span> <span data-ttu-id="1bfbc-113">您也可以使用 Visual Basic 中使用 PInvoke`Declare`陳述式，或套用`DllImport`屬性設定為空的程序。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-113">You can use PInvoke in Visual Basic by using either the `Declare` statement or applying the `DllImport` attribute to an empty procedure.</span></span>  
  
 <span data-ttu-id="1bfbc-114">Windows API 呼叫是 Visual Basic 程式在過去，很重要的一部分，但很少會需要使用 Visual Basic.NET。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-114">Windows API calls were an important part of Visual Basic programming in the past, but are seldom necessary with Visual Basic .NET.</span></span> <span data-ttu-id="1bfbc-115">可能的話，您應該使用從 managed 程式碼[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]來執行工作，而不是 Windows API 呼叫。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-115">Whenever possible, you should use managed code from the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] to perform tasks, instead of Windows API calls.</span></span> <span data-ttu-id="1bfbc-116">本逐步解說提供在使用這種情況下的資訊是必要的 Windows Api。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-116">This walkthrough provides information for those situations in which using Windows APIs is necessary.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="api-calls-using-declare"></a><span data-ttu-id="1bfbc-117">API 呼叫使用宣告</span><span class="sxs-lookup"><span data-stu-id="1bfbc-117">API Calls Using Declare</span></span>  
 <span data-ttu-id="1bfbc-118">呼叫 Windows Api 的最常見方式是使用`Declare`陳述式。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-118">The most common way to call Windows APIs is by using the `Declare` statement.</span></span>  
  
#### <a name="to-declare-a-dll-procedure"></a><span data-ttu-id="1bfbc-119">若要宣告的 DLL 程序</span><span class="sxs-lookup"><span data-stu-id="1bfbc-119">To declare a DLL procedure</span></span>  
  
1.  <span data-ttu-id="1bfbc-120">決定您想要呼叫的函式加上引數，引數類型的名稱，並傳回值，以及名稱與 DLL 包含它的位置。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-120">Determine the name of the function you want to call, plus its arguments, argument types, and return value, as well as the name and location of the DLL that contains it.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1bfbc-121">如需 Windows Api 的完整資訊，請參閱平台 SDK Windows API 中的 Win32 SDK 文件。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-121">For complete information about the Windows APIs, see the Win32 SDK documentation in the Platform SDK Windows API.</span></span> <span data-ttu-id="1bfbc-122">如需有關使用 Windows Api 的常數的詳細資訊，請檢查等平台 SDK 隨附的 Windows.h 的標頭檔。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-122">For more information about the constants that Windows APIs use, examine the header files such as Windows.h included with the Platform SDK.</span></span>  
  
2.  <span data-ttu-id="1bfbc-123">開啟新的 Windows 應用程式專案，依序按一下**的新**上**檔案**功能表，然後按一下**專案**。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-123">Open a new Windows Application project by clicking **New** on the **File** menu, and then clicking **Project**.</span></span> <span data-ttu-id="1bfbc-124">[ **新增專案** ] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-124">The **New Project** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="1bfbc-125">選取  **Windows 應用程式**從 Visual Basic 專案範本的清單。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-125">Select **Windows Application** from the list of Visual Basic project templates.</span></span> <span data-ttu-id="1bfbc-126">新的專案會顯示。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-126">The new project is displayed.</span></span>  
  
4.  <span data-ttu-id="1bfbc-127">新增下列`Declare`函式至類別或您要使用 DLL 的模組：</span><span class="sxs-lookup"><span data-stu-id="1bfbc-127">Add the following `Declare` function either to the class or module in which you want to use the DLL:</span></span>  
  
     [!code-vb[VbVbalrInterop#9](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_1.vb)]  
  
### <a name="parts-of-the-declare-statement"></a><span data-ttu-id="1bfbc-128">組件的 Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="1bfbc-128">Parts of the Declare Statement</span></span>  
 <span data-ttu-id="1bfbc-129">`Declare`陳述式包含下列項目。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-129">The `Declare` statement includes the following elements.</span></span>  
  
#### <a name="auto-modifier"></a><span data-ttu-id="1bfbc-130">Auto 修飾詞</span><span class="sxs-lookup"><span data-stu-id="1bfbc-130">Auto modifier</span></span>  
 <span data-ttu-id="1bfbc-131">`Auto`修飾詞會指示執行階段將根據根據通用語言執行階段規則 （或如果指定的別名名稱） 的方法名稱的字串轉換。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-131">The `Auto` modifier instructs the runtime to convert the string based on the method name according to common language runtime rules (or alias name if specified).</span></span>  
  
#### <a name="lib-and-alias-keywords"></a><span data-ttu-id="1bfbc-132">Lib 和別名的關鍵字</span><span class="sxs-lookup"><span data-stu-id="1bfbc-132">Lib and Alias keywords</span></span>  
 <span data-ttu-id="1bfbc-133">後面的名`Function`關鍵字是程式用來存取匯入的函式的名稱。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-133">The name following the `Function` keyword is the name your program uses to access the imported function.</span></span> <span data-ttu-id="1bfbc-134">它可以是您呼叫的函式的實際名稱相同，或者您可以使用任何有效的程序名稱，然後採用`Alias`關鍵字來指定您要呼叫的函式的實際名稱。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-134">It can be the same as the real name of the function you are calling, or you can use any valid procedure name and then employ the `Alias` keyword to specify the real name of the function you are calling.</span></span>  
  
 <span data-ttu-id="1bfbc-135">指定`Lib`關鍵字，後面的名稱和包含您要呼叫的函式的 DLL 位置。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-135">Specify the `Lib` keyword, followed by the name and location of the DLL that contains the function you are calling.</span></span> <span data-ttu-id="1bfbc-136">您不需要指定位於 Windows 系統目錄中檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-136">You do not need to specify the path for files located in the Windows system directories.</span></span>  
  
 <span data-ttu-id="1bfbc-137">使用`Alias`關鍵字，如果您呼叫的函式名稱不是有效的 Visual Basic 程序名稱，或您的應用程式中其他項目的名稱相衝突。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-137">Use the `Alias` keyword if the name of the function you are calling is not a valid Visual Basic procedure name, or conflicts with the name of other items in your application.</span></span> <span data-ttu-id="1bfbc-138">`Alias` 表示正在呼叫函式，則為 true 的名稱。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-138">`Alias` indicates the true name of the function being called.</span></span>  
  
#### <a name="argument-and-data-type-declarations"></a><span data-ttu-id="1bfbc-139">引數和資料型別宣告</span><span class="sxs-lookup"><span data-stu-id="1bfbc-139">Argument and Data Type Declarations</span></span>  
 <span data-ttu-id="1bfbc-140">宣告引數和其資料類型。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-140">Declare the arguments and their data types.</span></span> <span data-ttu-id="1bfbc-141">這個部分可能項挑戰，因為 Windows 會使用的資料類型不會對應至 Visual Studio 的資料型別。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-141">This part can be challenging because the data types that Windows uses do not correspond to Visual Studio data types.</span></span> <span data-ttu-id="1bfbc-142">Visual Basic 會為您許多工作，藉由將引數轉換成相容的資料類型，這個程序稱為*封送處理*。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-142">Visual Basic does a lot of the work for you by converting arguments to compatible data types, a process called *marshaling*.</span></span> <span data-ttu-id="1bfbc-143">您可以明確地控制如何引數會封送處理使用<xref:System.Runtime.InteropServices.MarshalAsAttribute>屬性中定義<xref:System.Runtime.InteropServices>命名空間。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-143">You can explicitly control how arguments are marshaled by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute defined in the <xref:System.Runtime.InteropServices> namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1bfbc-144">舊版的 Visual Basic 可讓您在宣告參數`As Any`，這表示該資料的任何資料型別可用。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-144">Previous versions of Visual Basic allowed you to declare parameters `As Any`, meaning that data of any data type could be used.</span></span> <span data-ttu-id="1bfbc-145">Visual Basic 會要求您使用特定資料類型，所有`Declare`陳述式。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-145">Visual Basic requires that you use a specific data type for all `Declare` statements.</span></span>  
  
#### <a name="windows-api-constants"></a><span data-ttu-id="1bfbc-146">Windows API 的常數</span><span class="sxs-lookup"><span data-stu-id="1bfbc-146">Windows API Constants</span></span>  
 <span data-ttu-id="1bfbc-147">某些引數為常數的組合。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-147">Some arguments are combinations of constants.</span></span> <span data-ttu-id="1bfbc-148">例如，`MessageBox`本逐步解說中的 API 會接受整數引數呼叫`Typ`，控制訊息方塊的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-148">For example, the `MessageBox` API shown in this walkthrough accepts an integer argument called `Typ` that controls how the message box is displayed.</span></span> <span data-ttu-id="1bfbc-149">您可以藉由檢查來判斷這些常數的數值`#define`WinUser.h 檔案中的陳述式。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-149">You can determine the numeric value of these constants by examining the `#define` statements in the file WinUser.h.</span></span> <span data-ttu-id="1bfbc-150">因此您可能想要使用的計算機來予以新增，然後將轉換成十進位數字的值通常會顯示以十六進位、。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-150">The numeric values are generally shown in hexadecimal, so you may want to use a calculator to add them and convert to decimal.</span></span> <span data-ttu-id="1bfbc-151">例如，如果您想要結合驚嘆號樣式常數`MB_ICONEXCLAMATION`0x00000030 和 是/無樣式`MB_YESNO`0x00000004，您可以將數字相加，並取得 0x00000034 或 52 結果的十進位。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-151">For example, if you want to combine the constants for the exclamation style `MB_ICONEXCLAMATION` 0x00000030 and the Yes/No style `MB_YESNO` 0x00000004, you can add the numbers and get a result of 0x00000034, or 52 decimal.</span></span> <span data-ttu-id="1bfbc-152">雖然您可以直接使用十進位的結果，最好是將這些值宣告為應用程式中的常數，並將它們結合使用`Or`運算子。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-152">Although you can use the decimal result directly, it is better to declare these values as constants in your application and combine them using the `Or` operator.</span></span>  
  
###### <a name="to-declare-constants-for-windows-api-calls"></a><span data-ttu-id="1bfbc-153">若要宣告常數的 Windows API 呼叫</span><span class="sxs-lookup"><span data-stu-id="1bfbc-153">To declare constants for Windows API calls</span></span>  
  
1.  <span data-ttu-id="1bfbc-154">您要呼叫 Windows 函式，請參閱文件。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-154">Consult the documentation for the Windows function you are calling.</span></span> <span data-ttu-id="1bfbc-155">決定使用的常數名稱以及包含這些常數的數值的.h 檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-155">Determine the name of the constants it uses and the name of the .h file that contains the numeric values for these constants.</span></span>  
  
2.  <span data-ttu-id="1bfbc-156">若要檢視標頭 (.h) 檔案的內容中使用文字編輯器，例如 [記事本]，並找出您正在使用的常數相關聯的值。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-156">Use a text editor, such as Notepad, to view the contents of the header (.h) file, and find the values associated with the constants you are using.</span></span> <span data-ttu-id="1bfbc-157">例如， `MessageBox` API 會使用常數`MB_ICONQUESTION`顯示訊息方塊中的問號。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-157">For example, the `MessageBox` API uses the constant `MB_ICONQUESTION` to show a question mark in the message box.</span></span> <span data-ttu-id="1bfbc-158">定義`MB_ICONQUESTION`WinUser.h 中，而且會出現，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1bfbc-158">The definition for `MB_ICONQUESTION` is in WinUser.h and appears as follows:</span></span>  
  
     `#define MB_ICONQUESTION             0x00000020L`  
  
3.  <span data-ttu-id="1bfbc-159">新增對等項目`Const`至您的類別或模組，讓您的應用程式可使用這些常數的陳述式。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-159">Add equivalent `Const` statements to your class or module to make these constants available to your application.</span></span> <span data-ttu-id="1bfbc-160">例如: </span><span class="sxs-lookup"><span data-stu-id="1bfbc-160">For example:</span></span>  
  
     [!code-vb[VbVbalrInterop#11](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_2.vb)]  
  
###### <a name="to-call-the-dll-procedure"></a><span data-ttu-id="1bfbc-161">若要呼叫的 DLL 程序</span><span class="sxs-lookup"><span data-stu-id="1bfbc-161">To call the DLL procedure</span></span>  
  
1.  <span data-ttu-id="1bfbc-162">新增名為按鈕`Button1`啟動以您的專案，然後按兩下以檢視其程式碼。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-162">Add a button named `Button1` to the startup form for your project, and then double-click it to view its code.</span></span> <span data-ttu-id="1bfbc-163">會顯示為按鈕的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-163">The event handler for the button is displayed.</span></span>  
  
2.  <span data-ttu-id="1bfbc-164">將程式碼加入`Click`加入呼叫程序，並提供適當的引數的按鈕事件處理常式：</span><span class="sxs-lookup"><span data-stu-id="1bfbc-164">Add code to the `Click` event handler for the button you added, to call the procedure and provide the appropriate arguments:</span></span>  
  
     [!code-vb[VbVbalrInterop#12](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_3.vb)]  
  
3.  <span data-ttu-id="1bfbc-165">按 F5 執行專案。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-165">Run the project by pressing F5.</span></span> <span data-ttu-id="1bfbc-166">訊息方塊會顯示這兩 **[是]** 並**No**回應按鈕。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-166">The message box is displayed with both **Yes** and **No** response buttons.</span></span> <span data-ttu-id="1bfbc-167">按一下其中一個。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-167">Click either one.</span></span>  
  
#### <a name="data-marshaling"></a><span data-ttu-id="1bfbc-168">封送處理的資料</span><span class="sxs-lookup"><span data-stu-id="1bfbc-168">Data Marshaling</span></span>  
 <span data-ttu-id="1bfbc-169">Visual Basic 會自動轉換參數和 Windows API 呼叫的傳回值的資料類型，但您可以使用`MarshalAs`屬性來明確地指定 API 的預期的 unmanaged 的資料類型。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-169">Visual Basic automatically converts the data types of parameters and return values for Windows API calls, but you can use the `MarshalAs` attribute to explicitly specify unmanaged data types that an API expects.</span></span> <span data-ttu-id="1bfbc-170">如需有關 interop 封送處理的詳細資訊，請參閱[Interop 封送處理](../../../framework/interop/interop-marshaling.md)。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-170">For more information about interop marshaling, see [Interop Marshaling](../../../framework/interop/interop-marshaling.md).</span></span>  
  
###### <a name="to-use-declare-and-marshalas-in-an-api-call"></a><span data-ttu-id="1bfbc-171">若要使用 Declare 與 MarshalAs API 呼叫</span><span class="sxs-lookup"><span data-stu-id="1bfbc-171">To use Declare and MarshalAs in an API call</span></span>  
  
1.  <span data-ttu-id="1bfbc-172">決定您想要呼叫，再加上其引數，資料類型的函式的名稱，並傳回值。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-172">Determine the name of the function you want to call, plus its arguments, data types, and return value.</span></span>  
  
2.  <span data-ttu-id="1bfbc-173">若要簡化存取權`MarshalAs`屬性，請將`Imports`陳述式的類別或模組，如下列範例所示的程式碼：</span><span class="sxs-lookup"><span data-stu-id="1bfbc-173">To simplify access to the `MarshalAs` attribute, add an `Imports` statement to the top of the code for the class or module, as in the following example:</span></span>  
  
     [!code-vb[VbVbalrInterop#13](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_4.vb)]  
  
3.  <span data-ttu-id="1bfbc-174">將函式原型匯入的函式新增至類別或模組，您使用，並套用`MarshalAs`屬性至參數或傳回值。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-174">Add a function prototype for the imported function to the class or module you are using, and apply the `MarshalAs` attribute to the parameters or return value.</span></span> <span data-ttu-id="1bfbc-175">在下列範例中，預期類型的 API 呼叫`void*`封送處理為`AsAny`:</span><span class="sxs-lookup"><span data-stu-id="1bfbc-175">In the following example, an API call that expects the type `void*` is marshaled as `AsAny`:</span></span>  
  
     [!code-vb[VbVbalrInterop#14](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_5.vb)]  
  
## <a name="api-calls-using-dllimport"></a><span data-ttu-id="1bfbc-176">API 呼叫使用 DllImport</span><span class="sxs-lookup"><span data-stu-id="1bfbc-176">API Calls Using DllImport</span></span>  
 <span data-ttu-id="1bfbc-177">`DllImport`屬性會提供 Dll 中呼叫函式，而不需要型別程式庫的第二種方式。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-177">The `DllImport` attribute provides a second way to call functions in DLLs without type libraries.</span></span> <span data-ttu-id="1bfbc-178">`DllImport` 大致上相當於使用`Declare`陳述式但可提供更充分掌控如何呼叫的函式。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-178">`DllImport` is roughly equivalent to using a `Declare` statement but provides more control over how functions are called.</span></span>  
  
 <span data-ttu-id="1bfbc-179">您可以使用`DllImport`大部分的 Windows api 呼叫，只要呼叫是指共用 (有時也稱為*靜態*) 方法。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-179">You can use `DllImport` with most Windows API calls as long as the call refers to a shared (sometimes called *static*) method.</span></span> <span data-ttu-id="1bfbc-180">您無法使用需要類別的執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-180">You cannot use methods that require an instance of a class.</span></span> <span data-ttu-id="1bfbc-181">不同於`Declare`陳述式，`DllImport`呼叫不能使用`MarshalAs`屬性。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-181">Unlike `Declare` statements, `DllImport` calls cannot use the `MarshalAs` attribute.</span></span>  
  
#### <a name="to-call-a-windows-api-using-the-dllimport-attribute"></a><span data-ttu-id="1bfbc-182">若要呼叫 Windows API 使用 DllImport 屬性</span><span class="sxs-lookup"><span data-stu-id="1bfbc-182">To call a Windows API using the DllImport attribute</span></span>  
  
1.  <span data-ttu-id="1bfbc-183">開啟新的 Windows 應用程式專案，依序按一下**的新**上**檔案**功能表，然後按一下**專案**。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-183">Open a new Windows Application project by clicking **New** on the **File** menu, and then clicking **Project**.</span></span> <span data-ttu-id="1bfbc-184">[ **新增專案** ] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-184">The **New Project** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="1bfbc-185">選取  **Windows 應用程式**從 Visual Basic 專案範本的清單。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-185">Select **Windows Application** from the list of Visual Basic project templates.</span></span> <span data-ttu-id="1bfbc-186">新的專案會顯示。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-186">The new project is displayed.</span></span>  
  
3.  <span data-ttu-id="1bfbc-187">新增名為按鈕`Button2`的啟動表單。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-187">Add a button named `Button2` to the startup form.</span></span>  
  
4.  <span data-ttu-id="1bfbc-188">按兩下`Button2`開啟表單的程式碼檢視。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-188">Double-click `Button2` to open the code view for the form.</span></span>  
  
5.  <span data-ttu-id="1bfbc-189">若要簡化存取權`DllImport`，新增`Imports`陳述式來啟動表單類別的程式碼頂端：</span><span class="sxs-lookup"><span data-stu-id="1bfbc-189">To simplify access to `DllImport`, add an `Imports` statement to the top of the code for the startup form class:</span></span>  
  
     [!code-vb[VbVbalrInterop#13](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_4.vb)]  
  
6.  <span data-ttu-id="1bfbc-190">宣告空函式前面`End Class`表單，和名稱的函式的陳述式`MoveFile`。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-190">Declare an empty function preceding the `End Class` statement for the form, and name the function `MoveFile`.</span></span>  
  
7.  <span data-ttu-id="1bfbc-191">適用於`Public`並`Shared`的函式宣告和設定參數的修飾詞`MoveFile`根據 Windows API 函式會使用的引數：</span><span class="sxs-lookup"><span data-stu-id="1bfbc-191">Apply the `Public` and `Shared` modifiers to the function declaration and set parameters for `MoveFile` based on the arguments the Windows API function uses:</span></span>  
  
     [!code-vb[VbVbalrInterop#16](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_6.vb)]  
  
     <span data-ttu-id="1bfbc-192">您的函式可以使用任何有效的程序名稱;`DllImport`屬性會指定在 DLL 中的名稱。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-192">Your function can have any valid procedure name; the `DllImport` attribute specifies the name in the DLL.</span></span> <span data-ttu-id="1bfbc-193">它也會處理參數封送處理的互通性和 API 所使用的傳回值，因此您可以選擇 Visual Studio 的資料類型，它們類似於的資料類型。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-193">It also handles interoperability marshaling for the parameters and return values, so you can choose Visual Studio data types that are similar to the data types the API uses.</span></span>  
  
8.  <span data-ttu-id="1bfbc-194">套用`DllImport`屬性為空白的函式。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-194">Apply the `DllImport` attribute to the empty function.</span></span> <span data-ttu-id="1bfbc-195">第一個參數是包含您要呼叫的函式的 dll 的位置與名稱。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-195">The first parameter is the name and location of the DLL containing the function you are calling.</span></span> <span data-ttu-id="1bfbc-196">您不需要指定位於 Windows 系統目錄中檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-196">You do not need to specify the path for files located in the Windows system directories.</span></span> <span data-ttu-id="1bfbc-197">第二個參數是在 Windows API 中指定的函式名稱的具名引數。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-197">The second parameter is a named argument that specifies the name of the function in the Windows API.</span></span> <span data-ttu-id="1bfbc-198">在此範例中，`DllImport`屬性會強制執行呼叫`MoveFile`轉送至`MoveFileW`KERNEL32 中。DLL。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-198">In this example, the `DllImport` attribute forces calls to `MoveFile` to be forwarded to `MoveFileW` in KERNEL32.DLL.</span></span> <span data-ttu-id="1bfbc-199">`MoveFileW`方法會將檔案複製從路徑`src`路徑`dst`。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-199">The `MoveFileW` method copies a file from the path `src` to the path `dst`.</span></span>  
  
     [!code-vb[VbVbalrInterop#17](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_7.vb)]  
  
9. <span data-ttu-id="1bfbc-200">將程式碼加入`Button2_Click`事件處理常式呼叫的函式：</span><span class="sxs-lookup"><span data-stu-id="1bfbc-200">Add code to the `Button2_Click` event handler to call the function:</span></span>  
  
     [!code-vb[VbVbalrInterop#18](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_8.vb)]  
  
10. <span data-ttu-id="1bfbc-201">建立名為 Test.txt 的檔案，並將它放在硬碟機 C:\Tmp 目錄中。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-201">Create a file named Test.txt and place it in the C:\Tmp directory on your hard drive.</span></span> <span data-ttu-id="1bfbc-202">如有必要，請建立 Tmp 目錄。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-202">Create the Tmp directory if necessary.</span></span>  
  
11. <span data-ttu-id="1bfbc-203">請按 F5 啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-203">Press F5 to start the application.</span></span> <span data-ttu-id="1bfbc-204">主要的表單隨即出現。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-204">The main form appears.</span></span>  
  
12. <span data-ttu-id="1bfbc-205">按一下  **Button2**。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-205">Click **Button2**.</span></span> <span data-ttu-id="1bfbc-206">如果可以移動檔案，則會顯示 「 已成功移動檔案 」 訊息。</span><span class="sxs-lookup"><span data-stu-id="1bfbc-206">The message "The file was moved successfully" is displayed if the file can be moved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bfbc-207">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1bfbc-207">See Also</span></span>  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="1bfbc-208">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="1bfbc-208">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [<span data-ttu-id="1bfbc-209">Auto</span><span class="sxs-lookup"><span data-stu-id="1bfbc-209">Auto</span></span>](../../../visual-basic/language-reference/modifiers/auto.md)  
 [<span data-ttu-id="1bfbc-210">Alias</span><span class="sxs-lookup"><span data-stu-id="1bfbc-210">Alias</span></span>](../../../visual-basic/language-reference/statements/alias-clause.md)  
 [<span data-ttu-id="1bfbc-211">COM Interop</span><span class="sxs-lookup"><span data-stu-id="1bfbc-211">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)  
 [<span data-ttu-id="1bfbc-212">在 Managed 程式碼中建立原型</span><span class="sxs-lookup"><span data-stu-id="1bfbc-212">Creating Prototypes in Managed Code</span></span>](../../../framework/interop/creating-prototypes-in-managed-code.md)  
 [<span data-ttu-id="1bfbc-213">做為回呼方法，委派封送處理</span><span class="sxs-lookup"><span data-stu-id="1bfbc-213">Marshaling a Delegate as a Callback Method</span></span>](../../../framework/interop/marshaling-a-delegate-as-a-callback-method.md)
