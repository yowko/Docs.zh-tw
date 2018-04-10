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
# <a name="walkthrough-accessing-a-web-service-by-using-type-providers"></a>逐步解說：使用型別提供者存取 Web 服務

> [!NOTE]
本指南針對 F # 3.0 所撰寫，而且會更新。  請參閱 [FSharp.Data](https://fsharp.github.io/FSharp.Data/) 以取得最新的跨平台型別提供者。

> [!NOTE]
應用程式開發介面參考連結將帶您到 MSDN。  docs.microsoft.com API 參考不完整。

本逐步解說將示範如何使用在 F # 3.0 來存取 WSDL 服務中使用的 Web 服務描述語言 (WSDL) 型別提供者。 在其他.NET 語言中，產生的程式碼來存取 web 服務呼叫 svcutil.exe，藉由加入 web 參考，比方說，C# 專案或取得 Visual Studio 為您呼叫 svcutil.exe。 在 F # 中，您有其他選項可使用 WSDL 的型別提供者，因此只要您撰寫的程式碼會建立 wsdlservice 型別、 型別產生並變成可用。 此程序依賴您撰寫程式碼時所使用的服務。

這個逐步解說將說明下列工作。 您必須完成它們依此順序順利完成此逐步解說：


- 建立專案
<br />

- 設定型別提供者
<br />

- 呼叫 web 服務，並處理結果
<br />


## <a name="creating-the-project"></a>建立專案
在步驟中，您可以建立專案，並加入適當的參考，以使用 WSDL 型別提供者。


#### <a name="to-create-and-set-up-an-f-project"></a>若要建立並設定 F# 專案

1. 開啟新的 F # 主控台應用程式專案。
<br />

2. 在**方案總管 中**，開啟專案的捷徑功能表**參考** 節點，然後選擇 **加入參考**。
<br />

3. 在**組件**區域中，選擇**Framework**，然後在可用組件清單中，選擇  **System.Runtime.Serialization**和**System.ServiceModel**。
<br />

4. 在**組件**區域中，選擇**延伸**。
<br />

5. 在可用組件清單中，選擇  **FSharp.Data.TypeProviders**，然後選擇  **確定**按鈕以加入這些組件的參考。
<br />

## <a name="configuring-the-type-provider"></a>設定型別提供者
在此步驟中，您可以使用 WSDL 型別提供者產生 TerraServer web 服務的型別。


#### <a name="to-configure-the-type-provider-and-generate-types"></a>若要設定型別提供者和產生類型

1. 加入下列程式碼，以開啟型別提供者命名空間。
<br />

```fsharp
open System
open System.ServiceModel
open Microsoft.FSharp.Linq
open Microsoft.FSharp.Data.TypeProviders
```

2. 加入下列程式碼來叫用 web 服務的型別提供者。 在此範例中，使用 TerraServer web 服務。
<br />

```fsharp
type TerraService = WsdlService<" HYPERLINK "https://terraserver-usa.com/TerraService2.asmx?WSDL" https://msrmaps.com/TerraService2.asmx?WSDL">
```

  如果服務 URI 拼錯，或者服務本身已關閉，或不執行底下這行程式碼會出現紅色曲線。 如果您指向程式碼時，錯誤訊息說明的問題。 您可以找到相同的資訊**錯誤清單**視窗或在**輸出 視窗**建置之後。
<br />  有兩種方式使用 app.config 檔案的專案，或使用靜態型別參數的型別提供者的宣告中指定的 WSDL 連接，組態設定。 您可以使用 svcutil.exe 來產生適當的組態檔項目。 如需有關如何使用 svcutil.exe 來產生 web 服務的組態資訊的詳細資訊，請參閱[ServiceModel Metadata Utility Tool &#40;Svcutil.exe &#41;](https://msdn.microsoft.com/library/aa347733.aspx). 如需 WSDL 的型別提供者的靜態型別參數的完整描述，請參閱[WsdlService 類型提供者](https://msdn.microsoft.com/visualfsharpdocs/conceptual/wsdlservice-type-provider-%5bfsharp%5d)。
<br />

## <a name="calling-the-web-service-and-processing-the-results"></a>呼叫 web 服務，並處理結果
每個 web 服務都有它自己的型別，其方法呼叫做為參數集。 在此步驟中，您可以準備這些參數，呼叫 web 方法，並處理它所傳回的資訊。


#### <a name="to-call-the-web-service-and-process-the-results"></a>呼叫 web 服務，並處理結果

1. Web 服務可能會逾時或停止運作，所以您應該將 web 服務呼叫中，例外狀況處理區塊。 撰寫下列程式碼嘗試從 web 服務取得資料。
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

請注意，您建立的資料類型所需的 web 服務，例如**位置**和**位置**，如 wsdlservice 型底下的巢狀型別輸入**TerraService**。
<br />


## <a name="see-also"></a>請參閱
[WsdlService 類型提供者](https://msdn.microsoft.com/visualfsharpdocs/conceptual/wsdlservice-type-provider-%5bfsharp%5d)

[類型提供者](index.md)
