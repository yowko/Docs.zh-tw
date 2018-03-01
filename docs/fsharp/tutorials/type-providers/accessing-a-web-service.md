---
title: "逐步解說-使用型別提供者 （F #） 來存取 Web 服務"
description: "了解如何使用在 F # 3.0 中使用的 Web 服務描述語言 (WSDL) 型別提供者來存取 WSDL 服務。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 63374fa9-8fb8-43ac-bcb9-ef2290d9f851
ms.openlocfilehash: 2929198172a4e9f908daa64af19208e07859263f
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
---
# <a name="walkthrough-accessing-a-web-service-by-using-type-providers"></a><span data-ttu-id="958dc-104">逐步解說：使用型別提供者存取 Web 服務</span><span class="sxs-lookup"><span data-stu-id="958dc-104">Walkthrough: Accessing a Web Service by Using Type Providers</span></span>

> [!NOTE]
<span data-ttu-id="958dc-105">本指南針對 F # 3.0 所撰寫，而且會更新。</span><span class="sxs-lookup"><span data-stu-id="958dc-105">This guide was written for F# 3.0 and will be updated.</span></span>  <span data-ttu-id="958dc-106">請參閱 [FSharp.Data](https://fsharp.github.io/FSharp.Data/) 以取得最新的跨平台型別提供者。</span><span class="sxs-lookup"><span data-stu-id="958dc-106">See [FSharp.Data](https://fsharp.github.io/FSharp.Data/) for up-to-date, cross-platform type providers.</span></span>

> [!NOTE]
<span data-ttu-id="958dc-107">應用程式開發介面參考連結將帶您到 MSDN。</span><span class="sxs-lookup"><span data-stu-id="958dc-107">The API reference links will take you to MSDN.</span></span>  <span data-ttu-id="958dc-108">docs.microsoft.com API 參考不完整。</span><span class="sxs-lookup"><span data-stu-id="958dc-108">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="958dc-109">本逐步解說將示範如何使用在 F # 3.0 來存取 WSDL 服務中使用的 Web 服務描述語言 (WSDL) 型別提供者。</span><span class="sxs-lookup"><span data-stu-id="958dc-109">This walkthrough shows you how to use the Web Services Description Language (WSDL) type provider that is available in F# 3.0 to access a WSDL service.</span></span> <span data-ttu-id="958dc-110">在其他.NET 語言中，產生的程式碼來存取 web 服務呼叫 svcutil.exe，藉由加入 web 參考，比方說，C# 專案或取得 Visual Studio 為您呼叫 svcutil.exe。</span><span class="sxs-lookup"><span data-stu-id="958dc-110">In other .NET languages, you generate the code to access the web service by calling svcutil.exe, or by adding a web reference in, for example, a C# project to get Visual Studio to call svcutil.exe for you.</span></span> <span data-ttu-id="958dc-111">在 F # 中，您有其他選項可使用 WSDL 的型別提供者，因此只要您撰寫的程式碼會建立 wsdlservice 型別、 型別產生並變成可用。</span><span class="sxs-lookup"><span data-stu-id="958dc-111">In F#, you have the additional option of using the WSDL type provider, so as soon as you write the code that creates the WsdlService type, the types are generated and become available.</span></span> <span data-ttu-id="958dc-112">此程序依賴您撰寫程式碼時所使用的服務。</span><span class="sxs-lookup"><span data-stu-id="958dc-112">This process relies on the service being available when you are writing the code.</span></span>

<span data-ttu-id="958dc-113">這個逐步解說將說明下列工作。</span><span class="sxs-lookup"><span data-stu-id="958dc-113">This walkthrough illustrates the following tasks.</span></span> <span data-ttu-id="958dc-114">您必須完成它們依此順序順利完成此逐步解說：</span><span class="sxs-lookup"><span data-stu-id="958dc-114">You must complete them in this order for the walkthrough to succeed:</span></span>


- <span data-ttu-id="958dc-115">建立專案</span><span class="sxs-lookup"><span data-stu-id="958dc-115">Creating the project</span></span>
<br />

- <span data-ttu-id="958dc-116">設定型別提供者</span><span class="sxs-lookup"><span data-stu-id="958dc-116">Configuring the type provider</span></span>
<br />

- <span data-ttu-id="958dc-117">呼叫 web 服務，並處理結果</span><span class="sxs-lookup"><span data-stu-id="958dc-117">Calling the web service, and processing the results</span></span>
<br />


## <a name="creating-the-project"></a><span data-ttu-id="958dc-118">建立專案</span><span class="sxs-lookup"><span data-stu-id="958dc-118">Creating the project</span></span>
<span data-ttu-id="958dc-119">在步驟中，您可以建立專案，並加入適當的參考，以使用 WSDL 型別提供者。</span><span class="sxs-lookup"><span data-stu-id="958dc-119">In the step, you create a project and add the appropriate references to use a WSDL type provider.</span></span>


