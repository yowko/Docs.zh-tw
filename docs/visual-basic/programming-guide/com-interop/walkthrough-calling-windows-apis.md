---
title: "Walkthrough: Calling Windows APIs (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "DLLs, calling"
  - "Windows API, walkthroughs"
  - "platform invoke, walkthroughs"
  - "API calls, walkthroughs [Visual Basic]"
  - "Windows API, calling"
  - "walkthroughs [Visual Basic], API calls"
  - "DllImport attribute, calling Windows API"
  - "Declare statement, declaring DLL functions"
ms.assetid: 9280ca96-7a93-47a3-8d01-6d01be0657cb
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 20
---
# Walkthrough: Calling Windows APIs (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Windows API 是屬於 Windows 作業系統一部分的動態連結程式庫 \(DLL\)。  當您無法自行寫入對等程序時，您就可使用它們來執行工作。  例如，Windows 會提供名為 `FlashWindowEx` 的函式，讓您將應用程式的標題列輪流顯示為淡色和深色。  
  
 在程式碼中使用 Windows API 的優點是可節省開發時間，因為它們包含數十種已撰寫且可立即使用的有用函式。  缺點是 Windows API 可能不易使用而且一出錯就非常嚴重。  
  
 Windows API 代表互通性的特定分類。  Windows API 不使用 Managed 程式碼、沒有內建型別程式庫，而且使用的資料型別也與 Visual Studio 的不同。  由於這些差異，也由於 Windows API 不是 COM 物件，因此 Windows API 與 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 之間是使用平台叫用或 PInvoke 來互通。  平台叫用是一種服務，可讓 Managed 程式碼呼叫在 DLL 中實作的 Unmanaged 函式。  如需詳細資訊，請參閱[使用 Unmanaged DLL 函式](../Topic/Consuming%20Unmanaged%20DLL%20Functions.md)。  使用 `Declare` 陳述式或將 `DllImport` 屬性套用至空白程序，即可在 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中使用 PInvoke。  
  
 Windows API 呼叫在過去是 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 程式設計的重要部分，但 [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong-md.md)] 就不太需要使用。  您應盡量使用 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 的 Managed 程式碼來執行工作，而不是使用 Window API 呼叫。  這個逐步解說會提供使用 Windows API 時所需的資訊。  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
## 使用 Declare 的 API 呼叫  
 最常呼叫 Windows API 的方法是使用 `Declare` 陳述式。  
  
#### 若要宣告 DLL 程序  
  
1.  決定要呼叫函式的名稱，同時決定其引數、引數型別、傳回值，以及包含它的 DLL 名稱和位置。  
  
    > [!NOTE]
    >  如需 Windows API 的完整資訊，請參閱 Platform SDK Windows API 中的 Win32 SDK 文件。  如需 Windows API 所用常數的詳細資訊，請檢視 Platform SDK 中的標頭檔，例如 Windows.h。  
  
2.  在 \[**檔案**\] 功能表中按一下 \[**新增**\]，接著按一下 \[**專案**\]，開啟一個新的 Windows 應用程式專案。  \[**新增專案**\] 對話方塊隨即出現。  
  
3.  在 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 專案範本清單中選取 \[**Windows 應用程式**\]。  接著會出現新專案。  
  
