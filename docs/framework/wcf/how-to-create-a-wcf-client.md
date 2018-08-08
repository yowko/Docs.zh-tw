---
title: HOW TO：建立 Windows Communication Foundation 用戶端
ms.date: 03/30/2017
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: d2932293536f875d8986d8d49842cddc196ced0f
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806269"
---
# <a name="how-to-create-a-windows-communication-foundation-client"></a>HOW TO：建立 Windows Communication Foundation 用戶端
這是建立 Windows Communication Foundation (WCF) 應用程式所需的六個工作的第四個。 六個工作的概觀，請參閱[入門教學課程](../../../docs/framework/wcf/getting-started-tutorial.md)主題。  
  
 本主題描述如何從 WCF 服務擷取中繼資料，並使用它來建立 WCF proxy 可以存取服務。 這個工作是使用 Visual Studio 提供的 [加入服務參考] 功能來完成。 這個工具會從服務的 MEX 端點取得中繼資料，並以您所選擇的語言 (預設為 C#) 產生用戶端 Proxy 的 Managed 原始程式碼檔。 除了建立用戶端 Proxy，此工具也會建立或更新用戶端的組態檔，讓用戶端應用程式在其中一個端點與服務連線。  
  
> [!NOTE]
>  您也可以使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)工具來產生 proxy 類別和組態，而不使用在 Visual Studio 內加入服務參考。  
  
> [!WARNING]
>  從 類別庫專案中呼叫 WCF 服務時[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]您可以使用 [加入服務參考] 功能來自動產生 proxy 與相關聯的組態檔。  類別庫專案將不會使用組態檔。 您必須將所產生組態檔中的設定加入至將會呼叫類別庫之可執行檔的 app.config 檔案。  
  
 用戶端應用程式會使用產生的 Proxy 類別來建立與服務通訊的用戶端。 此程序所述[How to： 使用用戶端](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)。  
  
### <a name="to-create-a-windows-communication-foundation-client"></a>若要建立 Windows Communication Foundation 用戶端  
  
1.  以滑鼠右鍵按一下 開始使用的方案，選取 建立新的主控台應用程式專案**新增**，**新專案**。 在**加入新的專案**對話方塊左側的對話方塊中，選取**Windows**下**C#** 或**VB**。 在對話方塊中間區段選取**主控台應用程式**。 將專案命名為 `GettingStartedClient`。  
  
2.  上按一下滑鼠右鍵，將 [gettingstartedclient] 專案的目標 framework 設定為.NET Framework 4.5 **GettingStartedClient**在 [方案總管] 中，然後選取**屬性**。 下拉式方塊中標示為**目標 Framework**選取 **.NET Framework 4.5**。 設定目標 framework VB 專案的方式稍有不同，請在 GettingStartedClient 專案屬性對話方塊，按一下**編譯**畫面中，左側索引標籤，然後按一下 **進階編譯選項**位於對話方塊左下角的按鈕。 然後選取 **.NET Framework 4.5**下拉式方塊中標示為**目標 Framework**。  
  
     設定目標 framework 會導致 Visual Studio 2011 重新載入該方案，請按**確定**出現提示時。  
  
3.  將 System.ServiceModel 的參考加入至 gettingstartedclient 專案，以滑鼠右鍵按一下**參考**在方案總管，然後選取 gettingstartedclient 專案下的資料夾**新增**參考。 在**加入參考**對話方塊中，選取**Framework**對話方塊的左側。 在 [搜尋組件] 文字方塊中輸入 `System.ServiceModel`。 在對話方塊中間區段選取**System.ServiceModel**，按一下 [**新增**按鈕，然後按一下**關閉**] 按鈕。 按一下以儲存方案**全部儲存**主功能表下的按鈕。  
  
4.  接著您要將服務參考加入至計算機服務。 您必須先啟動 GettingStartedHost 主控台應用程式，才能執行此作業。 一旦主機在執行您可以以滑鼠右鍵按一下方案總管 中 gettingstartedclient 專案底下的 參考 資料夾，並選取加入服務參考，然後輸入下列 URL 中的 加入服務參考 對話方塊的 位址 方塊中： 超連結"http://localhost:8000/ServiceModelSamples/Service"http://localhost:8000/ServiceModelSamples/Service按一下**移** 按鈕。 CalculatorService 接著應該會顯示在 [服務] 清單方塊中，請按兩下 [CalculatorService]，其將展開並顯示服務所實作的服務合約。 保留預設命名空間，並按一下**確定** 按鈕。  
  
     當您使用 Visual Studio 加入服務的參考時，新項目將會在 [方案總管] 中 [GettingStartedClient] 專案底下的 [服務參考] 資料夾下方出現。  如果您使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)將產生的原始程式碼檔和 app.config 檔案的工具。  
  
     您也可以使用命令列工具[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)使用適當參數來建立用戶端程式碼。 下列範例會產生服務的程式碼檔案與組態檔。 第一個範例示範如何在 VB 中產生 Proxy，第二個範例示範如何在 C# 中產生 Proxy：  
  
    ```  
    svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/ServiceModelSamples/service  
    ```  
  
    ```csharp  
    svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/ServiceModelSamples/service  
    ```  
  
 現在您已建立用戶端應用程式將用來呼叫計算機服務的 Proxy。 移到數列中的下一個主題： [How to： 設定用戶端](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)  
  
## <a name="see-also"></a>另請參閱  
 [ServiceModel 中繼資料公用程式工具 (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [快速入門](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [自我裝載](../../../docs/framework/wcf/samples/self-host.md)  
 [如何：使用組態檔發行服務的中繼資料](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [如何：使用 Svcutil.exe 來下載中繼資料文件](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
