---
title: 常數和列舉
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- constants [Visual Basic]
- constants [Visual Basic], list of
ms.assetid: 309c0ad5-83e4-4f96-99ea-83cd95107417
ms.openlocfilehash: 60cd1ddac9bca685ddc5778e7d289710245a183e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374482"
---
# <a name="constants-and-enumerations-visual-basic"></a>常數和列舉類型 (Visual Basic)

Visual Basic 為開發人員提供許多預先定義的常數和列舉。 常數會儲存在應用程式執行期間保持不變的值。 列舉提供使用相關常數組和建立常數值與名稱之關聯的便利方法。  
  
## <a name="constants"></a>常數  
  
### <a name="conditional-compilation-constants"></a>條件式編譯常數  

 下表列出適用于條件式編譯的預先定義常數。  
  
|**常數**|**說明**|  
|---|---|  
|`CONFIG`|字串，對應至**Configuration Manager**中 [使用中的**方案**設定] 方塊的目前設定。|  
|`DEBUG`|`Boolean`可以在 [**專案屬性**] 對話方塊中設定的值。 根據預設，專案的 Debug 設定會定義 `DEBUG` 。 當 `DEBUG` 定義時， <xref:System.Diagnostics.Debug> 類別方法會將輸出產生至 [**輸出**] 視窗。 未定義時，不會 <xref:System.Diagnostics.Debug> 編譯類別方法，也不會產生任何 Debug 輸出。|  
|`TARGET`|字串，代表專案的輸出類型或命令列**目標**選項的設定。 的可能值 `TARGET` 為：<br /><br /> -適用于 Windows 應用程式的 "winexe"。<br />-"exe" 代表主控台應用程式。<br />-類別庫的「程式庫」。<br />-模組的「模組」。<br />-**目標**選項可在 Visual Studio 整合式開發環境中設定。 如需詳細資訊，請參閱[-target （Visual Basic）](../reference/command-line-compiler/target.md)。|  
|`TRACE`|`Boolean`可以在 [**專案屬性**] 對話方塊中設定的值。 根據預設，專案的所有設定都會定義 `TRACE` 。 當 `TRACE` 定義時， <xref:System.Diagnostics.Trace> 類別方法會將輸出產生至 [**輸出**] 視窗。 未定義時，不會 <xref:System.Diagnostics.Trace> 編譯類別方法，也不 `Trace` 會產生任何輸出。|  
|`VBC_VER`|代表 Visual Basic 版本的數位（在*主要*中）。*次要*格式。|  
  
### <a name="print-and-display-constants"></a>列印和顯示常數  

 當您呼叫 print 和 display 函式時，您可以在程式碼中使用下列常數來取代實際的值。  
  
|**常數**|**說明**|  
|---|---|  
|`vbCrLf`|回車/換行字元組合。|  
|`vbCr`|回車符。|  
|`vbLf`|換行字元。|  
|`vbNewLine`|換行字元。|  
|`vbNullChar`|Null 字元。|  
|`vbNullString`|不是與長度為零的字串（""）;用於呼叫外部程式。|  
|`vbObjectError`|錯誤號碼。 使用者定義錯誤代碼應大於這個值。 例如：<br /><br /> `Err.Raise(Number) = vbObjectError + 1000`|  
|`vbTab`|Tab 字元。|  
|`vbBack`|倒退鍵字元。|  
|`vbFormFeed`|未在 Microsoft Windows 中使用。|  
|`vbVerticalTab`|不適用於 Microsoft Windows。|  
  
## <a name="enumerations"></a>列舉  

 下表列出並描述 Visual Basic 所提供的列舉。  
  
