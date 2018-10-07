---
title: 基本 HTTP 服務
ms.date: 03/30/2017
ms.assetid: 27048b43-8a54-4f2a-9952-594bbfab10ad
ms.openlocfilehash: 2e4aee93341404df5f06b096a9a7bf18a3c94f56
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2018
ms.locfileid: "48844705"
---
# <a name="basic-http-service"></a>基本 HTTP 服務
此範例示範如何實作 HTTP、 RPC 的服務，也就是一般稱為"POX"(Plain Old XML) 服務 – 使用 Windows Communication Foundation (WCF) REST 程式設計模型。 這個範例是由兩個元件所組成： 自我裝載的 WCF HTTP 服務 (Service.cs) 和主控台應用程式 (Program.cs) 建立服務並給它的呼叫。  
  
## <a name="sample-details"></a>範例詳細資料  
 WCF 服務會公開 2 個作業，`EchoWithGet`和`EchoWithPost`，它會傳回當做輸入傳遞的字串。  
  
 `EchoWithGet` 作業是以 <xref:System.ServiceModel.Web.WebGetAttribute> 加上附註，表示此作業會處理 HTTP `GET` 要求。 <xref:System.ServiceModel.Web.WebGetAttribute> 不會明確地指定 <xref:System.UriTemplate>，因此，此作業預期使用查詢字串參數和名稱 `s` 來傳入輸入字串。 請注意，此服務預期的 URI 格式可以使用 <xref:System.ServiceModel.Web.WebGetAttribute.UriTemplate%2A> 屬性自訂。  
  
 `EchoWithPost` 作業是以 <xref:System.ServiceModel.Web.WebInvokeAttribute> 加上附註，表示它不是 `GET` 作業 (它有副作用)。 <xref:System.ServiceModel.Web.WebInvokeAttribute> 不會明確地指定 `Method`，因此，此作業會處理 HTTP `POST` 要求，而且這些要求在要求主體中擁有字串 (例如，以 XML 格式)。 請注意，HTTP 方法和要求的 URI 格式可以分別使用 <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> 和 <xref:System.ServiceModel.Web.WebInvokeAttribute.UriTemplate> 屬性自訂。  
  
 App.config 檔案會以預設的 <xref:System.ServiceModel.Description.WebHttpEndpoint> 設定 WCF 服務，且 <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> 屬性設定為 `true`。 如此一來，WCF 基礎結構會建立自動 HTML 說明頁`http://localhost:8000/Customers/help`，提供如何建構服務的 HTTP 要求以及如何取用服務之 HTTP 回應的相關資訊。  
  
 Program.cs 會示範如何使用 WCF 通道處理站，才能呼叫服務以及處理回應。 請注意，這只是存取 WCF 服務的其中一種方式。 您也可以使用其他 .NET Framework 類別 (例如 <xref:System.Net.HttpWebRequest> 和 <xref:System.Net.WebClient>) 來存取服務。
  
 此範例包含同時在主控台應用程式中執行的自我裝載服務和用戶端。 當主控台應用程式執行時，用戶端會對服務發出要求，然後將相關的資訊從回應寫入至主控台視窗。  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  開啟基本 Http 服務範例的方案。 當啟動 Visual Studio 2012，您必須執行為此範例的系統管理員，才能順利執行。 執行這項操作，以滑鼠右鍵按一下 [Visual Studio 2012] 圖示，然後選取**系統管理員身分執行**從內容功能表。  
  
2.  按下 CTRL+SHIFT+B 建置方案，然後按下 Ctrl+F5，在不偵錯的情況下執行主控台應用程式。 主控台視窗隨即出現，並提供執行中服務的 URI，以及執行中服務之 HTML 說明頁的 URI。 您可以隨時在瀏覽器中輸入說明頁的 URI 來檢視 HTML 說明頁。 當範例執行時，用戶端會寫入目前活動的狀態。  
  
3.  按下任何按鍵可終止此範例。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\BasicHttpService`  
