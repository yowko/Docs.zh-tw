---
title: 基本 HTTP 服務
ms.date: 03/30/2017
ms.assetid: 27048b43-8a54-4f2a-9952-594bbfab10ad
ms.openlocfilehash: ec716b41efb3dde6e5afdb386d797e402d924b56
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045151"
---
# <a name="basic-http-service"></a>基本 HTTP 服務

這個範例會示範如何使用 Windows Communication Foundation (WCF) REST 程式設計模型, 來執行以 HTTP 為基礎、以 RPC 為基礎的服務也就一般, 稱為 "POX" (純舊 XML) 服務。 這個範例是由兩個元件所組成: 自我裝載的 WCF HTTP 服務 (Service.cs) 和主控台應用程式 (Program.cs), 它會建立服務並呼叫它。

## <a name="sample-details"></a>範例詳細資料

WCF 服務會公開2個作業`EchoWithGet` , `EchoWithPost`和, 其會傳回當做輸入傳遞的字串。

`EchoWithGet` 作業是以 <xref:System.ServiceModel.Web.WebGetAttribute> 標註，表示此作業會處理 HTTP `GET` 要求。 <xref:System.ServiceModel.Web.WebGetAttribute> 不會明確地指定 <xref:System.UriTemplate>，因此，此作業預期使用查詢字串參數和名稱 `s` 來傳入輸入字串。 請注意，此服務預期的 URI 格式可以使用 <xref:System.ServiceModel.Web.WebGetAttribute.UriTemplate%2A> 屬性自訂。

`EchoWithPost` 作業是以 <xref:System.ServiceModel.Web.WebInvokeAttribute> 標註，表示它不是 `GET` 作業 (它有副作用)。 <xref:System.ServiceModel.Web.WebInvokeAttribute> 不會明確地指定 `Method`，因此，此作業會處理 HTTP `POST` 要求，而且這些要求在要求主體中擁有字串 (例如，以 XML 格式)。 請注意，HTTP 方法和要求的 URI 格式可以分別使用 <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> 和 <xref:System.ServiceModel.Web.WebInvokeAttribute.UriTemplate> 屬性自訂。

App.config 檔案會以預設的 <xref:System.ServiceModel.Description.WebHttpEndpoint> 設定 WCF 服務，且 <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> 屬性設定為 `true`。 因此, WCF 基礎結構會在`http://localhost:8000/Customers/help`中建立自動 HTML 說明頁面, 其中提供如何對服務建立 HTTP 要求, 以及如何取用服務的 HTTP 回應的相關資訊。

Program.cs 會示範如何使用 WCF 通道處理站來呼叫服務和進程回應。 請注意，這只是存取 WCF 服務的其中一種方式。 您也可以使用其他 .NET Framework 類別 (例如 <xref:System.Net.HttpWebRequest> 和 <xref:System.Net.WebClient>) 來存取服務。

此範例包含同時在主控台應用程式中執行的自我裝載服務和用戶端。 當主控台應用程式執行時，用戶端會對服務發出要求，然後將相關的資訊從回應寫入至主控台視窗。

#### <a name="to-use-this-sample"></a>若要使用這個範例

1. 開啟基本 Http 服務範例的方案。 當啟動 Visual Studio 2012 時, 您必須以系統管理員身分執行, 才能讓範例成功執行。 方法是以滑鼠右鍵按一下 [Visual Studio 2012] 圖示, 然後從內容功能表選取 [以**系統管理員身分執行**]。

2. 按下 CTRL+SHIFT+B 建置方案，然後按下 Ctrl+F5，在不偵錯的情況下執行主控台應用程式。 主控台視窗隨即出現，並提供執行中服務的 URI，以及執行中服務之 HTML 說明頁的 URI。 您可以隨時在瀏覽器中輸入說明頁的 URI 來檢視 HTML 說明頁。 當範例執行時，用戶端會寫入目前活動的狀態。

3. 按下任何按鍵可終止此範例。

> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> 如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。 此範例位於下列目錄。
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\BasicHttpService`