#### <a name="to-create-and-set-up-an-f-project"></a><span data-ttu-id="958dc-120">若要建立並設定 F# 專案</span><span class="sxs-lookup"><span data-stu-id="958dc-120">To create and set up an F# project</span></span>

1. <span data-ttu-id="958dc-121">開啟新的 F # 主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="958dc-121">Open a new F# Console Application project.</span></span>
<br />

2. <span data-ttu-id="958dc-122">在**方案總管 中**，開啟專案的捷徑功能表**參考** 節點，然後選擇 **加入參考**。</span><span class="sxs-lookup"><span data-stu-id="958dc-122">In **Solution Explorer**, open the shortcut menu for the project's **Reference** node, and then choose **Add Reference**.</span></span>
<br />

3. <span data-ttu-id="958dc-123">在**組件**區域中，選擇**Framework**，然後在可用組件清單中，選擇  **System.Runtime.Serialization**和**System.ServiceModel**。</span><span class="sxs-lookup"><span data-stu-id="958dc-123">In the **Assemblies** area, choose **Framework**, and then, in the list of available assemblies, choose **System.Runtime.Serialization** and **System.ServiceModel**.</span></span>
<br />

4. <span data-ttu-id="958dc-124">在**組件**區域中，選擇**延伸**。</span><span class="sxs-lookup"><span data-stu-id="958dc-124">In the **Assemblies** area, choose **Extensions**.</span></span>
<br />

5. <span data-ttu-id="958dc-125">在可用組件清單中，選擇  **FSharp.Data.TypeProviders**，然後選擇  **確定**按鈕以加入這些組件的參考。</span><span class="sxs-lookup"><span data-stu-id="958dc-125">In the list of available assemblies, choose **FSharp.Data.TypeProviders**, and then choose the **OK** button to add references to these assemblies.</span></span>
<br />

## <a name="configuring-the-type-provider"></a><span data-ttu-id="958dc-126">設定型別提供者</span><span class="sxs-lookup"><span data-stu-id="958dc-126">Configuring the type provider</span></span>
<span data-ttu-id="958dc-127">在此步驟中，您可以使用 WSDL 型別提供者產生 TerraServer web 服務的型別。</span><span class="sxs-lookup"><span data-stu-id="958dc-127">In this step, you use the WSDL type provider to generate types for the TerraServer web service.</span></span>


#### <a name="to-configure-the-type-provider-and-generate-types"></a><span data-ttu-id="958dc-128">若要設定型別提供者和產生類型</span><span class="sxs-lookup"><span data-stu-id="958dc-128">To configure the type provider and generate types</span></span>

1. <span data-ttu-id="958dc-129">加入下列程式碼，以開啟型別提供者命名空間。</span><span class="sxs-lookup"><span data-stu-id="958dc-129">Add the following line of code to open the type provider namespace.</span></span>
<br />

```fsharp
open System
open System.ServiceModel
open Microsoft.FSharp.Linq
open Microsoft.FSharp.Data.TypeProviders
```

2. <span data-ttu-id="958dc-130">加入下列程式碼來叫用 web 服務的型別提供者。</span><span class="sxs-lookup"><span data-stu-id="958dc-130">Add the following line of code to invoke the type provider with a web service.</span></span> <span data-ttu-id="958dc-131">在此範例中，使用 TerraServer web 服務。</span><span class="sxs-lookup"><span data-stu-id="958dc-131">In this example, use the TerraServer web service.</span></span>
<br />

```fsharp
type TerraService = WsdlService<" HYPERLINK "https://terraserver-usa.com/TerraService2.asmx?WSDL" https://msrmaps.com/TerraService2.asmx?WSDL">
```

  <span data-ttu-id="958dc-132">如果服務 URI 拼錯，或者服務本身已關閉，或不執行底下這行程式碼會出現紅色曲線。</span><span class="sxs-lookup"><span data-stu-id="958dc-132">A red squiggle appears under this line of code if the service URI is misspelled or if the service itself is down or isn’t performing.</span></span> <span data-ttu-id="958dc-133">如果您指向程式碼時，錯誤訊息說明的問題。</span><span class="sxs-lookup"><span data-stu-id="958dc-133">If you point to the code, an error message describes the problem.</span></span> <span data-ttu-id="958dc-134">您可以找到相同的資訊**錯誤清單**視窗或在**輸出 視窗**建置之後。</span><span class="sxs-lookup"><span data-stu-id="958dc-134">You can find the same information in the **Error List** window or in the **Output Window** after you build.</span></span>