|列舉型別|Description|  
|---|---|  
|<xref:Microsoft.VisualBasic.AppWinStyle>|指出呼叫 <xref:Microsoft.VisualBasic.Interaction.Shell%2A> 函式時，被叫用之程式所使用的視窗樣式。|  
|<xref:Microsoft.VisualBasic.AudioPlayMode>|指示在呼叫音效方法時要如何播放聲音。|  
|<xref:Microsoft.VisualBasic.ApplicationServices.BuiltInRole>|指示在呼叫 <xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A> 方法時，要檢查的角色類型。|  
|<xref:Microsoft.VisualBasic.CallType>|表示呼叫 <xref:Microsoft.VisualBasic.Interaction.CallByName%2A> 函式時所叫用的程序類型。|  
|<xref:Microsoft.VisualBasic.CompareMethod>|指出在呼叫比較函式時字串的比較方式。|  
|<xref:Microsoft.VisualBasic.DateFormat>|指出在呼叫 <xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A> 函式時的日期顯示方式。|  
|<xref:Microsoft.VisualBasic.DateInterval>|指示呼叫日期相關函式時，如何決定日期間隔並將其格式化。|  
|<xref:Microsoft.VisualBasic.FileIO.DeleteDirectoryOption>|指定如果要刪除的目錄內包含檔案或目錄時，應該要如何處理。|  
|<xref:Microsoft.VisualBasic.DueDate>|指出呼叫帳務處理方法時的付款到期日。|  
|<xref:Microsoft.VisualBasic.FileIO.FieldType>|指出文字欄位是分隔的，還是固定寬度。|  
|<xref:Microsoft.VisualBasic.FileAttribute>|指出在呼叫檔案存取函式時所要使用的檔案屬性 (Attribute)。|  
|<xref:Microsoft.VisualBasic.FirstDayOfWeek>|指出在呼叫日期相關的函式時，哪天是一週的第一天。|  
|<xref:Microsoft.VisualBasic.FirstWeekOfYear>|指出在呼叫日期相關函式時，哪一週是一年的第一週。|  
|<xref:Microsoft.VisualBasic.MsgBoxResult>|指出訊息方塊上按下了哪個按鈕，由 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 函式傳回。|  
|<xref:Microsoft.VisualBasic.MsgBoxStyle>|表示呼叫 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 函式時要顯示的按鈕。|  
|<xref:Microsoft.VisualBasic.OpenAccess>|表示在呼叫檔案存取函式時，要如何開啟檔案。|  
|<xref:Microsoft.VisualBasic.OpenMode>|表示在呼叫檔案存取函式時，要如何開啟檔案。|  
|<xref:Microsoft.VisualBasic.OpenShare>|表示在呼叫檔案存取函式時，要如何開啟檔案。|  
|<xref:Microsoft.VisualBasic.FileIO.RecycleOption>|指定檔案要永久刪除或放在 [資源回收筒] 中。|  
|<xref:Microsoft.VisualBasic.FileIO.SearchOption>|指定是否要搜尋全部或僅搜尋最上層目錄。|  
|<xref:Microsoft.VisualBasic.TriState>|表示 `Boolean` 值，或在呼叫數位格式函數時是否應該使用預設值。|  
|<xref:Microsoft.VisualBasic.FileIO.UICancelOption>|指定當使用者在作業期間按一下 [**取消**] 時應該執行的動作。|  
|<xref:Microsoft.VisualBasic.FileIO.UIOption>|指定在複製、刪除或移動檔案或目錄時，是否要顯示進度對話方塊。|  
|<xref:Microsoft.VisualBasic.VariantType>|指出 Variant 物件的型別，並由 <xref:Microsoft.VisualBasic.Information.VarType%2A> 函式傳回相關資料。|  
|<xref:Microsoft.VisualBasic.VbStrConv>|表示呼叫 <xref:Microsoft.VisualBasic.Strings.StrConv%2A> 函式時要執行的轉換類型。|  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 語言參考](index.md)
- [常數的概觀](../programming-guide/language-features/constants-enums/constants-overview.md)
- [列舉的概觀](../programming-guide/language-features/constants-enums/enumerations-overview.md)
