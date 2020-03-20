---
title: JSONP
ms.date: 03/30/2017
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
ms.openlocfilehash: 6b5b42285539c2334bccaa04e1ba179d2cf0046c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183578"
---
# <a name="jsonp"></a>JSONP
此範例示範如何在 WCF REST 服務中支援 JSON with Padding (JSONP)。 JSONP 是一項慣例，透過在目前文件中產生指令碼標記，用來叫用 (Invoke) 跨網域指令碼。 結果會傳回到指定的回呼函式 (Callback Function)。 JSONP 基於這樣的理念：標記（如`<script src="http://..." >`可以評估來自任何域的腳本）以及這些標記檢索的腳本在可能已定義其他函數的作用域內進行評估。

## <a name="demonstrates"></a>示範
 使用 JSONP 撰寫的跨網域指令碼。

## <a name="discussion"></a>討論區
 此範例包含的網頁會在該網頁呈現在瀏覽器中之後，以動態方式加入指令碼區塊。 此指令碼區塊會呼叫具有單一作業 `GetCustomer` 的 WCF REST 服務。 WCF REST 服務會傳回回呼函式名稱中所包裝的客戶名稱和位址。 當 WCF REST 服務回應時，系統會使用客戶資料叫用網頁上的回呼函式，而且回呼函式會將資料顯示在網頁上。 插入指令碼標記與執行回呼函式是由 ASP.NET AJAX ScriptManager 控制項自動處理。 使用模式與使用所有 ASP.NET AJAX Proxy 相同，但是要加入一行來啟用 JSONP，如下列程式碼所示：

```csharp
var proxy = new JsonpAjaxService.CustomerService();
proxy.set_enableJsonp(true);
proxy.GetCustomer(onSuccess, onFail, null);
```

 網頁可以呼叫 WCF REST 服務，因為此服務使用的是 <xref:System.ServiceModel.Description.WebScriptEndpoint>，且 `crossDomainScriptAccessEnabled` 設定為 `true`。 這兩種配置都在\<系統下的 Web.config 檔中完成>。

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

 ScriptManager 會管理與服務的互動，並隱藏手動實作 JSONP 存取的複雜度。 當`crossDomainScriptAccessEnabled`設置為`true`，並且操作的回應格式為 JSON 時，WCF 基礎結構將檢查回檔查詢字串參數請求的 URI，並將 JSON 回應與回檔查詢字串參數的值包起來。 在此範例中，網頁會使用下列 URI 呼叫 WCF REST 服務。

```http
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0
```

 回呼查詢字串參數的值為 `JsonPCallback`，因此 WCF 服務會傳回 JSONP 回應，如下列範例所示。

```json
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});
```

 這個 JSONP 回應包含格式化為 JSON，且以網頁要求之回呼函式名稱包裝的客戶資料。 ScriptManager 將會使用指令碼標記執行這個回呼以達成跨網域要求，然後將結果傳遞到 onSuccess 標頭，這個標頭會傳遞到 ASP.NET AJAX Proxy 的 GetCustomer 作業。

 該示例由兩個ASP.NET Web 應用程式組成：一個僅包含 WCF 服務，另一個包含調用該服務的 .aspx 網頁。 運行解決方案時，Visual Studio 2012 將在不同的埠上託管這兩個網站，從而創建服務和用戶端在不同域中生存的環境。

> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。 此範例位於下列目錄。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a>執行範例  
  
1. 開啟 JSONP 範例的方案。  
  
2. 按 F5`http://localhost:26648/JSONPClientPage.aspx`在瀏覽器中啟動。  
  
3. 請注意，頁面載入後，"名稱"和"位址"的文本輸入由值填充。  這些值是在瀏覽器完成呈現頁面後，從對 WCF 服務的調用中提供的。
