---
title: 逐步解說：呼叫 Windows API
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
ms.openlocfilehash: 88b3df2f18add6641d0355d2c605bc5f74dabbc7
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91098316"
---
# <a name="walkthrough-calling-windows-apis-visual-basic"></a><span data-ttu-id="f3dc2-102">逐步解說：呼叫 Windows API (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f3dc2-102">Walkthrough: Calling Windows APIs (Visual Basic)</span></span>

<span data-ttu-id="f3dc2-103">Windows Api 是 (Dll) 的動態連結程式庫，這是 Windows 作業系統的一部分。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-103">Windows APIs are dynamic-link libraries (DLLs) that are part of the Windows operating system.</span></span> <span data-ttu-id="f3dc2-104">當難以撰寫您自己的對等程式時，您可以使用它們來執行工作。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-104">You use them to perform tasks when it is difficult to write equivalent procedures of your own.</span></span> <span data-ttu-id="f3dc2-105">例如，Windows 提供名為的函 `FlashWindowEx` 式，可讓您讓應用程式的標題列在淺色和深色陰影之間交替。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-105">For example, Windows provides a function named `FlashWindowEx` that lets you make the title bar for an application alternate between light and dark shades.</span></span>  
  
 <span data-ttu-id="f3dc2-106">在程式碼中使用 Windows Api 的優點是，它們可以節省開發時間，因為它們包含許多已撰寫並等候使用的實用功能。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-106">The advantage of using Windows APIs in your code is that they can save development time because they contain dozens of useful functions that are already written and waiting to be used.</span></span> <span data-ttu-id="f3dc2-107">缺點是 Windows Api 可能難以使用，並在發生問題時 unforgiving。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-107">The disadvantage is that Windows APIs can be difficult to work with and unforgiving when things go wrong.</span></span>  
  
 <span data-ttu-id="f3dc2-108">Windows Api 代表互通性的特殊類別。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-108">Windows APIs represent a special category of interoperability.</span></span> <span data-ttu-id="f3dc2-109">Windows Api 不會使用 managed 程式碼、沒有內建類型程式庫，而且使用的資料類型與 Visual Studio 所用的不同。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-109">Windows APIs do not use managed code, do not have built-in type libraries, and use data types that are different than those used with Visual Studio.</span></span> <span data-ttu-id="f3dc2-110">由於這些差異，而且 Windows Api 不是 COM 物件，因此與 Windows Api 的互通性和 .NET Framework 是使用平台叫用（或 PInvoke）來執行。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-110">Because of these differences, and because Windows APIs are not COM objects, interoperability with Windows APIs and the .NET Framework is performed using platform invoke, or PInvoke.</span></span> <span data-ttu-id="f3dc2-111">平台叫用是一種服務，可讓 managed 程式碼呼叫 Dll 中所執行的非受控函式。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-111">Platform invoke is a service that enables managed code to call unmanaged functions implemented in DLLs.</span></span> <span data-ttu-id="f3dc2-112">如需詳細資訊，請參閱 [使用非受控 DLL](../../../framework/interop/consuming-unmanaged-dll-functions.md)函式。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-112">For more information, see [Consuming Unmanaged DLL Functions](../../../framework/interop/consuming-unmanaged-dll-functions.md).</span></span> <span data-ttu-id="f3dc2-113">您可以使用 `Declare` 語句或將屬性套用至空白程式，在 Visual Basic 中使用 PInvoke `DllImport` 。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-113">You can use PInvoke in Visual Basic by using either the `Declare` statement or applying the `DllImport` attribute to an empty procedure.</span></span>  
  
 <span data-ttu-id="f3dc2-114">Windows API 呼叫在過去 Visual Basic 程式設計中是很重要的一部分，但是在 Visual Basic .NET 中很少需要。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-114">Windows API calls were an important part of Visual Basic programming in the past, but are seldom necessary with Visual Basic .NET.</span></span> <span data-ttu-id="f3dc2-115">可能的話，您應該使用 .NET Framework 中的 managed 程式碼來執行工作，而不是使用 Windows API 呼叫。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-115">Whenever possible, you should use managed code from the .NET Framework to perform tasks, instead of Windows API calls.</span></span> <span data-ttu-id="f3dc2-116">本逐步解說提供在需要使用 Windows Api 的情況下的資訊。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-116">This walkthrough provides information for those situations in which using Windows APIs is necessary.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="api-calls-using-declare"></a><span data-ttu-id="f3dc2-117">使用 Declare 的 API 呼叫</span><span class="sxs-lookup"><span data-stu-id="f3dc2-117">API Calls Using Declare</span></span>  

 <span data-ttu-id="f3dc2-118">呼叫 Windows Api 最常見的方法是使用 `Declare` 語句。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-118">The most common way to call Windows APIs is by using the `Declare` statement.</span></span>  
  
