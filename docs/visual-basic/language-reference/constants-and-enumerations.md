---
title: 常數和列舉類型 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- constants [Visual Basic]
- constants [Visual Basic], list of
ms.assetid: 309c0ad5-83e4-4f96-99ea-83cd95107417
ms.openlocfilehash: 33327a8d5e7ce7676ffda6245f3e4f9cccc8b1fb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573305"
---
# <a name="constants-and-enumerations-visual-basic"></a>常數和列舉類型 (Visual Basic)
Visual Basic 提供許多預先定義的常數和列舉型別適用於開發人員。 常數用來儲存保持不變的應用程式執行過程中的值。 列舉提供使用相關常數組和建立常數值與名稱之關聯的便利方法。  
  
## <a name="constants"></a>常數  
  
### <a name="conditional-compilation-constants"></a>條件式編譯常數  
 下表列出可用於條件式編譯的預先定義的常數。  
  
|**常數**|**描述**|  
|---|---|  
|`CONFIG`|字串，對應至目前的設定**作用中的方案組態**方塊中**Configuration Manager**。|  
|`DEBUG`|A`Boolean`中可設定的值**專案屬性** 對話方塊。 根據預設，專案的偵錯組態會定義`DEBUG`。 當`DEBUG`定義，則<xref:System.Diagnostics.Debug>類別方法會產生輸出**輸出**視窗。 當未定義時，<xref:System.Diagnostics.Debug>類別方法便不會編譯，並會產生任何偵錯輸出。|  
|`TARGET`|字串，表示的命令列設定或專案的輸出類型 **/目標**選項。 可能值`TARGET`是：<br /><br /> -「 winexe 「 Windows 應用程式。<br />-"exe"主控台應用程式。<br />-「 程式庫 」 之類別程式庫。<br />-對於模組的 「 模組 」。<br />- **/目標**選項可在 Visual Studio 整合式的開發環境中設定。 如需詳細資訊，請參閱 < [/target (Visual Basic)](../../visual-basic/reference/command-line-compiler/target.md)。|  
|`TRACE`|A`Boolean`中可設定的值**專案屬性** 對話方塊。 根據預設，專案的所有組態都定義`TRACE`。 當`TRACE`定義，則<xref:System.Diagnostics.Trace>類別方法會產生輸出**輸出**視窗。 未定義，當<xref:System.Diagnostics.Trace>類別方法便不會編譯，但沒有`Trace`會產生輸出。|  
|`VBC_VER`|代表 Visual Basic 版本，在中的數字*主要*。*次要*格式。 版本號碼[!INCLUDE[vbprvblong](~/includes/vbprvblong-md.md)]為 8.0。|  
  
### <a name="print-and-display-constants"></a>列印和顯示常數  
 當您呼叫列印和顯示功能時，您可以使用下列常數在您的程式碼來取代實際的值。  
  
|**常數**|**描述**|  
|---|---|  
|`vbCrLf`|歸位字元/換行字元組合。|  
|`vbCr`|歸位字元。|  
|`vbLf`|換行字元。|  
|`vbNewLine`|新行字元。|  
|`vbNullChar`|Null 字元。|  
|`vbNullString`|不同的零長度字串 ("");用來呼叫外部程序。|  
|`vbObjectError`|錯誤號碼。 使用者定義的錯誤號碼應該大於此值。 例如: <br /><br /> `Err.Raise(Number) = vbObjectError + 1000`|  
|`vbTab`|字元的索引標籤。|  
|`vbBack`|退格鍵字元。|  
|`vbFormFeed`|Microsoft Windows 中未使用。|  
|`vbVerticalTab`|在 Microsoft Windows 不實用。|  
  
## <a name="enumerations"></a>列舉  
 下表列出並說明 Visual Basic 所提供的列舉。  
  
