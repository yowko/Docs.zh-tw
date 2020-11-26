---
title: 作法：將追蹤陳述式新增至應用程式程式碼
description: 瞭解如何在 .NET 中將追蹤語句新增至應用程式程式碼。 最常用於追蹤的方法是將輸出寫入接聽程式的方法。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tracing [.NET Framework], conditional writes based on switches
- trace statements
- WriteLineIf method
- tracing [.NET Framework], adding trace statements
- Assert method, tracing code
- trace switches, conditional writes based on switches
- WriteIf method
ms.assetid: f3a93fa7-1717-467d-aaff-393e5c9828b4
ms.openlocfilehash: 6beecf39d4372a194a9110ed8942b998443934d4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244206"
---
# <a name="how-to-add-trace-statements-to-application-code"></a>作法：將追蹤陳述式新增至應用程式程式碼

追蹤最常使用的方法就是將輸出寫入接聽程式的方法：**Write**、**WriteIf**、**WriteLine**、**WriteLineIf**、**Assert** 和 **Fail**。 這些方法可以分成兩種類別：**Write**、**WriteLine** 與 **Fail** 都會無條件地發出輸出，而 **WriteIf**、**WriteLineIf** 與 **Assert** 則會測試布林條件，並根據條件的值寫入或不寫入。 如果條件為 `true`，**WriteIf** 與 **WriteLineIf** 會發出輸出，而如果條件為 `false`，則 **Assert** 會發出輸出。  
  
 設計追蹤和偵錯策略時，應該思考該輸出的內容為何。 多個以不相關資訊填滿的 **寫入** 語句將會建立難以讀取的記錄檔。 另一方面，使用 **WriteLine** 將相關的語句放在不同的行上，可能會讓您難以區分哪些資訊屬於同一個。 一般情況下，當您想要結合多個來源的資訊來建立單一的資訊訊息時，請使用多個 **Write** 語句，並在您想要建立單一完整訊息時使用 **WriteLine** 語句。  
  
### <a name="to-write-a-complete-line"></a>若要撰寫完整行  
  
1. 呼叫 <xref:System.Diagnostics.Trace.WriteLine%2A> 或 <xref:System.Diagnostics.Trace.WriteLineIf%2A> 方法。  
  
     將歸位字元附加到此方法傳回的訊息結尾，讓由 **Write**、**WriteIf**、**WriteLine** 或 **WriteLineIf** 傳回的下一個訊息，從下行開始：  
  
    ```vb  
    Dim errorFlag As Boolean = False  
    Trace.WriteLine("Error in AppendData procedure.")  
    Trace.WriteLineIf(errorFlag, "Error in AppendData procedure.")  
    ```  
  
    ```csharp  
    bool errorFlag = false;  
    System.Diagnostics.Trace.WriteLine ("Error in AppendData procedure.");  
    System.Diagnostics.Trace.WriteLineIf(errorFlag,
       "Error in AppendData procedure.");  
    ```  
  
### <a name="to-write-a-partial-line"></a>若要寫入部分行  
  
1. 呼叫 <xref:System.Diagnostics.Trace.Write%2A> 或 <xref:System.Diagnostics.Trace.WriteIf%2A> 方法。  
  
     由 **Write**、**WriteIf**、**WriteLine** 或 **WriteLineIf** 放出的下一個訊息，將會以 **Write** 或 **WriteIf** 陳述式所放出訊息的相同行開始：  
  
    ```vb  
    Dim errorFlag As Boolean = False  
    Trace.WriteIf(errorFlag, "Error in AppendData procedure.")  
    Debug.WriteIf(errorFlag, "Transaction abandoned.")  
    Trace.Write("Invalid value for data request")  
    ```  
  
    ```csharp  
    bool errorFlag = false;  
    System.Diagnostics.Trace.WriteIf(errorFlag,
       "Error in AppendData procedure.");  
    System.Diagnostics.Debug.WriteIf(errorFlag, "Transaction abandoned.");  
    Trace.Write("Invalid value for data request");  
    ```  
  
### <a name="to-verify-that-certain-conditions-exist-either-before-or-after-you-execute-a-method"></a>若要確認特定條件存在 (不論在執行方法之前或之後)  
  
1. 呼叫 <xref:System.Diagnostics.Trace.Assert%2A> 方法。  
  
    ```vb  
    Dim i As Integer = 4  
    Trace.Assert(i = 5, "i is not equal to 5.")  
    ```  
  
    ```csharp  
    int i = 4;  
    System.Diagnostics.Trace.Assert(i == 5, "i is not equal to 5.");  
    ```  
  
    > [!NOTE]
    > 追蹤和偵錯時都可以使用 **Assert**。 此範例會將呼叫堆疊輸出到任何 **Listeners** 集合中的接聽程式。 如需詳細資訊，請參閱 [Managed 程式碼中的判斷提示](/visualstudio/debugger/assertions-in-managed-code)以及 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Diagnostics.Debug.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.WriteLineIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteLineIf%2A?displayProperty=nameWithType>
- [追蹤和檢測應用程式](tracing-and-instrumenting-applications.md) (機器翻譯)
- [作法：建立、初始化和設定追蹤參數](how-to-create-initialize-and-configure-trace-switches.md)
- [追蹤參數](trace-switches.md)
- [追蹤接聽項](trace-listeners.md)
