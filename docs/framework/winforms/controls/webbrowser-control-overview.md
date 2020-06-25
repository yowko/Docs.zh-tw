---
title: WebBrowser 控制項概觀
description: 瞭解如何使用 WebBrowser 控制項，在單一應用程式中順暢地結合 Web 控制項與 Windows Forms 控制項。
ms.date: 03/30/2017
f1_keywords:
- WebBrowser
helpviewer_keywords:
- WebBrowser control [Windows Forms], about
- Web pages [Windows Forms], displaying in applications
ms.assetid: 6e3e1cc2-9c48-4136-9659-e99e4e60b7e9
ms.openlocfilehash: 6a0548bb0f5905d8f848ab13fb82d32b50caa891
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325745"
---
# <a name="webbrowser-control-overview"></a>WebBrowser 控制項概觀
<xref:System.Windows.Forms.WebBrowser>控制項提供 WebBrowser ActiveX 控制項的 managed 包裝函式。 受控包裝函式可讓您在 Windows Forms 用戶端應用程式中顯示網頁。 您可以使用 <xref:System.Windows.Forms.WebBrowser> 控制項來複製應用程式中的 Internet Explorer 網頁流覽功能，也可以停用預設的 Internet explorer 功能，並使用此控制項做為簡單的 HTML 檔案檢視器。 您也可以使用控制項，將 DHTML 型使用者介面專案新增至表單，並隱藏控制項中所裝載的事實 <xref:System.Windows.Forms.WebBrowser> 。 這種方法可讓您在單一應用程式中順暢地結合 Web 控制項與 Windows Forms 控制項。  
  
## <a name="frequently-used-properties-methods-and-events"></a>經常使用的屬性、方法和事件  
 <xref:System.Windows.Forms.WebBrowser>控制項有數個屬性、方法和事件，可讓您用來執行 Internet Explorer 中找到的控制項。 例如，您可以使用 `Navigate` 方法來執行網址列，以及 `GoBack` 、 `GoForward` 、 `Stop` 和 `Refresh` 方法，以在工具列上執行導覽按鈕。 您可以使用屬性的值 `Navigated` 和標題列，以屬性的值來處理事件，以更新網址列 `Url` `DocumentTitle` 。  
  
 如果您想要在應用程式內產生自己的頁面內容，您可以設定 `DocumentText` 屬性。 如果您熟悉 HTML 檔案物件模型（DOM），您也可以透過屬性操作目前網頁的內容 `Document` 。 使用此屬性，您可以在記憶體中儲存和修改檔，而不是在檔案之間流覽。  
  
 `Document`屬性也可讓您從用戶端應用程式程式碼呼叫在網頁腳本中實作為的方法。 若要從您的腳本程式碼存取您的用戶端應用程式程式碼，請設定 `ObjectForScripting` 屬性。 您所指定的物件可以由您的腳本當做物件來存取 `window.external` 。  
  
|Name|說明|  
|----------|-----------------|  
|<xref:System.Windows.Forms.WebBrowser.Document%2A> 屬性|取得物件，這個物件提供對目前網頁之 HTML 檔案物件模型（DOM）的 managed 存取。|  
|<xref:System.Windows.Forms.WebBrowser.DocumentCompleted> 事件|發生于網頁載入完成時。|  
|<xref:System.Windows.Forms.WebBrowser.DocumentText%2A> 屬性|取得或設定目前網頁的 HTML 內容。|  
|<xref:System.Windows.Forms.WebBrowser.DocumentTitle%2A> 屬性|取得目前網頁的標題。|  
|<xref:System.Windows.Forms.WebBrowser.GoBack%2A> 方法|導覽至歷程記錄中的前一頁。|  
|<xref:System.Windows.Forms.WebBrowser.GoForward%2A> 方法|導覽至歷程記錄中的下一頁。|  
|<xref:System.Windows.Forms.WebBrowser.Navigate%2A> 方法|流覽至指定的 URL。|  
|<xref:System.Windows.Forms.WebBrowser.Navigating> 事件|在導覽開始之前發生，可讓動作取消。|  
|<xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> 屬性|取得或設定網頁腳本程式碼可以用來與您的應用程式通訊的物件。|  
|<xref:System.Windows.Forms.WebBrowser.Print%2A> 方法|列印目前的網頁。|  
|<xref:System.Windows.Forms.WebBrowser.Refresh%2A> 方法|重載目前的網頁。|  
|<xref:System.Windows.Forms.WebBrowser.Stop%2A> 方法|終止目前的導覽並停止動態頁面元素，例如音效和動畫。|  
|<xref:System.Windows.Forms.WebBrowser.Url%2A> 屬性|取得或設定目前網頁的 URL。 設定此屬性會將控制項流覽至新的 URL。|  
  
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
- [如何：使用 WebBrowser 控制項巡覽至 URL](how-to-navigate-to-a-url-with-the-webbrowser-control.md)
- [操作說明：使用 WebBrowser 控制項列印](how-to-print-with-a-webbrowser-control.md)
- [操作說明：將 Web 瀏覽器功能加入至 Windows Forms 應用程式](how-to-add-web-browser-capabilities-to-a-windows-forms-application.md)
- [操作說明：在 Windows Forms 應用程式中建立 HTML 文件檢視器](how-to-create-an-html-document-viewer-in-a-windows-forms-application.md)
- [操作說明：實作 DHTML 程式碼和用戶端應用程式程式碼之間的雙向通訊](implement-two-way-com-between-dhtml-and-client.md)
- [WebBrowser 安全性](webbrowser-security.md)