|列舉|描述|  
|---|---|  
|<xref:Microsoft.VisualBasic.AppWinStyle>|指出呼叫時，叫用程式使用的視窗樣式<xref:Microsoft.VisualBasic.Interaction.Shell%2A>函式。|  
|<xref:Microsoft.VisualBasic.AudioPlayMode>|指出在呼叫音效方法時播放音效的方式。|  
|<xref:Microsoft.VisualBasic.ApplicationServices.BuiltInRole>|表示要檢查呼叫時的角色類型<xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A>方法。|  
|<xref:Microsoft.VisualBasic.CallType>|指出呼叫時所叫用的程序的類型<xref:Microsoft.VisualBasic.Interaction.CallByName%2A>函式。|  
|<xref:Microsoft.VisualBasic.CompareMethod>|指示如何比較字串時呼叫比較函式。|  
|<xref:Microsoft.VisualBasic.DateFormat>|指出如何顯示日期時呼叫<xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>函式。|  
|<xref:Microsoft.VisualBasic.DateInterval>|指示呼叫日期相關函式時，如何決定日期間隔並將其格式化。|  
|<xref:Microsoft.VisualBasic.FileIO.DeleteDirectoryOption>|指定要刪除的目錄包含檔案或目錄時應做些什麼。|  
|<xref:Microsoft.VisualBasic.DueDate>|付款何時到期會指出呼叫帳務處理方法。|  
|<xref:Microsoft.VisualBasic.FileIO.FieldType>|指出是否已分隔的文字欄位還是固定寬度。|  
|<xref:Microsoft.VisualBasic.FileAttribute>|指出呼叫檔案存取函式時要使用的檔案屬性。|  
|<xref:Microsoft.VisualBasic.FirstDayOfWeek>|指出呼叫日期相關的函式時要使用一週的第一天。|  
|<xref:Microsoft.VisualBasic.FirstWeekOfYear>|指出呼叫日期相關的函式時要使用一年的第一週。|  
|<xref:Microsoft.VisualBasic.MsgBoxResult>|指出訊息方塊上按下了哪個按鈕，由 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 函式傳回。|  
|<xref:Microsoft.VisualBasic.MsgBoxStyle>|表示呼叫 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 函式時要顯示的按鈕。|  
|<xref:Microsoft.VisualBasic.OpenAccess>|指出在呼叫檔案存取函式時，請開啟檔案的方式。|  
|<xref:Microsoft.VisualBasic.OpenMode>|指出在呼叫檔案存取函式時，請開啟檔案的方式。|  
|<xref:Microsoft.VisualBasic.OpenShare>|指出在呼叫檔案存取函式時，請開啟檔案的方式。|  
|<xref:Microsoft.VisualBasic.FileIO.RecycleOption>|指定檔案要永久刪除或放在資源回收筒中。|  
|<xref:Microsoft.VisualBasic.FileIO.SearchOption>|指定是否要搜尋所有或只有最上層目錄。|  
|<xref:Microsoft.VisualBasic.TriState>|指出`Boolean`值或呼叫數字格式化函式時是否使用預設值。|  
|<xref:Microsoft.VisualBasic.FileIO.UICancelOption>|指定項目應該是如果使用者按一下完成**取消**作業期間。|  
|<xref:Microsoft.VisualBasic.FileIO.UIOption>|指定要複製、 刪除或移動檔案或目錄時，顯示進度對話方塊。|  
|<xref:Microsoft.VisualBasic.VariantType>|指出變數物件，所傳回的型別<xref:Microsoft.VisualBasic.Information.VarType%2A>函式。|  
|<xref:Microsoft.VisualBasic.VbStrConv>|表示呼叫 <xref:Microsoft.VisualBasic.Strings.StrConv%2A> 函式時要執行的轉換類型。|  
  
## <a name="see-also"></a>另請參閱
- [Visual Basic 語言參考](../../visual-basic/language-reference/index.md)
- [Visual Basic](../../visual-basic/index.md)
- [常數的概觀](../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [列舉的概觀](../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
