---
title: 常數和列舉類型 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- enumerations [Visual Basic]
- constants [Visual Basic]
- constants [Visual Basic], list of
ms.assetid: 309c0ad5-83e4-4f96-99ea-83cd95107417
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: da42d58190e8069154cd8383cf0a87e0b19f5ae4
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="constants-and-enumerations-visual-basic"></a>常數和列舉類型 (Visual Basic)
Visual Basic 提供了一些預先定義的常數和列舉型別供開發人員。 常數用來儲存應用程式的執行過程中維持的值。 列舉提供使用相關常數組和建立常數值與名稱之關聯的便利方法。  
  
## <a name="constants"></a>常數  
  
### <a name="conditional-compilation-constants"></a>條件式編譯常數  
 下表列出可用於條件式編譯的預先定義的常數。  
  
|**常數**|**描述**|  
|---|---|  
|`CONFIG`|對應至的目前設定的字串**現用方案組態**方塊中**Configuration Manager**。|  
|`DEBUG`|A`Boolean`值可在設定**專案屬性** 對話方塊。 根據預設，定義專案的偵錯組態`DEBUG`。 當`DEBUG`定義，<xref:System.Diagnostics.Debug>類別方法會產生輸出至**輸出**視窗。 未定義時，<xref:System.Diagnostics.Debug>類別方法便不會編譯，並會產生任何偵錯輸出。|  
|`TARGET`|字串，表示命令列的設定或專案的輸出類型 **/目標**選項。 可能值`TARGET`是：<br /><br /> -「 winexe 」 的 Windows 應用程式。<br />-"exe"為主控台應用程式。<br />-「 程式庫 」 之類別程式庫。<br />-「 模組 」 的模組。<br />- **/目標**選項可以設定在[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]整合式的開發環境。 如需詳細資訊，請參閱[/target (Visual Basic)](../../visual-basic/reference/command-line-compiler/target.md)。|  
|`TRACE`|A`Boolean`值可在設定**專案屬性** 對話方塊。 根據預設，專案的所有組態都定義`TRACE`。 當`TRACE`定義，<xref:System.Diagnostics.Trace>類別方法會產生輸出至**輸出**視窗。 未定義時，<xref:System.Diagnostics.Trace>類別方法便不會編譯，且沒有`Trace`會產生輸出。|  
|`VBC_VER`|Visual Basic 版本，表示中的數字*主要*。*次要*格式。 版本號碼[!INCLUDE[vbprvblong](~/includes/vbprvblong-md.md)]是 8.0。|  
  
### <a name="print-and-display-constants"></a>列印和顯示常數  
 當您呼叫列印，並顯示函式時，您可以使用下列常數的實際值取代程式碼中。  
  
|**常數**|**描述**|  
|---|---|  
|`vbCrLf`|歸位字元/換行字元組合。|  
|`vbCr`|歸位字元。|  
|`vbLf`|換行字元。|  
|`vbNewLine`|新行字元。|  
|`vbNullChar`|Null 字元。|  
|`vbNullString`|不同於零長度字串 ("");用來呼叫外部程序。|  
|`vbObjectError`|錯誤號碼。 使用者定義的錯誤號碼應該大於此值。 例如: <br /><br /> `Err.Raise(Number) = vbObjectError + 1000`|  
|`vbTab`|定位字元。|  
|`vbBack`|退格鍵字元。|  
|`vbFormFeed`|不使用 Microsoft Windows 中。|  
|`vbVerticalTab`|Microsoft Windows 中不實用。|  
  
## <a name="enumerations"></a>列舉  
 下表列出並描述 Visual Basic 所提供的列舉。  
  
|列舉|描述|  
|---|---|  
|<xref:Microsoft.VisualBasic.AppWinStyle>|表示要用於叫用程式呼叫時的視窗樣式<xref:Microsoft.VisualBasic.Interaction.Shell%2A>函式。|  
|<xref:Microsoft.VisualBasic.AudioPlayMode>|表示如何在呼叫音訊方法時播放音效。|  
|<xref:Microsoft.VisualBasic.ApplicationServices.BuiltInRole>|表示要檢查呼叫時角色類型<xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A>方法。|  
|<xref:Microsoft.VisualBasic.CallType>|指出程序呼叫時所叫用的類型<xref:Microsoft.VisualBasic.Interaction.CallByName%2A>函式。|  
|<xref:Microsoft.VisualBasic.CompareMethod>|表示如何比較字串時呼叫的比較函式。|  
|<xref:Microsoft.VisualBasic.DateFormat>|指示如何顯示日期時呼叫<xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>函式。|  
|<xref:Microsoft.VisualBasic.DateInterval>|指示呼叫日期相關函式時，如何決定日期間隔並將其格式化。|  
|<xref:Microsoft.VisualBasic.FileIO.DeleteDirectoryOption>|指定應該的動作時要刪除的目錄含有檔案或目錄。|  
|<xref:Microsoft.VisualBasic.DueDate>|指出當付款的到期時間呼叫帳務處理方法。|  
|<xref:Microsoft.VisualBasic.FileIO.FieldType>|指出文字欄位是否會分隔或固定寬度。|  
|<xref:Microsoft.VisualBasic.FileAttribute>|表示呼叫檔案存取函式時所要使用的檔案屬性。|  
|<xref:Microsoft.VisualBasic.FirstDayOfWeek>|指示呼叫日期相關函式時所要使用的當週的第一天。|  
|<xref:Microsoft.VisualBasic.FirstWeekOfYear>|指示呼叫日期相關函式時所要使用年份的第一週。|  
|<xref:Microsoft.VisualBasic.MsgBoxResult>|指出訊息方塊上按下了哪個按鈕，由 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 函式傳回。|  
|<xref:Microsoft.VisualBasic.MsgBoxStyle>|表示呼叫 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 函式時要顯示的按鈕。|  
|<xref:Microsoft.VisualBasic.OpenAccess>|表示如何開啟檔案時呼叫的函式檔案存取。|  
|<xref:Microsoft.VisualBasic.OpenMode>|表示如何開啟檔案時呼叫的函式檔案存取。|  
|<xref:Microsoft.VisualBasic.OpenShare>|表示如何開啟檔案時呼叫的函式檔案存取。|  
|<xref:Microsoft.VisualBasic.FileIO.RecycleOption>|指定檔案是否應永久刪除或放在資源回收筒中。|  
|<xref:Microsoft.VisualBasic.FileIO.SearchOption>|指定是否要搜尋所有或只有最上層目錄。|  
|<xref:Microsoft.VisualBasic.TriState>|指出`Boolean`值或呼叫數字格式的函式時是否使用預設值。|  
|<xref:Microsoft.VisualBasic.FileIO.UICancelOption>|指定應完成，如果使用者按一下**取消**作業期間。|  
|<xref:Microsoft.VisualBasic.FileIO.UIOption>|指定要複製、 刪除或移動檔案或目錄時，顯示進度對話方塊。|  
|<xref:Microsoft.VisualBasic.VariantType>|表示 variant 的物件，所傳回的類型<xref:Microsoft.VisualBasic.Information.VarType%2A>函式。|  
|<xref:Microsoft.VisualBasic.VbStrConv>|表示呼叫 <xref:Microsoft.VisualBasic.Strings.StrConv%2A> 函式時要執行的轉換類型。|  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 語言參考](../../visual-basic/language-reference/index.md)  
 [Visual Basic](../../visual-basic/index.md)  
 [常數的概觀](../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [列舉的概觀](../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
