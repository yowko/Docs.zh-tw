---
title: HOW TO：實作 DHTML 程式碼和用戶端應用程式程式碼之間的雙向通訊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- WebBrowser.ObjectForScripting
- WebBrowser.Document
helpviewer_keywords:
- WebBrowser control [Windows Forms], examples
- communications [Windows Forms], DHTML and client applications
- examples [Windows Forms], WebBrowser control
- WebBrowser control [Windows Forms], communication between DHTML and client application
- DHTML [Windows Forms], embedding in Windows Forms
ms.assetid: 55353a32-b09e-4479-a521-ff3a5ff9a708
ms.openlocfilehash: 26cbc995a749c4c129729be700dee588d1033a05
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953429"
---
# <a name="how-to-implement-two-way-communication-between-dhtml-code-and-client-application-code"></a>HOW TO：實作 DHTML 程式碼和用戶端應用程式程式碼之間的雙向通訊

您可以使用 <xref:System.Windows.Forms.WebBrowser> 控制項，將現有的動態 HTML (DHTML) Web 應用程式程式碼加入至 Windows Form 用戶端應用程式。 這適用於投資了大量的開發時間在建立 DHTML 控制項，而且您想要利用 Windows Form 的豐富使用者介面功能而又不需要重新撰寫現有程式碼的情況。

<xref:System.Windows.Forms.WebBrowser> 控制項可讓您實作用戶端應用程式程式碼與網頁指令碼程式碼之間的雙向通訊，這是透過 <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> 和 <xref:System.Windows.Forms.WebBrowser.Document%2A> 屬性。 此外，您可以設定 <xref:System.Windows.Forms.WebBrowser> 控制，好讓您的 Web 控制項與應用程式表單上其他控制項順暢地混合，隱藏其 DHTML 實作。 若要順暢地混合控制項，請格式化所顯示的頁面，以便其背景色彩和視覺化樣式符合表單的其餘部分，並使用 <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A><xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> 和 <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> 屬性停用標準瀏覽器功能。

## <a name="to-embed-dhtml-in-your-windows-forms-application"></a>在 Windows Form 應用程式中內嵌 DHTML

1. 將 <xref:System.Windows.Forms.WebBrowser> 控制項的 <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> 屬性設為 `false`，以防止 <xref:System.Windows.Forms.WebBrowser> 控制項開啟放到它上面的檔案。

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#1)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#1)]

2. 將控制項的 <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> 屬性設為 `false`，以防止使用者在 <xref:System.Windows.Forms.WebBrowser> 控制項上按一下滑鼠右鍵時顯示其捷徑功能表。

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#2)]

3. 將控制項的 <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> 屬性設為 `false`，以防止 <xref:System.Windows.Forms.WebBrowser> 控制項回應快速鍵。

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#3)]

4. 設定表單建構函式或 <xref:System.Windows.Forms.Form.Load> 事件處理常式中的 <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> 屬性。

     下列程式碼會使用指令碼物件本身的表單類別。

    > [!NOTE]
    > 元件物件模型 (COM) 必須能夠存取指令碼物件。 若要讓 COM 可看見表單，請將 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 屬性加入到您的表單類別。

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#4)]

5. 在您指令碼程式碼將使用的應用程式程式碼中實作公用屬性或方法。

     比方說，如果指令碼物件使用表單類別，請將下列程式碼加入至表單類別。

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#5)]

6. 在指令碼程式碼中使用 `window.external` 物件來存取指定物件的公用屬性和方法。

     下列 HTML 程式碼示範如何按一下按鈕以在指令碼物件上呼叫方法。 將此程式碼複製到您使用控制項 <xref:System.Windows.Forms.WebBrowser.Navigate%2A> 方法載入的 HTML 文件的 BODY 項目，或是您指派給控制項 <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> 屬性的 HTML 文件的 BODY 項目。

    ```html
    <button onclick="window.external.Test('called from script code')">
        call client code from script code
    </button>
    ```

7. 實作您應用程式程式碼將使用之指令碼中的函式。

     下列 HTML SCRIPT 項目提供範例函式。 將此程式碼複製到您使用控制項 <xref:System.Windows.Forms.WebBrowser.Navigate%2A> 方法載入的 HTML 文件的 HEAD 項目，或是您指派給控制項 <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> 屬性的 HTML 文件的 HEAD 項目。

    ```html
    <script>
    function test(message) {
        alert(message);
    }
    </script>
    ```

8. 使用 <xref:System.Windows.Forms.WebBrowser.Document%2A> 屬性來從用戶端應用程式程式碼存取指令碼。

     例如，將下列程式碼加入至按鈕 <xref:System.Windows.Forms.Control.Click> 事件處理常式。

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#8)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#8)]

9. 當您完成偵錯您 DHTML 時，請將控制項的 <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> 屬性設為 `true`，以防止 <xref:System.Windows.Forms.WebBrowser> 控制項顯示指令碼問題的錯誤訊息。

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#9)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#9)]

## <a name="example"></a>範例

下列完整程式碼範例提供示範應用程式，您可以用它來了解這項功能。 HTML 程式碼會透過 <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> 屬性載入至 <xref:System.Windows.Forms.WebBrowser> 控制項，而不會從個別的 HTML 檔案載入。

[!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#0)]
[!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#0)]

## <a name="compiling-the-code"></a>編譯程式碼

此程式碼需要：

- System 和 System.Windows.Forms 組件的參考。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.Document%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A?displayProperty=nameWithType>
- [WebBrowser 控制項](webbrowser-control-windows-forms.md)
