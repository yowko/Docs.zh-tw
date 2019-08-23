---
title: 逐步解說：呼叫 Windows Api (Visual Basic)
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
ms.openlocfilehash: 8e6d3e7f84c96d145a48daa27918cbb2cb3b61ac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958303"
---
# <a name="walkthrough-calling-windows-apis-visual-basic"></a><span data-ttu-id="093c9-102">逐步解說：呼叫 Windows Api (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="093c9-102">Walkthrough: Calling Windows APIs (Visual Basic)</span></span>
<span data-ttu-id="093c9-103">Windows Api 是動態連結程式庫 (Dll), 屬於 Windows 作業系統的一部分。</span><span class="sxs-lookup"><span data-stu-id="093c9-103">Windows APIs are dynamic-link libraries (DLLs) that are part of the Windows operating system.</span></span> <span data-ttu-id="093c9-104">當您很難以撰寫自己的對等程式時, 可以使用它們來執行工作。</span><span class="sxs-lookup"><span data-stu-id="093c9-104">You use them to perform tasks when it is difficult to write equivalent procedures of your own.</span></span> <span data-ttu-id="093c9-105">例如, Windows 提供名為`FlashWindowEx`的函式, 可讓您讓應用程式的標題列在淺色與深色之間交替。</span><span class="sxs-lookup"><span data-stu-id="093c9-105">For example, Windows provides a function named `FlashWindowEx` that lets you make the title bar for an application alternate between light and dark shades.</span></span>  
  
 <span data-ttu-id="093c9-106">在您的程式碼中使用 Windows Api 的優點是可以節省開發時間, 因為它們包含數十個已撰寫並等候使用的實用函式。</span><span class="sxs-lookup"><span data-stu-id="093c9-106">The advantage of using Windows APIs in your code is that they can save development time because they contain dozens of useful functions that are already written and waiting to be used.</span></span> <span data-ttu-id="093c9-107">缺點是, Windows Api 在發生錯誤時很容易使用和 unforgiving。</span><span class="sxs-lookup"><span data-stu-id="093c9-107">The disadvantage is that Windows APIs can be difficult to work with and unforgiving when things go wrong.</span></span>  
  
 <span data-ttu-id="093c9-108">Windows Api 代表一種特殊的互通性分類。</span><span class="sxs-lookup"><span data-stu-id="093c9-108">Windows APIs represent a special category of interoperability.</span></span> <span data-ttu-id="093c9-109">Windows Api 不會使用 managed 程式碼、沒有內建類型程式庫, 以及使用與 Visual Studio 搭配使用的資料類型。</span><span class="sxs-lookup"><span data-stu-id="093c9-109">Windows APIs do not use managed code, do not have built-in type libraries, and use data types that are different than those used with Visual Studio.</span></span> <span data-ttu-id="093c9-110">因為有這些差異, 而且因為 Windows Api 不是 COM 物件, 所以與 Windows Api 的互通性和 .NET Framework 是使用平台叫用或 PInvoke 來執行。</span><span class="sxs-lookup"><span data-stu-id="093c9-110">Because of these differences, and because Windows APIs are not COM objects, interoperability with Windows APIs and the .NET Framework is performed using platform invoke, or PInvoke.</span></span> <span data-ttu-id="093c9-111">平台叫用是一項服務, 可讓 managed 程式碼呼叫在 Dll 中實作用的非受控函式。</span><span class="sxs-lookup"><span data-stu-id="093c9-111">Platform invoke is a service that enables managed code to call unmanaged functions implemented in DLLs.</span></span> <span data-ttu-id="093c9-112">如需詳細資訊, 請參閱[使用非受控 DLL](../../../framework/interop/consuming-unmanaged-dll-functions.md)函式。</span><span class="sxs-lookup"><span data-stu-id="093c9-112">For more information, see [Consuming Unmanaged DLL Functions](../../../framework/interop/consuming-unmanaged-dll-functions.md).</span></span> <span data-ttu-id="093c9-113">您可以使用`Declare`語句, 或`DllImport`將屬性套用至空白程式, 以在 Visual Basic 中使用 PInvoke。</span><span class="sxs-lookup"><span data-stu-id="093c9-113">You can use PInvoke in Visual Basic by using either the `Declare` statement or applying the `DllImport` attribute to an empty procedure.</span></span>  
  
 <span data-ttu-id="093c9-114">Windows API 呼叫是過去 Visual Basic 程式設計中很重要的一環, 但 Visual Basic .NET 時很少需要。</span><span class="sxs-lookup"><span data-stu-id="093c9-114">Windows API calls were an important part of Visual Basic programming in the past, but are seldom necessary with Visual Basic .NET.</span></span> <span data-ttu-id="093c9-115">可能的話, 您應該使用 .NET Framework 的 managed 程式碼來執行工作, 而不是 Windows API 呼叫。</span><span class="sxs-lookup"><span data-stu-id="093c9-115">Whenever possible, you should use managed code from the .NET Framework to perform tasks, instead of Windows API calls.</span></span> <span data-ttu-id="093c9-116">本逐步解說會針對需要使用 Windows Api 的情況提供相關資訊。</span><span class="sxs-lookup"><span data-stu-id="093c9-116">This walkthrough provides information for those situations in which using Windows APIs is necessary.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="api-calls-using-declare"></a><span data-ttu-id="093c9-117">使用 Declare 的 API 呼叫</span><span class="sxs-lookup"><span data-stu-id="093c9-117">API Calls Using Declare</span></span>  
 <span data-ttu-id="093c9-118">呼叫 Windows api 最常見的方式是使用`Declare`語句。</span><span class="sxs-lookup"><span data-stu-id="093c9-118">The most common way to call Windows APIs is by using the `Declare` statement.</span></span>  
  
