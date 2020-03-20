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
# <a name="data-binding-in-an-aspnet-client"></a><span data-ttu-id="30cf1-102">ASP.NET 用戶端中的資料繫結</span><span class="sxs-lookup"><span data-stu-id="30cf1-102">Data Binding in an ASP.NET Client</span></span>
<span data-ttu-id="30cf1-103">此示例演示如何在 Web 表單應用程式中綁定典型 Windows 通信基礎 （WCF） 服務返回的資料。</span><span class="sxs-lookup"><span data-stu-id="30cf1-103">This sample demonstrates how to bind data returned by a typical Windows Communication Foundation (WCF) service in a Web Forms application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="30cf1-104">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="30cf1-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="30cf1-105">這個範例會示範實作可定義要求-回覆通訊模式之合約的服務。</span><span class="sxs-lookup"><span data-stu-id="30cf1-105">This sample demonstrates a service that implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="30cf1-106">該示例包括可從瀏覽器訪問的用戶端 Web 表單應用程式和由 Internet 資訊服務 （IIS） 託管的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="30cf1-106">The sample consists of a client Web Forms application accessible from a browser and a WCF service hosted by Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="30cf1-107">服務會實作定義要求-回覆通訊模式的合約。</span><span class="sxs-lookup"><span data-stu-id="30cf1-107">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="30cf1-108">合約是由 `IWeatherService` 介面所定義，而該介面會公開 (Expose) 名為 `GetWeatherData` 的作業。</span><span class="sxs-lookup"><span data-stu-id="30cf1-108">The contract is defined by the `IWeatherService` interface, which exposes an operation named `GetWeatherData`.</span></span> <span data-ttu-id="30cf1-109">這項作業會接受城市陣列並傳回 `WeatherData` 物件的陣列，而這些物件表示某個城市的最高和最低預測溫度。</span><span class="sxs-lookup"><span data-stu-id="30cf1-109">This operation accepts an array of cities and returns an array of `WeatherData` objects that represent the high and low forecasted temperature for a city.</span></span>  
  
 <span data-ttu-id="30cf1-110">在ASP.NET用戶端 .aspx 頁上，定義了 DataGrid Web 控制項，其中包含服務返回的資料的圖形表示形式。</span><span class="sxs-lookup"><span data-stu-id="30cf1-110">On the ASP.NET client .aspx page, a DataGrid Web control is defined, which contains the graphical representation of the data returned by the service.</span></span> <span data-ttu-id="30cf1-111">.aspx 頁上的代碼調用 WCF 服務以訪問天氣資料，並將資料返回到`WeatherData`物件陣列。</span><span class="sxs-lookup"><span data-stu-id="30cf1-111">Code on the .aspx page calls the WCF service for weather data and returns the data to an array of `WeatherData` objects.</span></span> <span data-ttu-id="30cf1-112">DataGrid 指定從何處取得其資料的方式，是將 `DataSource` 屬性設定為該陣列。</span><span class="sxs-lookup"><span data-stu-id="30cf1-112">The DataGrid specifies where to get its data from by setting its `DataSource` property to that array.</span></span> <span data-ttu-id="30cf1-113">呼叫 DataGrid 的 `DataBind` 方法時便會發生資料繫結。</span><span class="sxs-lookup"><span data-stu-id="30cf1-113">The data binding occurs with a call to the DataGrid's `DataBind` method.</span></span> <span data-ttu-id="30cf1-114">所有這些代碼都包含在 中。`aspx`</span><span class="sxs-lookup"><span data-stu-id="30cf1-114">All of this code is contained inside the .`aspx`</span></span> <span data-ttu-id="30cf1-115">頁面`Page_Load`的方法，因此每次使用者刷新瀏覽器頁面時，資料都會在 DataGrid 中更新。</span><span class="sxs-lookup"><span data-stu-id="30cf1-115">page's `Page_Load` method, so every time the user refreshes the browser page, the data is updated in the DataGrid.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="30cf1-116">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="30cf1-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="30cf1-117">確保已為 Windows[通信基礎示例執行一次性設置過程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="30cf1-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="30cf1-118">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="30cf1-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="30cf1-119">這個範例的用戶端是在程式開發 Web 伺服器中執行的網站。</span><span class="sxs-lookup"><span data-stu-id="30cf1-119">This sample's client is a Web site that runs under a development Web server.</span></span> <span data-ttu-id="30cf1-120">要啟動開發 Web 服務器，在命令提示符下鍵入以下內容`%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`： 。</span><span class="sxs-lookup"><span data-stu-id="30cf1-120">To launch the development Web server, type the following at the command prompt: `%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`.</span></span> <span data-ttu-id="30cf1-121">然後流覽到`http://localhost:8000/client`。</span><span class="sxs-lookup"><span data-stu-id="30cf1-121">Then browse to `http://localhost:8000/client`.</span></span> <span data-ttu-id="30cf1-122">如果要在多部電腦上執行這個範例，請使用伺服器的電腦名稱來取代用戶端的 Web.config 檔案中的 的所有參照。</span><span class="sxs-lookup"><span data-stu-id="30cf1-122">To run this sample across computers, replace all references to `localhost` in the client's Web.config file with the computer name of the server.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="30cf1-123">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="30cf1-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="30cf1-124">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="30cf1-124">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="30cf1-125">如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。</span><span class="sxs-lookup"><span data-stu-id="30cf1-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="30cf1-126">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="30cf1-126">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WebForms`
