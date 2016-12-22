---
title: "Constants and Enumerations (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "enumerations [Visual Basic]"
  - "constants"
  - "constants, list of"
ms.assetid: 309c0ad5-83e4-4f96-99ea-83cd95107417
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Constants and Enumerations (Visual Basic)
[!INCLUDE[vs2017banner](../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 提供一些預先定義的常數和列舉型別供開發人員使用。  常數會儲存在應用程式的執行過程中仍為常數的值。  列舉型別提供使用相關常數組和建立常數值與名稱間關聯的便利方法。  
  
## 常數  
  
### 條件式編譯的常數  
 下表列出了可用於條件式編譯的預先定義常數。  
  
|||  
|-|-|  
|**常數**|**描述**|  
|`CONFIG`|字串，對應至 \[**組態管理員**\] 中 \[**使用中的方案組態**\] 方塊的目前設定。|  
|`DEBUG`|`Boolean` 值，可以在 \[**專案屬性**\] 對話方塊中設定。  依預設，專案的 \[偵錯\] 組態可定義 `DEBUG` 方式。  定義 `DEBUG` 方式後，<xref:System.Diagnostics.Debug> 類別方法 \(Class Method\) 會產生輸出到 \[**輸出**\] 視窗。  如果沒有定義，<xref:System.Diagnostics.Debug> 類別方法就不會進行編譯，也不會產生 Debug 輸出。|  
|`TARGET`|字串，表示專案的輸出型別或命令列 **\/target** 選項。  `TARGET` 的可能值為：<br /><br /> -   用於 Windows 應用程式 "winexe"。<br />-   用於主控台應用程式的 "exe"。<br />-   用於類別庫的 "library"。<br />-   用於模組 "module"。<br />-   **\/target** 選項可於 [!INCLUDE[vsprvs](../../csharp/includes/vsprvs_md.md)] 整合式開發環境中設定。  如需詳細資訊，請參閱 [\/target](../../visual-basic/reference/command-line-compiler/target.md)。|  
|`TRACE`|`Boolean` 值，可以在 \[**專案屬性**\] 對話方塊中設定。  依預設，專案的所有組態可定義 `TRACE` 方式。  定義 `TRACE` 方式後，<xref:System.Diagnostics.Trace> 類別方法 \(Class Method\) 會產生輸出到 \[**輸出**\] 視窗。  如果沒有定義，<xref:System.Diagnostics.Trace> 類別方法就不會進行編譯，也不會產生 `Trace` 輸出。|  
|`VBC_VER`|此號碼代表 [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 版本，其格式為 *major*.*minor*。  [!INCLUDE[vbprvblong](../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)] 的版本號碼為 8.0。|  
  
### 列印和顯示常數  
 當呼叫列印和顯示函式時，您可在程式碼中使用下列常數來取代實際值。  
  
|||  
|-|-|  
|**常數**|**描述**|  
|`vbCrLf`|歸位\/換行字元 \(Carriage Return\/Line Feed\) 組合。|  
|`vbCr`|歸位字元。|  
|`vbLf`|換行字元。|  
|`vbNewLine`|新行字元 \(Newline Character\)。|  
|`vbNullChar`|Null 字元。|  
|`vbNullString`|與長度為零的字串 \(""\) 不同；用來呼叫外部程序。|  
|`vbObjectError`|錯誤代碼。  使用者定義錯誤代碼應大於這個值。  例如：<br /><br /> `Err.Raise(Number) = vbObjectError + 1000`|  
|`vbTab`|定位字元。|  
|`vbBack`|退格鍵 \(Backspace\)。|  
|`vbFormFeed`|Microsoft Windows 不適用。|  
|`vbVerticalTab`|在 Microsoft Windows 中的作用不大。|  
  
## 列舉  
 下表列出並描述 [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 所提供的列舉型別。  
  
|||  
|-|-|  
|列舉|描述|  
|<xref:Microsoft.VisualBasic.AppWinStyle>|指出呼叫 <xref:Microsoft.VisualBasic.Interaction.Shell%2A> 函式時，被叫用之程式所使用的視窗樣式。|  
|<xref:Microsoft.VisualBasic.AudioPlayMode>|指示在呼叫音效方法時要如何播放聲音。|  
|<xref:Microsoft.VisualBasic.ApplicationServices.BuiltInRole>|指示在呼叫 <xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A> 方法時，要檢查的角色類型。|  
|<xref:Microsoft.VisualBasic.CallType>|表示呼叫 <xref:Microsoft.VisualBasic.Interaction.CallByName%2A> 函式時所叫用的程序類型。|  
|<xref:Microsoft.VisualBasic.CompareMethod>|指出在呼叫比較函式時字串的比較方式。|  
|<xref:Microsoft.VisualBasic.DateFormat>|指出在呼叫 <xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A> 函式時的日期顯示方式。|  
|<xref:Microsoft.VisualBasic.DateInterval>|指出在呼叫日期相關的函式時，判斷和格式化日期間隔的方式。|  
|<xref:Microsoft.VisualBasic.FileIO.DeleteDirectoryOption>|指定如果要刪除的目錄內包含檔案或目錄時，應該要如何處理。|  
|<xref:Microsoft.VisualBasic.DueDate>|指出呼叫帳務處理方法時的付款到期日。|  
|<xref:Microsoft.VisualBasic.FileIO.FieldType>|指出文字欄位是以分隔符號分隔還是固定寬度的。|  
|<xref:Microsoft.VisualBasic.FileAttribute>|指出在呼叫檔案存取函式時所要使用的檔案屬性 \(Attribute\)。|  
|<xref:Microsoft.VisualBasic.FirstDayOfWeek>|指出在呼叫日期相關的函式時，哪天是一週的第一天。|  
|<xref:Microsoft.VisualBasic.FirstWeekOfYear>|指出在呼叫日期相關函式時，哪一週是一年的第一週。|  
|<xref:Microsoft.VisualBasic.MsgBoxResult>|指出在訊息方塊中按下的按鈕，並由 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 函式傳回相關資料。|  
|<xref:Microsoft.VisualBasic.MsgBoxStyle>|指出在呼叫 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 函式時所要顯示的按鈕。|  
|<xref:Microsoft.VisualBasic.OpenAccess>|表示在呼叫檔案存取函式時，要如何開啟檔案。|  
|<xref:Microsoft.VisualBasic.OpenMode>|表示在呼叫檔案存取函式時，要如何開啟檔案。|  
|<xref:Microsoft.VisualBasic.OpenShare>|表示在呼叫檔案存取函式時，要如何開啟檔案。|  
|<xref:Microsoft.VisualBasic.FileIO.RecycleOption>|指定檔案要永久刪除或放在 \[資源回收筒\] 中。|  
|<xref:Microsoft.VisualBasic.FileIO.SearchOption>|指定是否要搜尋全部或僅搜尋最上層目錄。|  
|<xref:Microsoft.VisualBasic.TriState>|表示布林值 \(`Boolean`\)，或者在呼叫數字格式的函式時是否使用預設值。|  
|<xref:Microsoft.VisualBasic.FileIO.UICancelOption>|指定當使用者於作業期間按下 \[**取消**\] 時，所要完成的工作。|  
|<xref:Microsoft.VisualBasic.FileIO.UIOption>|指定在複製、刪除或移動檔案或目錄時，是否要顯示進度對話方塊。|  
|<xref:Microsoft.VisualBasic.VariantType>|指出 Variant 物件的型別，並由 <xref:Microsoft.VisualBasic.Information.VarType%2A> 函式傳回相關資料。|  
|<xref:Microsoft.VisualBasic.VbStrConv>|指出在呼叫 <xref:Microsoft.VisualBasic.Strings.StrConv%2A> 函式時要執行的轉換類型。|  
  
## 請參閱  
 [Visual Basic Language Reference](../../visual-basic/language-reference/index.md)   
 [Visual Basic](../../visual-basic/index.md)   
 [Constants Overview](../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)   
 [Enumerations Overview](../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)