---
title: HOW TO：建立 Windows Communication Foundation 用戶端
ms.date: 09/14/2018
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: 1eadb5008575a1a53d685db14d68e42d0dce1360
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47070672"
---
# <a name="how-to-create-a-windows-communication-foundation-client"></a>HOW TO：建立 Windows Communication Foundation 用戶端

這是建立 Windows Communication Foundation (WCF) 應用程式所需的六個工作的第四個。 如需這六個工作的概觀，請參閱[使用者入門教學課程](../../../docs/framework/wcf/getting-started-tutorial.md)主題。

本主題描述如何從 WCF 服務擷取中繼資料，並使用它來建立 WCF proxy 以存取服務。 這項工作使用來完成**加入服務參考**Visual Studio 所提供的功能。 這個工具會從服務的 MEX 端點取得中繼資料，並以您所選擇的語言 (預設為 C#) 產生用戶端 Proxy 的 Managed 原始程式碼檔。 除了建立用戶端 Proxy，此工具也會建立或更新用戶端的組態檔，讓用戶端應用程式在其中一個端點與服務連線。

> [!NOTE]
> 您也可以使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)工具來產生 proxy 類別和組態，而不使用**加入服務參考**Visual Studio 中。

> [!NOTE]
> 當從 Visual Studio 中的類別庫專案中呼叫 WCF 服務，您可以使用**加入服務參考**功能來自動產生 proxy 和相關聯的組態檔。 類別庫專案將不會使用組態檔。 您要在產生的組態檔中加入呼叫類別庫的可執行檔的 app.config 檔案的設定。

用戶端應用程式會使用產生的 Proxy 類別來建立與服務通訊的用戶端。 此程序所述[如何： 使用用戶端](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)。

## <a name="to-create-a-windows-communication-foundation-client"></a>若要建立 Windows Communication Foundation 用戶端

1. Visual Studio 中建立新的主控台應用程式專案。 中的 [入門] 方案上按一下滑鼠右鍵**方案總管**，然後選取**新增** > **新專案**。 在 **加入新的專案** 對話方塊的左側，選取**Windows 桌面** 類別下的**Visual C#** 或**Visual Basic**。 選取 **主控台應用程式 (.NET Framework)** 範本，然後再將專案命名為**GettingStartedClient**。

2. 將 System.ServiceModel 的參考新增至 [gettingstartedclient] 專案中。 以滑鼠右鍵按一下**參考**中 [gettingstartedclient] 專案下的資料夾**方案總管**，然後選取**加入參考**。 在 **加入參考**對話方塊中，選取**Framework**在對話方塊左側**組件**。 尋找並選取**System.ServiceModel**，然後選擇**確定**。 選取儲存方案**檔案** > **全部儲存**。

3. 加入至計算機服務的服務參考。

   1. 首先，啟動 GettingStartedHost 主控台應用程式。

   2. 一旦主機正在執行，以滑鼠右鍵按一下**參考**中 [gettingstartedclient] 專案下的資料夾**方案總管**，然後選取**新增** >  **服務參考**。

   3. 在的 [位址] 方塊中輸入下列 URL**加入服務參考**對話方塊： [http://localhost:8000/GettingStartedClient/Service](http://localhost:8000/GettingStartedClient/Service)

   4. 選擇**移**。

   CalculatorService 所示**Services**清單方塊。 按兩下 CalculatorService 將它展開並顯示服務所實作的服務合約。 保留為預設命名空間-選擇**確定**。

    當您將使用 Visual Studio 服務的參考時，新的項目會出現在**方案總管**下方**服務參考**gettingstartedclient 專案底下的資料夾。 如果您使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)工具、 原始程式碼檔和 app.config 檔案會產生。

    您也可以使用命令列工具[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)搭配適當的參數，來建立用戶端程式碼。 下列範例會產生服務的程式碼檔案與組態檔。 第一個範例示範如何在 VB 中，產生 proxy 和第二個示範如何在 C# 中產生的 proxy:

    ```shell
    svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStartedClient/service
    ```

    ```shell
    svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStartedClient/service
    ```

## <a name="next-steps"></a>後續步驟

您已建立用戶端應用程式將用來呼叫計算機服務的 proxy。 請繼續進行系列中的下一個主題。

> [!div class="nextstepaction"]
> [如何：設定用戶端](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)

## <a name="see-also"></a>另請參閱

- [ServiceModel 中繼資料公用程式工具 (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [快速入門](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [自我裝載](../../../docs/framework/wcf/samples/self-host.md)
- [如何：使用組態檔發行服務的中繼資料](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [如何：使用 Svcutil.exe 來下載中繼資料文件](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
