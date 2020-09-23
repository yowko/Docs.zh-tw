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
# <a name="walkthrough-calling-windows-apis-visual-basic"></a>逐步解說：呼叫 Windows API (Visual Basic)

Windows Api 是 (Dll) 的動態連結程式庫，這是 Windows 作業系統的一部分。 當難以撰寫您自己的對等程式時，您可以使用它們來執行工作。 例如，Windows 提供名為的函 `FlashWindowEx` 式，可讓您讓應用程式的標題列在淺色和深色陰影之間交替。  
  
 在程式碼中使用 Windows Api 的優點是，它們可以節省開發時間，因為它們包含許多已撰寫並等候使用的實用功能。 缺點是 Windows Api 可能難以使用，並在發生問題時 unforgiving。  
  
 Windows Api 代表互通性的特殊類別。 Windows Api 不會使用 managed 程式碼、沒有內建類型程式庫，而且使用的資料類型與 Visual Studio 所用的不同。 由於這些差異，而且 Windows Api 不是 COM 物件，因此與 Windows Api 的互通性和 .NET Framework 是使用平台叫用（或 PInvoke）來執行。 平台叫用是一種服務，可讓 managed 程式碼呼叫 Dll 中所執行的非受控函式。 如需詳細資訊，請參閱 [使用非受控 DLL](../../../framework/interop/consuming-unmanaged-dll-functions.md)函式。 您可以使用 `Declare` 語句或將屬性套用至空白程式，在 Visual Basic 中使用 PInvoke `DllImport` 。  
  
 Windows API 呼叫在過去 Visual Basic 程式設計中是很重要的一部分，但是在 Visual Basic .NET 中很少需要。 可能的話，您應該使用 .NET Framework 中的 managed 程式碼來執行工作，而不是使用 Windows API 呼叫。 本逐步解說提供在需要使用 Windows Api 的情況下的資訊。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="api-calls-using-declare"></a>使用 Declare 的 API 呼叫  

 呼叫 Windows Api 最常見的方法是使用 `Declare` 語句。  
  
### <a name="to-declare-a-dll-procedure"></a>宣告 DLL 程式  
  
1. 判斷您想要呼叫之函式的名稱，加上其引數、引數型別和傳回值，以及包含該函式之 DLL 的名稱和位置。  
  
    > [!NOTE]
    > 如需 Windows Api 的完整資訊，請參閱 Platform SDK Windows API 中的 Win32 SDK 檔。 如需有關 Windows Api 使用之常數的詳細資訊，請檢查包含在 Platform SDK 中的標頭檔，例如 Windows .h。  
  
2. **在 [檔案**] 功能表上按一下 [**新增**]，然後按一下 [**專案**]，以開啟新的 Windows 應用程式專案。 [新增專案]  對話方塊隨即出現。  
  
3. 從 Visual Basic 專案範本清單中選取 [ **Windows 應用程式** ]。 新的專案隨即顯示。  
  