### <a name="to-declare-a-dll-procedure"></a><span data-ttu-id="f3dc2-119">宣告 DLL 程式</span><span class="sxs-lookup"><span data-stu-id="f3dc2-119">To declare a DLL procedure</span></span>  
  
1. <span data-ttu-id="f3dc2-120">判斷您想要呼叫之函式的名稱，加上其引數、引數型別和傳回值，以及包含該函式之 DLL 的名稱和位置。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-120">Determine the name of the function you want to call, plus its arguments, argument types, and return value, as well as the name and location of the DLL that contains it.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f3dc2-121">如需 Windows Api 的完整資訊，請參閱 Platform SDK Windows API 中的 Win32 SDK 檔。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-121">For complete information about the Windows APIs, see the Win32 SDK documentation in the Platform SDK Windows API.</span></span> <span data-ttu-id="f3dc2-122">如需有關 Windows Api 使用之常數的詳細資訊，請檢查包含在 Platform SDK 中的標頭檔，例如 Windows .h。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-122">For more information about the constants that Windows APIs use, examine the header files such as Windows.h included with the Platform SDK.</span></span>  
  
2. <span data-ttu-id="f3dc2-123">**在 [檔案**] 功能表上按一下 [**新增**]，然後按一下 [**專案**]，以開啟新的 Windows 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-123">Open a new Windows Application project by clicking **New** on the **File** menu, and then clicking **Project**.</span></span> <span data-ttu-id="f3dc2-124">[新增專案]  對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-124">The **New Project** dialog box appears.</span></span>  
  
3. <span data-ttu-id="f3dc2-125">從 Visual Basic 專案範本清單中選取 [ **Windows 應用程式** ]。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-125">Select **Windows Application** from the list of Visual Basic project templates.</span></span> <span data-ttu-id="f3dc2-126">新的專案隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-126">The new project is displayed.</span></span>  
  
