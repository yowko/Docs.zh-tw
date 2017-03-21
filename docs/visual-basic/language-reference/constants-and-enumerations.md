---
title: "常數和列舉 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- enumerations [Visual Basic]
- constants
- constants, list of
ms.assetid: 309c0ad5-83e4-4f96-99ea-83cd95107417
caps.latest.revision: 18
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: e37ef2e3c51e96e85cb214054195016e69d52382
ms.lasthandoff: 03/13/2017

---
# <a name="constants-and-enumerations-visual-basic"></a>常數和列舉類型 (Visual Basic)
[!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]提供一些預先定義的常數和列舉型別供開發人員使用。 常數用來儲存保持不變的應用程式執行過程中的值。 列舉型別提供便利的方式使用組相關常數和常數值與名稱。  
  
## <a name="constants"></a>常數  
  
### <a name="conditional-compilation-constants"></a>條件式編譯的常數  
 下表列出可用於條件式編譯的預先定義的常數。  
  
|**常數**|**說明**|  
|---|---|  
|`CONFIG`|字串，對應至目前的設定**作用中方案組態**方塊**Configuration Manager**。|  
|`DEBUG`|A`Boolean`值可在設定**專案屬性**對話方塊。 根據預設，專案的偵錯組態會定義`DEBUG`。 當`DEBUG`定義，<xref:System.Diagnostics.Debug>類別方法會產生輸出**輸出**視窗。</xref:System.Diagnostics.Debug> 未定義時，<xref:System.Diagnostics.Debug>類別方法便不會編譯，會產生任何偵錯輸出。</xref:System.Diagnostics.Debug>|  
|`TARGET`|字串，表示命令列中的設定或專案的輸出類型**/目標**選項。 可能的值`TARGET`是︰<br /><br /> -「 winexe 」 的 Windows 應用程式。<br />-"exe"主控台應用程式。<br />-類別程式庫的 「 媒體櫃 」。<br />-「 模組 」 的模組。<br />- **/目標**選項可以設定在[!INCLUDE[vsprvs](../../csharp/includes/vsprvs_md.md)]整合式的開發環境。 如需詳細資訊，請參閱[/target (Visual Basic)](../../visual-basic/reference/command-line-compiler/target.md)。|  
|`TRACE`|A`Boolean`值可在設定**專案屬性**對話方塊。 根據預設，專案的所有組態都定義`TRACE`。 當`TRACE`定義，<xref:System.Diagnostics.Trace>類別方法會產生輸出**輸出**視窗。</xref:System.Diagnostics.Trace> 未定義時，<xref:System.Diagnostics.Trace>類別方法便不會編譯，但不含任何`Trace`不會產生輸出。</xref:System.Diagnostics.Trace>|  
|`VBC_VER`|數字代表[!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]版本，請在*主要*。*次要*格式。 版本號碼[!INCLUDE[vbprvblong](../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]是 8.0。|  
  
### <a name="print-and-display-constants"></a>列印和顯示常數  
 當您呼叫列印和顯示功能時，您可以使用下列常數來取代實際值的程式碼中。  
  
|**常數**|**說明**|  
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
 下表列出並描述所提供的列舉型別[!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。  
  
|列舉|描述|  
|---|---|  
|<xref:Microsoft.VisualBasic.AppWinStyle></xref:Microsoft.VisualBasic.AppWinStyle>|表示呼叫時，叫用程式使用的視窗樣式<xref:Microsoft.VisualBasic.Interaction.Shell%2A>函式。</xref:Microsoft.VisualBasic.Interaction.Shell%2A>|  
|<xref:Microsoft.VisualBasic.AudioPlayMode></xref:Microsoft.VisualBasic.AudioPlayMode>|指出如何呼叫音效方法時播放音效。|  
|<xref:Microsoft.VisualBasic.ApplicationServices.BuiltInRole></xref:Microsoft.VisualBasic.ApplicationServices.BuiltInRole>|表示要檢查呼叫時的角色類型<xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A>方法。</xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A>|  
|<xref:Microsoft.VisualBasic.CallType></xref:Microsoft.VisualBasic.CallType>|指出程序呼叫時所叫用的類型<xref:Microsoft.VisualBasic.Interaction.CallByName%2A>函式。</xref:Microsoft.VisualBasic.Interaction.CallByName%2A>|  
|<xref:Microsoft.VisualBasic.CompareMethod></xref:Microsoft.VisualBasic.CompareMethod>|指示如何比較字串時呼叫比較函式。|  
|<xref:Microsoft.VisualBasic.DateFormat></xref:Microsoft.VisualBasic.DateFormat>|指示如何顯示日期時呼叫<xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>函式。</xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>|  
|<xref:Microsoft.VisualBasic.DateInterval></xref:Microsoft.VisualBasic.DateInterval>|指示呼叫日期相關函式時，如何決定日期間隔並將其格式化。|  
|<xref:Microsoft.VisualBasic.FileIO.DeleteDirectoryOption></xref:Microsoft.VisualBasic.FileIO.DeleteDirectoryOption>|指定應該的動作時要刪除的目錄包含檔案或目錄。|  
|<xref:Microsoft.VisualBasic.DueDate></xref:Microsoft.VisualBasic.DueDate>|指出當付款的到期時間呼叫帳務處理方法。|  
|<xref:Microsoft.VisualBasic.FileIO.FieldType></xref:Microsoft.VisualBasic.FileIO.FieldType>|表示文字欄位是否會分隔或固定寬度。|  
|<xref:Microsoft.VisualBasic.FileAttribute></xref:Microsoft.VisualBasic.FileAttribute>|表示呼叫檔案存取函式時要使用的檔案屬性。|  
|<xref:Microsoft.VisualBasic.FirstDayOfWeek></xref:Microsoft.VisualBasic.FirstDayOfWeek>|表示呼叫日期相關的函式時要使用一週的第一天。|  
|<xref:Microsoft.VisualBasic.FirstWeekOfYear></xref:Microsoft.VisualBasic.FirstWeekOfYear>|表示呼叫日期相關的函式時要使用的年份的第一週。|  
|<xref:Microsoft.VisualBasic.MsgBoxResult></xref:Microsoft.VisualBasic.MsgBoxResult>|指出哪一個按鈕按下一個訊息方塊中，所傳回<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>函式。</xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>|  
|<xref:Microsoft.VisualBasic.MsgBoxStyle></xref:Microsoft.VisualBasic.MsgBoxStyle>|表示要顯示呼叫時的按鈕<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>函式。</xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>|  
|<xref:Microsoft.VisualBasic.OpenAccess></xref:Microsoft.VisualBasic.OpenAccess>|指出如何開啟檔案時呼叫檔案存取函式。|  
|<xref:Microsoft.VisualBasic.OpenMode></xref:Microsoft.VisualBasic.OpenMode>|指出如何開啟檔案時呼叫檔案存取函式。|  
|<xref:Microsoft.VisualBasic.OpenShare></xref:Microsoft.VisualBasic.OpenShare>|指出如何開啟檔案時呼叫檔案存取函式。|  
|<xref:Microsoft.VisualBasic.FileIO.RecycleOption></xref:Microsoft.VisualBasic.FileIO.RecycleOption>|指定檔案要永久刪除或放在資源回收筒中。|  
|<xref:Microsoft.VisualBasic.FileIO.SearchOption></xref:Microsoft.VisualBasic.FileIO.SearchOption>|指定是否要搜尋所有或最上層的目錄。|  
|<xref:Microsoft.VisualBasic.TriState></xref:Microsoft.VisualBasic.TriState>|指出`Boolean`值或數字格式的函式的呼叫時是否使用預設值。|  
|<xref:Microsoft.VisualBasic.FileIO.UICancelOption></xref:Microsoft.VisualBasic.FileIO.UICancelOption>|指定應完成使用者**取消**作業期間。|  
|<xref:Microsoft.VisualBasic.FileIO.UIOption></xref:Microsoft.VisualBasic.FileIO.UIOption>|指定要複製、 刪除或移動檔案或目錄時，顯示進度對話方塊。|  
|<xref:Microsoft.VisualBasic.VariantType></xref:Microsoft.VisualBasic.VariantType>|表示所傳回的 variant 物件的類型<xref:Microsoft.VisualBasic.Information.VarType%2A>函式。</xref:Microsoft.VisualBasic.Information.VarType%2A>|  
|<xref:Microsoft.VisualBasic.VbStrConv></xref:Microsoft.VisualBasic.VbStrConv>|表示要執行時呼叫的轉換類型<xref:Microsoft.VisualBasic.Strings.StrConv%2A>函式。</xref:Microsoft.VisualBasic.Strings.StrConv%2A>|  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 語言參考](../../visual-basic/language-reference/index.md)   
 [Visual Basic](../../visual-basic/index.md)   
 [常數的概觀](../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)   
 [列舉的概觀](../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
