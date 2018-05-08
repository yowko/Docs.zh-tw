---
title: WebBrowser 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- WebBrowser
helpviewer_keywords:
- WebBrowser control [Windows Forms], about
- Web pages [Windows Forms], displaying in applications
ms.assetid: 6e3e1cc2-9c48-4136-9659-e99e4e60b7e9
ms.openlocfilehash: 2e69b71b3e354101d950d6f7011b13fc7c0de030
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="webbrowser-control-overview"></a>WebBrowser 控制項概觀
<xref:System.Windows.Forms.WebBrowser>控制項提供 WebBrowser ActiveX 控制項 managed 包裝函式。 Managed 包裝函式可讓您在 Windows Form 用戶端應用程式中顯示網頁。 您可以使用<xref:System.Windows.Forms.WebBrowser>控制項複製 Internet Explorer Web 瀏覽功能，您的應用程式，或者您可以停用預設的 Internet Explorer 功能和控制項做為簡單的 HTML 文件檢視器。 您也可以使用此控制項將 DHTML 為基礎的使用者介面項目加入至表單，隱藏的事實，它們會裝載在<xref:System.Windows.Forms.WebBrowser>控制項。 這種方法可讓您順暢地結合到單一應用程式的 Windows Form 控制項使用的 Web 控制項。  
  
## <a name="frequently-used-properties-methods-and-events"></a>常用的屬性、 方法和事件  
 <xref:System.Windows.Forms.WebBrowser>控制項有數個屬性、 方法和事件，您可以用來實作控制項，Internet Explorer 中。 例如，您可以使用`Navigate`方法，以實作網址列中，而`GoBack`， `GoForward`， `Stop`，和`Refresh`方法來實作工具列上的 瀏覽按鈕。 您可以處理`Navigated`事件，以更新其值為 [網址] 列`Url`屬性和標題列的值與`DocumentTitle`屬性。  
  
 如果您想要產生您自己的網頁內容應用程式中，您可以設定`DocumentText`屬性。 如果您是熟悉 HTML 文件物件模型 (DOM)，您也可以處理透過目前網頁的內容`Document`屬性。 具有此屬性，您可以儲存和修改記憶體，而不在檔案之間巡覽的文件。  
  
 `Document`屬性也可讓您呼叫在網頁指令碼從用戶端應用程式程式碼中實作的方法。 若要從指令碼程式碼存取您的用戶端應用程式程式碼，設定`ObjectForScripting`屬性。 您指定的物件可以存取您的指令碼，做為`window.external`物件。  
  
|名稱|描述|  
|----------|-----------------|  
|<xref:System.Windows.Forms.WebBrowser.Document%2A> 屬性|取得物件，提供受管理的存取權，目前網頁的 HTML 文件物件模型 (DOM)。|  
|<xref:System.Windows.Forms.WebBrowser.DocumentCompleted> 事件|當網頁載入完畢時，就會發生。|  
|<xref:System.Windows.Forms.WebBrowser.DocumentText%2A> 屬性|取得或設定內容的目前網頁的 HTML。|  
|<xref:System.Windows.Forms.WebBrowser.DocumentTitle%2A> 屬性|取得目前網頁的標題。|  
|<xref:System.Windows.Forms.WebBrowser.GoBack%2A> 方法|巡覽至歷程記錄中的上一頁。|  
|<xref:System.Windows.Forms.WebBrowser.GoForward%2A> 方法|巡覽至歷程記錄的下一個頁面。|  
|<xref:System.Windows.Forms.WebBrowser.Navigate%2A> 方法|巡覽至指定的 URL。|  
|<xref:System.Windows.Forms.WebBrowser.Navigating> 事件|發生於之前瀏覽開始，啟用取消的動作。|  
|<xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> 屬性|取得或設定指令碼的網頁可以用來與您的應用程式通訊的物件。|  
|<xref:System.Windows.Forms.WebBrowser.Print%2A> 方法|列印目前頁面。|  
|<xref:System.Windows.Forms.WebBrowser.Refresh%2A> 方法|重新載入目前頁面。|  
|<xref:System.Windows.Forms.WebBrowser.Stop%2A> 方法|中止目前的巡覽和停止音效及動畫等動態頁面項目。|  
|<xref:System.Windows.Forms.WebBrowser.Url%2A> 屬性|取得或設定目前網頁的 URL。 設定這個屬性可巡覽至新的 URL 控制項。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.WebBrowser>  
 <xref:System.Windows.Forms.WebBrowserDocumentCompletedEventArgs>  
 <xref:System.Windows.Forms.WebBrowserDocumentCompletedEventHandler>  
 <xref:System.Windows.Forms.WebBrowserEncryptionLevel>  
 <xref:System.Windows.Forms.WebBrowserNavigatedEventArgs>  
 <xref:System.Windows.Forms.WebBrowserNavigatedEventHandler>  
 <xref:System.Windows.Forms.WebBrowserNavigatingEventArgs>  
 <xref:System.Windows.Forms.WebBrowserNavigatingEventHandler>  
 <xref:System.Windows.Forms.WebBrowserProgressChangedEventArgs>  
 <xref:System.Windows.Forms.WebBrowserReadyState>  
 <xref:System.Windows.Forms.WebBrowserRefreshOption>  
 [操作說明：使用 WebBrowser 控制項巡覽至 URL](../../../../docs/framework/winforms/controls/how-to-navigate-to-a-url-with-the-webbrowser-control.md)  
 [操作說明：使用 WebBrowser 控制項列印](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)  
 [操作說明：將 Web 瀏覽器功能加入至 Windows Forms 應用程式](../../../../docs/framework/winforms/controls/how-to-add-web-browser-capabilities-to-a-windows-forms-application.md)  
 [操作說明：在 Windows Forms 應用程式中建立 HTML 文件檢視器](../../../../docs/framework/winforms/controls/how-to-create-an-html-document-viewer-in-a-windows-forms-application.md)  
 [操作說明：實作 DHTML 程式碼和用戶端應用程式程式碼之間的雙向通訊](../../../../docs/framework/winforms/controls/implement-two-way-com-between-dhtml-and-client.md)  
 [WebBrowser 安全性](../../../../docs/framework/winforms/controls/webbrowser-security.md)
