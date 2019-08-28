---
title: ASP.NET 用戶端中的資料繫結
ms.date: 03/30/2017
ms.assetid: 68b49fa6-94e7-4d4c-a34e-902a2b3770b6
ms.openlocfilehash: c5faeb99fa8fb153f1ab74f5f00786355af50016
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045098"
---
# <a name="data-binding-in-an-aspnet-client"></a>ASP.NET 用戶端中的資料繫結
這個範例會示範如何在 Web Forms 應用程式中系結一般 Windows Communication Foundation (WCF) 服務所傳回的資料。  
  
> [!NOTE]
> 此範例的安裝程序與建置指示位於本主題的結尾。  
  
 這個範例會示範實作可定義要求-回覆通訊模式之合約的服務。 此範例包含可從瀏覽器存取的用戶端 Web Forms 應用程式, 以及由 Internet Information Services (IIS) 主控的 WCF 服務。  
  
 服務會實作定義要求-回覆通訊模式的合約。 合約是由 `IWeatherService` 介面所定義，而該介面會公開 (Expose) 名為 `GetWeatherData` 的作業。 這項作業會接受城市陣列並傳回 `WeatherData` 物件的陣列，而這些物件表示某個城市的最高和最低預測溫度。  
  
 在 ASP.NET client .aspx 頁面上, 會定義 DataGrid Web 控制項, 其中包含服務所傳回之資料的圖形表示。 .Aspx 頁面上的程式碼會呼叫 WCF 服務中的氣象資料, 並將資料傳回`WeatherData`物件的陣列。 DataGrid 指定從何處取得其資料的方式，是將 `DataSource` 屬性設定為該陣列。 呼叫 DataGrid 的 `DataBind` 方法時便會發生資料繫結。 所有此程式碼都包含在內。`aspx` 頁面的`Page_Load`方法, 如此一來, 每當使用者重新整理瀏覽器頁面時, 資料就會在 DataGrid 中更新。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3. 這個範例的用戶端是在程式開發 Web 伺服器中執行的網站。 若要啟動開發 Web 服務器, 請在命令提示字元中輸入下列`%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`命令:。 然後流覽至`http://localhost:8000/client`。 如果要在多部電腦上執行這個範例，請使用伺服器的電腦名稱來取代用戶端的 Web.config 檔案中的 `localhost`的所有參照。  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> 如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。 此範例位於下列目錄。  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WebForms`
