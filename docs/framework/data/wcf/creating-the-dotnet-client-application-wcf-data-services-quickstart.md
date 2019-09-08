---
title: 建立 .NET Framework 用戶端應用程式 (WCF 資料服務快速入門)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 41ade767-eeab-437d-9121-9797e8fb8045
ms.openlocfilehash: 9995a509bf997298d991a1f66cfdf3cae6cd0395
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790961"
---
# <a name="creating-the-net-framework-client-application-wcf-data-services-quickstart"></a>建立 .NET Framework 用戶端應用程式 (WCF 資料服務快速入門)

這是 WCF Data Services 快速入門的最後一項工作。 在這項工作中，您會在方案中加入主控台應用程式、在這個新[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]的用戶端應用程式中加入摘要的參考，並使用產生的用戶端資料服務類別和用戶端程式庫，從用戶端應用程式存取 OData 饋送.

> [!NOTE]
> 不需要 .NET Framework 架構的用戶端應用程式也可存取資料摘要。 任何取用 OData 摘要的應用程式元件都可存取資料服務。 如需詳細資訊，請參閱[在用戶端應用程式中使用資料服務](using-a-data-service-in-a-client-application-wcf-data-services.md)。

## <a name="to-create-the-client-application-by-using-visual-studio"></a>若要使用 Visual Studio 建立用戶端應用程式

1. 在**方案總管**中，以滑鼠右鍵按一下方案，然後按一下 [**加入**]，再按一下 [**新增專案**]。

2. 在左窗格中，選取 [**已安裝**] > [**視覺C#效果**] 或 [ **Visual Basic**] > **Windows 桌面**]，然後選取 [ **WPF 應用程式** 範本。

3. 針對`NorthwindClient` [專案名稱] 輸入，然後按一下 **[確定]** 。

4. 開啟 MainWindow.xaml 檔案，並以下列程式碼取代 XAML 程式碼：

     [!code-xaml[Astoria Quickstart Client#Window1Xaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml#window1xaml)]

## <a name="to-add-a-data-service-reference-to-the-project"></a>若要將資料服務參考加入至專案

1. 在**方案總管**中，以滑鼠右鍵按一下 NorthwindClient 專案，按一下 [**加入** > **服務參考**]，然後按一下 [**探索**]。

     這會顯示您在第一個工作中建立的 Northwind 資料服務。

2. 在 [**命名空間**] 文字方塊中`Northwind`，輸入，然後按一下 **[確定]** 。

     這會將新的程式碼檔案加入至專案中，此專案包含的資料類別可用來存取做為物件的資料服務資源，並與之進行互動。 在命名空間 `NorthwindClient.Northwind` 中建立資料類別。

## <a name="to-access-data-service-data-in-the-wpf-application"></a>在 WPF 應用程式中存取資料服務的資料

1. 在 [ **NorthwindClient**] 下的**方案總管**中，以滑鼠右鍵按一下專案，然後按一下 [**加入參考**]。

2. 在 [**加入參考**] 對話方塊中，按一下 [ **.net** ] 索引標籤，選取 [system.web] 元件，然後按一下 **[確定]** 。

3. 在 [ **NorthwindClient**] 下的`using` **方案總管**中，開啟 mainwindow.xaml 檔案的字碼頁，並加入下列語句（`Imports`在 Visual Basic 中）。

    [!code-csharp[Astoria Quickstart Client#Using](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_client/cs/window1.xaml.cs#using)]
    [!code-vb[Astoria Quickstart Client#Using](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml.vb#using)]

4. 插入下列查詢資料服務的程式碼，並將 <xref:System.Data.Services.Client.DataServiceCollection%601> 的結果繫結到 `MainWindow` 類別裡：

    > [!NOTE]
    > 您必須用裝載 Northwind 資料服務之執行個體的伺服器及連接埠來取代主機名稱 `localhost:12345`。

     [!code-csharp[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_client/cs/window1.xaml.cs#querycode)]
     [!code-vb[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml.vb#querycode)]

5. 將下列儲存變更的程式碼插入 `MainWindow` 類別中：

     [!code-csharp[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_client/cs/window1.xaml.cs#savechanges)]
     [!code-vb[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml.vb#savechanges)]

## <a name="to-build-and-run-the-northwindclient-application"></a>建置和執行 NorthwindClient 應用程式

1. 在**方案總管**中，以滑鼠右鍵按一下 NorthwindClient 專案，然後選取 [**設定為啟始專案**]。

2. 按**F5**啟動應用程式。

     如此會建置方案，並啟動用戶端應用程式。 從服務要求資料，並顯示在主控台中。

3. 在資料格的 [**數量**] 資料行中編輯值，然後按一下 [**儲存**]。

     資料服務的變更會被儲存。

    > [!NOTE]
    > 此版本的 NorthwindClient 應用程式不支援新增及刪除實體。

## <a name="next-steps"></a>後續步驟

您已成功建立存取範例 Northwind OData 摘要的用戶端應用程式。 您也已完成 WCF Data Services 快速入門！

如需從 .NET Framework 應用程式存取 OData 摘要的詳細資訊，請參閱[WCF Data Services 用戶端程式庫](wcf-data-services-client-library.md)。

## <a name="see-also"></a>另請參閱

- [快速入門](getting-started-with-wcf-data-services.md)
- [資源](wcf-data-services-resources.md)
