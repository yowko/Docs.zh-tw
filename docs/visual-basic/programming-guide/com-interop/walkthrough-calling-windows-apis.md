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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 5001ccebb0a5b8cadd4e856342601506cf1d033f
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-calling-windows-apis-visual-basic"></a>逐步解說：呼叫 Windows API (Visual Basic)
Windows Api，是屬於 Windows 作業系統的動態連結程式庫 (Dll)。 您可以使用它們來執行工作時很難撰寫您自己的對等的程序。 例如，Windows 提供函式，名為`FlashWindowEx`，可讓您的應用程式的標題列光影灰色陰影之間交替。  
  
 在您的程式碼中使用 Windows Api 的優點是，它們就可以節省開發時間，因為它們包含數十個有用的功能已經撰寫，並可立即使用。 缺點是 Windows Api 很難發生錯誤時工作和正確性。  
  
 Windows Api 都代表一個特殊種類的互通性。 Windows Api 不會使用 managed 程式碼，並沒有內建型別程式庫，並使用不同的 Visual Studio 搭配使用的資料型別。 由於這些差異，而且因為 Windows Api 不是 COM 物件，與 Windows Api 的互通性和[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]透過平台叫用，或 PInvoke。 平台叫用是一項服務，可讓 managed 程式碼呼叫 unmanaged 函式在 Dll 中實作。 如需詳細資訊，請參閱[使用 Unmanaged DLL 函式](http://msdn.microsoft.com/library/eca7606e-ebfb-4f47-b8d9-289903fdc045)。 您可以使用中的 PInvoke[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]使用`Declare`陳述式或套用`DllImport`屬性設定為空的程序。  
  
 Windows API 呼叫是很重要的一部分[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]程式設計在過去，但這是很少需要[!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]。 可能的話，您應該使用 managed 程式碼的[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]來執行工作，而不是 Windows API 呼叫。 本逐步解說提供這兩種情況中使用的資訊是必要的 Windows Api。  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
## <a name="api-calls-using-declare"></a>API 呼叫使用宣告  
 呼叫 Windows Api 的最常見方式是使用`Declare`陳述式。  
  
#### <a name="to-declare-a-dll-procedure"></a>宣告 DLL 程序  
  
1.  決定您想要呼叫時，函式加上引數，引數類型的名稱，並傳回值，以及名稱和包含該 DLL 的位置。  
  
    > [!NOTE]
    >  如需 Windows Api 的完整資訊，請參閱平台 SDK Windows API 中的 Win32 SDK 文件。 如需有關使用 Windows Api 的常數的詳細資訊，請檢查例如 Windows.h 平台 SDK 隨附的標頭檔。  
  
2.  開啟新的 Windows 應用程式專案，依序按一下**新增**上**檔案**] 功能表，然後按一下 [**專案**。 [ **新增專案** ] 對話方塊隨即出現。  
  
3.  選取**Windows 應用程式**從清單中的[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]專案範本。 會顯示新的專案。  
  
4.  新增下列`Declare`函式類別，或是您要使用 DLL 的模組︰  
  
     [!code-vb[VbVbalrInterop #&9;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_1.vb)]  
  
### <a name="parts-of-the-declare-statement"></a>組件的 Declare 陳述式  
 `Declare`陳述式包括下列項目。  
  
#### <a name="auto-modifier"></a>自動修飾詞  
 `Auto`修飾詞會指示執行階段根據根據通用語言執行階段規則 （或別名名稱，如果指定） 的方法名稱的字串轉換。  
  
#### <a name="lib-and-alias-keywords"></a>Lib 和別名的關鍵字  
 名稱下`Function`關鍵字是程式用來存取匯入函式的名稱。 它可以是您呼叫的函式的實際名稱相同，或者您可以使用任何有效的程序名稱，然後採用`Alias`關鍵字來指定您要呼叫的函式的實際名稱。  
  
 指定`Lib`關鍵字，後面的名稱和位置，其中包含您要呼叫的函式的 dll。 您不需要指定位於 Windows 系統目錄中檔案的路徑。  
  
 使用`Alias`關鍵字，如果您要呼叫的函式名稱不是有效的[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]程序名稱或與您的應用程式中其他項目的名稱衝突。 `Alias`表示所呼叫的函式，則為 true 的名稱。  
  
#### <a name="argument-and-data-type-declarations"></a>引數和資料型別宣告  
 宣告的引數和其資料型別。 此組件可能項挑戰，因為 Windows 所使用的資料型別不會對應至 Visual Studio 資料型別。 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]將引數轉換為相容的資料型別，稱為程序會為您完成許多工作*封送處理*。 您可以明確地控制如何引數會封送處理使用<xref:System.Runtime.InteropServices.MarshalAsAttribute>中定義屬性<xref:System.Runtime.InteropServices>命名空間。</xref:System.Runtime.InteropServices> </xref:System.Runtime.InteropServices.MarshalAsAttribute>  
  
> [!NOTE]
>  舊版的[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]允許您將參數宣告`As Any`，亦即該資料的任何資料型別可用。 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]要求您使用特定資料型別所有`Declare`陳述式。  
  
#### <a name="windows-api-constants"></a>Windows API 常數  
 某些引數為常數的組合。 例如，`MessageBox`本逐步解說中的 API 可接受整數引數呼叫`Typ`，控制訊息方塊的顯示方式。 您可以藉由檢查來判斷兩個常數數值`#define`winuser.h 檔案中的陳述式。 數字的值是通常以十六進位顯示，因此您可以使用 [小算盤] 將活動加入並轉換為十進位數。 例如，如果您想要合併的驚嘆號樣式常數`MB_ICONEXCLAMATION`0x00000030 與是/無樣式`MB_YESNO`0x00000004，您可以將數字相加，並取得 0x00000034 或 52 結果十進位。 雖然您可以直接使用十進位結果，最好是將這些值宣告為您的應用程式中的常數，並將它們結合使用`Or`運算子。  
  
###### <a name="to-declare-constants-for-windows-api-calls"></a>若要宣告常數的 Windows API 呼叫  
  
1.  您要呼叫 Windows 函式，請參閱文件。 決定使用的常數名稱以及包含這些常數數值的.h 檔案的名稱。  
  
2.  若要檢視內容的標頭 (.h) 檔，使用文字編輯器，例如 [記事本]，並找出您正在使用的常數與相關聯的值。 例如， `MessageBox` API 所使用的常數`MB_ICONQUESTION`在訊息方塊中顯示問號。 定義`MB_ICONQUESTION`WinUser.h 中，會出現，如下所示︰  
  
     `#define MB_ICONQUESTION             0x00000020L`  
  
3.  加入對等項目`Const`至您的類別或模組，讓您的應用程式可使用這些常數的陳述式。 例如:   
  
     [!code-vb[VbVbalrInterop #&11;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_2.vb)]  
  
###### <a name="to-call-the-dll-procedure"></a>呼叫 DLL 的程序  
  
1.  新增一個按鈕名為`Button1`啟動表單專案，然後按兩下以檢視其程式碼。 隨即出現按鈕的事件處理常式。  
  
2.  加入程式碼以`Click`加入呼叫程序，並提供適當的引數的按鈕事件處理常式︰  
  
     [!code-vb[VbVbalrInterop #&12;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_3.vb)]  
  
3.  按 F5 執行專案。 訊息方塊會顯示這兩個**是**和**否**回應按鈕。 按一下其中一個。  
  
#### <a name="data-marshaling"></a>資料封送處理  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]自動轉換資料類型的參數和傳回值的 Windows API 呼叫，但是您可以使用`MarshalAs`屬性來明確指定 API 所預期的不受管理的資料型別。 如需 interop 封送處理的詳細資訊，請參閱[Interop 封送處理](http://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a)。  
  
###### <a name="to-use-declare-and-marshalas-in-an-api-call"></a>若要使用 Declare 和 MarshalAs API 呼叫  
  
1.  決定您想要再加上其引數，呼叫資料類型的函式的名稱，並傳回值。  
  
2.  若要簡化存取`MarshalAs`屬性中，加入`Imports`陳述式的類別或模組，如下列範例所示的程式碼頂端︰  
  
     [!code-vb[VbVbalrInterop #&13;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_4.vb)]  
  
3.  將函式原型來匯入函式加入至類別或模組，您使用，並套用`MarshalAs`屬性的參數或傳回值。 在下列範例中，可預期的型別的 API 呼叫`void*`封送處理為`AsAny`:  
  
     [!code-vb[VbVbalrInterop #&14;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_5.vb)]  
  
## <a name="api-calls-using-dllimport"></a>API 呼叫使用 DllImport  
 `DllImport`屬性會提供 Dll 中呼叫函式，而不需要型別程式庫的第二種方式。 `DllImport`大致上相當於使用`Declare`陳述式，但提供更充分掌控函式呼叫的方式。  
  
 您可以使用`DllImport`與大多數 Windows API 呼叫，只要呼叫指的是共用 (有時稱為*靜態*) 方法。 您不能使用需要的類別執行個體的方法。 不同於`Declare`陳述式，`DllImport`呼叫不能使用`MarshalAs`屬性。  
  
#### <a name="to-call-a-windows-api-using-the-dllimport-attribute"></a>呼叫 Windows API 使用 DllImport 屬性  
  
1.  開啟新的 Windows 應用程式專案，依序按一下**新增**上**檔案**] 功能表，然後按一下 [**專案**。 [ **新增專案** ] 對話方塊隨即出現。  
  
2.  選取**Windows 應用程式**從清單中的[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]專案範本。 會顯示新的專案。  
  
3.  新增一個按鈕名為`Button2`的啟動表單。  
  
4.  按兩下`Button2`開啟表單的程式碼檢視。  
  
5.  若要簡化存取`DllImport`，加入`Imports`啟動表單類別的程式碼頂端的陳述式︰  
  
     [!code-vb[VbVbalrInterop #&13;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_4.vb)]  
  
6.  空白的函式之前宣告`End Class`表單中，而且名稱函式的陳述式`MoveFile`。  
  
7.  套用`Public`和`Shared`函式宣告和設定參數的修飾詞`MoveFile`根據 Windows API 函式會使用的引數︰  
  
     [!code-vb[VbVbalrInterop #&16;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_6.vb)]  
  
     您的函式可以有任何有效的程序名稱;`DllImport`屬性在 DLL 中指定的名稱。 它也會處理互通性封送處理參數和傳回值，因此您可以選擇 Visual Studio 資料類型類似的資料類型則 API 使用。  
  
8.  套用`DllImport`屬性設定為空白的函式。 第一個參數是包含您要呼叫的函式的 dll 位置與名稱。 您不需要指定位於 Windows 系統目錄中檔案的路徑。 第二個參數是在 Windows API 中指定的函式名稱的具名引數。 在此範例中，`DllImport`屬性會強制執行呼叫`MoveFile`轉送至`MoveFileW`KERNEL32 中。DLL。 `MoveFileW`方法會複製檔案的路徑`src`路徑`dst`。  
  
     [!code-vb[VbVbalrInterop #&17;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_7.vb)]  
  
9. 加入程式碼以`Button2_Click`事件處理常式呼叫的函式︰  
  
     [!code-vb[VbVbalrInterop #&18;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_8.vb)]  
  
10. 建立名為 Test.txt 的檔案，並將它放在硬碟上 C:\Tmp 目錄中。 如有必要，請建立 Tmp 目錄。  
  
11. 請按 F5 啟動應用程式。 主表單隨即出現。  
  
12. 按一下  **Button2**。 如果可以移動檔案，會顯示 「 已成功移動檔案 」 訊息。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.InteropServices.DllImportAttribute></xref:System.Runtime.InteropServices.DllImportAttribute>   
 <xref:System.Runtime.InteropServices.MarshalAsAttribute></xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)   
 [自動](../../../visual-basic/language-reference/modifiers/auto.md)   
 [別名](../../../visual-basic/language-reference/statements/alias-clause.md)   
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)   
 [在 Managed 程式碼中建立原型](http://msdn.microsoft.com/library/ecdcf25d-cae3-4f07-a2b6-8397ac6dc42d)   
 [做為回呼方法，委派封送處理](http://msdn.microsoft.com/library/6ddd7866-9804-4571-84de-83f5cc017a5a)
