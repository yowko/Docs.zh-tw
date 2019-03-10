---
title: WebBrowser 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- WebBrowser
helpviewer_keywords:
- WebBrowser control [Windows Forms], about
- Web pages [Windows Forms], displaying in applications
ms.assetid: 6e3e1cc2-9c48-4136-9659-e99e4e60b7e9
ms.openlocfilehash: cc998fd88f3487aa20f6cef73aacb6c07f92c7ad
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710091"
---
# <a name="webbrowser-control-overview"></a>WebBrowser 控制項概觀
<xref:System.Windows.Forms.WebBrowser>控制項會提供 WebBrowser ActiveX 控制項的 managed 包裝函式。 Managed 包裝函式可讓您在 Windows Form 用戶端應用程式中顯示網頁的網頁。 您可以使用<xref:System.Windows.Forms.WebBrowser>複製您的應用程式，或者您的 Internet Explorer Web 瀏覽功能的控制項可以停用 Internet Explorer 的預設功能，並將簡單的 HTML 文件檢視器控制項。 您也可以使用控制項將 DHTML 為基礎的使用者介面項目新增至您的表單，隱藏的事實，它們裝載於<xref:System.Windows.Forms.WebBrowser>控制項。 這種方法可讓您順暢地結合在單一應用程式中的 Windows Form 控制項使用的 Web 控制項。  
  
## <a name="frequently-used-properties-methods-and-events"></a>常用的屬性、 方法和事件  
 <xref:System.Windows.Forms.WebBrowser>控制項有數個屬性、 方法和事件，您可以用來實作 Internet Explorer 中的控制項。 比方說，您可以使用`Navigate`方法，以實作網址列中，而`GoBack`， `GoForward`， `Stop`，和`Refresh`來實作瀏覽按鈕的工具列上的方法。 您可以處理`Navigated`事件，以更新 [網址] 列的值`Url`屬性和值的標題列`DocumentTitle`屬性。  
  
 如果您想要產生您自己的網頁內容，應用程式中，您可以設定`DocumentText`屬性。 如果您是熟悉 HTML 文件物件模型 (DOM)，您也可以操作的目前 Web 網頁透過內容`Document`屬性。 與這個屬性中，您可以儲存，並修改文件，而不是在檔案之間巡覽的記憶體中。  
  
 `Document`屬性也可讓您呼叫在網頁上指令碼從您的用戶端應用程式程式碼的程式碼中實作的方法。 若要從您指令碼的程式碼中存取您的用戶端應用程式程式碼，請設定`ObjectForScripting`屬性。 您指定的物件可以存取您的指令碼，做為`window.external`物件。  
  
|名稱|描述|  
|----------|-----------------|  
|<xref:System.Windows.Forms.WebBrowser.Document%2A> 屬性|取得物件，提供目前 Web 網頁的 HTML 文件物件模型 (DOM) 的受管理的存取。|  
|<xref:System.Windows.Forms.WebBrowser.DocumentCompleted> 事件|網頁完成載入時，就會發生。|  
|<xref:System.Windows.Forms.WebBrowser.DocumentText%2A> 屬性|取得或設定目前 Web 網頁內容的 HTML。|  
|<xref:System.Windows.Forms.WebBrowser.DocumentTitle%2A> 屬性|取得目前 Web 網頁的標題。|  
|<xref:System.Windows.Forms.WebBrowser.GoBack%2A> 方法|瀏覽至 歷程記錄中的上一頁。|  
|<xref:System.Windows.Forms.WebBrowser.GoForward%2A> 方法|瀏覽至 歷程記錄的下一個頁面。|  
|<xref:System.Windows.Forms.WebBrowser.Navigate%2A> 方法|瀏覽至指定的 URL。|  
|<xref:System.Windows.Forms.WebBrowser.Navigating> 事件|導覽開始，啟用要取消的動作之前發生。|  
|<xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> 屬性|取得或設定指令碼的網頁可以用來與您的應用程式通訊的物件。|  
|<xref:System.Windows.Forms.WebBrowser.Print%2A> 方法|列印目前的網頁。|  
|<xref:System.Windows.Forms.WebBrowser.Refresh%2A> 方法|重新載入目前的網頁。|  
|<xref:System.Windows.Forms.WebBrowser.Stop%2A> 方法|中止目前的巡覽，並停止音效及動畫等動態頁面項目。|  
|<xref:System.Windows.Forms.WebBrowser.Url%2A> 屬性|取得或設定目前 Web 網頁的 URL。 設定這個屬性會瀏覽至新的 URL 的控制項。|  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowserDocumentCompletedEventArgs>
- <xref:System.Windows.Forms.WebBrowserDocumentCompletedEventHandler>
- <xref:System.Windows.Forms.WebBrowserEncryptionLevel>
- <xref:System.Windows.Forms.WebBrowserNavigatedEventArgs>
- <xref:System.Windows.Forms.WebBrowserNavigatedEventHandler>
- <xref:System.Windows.Forms.WebBrowserNavigatingEventArgs>
- <xref:System.Windows.Forms.WebBrowserNavigatingEventHandler>
- <xref:System.Windows.Forms.WebBrowserProgressChangedEventArgs>
- <xref:System.Windows.Forms.WebBrowserReadyState>
- <xref:System.Windows.Forms.WebBrowserRefreshOption>
- [如何：瀏覽至 URL，以使用 WebBrowser 控制項](how-to-navigate-to-a-url-with-the-webbrowser-control.md)
- [如何：使用 WebBrowser 控制項列印](how-to-print-with-a-webbrowser-control.md)
- [如何：將 Web 瀏覽器功能加入至 Windows Forms 應用程式](how-to-add-web-browser-capabilities-to-a-windows-forms-application.md)
- [如何：建立 Windows Forms 應用程式中的 HTML 文件檢視器](how-to-create-an-html-document-viewer-in-a-windows-forms-application.md)
- [如何：實作 DHTML 程式碼和用戶端應用程式程式碼之間的雙向通訊](implement-two-way-com-between-dhtml-and-client.md)
- [WebBrowser 安全性](webbrowser-security.md)
