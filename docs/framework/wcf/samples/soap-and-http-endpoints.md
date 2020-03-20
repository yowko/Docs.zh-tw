---
title: SOAP 及 HTTP 端點
ms.date: 03/30/2017
ms.assetid: e3c8be75-9dda-4afa-89b6-a82cb3b73cf8
ms.openlocfilehash: f10b1aa4514aee50c0c0d17cabdb9516a3ca7584
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144015"
---
# <a name="soap-and-http-endpoints"></a>SOAP 及 HTTP 端點
此示例演示如何實現基於 RPC 的服務，並使用 WCF Web 程式設計模型以 SOAP 格式和"純舊 XML"（POX） 格式公開該服務。 有關服務 HTTP 綁定的更多詳細資訊，請參閱[基本 HTTP 服務](../../../../docs/framework/wcf/samples/basic-http-service.md)示例。 這個範例的重點在於，使用不同繫結透過 SOAP 和 HTTP 公開相同服務的相關詳細資料。  
  
## <a name="demonstrates"></a>示範  
 使用 WCF 通過 SOAP 和 HTTP 公開 RPC 服務。  
  
## <a name="discussion"></a>討論區  
 此示例由兩個元件組成：包含 WCF 服務的 Web 應用程式專案（服務）和使用 SOAP 和 HTTP 綁定調用服務操作的主控台應用程式（用戶端）。  
  
 WCF 服務公開了 2`GetData`個`PutData`操作 ，並且與作為輸入傳遞的字串相呼應。 服務作業會以 <xref:System.ServiceModel.Web.WebGetAttribute> 和 <xref:System.ServiceModel.Web.WebInvokeAttribute> 標註。 這些屬性會控制這些作業的 HTTP 投射。 此外，這些作業還會以 <xref:System.ServiceModel.OperationContractAttribute> 標註，這個屬性可讓作業透過 SOAP 繫結公開。 服務的 `PutData` 方法會擲回 <xref:System.ServiceModel.Web.WebFaultException>，它會使用 HTTP 狀態碼透過 HTTP 送回，以及透過 SOAP 做為 SOAP 錯誤送回。  
  
 Web.config 檔配置具有 3 個終結點的 WCF 服務：  
  
- ~/service.svc/mex 端點，這個端點會公開服務中繼資料讓 SOAP 用戶端存取。  
  
- ~/service.svc/http 端點，這個端點會讓用戶端使用 HTTP 繫結存取服務。  
  
- ~/service.svc/soap 端點，這個端點可讓用戶端使用 SOAP over HTTP 繫結存取服務。  
  
 HTTP 終結點配置了已`webHttp``helpEnabled`設置為`true`> 標準終結點<。 因此，服務會在 HTTP 用戶端可用來存取服務的 ~/service.svc/http/help 公開 XHTML 說明頁。  
  
 用戶端專案演示使用 SOAP 代理（通過**添加服務引用**生成）訪問服務，並使用 訪問服務<xref:System.Net.WebClient>。  
  
 這個範例包含 Web 主控服務和主控台應用程式。 當主控台應用程式執行時，用戶端會對服務發出要求，然後將相關的資訊從回應寫入至主控台視窗。  
  
#### <a name="to-run-the-sample"></a>執行範例  
  
1. 開啟「SOAP 和 HTTP 端點範例」的方案。  
  
2. 按 CTRL+SHIFT+B 建置解決方案。  
  
3. 如果尚未打開，請按 CTRL+W，S 打開**解決方案資源管理器**視窗。  
  
4. 在 **"解決方案資源管理器"** 視窗中，按右鍵 **"服務**"專案並將游標放在 **"調試**上下文"功能表選項上，以便顯示 **"開始新實例"** 內容功能表。 按一下 **"啟動新實例**"。 這樣會啟動裝載服務的 ASP.NET 程式開發伺服器。  
  
5. 在"解決方案資源管理器"視窗中，按右鍵"用戶端"專案並將游標放在 **"調試上下文"** 功能表選項上，以便顯示 **"開始新實例"** 內容功能表。 按一下 **"啟動新實例**"。  
  
6. 用戶端主控台視窗隨即出現，並提供執行中服務的 URI，以及執行中服務之 HTML 說明頁的 URI。 您可以隨時在瀏覽器中輸入說明頁的 URI 來檢視 HTML 說明頁。  
  
7. 當範例執行時，用戶端會寫入目前活動的狀態。  
  
8. 按下任何按鍵可終止用戶端主控台應用程式。  
  
9. 按 SHIFT+F5 停止對服務偵錯。  
  
10. 在 Windows 通知區域中，按右鍵ASP.NET開發伺服器圖示，然後從內容功能表中選擇 **"停止**"。  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。 此範例位於下列目錄。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\SoapAndHttpEndpoints`
