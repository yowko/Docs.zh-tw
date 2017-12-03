---
title: "Windows Forms 用戶端中的資料繫結"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2a30b37-d6e2-4552-820e-e60b2bbe8829
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 905d010c1ecdab1fc7b2c99e6d720b85ad40be32
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="data-binding-in-a-windows-forms-client"></a><span data-ttu-id="d8a27-102">Windows Forms 用戶端中的資料繫結</span><span class="sxs-lookup"><span data-stu-id="d8a27-102">Data Binding in a Windows Forms Client</span></span>
<span data-ttu-id="d8a27-103">這個範例會示範如何在 Windows Form 應用程式中繫結 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務所傳回的資料。</span><span class="sxs-lookup"><span data-stu-id="d8a27-103">This sample demonstrates how to bind to data returned by a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service in a Windows Forms application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d8a27-104">此範例的安裝程序與建置指示位於本文的結尾。</span><span class="sxs-lookup"><span data-stu-id="d8a27-104">The setup procedure and build instructions for this sample are located at the end of this article.</span></span>  
  
 <span data-ttu-id="d8a27-105">這個範例會示範實作可定義要求-回覆通訊模式之合約的服務。</span><span class="sxs-lookup"><span data-stu-id="d8a27-105">This sample demonstrates a service that implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="d8a27-106">此範例是由用戶端 Windows Forms 應用程式 (.exe)，以及網際網路資訊服務 (IIS) 裝載的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務所組成。</span><span class="sxs-lookup"><span data-stu-id="d8a27-106">The sample consists of a client Windows Forms application (.exe) and a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service hosted by Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="d8a27-107">合約是由 `IWeatherService` 介面所定義，而該介面會公開 (Expose) 名為 `GetWeatherData` 的作業。</span><span class="sxs-lookup"><span data-stu-id="d8a27-107">The contract is defined by the `IWeatherService` interface, which exposes an operation named `GetWeatherData`.</span></span> <span data-ttu-id="d8a27-108">這項作業會接受城市陣列並傳回 `WeatherData` 物件的陣列，而這些物件表示某個城市的最高和最低預測溫度。</span><span class="sxs-lookup"><span data-stu-id="d8a27-108">This operation accepts an array of cities and returns an array of `WeatherData` objects that represent the high and low forecasted temperature for a city.</span></span>  
  
 <span data-ttu-id="d8a27-109">資料繫結 (Data Binding) 會發生在 Windows Forms 應用程式的用戶端上。</span><span class="sxs-lookup"><span data-stu-id="d8a27-109">The data binding occurs on the client in the Windows Forms application.</span></span> <span data-ttu-id="d8a27-110">`DataGridView` 為資料的圖形表示，定義於 Windows Forms 設計工具中。</span><span class="sxs-lookup"><span data-stu-id="d8a27-110">A `DataGridView` is defined in the Windows Forms designer, which is a graphical representation of the data.</span></span> <span data-ttu-id="d8a27-111">此外，還會建立名為 `BindingSource` 的媒介。</span><span class="sxs-lookup"><span data-stu-id="d8a27-111">An intermediary named `BindingSource` is also created.</span></span> <span data-ttu-id="d8a27-112">而 `BindingSource` 的資料來源會設為服務所傳回的資料陣列。</span><span class="sxs-lookup"><span data-stu-id="d8a27-112">The data source of `BindingSource` is set to the data array returned by the service.</span></span> <span data-ttu-id="d8a27-113">`BindingSource` 的目的在於提供資料和資料檢視之間的間接取值 (Indirection) 層。</span><span class="sxs-lookup"><span data-stu-id="d8a27-113">The purpose of the `BindingSource` is to provide a layer of indirection between the data and the data view.</span></span> <span data-ttu-id="d8a27-114">所有的資料互動 (例如巡覽、排序、篩選和更新) 都會透過呼叫 `BindingSource` 元件來完成。</span><span class="sxs-lookup"><span data-stu-id="d8a27-114">All interaction with the data, such as navigating, sorting, filtering, and updating, is accomplished with calls to the `BindingSource` component.</span></span> <span data-ttu-id="d8a27-115">為了要完成 `DataGridView` 的資料繫結，`datasource` 的 `DataGridView` 會接著設為 `BindingSource` 物件。</span><span class="sxs-lookup"><span data-stu-id="d8a27-115">To accomplish data binding to the `DataGridView`, the `datasource` of the `DataGridView` is then set to the `BindingSource` object.</span></span> <span data-ttu-id="d8a27-116">然後，從 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務傳回的所有資料會以圖形方式顯示給使用者。</span><span class="sxs-lookup"><span data-stu-id="d8a27-116">All of the data returned from the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is then displayed graphically to the user.</span></span>  <span data-ttu-id="d8a27-117">每次使用者按一下按鈕，傳回的資料就會在資料繫結的 `DataGridView` 中自動更新。</span><span class="sxs-lookup"><span data-stu-id="d8a27-117">Every time the user clicks the button, the returned data is automatically updated in the data-bound `DataGridView`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d8a27-118">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="d8a27-118">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d8a27-119">請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="d8a27-119">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="d8a27-120">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="d8a27-120">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="d8a27-121">若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="d8a27-121">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d8a27-122">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="d8a27-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d8a27-123">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="d8a27-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d8a27-124">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="d8a27-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d8a27-125">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="d8a27-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WindowsForms`  
  
## <a name="see-also"></a><span data-ttu-id="d8a27-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8a27-126">See Also</span></span>
