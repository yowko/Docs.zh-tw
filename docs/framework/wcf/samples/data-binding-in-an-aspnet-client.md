---
title: ASP.NET 用戶端中的資料繫結
ms.date: 03/30/2017
ms.assetid: 68b49fa6-94e7-4d4c-a34e-902a2b3770b6
ms.openlocfilehash: c068c1cab5a5b9dad75e781e58076f4066a3b2a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145003"
---
# <a name="data-binding-in-an-aspnet-client"></a>ASP.NET 用戶端中的資料繫結
此示例演示如何在 Web 表單應用程式中綁定典型 Windows 通信基礎 （WCF） 服務返回的資料。  
  
> [!NOTE]
> 此範例的安裝程序與建置指示位於本主題的結尾。  
  
 這個範例會示範實作可定義要求-回覆通訊模式之合約的服務。 該示例包括可從瀏覽器訪問的用戶端 Web 表單應用程式和由 Internet 資訊服務 （IIS） 託管的 WCF 服務。  
  
 服務會實作定義要求-回覆通訊模式的合約。 合約是由 `IWeatherService` 介面所定義，而該介面會公開 (Expose) 名為 `GetWeatherData` 的作業。 這項作業會接受城市陣列並傳回 `WeatherData` 物件的陣列，而這些物件表示某個城市的最高和最低預測溫度。  
  
 在ASP.NET用戶端 .aspx 頁上，定義了 DataGrid Web 控制項，其中包含服務返回的資料的圖形表示形式。 .aspx 頁上的代碼調用 WCF 服務以訪問天氣資料，並將資料返回到`WeatherData`物件陣列。 DataGrid 指定從何處取得其資料的方式，是將 `DataSource` 屬性設定為該陣列。 呼叫 DataGrid 的 `DataBind` 方法時便會發生資料繫結。 所有這些代碼都包含在 中。`aspx` 頁面`Page_Load`的方法，因此每次使用者刷新瀏覽器頁面時，資料都會在 DataGrid 中更新。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 確保已為 Windows[通信基礎示例執行一次性設置過程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3. 這個範例的用戶端是在程式開發 Web 伺服器中執行的網站。 要啟動開發 Web 服務器，在命令提示符下鍵入以下內容`%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`： 。 然後流覽到`http://localhost:8000/client`。 如果要在多部電腦上執行這個範例，請使用伺服器的電腦名稱來取代用戶端的 Web.config 檔案中的 的所有參照。  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。 此範例位於下列目錄。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WebForms`