<br />  <span data-ttu-id="958dc-135">有兩種方式使用 app.config 檔案的專案，或使用靜態型別參數的型別提供者的宣告中指定的 WSDL 連接，組態設定。</span><span class="sxs-lookup"><span data-stu-id="958dc-135">There are two ways to specify configuration settings for a WSDL connection, by using the app.config file for the project, or by using the static type parameters in the type provider declaration.</span></span> <span data-ttu-id="958dc-136">您可以使用 svcutil.exe 來產生適當的組態檔項目。</span><span class="sxs-lookup"><span data-stu-id="958dc-136">You can use svcutil.exe to generate appropriate configuration file elements.</span></span> <span data-ttu-id="958dc-137">如需有關如何使用 svcutil.exe 來產生 web 服務的組態資訊的詳細資訊，請參閱[ServiceModel Metadata Utility Tool &#40;Svcutil.exe &#41;](https://msdn.microsoft.com/library/aa347733.aspx).</span><span class="sxs-lookup"><span data-stu-id="958dc-137">For more information about using svcutil.exe to generate configuration information for a web service, see [ServiceModel Metadata Utility Tool &#40;Svcutil.exe&#41;](https://msdn.microsoft.com/library/aa347733.aspx).</span></span> <span data-ttu-id="958dc-138">如需 WSDL 的型別提供者的靜態型別參數的完整描述，請參閱[WsdlService 類型提供者](https://msdn.microsoft.com/visualfsharpdocs/conceptual/wsdlservice-type-provider-%5bfsharp%5d)。</span><span class="sxs-lookup"><span data-stu-id="958dc-138">For a full description of the static type parameters for the WSDL type provider, see [WsdlService Type Provider](https://msdn.microsoft.com/visualfsharpdocs/conceptual/wsdlservice-type-provider-%5bfsharp%5d).</span></span>
<br />

## <a name="calling-the-web-service-and-processing-the-results"></a><span data-ttu-id="958dc-139">呼叫 web 服務，並處理結果</span><span class="sxs-lookup"><span data-stu-id="958dc-139">Calling the web service, and processing the results</span></span>
<span data-ttu-id="958dc-140">每個 web 服務都有它自己的型別，其方法呼叫做為參數集。</span><span class="sxs-lookup"><span data-stu-id="958dc-140">Each web service has its own set of types that are used as parameters for its method calls.</span></span> <span data-ttu-id="958dc-141">在此步驟中，您可以準備這些參數，呼叫 web 方法，並處理它所傳回的資訊。</span><span class="sxs-lookup"><span data-stu-id="958dc-141">In this step, you prepare these parameters, call a web method, and process the information that it returns.</span></span>


#### <a name="to-call-the-web-service-and-process-the-results"></a><span data-ttu-id="958dc-142">呼叫 web 服務，並處理結果</span><span class="sxs-lookup"><span data-stu-id="958dc-142">To call the web service, and process the results</span></span>

1. <span data-ttu-id="958dc-143">Web 服務可能會逾時或停止運作，所以您應該將 web 服務呼叫中，例外狀況處理區塊。</span><span class="sxs-lookup"><span data-stu-id="958dc-143">The web service might time out or stop functioning, so you should include the web service call in an exception handling block.</span></span> <span data-ttu-id="958dc-144">撰寫下列程式碼嘗試從 web 服務取得資料。</span><span class="sxs-lookup"><span data-stu-id="958dc-144">Write the following code to try to get data from the web service.</span></span>
<br />

```fsharp
try
  let terraClient = TerraService.GetTerraServiceSoap ()
  let myPlace = new TerraService.ServiceTypes.msrmaps.com.Place(City = "Redmond", State = "Washington", Country = "United States")
  let myLocation = terraClient.ConvertPlaceToLonLatPt(myPlace)
  printfn "Redmond Latitude: %f Longitude: %f" (myLocation.Lat) (myLocation.Lon)
with
| :? ServerTooBusyException as exn ->
  let innerMessage =
    match (exn.InnerException) with
    | null -> ""
    | innerExn -> innerExn.Message
  printfn "An exception occurred:\n %s\n %s" exn.Message innerMessage
| exn -> printfn "An exception occurred: %s" exn.Message
```

<span data-ttu-id="958dc-145">請注意，您建立的資料類型所需的 web 服務，例如**位置**和**位置**，如 wsdlservice 型底下的巢狀型別輸入**TerraService**。</span><span class="sxs-lookup"><span data-stu-id="958dc-145">Notice that you create the data types that are needed for the web service, such as **Place** and **Location**, as nested types under the WsdlService type **TerraService**.</span></span>
<br />


## <a name="see-also"></a><span data-ttu-id="958dc-146">請參閱</span><span class="sxs-lookup"><span data-stu-id="958dc-146">See Also</span></span>
[<span data-ttu-id="958dc-147">WsdlService 類型提供者</span><span class="sxs-lookup"><span data-stu-id="958dc-147">WsdlService Type Provider</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/wsdlservice-type-provider-%5bfsharp%5d)

[<span data-ttu-id="958dc-148">類型提供者</span><span class="sxs-lookup"><span data-stu-id="958dc-148">Type Providers</span></span>](index.md)