### <a name="to-declare-a-dll-procedure"></a><span data-ttu-id="093c9-119">若要宣告 DLL 程式</span><span class="sxs-lookup"><span data-stu-id="093c9-119">To declare a DLL procedure</span></span>  
  
1. <span data-ttu-id="093c9-120">決定您想要呼叫的函式名稱, 加上其引數、引數類型和傳回值, 以及包含它的 DLL 名稱和位置。</span><span class="sxs-lookup"><span data-stu-id="093c9-120">Determine the name of the function you want to call, plus its arguments, argument types, and return value, as well as the name and location of the DLL that contains it.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="093c9-121">如需 Windows Api 的完整資訊, 請參閱 Platform SDK Windows API 中的 Win32 SDK 檔。</span><span class="sxs-lookup"><span data-stu-id="093c9-121">For complete information about the Windows APIs, see the Win32 SDK documentation in the Platform SDK Windows API.</span></span> <span data-ttu-id="093c9-122">如需 Windows Api 所使用之常數的詳細資訊, 請檢查包含在 Platform SDK 中的標頭檔 (例如 Windows .h)。</span><span class="sxs-lookup"><span data-stu-id="093c9-122">For more information about the constants that Windows APIs use, examine the header files such as Windows.h included with the Platform SDK.</span></span>  
  
2. <span data-ttu-id="093c9-123">按一下 [檔案] 功能表上的 [**新增**],然後按一下 [**專案**], 以開啟新的 Windows 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="093c9-123">Open a new Windows Application project by clicking **New** on the **File** menu, and then clicking **Project**.</span></span> <span data-ttu-id="093c9-124">[ **新增專案** ] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="093c9-124">The **New Project** dialog box appears.</span></span>  
  
