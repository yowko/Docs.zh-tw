---
title: JSONP
ms.date: 03/30/2017
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
ms.openlocfilehash: bd5d9afcfa35e598191db1d125418686f5dd0af1
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510354"
---
# <a name="jsonp"></a>JSONP
此範例示範如何在 WCF REST 服務中支援 JSON with Padding (JSONP)。 JSONP 是一項慣例，透過在目前文件中產生指令碼標記，用來叫用 (Invoke) 跨網域指令碼。 結果會傳回到指定的回呼函式 (Callback Function)。 JSONP 的基礎概念是，這類`<script src="http://..." >`可以評估來自任何網域的指令碼，而這些標記擷取的指令碼會以其他函式可能已定義範圍內評估。  
  
## <a name="demonstrates"></a>示範  
 使用 JSONP 撰寫的跨網域指令碼。  
  
## <a name="discussion"></a>討論  
 此範例包含的網頁會在該網頁呈現在瀏覽器中之後，以動態方式加入指令碼區塊。 此指令碼區塊會呼叫具有單一作業 `GetCustomer` 的 WCF REST 服務。 WCF REST 服務會傳回回呼函式名稱中所包裝的客戶名稱和位址。 當 WCF REST 服務回應時，系統會使用客戶資料叫用網頁上的回呼函式，而且回呼函式會將資料顯示在網頁上。 插入指令碼標記與執行回呼函式是由 ASP.NET AJAX ScriptManager 控制項自動處理。 使用模式與使用所有 ASP.NET AJAX Proxy 相同，但是要加入一行來啟用 JSONP，如下列程式碼所示：  
  
```csharp  
var proxy = new JsonpAjaxService.CustomerService();  
proxy.set_enableJsonp(true);  
proxy.GetCustomer(onSuccess, onFail, null);  
```  
  
 網頁可以呼叫 WCF REST 服務，因為此服務使用的是 <xref:System.ServiceModel.Description.WebScriptEndpoint>，且 `crossDomainScriptAccessEnabled` 設定為 `true`。 這兩種設定下的 Web.config 檔案中完成\<system.serviceModel > 項目。  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
  <standardEndpoints>  
    <webScriptEndpoint>  
      <standardEndpoint name="" crossDomainScriptAccessEnabled="true"/>  
    </webScriptEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 ScriptManager 會管理與服務的互動，並隱藏手動實作 JSONP 存取的複雜度。 當`crossDomainScriptAccessEnabled`設為`true`和作業的回應格式是 JSON，WCF 基礎結構會檢查回呼查詢字串參數要求的 URI，並包裝 JSON 回應的回呼查詢字串值參數。 在此範例中，網頁會使用下列 URI 呼叫 WCF REST 服務。  
  
```  
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0  
```  
  
 回呼查詢字串參數的值為 `JsonPCallback`，因此 WCF 服務會傳回 JSONP 回應，如下列範例所示。  
  
```  
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});  
```  
  
 這個 JSONP 回應包含格式化為 JSON，且以網頁要求之回呼函式名稱包裝的客戶資料。 ScriptManager 將會使用指令碼標記執行這個回呼以達成跨網域要求，然後將結果傳遞到 onSuccess 標頭，這個標頭會傳遞到 ASP.NET AJAX Proxy 的 GetCustomer 作業。  
  
 此範例包含兩個 ASP.NET web 應用程式： 一個包含只是 WCF 服務，而另一個包含的.aspx 網頁，它會呼叫服務。 執行方案時，[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 將會在不同的連接埠上裝載兩個網站，這樣就可以建立一個服務和用戶端存留在不同網域上的環境。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a>若要執行範例  
  
1.  開啟 JSONP 範例的方案。  
  
2.  按 F5 以啟動`http://localhost:26648/JSONPClientPage.aspx`瀏覽器中。  
  
3.  請注意，在頁面載入之後，"Name"和"Address"的文字輸入會以值填入。  瀏覽器完成頁面的呈現之後從 WCF 服務的呼叫提供這些值。