4. <span data-ttu-id="f3dc2-127">將下列函式新增 `Declare` 至您要在其中使用 DLL 的類別或模組：</span><span class="sxs-lookup"><span data-stu-id="f3dc2-127">Add the following `Declare` function either to the class or module in which you want to use the DLL:</span></span>  
  
     [!code-vb[VbVbalrInterop#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#9)]  
  
### <a name="parts-of-the-declare-statement"></a><span data-ttu-id="f3dc2-128">Declare 語句的元件</span><span class="sxs-lookup"><span data-stu-id="f3dc2-128">Parts of the Declare Statement</span></span>  

 <span data-ttu-id="f3dc2-129">`Declare`語句包含下列元素。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-129">The `Declare` statement includes the following elements.</span></span>  
  
#### <a name="auto-modifier"></a><span data-ttu-id="f3dc2-130">Auto 修飾詞</span><span class="sxs-lookup"><span data-stu-id="f3dc2-130">Auto modifier</span></span>  

 <span data-ttu-id="f3dc2-131">此 `Auto` 修飾詞會根據 common language runtime 規則 (或別名名稱（如果指定) ），指示執行時間根據方法名稱來轉換字串。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-131">The `Auto` modifier instructs the runtime to convert the string based on the method name according to common language runtime rules (or alias name if specified).</span></span>  
  
#### <a name="lib-and-alias-keywords"></a><span data-ttu-id="f3dc2-132">Lib 和 Alias 關鍵字</span><span class="sxs-lookup"><span data-stu-id="f3dc2-132">Lib and Alias keywords</span></span>  

 <span data-ttu-id="f3dc2-133">關鍵字後面的名稱 `Function` 是程式用來存取匯入函式的名稱。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-133">The name following the `Function` keyword is the name your program uses to access the imported function.</span></span> <span data-ttu-id="f3dc2-134">它可以與您所呼叫之函式的真實名稱相同，或者您可以使用任何有效的程式名稱，然後使用 `Alias` 關鍵字來指定您要呼叫之函式的真實名稱。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-134">It can be the same as the real name of the function you are calling, or you can use any valid procedure name and then employ the `Alias` keyword to specify the real name of the function you are calling.</span></span>  
  
 <span data-ttu-id="f3dc2-135">指定 `Lib` 關鍵字，後面接著包含您要呼叫之函式的 DLL 名稱和位置。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-135">Specify the `Lib` keyword, followed by the name and location of the DLL that contains the function you are calling.</span></span> <span data-ttu-id="f3dc2-136">您不需要為位於 Windows 系統目錄中的檔案指定路徑。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-136">You do not need to specify the path for files located in the Windows system directories.</span></span>  
  
 <span data-ttu-id="f3dc2-137">`Alias`如果您要呼叫的函式名稱不是有效的 Visual Basic 程式名稱，或與應用程式中其他專案的名稱衝突，請使用關鍵字。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-137">Use the `Alias` keyword if the name of the function you are calling is not a valid Visual Basic procedure name, or conflicts with the name of other items in your application.</span></span> <span data-ttu-id="f3dc2-138">`Alias` 指出所呼叫之函式的真實名稱。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-138">`Alias` indicates the true name of the function being called.</span></span>  
  
#### <a name="argument-and-data-type-declarations"></a><span data-ttu-id="f3dc2-139">引數和資料類型宣告</span><span class="sxs-lookup"><span data-stu-id="f3dc2-139">Argument and Data Type Declarations</span></span>  

 <span data-ttu-id="f3dc2-140">宣告引數和其資料類型。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-140">Declare the arguments and their data types.</span></span> <span data-ttu-id="f3dc2-141">這個部分可能會很困難，因為 Windows 使用的資料類型不會對應至 Visual Studio 資料類型。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-141">This part can be challenging because the data types that Windows uses do not correspond to Visual Studio data types.</span></span> <span data-ttu-id="f3dc2-142">Visual Basic 藉由將引數轉換成相容的資料類型（稱為 *封送*處理的程式），來為您執行許多工作。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-142">Visual Basic does a lot of the work for you by converting arguments to compatible data types, a process called *marshaling*.</span></span> <span data-ttu-id="f3dc2-143">您可以使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 命名空間中定義的屬性，明確控制引數的封送處理方式 <xref:System.Runtime.InteropServices> 。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-143">You can explicitly control how arguments are marshaled by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute defined in the <xref:System.Runtime.InteropServices> namespace.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f3dc2-144">舊版 Visual Basic 允許您宣告參數 `As Any` ，表示可以使用任何資料類型的資料。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-144">Previous versions of Visual Basic allowed you to declare parameters `As Any`, meaning that data of any data type could be used.</span></span> <span data-ttu-id="f3dc2-145">Visual Basic 需要針對所有語句使用特定的資料類型 `Declare` 。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-145">Visual Basic requires that you use a specific data type for all `Declare` statements.</span></span>  
  
#### <a name="windows-api-constants"></a><span data-ttu-id="f3dc2-146">Windows API 常數</span><span class="sxs-lookup"><span data-stu-id="f3dc2-146">Windows API Constants</span></span>  

 <span data-ttu-id="f3dc2-147">某些引數是常數的組合。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-147">Some arguments are combinations of constants.</span></span> <span data-ttu-id="f3dc2-148">例如， `MessageBox` 在此逐步解說中所顯示的 API 會接受一個稱為的整數引數 `Typ` ，以控制訊息框的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-148">For example, the `MessageBox` API shown in this walkthrough accepts an integer argument called `Typ` that controls how the message box is displayed.</span></span> <span data-ttu-id="f3dc2-149">您可以檢查 WinUser 檔案中的語句來判斷這些常數的數值 `#define` 。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-149">You can determine the numeric value of these constants by examining the `#define` statements in the file WinUser.h.</span></span> <span data-ttu-id="f3dc2-150">數值通常會以十六進位顯示，因此您可能會想要使用計算機來新增它們並轉換成 decimal。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-150">The numeric values are generally shown in hexadecimal, so you may want to use a calculator to add them and convert to decimal.</span></span> <span data-ttu-id="f3dc2-151">例如，如果您想要結合驚嘆號樣式0x00000030 的常數和 [ `MB_ICONEXCLAMATION` 是]/[否] 樣式 `MB_YESNO` 的0x00000004，您可以加入數位並取得0x00000034 的結果，或 52 decimal。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-151">For example, if you want to combine the constants for the exclamation style `MB_ICONEXCLAMATION` 0x00000030 and the Yes/No style `MB_YESNO` 0x00000004, you can add the numbers and get a result of 0x00000034, or 52 decimal.</span></span> <span data-ttu-id="f3dc2-152">雖然您可以直接使用 decimal 結果，但最好是將這些值宣告為應用程式中的常數，並使用運算子將它們合併 `Or` 。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-152">Although you can use the decimal result directly, it is better to declare these values as constants in your application and combine them using the `Or` operator.</span></span>  
  
##### <a name="to-declare-constants-for-windows-api-calls"></a><span data-ttu-id="f3dc2-153">宣告 Windows API 呼叫的常數</span><span class="sxs-lookup"><span data-stu-id="f3dc2-153">To declare constants for Windows API calls</span></span>  
  
1. <span data-ttu-id="f3dc2-154">請參閱您所呼叫 Windows 函式的檔。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-154">Consult the documentation for the Windows function you are calling.</span></span> <span data-ttu-id="f3dc2-155">判斷其所使用的常數名稱，以及包含這些常數數值的 .h 檔案名。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-155">Determine the name of the constants it uses and the name of the .h file that contains the numeric values for these constants.</span></span>  
  
2. <span data-ttu-id="f3dc2-156">使用文字編輯器（例如 [記事本]）來查看標頭 ( .h) 檔案的內容，並尋找與您正在使用之常數相關聯的值。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-156">Use a text editor, such as Notepad, to view the contents of the header (.h) file, and find the values associated with the constants you are using.</span></span> <span data-ttu-id="f3dc2-157">例如，API 會 `MessageBox` 使用常數 `MB_ICONQUESTION` 在訊息方塊中顯示問號。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-157">For example, the `MessageBox` API uses the constant `MB_ICONQUESTION` to show a question mark in the message box.</span></span> <span data-ttu-id="f3dc2-158">的定義位於 `MB_ICONQUESTION` WinUser 中，並顯示如下：</span><span class="sxs-lookup"><span data-stu-id="f3dc2-158">The definition for `MB_ICONQUESTION` is in WinUser.h and appears as follows:</span></span>  
  
     `#define MB_ICONQUESTION             0x00000020L`  
  
3. <span data-ttu-id="f3dc2-159">將對等 `Const` 語句新增至您的類別或模組，以將這些常數提供給您的應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-159">Add equivalent `Const` statements to your class or module to make these constants available to your application.</span></span> <span data-ttu-id="f3dc2-160">例如：</span><span class="sxs-lookup"><span data-stu-id="f3dc2-160">For example:</span></span>  
  
     [!code-vb[VbVbalrInterop#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#11)]  
  
###### <a name="to-call-the-dll-procedure"></a><span data-ttu-id="f3dc2-161">呼叫 DLL 程式</span><span class="sxs-lookup"><span data-stu-id="f3dc2-161">To call the DLL procedure</span></span>  
  
1. <span data-ttu-id="f3dc2-162">將名為的按鈕新增 `Button1` 至專案的啟動表單，然後按兩下以查看其程式碼。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-162">Add a button named `Button1` to the startup form for your project, and then double-click it to view its code.</span></span> <span data-ttu-id="f3dc2-163">按鈕的事件處理常式隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-163">The event handler for the button is displayed.</span></span>  
  
2. <span data-ttu-id="f3dc2-164">將程式碼加入至 `Click` 您所加入之按鈕的事件處理常式，以呼叫程式並提供適當的引數：</span><span class="sxs-lookup"><span data-stu-id="f3dc2-164">Add code to the `Click` event handler for the button you added, to call the procedure and provide the appropriate arguments:</span></span>  
  
     [!code-vb[VbVbalrInterop#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#12)]  
  
3. <span data-ttu-id="f3dc2-165">按下 F5 來執行專案。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-165">Run the project by pressing F5.</span></span> <span data-ttu-id="f3dc2-166">訊息方塊會顯示 [ **是]** 和 [ **沒有** 回應] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-166">The message box is displayed with both **Yes** and **No** response buttons.</span></span> <span data-ttu-id="f3dc2-167">按一下其中一個。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-167">Click either one.</span></span>  
  
#### <a name="data-marshaling"></a><span data-ttu-id="f3dc2-168">資料封送處理</span><span class="sxs-lookup"><span data-stu-id="f3dc2-168">Data Marshaling</span></span>  

 <span data-ttu-id="f3dc2-169">Visual Basic 會自動轉換 Windows API 呼叫的參數和傳回值的資料類型，但您可以使用 `MarshalAs` 屬性來明確指定 API 預期的非受控資料類型。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-169">Visual Basic automatically converts the data types of parameters and return values for Windows API calls, but you can use the `MarshalAs` attribute to explicitly specify unmanaged data types that an API expects.</span></span> <span data-ttu-id="f3dc2-170">如需有關 interop 封送處理的詳細資訊，請參閱 [Interop 封送處理](../../../framework/interop/interop-marshaling.md)。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-170">For more information about interop marshaling, see [Interop Marshaling](../../../framework/interop/interop-marshaling.md).</span></span>  
  
##### <a name="to-use-declare-and-marshalas-in-an-api-call"></a><span data-ttu-id="f3dc2-171">在 API 呼叫中使用 Declare 和 MarshalAs</span><span class="sxs-lookup"><span data-stu-id="f3dc2-171">To use Declare and MarshalAs in an API call</span></span>  
  
1. <span data-ttu-id="f3dc2-172">判斷您想要呼叫之函式的名稱，加上其引數、資料類型和傳回值。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-172">Determine the name of the function you want to call, plus its arguments, data types, and return value.</span></span>  
  
2. <span data-ttu-id="f3dc2-173">若要簡化對屬性的存取 `MarshalAs` ，請將 `Imports` 語句加入至類別或模組的程式碼頂端，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="f3dc2-173">To simplify access to the `MarshalAs` attribute, add an `Imports` statement to the top of the code for the class or module, as in the following example:</span></span>  
  
     [!code-vb[VbVbalrInterop#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#13)]  
  
3. <span data-ttu-id="f3dc2-174">將匯入函式的函式原型新增至您所使用的類別或模組，然後將 `MarshalAs` 屬性套用至參數或傳回值。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-174">Add a function prototype for the imported function to the class or module you are using, and apply the `MarshalAs` attribute to the parameters or return value.</span></span> <span data-ttu-id="f3dc2-175">在下列範例中，需要類型的 API 呼叫 `void*` 封送處理為 `AsAny` ：</span><span class="sxs-lookup"><span data-stu-id="f3dc2-175">In the following example, an API call that expects the type `void*` is marshaled as `AsAny`:</span></span>  
  
     [!code-vb[VbVbalrInterop#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#14)]  
  
## <a name="api-calls-using-dllimport"></a><span data-ttu-id="f3dc2-176">使用 DllImport 的 API 呼叫</span><span class="sxs-lookup"><span data-stu-id="f3dc2-176">API Calls Using DllImport</span></span>  

 <span data-ttu-id="f3dc2-177">`DllImport`屬性提供的第二種方式是在沒有類型程式庫的 dll 中呼叫函式。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-177">The `DllImport` attribute provides a second way to call functions in DLLs without type libraries.</span></span> <span data-ttu-id="f3dc2-178">`DllImport` 大致上相當於使用 `Declare` 語句，但可讓您更充分掌控函數的呼叫方式。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-178">`DllImport` is roughly equivalent to using a `Declare` statement but provides more control over how functions are called.</span></span>  
  
 <span data-ttu-id="f3dc2-179">`DllImport`只要呼叫參考共用 (（有時稱為*靜態*) 方法），就可以使用與大部分的 Windows API 呼叫。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-179">You can use `DllImport` with most Windows API calls as long as the call refers to a shared (sometimes called *static*) method.</span></span> <span data-ttu-id="f3dc2-180">您無法使用需要類別實例的方法。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-180">You cannot use methods that require an instance of a class.</span></span> <span data-ttu-id="f3dc2-181">不同 `Declare` 于語句， `DllImport` 呼叫不能使用 `MarshalAs` 屬性。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-181">Unlike `Declare` statements, `DllImport` calls cannot use the `MarshalAs` attribute.</span></span>  
  
### <a name="to-call-a-windows-api-using-the-dllimport-attribute"></a><span data-ttu-id="f3dc2-182">使用 DllImport 屬性呼叫 Windows API</span><span class="sxs-lookup"><span data-stu-id="f3dc2-182">To call a Windows API using the DllImport attribute</span></span>  
  
1. <span data-ttu-id="f3dc2-183">**在 [檔案**] 功能表上按一下 [**新增**]，然後按一下 [**專案**]，以開啟新的 Windows 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-183">Open a new Windows Application project by clicking **New** on the **File** menu, and then clicking **Project**.</span></span> <span data-ttu-id="f3dc2-184">[新增專案]  對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-184">The **New Project** dialog box appears.</span></span>  
  
2. <span data-ttu-id="f3dc2-185">從 Visual Basic 專案範本清單中選取 [ **Windows 應用程式** ]。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-185">Select **Windows Application** from the list of Visual Basic project templates.</span></span> <span data-ttu-id="f3dc2-186">新的專案隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-186">The new project is displayed.</span></span>  
  
3. <span data-ttu-id="f3dc2-187">將名為的按鈕加入 `Button2` 至啟動表單。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-187">Add a button named `Button2` to the startup form.</span></span>  
  
4. <span data-ttu-id="f3dc2-188">按兩下 `Button2` 以開啟表單的程式碼視圖。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-188">Double-click `Button2` to open the code view for the form.</span></span>  
  
5. <span data-ttu-id="f3dc2-189">若要簡化 `DllImport` 的存取，請將 `Imports` 語句加入至 startup form 類別的程式碼頂端：</span><span class="sxs-lookup"><span data-stu-id="f3dc2-189">To simplify access to `DllImport`, add an `Imports` statement to the top of the code for the startup form class:</span></span>  
  
     [!code-vb[VbVbalrInterop#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#13)]  
  
6. <span data-ttu-id="f3dc2-190">在表單的語句前面宣告空的函式 `End Class` ，並為函數命名 `MoveFile` 。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-190">Declare an empty function preceding the `End Class` statement for the form, and name the function `MoveFile`.</span></span>  
  
7. <span data-ttu-id="f3dc2-191">將和修飾詞套用 `Public` `Shared` 至函式宣告，並 `MoveFile` 根據 Windows API 函數使用的引數來設定參數：</span><span class="sxs-lookup"><span data-stu-id="f3dc2-191">Apply the `Public` and `Shared` modifiers to the function declaration and set parameters for `MoveFile` based on the arguments the Windows API function uses:</span></span>  
  
     [!code-vb[VbVbalrInterop#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#16)]  
  
     <span data-ttu-id="f3dc2-192">您的函式可以有任何有效的程式名稱; `DllImport` 屬性會在 DLL 中指定名稱。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-192">Your function can have any valid procedure name; the `DllImport` attribute specifies the name in the DLL.</span></span> <span data-ttu-id="f3dc2-193">它也會處理參數和傳回值的互通性封送處理，因此您可以選擇與 API 使用的資料類型類似的 Visual Studio 資料類型。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-193">It also handles interoperability marshaling for the parameters and return values, so you can choose Visual Studio data types that are similar to the data types the API uses.</span></span>  
  
8. <span data-ttu-id="f3dc2-194">將 `DllImport` 屬性套用至空白函數。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-194">Apply the `DllImport` attribute to the empty function.</span></span> <span data-ttu-id="f3dc2-195">第一個參數是 DLL 的名稱和位置，其中包含您要呼叫的函式。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-195">The first parameter is the name and location of the DLL containing the function you are calling.</span></span> <span data-ttu-id="f3dc2-196">您不需要為位於 Windows 系統目錄中的檔案指定路徑。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-196">You do not need to specify the path for files located in the Windows system directories.</span></span> <span data-ttu-id="f3dc2-197">第二個參數是具名引數，可指定 Windows API 中的函式名稱。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-197">The second parameter is a named argument that specifies the name of the function in the Windows API.</span></span> <span data-ttu-id="f3dc2-198">在此範例中， `DllImport` 屬性會強制將呼叫 `MoveFile` 轉送至 `MoveFileW` KERNEL32.DLL 中的。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-198">In this example, the `DllImport` attribute forces calls to `MoveFile` to be forwarded to `MoveFileW` in KERNEL32.DLL.</span></span> <span data-ttu-id="f3dc2-199">`MoveFileW`方法會將檔案從路徑複製 `src` 到路徑 `dst` 。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-199">The `MoveFileW` method copies a file from the path `src` to the path `dst`.</span></span>  
  
     [!code-vb[VbVbalrInterop#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#17)]  
  
9. <span data-ttu-id="f3dc2-200">將程式碼加入至 `Button2_Click` 事件處理常式，以呼叫函數：</span><span class="sxs-lookup"><span data-stu-id="f3dc2-200">Add code to the `Button2_Click` event handler to call the function:</span></span>  
  
     [!code-vb[VbVbalrInterop#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#18)]  
  
10. <span data-ttu-id="f3dc2-201">建立名為 Test.txt 的檔案，並將它放在硬碟的 C:\Tmp 目錄中。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-201">Create a file named Test.txt and place it in the C:\Tmp directory on your hard drive.</span></span> <span data-ttu-id="f3dc2-202">如有必要，請建立 Tmp 目錄。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-202">Create the Tmp directory if necessary.</span></span>  
  
11. <span data-ttu-id="f3dc2-203">請按 F5 啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-203">Press F5 to start the application.</span></span> <span data-ttu-id="f3dc2-204">主要表單隨即出現。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-204">The main form appears.</span></span>  
  
12. <span data-ttu-id="f3dc2-205">按一下 [ **Button2**]。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-205">Click **Button2**.</span></span> <span data-ttu-id="f3dc2-206">如果可以移動檔案，則會顯示「檔案已成功移動」訊息。</span><span class="sxs-lookup"><span data-stu-id="f3dc2-206">The message "The file was moved successfully" is displayed if the file can be moved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3dc2-207">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3dc2-207">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="f3dc2-208">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="f3dc2-208">Declare Statement</span></span>](../../language-reference/statements/declare-statement.md)
- [<span data-ttu-id="f3dc2-209">Auto</span><span class="sxs-lookup"><span data-stu-id="f3dc2-209">Auto</span></span>](../../language-reference/modifiers/auto.md)
- [<span data-ttu-id="f3dc2-210">別名</span><span class="sxs-lookup"><span data-stu-id="f3dc2-210">Alias</span></span>](../../language-reference/statements/alias-clause.md)
- [<span data-ttu-id="f3dc2-211">COM Interop</span><span class="sxs-lookup"><span data-stu-id="f3dc2-211">COM Interop</span></span>](index.md)
- [<span data-ttu-id="f3dc2-212">在 Managed 程式碼中建立原型</span><span class="sxs-lookup"><span data-stu-id="f3dc2-212">Creating Prototypes in Managed Code</span></span>](../../../framework/interop/creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="f3dc2-213">做為回呼方法，委派封送處理</span><span class="sxs-lookup"><span data-stu-id="f3dc2-213">Marshaling a Delegate as a Callback Method</span></span>](../../../framework/interop/marshaling-a-delegate-as-a-callback-method.md)
