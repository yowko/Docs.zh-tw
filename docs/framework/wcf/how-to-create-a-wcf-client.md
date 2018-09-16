---
title: HOW TO：建立 Windows Communication Foundation 用戶端
ms.date: 03/30/2017
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: e5655a6fdc06e69d801cb38b7ee7412450f0d34c
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2018
ms.locfileid: "45674139"
---
# <a name="how-to-create-a-windows-communication-foundation-client"></a>HOW TO：建立 Windows Communication Foundation 用戶端

這是建立 Windows Communication Foundation (WCF) 應用程式所需的六個工作的第四個。 如需這六個工作的概觀，請參閱[使用者入門教學課程](../../../docs/framework/wcf/getting-started-tutorial.md)主題。

本主題描述如何從 WCF 服務擷取中繼資料，並使用它來建立 WCF proxy 以存取服務。 這個工作是使用 Visual Studio 提供的 [加入服務參考] 功能來完成。 這個工具會從服務的 MEX 端點取得中繼資料，並以您所選擇的語言 (預設為 C#) 產生用戶端 Proxy 的 Managed 原始程式碼檔。 除了建立用戶端 Proxy，此工具也會建立或更新用戶端的組態檔，讓用戶端應用程式在其中一個端點與服務連線。

> [!NOTE]
> 您也可以使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)工具來產生 proxy 類別和組態，而不使用 Visual studio 的 加入服務參考。

> [!WARNING]
> 從類別庫專案中呼叫 WCF 服務時[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]您可以使用 「 加入服務參考 」 功能來自動產生 proxy 和相關聯的組態檔。  類別庫專案將不會使用組態檔。 您必須將所產生組態檔中的設定加入至將會呼叫類別庫之可執行檔的 app.config 檔案。

 用戶端應用程式會使用產生的 Proxy 類別來建立與服務通訊的用戶端。 此程序所述[如何： 使用用戶端](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)。

## <a name="to-create-a-windows-communication-foundation-client"></a>若要建立 Windows Communication Foundation 用戶端

1.  以滑鼠右鍵按一下 [快速入門] 方案，選取建立新的主控台應用程式專案**新增**，**新的專案**。 在 [新增專案] 對話方塊的左側，選取 [C#] 或 [VB] 下方的 [Windows]。 在對話方塊的中間區段中選取 [主控台應用程式]。 將專案命名為 `GettingStartedClient`。

2.  Gettingstartedclient 專案的目標 framework 設定為.NET Framework 4.5，以滑鼠右鍵按一下**GettingStartedClient**方案總管 中，然後選取**屬性**。 在標示 [目標 Framework] 的下拉式方塊中選取 [.NET Framework 4.5]。 設定目標 framework VB 專案有點不同，請在 GettingStartedClient 專案屬性對話方塊中，按一下**編譯**左手邊的畫面中，索引標籤，然後按一下**進階編譯選項**在對話方塊的左下角的按鈕。 接著在標籤為 [目標 Framework] 的下拉式方塊中選取 [.NET Framework 4.5]。

     設定目標 framework 會導致 Visual Studio 2011 重新載入該方案中，按下**確定**出現提示時。

3.  將 System.ServiceModel 的參考新增至 [gettingstartedclient] 專案中，以滑鼠右鍵按一下**參考**在 [方案總管]，然後選取 [gettingstartedclient] 專案下的資料夾**新增**參考。 在 [新增參考] 對話方塊中，選取對話方塊左側的 [Framework]。 在 [搜尋組件] 文字方塊中輸入 `System.ServiceModel`。 在對話方塊中間區段中選取 [System.ServiceModel]，按一下 [新增] 按鈕，然後按一下 [關閉] 按鈕。 按一下以儲存方案**全部儲存**主功能表下的按鈕。

4.  接下來，您會新增至計算機服務的服務參考。 您必須先啟動 GettingStartedHost 主控台應用程式，才能執行此作業。 一旦主機正在執行，以滑鼠右鍵按一下**參考**中 [gettingstartedclient] 專案下的資料夾**方案總管**，然後選取**新增** >  **服務參考**。 在下列 URL 中的 [位址] 方塊中的型別**加入服務參考** 對話方塊： [ http://localhost:8000/GettingStartedClient/Service ](http://localhost:8000/GettingStartedClient/Service) ，按一下 [**移**] 按鈕。 CalculatorService 接著應該顯示在 [服務] 清單中。 按兩下 CalculatorService，它會展開並顯示服務所實作的服務合約。 保留預設命名空間，並按一下**確定** 按鈕。

     當您使用 Visual Studio 加入服務的參考時，新項目將會在 [方案總管] 中 [GettingStartedClient] 專案底下的 [服務參考] 資料夾下方出現。  如果您使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)工具將產生的原始程式碼檔和 app.config 檔案。

     您也可以使用命令列工具[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)搭配適當的參數，來建立用戶端程式碼。 下列範例會產生服務的程式碼檔案與組態檔。 第一個範例示範如何在 VB 中產生 Proxy，第二個範例示範如何在 C# 中產生 Proxy：

    ```
    svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStartedClient/service
    ```

    ```csharp
    svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStartedClient/service
    ```

 現在您已建立用戶端應用程式將用來呼叫計算機服務的 Proxy。 請繼續進行系列中的下一個主題： [How to： 設定用戶端](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)

## <a name="see-also"></a>另請參閱

- [ServiceModel 中繼資料公用程式工具 (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [快速入門](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [自我裝載](../../../docs/framework/wcf/samples/self-host.md)
- [如何：使用組態檔發行服務的中繼資料](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [如何：使用 Svcutil.exe 來下載中繼資料文件](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