4.  將下列 `Declare` 函式加入至要在其中使用 DLL 的類別或模組：  
  
     [!code-vb[VbVbalrInterop#9](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_1.vb)]  
  
### Declare 陳述式的組成部分  
 `Declare` 陳述式包含下列項目。  
  
#### Auto 修飾詞  
 `Auto` 修飾詞會指示執行階段依 Common Language Runtime 規則 \(或在指定別名名稱時加以使用\) 以方法名稱為基礎轉換字串。  
  
#### Lib 和 Alias 關鍵字  
 跟在 `Function` 關鍵字後面的名稱是您的程式用於存取匯入函式的名稱。  這個名稱可以與您所呼叫函式的實際名稱相同，或是您也可以使用任何有效的程序名稱，然後使用 `Alias` 關鍵字指定您所呼叫函式的實際名稱。  
  
 指定 `Lib` 關鍵字後面跟著包含所呼叫函式之 DLL 的名稱和位置。  您不需要為位於 Windows 系統目錄中的檔案指定路徑。  
  
 如果正在呼叫的函式名稱不是有效的 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 程序名稱，或與應用程式中的其他項目名稱發生衝突，請使用 `Alias` 關鍵字。  `Alias` 表示正在呼叫之函式的真正名稱。  
  
#### 引數和資料型別宣告  
 宣告引數及其資料型別。  因為 Windows 使用的資料型別不等於 Visual Studio 資料型別，所以這部分十分有挑戰性。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 需執行許多工作，將引數轉換成相容的資料型別，此處理序名為「*封送處理*」\(Marshaling\)。  您可使用在 <xref:System.Runtime.InteropServices> 命名空間中定義的 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性，明確控制封送處理引數的方式。  
  
> [!NOTE]
>  舊版的 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 可讓您宣告參數 `As Any`，這表示可使用任何資料型別的資料。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 需要您將特定資料型別用於所有 `Declare` 陳述式。  
  
#### Windows API 常數  
 有些引數是常數的組合。  例如，逐步解說中的 `MessageBox` API 接受名為 `Typ` 的整數引數，用於控制訊息方塊的顯示方式。  您可以藉由檢查 WinUser.h 檔案中的 `#define` 陳述式，來判斷這些常數的數值。  數值通常是以十六進位顯示，因此您可能需要使用計算機，將這些數值相加，並轉換為十進位數。  例如，如果您要將驚嘆號樣式 `MB_ICONEXCLAMATION` 0x00000030 和「是\/否」樣式 `MB_YESNO` 0x00000004 的常數結合，則可將數字相加並得到結果 0x00000034，或是以十進位表示的 52。  雖然您可以直接使用十進位結果，但最好還是在應用程式中將這些值宣告為常數，並使用 `Or` 運算子加以組合。  
  
###### 若要宣告 Windows API 呼叫的常數  
  
1.  請參閱文件，以了解正在呼叫的 Windows 函式。  判斷所使用的常數名稱，以及含有這些常數之數值的 .h 檔案名稱。  
  
2.  使用記事本之類的文字編輯器來檢視標頭檔 \(.h\) 的內容，找出與所使用常數相關的值。  例如，`MessageBox` API 會使用常數 `MB_ICONQUESTION`，以便於訊息方塊中顯示問號。  `MB_ICONQUESTION` 在 WinUser.h 中的定義和樣子如下：  
  
     `#define MB_ICONQUESTION             0x00000020L`  
  
3.  在類別或模組中加入對等的 `Const` 陳述式，以便讓您的應用程式可使用這些常數。  例如：  
  
     [!code-vb[VbVbalrInterop#11](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_2.vb)]  
  
###### 若要呼叫 DLL 程序  
  
1.  將名為 `Button1` 的按鈕加入專案的啟動表單，然後按兩下來檢視其程式碼。  接著會顯示按鈕的事件處理常式。  
  
2.  在剛加入按鈕的 `Click` 事件處理常式中加入程式碼，以呼叫程序並提供適當引數：  
  
     [!code-vb[VbVbalrInterop#12](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_3.vb)]  
  
3.  按 F5 執行專案。  接著會顯示包含 \[**是**\] 和 \[**否**\] 回應按鈕的訊息方塊。  按一下其中一個按鈕。  
  
#### 資料封送處理  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會自動為 Windows API 呼叫轉換參數和傳回值的資料型別，但您可使用 `MarshalAs` 屬性，明確指定 API 預期使用的 Unmanaged 資料型別。  如需 Interop 封送處理的詳細資訊，請參閱 [Interop 封送處理](../Topic/Interop%20Marshaling.md)。  
  
###### 若要在 API 呼叫中使用 Declare 和 MarshalAs  
  
1.  判斷要呼叫函式的名稱、加上其引數、資料型別和傳回值。  
  
2.  為了簡化存取 `MarshalAs` 屬性，將 `Imports` 陳述式加到類別或模組的程式碼上方，如下列範例所示：  
  
     [!code-vb[VbVbalrInterop#13](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_4.vb)]  
  
3.  將匯入函式的函式原型加入至所使用的類別或模組，接著將 `MarshalAs` 屬性套用至參數或傳回值。  在下列範例中，API 呼叫預期會將 `void*` 型別封送處理為 `AsAny`：  
  
     [!code-vb[VbVbalrInterop#14](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_5.vb)]  
  
## 使用 DllImport 的 API 呼叫  
 `DllImport` 屬性會提供第二種方法，來呼叫沒有型別程式庫之 DLL 中的函式。  `DllImport` 大致上等於使用 `Declare` 陳述式，但會對呼叫函式的方式提供較多的控制。  
  
 您可在多數的 Windows API 呼叫中使用 `DllImport`，只要呼叫參考共用 \(有時稱為「*靜態*」\(Static\)\) 方法即可。  您不能使用需要類別執行個體的方法。  與 `Declare` 陳述式不同，`DllImport` 呼叫無法使用 `MarshalAs` 屬性。  
  
#### 若要使用 DllImport 屬性呼叫  
  
1.  在 \[**檔案**\] 功能表中按一下 \[**新增**\]，接著按一下 \[**專案**\]，開啟一個新的 Windows 應用程式專案。  \[**新增專案**\] 對話方塊隨即出現。  
  
2.  在 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 專案範本清單中選取 \[**Windows 應用程式**\]。  接著會出現新專案。  
  
3.  將名為 `Button2` 的按鈕加入啟動表單。  
  
4.  按兩下 `Button2` 以開啟表單的程式碼檢視。  
  
5.  為了簡化存取 `DllImport`，將 `Imports` 陳述式加入至啟動表單類別的程式碼上方：  
  
     [!code-vb[VbVbalrInterop#13](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_4.vb)]  
  
6.  在表單的 `End Class` 陳述式之前宣告空函式，並將函式命名為 `MoveFile`。  
  
7.  將 `Public` 和 `Shared` 修飾詞套用至函式宣告，並根據 Windows API 函式使用的引數設定 `MoveFile` 的參數：  
  
     [!code-vb[VbVbalrInterop#16](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_6.vb)]  
  
     您的函式可有任何有效的程序名稱，`DllImport` 屬性會在 DLL 中指定名稱。  它也會處理參數和傳回值的互通性封送處理，因此您可選擇與 API 所使用資料型別類似的 Visual Studio 資料型別。  
  
8.  將 `DllImport` 屬性套用至空函式。  第一個參數是包含要呼叫函式之 DLL 的名稱和位置。  您不需要為位於 Windows 系統目錄中的檔案指定路徑。  第二個參數是指定 Windows API 中函式名稱的具名引數。  在這個範例中，`DllImport` 屬性會強制將 `MoveFile` 的呼叫轉送至 KERNEL32.DLL 中的 `MoveFileW`。  `MoveFileW` 方法可將檔案從路徑 `src` 複製到路徑 `dst`。  
  
     [!code-vb[VbVbalrInterop#17](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_7.vb)]  
  
9. 將程式碼加入至 `Button2_Click` 事件處理常式來呼叫函式：  
  
     [!code-vb[VbVbalrInterop#18](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_8.vb)]  
  
10. 建立名為 Test.txt 的檔案，並將其置於硬碟上的 C:\\Tmp 目錄中。  視需要建立 Tmp 目錄。  
  
11. 請按 F5 啟動應用程式。  主表單隨即顯示。  
  
12. 按一下 \[**Button2**\]。  如果可移動檔案，就會顯示「已成功移動檔案」的訊息。  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)   
 [Auto](../../../visual-basic/language-reference/modifiers/auto.md)   
 [Alias](../../../visual-basic/language-reference/statements/alias-clause.md)   
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)   
 [在 Managed 程式碼中建立原型](../Topic/Creating%20Prototypes%20in%20Managed%20Code.md)   
 [做為回呼方法，委派封送處理](../Topic/Marshaling%20a%20Delegate%20as%20a%20Callback%20Method.md)