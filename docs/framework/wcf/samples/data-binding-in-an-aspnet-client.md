---
title: "ASP.NET 用戶端中的資料繫結"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68b49fa6-94e7-4d4c-a34e-902a2b3770b6
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 18d133b8eb5bef9e6e9152ef856265c1cbe18b51
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="data-binding-in-an-aspnet-client"></a>ASP.NET 用戶端中的資料繫結
這個範例會示範如何在 Web Forms 應用程式中繫結一般 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務所傳回的資料。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 這個範例會示範實作可定義要求-回覆通訊模式之合約的服務。 此範例是由能夠從瀏覽器存取的用戶端 Web Forms 應用程式，以及由網際網路資訊服務 (IIS) 裝載的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務所組成。  
  
 服務會實作定義要求-回覆通訊模式的合約。 合約是由 `IWeatherService` 介面所定義，而該介面會公開 (Expose) 名為 `GetWeatherData` 的作業。 這項作業會接受城市陣列並傳回 `WeatherData` 物件的陣列，而這些物件表示某個城市的最高和最低預測溫度。  
  
 在 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 用戶端 .aspx 頁面上會定義 DataGrid Web 控制項，其中包含服務傳回之資料的圖形表示。 .aspx 頁面上的程式碼會呼叫 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務以取得天氣資料，然後將該資料傳回 `WeatherData` 物件的陣列。 DataGrid 指定從何處取得其資料的方式，是將 `DataSource` 屬性設定為該陣列。 呼叫 DataGrid 的 `DataBind` 方法時便會發生資料繫結。 這段程式碼包含在。`aspx` 網頁的`Page_Load`方法，所以每當使用者重新整理瀏覽器 頁面上，資料會更新在資料格中。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3.  這個範例的用戶端是在程式開發 Web 伺服器中執行的網站。 若要啟動開發 Web 伺服器，請在命令提示字元中輸入下列:"`%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`。 接下來，瀏覽至 http://localhost:8000/client。 如果要在多部電腦上執行這個範例，請使用伺服器的電腦名稱來取代用戶端的 Web.config 檔案中的 `localhost`的所有參照。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WebForms`  
  
## <a name="see-also"></a>另請參閱
