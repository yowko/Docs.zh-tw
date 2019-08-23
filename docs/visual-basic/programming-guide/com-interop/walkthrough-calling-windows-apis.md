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
# <a name="walkthrough-calling-windows-apis-visual-basic"></a>逐步解說：呼叫 Windows Api (Visual Basic)
Windows Api 是動態連結程式庫 (Dll), 屬於 Windows 作業系統的一部分。 當您很難以撰寫自己的對等程式時, 可以使用它們來執行工作。 例如, Windows 提供名為`FlashWindowEx`的函式, 可讓您讓應用程式的標題列在淺色與深色之間交替。  
  
 在您的程式碼中使用 Windows Api 的優點是可以節省開發時間, 因為它們包含數十個已撰寫並等候使用的實用函式。 缺點是, Windows Api 在發生錯誤時很容易使用和 unforgiving。  
  
 Windows Api 代表一種特殊的互通性分類。 Windows Api 不會使用 managed 程式碼、沒有內建類型程式庫, 以及使用與 Visual Studio 搭配使用的資料類型。 因為有這些差異, 而且因為 Windows Api 不是 COM 物件, 所以與 Windows Api 的互通性和 .NET Framework 是使用平台叫用或 PInvoke 來執行。 平台叫用是一項服務, 可讓 managed 程式碼呼叫在 Dll 中實作用的非受控函式。 如需詳細資訊, 請參閱[使用非受控 DLL](../../../framework/interop/consuming-unmanaged-dll-functions.md)函式。 您可以使用`Declare`語句, 或`DllImport`將屬性套用至空白程式, 以在 Visual Basic 中使用 PInvoke。  
  
 Windows API 呼叫是過去 Visual Basic 程式設計中很重要的一環, 但 Visual Basic .NET 時很少需要。 可能的話, 您應該使用 .NET Framework 的 managed 程式碼來執行工作, 而不是 Windows API 呼叫。 本逐步解說會針對需要使用 Windows Api 的情況提供相關資訊。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="api-calls-using-declare"></a>使用 Declare 的 API 呼叫  
 呼叫 Windows api 最常見的方式是使用`Declare`語句。  
  
### <a name="to-declare-a-dll-procedure"></a>若要宣告 DLL 程式  
  
1. 決定您想要呼叫的函式名稱, 加上其引數、引數類型和傳回值, 以及包含它的 DLL 名稱和位置。  
  
    > [!NOTE]
    > 如需 Windows Api 的完整資訊, 請參閱 Platform SDK Windows API 中的 Win32 SDK 檔。 如需 Windows Api 所使用之常數的詳細資訊, 請檢查包含在 Platform SDK 中的標頭檔 (例如 Windows .h)。  
  
2. 按一下 [檔案] 功能表上的 [**新增**],然後按一下 [**專案**], 以開啟新的 Windows 應用程式專案。 [ **新增專案** ] 對話方塊隨即出現。  
  
3. 從 Visual Basic 專案範本清單中選取 [ **Windows 應用程式**]。 隨即顯示新專案。  
  
