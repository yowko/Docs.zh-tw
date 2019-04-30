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
ms.openlocfilehash: 8fd63c2abedcd416937e2c281486bdc1716a275f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62022398"
---
# <a name="walkthrough-calling-windows-apis-visual-basic"></a>逐步解說：呼叫 Windows Api (Visual Basic)
Windows Api 是屬於 Windows 作業系統的動態連結程式庫 (Dll)。 您可以使用它們來執行工作時很難撰寫您自己的對等的程序。 比方說，Windows 會提供名為函式`FlashWindowEx`，可讓您的應用程式的標題列淺色與深色陰影之間。  
  
 在您的程式碼中使用 Windows Api 的優點是，他們就可以節省開發時間，因為它們包含數十個有用的功能，已撰寫並可立即使用。 缺點是 Windows Api 很難進行運作和十足，發生錯誤時。  
  
 Windows Api 就是一個特殊種類的互通性。 Windows Api 無法使用 managed 程式碼，並沒有內建型別程式庫，並使用不同於 Visual Studio 搭配使用的資料類型。 由於這些差異，以及因為 Windows Api 不是 COM 物件，與 Windows Api 的互通性和[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]必須利用平台叫用，或 PInvoke。 平台叫用是一項服務，可讓 managed 程式碼呼叫 unmanaged 的 Dll 中實作的函式。 如需詳細資訊，請參閱 <<c0> [ 使用 Unmanaged DLL 函式](../../../framework/interop/consuming-unmanaged-dll-functions.md)。 您也可以使用 Visual Basic 中使用 PInvoke`Declare`陳述式，或套用`DllImport`屬性設定為空的程序。  
  
 Windows API 呼叫是 Visual Basic 程式在過去，很重要的一部分，但很少會需要使用 Visual Basic.NET。 可能的話，您應該使用從 managed 程式碼[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]來執行工作，而不是 Windows API 呼叫。 本逐步解說提供在使用這種情況下的資訊是必要的 Windows Api。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="api-calls-using-declare"></a>API 呼叫使用宣告  
 呼叫 Windows Api 的最常見方式是使用`Declare`陳述式。  
  
#### <a name="to-declare-a-dll-procedure"></a>若要宣告的 DLL 程序  
  
1. 決定您想要呼叫的函式加上引數，引數類型的名稱，並傳回值，以及名稱與 DLL 包含它的位置。  
  
    > [!NOTE]
    >  如需 Windows Api 的完整資訊，請參閱平台 SDK Windows API 中的 Win32 SDK 文件。 如需有關使用 Windows Api 的常數的詳細資訊，請檢查等平台 SDK 隨附的 Windows.h 的標頭檔。  
  
2. 開啟新的 Windows 應用程式專案，依序按一下**的新**上**檔案**功能表，然後按一下**專案**。 [ **新增專案** ] 對話方塊隨即出現。  
  
3. 選取  **Windows 應用程式**從 Visual Basic 專案範本的清單。 新的專案會顯示。  
  