4. 將下列函式新增 `Declare` 至您要在其中使用 DLL 的類別或模組：  
  
     [!code-vb[VbVbalrInterop#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#9)]  
  
### <a name="parts-of-the-declare-statement"></a>Declare 語句的元件  

 `Declare`語句包含下列元素。  
  
#### <a name="auto-modifier"></a>Auto 修飾詞  

 此 `Auto` 修飾詞會根據 common language runtime 規則 (或別名名稱（如果指定) ），指示執行時間根據方法名稱來轉換字串。  
  
#### <a name="lib-and-alias-keywords"></a>Lib 和 Alias 關鍵字  

 關鍵字後面的名稱 `Function` 是程式用來存取匯入函式的名稱。 它可以與您所呼叫之函式的真實名稱相同，或者您可以使用任何有效的程式名稱，然後使用 `Alias` 關鍵字來指定您要呼叫之函式的真實名稱。  
  
 指定 `Lib` 關鍵字，後面接著包含您要呼叫之函式的 DLL 名稱和位置。 您不需要為位於 Windows 系統目錄中的檔案指定路徑。  
  
 `Alias`如果您要呼叫的函式名稱不是有效的 Visual Basic 程式名稱，或與應用程式中其他專案的名稱衝突，請使用關鍵字。 `Alias` 指出所呼叫之函式的真實名稱。  
  
#### <a name="argument-and-data-type-declarations"></a>引數和資料類型宣告  

 宣告引數和其資料類型。 這個部分可能會很困難，因為 Windows 使用的資料類型不會對應至 Visual Studio 資料類型。 Visual Basic 藉由將引數轉換成相容的資料類型（稱為 *封送*處理的程式），來為您執行許多工作。 您可以使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 命名空間中定義的屬性，明確控制引數的封送處理方式 <xref:System.Runtime.InteropServices> 。  
  
> [!NOTE]
> 舊版 Visual Basic 允許您宣告參數 `As Any` ，表示可以使用任何資料類型的資料。 Visual Basic 需要針對所有語句使用特定的資料類型 `Declare` 。  
  
#### <a name="windows-api-constants"></a>Windows API 常數  

 某些引數是常數的組合。 例如， `MessageBox` 在此逐步解說中所顯示的 API 會接受一個稱為的整數引數 `Typ` ，以控制訊息框的顯示方式。 您可以檢查 WinUser 檔案中的語句來判斷這些常數的數值 `#define` 。 數值通常會以十六進位顯示，因此您可能會想要使用計算機來新增它們並轉換成 decimal。 例如，如果您想要結合驚嘆號樣式0x00000030 的常數和 [ `MB_ICONEXCLAMATION` 是]/[否] 樣式 `MB_YESNO` 的0x00000004，您可以加入數位並取得0x00000034 的結果，或 52 decimal。 雖然您可以直接使用 decimal 結果，但最好是將這些值宣告為應用程式中的常數，並使用運算子將它們合併 `Or` 。  
  
##### <a name="to-declare-constants-for-windows-api-calls"></a>宣告 Windows API 呼叫的常數  
  
1. 請參閱您所呼叫 Windows 函式的檔。 判斷其所使用的常數名稱，以及包含這些常數數值的 .h 檔案名。  
  
2. 使用文字編輯器（例如 [記事本]）來查看標頭 ( .h) 檔案的內容，並尋找與您正在使用之常數相關聯的值。 例如，API 會 `MessageBox` 使用常數 `MB_ICONQUESTION` 在訊息方塊中顯示問號。 的定義位於 `MB_ICONQUESTION` WinUser 中，並顯示如下：  
  
     `#define MB_ICONQUESTION             0x00000020L`  
  
3. 將對等 `Const` 語句新增至您的類別或模組，以將這些常數提供給您的應用程式使用。 例如：  
  
     [!code-vb[VbVbalrInterop#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#11)]  
  
###### <a name="to-call-the-dll-procedure"></a>呼叫 DLL 程式  
  
1. 將名為的按鈕新增 `Button1` 至專案的啟動表單，然後按兩下以查看其程式碼。 按鈕的事件處理常式隨即顯示。  
  
2. 將程式碼加入至 `Click` 您所加入之按鈕的事件處理常式，以呼叫程式並提供適當的引數：  
  
     [!code-vb[VbVbalrInterop#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#12)]  
  
3. 按下 F5 來執行專案。 訊息方塊會顯示 [ **是]** 和 [ **沒有** 回應] 按鈕。 按一下其中一個。  
  
#### <a name="data-marshaling"></a>資料封送處理  

 Visual Basic 會自動轉換 Windows API 呼叫的參數和傳回值的資料類型，但您可以使用 `MarshalAs` 屬性來明確指定 API 預期的非受控資料類型。 如需有關 interop 封送處理的詳細資訊，請參閱 [Interop 封送處理](../../../framework/interop/interop-marshaling.md)。  
  
##### <a name="to-use-declare-and-marshalas-in-an-api-call"></a>在 API 呼叫中使用 Declare 和 MarshalAs  
  
1. 判斷您想要呼叫之函式的名稱，加上其引數、資料類型和傳回值。  
  
2. 若要簡化對屬性的存取 `MarshalAs` ，請將 `Imports` 語句加入至類別或模組的程式碼頂端，如下列範例所示：  
  
     [!code-vb[VbVbalrInterop#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#13)]  
  
3. 將匯入函式的函式原型新增至您所使用的類別或模組，然後將 `MarshalAs` 屬性套用至參數或傳回值。 在下列範例中，需要類型的 API 呼叫 `void*` 封送處理為 `AsAny` ：  
  
     [!code-vb[VbVbalrInterop#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#14)]  
  
## <a name="api-calls-using-dllimport"></a>使用 DllImport 的 API 呼叫  

 `DllImport`屬性提供的第二種方式是在沒有類型程式庫的 dll 中呼叫函式。 `DllImport` 大致上相當於使用 `Declare` 語句，但可讓您更充分掌控函數的呼叫方式。  
  
 `DllImport`只要呼叫參考共用 (（有時稱為*靜態*) 方法），就可以使用與大部分的 Windows API 呼叫。 您無法使用需要類別實例的方法。 不同 `Declare` 于語句， `DllImport` 呼叫不能使用 `MarshalAs` 屬性。  
  
### <a name="to-call-a-windows-api-using-the-dllimport-attribute"></a>使用 DllImport 屬性呼叫 Windows API  
  
1. **在 [檔案**] 功能表上按一下 [**新增**]，然後按一下 [**專案**]，以開啟新的 Windows 應用程式專案。 [新增專案]  對話方塊隨即出現。  
  
2. 從 Visual Basic 專案範本清單中選取 [ **Windows 應用程式** ]。 新的專案隨即顯示。  
  
3. 將名為的按鈕加入 `Button2` 至啟動表單。  
  
4. 按兩下 `Button2` 以開啟表單的程式碼視圖。  
  
5. 若要簡化 `DllImport` 的存取，請將 `Imports` 語句加入至 startup form 類別的程式碼頂端：  
  
     [!code-vb[VbVbalrInterop#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#13)]  
  
6. 在表單的語句前面宣告空的函式 `End Class` ，並為函數命名 `MoveFile` 。  
  
7. 將和修飾詞套用 `Public` `Shared` 至函式宣告，並 `MoveFile` 根據 Windows API 函數使用的引數來設定參數：  
  
     [!code-vb[VbVbalrInterop#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#16)]  
  
     您的函式可以有任何有效的程式名稱; `DllImport` 屬性會在 DLL 中指定名稱。 它也會處理參數和傳回值的互通性封送處理，因此您可以選擇與 API 使用的資料類型類似的 Visual Studio 資料類型。  
  
8. 將 `DllImport` 屬性套用至空白函數。 第一個參數是 DLL 的名稱和位置，其中包含您要呼叫的函式。 您不需要為位於 Windows 系統目錄中的檔案指定路徑。 第二個參數是具名引數，可指定 Windows API 中的函式名稱。 在此範例中， `DllImport` 屬性會強制將呼叫 `MoveFile` 轉送至 `MoveFileW` KERNEL32.DLL 中的。 `MoveFileW`方法會將檔案從路徑複製 `src` 到路徑 `dst` 。  
  
     [!code-vb[VbVbalrInterop#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#17)]  
  
9. 將程式碼加入至 `Button2_Click` 事件處理常式，以呼叫函數：  
  
     [!code-vb[VbVbalrInterop#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#18)]  
  
10. 建立名為 Test.txt 的檔案，並將它放在硬碟的 C:\Tmp 目錄中。 如有必要，請建立 Tmp 目錄。  
  
11. 請按 F5 啟動應用程式。 主要表單隨即出現。  
  
12. 按一下 [ **Button2**]。 如果可以移動檔案，則會顯示「檔案已成功移動」訊息。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Declare Statement](../../language-reference/statements/declare-statement.md)
- [Auto](../../language-reference/modifiers/auto.md)
- [別名](../../language-reference/statements/alias-clause.md)
- [COM Interop](index.md)
- [在 Managed 程式碼中建立原型](../../../framework/interop/creating-prototypes-in-managed-code.md)
- [做為回呼方法，委派封送處理](../../../framework/interop/marshaling-a-delegate-as-a-callback-method.md)