4. 將下列`Declare`函數新增至您要使用 DLL 的類別或模組:  
  
     [!code-vb[VbVbalrInterop#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#9)]  
  
### <a name="parts-of-the-declare-statement"></a>Declare 語句的部分  
 `Declare`語句包含下列元素。  
  
#### <a name="auto-modifier"></a>Auto 修飾詞  
 `Auto`修飾詞會指示執行時間根據方法名稱, 依據通用語言執行時間規則 (如果有指定, 則為別名名稱) 來轉換字串。  
  
#### <a name="lib-and-alias-keywords"></a>Lib 和 Alias 關鍵字  
 `Function`關鍵字後面的名稱是您的程式用來存取匯入函式的名稱。 它可以與您所呼叫之函式的實際名稱相同, 或者您可以使用任何有效的程式名稱, 然後採用`Alias`關鍵字來指定您要呼叫之函式的實際名稱。  
  
 `Lib`指定關鍵字, 後面接著包含您要呼叫之函數的 DLL 名稱和位置。 您不需要指定位於 Windows 系統目錄中的檔案路徑。  
  
 如果您呼叫的函式名稱不是有效的 Visual Basic 程式名稱, 或是與應用程式中其他專案的名稱衝突, 請使用關鍵字。`Alias` `Alias`表示所呼叫之函式的真正名稱。  
  
#### <a name="argument-and-data-type-declarations"></a>引數和資料類型宣告  
 宣告引數及其資料類型。 這個部分可能相當困難, 因為 Windows 所使用的資料類型不會對應到 Visual Studio 的資料類型。 Visual Basic 藉由將引數轉換成相容的資料類型 (稱為*封送*處理的進程), 為您執行許多工作。 您可以使用<xref:System.Runtime.InteropServices.MarshalAsAttribute> <xref:System.Runtime.InteropServices>命名空間中定義的屬性, 明確控制引數的封送處理方式。  
  
> [!NOTE]
> 舊版的 Visual Basic 可讓您宣告參數`As Any`, 這表示可以使用任何資料類型的資料。 Visual Basic 要求您針對所有`Declare`語句使用特定的資料類型。  
  
#### <a name="windows-api-constants"></a>Windows API 常數  
 某些引數是常數的組合。 例如, 本逐步`MessageBox`解說中所顯示的 API 會接受名`Typ`為的整數引數, 以控制訊息框的顯示方式。 您可以檢查 WinUser 檔案中的`#define`語句, 判斷這些常數的數值。 數值通常會以十六進位顯示, 因此您可能會想要使用計算機來新增它們並轉換成 decimal。 例如, 如果您想要結合驚嘆號樣式`MB_ICONEXCLAMATION` 0x00000030 和 Yes/No 樣式`MB_YESNO` 0x00000004 的常數, 您可以加入數位並取得0x00000034 的結果, 或52的 decimal。 雖然您可以直接使用十進位結果, 但最好是將這些值宣告為應用程式中的常數, 並使用`Or`運算子加以結合。  
  
##### <a name="to-declare-constants-for-windows-api-calls"></a>若要宣告 Windows API 呼叫的常數  
  
1. 請參閱檔, 以瞭解您所呼叫的 Windows 函式。 判斷它所使用的常數名稱, 以及包含這些常數之數值的 .h 檔案名稱。  
  
2. 使用文字編輯器 (例如 [記事本]) 來查看標頭 (.h) 檔案的內容, 並尋找與您所使用之常數相關聯的值。 例如, `MessageBox` API 會使用常數`MB_ICONQUESTION` , 在訊息方塊中顯示問號。 的定義`MB_ICONQUESTION`位於 WinUser 中, 並顯示如下:  
  
     `#define MB_ICONQUESTION             0x00000020L`  
  
3. 將對`Const`等語句加入至您的類別或模組, 讓這些常數可供您的應用程式使用。 例如：  
  
     [!code-vb[VbVbalrInterop#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#11)]  
  
###### <a name="to-call-the-dll-procedure"></a>呼叫 DLL 程式  
  
1. 將名`Button1`為的按鈕新增至專案的啟動表單, 然後按兩下以查看其程式碼。 隨即顯示按鈕的事件處理常式。  
  
2. 將程式碼加入`Click`至您所加入按鈕的事件處理常式中, 以呼叫程式並提供適當的引數:  
  
     [!code-vb[VbVbalrInterop#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#12)]  
  
3. 按 F5 執行專案。 訊息方塊會顯示 [**是]** 和 [**沒有**回應] 按鈕。 按一下其中一個。  
  
#### <a name="data-marshaling"></a>資料封送處理  
 Visual Basic 會自動轉換參數的資料類型和 Windows API 呼叫的傳回值, 但您可以使用`MarshalAs`屬性來明確指定 API 預期的非受控資料類型。 如需 interop 封送處理的詳細資訊, 請參閱[Interop 封送處理](../../../framework/interop/interop-marshaling.md)。  
  
##### <a name="to-use-declare-and-marshalas-in-an-api-call"></a>在 API 呼叫中使用 Declare 和 MarshalAs  
  
1. 判斷您想要呼叫的函式名稱, 加上其引數、資料類型和傳回值。  
  
2. 若要簡化屬性的`MarshalAs`存取, 請在`Imports`類別或模組的程式碼頂端加入語句, 如下列範例所示:  
  
     [!code-vb[VbVbalrInterop#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#13)]  
  
3. 將匯入函式的函式原型新增至您所使用的類別或模組, 並`MarshalAs`將屬性套用至參數或傳回值。 在下列範例中, 預期類型`void*`的 API 呼叫會封送處理為: `AsAny`  
  
     [!code-vb[VbVbalrInterop#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#14)]  
  
## <a name="api-calls-using-dllimport"></a>使用 DllImport 的 API 呼叫  
 `DllImport`屬性提供第二種方式來呼叫 dll 中的函式, 而不使用類型程式庫。 `DllImport`大致上相當於使用`Declare`語句, 但可讓您更充分掌控函數的呼叫方式。  
  
 只要呼叫是`DllImport`指共用 (有時稱為*靜態*) 方法, 您就可以使用搭配大部分的 Windows API 呼叫。 您不能使用需要類別實例的方法。 不同`Declare` `DllImport`于語句`MarshalAs` , 呼叫不能使用屬性。  
  
### <a name="to-call-a-windows-api-using-the-dllimport-attribute"></a>使用 DllImport 屬性呼叫 Windows API  
  
1. 按一下 [檔案] 功能表上的 [**新增**],然後按一下 [**專案**], 以開啟新的 Windows 應用程式專案。 [ **新增專案** ] 對話方塊隨即出現。  
  
2. 從 Visual Basic 專案範本清單中選取 [ **Windows 應用程式**]。 隨即顯示新專案。  
  
3. 將名`Button2`為的按鈕新增至 [啟動表單]。  
  
4. `Button2`按兩下以開啟表單的程式碼視圖。  
  
5. 若要簡化對`DllImport`的存取, `Imports`請將語句新增至啟動表單類別的程式碼頂端:  
  
     [!code-vb[VbVbalrInterop#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#13)]  
  
6. 在表單的`End Class`語句前面宣告空白函式, 並`MoveFile`將函式命名為。  
  
7. `Public`將和`Shared`修飾詞套用至函式宣告, 並根據 Windows `MoveFile` API 函式所使用的引數設定的參數:  
  
     [!code-vb[VbVbalrInterop#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#16)]  
  
     您的函式可以有任何有效的程式名稱;`DllImport`屬性會指定 DLL 中的名稱。 它也會處理參數和傳回值的互通性封送處理, 因此您可以選擇與 API 所使用的資料類型 Visual Studio 的資料類型。  
  
8. `DllImport`將屬性套用至空白函數。 第一個參數是包含您要呼叫之函式的 DLL 名稱和位置。 您不需要指定位於 Windows 系統目錄中的檔案路徑。 第二個參數是具名引數, 可指定 Windows API 中的函式名稱。 在此範例中, `DllImport`屬性會強制將`MoveFile`呼叫轉送到`MoveFileW` kernel32.dll 中的。URLMON.DLL. 方法會將檔案從路徑`src`複製到路徑`dst`。 `MoveFileW`  
  
     [!code-vb[VbVbalrInterop#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#17)]  
  
9. 將程式碼`Button2_Click`加入至事件處理常式以呼叫函數:  
  
     [!code-vb[VbVbalrInterop#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#18)]  
  
10. 建立名為 test.txt 的檔案, 並將它放在硬碟的 C:\Tmp 目錄中。 視需要建立 Tmp 目錄。  
  
11. 請按 F5 啟動應用程式。 主要表單隨即出現。  
  
12. 按一下 [ **Button2**]。 如果可以移動檔案, 就會顯示「檔案已成功移動」訊息。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Auto](../../../visual-basic/language-reference/modifiers/auto.md)
- [Alias](../../../visual-basic/language-reference/statements/alias-clause.md)
- [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)
- [在 Managed 程式碼中建立原型](../../../framework/interop/creating-prototypes-in-managed-code.md)
- [做為回呼方法，委派封送處理](../../../framework/interop/marshaling-a-delegate-as-a-callback-method.md)