4. 新增下列`Declare`函式至類別或您要使用 DLL 的模組：  
  
     [!code-vb[VbVbalrInterop#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#9)]  
  
### <a name="parts-of-the-declare-statement"></a>組件的 Declare 陳述式  
 `Declare`陳述式包含下列項目。  
  
#### <a name="auto-modifier"></a>Auto 修飾詞  
 `Auto`修飾詞會指示執行階段將根據根據通用語言執行階段規則 （或如果指定的別名名稱） 的方法名稱的字串轉換。  
  
#### <a name="lib-and-alias-keywords"></a>Lib 和別名的關鍵字  
 後面的名`Function`關鍵字是程式用來存取匯入的函式的名稱。 它可以是您呼叫的函式的實際名稱相同，或者您可以使用任何有效的程序名稱，然後採用`Alias`關鍵字來指定您要呼叫的函式的實際名稱。  
  
 指定`Lib`關鍵字，後面的名稱和包含您要呼叫的函式的 DLL 位置。 您不需要指定位於 Windows 系統目錄中檔案的路徑。  
  
 使用`Alias`關鍵字，如果您呼叫的函式名稱不是有效的 Visual Basic 程序名稱，或您的應用程式中其他項目的名稱相衝突。 `Alias` 表示正在呼叫函式，則為 true 的名稱。  
  
#### <a name="argument-and-data-type-declarations"></a>引數和資料型別宣告  
 宣告引數和其資料類型。 這個部分可能項挑戰，因為 Windows 會使用的資料類型不會對應至 Visual Studio 的資料型別。 Visual Basic 會為您許多工作，藉由將引數轉換成相容的資料類型，這個程序稱為*封送處理*。 您可以明確地控制如何引數會封送處理使用<xref:System.Runtime.InteropServices.MarshalAsAttribute>屬性中定義<xref:System.Runtime.InteropServices>命名空間。  
  
> [!NOTE]
>  舊版的 Visual Basic 可讓您在宣告參數`As Any`，這表示該資料的任何資料型別可用。 Visual Basic 會要求您使用特定資料類型，所有`Declare`陳述式。  
  
#### <a name="windows-api-constants"></a>Windows API 的常數  
 某些引數為常數的組合。 例如，`MessageBox`本逐步解說中的 API 會接受整數引數呼叫`Typ`，控制訊息方塊的顯示方式。 您可以藉由檢查來判斷這些常數的數值`#define`WinUser.h 檔案中的陳述式。 因此您可能想要使用的計算機來予以新增，然後將轉換成十進位數字的值通常會顯示以十六進位、。 例如，如果您想要結合驚嘆號樣式常數`MB_ICONEXCLAMATION`0x00000030 和 是/無樣式`MB_YESNO`0x00000004，您可以將數字相加，並取得 0x00000034 或 52 結果的十進位。 雖然您可以直接使用十進位的結果，最好是將這些值宣告為應用程式中的常數，並將它們結合使用`Or`運算子。  
  
###### <a name="to-declare-constants-for-windows-api-calls"></a>若要宣告常數的 Windows API 呼叫  
  
1. 您要呼叫 Windows 函式，請參閱文件。 決定使用的常數名稱以及包含這些常數的數值的.h 檔案的名稱。  
  
2. 若要檢視標頭 (.h) 檔案的內容中使用文字編輯器，例如 [記事本]，並找出您正在使用的常數相關聯的值。 例如， `MessageBox` API 會使用常數`MB_ICONQUESTION`顯示訊息方塊中的問號。 定義`MB_ICONQUESTION`WinUser.h 中，而且會出現，如下所示：  
  
     `#define MB_ICONQUESTION             0x00000020L`  
  
3. 新增對等項目`Const`至您的類別或模組，讓您的應用程式可使用這些常數的陳述式。 例如：  
  
     [!code-vb[VbVbalrInterop#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#11)]  
  
###### <a name="to-call-the-dll-procedure"></a>若要呼叫的 DLL 程序  
  
1. 新增名為按鈕`Button1`啟動以您的專案，然後按兩下以檢視其程式碼。 會顯示為按鈕的事件處理常式。  
  
2. 將程式碼加入`Click`加入呼叫程序，並提供適當的引數的按鈕事件處理常式：  
  
     [!code-vb[VbVbalrInterop#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#12)]  
  
3. 按 F5 執行專案。 訊息方塊會顯示這兩 **[是]** 並**No**回應按鈕。 按一下其中一個。  
  
#### <a name="data-marshaling"></a>封送處理的資料  
 Visual Basic 會自動轉換參數和 Windows API 呼叫的傳回值的資料類型，但您可以使用`MarshalAs`屬性來明確地指定 API 的預期的 unmanaged 的資料類型。 如需有關 interop 封送處理的詳細資訊，請參閱[Interop 封送處理](../../../framework/interop/interop-marshaling.md)。  
  
###### <a name="to-use-declare-and-marshalas-in-an-api-call"></a>若要使用 Declare 與 MarshalAs API 呼叫  
  
1. 決定您想要呼叫，再加上其引數，資料類型的函式的名稱，並傳回值。  
  
2. 若要簡化存取權`MarshalAs`屬性，請將`Imports`陳述式的類別或模組，如下列範例所示的程式碼：  
  
     [!code-vb[VbVbalrInterop#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#13)]  
  
3. 將函式原型匯入的函式新增至類別或模組，您使用，並套用`MarshalAs`屬性至參數或傳回值。 在下列範例中，預期類型的 API 呼叫`void*`封送處理為`AsAny`:  
  
     [!code-vb[VbVbalrInterop#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#14)]  
  
## <a name="api-calls-using-dllimport"></a>API 呼叫使用 DllImport  
 `DllImport`屬性會提供 Dll 中呼叫函式，而不需要型別程式庫的第二種方式。 `DllImport` 大致上相當於使用`Declare`陳述式但可提供更充分掌控如何呼叫的函式。  
  
 您可以使用`DllImport`大部分的 Windows api 呼叫，只要呼叫是指共用 (有時也稱為*靜態*) 方法。 您無法使用需要類別的執行個體方法。 不同於`Declare`陳述式，`DllImport`呼叫不能使用`MarshalAs`屬性。  
  
#### <a name="to-call-a-windows-api-using-the-dllimport-attribute"></a>若要呼叫 Windows API 使用 DllImport 屬性  
  
1. 開啟新的 Windows 應用程式專案，依序按一下**的新**上**檔案**功能表，然後按一下**專案**。 [ **新增專案** ] 對話方塊隨即出現。  
  
2. 選取  **Windows 應用程式**從 Visual Basic 專案範本的清單。 新的專案會顯示。  
  
3. 新增名為按鈕`Button2`的啟動表單。  
  
4. 按兩下`Button2`開啟表單的程式碼檢視。  
  
5. 若要簡化存取權`DllImport`，新增`Imports`陳述式來啟動表單類別的程式碼頂端：  
  
     [!code-vb[VbVbalrInterop#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#13)]  
  
6. 宣告空函式前面`End Class`表單，和名稱的函式的陳述式`MoveFile`。  
  
7. 適用於`Public`並`Shared`的函式宣告和設定參數的修飾詞`MoveFile`根據 Windows API 函式會使用的引數：  
  
     [!code-vb[VbVbalrInterop#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#16)]  
  
     您的函式可以使用任何有效的程序名稱;`DllImport`屬性會指定在 DLL 中的名稱。 它也會處理參數封送處理的互通性和 API 所使用的傳回值，因此您可以選擇 Visual Studio 的資料類型，它們類似於的資料類型。  
  
8. 套用`DllImport`屬性為空白的函式。 第一個參數是包含您要呼叫的函式的 dll 的位置與名稱。 您不需要指定位於 Windows 系統目錄中檔案的路徑。 第二個參數是在 Windows API 中指定的函式名稱的具名引數。 在此範例中，`DllImport`屬性會強制執行呼叫`MoveFile`轉送至`MoveFileW`KERNEL32 中。DLL。 `MoveFileW`方法會將檔案複製從路徑`src`路徑`dst`。  
  
     [!code-vb[VbVbalrInterop#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#17)]  
  
9. 將程式碼加入`Button2_Click`事件處理常式呼叫的函式：  
  
     [!code-vb[VbVbalrInterop#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#18)]  
  
10. 建立名為 Test.txt 的檔案，並將它放在硬碟機 C:\Tmp 目錄中。 如有必要，請建立 Tmp 目錄。  
  
11. 請按 F5 啟動應用程式。 主要的表單隨即出現。  
  
12. 按一下  **Button2**。 如果可以移動檔案，則會顯示 「 已成功移動檔案 」 訊息。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Auto](../../../visual-basic/language-reference/modifiers/auto.md)
- [Alias](../../../visual-basic/language-reference/statements/alias-clause.md)
- [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)
- [在 Managed 程式碼中建立原型](../../../framework/interop/creating-prototypes-in-managed-code.md)
- [做為回呼方法，委派封送處理](../../../framework/interop/marshaling-a-delegate-as-a-callback-method.md)