3. <span data-ttu-id="093c9-125">從 Visual Basic 專案範本清單中選取 [ **Windows 應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="093c9-125">Select **Windows Application** from the list of Visual Basic project templates.</span></span> <span data-ttu-id="093c9-126">隨即顯示新專案。</span><span class="sxs-lookup"><span data-stu-id="093c9-126">The new project is displayed.</span></span>  
  
4. <span data-ttu-id="093c9-127">將下列`Declare`函數新增至您要使用 DLL 的類別或模組:</span><span class="sxs-lookup"><span data-stu-id="093c9-127">Add the following `Declare` function either to the class or module in which you want to use the DLL:</span></span>  
  
     [!code-vb[VbVbalrInterop#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#9)]  
  
### <a name="parts-of-the-declare-statement"></a><span data-ttu-id="093c9-128">Declare 語句的部分</span><span class="sxs-lookup"><span data-stu-id="093c9-128">Parts of the Declare Statement</span></span>  
 <span data-ttu-id="093c9-129">`Declare`語句包含下列元素。</span><span class="sxs-lookup"><span data-stu-id="093c9-129">The `Declare` statement includes the following elements.</span></span>  
  
#### <a name="auto-modifier"></a><span data-ttu-id="093c9-130">Auto 修飾詞</span><span class="sxs-lookup"><span data-stu-id="093c9-130">Auto modifier</span></span>  
 <span data-ttu-id="093c9-131">`Auto`修飾詞會指示執行時間根據方法名稱, 依據通用語言執行時間規則 (如果有指定, 則為別名名稱) 來轉換字串。</span><span class="sxs-lookup"><span data-stu-id="093c9-131">The `Auto` modifier instructs the runtime to convert the string based on the method name according to common language runtime rules (or alias name if specified).</span></span>  
  
#### <a name="lib-and-alias-keywords"></a><span data-ttu-id="093c9-132">Lib 和 Alias 關鍵字</span><span class="sxs-lookup"><span data-stu-id="093c9-132">Lib and Alias keywords</span></span>  
 <span data-ttu-id="093c9-133">`Function`關鍵字後面的名稱是您的程式用來存取匯入函式的名稱。</span><span class="sxs-lookup"><span data-stu-id="093c9-133">The name following the `Function` keyword is the name your program uses to access the imported function.</span></span> <span data-ttu-id="093c9-134">它可以與您所呼叫之函式的實際名稱相同, 或者您可以使用任何有效的程式名稱, 然後採用`Alias`關鍵字來指定您要呼叫之函式的實際名稱。</span><span class="sxs-lookup"><span data-stu-id="093c9-134">It can be the same as the real name of the function you are calling, or you can use any valid procedure name and then employ the `Alias` keyword to specify the real name of the function you are calling.</span></span>  
  
 <span data-ttu-id="093c9-135">`Lib`指定關鍵字, 後面接著包含您要呼叫之函數的 DLL 名稱和位置。</span><span class="sxs-lookup"><span data-stu-id="093c9-135">Specify the `Lib` keyword, followed by the name and location of the DLL that contains the function you are calling.</span></span> <span data-ttu-id="093c9-136">您不需要指定位於 Windows 系統目錄中的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="093c9-136">You do not need to specify the path for files located in the Windows system directories.</span></span>  
  
 <span data-ttu-id="093c9-137">如果您呼叫的函式名稱不是有效的 Visual Basic 程式名稱, 或是與應用程式中其他專案的名稱衝突, 請使用關鍵字。`Alias`</span><span class="sxs-lookup"><span data-stu-id="093c9-137">Use the `Alias` keyword if the name of the function you are calling is not a valid Visual Basic procedure name, or conflicts with the name of other items in your application.</span></span> <span data-ttu-id="093c9-138">`Alias`表示所呼叫之函式的真正名稱。</span><span class="sxs-lookup"><span data-stu-id="093c9-138">`Alias` indicates the true name of the function being called.</span></span>  
  
#### <a name="argument-and-data-type-declarations"></a><span data-ttu-id="093c9-139">引數和資料類型宣告</span><span class="sxs-lookup"><span data-stu-id="093c9-139">Argument and Data Type Declarations</span></span>  
 <span data-ttu-id="093c9-140">宣告引數及其資料類型。</span><span class="sxs-lookup"><span data-stu-id="093c9-140">Declare the arguments and their data types.</span></span> <span data-ttu-id="093c9-141">這個部分可能相當困難, 因為 Windows 所使用的資料類型不會對應到 Visual Studio 的資料類型。</span><span class="sxs-lookup"><span data-stu-id="093c9-141">This part can be challenging because the data types that Windows uses do not correspond to Visual Studio data types.</span></span> <span data-ttu-id="093c9-142">Visual Basic 藉由將引數轉換成相容的資料類型 (稱為*封送*處理的進程), 為您執行許多工作。</span><span class="sxs-lookup"><span data-stu-id="093c9-142">Visual Basic does a lot of the work for you by converting arguments to compatible data types, a process called *marshaling*.</span></span> <span data-ttu-id="093c9-143">您可以使用<xref:System.Runtime.InteropServices.MarshalAsAttribute> <xref:System.Runtime.InteropServices>命名空間中定義的屬性, 明確控制引數的封送處理方式。</span><span class="sxs-lookup"><span data-stu-id="093c9-143">You can explicitly control how arguments are marshaled by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute defined in the <xref:System.Runtime.InteropServices> namespace.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="093c9-144">舊版的 Visual Basic 可讓您宣告參數`As Any`, 這表示可以使用任何資料類型的資料。</span><span class="sxs-lookup"><span data-stu-id="093c9-144">Previous versions of Visual Basic allowed you to declare parameters `As Any`, meaning that data of any data type could be used.</span></span> <span data-ttu-id="093c9-145">Visual Basic 要求您針對所有`Declare`語句使用特定的資料類型。</span><span class="sxs-lookup"><span data-stu-id="093c9-145">Visual Basic requires that you use a specific data type for all `Declare` statements.</span></span>  
  
#### <a name="windows-api-constants"></a><span data-ttu-id="093c9-146">Windows API 常數</span><span class="sxs-lookup"><span data-stu-id="093c9-146">Windows API Constants</span></span>  
 <span data-ttu-id="093c9-147">某些引數是常數的組合。</span><span class="sxs-lookup"><span data-stu-id="093c9-147">Some arguments are combinations of constants.</span></span> <span data-ttu-id="093c9-148">例如, 本逐步`MessageBox`解說中所顯示的 API 會接受名`Typ`為的整數引數, 以控制訊息框的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="093c9-148">For example, the `MessageBox` API shown in this walkthrough accepts an integer argument called `Typ` that controls how the message box is displayed.</span></span> <span data-ttu-id="093c9-149">您可以檢查 WinUser 檔案中的`#define`語句, 判斷這些常數的數值。</span><span class="sxs-lookup"><span data-stu-id="093c9-149">You can determine the numeric value of these constants by examining the `#define` statements in the file WinUser.h.</span></span> <span data-ttu-id="093c9-150">數值通常會以十六進位顯示, 因此您可能會想要使用計算機來新增它們並轉換成 decimal。</span><span class="sxs-lookup"><span data-stu-id="093c9-150">The numeric values are generally shown in hexadecimal, so you may want to use a calculator to add them and convert to decimal.</span></span> <span data-ttu-id="093c9-151">例如, 如果您想要結合驚嘆號樣式`MB_ICONEXCLAMATION` 0x00000030 和 Yes/No 樣式`MB_YESNO` 0x00000004 的常數, 您可以加入數位並取得0x00000034 的結果, 或52的 decimal。</span><span class="sxs-lookup"><span data-stu-id="093c9-151">For example, if you want to combine the constants for the exclamation style `MB_ICONEXCLAMATION` 0x00000030 and the Yes/No style `MB_YESNO` 0x00000004, you can add the numbers and get a result of 0x00000034, or 52 decimal.</span></span> <span data-ttu-id="093c9-152">雖然您可以直接使用十進位結果, 但最好是將這些值宣告為應用程式中的常數, 並使用`Or`運算子加以結合。</span><span class="sxs-lookup"><span data-stu-id="093c9-152">Although you can use the decimal result directly, it is better to declare these values as constants in your application and combine them using the `Or` operator.</span></span>  
  
##### <a name="to-declare-constants-for-windows-api-calls"></a><span data-ttu-id="093c9-153">若要宣告 Windows API 呼叫的常數</span><span class="sxs-lookup"><span data-stu-id="093c9-153">To declare constants for Windows API calls</span></span>  
  
1. <span data-ttu-id="093c9-154">請參閱檔, 以瞭解您所呼叫的 Windows 函式。</span><span class="sxs-lookup"><span data-stu-id="093c9-154">Consult the documentation for the Windows function you are calling.</span></span> <span data-ttu-id="093c9-155">判斷它所使用的常數名稱, 以及包含這些常數之數值的 .h 檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="093c9-155">Determine the name of the constants it uses and the name of the .h file that contains the numeric values for these constants.</span></span>  
  
2. <span data-ttu-id="093c9-156">使用文字編輯器 (例如 [記事本]) 來查看標頭 (.h) 檔案的內容, 並尋找與您所使用之常數相關聯的值。</span><span class="sxs-lookup"><span data-stu-id="093c9-156">Use a text editor, such as Notepad, to view the contents of the header (.h) file, and find the values associated with the constants you are using.</span></span> <span data-ttu-id="093c9-157">例如, `MessageBox` API 會使用常數`MB_ICONQUESTION` , 在訊息方塊中顯示問號。</span><span class="sxs-lookup"><span data-stu-id="093c9-157">For example, the `MessageBox` API uses the constant `MB_ICONQUESTION` to show a question mark in the message box.</span></span> <span data-ttu-id="093c9-158">的定義`MB_ICONQUESTION`位於 WinUser 中, 並顯示如下:</span><span class="sxs-lookup"><span data-stu-id="093c9-158">The definition for `MB_ICONQUESTION` is in WinUser.h and appears as follows:</span></span>  
  
     `#define MB_ICONQUESTION             0x00000020L`  
  
3. <span data-ttu-id="093c9-159">將對`Const`等語句加入至您的類別或模組, 讓這些常數可供您的應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="093c9-159">Add equivalent `Const` statements to your class or module to make these constants available to your application.</span></span> <span data-ttu-id="093c9-160">例如：</span><span class="sxs-lookup"><span data-stu-id="093c9-160">For example:</span></span>  
  
     [!code-vb[VbVbalrInterop#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#11)]  
  
###### <a name="to-call-the-dll-procedure"></a><span data-ttu-id="093c9-161">呼叫 DLL 程式</span><span class="sxs-lookup"><span data-stu-id="093c9-161">To call the DLL procedure</span></span>  
  
1. <span data-ttu-id="093c9-162">將名`Button1`為的按鈕新增至專案的啟動表單, 然後按兩下以查看其程式碼。</span><span class="sxs-lookup"><span data-stu-id="093c9-162">Add a button named `Button1` to the startup form for your project, and then double-click it to view its code.</span></span> <span data-ttu-id="093c9-163">隨即顯示按鈕的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="093c9-163">The event handler for the button is displayed.</span></span>  
  
2. <span data-ttu-id="093c9-164">將程式碼加入`Click`至您所加入按鈕的事件處理常式中, 以呼叫程式並提供適當的引數:</span><span class="sxs-lookup"><span data-stu-id="093c9-164">Add code to the `Click` event handler for the button you added, to call the procedure and provide the appropriate arguments:</span></span>  
  
     [!code-vb[VbVbalrInterop#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#12)]  
  
3. <span data-ttu-id="093c9-165">按 F5 執行專案。</span><span class="sxs-lookup"><span data-stu-id="093c9-165">Run the project by pressing F5.</span></span> <span data-ttu-id="093c9-166">訊息方塊會顯示 [**是]** 和 [**沒有**回應] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="093c9-166">The message box is displayed with both **Yes** and **No** response buttons.</span></span> <span data-ttu-id="093c9-167">按一下其中一個。</span><span class="sxs-lookup"><span data-stu-id="093c9-167">Click either one.</span></span>  
  
#### <a name="data-marshaling"></a><span data-ttu-id="093c9-168">資料封送處理</span><span class="sxs-lookup"><span data-stu-id="093c9-168">Data Marshaling</span></span>  
 <span data-ttu-id="093c9-169">Visual Basic 會自動轉換參數的資料類型和 Windows API 呼叫的傳回值, 但您可以使用`MarshalAs`屬性來明確指定 API 預期的非受控資料類型。</span><span class="sxs-lookup"><span data-stu-id="093c9-169">Visual Basic automatically converts the data types of parameters and return values for Windows API calls, but you can use the `MarshalAs` attribute to explicitly specify unmanaged data types that an API expects.</span></span> <span data-ttu-id="093c9-170">如需 interop 封送處理的詳細資訊, 請參閱[Interop 封送處理](../../../framework/interop/interop-marshaling.md)。</span><span class="sxs-lookup"><span data-stu-id="093c9-170">For more information about interop marshaling, see [Interop Marshaling](../../../framework/interop/interop-marshaling.md).</span></span>  
  
##### <a name="to-use-declare-and-marshalas-in-an-api-call"></a><span data-ttu-id="093c9-171">在 API 呼叫中使用 Declare 和 MarshalAs</span><span class="sxs-lookup"><span data-stu-id="093c9-171">To use Declare and MarshalAs in an API call</span></span>  
  
1. <span data-ttu-id="093c9-172">判斷您想要呼叫的函式名稱, 加上其引數、資料類型和傳回值。</span><span class="sxs-lookup"><span data-stu-id="093c9-172">Determine the name of the function you want to call, plus its arguments, data types, and return value.</span></span>  
  
2. <span data-ttu-id="093c9-173">若要簡化屬性的`MarshalAs`存取, 請在`Imports`類別或模組的程式碼頂端加入語句, 如下列範例所示:</span><span class="sxs-lookup"><span data-stu-id="093c9-173">To simplify access to the `MarshalAs` attribute, add an `Imports` statement to the top of the code for the class or module, as in the following example:</span></span>  
  
     [!code-vb[VbVbalrInterop#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#13)]  
  
3. <span data-ttu-id="093c9-174">將匯入函式的函式原型新增至您所使用的類別或模組, 並`MarshalAs`將屬性套用至參數或傳回值。</span><span class="sxs-lookup"><span data-stu-id="093c9-174">Add a function prototype for the imported function to the class or module you are using, and apply the `MarshalAs` attribute to the parameters or return value.</span></span> <span data-ttu-id="093c9-175">在下列範例中, 預期類型`void*`的 API 呼叫會封送處理為: `AsAny`</span><span class="sxs-lookup"><span data-stu-id="093c9-175">In the following example, an API call that expects the type `void*` is marshaled as `AsAny`:</span></span>  
  
     [!code-vb[VbVbalrInterop#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#14)]  
  
## <a name="api-calls-using-dllimport"></a><span data-ttu-id="093c9-176">使用 DllImport 的 API 呼叫</span><span class="sxs-lookup"><span data-stu-id="093c9-176">API Calls Using DllImport</span></span>  
 <span data-ttu-id="093c9-177">`DllImport`屬性提供第二種方式來呼叫 dll 中的函式, 而不使用類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="093c9-177">The `DllImport` attribute provides a second way to call functions in DLLs without type libraries.</span></span> <span data-ttu-id="093c9-178">`DllImport`大致上相當於使用`Declare`語句, 但可讓您更充分掌控函數的呼叫方式。</span><span class="sxs-lookup"><span data-stu-id="093c9-178">`DllImport` is roughly equivalent to using a `Declare` statement but provides more control over how functions are called.</span></span>  
  
 <span data-ttu-id="093c9-179">只要呼叫是`DllImport`指共用 (有時稱為*靜態*) 方法, 您就可以使用搭配大部分的 Windows API 呼叫。</span><span class="sxs-lookup"><span data-stu-id="093c9-179">You can use `DllImport` with most Windows API calls as long as the call refers to a shared (sometimes called *static*) method.</span></span> <span data-ttu-id="093c9-180">您不能使用需要類別實例的方法。</span><span class="sxs-lookup"><span data-stu-id="093c9-180">You cannot use methods that require an instance of a class.</span></span> <span data-ttu-id="093c9-181">不同`Declare` `DllImport`于語句`MarshalAs` , 呼叫不能使用屬性。</span><span class="sxs-lookup"><span data-stu-id="093c9-181">Unlike `Declare` statements, `DllImport` calls cannot use the `MarshalAs` attribute.</span></span>  
  
### <a name="to-call-a-windows-api-using-the-dllimport-attribute"></a><span data-ttu-id="093c9-182">使用 DllImport 屬性呼叫 Windows API</span><span class="sxs-lookup"><span data-stu-id="093c9-182">To call a Windows API using the DllImport attribute</span></span>  
  
1. <span data-ttu-id="093c9-183">按一下 [檔案] 功能表上的 [**新增**],然後按一下 [**專案**], 以開啟新的 Windows 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="093c9-183">Open a new Windows Application project by clicking **New** on the **File** menu, and then clicking **Project**.</span></span> <span data-ttu-id="093c9-184">[ **新增專案** ] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="093c9-184">The **New Project** dialog box appears.</span></span>  
  
2. <span data-ttu-id="093c9-185">從 Visual Basic 專案範本清單中選取 [ **Windows 應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="093c9-185">Select **Windows Application** from the list of Visual Basic project templates.</span></span> <span data-ttu-id="093c9-186">隨即顯示新專案。</span><span class="sxs-lookup"><span data-stu-id="093c9-186">The new project is displayed.</span></span>  
  
3. <span data-ttu-id="093c9-187">將名`Button2`為的按鈕新增至 [啟動表單]。</span><span class="sxs-lookup"><span data-stu-id="093c9-187">Add a button named `Button2` to the startup form.</span></span>  
  
4. <span data-ttu-id="093c9-188">`Button2`按兩下以開啟表單的程式碼視圖。</span><span class="sxs-lookup"><span data-stu-id="093c9-188">Double-click `Button2` to open the code view for the form.</span></span>  
  
5. <span data-ttu-id="093c9-189">若要簡化對`DllImport`的存取, `Imports`請將語句新增至啟動表單類別的程式碼頂端:</span><span class="sxs-lookup"><span data-stu-id="093c9-189">To simplify access to `DllImport`, add an `Imports` statement to the top of the code for the startup form class:</span></span>  
  
     [!code-vb[VbVbalrInterop#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#13)]  
  
6. <span data-ttu-id="093c9-190">在表單的`End Class`語句前面宣告空白函式, 並`MoveFile`將函式命名為。</span><span class="sxs-lookup"><span data-stu-id="093c9-190">Declare an empty function preceding the `End Class` statement for the form, and name the function `MoveFile`.</span></span>  
  
7. <span data-ttu-id="093c9-191">`Public`將和`Shared`修飾詞套用至函式宣告, 並根據 Windows `MoveFile` API 函式所使用的引數設定的參數:</span><span class="sxs-lookup"><span data-stu-id="093c9-191">Apply the `Public` and `Shared` modifiers to the function declaration and set parameters for `MoveFile` based on the arguments the Windows API function uses:</span></span>  
  
     [!code-vb[VbVbalrInterop#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#16)]  
  
     <span data-ttu-id="093c9-192">您的函式可以有任何有效的程式名稱;`DllImport`屬性會指定 DLL 中的名稱。</span><span class="sxs-lookup"><span data-stu-id="093c9-192">Your function can have any valid procedure name; the `DllImport` attribute specifies the name in the DLL.</span></span> <span data-ttu-id="093c9-193">它也會處理參數和傳回值的互通性封送處理, 因此您可以選擇與 API 所使用的資料類型 Visual Studio 的資料類型。</span><span class="sxs-lookup"><span data-stu-id="093c9-193">It also handles interoperability marshaling for the parameters and return values, so you can choose Visual Studio data types that are similar to the data types the API uses.</span></span>  
  
8. <span data-ttu-id="093c9-194">`DllImport`將屬性套用至空白函數。</span><span class="sxs-lookup"><span data-stu-id="093c9-194">Apply the `DllImport` attribute to the empty function.</span></span> <span data-ttu-id="093c9-195">第一個參數是包含您要呼叫之函式的 DLL 名稱和位置。</span><span class="sxs-lookup"><span data-stu-id="093c9-195">The first parameter is the name and location of the DLL containing the function you are calling.</span></span> <span data-ttu-id="093c9-196">您不需要指定位於 Windows 系統目錄中的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="093c9-196">You do not need to specify the path for files located in the Windows system directories.</span></span> <span data-ttu-id="093c9-197">第二個參數是具名引數, 可指定 Windows API 中的函式名稱。</span><span class="sxs-lookup"><span data-stu-id="093c9-197">The second parameter is a named argument that specifies the name of the function in the Windows API.</span></span> <span data-ttu-id="093c9-198">在此範例中, `DllImport`屬性會強制將`MoveFile`呼叫轉送到`MoveFileW` kernel32.dll 中的。URLMON.DLL.</span><span class="sxs-lookup"><span data-stu-id="093c9-198">In this example, the `DllImport` attribute forces calls to `MoveFile` to be forwarded to `MoveFileW` in KERNEL32.DLL.</span></span> <span data-ttu-id="093c9-199">方法會將檔案從路徑`src`複製到路徑`dst`。 `MoveFileW`</span><span class="sxs-lookup"><span data-stu-id="093c9-199">The `MoveFileW` method copies a file from the path `src` to the path `dst`.</span></span>  
  
     [!code-vb[VbVbalrInterop#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#17)]  
  
9. <span data-ttu-id="093c9-200">將程式碼`Button2_Click`加入至事件處理常式以呼叫函數:</span><span class="sxs-lookup"><span data-stu-id="093c9-200">Add code to the `Button2_Click` event handler to call the function:</span></span>  
  
     [!code-vb[VbVbalrInterop#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#18)]  
  
10. <span data-ttu-id="093c9-201">建立名為 test.txt 的檔案, 並將它放在硬碟的 C:\Tmp 目錄中。</span><span class="sxs-lookup"><span data-stu-id="093c9-201">Create a file named Test.txt and place it in the C:\Tmp directory on your hard drive.</span></span> <span data-ttu-id="093c9-202">視需要建立 Tmp 目錄。</span><span class="sxs-lookup"><span data-stu-id="093c9-202">Create the Tmp directory if necessary.</span></span>  
  
11. <span data-ttu-id="093c9-203">請按 F5 啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="093c9-203">Press F5 to start the application.</span></span> <span data-ttu-id="093c9-204">主要表單隨即出現。</span><span class="sxs-lookup"><span data-stu-id="093c9-204">The main form appears.</span></span>  
  
12. <span data-ttu-id="093c9-205">按一下 [ **Button2**]。</span><span class="sxs-lookup"><span data-stu-id="093c9-205">Click **Button2**.</span></span> <span data-ttu-id="093c9-206">如果可以移動檔案, 就會顯示「檔案已成功移動」訊息。</span><span class="sxs-lookup"><span data-stu-id="093c9-206">The message "The file was moved successfully" is displayed if the file can be moved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="093c9-207">另請參閱</span><span class="sxs-lookup"><span data-stu-id="093c9-207">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="093c9-208">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="093c9-208">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="093c9-209">Auto</span><span class="sxs-lookup"><span data-stu-id="093c9-209">Auto</span></span>](../../../visual-basic/language-reference/modifiers/auto.md)
- [<span data-ttu-id="093c9-210">Alias</span><span class="sxs-lookup"><span data-stu-id="093c9-210">Alias</span></span>](../../../visual-basic/language-reference/statements/alias-clause.md)
- [<span data-ttu-id="093c9-211">COM Interop</span><span class="sxs-lookup"><span data-stu-id="093c9-211">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)
- [<span data-ttu-id="093c9-212">在 Managed 程式碼中建立原型</span><span class="sxs-lookup"><span data-stu-id="093c9-212">Creating Prototypes in Managed Code</span></span>](../../../framework/interop/creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="093c9-213">做為回呼方法，委派封送處理</span><span class="sxs-lookup"><span data-stu-id="093c9-213">Marshaling a Delegate as a Callback Method</span></span>](../../../framework/interop/marshaling-a-delegate-as-a-callback-method.md)
