---
title: 教學課程：建立 Windows Communication Foundation 用戶端
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: ddb5167c7f71a263377fb465ec44ee21057fbf4a
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928897"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a>教學課程：建立 Windows Communication Foundation 用戶端

本教學課程說明建立基本 Windows Communication Foundation （WCF）應用程式所需的五個工作中的第四個。 如需教學課程的總覽，請[參閱教學課程：Windows Communication Foundation 應用程式](getting-started-tutorial.md)入門。

建立 WCF 應用程式的下一個工作是從 WCF 服務抓取中繼資料來建立用戶端。 您可以使用 Visual Studio 加入服務參考，以取得來自服務 MEX 端點的中繼資料。 Visual Studio 接著會以您選擇的語言，產生用戶端 proxy 的 managed 原始程式碼檔。 它也會建立用戶端設定檔（*app.config*）。 此檔案可讓用戶端應用程式連接到端點上的服務。 

> [!NOTE]
> 如果您從 Visual Studio 的類別庫專案中呼叫 WCF 服務，請使用**加入服務參考**功能來自動產生 proxy 和相關聯的設定檔。 不過，因為類別庫專案不使用此設定檔，所以您必須將產生的設定檔中的設定，新增至呼叫類別庫之可執行檔的*app.config*檔案。

> [!NOTE]
> 或者，使用 [ [System.servicemodel 中繼資料公用程式] 工具](#servicemodel-metadata-utility-tool)，而不是 [Visual Studio] 來產生 proxy 類別和設定檔。

用戶端應用程式會使用產生的 Proxy 類別來建立與服務通訊的用戶端。 本程式說明于[教學課程：使用用戶端](how-to-use-a-wcf-client.md)。

在本教學課程中，您將了解如何：
> [!div class="checklist"]
>
> - 為 WCF 用戶端建立和設定主控台應用程式專案。
> - 將服務參考加入至 WCF 服務，以產生 proxy 類別和設定檔。

## <a name="create-a-windows-communication-foundation-client"></a>建立 Windows Communication Foundation 用戶端

1. 在 Visual Studio 中建立主控台應用程式專案： 

    1. 從 [**檔案] 功能表中，選取 [** **開啟** > **專案/方案**]，然後流覽至您先前建立的**GettingStarted**方案（*GettingStarted*）。 選取 [開啟]。

    2. 從 [ **View** ] 功能表中，選取 [**方案總管**]。

    3. 在 [**方案總管**] 視窗中，選取 [ **GettingStarted** ] 解決方案（最上層節點），然後從快捷方式功能表選取 [**加入** > **新專案**]。 
    
    4. 在左側的 [**加入新專案**] 視窗中，選取 [  **C#視覺效果**] 或 [ **Visual Basic**] 底下的 [ **Windows 桌面**] 類別。 

    5. 選取 [**主控台應用程式（.NET Framework）** ] 範本，然後在 [**名稱**] 中輸入*GettingStartedClient* 。 選取 [確定]。

2. 將**GettingStartedClient**專案中的參考新增至<xref:System.ServiceModel>元件： 

    1. 在 [**方案總管**] 視窗中，選取 [ **GettingStartedClient** ] 專案底下的 [**參考**] 資料夾，然後從快捷方式功能表選取 [**加入參考**]。 

    2. 在 [**加入參考**] 視窗中，于視窗左側的 [**元件**] 底下，選取 [**架構**]。
    
    3. 尋找並選取 [ **System.servicemodel**]，然後選擇 **[確定]** 。 

    4. 選取 > [檔案] [**全部儲存**]**以儲存方案**。

3. 將服務參考新增至計算機服務：

   1. 在 [**方案總管**] 視窗中，選取 [ **GettingStartedClient** ] 專案底下的 [**參考**] 資料夾，然後從快捷方式功能表選取 [**加入服務參考**]。

   2. 在 [**加入服務參考**] 視窗中，選取 [**探索**]。

      CalculatorService 服務會啟動，並 Visual Studio 顯示在 [**服務**] 方塊中。

   3. 選取 [ **CalculatorService** ] 將其展開，並顯示服務所執行的服務合約。 保留預設的**命名空間**，然後選擇 **[確定]** 。

      Visual Studio 會在**GettingStartedClient**專案的 [**已連線的服務**] 資料夾下加入新的專案。 

### <a name="servicemodel-metadata-utility-tool"></a>System.servicemodel 中繼資料公用程式工具

下列範例示範如何選擇性地使用[System.servicemodel 中繼資料公用程式工具（Svcutil）](servicemodel-metadata-utility-tool-svcutil-exe.md)來產生 proxy 類別檔案。 此工具會產生 proxy 類別檔案和*app.config*檔案。 下列範例顯示如何分別在和 Visual Basic 中C#產生 proxy：

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a>用戶端設定檔

建立用戶端之後，Visual Studio 會在**GettingStartedClient**專案中建立**app.config**設定檔，此檔案應該類似于下列範例：

```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
        <startup>
            <!-- specifies the version of WCF to use-->
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.1" />
        </startup>
        <system.serviceModel>
            <bindings>
                <!-- Uses wsHttpBinding-->
                <wsHttpBinding>
                    <binding name="WSHttpBinding_ICalculator" />
                </wsHttpBinding>
            </bindings>
            <client>
                <!-- specifies the endpoint to use when calling the service -->
                <endpoint address="http://localhost:8000/GettingStarted/CalculatorService"
                    binding="wsHttpBinding" bindingConfiguration="WSHttpBinding_ICalculator"
                    contract="ServiceReference1.ICalculator" name="WSHttpBinding_ICalculator">
                    <identity>
                        <dns value="localhost" />
                    </identity>
                </endpoint>
            </client>
        </system.serviceModel>
    </configuration>
```

在 [ [ \<system.servicemodel >](../configure-apps/file-schema/wcf/system-servicemodel.md) ] [ \<](../configure-apps/file-schema/wcf/endpoint-element.md)區段下，請注意端點 > 元素。 端點元素會定義用戶端用來存取服務的端點，如下所示： **&lt; &gt;**

- 位址： `http://localhost:8000/GettingStarted/CalculatorService`。 端點的位址。
- 服務合約： `ServiceReference1.ICalculator`。 服務合約會處理 WCF 用戶端與服務之間的通訊。 當您使用其**加入服務參考**函數時，Visual Studio 產生此合約。 基本上，它是您在 GettingStartedLib 專案中定義的合約複本。 
- 系結<xref:System.ServiceModel.WSHttpBinding>：。 系結會將 HTTP 指定為傳輸、互通安全性，以及其他設定詳細資料。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您將了解如何：
> [!div class="checklist"]
>
> - 為 WCF 用戶端建立和設定主控台應用程式專案。
> - 將服務參考加入至 WCF 服務，以產生用戶端應用程式的 proxy 類別和設定檔。

請前進到下一個教學課程，以瞭解如何使用產生的用戶端。

> [!div class="nextstepaction"]
> [教學課程：使用 WCF 用戶端](how-to-use-a-wcf-client.md)
