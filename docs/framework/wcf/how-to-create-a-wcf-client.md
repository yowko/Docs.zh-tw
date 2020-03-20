---
title: 教程：創建 Windows 通信基礎用戶端
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: bfa4cbacc5a947cb51d577503b5e46f9a5f8de39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184106"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a>教程：創建 Windows 通信基礎用戶端

本教程介紹創建基本 Windows 通信基礎 （WCF） 應用程式所需的五項任務中的第四個。 有關教程的概述，請參閱[教程：開始使用 Windows 通信基礎應用程式](getting-started-tutorial.md)。

創建 WCF 應用程式的下一個任務是通過從 WCF 服務檢索中繼資料來創建用戶端。 您可以使用 Visual Studio 添加服務引用，該服務引用從服務的 MEX 終結點獲取中繼資料。 然後，Visual Studio 會以您選擇的語言為用戶端代理生成託管原始程式碼檔。 它還創建一個用戶端設定檔 *（App.config*）。 此檔使用戶端應用程式能夠在終結點連接到服務。

> [!NOTE]
> 如果從 Visual Studio 中的類庫專案調用 WCF 服務，請使用 **"添加服務參考"** 功能自動生成代理和相關設定檔。 但是，由於類庫專案不使用此設定檔，因此您需要將生成的設定檔中的設置添加到調用類庫的可執行檔*App.config*檔中。

> [!NOTE]
> 作為替代方法，請使用[ServiceModel 中繼資料實用程式工具](#servicemodel-metadata-utility-tool)而不是 Visual Studio 來生成代理類和設定檔。

用戶端應用程式會使用產生的 Proxy 類別來建立與服務通訊的用戶端。 此過程在教程中描述[：使用用戶端](how-to-use-a-wcf-client.md)。

在本教學課程中，您會了解如何：
> [!div class="checklist"]
>
> - 為 WCF 用戶端創建和配置主控台應用專案。
> - 向 WCF 服務添加服務引用以生成代理類和設定檔。

## <a name="create-a-windows-communication-foundation-client"></a>創建 Windows 通信基礎用戶端

1. 在視覺化工作室中創建主控台應用專案：

    1. 在 **"檔"** 功能表中，選擇 **"打開** > **專案/解決方案**"並流覽到您以前創建的**入門**解決方案 （*獲取入門.sln*）。 選取 [開啟]****。

    2. 在 **"查看"** 功能表中，選擇 **"解決方案資源管理器**"。

    3. 在 **"解決方案資源管理器"** 視窗中，選擇 **"入門"** 解決方案（頂部節點），然後從快顯功能表中選擇 **"添加新** > **專案**"。

    4. 在左側的 **"添加新專案**"視窗中，在 **"可視 C#"** 或"**可視基本**"下選擇**Windows 桌面**類別。

    5. 選擇**主控台應用 （.NET 框架）** 範本，然後輸入"*開始用戶端*"**名稱**。 選取 [確定]****。

2. 在**入門用戶端**專案中向<xref:System.ServiceModel>程式集增加參考：

    1. 在 **"解決方案資源管理器"** 視窗中，選擇 **"入門用戶端**"專案下的 **"參考"** 資料夾，然後從快顯功能表中選擇 **"增加參考**"。

    2. 在"**增加參考**"視窗中，在視窗左側的 **"程式集**"下，選擇 **"框架**"。

    3. 查找並選擇 **"系統.服務模式**"，然後選擇 **"確定**"。

    4. 通過選擇 **"全部保存檔** > **"保存**解決方案。

3. 向計算機服務添加服務引用：

   1. 在 **"解決方案資源管理器"** 視窗中，選擇 **"入門用戶端**"專案下的 **"參考"** 資料夾，然後從快顯功能表中選擇 **"添加服務參考**"。

   2. 在 **"添加服務參考"** 視窗中，選擇 **"發現**"。

      計算機服務啟動，視覺化工作室在 **"服務**"框中顯示它。

   3. 選擇**計算機服務**以展開它並顯示服務實現的服務協定。 保留預設**命名空間**並選擇 **"確定**"。

      Visual Studio 在 **"入門用戶端**"專案中的 **"已連接服務**"資料夾下添加新專案。

### <a name="servicemodel-metadata-utility-tool"></a>服務模型中繼資料實用程式工具

以下示例演示如何選擇使用[ServiceModel 中繼資料實用程式工具 （Svcutil.exe）](servicemodel-metadata-utility-tool-svcutil-exe.md)來生成代理類檔。 此工具生成代理類檔和*App.config*檔。 以下示例分別演示如何在 C# 和 Visual Basic 中生成代理：

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a>用戶端組態檔

創建用戶端後，Visual Studio 將在 **"入門Client"** 專案中創建**App.config**設定檔，該檔應類似于以下示例：

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

在[\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md)部分下，請注意[\<終結點>](../configure-apps/file-schema/wcf/endpoint-element.md)元素。 ** &lt;終結點&gt;** 元素定義用戶端用於訪問服務的終結點，如下所示：

- 位址： `http://localhost:8000/GettingStarted/CalculatorService`. 端點的位址。
- 服務合同： `ServiceReference1.ICalculator`. 服務協定處理 WCF 用戶端和服務之間的通信。 當您使用其 **"添加服務參考"** 功能時，Visual Studio 生成了此協定。 它實質上是您在入門專案中定義的合同副本。
- 綁定： <xref:System.ServiceModel.WSHttpBinding>. 綁定指定 HTTP 作為傳輸、可交互操作的安全性和其他配置詳細資訊。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已了解如何：
> [!div class="checklist"]
>
> - 為 WCF 用戶端創建和配置主控台應用專案。
> - 向 WCF 服務添加服務引用，以生成用戶端應用程式的代理類和設定檔。

前進至下一個教程，瞭解如何使用生成的用戶端。

> [!div class="nextstepaction"]
> [教程：使用 WCF 用戶端](how-to-use-a-wcf-client.md)
