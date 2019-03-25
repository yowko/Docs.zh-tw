---
title: 教學課程：建立 Windows Communication Foundation 用戶端
ms.dat8: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: 051275e56a8e63c6ab8136dbb9e24bdcf4c387df
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2019
ms.locfileid: "58411853"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a>教學課程：建立 Windows Communication Foundation 用戶端

本教學課程說明建立基本的 Windows Communication Foundation (WCF) 應用程式所需的五個工作的第四個。 如需教學課程的概觀，請參閱[教學課程：開始使用 Windows Communication Foundation 應用程式](getting-started-tutorial.md)。

建立 WCF 應用程式的下一個工作是藉由從 WCF 服務擷取中繼資料來建立用戶端。 您可以使用 Visual Studio 加入服務參考，就會從服務的 MEX 端點取得中繼資料。 Visual Studio 接著會產生您所選擇的語言用戶端 proxy 的 managed 的原始程式碼檔。 它也會建立用戶端組態檔 (*App.config*)。 此檔案可讓用戶端應用程式連接到端點的服務。 

> [!NOTE]
> 如果您從 Visual Studio 中的類別庫專案中呼叫 WCF 服務，使用**加入服務參考**功能來自動產生 proxy 和相關聯的組態檔。 不過，因為類別庫專案不使用此組態檔，您需要將設定新增至產生的組態檔中*App.config*呼叫類別庫之可執行檔的檔案。

> [!NOTE]
> 或者，使用[ServiceModel Metadata Utility 工具](#servicemodel-metadata-utility-tool)而非 Visual Studio 來產生 proxy 類別及組態檔。

用戶端應用程式會使用產生的 Proxy 類別來建立與服務通訊的用戶端。 此程序所述[教學課程：使用用戶端](how-to-use-a-wcf-client.md)。

在本教學課程中，您將了解如何：
> [!div class="checklist"]
> - 建立及設定 WCF 用戶端的主控台應用程式專案。
> - 加入服務參考至 WCF 服務，以產生 proxy 類別和組態檔。


## <a name="create-a-windows-communication-foundation-client"></a>建立 Windows Communication Foundation 用戶端

1. Visual Studio 中建立主控台應用程式專案： 

    1. 從**檔案**功能表上，選取**開放** > **專案/方案**並瀏覽至**GettingStarted**解決方案您先前建立 (*GettingStarted.sln*)。 選取 [開啟] 。

    2. 從**檢視**功能表上，選取**方案總管 中**。

    3. 在 [**方案總管] 中**視窗中，選取**GettingStarted**方案 （最上層節點），然後再選取**新增** > **新專案**快顯功能表中。 
    
    4. 在 [**加入新的專案**視窗中的，在左側，選取**Windows 桌面**] 類別下的**Visual C#** 或**Visual Basic**. 

    5. 選取 **主控台應用程式 (.NET Framework)** 範本，然後輸入*GettingStartedClient*如**名稱**。 選取 [確定]。

2. 加入參考**GettingStartedClient**專案加入<xref:System.ServiceModel>組件： 

    1.  在 **方案總管 中**視窗中，選取**參考**下的資料夾**GettingStartedClient**專案，然後再選取**加入參考**快顯功能表中。 

    2. 在 [**加入參考**] 視窗底下**組件**在視窗的左側，選取**Framework**。
    
    3. 尋找並選取**System.ServiceModel**，然後選擇**確定**。 

    4. 選取儲存方案**檔案** > **全部儲存**。

3. 加入計算機服務的服務參考：

   1. 在 [**方案總管] 中**視窗中，選取**參考**下的資料夾**GettingStartedClient**專案，然後再選取**加入服務參考**從捷徑功能表。

   2. 在 **加入服務參考**視窗中，選取**Discover**。

      CalculatorService 服務啟動和 Visual Studio 會顯示在**Services**  方塊中。

   3. 選取  **CalculatorService**將它展開並顯示服務所實作的服務合約。 保留預設值**命名空間**，然後選擇**確定**。

      Visual Studio 會加入新項目底下**已連線的服務**中的資料夾**GettingStartedClient**專案。 


### <a name="servicemodel-metadata-utility-tool"></a>ServiceModel Metadata Utility 工具

下列範例示範如何選擇性地使用[ServiceModel Metadata Utility 工具 (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)來產生 proxy 類別檔案。 此工具會產生 proxy 類別檔案和*App.config*檔案。 下列範例示範如何產生的 proxy，在C#和 Visual Basic 中，分別：

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a>用戶端組態檔

您已建立用戶端之後，Visual Studio 會建立**App.config**中的設定檔**GettingStartedClient**專案，應該會類似下列的範例：

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

底下[ \<system.serviceModel >](../configure-apps/file-schema/wcf/system-servicemodel.md)區段中，注意[\<端點 >](../configure-apps/file-schema/wcf/endpoint-element.md)項目。 **&lt;端點&gt;** 項目定義的端點，讓用戶端來存取服務，如下所示：
- 地址： `http://localhost:8000/GettingStarted/CalculatorService`。 端點的位址。
- 服務合約： `ServiceReference1.ICalculator`。 服務合約處理 WCF 用戶端與服務之間的通訊。 當您使用時，visual Studio 會產生此合約及其**加入服務參考**函式。 它基本上是複本在 GettingStartedLib 專案中所定義的合約。 
- 繫結： <xref:System.ServiceModel.WSHttpBinding>。 繫結會指定 HTTP 傳輸、 互通安全性，以及其他組態詳細資料。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您將了解如何：
> [!div class="checklist"]
> - 建立及設定 WCF 用戶端的主控台應用程式專案。
> - 加入服務參考至 WCF 服務，以產生用戶端應用程式的 proxy 類別和組態檔。

請前進到下一個教學課程，以了解如何使用產生的用戶端。

> [!div class="nextstepaction"]
> [教學課程：使用 WCF 用戶端](how-to-use-a-wcf-client.md)


